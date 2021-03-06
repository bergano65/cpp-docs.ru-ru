---
title: Класс concurrent_priority_queue
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::clear
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::empty
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::get_allocator
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::push
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::size
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::swap
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::try_pop
helpviewer_keywords:
- concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
ms.openlocfilehash: 1d8651d1391ded2970a00a7429c36f341a438659
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143218"
---
# <a name="concurrent_priority_queue-class"></a>Класс concurrent_priority_queue

Класс `concurrent_priority_queue` — это контейнер, который позволяет нескольким потокам параллельно помещать и извлекать элементы. Элементы извлекаются в порядке приоритета, определяемого функтором, предоставленным в качестве аргумента шаблона.

## <a name="syntax"></a>Синтаксис

```cpp
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

### <a name="parameters"></a>Параметры

*T*<br/>
Тип данных элементов, хранимых в очереди с приоритетом.

*_Compare*<br/>
Тип объекта функции, который может сравнивать значения двух элементов в качестве ключей сортировки для определения их относительного порядка в очереди с приоритетом. Этот аргумент является необязательным, и в качестве значения по умолчанию используется бинарный предикат `less<T>`.

*_Ax*<br/>
Тип, представляющий хранимый объект распределителя, инкапсулирующий сведения о распределении и освобождении памяти для параллельной очереди с приоритетом. Этот аргумент является необязательным, и значением по умолчанию является `allocator<T>`.

## <a name="members"></a>Члены

### <a name="public-typedefs"></a>Общедоступные определения типов

|Имя|Description|
|----------|-----------------|
|`allocator_type`|Тип, представляющий класс распределителя для параллельной очереди с приоритетом.|
|`const_reference`|Тип, представляющий константную ссылку на элемент типа, хранящийся в параллельной очереди с приоритетом.|
|`reference`|Тип, представляющий ссылку на элемент типа, хранящийся в параллельной очереди с приоритетом.|
|`size_type`|Тип, который подсчитывает число элементов в параллельной очереди с приоритетом.|
|`value_type`|Тип, представляющий тип данных, хранящихся в параллельной очереди с приоритетом.|

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Description|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|Перегружен. Создает параллельную очередь с приоритетом.|

### <a name="public-methods"></a>Открытые методы

|Имя|Description|
|----------|-----------------|
|[пусто](#clear)|Удаляет все элементы в параллельной очереди с приоритетом. Этот метод не является типобезопасным в режиме параллелизма.|
|[empty](#empty)|Проверяет, пуста ли параллельная очередь с приоритетом в момент, когда этот метод вызывается. Этот метод является типобезопасным в режиме параллелизма.|
|[get_allocator](#get_allocator)|Возвращает копию распределителя, используемого для создания параллельной очереди с приоритетом. Этот метод является типобезопасным в режиме параллелизма.|
|[push](#push)|Перегружен. Добавляет элемент в параллельную очередь с приоритетом. Этот метод является типобезопасным в режиме параллелизма.|
|[size](#size)|Возвращает число элементов в параллельной очереди с приоритетом. Этот метод является типобезопасным в режиме параллелизма.|
|[swap](#swap)|Меняет местами содержимое двух параллельных очередей с приоритетом. Этот метод не является типобезопасным в режиме параллелизма.|
|[try_pop](#try_pop)|Удаляет и возвращает элемент наивысшего приоритета из очереди, если очередь не пуста. Этот метод является типобезопасным в режиме параллелизма.|

### <a name="public-operators"></a>Открытые операторы

|Имя|Description|
|----------|-----------------|
|[оператор=](#operator_eq)|Перегружен. Присваивает этому элементу содержимое другого объекта `concurrent_priority_queue`. Этот метод не является типобезопасным в режиме параллелизма.|

## <a name="remarks"></a>Remarks

Подробные сведения о классе `concurrent_priority_queue` см. в разделе [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`concurrent_priority_queue`

## <a name="requirements"></a>Требования

**Заголовок:** concurrent_priority_queue. h

**Пространство имен:** concurrency

## <a name="clear"></a>открытым

Удаляет все элементы в параллельной очереди с приоритетом. Этот метод не является типобезопасным в режиме параллелизма.

```cpp
void clear();
```

### <a name="remarks"></a>Remarks

`clear` не является типобезопасным. Необходимо убедиться, что никакие другие потоки не вызывают методы в очереди параллельных приоритетов при вызове этого метода. `clear` не освобождает память.

## <a name="ctor"></a>concurrent_priority_queue

Создает параллельную очередь с приоритетом.

```cpp
explicit concurrent_priority_queue(
    const allocator_type& _Al = allocator_type());

