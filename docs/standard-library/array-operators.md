---
title: Операторы &lt;array&gt;
ms.date: 11/04/2016
f1_keywords:
- array/std::array::operator!=
- array/std::array::operator<
- array/std::array::operator<=
- array/std::array::operator>
- array/std::array::operator>=
- array/std::array::operator==
ms.assetid: c8f46282-f179-4909-9a01-639cb8e18c27
ms.openlocfilehash: 3d65cd6b6b8549fd9964f6c5bb6d8b2d3c0a27b6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427305"
---
# <a name="ltarraygt-operators"></a>Операторы &lt;array&gt;

Заголовок **> массива \<содержит следующие функции** шаблона сравнения, не являющиеся элементами.

||||
|-|-|-|
|[operator!=](#op_neq)|[оператор&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[оператор&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator!=

Сравнение массивов на неравенство.

```cpp
template <Ty, std::size_t N>
bool operator!=(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Параметры

*Ty*\
Тип элемента.

*N*\
Размер массива.

*left*\
Левый контейнер для сравнения.

*справа*\
Правый контейнер для сравнения.

### <a name="remarks"></a>Remarks

Функция-шаблон возвращает `!(left == right)`.

### <a name="example"></a>Пример

```cpp
// std__array__operator_ne.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};

// display contents " 4 5 6 7"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 != c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 != c1);
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 5 6 7
false
true
```

## <a name="op_lt"></a> operator&lt;

Сравнение массивов "меньше, чем".

```cpp
template <Ty, std::size_t N>
bool operator<(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Параметры

*Ty*\
Тип элемента.

*N*\
Размер массива.

*left*\
Левый контейнер для сравнения.

*справа*\
Правый контейнер для сравнения.

### <a name="remarks"></a>Remarks

Функция шаблона перегружает `operator<` для сравнения двух объектов [класса массива](../standard-library/array-class-stl.md)шаблонов класса. Функция возвращает `lexicographical_compare(left.begin(), left.end(), right.begin())`.

### <a name="example"></a>Пример

```cpp
// std__array__operator_lt.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};

// display contents " 4 5 6 7"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 < c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 < c1);
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 5 6 7
false
true
```

## <a name="op_lt_eq"></a>  operator&lt;=

Сравнение массивов "меньше или равно".

```cpp
template <Ty, std::size_t N>
bool operator<=(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Параметры

*Ty*\
Тип элемента.

*N*\
Размер массива.

*left*\
Левый контейнер для сравнения.

*справа*\
Правый контейнер для сравнения.

### <a name="remarks"></a>Remarks

Функция-шаблон возвращает `!(right < left)`.

### <a name="example"></a>Пример

```cpp
// std__array__operator_le.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};

// display contents " 4 5 6 7"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 <= c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c1 <= c0);
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 5 6 7
true
false
```

## <a name="op_eq_eq"></a> operator==

Сравнение массивов на равенство.

```cpp
template <Ty, std::size_t N>
bool operator==(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Параметры

*Ty*\
Тип элемента.

*N*\
Размер массива.

*left*\
Левый контейнер для сравнения.

*справа*\
Правый контейнер для сравнения.

### <a name="remarks"></a>Remarks

Функция шаблона перегружает `operator==` для сравнения двух объектов [класса массива](../standard-library/array-class-stl.md)шаблонов класса. Функция возвращает `equal(left.begin(), left.end(), right.begin())`.

### <a name="example"></a>Пример

```cpp
// std__array__operator_eq.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};

// display contents " 4 5 6 7"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 == c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 == c1);
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 5 6 7
true
false
```

## <a name="op_gt"></a> operator&gt;

Сравнение массивов "больше, чем".

```cpp
template <Ty, std::size_t N>
bool operator>(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Параметры

*Ty*\
Тип элемента.

*N*\
Размер массива.

*left*\
Левый контейнер для сравнения.

*справа*\
Правый контейнер для сравнения.

### <a name="remarks"></a>Remarks

Функция-шаблон возвращает `(right < left)`.

### <a name="example"></a>Пример

```cpp
// std__array__operator_gt.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};

// display contents " 4 5 6 7"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 > c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c1 > c0);
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 5 6 7
false
true
```

## <a name="op_gt_eq"></a>  operator&gt;=

Сравнение массивов "больше или равно".

```cpp
template <Ty, std::size_t N>
bool operator>=(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Параметры

*Ty*\
Тип элемента.

*N*\
Размер массива.

*left*\
Левый контейнер для сравнения.

*справа*\
Правый контейнер для сравнения.

### <a name="remarks"></a>Remarks

Функция-шаблон возвращает `!(left < right)`.

### <a name="example"></a>Пример

```cpp
// std__array__operator_ge.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};

// display contents " 4 5 6 7"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 >= c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 >= c1);
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 5 6 7
true
false
```

## <a name="see-also"></a>См. также раздел

[\<array>](../standard-library/array.md)
