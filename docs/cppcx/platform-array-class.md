---
title: Класс Platform::Array
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Array
- VCCORLIB/Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: 7d9fca4de954b5ba9c7cbcb3bdfce0fe3263dbd7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445797"
---
# <a name="platformarray-class"></a>Класс Platform::Array

Представляет изменяемый одномерный массив, который можно получать и передавать через двоичный интерфейс приложений (ABI).

## <a name="syntax"></a>Синтаксис

```cpp
template <typename T>
private ref class Array<TArg, 1> :
    public WriteOnlyArray<TArg, 1>,
    public IBoxArray<TArg>
```

### <a name="members"></a>Члены

Platform:: Array наследует все свои методы от [класса Platform:: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) и реализует свойство `Value` [интерфейса Platform:: IBoxArray](../cppcx/platform-iboxarray-interface.md).

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Description|
|----------|-----------------|
|[Конструкторы массивов](#ctor)|Инициализирует одномерный, изменяемый массив типов, заданный параметром шаблона класса *T*.|

### <a name="methods"></a>Методы

См. [класс Platform:: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md).

### <a name="properties"></a>Свойства

|||
|-|-|
|[Массив:: значение](#value)|Получает дескриптор текущего массива.|

### <a name="remarks"></a>Remarks

Класс Array является запечатанным и наследовать его нельзя.

Система типов среда выполнения Windows не поддерживает концепцию массива массивов и, следовательно, нельзя передать IVector < Platform:: Array\<T > > в качестве возвращаемого значения или параметра метода. Для передачи массива массивов или последовательности массивов в ABI используйте `IVector<IVector<T>^>`.

Дополнительные сведения о том, когда и как использовать Platform:: Array, см. в разделе [Array и WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

Этот класс определен в заголовке vccorlib.h, который автоматически включается компилятором. Он отображается в IntelliSense, но не в обозревателе объектов, так как он не является общедоступным типом, определенным в Platform. winmd.

### <a name="requirements"></a>Требования

Параметр компилятора: **/ZW**

## <a name="ctor"></a>Конструкторы массивов

Инициализирует одномерный, изменяемый массив типов, заданный параметром шаблона класса *T*.

## <a name="syntax"></a>Синтаксис

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>Параметры

*T*<br/>
Параметр шаблона класса.

*size*<br/>
Количество элементов в массиве.

*data*<br/>
Указатель на массив данных типа `T`, используемый для инициализации данного объекта Array.

### <a name="remarks"></a>Remarks

Дополнительные сведения о создании экземпляров Platform:: Array см. в разделе [Array и WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="get"></a>Метод Array:: Get

Извлекает ссылку на элемент массива с указанным индексом.

## <a name="syntax"></a>Синтаксис

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>Параметры

*index*<br/>
Отсчитываемый от нуля индекс, указывающий на элемент в массиве. Минимальный индекс равен 0, а максимальный индекс — значению, заданному параметром `size` в [конструкторе массива](#ctor).

### <a name="return-value"></a>Возвращаемое значение

Элемент массива, заданный параметром `index`.

## <a name="value"></a>Свойство массива:: value

Получает дескриптор текущего массива.

## <a name="syntax"></a>Синтаксис

```cpp
property Array^ Value;
```

### <a name="return-value"></a>Возвращаемое значение

Дескриптор текущего массива.

## <a name="see-also"></a>См. также раздел

[Пространство имен Platform](../cppcx/platform-namespace-c-cx.md)<br/>
[Классы Array и WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
