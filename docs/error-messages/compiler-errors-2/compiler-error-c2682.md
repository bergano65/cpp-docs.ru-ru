---
title: Ошибка компилятора C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: c1ce0132ed0db418359effe60f59e1eb2d3cc221
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760287"
---
# <a name="compiler-error-c2682"></a>Ошибка компилятора C2682

невозможно использовать casting_operator для преобразования из "тип1" в "тип2"

Оператор приведения попытался выполнить преобразование между несовместимыми типами. Например, оператор [dynamic_cast](../../cpp/dynamic-cast-operator.md) нельзя использовать для преобразования указателя в ссылку. Оператор `dynamic_cast` нельзя использовать для приведения квалификаторов. Все квалификаторы типов должны совпадать.

Оператор `const_cast` можно использовать для удаления таких атрибутов, как `const`, `volatile`или `__unaligned`.

Следующий пример приводит к возникновению ошибки C2682:

```cpp
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

Следующий пример приводит к возникновению ошибки C2682:

```cpp
// C2682b.cpp
// compile with: /clr
ref struct R{};
ref struct RR : public R{};
ref struct H {
   RR^ r ;
   short s;
   int i;
};

int main() {
   H^ h = gcnew H();
   interior_ptr<int>lr = &(h->i);
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK
}
```
