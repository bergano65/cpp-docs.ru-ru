---
title: Ошибка компилятора C2638
ms.date: 11/04/2016
f1_keywords:
- C2638
helpviewer_keywords:
- C2638
ms.assetid: 9d4275e8-406d-455e-afee-3a37799230e0
ms.openlocfilehash: 6053e9bcf49159e8ceefe9264d30319493c4cf1b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748350"
---
# <a name="compiler-error-c2638"></a>Ошибка компилятора C2638

"идентификатор": недопустимый модификатор __based для указателя на член

Модификатор `__based` нельзя использовать для указателей на члены.

Следующий пример приводит к возникновению ошибки C2638:

```cpp
// C2638.cpp
void *a;

class C {
public:
   int i;
   int j;
   int func();
};
int __based (a) C::* cpi = &C::i;  // C2638
int (__based (a) C::* cpf)() = &C::func; // c2638
```
