---
title: Ошибка компилятора C2529
ms.date: 11/04/2016
f1_keywords:
- C2529
helpviewer_keywords:
- C2529
ms.assetid: 73a99e55-b91e-488d-9b72-cc80faaeb436
ms.openlocfilehash: f5a10131fe03bd98078e87f71d07bf02c51d34f4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760417"
---
# <a name="compiler-error-c2529"></a>Ошибка компилятора C2529

"имя": ссылка на ссылку недопустима

Эта ошибка может быть исправлена с помощью синтаксиса указателя и объявления ссылки на указатель.

Следующий пример приводит к возникновению ошибки C2529:

```cpp
// C2529.cpp
// compile with: /c
int i;
int &ri = i;
int &(&rri) = ri;   // C2529
```
