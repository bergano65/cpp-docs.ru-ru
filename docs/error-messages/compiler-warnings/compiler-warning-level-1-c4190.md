---
title: Компилятор предупреждение (уровень 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 05984594a57878aad8037861a15ac9284ff65192
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386503"
---
# <a name="compiler-warning-level-1-c4190"></a>Компилятор предупреждение (уровень 1) C4190

«идентификатор1» имеет С-компоновка, но возвращаемый тип UDT «идентификатор2», которая несовместима с C

Функции или указатель на функцию имеет тип возвращаемого значения UDT (определяемый пользователем тип, который является класса, структуры, перечисления или объединения) и `extern` компоновка «C». Это допускается если:

- Все вызовы этой функции происходят из C++.

- Определение функции находится в C++.

## <a name="example"></a>Пример

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```