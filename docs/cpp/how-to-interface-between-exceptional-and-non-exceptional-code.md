---
title: Как взаимодействовать с исключительным и неисключительным кодом
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: fd5bb4af-5665-46a1-a321-614b48d4061e
ms.openlocfilehash: fccc40302ab7bd43b3e6b2f87eef488c7813c9be
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245613"
---
# <a name="how-to-interface-between-exceptional-and-non-exceptional-code"></a>Как взаимодействовать с исключительным и неисключительным кодом

В этой статье описывается, как реализовать последовательную обработку исключений в C++ модуле, а также как преобразовать эти исключения в коды ошибок и из них на границах исключений.

Иногда C++ модуль может взаимодействовать с кодом, который не использует исключения (код не является исключительным). Такой интерфейс называется *границей исключения*. Например, может потребоваться вызвать функцию Win32 `CreateFile` в C++ программе. `CreateFile` не создает исключения; Вместо этого он устанавливает коды ошибок, которые могут быть получены функцией `GetLastError`. Если C++ программа не является тривиальной, то в ней, вероятно, будет предпочтительнее иметь единообразную политику обработки ошибок на основе исключений. И вы, вероятно, не хотите отменять исключения просто потому, что вы будете взаимодействовать с неисключительным кодом, и ни на что не хотите смешивать политики ошибок на основе исключений и исключений C++ , не основанных на исключениях, в модуле.

## <a name="calling-non-exceptional-functions-from-c"></a>Вызов неисключительных функций изC++

При вызове неисключительной функции из C++, идея заключается в переносе этой функции в C++ функцию, которая обнаруживает ошибки, а затем, возможно, вызывает исключение. При проектировании такой функции-оболочки сначала необходимо решить, какой тип гарантии исключения следует предоставить: без-Throw, строгий или базовый. Во-вторых, разработайте функцию таким образом, чтобы все ресурсы, например дескрипторы файлов, были правильно освобождены при возникновении исключения. Как правило, это означает, что для владельца ресурсов используются смарт-указатели или аналогичные диспетчеры ресурсов. Дополнительные сведения о вопросах проектирования см. [в разделе руководство. проектирование безопасности исключений](how-to-design-for-exception-safety.md).

### <a name="example"></a>Пример

В следующем примере показаны C++ функции, которые используют `CreateFile` Win32 и функции `ReadFile` внутренне для открытия и чтения двух файлов.  Класс `File` — это программа-оболочка для получения ресурсов (RAII) для дескрипторов файлов. Его конструктор обнаруживает условие "файл не найден" и создает исключение для распространения ошибки вверх по стеку вызовов C++ модуля (в данном примере это функция `main()`). Если исключение создается после того, как объект `File` полностью создан, деструктор автоматически вызывает метод `CloseHandle`, чтобы освободить этот файл. (Если вы предпочитаете, можно использовать класс `CHandle` ATL для этой же цели или `unique_ptr` вместе с пользовательским удалением.) Функции, вызывающие API-интерфейсы Win32 и CRT, обнаруживают ошибки C++ , а затем выдают исключения с помощью локально определенной функции `ThrowLastErrorIf`, которая, в свою очередь, использует класс `Win32Exception`, производный от класса `runtime_error`. Все функции в этом примере обеспечивают строгую гарантию исключений. Если исключение создается в любой точке этих функций, ресурсы не теряются и состояние программы не изменяется.

