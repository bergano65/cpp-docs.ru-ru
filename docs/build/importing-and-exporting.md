---
title: Импортирование и экспортирование
ms.date: 05/06/2019
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: 03931f7f128ab0666890bb8e76677db67dda8fc7
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220638"
---
# <a name="importing-and-exporting"></a>Импортирование и экспортирование

Можно импортировать открытые символы в приложение или экспортировать функции из библиотеки DLL с помощью двух методов:

- Использование файла определения модуля (DEF) при построении библиотеки DLL

- Используйте ключевые слова **__declspec(dllimport)** или **__declspec(dllexport)** в определении функции в главном приложении

## <a name="using-a-def-file"></a>С помощью DEF-файла

Файл определения модуля (DEF) — это текстовый файл, содержащий один или несколько операторов модуля, описывающих различные атрибуты библиотеки DLL. Если вы не используете **__declspec(dllimport)** или **__declspec(dllexport)** DEF-файла для экспорта функций библиотеки DLL, необходимой библиотеке DLL.

Можно использовать DEF-файлы для [Импорт в приложение](importing-using-def-files.md) или [Экспорт из библиотеки DLL](exporting-from-a-dll-using-def-files.md).

## <a name="using-declspec"></a>С помощью __declspec

Необходимо использовать **__declspec(dllimport)** для кода для компиляции правильно, но это позволяет компилятору создавать лучший код. Компилятор способен создавать лучший код, так как он может определить наличие функции в библиотеке DLL или нет, который позволяет компилятору создавать код, который пропускает уровень косвенного обращения, обычно может присутствовать в вызов функции, которая библиотеке. Тем не менее, необходимо использовать **__declspec(dllimport)** Импорт переменных, используемых в библиотеке DLL.

В разделе EXPORTS файл .def правильное **__declspec(dllexport)** не является обязательным. **__declspec(dllexport)** был добавлен предоставляют простой способ экспорта функций из файла .exe или .dll без использования DEF-файла.

Формат переносимого исполняемого файла Win32 позволяет свести к минимуму число страниц, предназначенных для отладки импортов. Чтобы сделать это, она помещает все адреса импорта по любой программе, в одном месте, именем таблицы адресов импорта. Благодаря этому загрузчик для изменения только одного или двух страниц при доступе к эти операции.

## <a name="what-do-you-want-to-do"></a>Выберите действие

- [Импорт в приложение](importing-into-an-application-using-declspec-dllimport.md)

- [Экспорт из библиотеки DLL](exporting-from-a-dll.md)

## <a name="see-also"></a>См. также

[Создание библиотек DLL на C/C++ в Visual Studio](dlls-in-visual-cpp.md)
