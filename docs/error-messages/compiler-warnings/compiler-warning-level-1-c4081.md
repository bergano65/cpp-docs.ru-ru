---
title: Предупреждение компилятора (уровень 1) C4081
ms.date: 11/04/2016
f1_keywords:
- C4081
helpviewer_keywords:
- C4081
ms.assetid: 6f656373-a080-4989-bbc9-e2f894b03293
ms.openlocfilehash: 39b2c7b117f2040d68e42dd6cca37942c11bf0da
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626948"
---
# <a name="compiler-warning-level-1-c4081"></a>Предупреждение компилятора (уровень 1) C4081

требуется "токен1"; обнаружено "токен2"

Компилятору в данном контексте требуется другой токен.

## <a name="example"></a>Пример

```cpp
// C4081.cpp
// compile with: /W1 /LD
#pragma optimize) "l", on )   // C4081
```