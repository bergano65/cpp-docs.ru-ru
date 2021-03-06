---
title: noexcept (C++)
ms.date: 11/19/2019
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: 5e8d58ed246b0143dc3d3be545cd796a4c3d60ed
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245630"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C++ 11:** Указывает, может ли функция создавать исключения.

## <a name="syntax"></a>Синтаксис

> *Кроме-Expression*: &nbsp;&nbsp;&nbsp;&nbsp;, **Кроме** &nbsp;&nbsp;&nbsp;&nbsp;, **Кроме (** *константное выражение* **)**

### <a name="parameters"></a>Параметры

*константное выражение*<br/>
Константное выражение типа **bool** , которое указывает, является ли набор возможных типов исключений пустым. Неусловная версия эквивалентна `noexcept(true)`.

## <a name="remarks"></a>Примечания

*Выражение* "без исключения" является разновидностью *спецификации исключений*, суффиксом для объявления функции, представляющей набор типов, которые могут сопоставляться обработчиком исключений для любого исключения, которое выходит из функции. Унарный условный оператор `noexcept(`*constant_expression*`)`, где *constant_expression* возвращает **true**, и его безусловный синоним, **Кроме**, укажите, что набор возможных типов исключений, которые могут выходить из функции, пуст. Это значит, что функция никогда не создает исключение и никогда не позволяет распространять исключение за пределы области действия. Оператор `noexcept(`*constant_expression*`)`, где *constant_expression* возвращает **значение false**, или отсутствие спецификации исключения (кроме деструктора или функции освобождения) указывает, что набор возможных исключений, которые могут выйти из функции, — это набор всех типов.

Пометьте функцию как **исключение** , только если все функции, которые она вызывает, прямо или косвенно, также являются **исключением** или **константой**. Компилятор не обязательно проверяет каждый путь кода на наличие исключений, которые могут подниматься к функции, **Кроме** . Если исключение выходит из внешней области функции, помеченной `noexcept`, метод [std:: Terminate](../standard-library/exception-functions.md#terminate) вызывается немедленно, и нет гарантии, что будут вызываться деструкторы любых объектов в области. Используйте **вместо** `throw()`спецификатора динамического исключения, который теперь является устаревшим в стандарте. Мы рекомендуем применить `noexcept` к любой функции, которая никогда не позволяет использовать исключение для распространения стека вызовов. Если функция объявлена как **исключение**, она позволяет компилятору создавать более эффективный код в нескольких разных контекстах. Дополнительные сведения см. в разделе [спецификации исключений](exception-specifications-throw-cpp.md).

## <a name="example"></a>Пример

Функция шаблона, которая копирует свой аргумент, может быть объявлена как, **за исключением** того, что копируемый объект является обычным старым типом данных (Pod). Такая функция может быть объявлена следующим образом:

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>См. также:

[Современные C++ рекомендации по исключениям и обработке ошибок](errors-and-exception-handling-modern-cpp.md)<br/>
[Спецификации исключений (throw, не Except)](exception-specifications-throw-cpp.md)