---
title: Предупреждение компилятора (уровень 4) C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: 1ec3e64548cead53cea906cdf2abd3dd25ee06d4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991387"
---
# <a name="compiler-warning-level-4-c4256"></a>Предупреждение компилятора (уровень 4) C4256

"функция": конструктор для класса с виртуальными базовыми базами имеет "..."; вызовы могут быть несовместимы с более старыми версиями VisualC++

Возможна несовместимость.

Рассмотрим следующий пример программного кода: Если определение конструктора S2:: S2 (int i,...) было скомпилировано с помощью версии компилятора Майкрософт C++ до версии 7, но следующий пример компилируется с использованием текущей версии, вызов конструктора для S3 будет работать неправильно из-за изменения соглашения о вызове специального варианта. Если оба были скомпилированы с помощью C++ Visual 6,0, вызов будет работать неверно, если для многоточия не было передано ни одного параметра.

Чтобы устранить это предупреждение,

1. Не используйте многоточие в конструкторе.

1. Убедитесь, что все компоненты в проекте построены с текущей версией (включая все библиотеки, которые могут определять этот класс или ссылаться на него), а затем отключите предупреждение с помощью директивы pragma [warning](../../preprocessor/warning.md) .

Следующий пример приводит к возникновению ошибки C4256:

```cpp
// C4256.cpp
// compile with: /W4
// #pragma warning(disable : 4256)
struct S1
{
};

struct S2: virtual public S1
{
   S2( int i, ... )    // C4256
   {
      i = 0;
   }
   /*
   // try the following line instead
   S2( int i)
   {
      i = 0;
   }
   */
};

void func1()
{
   S2 S3( 2, 1, 2 );   // C4256
   // try the following line instead
   // S2 S3( 2 );
}

int main()
{
}
```
