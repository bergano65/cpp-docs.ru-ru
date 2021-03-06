---
title: Прагма pointers_to_members
ms.date: 08/29/2019
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
ms.openlocfilehash: 6058e3e4855eb745a01410e31eb9f454ef131ab1
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821412"
---
# <a name="pointers_to_members-pragma"></a>Прагма pointers_to_members

**C++Зависящ**

Указывает, можно ли объявить указатель на член класса до определения связанного класса. Используется для управления размером указателя и кодом, необходимым для интерпретации указателя.

## <a name="syntax"></a>Синтаксис

> **#pragma pointers_to_members (** *указатель-объявление* [ **,** *большинство-общие-представление* ])

## <a name="remarks"></a>Заметки

**Pointers_to_membersную** директиву pragma можно поместить в исходный файл в качестве альтернативы использованию параметров компилятора [/VMB или/vmg](../build/reference/vmb-vmg-representation-method.md) или [ключевых слов наследования](../cpp/inheritance-keywords.md).

Аргумент *объявления указателя* указывает, был ли объявлен указатель на член до или после определения связанной функции. Аргумент *объявления указателя* является одним из следующих двух символов:

| Аргумент | Comments |
|--------------|--------------|
| **full_generality** | Создает безопасный, но не всегда оптимальный код. **Full_generality** используется, если любой указатель на член объявляется перед связанным определением класса. Этот аргумент всегда использует представление указателя, указанное в аргументе *наиболее общего представления* . Эквивалентен /vmg. |
| **best_case** | Создает безопасный, оптимальный код с использованием наилучшего представления всех указателей на элементы. Требует определения класса перед объявлением указателя на член класса. Значение по умолчанию — **best_case**. |

*Наиболее общий аргумент представления* указывает наименьшее представление указателя, которое компилятор может безопасно использовать для ссылки на любой указатель на член класса в записи преобразования. Аргумент может принимать одно из следующих значений:

| Аргумент | Comments |
|--------------|--------------|
| **single_inheritance** | Наиболее общее представление является указателем на функцию-член с единичным наследованием. Вызывает ошибку, если модель наследования определения класса, для которой объявлен указатель на член класса, является множественной или виртуальной. |
| **multiple_inheritance** | Наиболее общее представление является указателем на функцию-член с множественным наследованием. Вызывает ошибку, если модель наследования определения класса, для которой объявлен указатель на элемент, является виртуальной. |
| **virtual_inheritance** | Наиболее общее представление является указателем на функцию-член с виртуальным наследованием. Никогда не вызывает ошибку. **virtual_inheritance** является аргументом по умолчанию при использовании `#pragma pointers_to_members(full_generality)`. |

> [!CAUTION]
> Рекомендуется поместить директиву pragma **pointers_to_members** только в файл исходного кода, который требуется изменить, и только после любой директивы `#include`. Такой подход уменьшает риск влияния директивы pragma на другие файлы и случайного указания нескольких определений для одной переменной, функции или имени класса.

## <a name="example"></a>Пример

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**КОНЕЦ C++ конкретного**

## <a name="see-also"></a>См. также:

[Директивы pragma и ключевое слово __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