explicit concurrent_priority_queue(
    size_type _Init_capacity,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_priority_queue(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());

concurrent_priority_queue(
    const concurrent_priority_queue& _Src);

concurrent_priority_queue(
    const concurrent_priority_queue& _Src,
    const allocator_type& _Al);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src,
    const allocator_type& _Al);
```

### <a name="parameters"></a>Параметры

*_InputIterator*<br/>
Тип итератора ввода.

*_Al*<br/>
Класс распределителя для использования с данным объектом.

*_Init_capacity*<br/>
Начальная производительность объекта `concurrent_priority_queue`.

*_Begin*<br/>
Положение первого элемента в диапазоне копируемых элементов.

*_End*<br/>
Положение первого элемента после диапазона копируемых элементов.

*_Src*<br/>
Исходный объект `concurrent_priority_queue` для копирования или перемещения элементов.

### <a name="remarks"></a>Remarks

Все конструкторы хранят объект распределителя `_Al` и инициализируют очередь приоритетов.

Первый конструктор указывает пустую очередь начального приоритета и при необходимости задает распределитель.

Второй конструктор указывает очередь приоритетов с начальной емкостью `_Init_capacity` и при необходимости задает распределитель.

Третий конструктор указывает значения, предоставляемые диапазоном итератора [`_Begin`, `_End`), и при необходимости задает распределитель.

Четвертый и пятый конструкторы указывают копию `_Src`очереди приоритета.

Шестой и седьмой конструкторы указывают на перемещение `_Src`очереди приоритета.

## <a name="empty"></a>указано

Проверяет, пуста ли параллельная очередь с приоритетом в момент, когда этот метод вызывается. Этот метод является типобезопасным в режиме параллелизма.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Возвращаемое значение

**значение true** , если очередь приоритетов была пустой в момент вызова функции; в противном случае — **значение false** .

## <a name="get_allocator"></a>get_allocator

Возвращает копию распределителя, используемого для создания параллельной очереди с приоритетом. Этот метод является типобезопасным в режиме параллелизма.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Возвращаемое значение

Копия распределителя, используемая для создания объекта `concurrent_priority_queue`.

## <a name="operator_eq"></a>Оператор =

Присваивает этому элементу содержимое другого объекта `concurrent_priority_queue`. Этот метод не является типобезопасным в режиме параллелизма.

```cpp
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>Параметры

*_Src*<br/>
Исходный объект `concurrent_priority_queue`.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на этот объект `concurrent_priority_queue`.

## <a name="push"></a>распространение

Добавляет элемент в параллельную очередь с приоритетом. Этот метод является типобезопасным в режиме параллелизма.

```cpp
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>Параметры

*_Elem*<br/>
Элемент, добавляемый в очередь параллельных приоритетов.

## <a name="size"></a>изменять

Возвращает число элементов в параллельной очереди с приоритетом. Этот метод является типобезопасным в режиме параллелизма.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Возвращаемое значение

Число элементов в этом `concurrent_priority_queue` объекте.

### <a name="remarks"></a>Remarks

Возвращаемый размер гарантированно включает все элементы, добавленные вызовами функции `push`. Однако он может не отражать результаты ожидающих параллельных операций.

## <a name="swap"></a>позиции

Меняет местами содержимое двух параллельных очередей с приоритетом. Этот метод не является типобезопасным в режиме параллелизма.

```cpp
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>Параметры

*_Queue*<br/>
Объект `concurrent_priority_queue` для обмена содержимым.

## <a name="try_pop"></a>try_pop

Удаляет и возвращает элемент наивысшего приоритета из очереди, если очередь не пуста. Этот метод является типобезопасным в режиме параллелизма.

```cpp
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>Параметры

*_Elem*<br/>
Ссылка на переменную, которая будет заполнена элементом с наивысшим приоритетом, если очередь не пуста.

### <a name="return-value"></a>Возвращаемое значение

значение **true** , если значение было извлечено, и **false** в противном случае.

## <a name="see-also"></a>См. также раздел

[Пространство имен concurrency](concurrency-namespace.md)<br/>
[Параллельные контейнеры и объекты](../../../parallel/concrt/parallel-containers-and-objects.md)
