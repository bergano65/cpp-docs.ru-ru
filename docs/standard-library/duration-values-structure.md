---
title: Структура duration_values
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: ba4b202a5c8c6da742ac884bf58a5b8c55373d14
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454287"
---
# <a name="durationvalues-structure"></a>Структура duration_values

Предоставляет конкретные значения для параметра-шаблона [длительности](../standard-library/duration-class.md) `Rep`.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Участники

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[max](#max)|Статический. Указывает верхний предел для значения типа `Rep`.|
|[min](#min)|Статический. Указывает нижний предел для значения типа `Rep`.|
|[нуль](#zero)|Статический. Возвращает `Rep(0)`.|

## <a name="requirements"></a>Требования

**Заголовок:** \<Chrono >

**Пространство имен:** std::chrono

## <a name="max"></a>  duration_values::max

Статический метод, который возвращает верхнюю границу значений типа `Ref`.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Возвращаемое значение

Фактически возвращает `numeric_limits<Rep>::max()`.

### <a name="remarks"></a>Примечания

Если `Rep` является пользовательским типом, возвращаемое значение должно быть больше [duration_values::zero](#zero).

## <a name="min"></a>  duration_values::min

Статический метод, который возвращает нижнюю границу для значений типа `Ref`.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Возвращаемое значение

Фактически возвращает `numeric_limits<Rep>::lowest()`.

### <a name="remarks"></a>Примечания

Если `Rep` является пользовательским типом, возвращаемое значение должно быть меньше или равно [duration_values::zero](#zero).

## <a name="zero"></a>  duration_values::zero

Возвращает `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Примечания

Если `Rep` является пользовательским типом, возвращаемое значение должно представлять аддитивную бесконечность.

## <a name="see-also"></a>См. также

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