```cpp
// compile with: /EHsc
#include <Windows.h>
#include <stdlib.h>
#include <vector>
#include <iostream>
#include <string>
#include <limits>
#include <stdexcept>

using namespace std;

string FormatErrorMessage(DWORD error, const string& msg)
{
    static const int BUFFERLENGTH = 1024;
    vector<char> buf(BUFFERLENGTH);
    FormatMessageA(FORMAT_MESSAGE_FROM_SYSTEM, 0, error, 0, buf.data(),
        BUFFERLENGTH - 1, 0);
    return string(buf.data()) + "   ("  + msg  + ")";
}

class Win32Exception : public runtime_error
{
private:
    DWORD m_error;
public:
    Win32Exception(DWORD error, const string& msg)
        : runtime_error(FormatErrorMessage(error, msg)), m_error(error) { }

    DWORD GetErrorCode() const { return m_error; }
};

void ThrowLastErrorIf(bool expression, const string& msg)
{
    if (expression) {
        throw Win32Exception(GetLastError(), msg);
    }
}

class File
{
private:
    HANDLE m_handle;

    // Declared but not defined, to avoid double closing.
    File& operator=(const File&);
    File(const File&);
public:
    explicit File(const string& filename)
    {
        m_handle = CreateFileA(filename.c_str(), GENERIC_READ, FILE_SHARE_READ,
            nullptr, OPEN_EXISTING, FILE_ATTRIBUTE_READONLY, nullptr);
        ThrowLastErrorIf(m_handle == INVALID_HANDLE_VALUE,
            "CreateFile call failed on file named " + filename);
    }

    ~File() { CloseHandle(m_handle); }

    HANDLE GetHandle() { return m_handle; }
};

size_t GetFileSizeSafe(const string& filename)
{
    File fobj(filename);
    LARGE_INTEGER filesize;

    BOOL result = GetFileSizeEx(fobj.GetHandle(), &filesize);
    ThrowLastErrorIf(result == FALSE, "GetFileSizeEx failed: " + filename);

    if (filesize.QuadPart < (numeric_limits<size_t>::max)()) {
        return filesize.QuadPart;
    } else {
        throw;
    }
}

vector<char> ReadFileVector(const string& filename)
{
    File fobj(filename);
    size_t filesize = GetFileSizeSafe(filename);
    DWORD bytesRead = 0;

    vector<char> readbuffer(filesize);

    BOOL result = ReadFile(fobj.GetHandle(), readbuffer.data(), readbuffer.size(),
        &bytesRead, nullptr);
    ThrowLastErrorIf(result == FALSE, "ReadFile failed: " + filename);

    cout << filename << " file size: " << filesize << ", bytesRead: "
        << bytesRead << endl;

    return readbuffer;
}

bool IsFileDiff(const string& filename1, const string& filename2)
{
    return ReadFileVector(filename1) != ReadFileVector(filename2);
}

#include <iomanip>

int main ( int argc, char* argv[] )
{
    string filename1("file1.txt");
    string filename2("file2.txt");

    try
    {
        if(argc > 2) {
            filename1 = argv[1];
            filename2 = argv[2];
        }

        cout << "Using file names " << filename1 << " and " << filename2 << endl;

        if (IsFileDiff(filename1, filename2)) {
            cout << "+++ Files are different." << endl;
        } else {
            cout<< "=== Files match." << endl;
        }
    }
    catch(const Win32Exception& e)
    {
        ios state(nullptr);
        state.copyfmt(cout);
        cout << e.what() << endl;
        cout << "Error code: 0x" << hex << uppercase << setw(8) << setfill('0')
            << e.GetErrorCode() << endl;
        cout.copyfmt(state); // restore previous formatting
    }
}
```

## <a name="calling-exceptional-code-from-non-exceptional-code"></a>Вызов исключительного кода из неисключительного кода

C++функции, объявленные как "extern C", могут вызываться программами на языке C. C++COM-серверы можно использовать в коде, написанном на любом из нескольких различных языков. При реализации открытых функций с поддержкой исключений в C++ для вызова неисключительным кодом C++ функция не должна разрешать всем исключениям распространяться обратно вызывающему объекту. Поэтому C++ функция должна явным образом перехватить каждое исключение, которое ему известно, как управлять, и при необходимости преобразовать исключение в код ошибки, распознаваемый вызывающим объектом. Если известны не все потенциальные исключения, C++ функция должна иметь блок `catch(...)` в качестве последнего обработчика. В этом случае лучше сообщить вызывающей стороне о неустранимой ошибке, так как ваша программа может находиться в неизвестном состоянии.

В следующем примере показана функция, которая предполагает, что любое исключение, которое может быть создано, является либо Win32Exception, либо типом исключения, производным от `std::exception`. Функция перехватывает любое исключение этих типов и распространяет сведения об ошибке как код ошибки Win32 вызывающему объекту.

```cpp
BOOL DiffFiles2(const string& file1, const string& file2)
{
    try
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return FALSE;
        }
        return TRUE;
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }

    catch(std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return FALSE;
}
```

При преобразовании из исключений в коды ошибок часто возникают проблемы, возникающие в том, что коды ошибок зачастую не содержат богатую информацию, которую может хранить исключение. Чтобы устранить эту ошибку, можно предоставить блок **catch** для каждого конкретного типа исключения, который может быть создан, и выполнить ведение журнала для записи сведений об исключении перед его преобразованием в код ошибки. Такой подход может создать большое количество повторов кода, если в нескольких функциях используется один набор блоков **catch** . Хорошим способом избежать повторения кода является рефакторинг этих блоков в одну закрытую служебную функцию, которая реализует блоки **try** и **catch** и принимает объект функции, который вызывается в блоке **try** . В каждой открытой функции передайте код в служебную функцию в виде лямбда-выражения.

```cpp
template<typename Func>
bool Win32ExceptionBoundary(Func&& f)
{
    try
    {
        return f();
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }
    catch(const std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return false;
}
```

В следующем примере показано, как написать лямбда-выражение, определяющее функтор. Если функтор определен как "встроенный" с помощью лямбда-выражения, часто бывает проще прочитать, чем если бы он был записан как объект именованной функции.

```cpp
bool DiffFiles3(const string& file1, const string& file2)
{
    return Win32ExceptionBoundary([&]() -> bool
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return false;
        }
        return true;
    });
}
```

Дополнительные сведения о лямбда-выражениях см. в разделе [Лямбда-выражения](lambda-expressions-in-cpp.md).

## <a name="see-also"></a>См. также:

[Современные C++ рекомендации по исключениям и обработке ошибок](errors-and-exception-handling-modern-cpp.md)<br/>
[Практическое руководство. Разработка с учетом безопасности исключений](how-to-design-for-exception-safety.md)<br/>
