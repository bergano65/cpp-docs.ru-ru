---
title: Класс function
ms.date: 11/04/2016
f1_keywords:
- functional/std::function
- functional/std::function::result_type
- functional/std::function::assign
- functional/std::function::swap
- functional/std::function::target
- functional/std::function::target_type
- functional/std::function::operator unspecified
- functional/std::function::operator()
helpviewer_keywords:
- std::function [C++]
- std::function [C++], result_type
- std::function [C++], assign
- std::function [C++], swap
- std::function [C++], target
- std::function [C++], target_type
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
ms.openlocfilehash: 432b61c7bc5b7f0e6f82e5bfeca7758c70785774
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689639"
---
# <a name="function-class"></a>Класс function

Программа-оболочка для вызываемого объекта.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Fty>
class function  // Fty of type Ret(T1, T2, ..., TN)
    : public unary_function<T1, Ret>       // when Fty is Ret(T1)
    : public binary_function<T1, T2, Ret>  // when Fty is Ret(T1, T2)
{
public:
    typedef Ret result_type;

    function();
    function(nullptr_t);
    function(const function& right);
    template <class Fty2>
        function(Fty2 fn);
    template <class Fty2, class Alloc>
        function(reference_wrapper<Fty2>, const Alloc& Ax);

    template <class Fty2, class Alloc>
        void assign(Fty2, const Alloc& Ax);
    template <class Fty2, class Alloc>
        void assign(reference_wrapper<Fty2>, const Alloc& Ax);
    function& operator=(nullptr_t);
    function& operator=(const function&);
    template <class Fty2>
        function& operator=(Fty2);
    template <class Fty2>
        function& operator=(reference_wrapper<Fty2>);

    void swap(function&);
    explicit operator bool() const;

    result_type operator()(T1, T2, ....., TN) const;
    const std::type_info& target_type() const;
    template <class Fty2>
        Fty2 *target();

    template <class Fty2>
        const Fty2 *target() const;

    template <class Fty2>
        void operator==(const Fty2&) const = delete;
    template <class Fty2>
        void operator!=(const Fty2&) const = delete;
};
```

### <a name="parameters"></a>Параметры

*Фти* \
Тип функции для заключения в оболочку.

@No__t_1 *AX*
Функция распределителя.

## <a name="remarks"></a>Заметки

Шаблон класса — это обертка вызова, сигнатура вызова которого `Ret(T1, T2, ..., TN)`. Они позволяют заключить в универсальную оболочку различные вызываемые объекты.

Некоторые функции-члены принимают операнд с именем нужного целевого объекта. Такой операнд можно задать несколькими способами:

`fn` — вызываемый объект `fn`; после вызова объект `function` содержит копию `fn`;

`fnref` — вызываемый объект, который именует `fnref.get()`; после вызова объект `function` содержит ссылку на `fnref.get()`;

`right` — вызываемый объект, при наличии, который содержится в объекте `function` `right`;

`npc` — указатель null; после вызова объект `function` пуст.

Во всех случаях `INVOKE(f, t1, t2, ..., tN)`, где `f` — вызываемый объект, а `t1, t2, ..., tN` — значения lvalue типов `T1, T2, ..., TN` соответственно, должен иметь правильный формат и, если `Ret` не void, преобразуется в `Ret`.

Пустой объект `function` не содержит вызываемый объект или ссылку на вызываемый объект.

## <a name="members"></a>Члены

### <a name="constructors"></a>Конструкторы

|||
|-|-|
|[function](#function)|Создает оболочку, которая является пустой или содержит вызываемый объект произвольного типа с фиксированной сигнатурой.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[result_type](#result_type)|Возвращаемый тип хранимого вызываемого объекта.|

### <a name="functions"></a>Функции

|||
|-|-|
|[assign](#assign)|Присваивает вызываемый объект данному объекту функции.|
|[swap](#swap)|Меняет местами два вызываемых объекта.|
|[target](#target)|Проверяет, является ли вызываемый объект вызываемым, как указано.|
|[target_type](#target_type)|Возвращает сведения о типе в вызываемый объект.|

### <a name="operators"></a>Операторы

|||
|-|-|
|[оператор не указан](#op_unspecified)|Проверяет, существует ли вызываемый объект.|
|[operator()](#op_call)|Вызывает вызываемый объект.|
|[оператор=](#op_eq)|Заменяет хранимый вызываемый объект.|

## <a name="assign"></a>назначать

Присваивает вызываемый объект данному объекту функции.

```cpp
template <class Fx, class Alloc>
    void assign(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    void assign(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>Параметры

*_Func* \
Вызываемый объект.

*_Fnref* \
Оболочка ссылки, которая содержит вызываемый объект.

@No__t_1 *AX*
Объект распределителя.

### <a name="remarks"></a>Заметки

Каждая функция-член заменяет `callable object`, который содержится в `*this`, на вызываемый объект, переданный как `operand`. Выделяйте хранилище с помощью объекта распределителя *AX*.

## <a name="function"></a>функций

Создает оболочку, которая является пустой или содержит вызываемый объект произвольного типа с фиксированной сигнатурой.

```cpp
function();
function(nullptr_t npc);
function(const function& right);
template <class Fx>
    function(Fx _Func);
template <class Fx>
    function(reference_wrapper<Fx> _Fnref);
template <class Fx, class Alloc>
    function(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    function(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>Параметры

*справа* \
Объект функции для копирования.

*Fx* \
Тип вызываемого объекта.

*_Func* \
Вызываемый объект, для которого создается оболочка.

@No__t_1 *выделения*
Тип распределителя.

@No__t_1 *AX*
Распределитель.

*_Fnref* \
Ссылка на вызываемый объект для упаковки.

### <a name="remarks"></a>Заметки

Первые два конструктора создают пустой объект `function`. Следующие три конструктора создают объект `function`, который содержит вызываемый объект, переданный как операнд. Последние два конструктора выделяют память с объектом распределителя Ax.

### <a name="example"></a>Пример

```cpp
// std__functional__function_function.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>
#include <vector>

int square(int val)
{
    return val * val;
}

class multiply_by
{
public:
    explicit multiply_by(const int n) : m_n(n) { }

    int operator()(const int x) const
    {
        return m_n * x;
    }

private:
    int m_n;
};

int main()
{

    typedef std::vector< std::function<int (int)> > vf_t;

    vf_t v;
    v.push_back(square);
    v.push_back(std::negate<int>());
    v.push_back(multiply_by(3));

    for (vf_t::const_iterator i = v.begin(); i != v.end(); ++i)
    {
        std::cout << (*i)(10) << std::endl;
    }

    std::function<int (int)> f = v[0];
    std::function<int (int)> g;

    if (f) {
        std::cout << "f is non-empty (correct)." << std::endl;
    } else {
        std::cout << "f is empty (can't happen)." << std::endl;
    }

    if (g) {
        std::cout << "g is non-empty (can't happen)." << std::endl;
    } else {
        std::cout << "g is empty (correct)." << std::endl;
    }

    return 0;
}
```

```Output
100
-10
30
f is non-empty (correct).
g is empty (correct).
```

## <a name="op_unspecified"></a>оператор не указан

Проверяет, существует ли вызываемый объект.

```cpp
operator unspecified();
```

### <a name="remarks"></a>Заметки

Оператор возвращает значение, которое преобразуется в **bool** со значением true только в том случае, если объект не является пустым. Его можно использовать, чтобы проверить, является ли объект пустым.

### <a name="example"></a>Пример

```cpp
// std__functional__function_operator_bool.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == " << (bool)fn0 << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == " << (bool)fn1 << std::endl;

    return (0);
    }
```

```Output
not empty == false
not empty == true
```

## <a name="op_call"></a>оператор ()

Вызывает вызываемый объект.

```cpp
result_type operator()(
    T1 t1,
    T2 t2, ...,
    TN tN);
```

### <a name="parameters"></a>Параметры

@No__t_1 *тн*
Тип N-го аргумента вызова.

\ *тн*
N-й аргумент вызова.

### <a name="remarks"></a>Заметки

Функция-член возвращает `INVOKE(fn, t1, t2, ..., tN, Ret)`, где `fn` — целевой объект, хранящийся в `*this`. Его можно использовать для вызова вызываемого объекта в оболочке.

### <a name="example"></a>Пример

```cpp
// std__functional__function_operator_call.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="op_eq"></a>Оператор =

Заменяет хранимый вызываемый объект.

```cpp
function& operator=(null_ptr_type npc);
function& operator=(const function& right);
template <class Fty>
    function& operator=(Fty fn);
template <class Fty>
    function& operator=(reference_wrapper<Fty> fnref);
```

### <a name="parameters"></a>Параметры

*нпк* \
Константа указателя null.

*справа* \
Объект функции для копирования.

*fn* \
Вызываемый объект, для которого создается оболочка.

*фнреф* \
Ссылка на вызываемый объект для упаковки.

### <a name="remarks"></a>Заметки

Каждый оператор заменяет вызываемый объект, который содержится в `*this`, на вызываемый объект, переданный как операнд.

### <a name="example"></a>Пример

```cpp
// std__functional__function_operator_as.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "val == " << fn0(3) << std::endl;

    std::function<int (int)> fn1;
    fn1 = 0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    fn1 = neg;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = fn0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = std::cref(fn1);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true
empty == false
val == -3
empty == false
val == -3
empty == false
val == -3
```

## <a name="result_type"></a>result_type

Возвращаемый тип хранимого вызываемого объекта.

```cpp
typedef Ret result_type;
```

### <a name="remarks"></a>Заметки

typedef — синоним типа `Ret` в сигнатуре вызова шаблона. Его можно использовать, чтобы определить возвращаемый тип упакованного вызываемого объекта.

### <a name="example"></a>Пример

```cpp
// std__functional__function_result_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    std::function<int (int)>::result_type val = fn1(3);
    std::cout << "val == " << val << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="swap"></a>позиции

Меняет местами два вызываемых объекта.

```cpp
void swap(function& right);
```

### <a name="parameters"></a>Параметры

*справа* \
Объект функции для обмена.

### <a name="remarks"></a>Заметки

Функция – член меняет местами целевые объекты между `*this` и *right*. Она делает это в константном времени и не создает исключений.

### <a name="example"></a>Пример

```cpp
// std__functional__function_swap.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "val == " << fn0(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << std::endl;

    fn0.swap(fn1);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true

empty == true
empty == false
val == -3
```

## <a name="target"></a>мишень

Проверяет, является ли вызываемый объект вызываемым, как указано.

```cpp
template <class Fty2>
    Fty2 *target();
template <class Fty2>
    const Fty2 *target() const;
```

### <a name="parameters"></a>Параметры

*Fty2* \
Тип целевого вызываемого объекта для проверки.

### <a name="remarks"></a>Заметки

Тип *Fty2* должен быть вызван для типов аргументов `T1, T2, ..., TN` и тип возвращаемого значения `Ret`. Если `target_type() == typeid(Fty2)`, шаблон функций-членов возвращает адрес целевого объекта; в противном случае возвращается 0.

Тип *Fty2* вызываемый для типов аргументов `T1, T2, ..., TN` и тип возвращаемого значения `Ret`, если для значения lvalue `fn, t1, t2, ..., tN` типов `Fty2, T1, T2, ..., TN` соответственно, `INVOKE(fn, t1, t2, ..., tN)` имеет правильный формат и, если `Ret` не является **void**, можно преобразовать в `Ret`.

### <a name="example"></a>Пример

```cpp
// std__functional__function_target.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    typedef int (*Myfun)(int);
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "no target == " << (fn0.target<Myfun>() == 0) << std::endl;

    Myfun *fptr = fn0.target<Myfun>();
    std::cout << "val == " << (*fptr)(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "no target == " << (fn1.target<Myfun>() == 0) << std::endl;

    return (0);
    }
```

```Output
empty == false
no target == false
val == -3
empty == true
no target == true
```

## <a name="target_type"></a>target_type

Возвращает сведения о типе в вызываемый объект.

```cpp
const std::type_info& target_type() const;
```

### <a name="remarks"></a>Заметки

Функция-член возвращает `typeid(void)`, если значение `*this` пустое, в противном случае возвращает `typeid(T)`, где `T` — тип целевого объекта.

### <a name="example"></a>Пример

```cpp
// std__functional__function_target_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "type == " << fn0.target_type().name() << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "type == " << fn1.target_type().name() << std::endl;

    return (0);
    }
```

```Output
empty == false
type == int (__cdecl*)(int)
empty == true
type == void
```
