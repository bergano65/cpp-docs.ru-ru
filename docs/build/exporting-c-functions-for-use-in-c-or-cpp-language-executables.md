---
title: Экспорт функций на языке C для использования в исполняемых файлах, исходный код которых написан на языке C или C++
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
ms.openlocfilehash: b7ba2ed30615efb3b05e71cecf0ea69898feb8ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273577"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Экспорт функций на языке C для использования в исполняемых файлах, исходный код которых написан на языке C или C++

При наличии функций в библиотеке DLL написанное на C, которое необходимо получить доступ из языка C или C++ языковой модуль следует использовать **__cplusplus** макрос препроцессора, чтобы определить язык, который компилируется и затем объявите их функции с компоновкой C, если используется C++ языковой модуль. Если вы используете этот метод и предоставить файлы заголовка для библиотеки DLL, эти функции могут использоваться пользователями C и C++ без изменения.

В следующем коде показано файл заголовка, который может использоваться клиентскими приложениями C и C++:

```h
// MyCFuncs.h
#ifdef __cplusplus
extern "C" {  // only need to export C interface if
              // used by C++ source code
#endif

__declspec( dllimport ) void MyCFunc();
__declspec( dllimport ) void AnotherCFunc();

#ifdef __cplusplus
}
#endif
```

Если вам необходимо связать функции C для исполняемого файла C++ и файлы заголовков объявление функции не использовали метод выше в файле исходного кода C++, выполните следующую команду, чтобы запретить компилятору выполнять Декорирование имен функций C:

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>Выберите действие

- [Экспорт из DLL с использованием DEF-файлы](exporting-from-a-dll-using-def-files.md)

- [Экспорт из библиотеки DLL с использованием __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Экспорт и импорт с использованием AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Определение подходящего метода экспорта для использования](determining-which-exporting-method-to-use.md)

- [Импорт в приложение с помощью __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Инициализация библиотеки DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Дополнительные сведения

- [Декорированные имена](reference/decorated-names.md)

- [Использование ключевого слова extern для задания компоновки](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>См. также

[Экспорт из библиотеки DLL](exporting-from-a-dll.md)
