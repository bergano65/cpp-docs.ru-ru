---
title: Предупреждение компилятора (уровень 1) C4228
ms.date: 11/04/2016
f1_keywords:
- C4228
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
ms.openlocfilehash: 75bd34a4338db7a430c1951d5bc3bd61dbce4f64
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627264"
---
# <a name="compiler-warning-level-1-c4228"></a>Предупреждение компилятора (уровень 1) C4228

нестандартное расширение: квалификаторы после запятой в списке деклараторов игнорируются

Использование квалификаторов, таких как **const** или `volatile` после запятой при объявлении переменных, является расширением Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Пример

```cpp
// C4228.cpp
// compile with: /W1
int j, const i = 0;  // C4228
int k;
int const m = 0;  // ok
int main()
{
}
```