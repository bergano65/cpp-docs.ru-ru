---
title: Предупреждение компилятора (уровень 4) C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 3a8f2093e90f8a681d171e19e2b8a066546f8684
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990659"
---
# <a name="compiler-warning-level-4-c4571"></a>Предупреждение компилятора (уровень 4) C4571

Информация: семантика catch (...) изменилась с C++ момента выпуска Visual 7,1; структурированные исключения (SEH) больше не перехватываются

C4571 создается для каждого блока catch (...) при компиляции с параметром **/EHs**.

При компиляции с параметром **/EHs**блок catch (...) не будет перехватывать структурированное исключение (например, деление на ноль, указатель null); блок catch (...) будет перехватывать только явно вызванные C++ исключения.  Дополнительные сведения см. в разделе [Обработка исключений](../../cpp/exception-handling-in-visual-cpp.md).

Это предупреждение отключено по умолчанию.  Включите это предупреждение, чтобы убедиться, что при компиляции с параметром **/EHs** блоки catch (...) не будут перехватывать структурированные исключения.  Подробнее: [Выключенные по умолчанию предупреждения компилятора](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Разрешить C4571 можно одним из следующих способов:

- Скомпилируйте с **/EHa** , если блоки catch (...) все еще нужны для перехвата структурированных исключений.

- Не включайте C4571, если блоки catch (...) не должны перехватывать структурированные исключения, но все равно требуется использовать блоки catch (...).  Структурированные исключения по-прежнему можно перехватывать с помощью ключевых слов обработки структурированных исключений ( **__try**, **__except**и **__finally**).  Но помните, что если скомпилированные деструкторы **/EHs** будут вызываться только при C++ возникновении исключения, а не при возникновении исключения SEH.

- Замените блок catch (...) на блоки catch для конкретных C++ исключений и при необходимости добавьте обработку структурированных C++ исключений вокруг обработки исключений ( **__try**, **__except**и **__finally**).  Дополнительные сведения см. [в разделе структурированная обработка исключений (C/C++)](../../cpp/structured-exception-handling-c-cpp.md) .

Дополнительные сведения см. в разделе [/EH (модель обработки исключений)](../../build/reference/eh-exception-handling-model.md) .

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C4571.

```cpp
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```
