---
title: Предупреждение компилятора (уровень 1) C4470
ms.date: 11/04/2016
f1_keywords:
- C4470
helpviewer_keywords:
- C4470
ms.assetid: f52a3eaa-a235-4747-a47d-9ec4ad4cb0ea
ms.openlocfilehash: dc1efad7f18310727e2fdb756e49b95294357c4d
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965412"
---
# <a name="compiler-warning-level-1-c4470"></a>Предупреждение компилятора (уровень 1) C4470

контрольные точки pragma с плавающей запятой игнорируются в/CLR

Директивы pragma элемента управления float:

- [fenv_access](../../preprocessor/fenv-access.md)

- [float_control](../../preprocessor/float-control.md)

- [fp_contract](../../preprocessor/fp-contract.md)

не оказывает влияния на [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

Следующий пример приводит к возникновению ошибки C4470:

```cpp
// C4470.cpp
// compile with: /clr /W1 /LD
#pragma float_control(except, on)   // C4470
```