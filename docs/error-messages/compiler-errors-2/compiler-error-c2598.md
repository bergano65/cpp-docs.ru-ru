---
title: Ошибка компилятора C2598
ms.date: 11/04/2016
f1_keywords:
- C2598
helpviewer_keywords:
- C2598
ms.assetid: 40777c62-39ba-441e-b081-f49f94b43547
ms.openlocfilehash: a1ad34d454c5dc80feaac1df1383854391100ab0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759325"
---
# <a name="compiler-error-c2598"></a>Ошибка компилятора C2598

спецификация компоновки должна быть в глобальной области видимости

Описатель компоновки объявлен в локальной области видимости.

Следующий пример приводит к возникновению ошибки C2598:

```cpp
// C2598.cpp
// compile with: /c
void func() {
   extern "C" int func2();   // C2598
}

extern "C" int func( int i );
```
