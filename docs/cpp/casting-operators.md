---
title: Операторы приведения
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: e2ac8e9079b1d30dca077363bbb6cef35960902e
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345102"
---
# <a name="casting-operators"></a>Операторы приведения

Некоторые операторы приведения типа используются только в языке C++. Эти операторы позволяют устранить неоднозначность и возможности допустить ошибку, которые характеры для приведения типов в стиле языка C. Эти операторы перечислены ниже.

- [dynamic_cast](../cpp/dynamic-cast-operator.md) используется для преобразования полиморфных типов.

- [static_cast](../cpp/static-cast-operator.md) используется для преобразования неполиморфных типов.

- [const_cast](../cpp/const-cast-operator.md) используется для удаления **const**, **volatile**, и **__unaligned** атрибуты.

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) для простой повторной интерпретации разрядов.

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) используется в C++выполняет для создания проверяемых MSIL.

Используйте **const_cast** и **reinterpret_cast** в качестве последнего средства, так как же опасностях как приведения старого стиля представления этих операторов. Однако они необходимы, чтобы полностью заменить приведения старого стиля.

## <a name="see-also"></a>См. также

[Приведение](../cpp/casting.md)