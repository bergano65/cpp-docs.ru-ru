---
title: Класс CStringRefElementTraits
ms.date: 11/04/2016
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
ms.openlocfilehash: c57fda64689a80dfa548977e56b0416641bb4360
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277413"
---
# <a name="cstringrefelementtraits-class"></a>Класс CStringRefElementTraits

Этот класс предоставляет статические функции, связанные с строк, которые хранятся в объектах класса коллекции. Объекты-строки обрабатываются как ссылки.

## <a name="syntax"></a>Синтаксис

```
template <typename T>
class CStringRefElementTraits : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Параметры

*T*<br/>
Тип данных, хранимых в коллекции.

## <a name="members"></a>Участники

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[CStringRefElementTraits::CompareElements](#compareelements)|Вызовите эту статическую функцию для сравнения двух строковых элементов на предмет равенства.|
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|Вызовите эту статическую функцию для сравнения двух элементов строки.|
|[CStringRefElementTraits::Hash](#hash)|Вызовите эту статическую функция для вычисления хэш-значение для заданной строки элемента.|

## <a name="remarks"></a>Примечания

Этот класс предоставляет статические функции для сравнения строк, а также для создания хэш-значение. Эти функции полезны при использовании класса коллекции для хранения строковых данных. В отличие от [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) и [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md), `CStringRefElementTraits` вызывает `CString` аргументы нельзя передать как **const** `CString&` ссылки.

Дополнительные сведения см. в разделе [классы коллекций ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>Требования

**Заголовок:** atlcoll.h

##  <a name="compareelements"></a>  CStringRefElementTraits::CompareElements

Вызовите эту статическую функцию для сравнения двух строковых элементов на предмет равенства.

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>Параметры

*element1*<br/>
Первая строка, элемент.

*элемент элемент2*<br/>
Вторая строка элемента.

### <a name="return-value"></a>Возвращаемое значение

Возвращает значение true, если элементы равны; значение false в противном случае.

##  <a name="compareelementsordered"></a>  CStringRefElementTraits::CompareElementsOrdered

Вызовите эту статическую функцию для сравнения двух элементов строки.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Параметры

*str1*<br/>
Первая строка, элемент.

*str2*<br/>
Вторая строка элемента.

### <a name="return-value"></a>Возвращаемое значение

Нуль, если строки идентичны, < 0 Если *str1* — меньше, чем *str2*, или > 0 Если *str1* больше, чем *str2*. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) метод используется для выполнения сравнений.

##  <a name="hash"></a>  CStringRefElementTraits::Hash

Вызовите эту статическую функция для вычисления хэш-значение для заданной строки элемента.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Параметры

*str*<br/>
Элемент строку.

### <a name="return-value"></a>Возвращаемое значение

Возвращает хэш-значение, вычисляемое с использованием содержимого строки.

## <a name="see-also"></a>См. также

[Класс CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Общие сведения о классе](../../atl/atl-class-overview.md)
