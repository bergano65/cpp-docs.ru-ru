---
title: Ошибка компилятора C3160
ms.date: 11/04/2016
f1_keywords:
- C3160
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
ms.openlocfilehash: 4d6f415c8b3c8275ac45ef4d4313021100d9a833
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755152"
---
# <a name="compiler-error-c3160"></a>Ошибка компилятора C3160

pointer: данные-член управляемого класса или класса WinRT не могут иметь этот тип

Внутренние указатели сборки мусора могут указывать на внутреннюю часть управляемого класса или класса WinRT. Так как они выполняются медленнее, чем указатели на весь объект, и требуют специальной обработки сборщиком мусора, внутренние управляемые указатели нельзя объявлять как члены класса.

Следующий пример приводит к возникновению ошибки C3160:

```cpp
// C3160.cpp
// compile with: /clr
ref struct A {
   // cannot create interior pointers inside a class
   interior_ptr<int> pg;   // C3160
   int g;   // OK
   int* pg2;   // OK
};

int main() {
   interior_ptr<int> pg2;   // OK
}
```
