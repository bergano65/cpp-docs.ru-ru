---
title: Ошибка компилятора C2423
ms.date: 11/04/2016
f1_keywords:
- C2423
helpviewer_keywords:
- C2423
ms.assetid: 8797fb8b-b58b-4add-b6e6-2a9a3cd9084d
ms.openlocfilehash: 29203d3816f82bce95be656fdf71cb6536b325b9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744671"
---
# <a name="compiler-error-c2423"></a>Ошибка компилятора C2423

"число": недопустимый масштаб

Для масштабирования регистра в встроенном коде ассемблера используется число, отличное от 1, 2, 4 или 8.

Следующий пример приводит к возникновению ошибки C2423:

```cpp
// C2423.cpp
// processor: x86
int main() {
   _asm {
      lea EAX, [EAX*3]   // C2423
      lea EAX, [EAX+EAX*2]   // OK
   }
}
```
