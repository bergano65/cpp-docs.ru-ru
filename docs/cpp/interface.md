---
title: __interface
ms.date: 05/07/2019
f1_keywords:
- __interface_cpp
helpviewer_keywords:
- __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
ms.openlocfilehash: 7c95e3700b4124c4793e0214ed3b06ecfeee72f1
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222075"
---
# <a name="interface"></a>__interface

**Блок, относящийся только к системам Microsoft**

Microsoft C++ интерфейса могут быть определены следующим образом:

- Может наследовать от произвольного (включая 0) числа базовых интерфейсов.

- Не может наследовать от базового класса.

- Может содержать только открытые, чисто виртуальные методы.

- Не может содержать конструкторы, деструкторы или операторы.

- Не может содержать статические методы.

- Не может содержать члены данных; свойства допускаются.

## <a name="syntax"></a>Синтаксис

```
modifier __interface interface-name {interface-definition};
```

## <a name="remarks"></a>Примечания

Объект C++ [класс](../cpp/class-cpp.md) или [структуры](../cpp/struct-cpp.md) могут быть реализованы с учетом этих правил, но **__interface** применяет их.

Например, ниже приведен пример определения интерфейса:

```cpp
__interface IMyInterface {
   HRESULT CommitX();
   HRESULT get_X(BSTR* pbstrName);
};
```

Сведения об управляемых интерфейсах см. в разделе [класс интерфейса](../extensions/interface-class-cpp-component-extensions.md).

Обратите внимание — нет необходимости явно указывать, что функции `CommitX` и `get_X` являются чистой виртуальными. Эквивалентное объявление для первой функции могло бы быть следующим:

```cpp
virtual HRESULT CommitX() = 0;
```

**__interface** подразумевает [novtable](../cpp/novtable.md) **__declspec** модификатор.

## <a name="example"></a>Пример

В следующем примере показано, как использовать свойства, объявленные в интерфейсе.

```cpp
// deriv_interface.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <string.h>
#include <comdef.h>
#include <stdio.h>

[module(name="test")];

[ object, uuid("00000000-0000-0000-0000-000000000001"), library_block ]
__interface IFace {
   [ id(0) ] int int_data;
   [ id(5) ] BSTR bstr_data;
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]
class MyClass : public IFace {
private:
    int m_i;
    BSTR m_bstr;

public:
    MyClass()
    {
        m_i = 0;
        m_bstr = 0;
    }

    ~MyClass()
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
    }

    int get_int_data()
    {
        return m_i;
    }

    void put_int_data(int _i)
    {
        m_i = _i;
    }

    BSTR get_bstr_data()
    {
        BSTR bstr = ::SysAllocString(m_bstr);
        return bstr;
    }

    void put_bstr_data(BSTR bstr)
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
        m_bstr = ::SysAllocString(bstr);
    }
};

int main()
{
    _bstr_t bstr("Testing");
    CoInitialize(NULL);
    CComObject<MyClass>* p;
    CComObject<MyClass>::CreateInstance(&p);
    p->int_data = 100;
    printf_s("p->int_data = %d\n", p->int_data);
    p->bstr_data = bstr;
    printf_s("bstr_data = %S\n", p->bstr_data);
}
```

```Output
p->int_data = 100
bstr_data = Testing
```

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Ключевые слова](../cpp/keywords-cpp.md)<br/>
[Атрибуты интерфейса](../windows/attributes/interface-attributes.md)