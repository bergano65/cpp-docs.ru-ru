---
title: Ошибка компилятора C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: e4952f4702d871ecf1c818b1fc7394e54a1a295f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743891"
---
# <a name="compiler-error-c2464"></a>Ошибка компилятора C2464

"идентификатор": невозможно использовать "New" для выделения ссылки

Идентификатор ссылки был выделен с помощью оператора `new`. Ссылки не являются объектами памяти, поэтому `new` не может возвращать указатель на них. Используйте синтаксис объявления стандартной переменной для объявления ссылки.

Следующий пример приводит к возникновению ошибки C2464:

```cpp
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```
