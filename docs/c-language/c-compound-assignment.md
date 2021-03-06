---
title: Составное назначение C
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
ms.openlocfilehash: 39a9391e2a62a59c5e7fd7937c1f3d12509b76ad
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148768"
---
# <a name="c-compound-assignment"></a>Составное назначение C

Составные операторы присваивания объединяют оператор простого присваивания с другим бинарным оператором. Составные операторы присваивания выполняют операцию, заданную дополнительными оператором, затем присваивают результат левому операнду. Например, составное выражение присваивания

> *expression1* **+=** *expression2*

можно понимать как

> *expression1* **=** *expression1* **+** *expression2*

Но составной оператор присваивания не эквивалентен своей развернутой версии, так как в составном операторе присваивания выражение *выражение1* вычисляется только один раз, а в развернутой версии выражение *выражение1* вычисляется дважды: в операции сложения и в операции присваивания.

Операнды составного оператора присваивания должны быть целочисленного типа или типа с плавающей запятой. Каждый составной оператор присваивания выполняет те же преобразования, что и соответствующий бинарный оператор, и соответственно ограничивает типы своих операндов. Левый операнд операторов сложения с присваиванием (`+=`) и вычитания с присваиванием (**-=**) может иметь тип указателя, при этом правый операнд должен быть целочисленного типа. Результат составной операции присваивания имеет значение и тип левого операнда.

```C
#define MASK 0xff00

n &= MASK;
```

В этом примере операция побитового включающего AND выполняется для `n` и `MASK`, а результат присваивается переменной `n`. Константа манифеста `MASK` определяется с помощью директивы препроцессора [#define](../preprocessor/hash-define-directive-c-cpp.md).

## <a name="see-also"></a>См. также

[Операторы присваивания C](../c-language/c-assignment-operators.md)
