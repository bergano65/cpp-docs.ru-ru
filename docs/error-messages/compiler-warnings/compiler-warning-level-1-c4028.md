---
title: Предупреждение компилятора (уровень 1) C4028
ms.date: 11/04/2016
f1_keywords:
- C4028
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
ms.openlocfilehash: 19bfd2659ee9017d3a304dee2d647da091515876
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623851"
---
# <a name="compiler-warning-level-1-c4028"></a>Предупреждение компилятора (уровень 1) C4028

формальный параметр "число" отличается от объявления

Тип формального параметра не согласуется с соответствующим параметром в объявлении. Используется тип в исходном объявлении.

Это предупреждение допустимо только для исходного кода на языке C.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C4028.

```c
// C4028.c
// compile with: /W1 /Za
void f(int , ...);
void f(int i, int j) {}   // C4028

void g(int , int);
void g(int i, int j) {}   // OK

int main() {}
```