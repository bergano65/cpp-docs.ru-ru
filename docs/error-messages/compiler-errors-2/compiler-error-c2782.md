---
title: Ошибка компилятора C2782
ms.date: 11/04/2016
f1_keywords:
- C2782
helpviewer_keywords:
- C2782
ms.assetid: 8b685422-294d-4f64-9f3d-c14eaf03a93d
ms.openlocfilehash: c779a9789f532a5d623401058b9ea7e268ede17d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739731"
---
# <a name="compiler-error-c2782"></a>Ошибка компилятора C2782

"объявление": параметр шаблона "идентификатор" неоднозначен

Компилятор не может определить тип аргумента шаблона.

Следующий пример приводит к возникновению ошибки C2782:

```cpp
// C2782.cpp
template<typename T>
void f(T, T) {}

int main() {
   f(1, 'c');   // C2782
   // try the following line instead
   // f<int>(1, 'c');
}
```

C2782 также может возникать при использовании универсальных шаблонов:

```cpp
// C2782b.cpp
// compile with: /clr
generic<typename T> void gf(T, T) { }

int main() {
   gf(1, 'c'); // C2782
   // try the following line instead
   // gf<int>(1, 'c');
}
```
