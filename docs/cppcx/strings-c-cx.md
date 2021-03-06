---
title: Строки (C++/CX)
ms.date: 01/22/2017
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
ms.openlocfilehash: 8f7cbdd02cb1d38231c476ba939009a95533a046
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403247"
---
# <a name="strings-ccx"></a>Строки (C++/CX)

Текст в среде выполнения Windows представлена в C++/CX по [класс Platform::String](../cppcx/platform-string-class.md). Используйте `Platform::String Class` при передаче строки и обратно в методы в классах среды выполнения Windows, или когда выполняется взаимодействие с другими компонентами среды выполнения Windows через границы двоичного интерфейса (ABI) приложения. `Platform::String Class` предоставляет методы для некоторых типичных операций над строками, но он является полнофункциональным классом строки. При разработке модуля в C++ используйте стандартные строковые типы C++ (такие как [wstring](../standard-library/basic-string-class.md) ) для сложной обработки строк и преобразуйте конечный результат в тип [Platform::String^](../cppcx/platform-string-class.md) , прежде чем передать его открытому интерфейсу или получить его из такого интерфейса. Операция преобразования между типом `wstring` или `wchar_t*` и типом `Platform::String`проста и эффективна.

**Быстрая передача**

В некоторых случаях компилятор может удостовериться, что есть возможность безопасно создать экземпляр класса `Platform::String` или передать объект `String` функции, не копируя основные данные строки. Эти операции называются *быстрой передачей* , и их выполнение прозрачно.

## <a name="string-construction"></a>Создание строк

Значение объекта `String` — неизменяемая (доступная только для чтения) последовательность символов `char16` (16-разрядных символов Юникода). Поскольку объект `String` является неизменяемым, присвоение нового строкового литерала переменной `String` фактически заменяет исходный объект `String` новым объектом `String` . При операции объединения исходный объект `String` разрушается, и создается новый объект.

**Литералы**

*Символ-литерал* — это символ, заключенный в одиночные кавычки, а *строка-литерал* — это последовательность символов, заключенная в двойные кавычки. Если для инициализации переменной String^ используется литерал, компилятор предполагает, что литерал состоит из символов `char16` . Таким образом, нет необходимости указывать перед литералом модификатор строки "L" или заключать литерал в макрос **_T()** или **TEXT()** . Дополнительные сведения о поддержке Юникода в C++ см. в разделах [Unicode Programming Summary](../text/unicode-programming-summary.md).

В следующем примере показаны различные способы создания объектов `String` .

[!code-cpp[cx_strings#01](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#01)]

## <a name="string-handling-operations"></a>Операции обработки строк

Класс `String` предоставляет методы и операторы для объединения и сравнения строк и других простейших операций со строками. Для более сложных манипуляций со строками используйте функцию-член `String::Data()` для получения значения объекта `String^` в виде объекта `const wchar_t*`. Затем с помощью этого значения инициализируйте класс `std::wstring`, имеющий более богатый набор функций по обработке строк.

[!code-cpp[cx_strings#03](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#03)]

## <a name="string-conversions"></a>Преобразование строк

Объект `Platform::String` может содержать только символы `char16` или символ `NULL` . Если приложение должно работать с 8-разрядными символами, используйте [String::Data](../cppcx/platform-string-class.md#data) для извлечения текста в качестве `const wchar_t*`. Затем можно воспользоваться соответствующими функциям Windows или стандартной библиотеки для выполнения операций с данными и преобразовать их обратно в объект `wchar_t*` или [wstring](../standard-library/basic-string-class.md), из которого можно создать новый объект `Platform::String`.

В приведенном ниже фрагменте кода демонстрируется, как преобразовать переменную `String^` в переменную `wstring` и обратно. Дополнительные сведения об операциях со строками, используемых в этом примере, см. в разделе [basic_string::replace](../standard-library/basic-string-class.md#replace).

[!code-cpp[cx_strings#04](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#04)]

## <a name="string-length-and-embedded-null-values"></a>Длина строки и значения NULL внутри строк

[String::Length](../cppcx/platform-string-class.md#length) возвращает количество символов в строке, а не количество байтов. Символ NULL, означающий конец строки, не учитывается, если вы не указали обратное при создании строки с помощью семантики стека.

Объект `Platform::String` может содержать значения NULL внутри строки, но только если они получены в результате операции объединения. Значения NULL внутри строки не поддерживаются в строковых литералах, поэтому из нельзя использовать для инициализации объектов `Platform::String`таким способом. Значения NULL в объектах `Platform::String` игнорируются при отображении строки, например когда она присваивается свойству `TextBlock::Text` . Когда строковое значение возвращается свойством `Data` , значения NULL внутри строки удаляются.

## <a name="stringreference"></a>StringReference

В некоторых случаях код (a) получает std::wstring или строку wchar_t или L»» строка литерала и просто передает их в другой метод, который принимает строку ^ в качестве входного параметра. Если исходный строковый буфер остается допустимым и не изменяется до возвращения результата функцией, строку `wchar_t*` или строковый литерал можно преобразовать в [Platform::StringReference](../cppcx/platform-stringreference-class.md), а затем передать вместо `Platform::String^`. Это допустимо, поскольку в `StringReference` имеется определенное пользователем преобразование в тип `Platform::String^`. Благодаря `StringReference` можно избежать создания дополнительной копии строковых данных. В циклах, включающих передачу большого количества строк или передачу очень длинных строк, с помощью `StringReference`можно теоретически добиться значительного выигрыша в производительности. Но поскольку `StringReference` фактически занимает исходный строковый буфер, необходимо соблюдать осторожность, чтобы не повредить память. Не следует передавать `StringReference` в асинхронный метод, если нет гарантии, что исходная строка будет находиться в области видимости, когда выполнение метода закончится. При инициализации String^ из StringReference происходит принудительное выделение памяти и копирование содержимого строки, если имеется второй оператор присваивания. В этом случае выигрыш в производительности `StringReference`теряется.

Обратите внимание, что `StringReference` является типом класса стандартного языка C++, а не ссылочным классом; его нельзя использовать в определяемых пользователем открытых интерфейсах ссылочных классов.

В следующем примере показано, как использовать StringReference.

```
void GetDecodedStrings(std::vector<std::wstring> strings)
{
    using namespace Windows::Security::Cryptography;
    using namespace Windows::Storage::Streams;

    for (auto&& s : strings)
    {
        // Method signature is IBuffer^ CryptographicBuffer::DecodeFromBase64String (Platform::String^)
        // Call using StringReference:
        IBuffer^ buffer = CryptographicBuffer::DecodeFromBase64String(StringReference(s.c_str()));

        //...do something with buffer
    }
}
```
