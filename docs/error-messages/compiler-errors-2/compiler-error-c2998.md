---
title: Ошибка компилятора C2998
ms.date: 11/04/2016
f1_keywords:
- C2998
helpviewer_keywords:
- C2998
ms.assetid: 8193d491-b5d9-4477-acb1-cf166889c070
ms.openlocfilehash: 2a9b4190cab9589fbe7419cba7ec94e49bb6d9ba
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742409"
---
# <a name="compiler-error-c2998"></a>Ошибка компилятора C2998

"идентификатор": не может быть определением шаблона

Компилятору не удалось обработать синтаксис, используемый в определении шаблона.

Следующий пример приводит к возникновению ошибки C2998:

```cpp
// C2998.cpp
// compile with: /c
template <class T> int x = 1018; // C2998
```
