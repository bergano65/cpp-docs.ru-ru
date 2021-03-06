---
title: Класс task_options (среда выполнения с параллелизмом)
ms.date: 11/04/2016
f1_keywords:
- ppltasks/concurrency::task_options
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
ms.openlocfilehash: 5f60a07d709a79f3ce4845c8fbd1c40cb2ee7328
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142534"
---
# <a name="task_options-class-concurrency-runtime"></a>Класс task_options (среда выполнения с параллелизмом)

Представляет допустимые параметры для создания задачи

## <a name="syntax"></a>Синтаксис

```cpp
class task_options;
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Description|
|----------|-----------------|
|[Конструктор task_options:: task_options (среда выполнения с параллелизмом)](#ctor)|Перегружен. Заданный по умолчанию список параметров создания задачи|

### <a name="public-methods"></a>Открытые методы

|Имя|Description|
|----------|-----------------|
|[Метод task_options:: get_cancellation_token (среда выполнения с параллелизмом)](#get_cancellation_token)|Возвращает токен отмены|
|[Метод task_options:: get_continuation_context (среда выполнения с параллелизмом)](#get_continuation_context)|Возвращает контекст продолжения|
|[Метод task_options:: get_scheduler (среда выполнения с параллелизмом)](#get_scheduler)|Возвращает планировщик|
|[Метод task_options:: has_cancellation_token (среда выполнения с параллелизмом)](#has_cancellation_token)|Показывает, был ли определен токен отмены пользователем|
|[Метод task_options:: has_scheduler (среда выполнения с параллелизмом)](#has_scheduler)|Показывает, был ли определен планировщик n пользователем|
|[Метод task_options:: set_cancellation_token (среда выполнения с параллелизмом)](#set_cancellation_token)|Задает токен в параметрах|
|[Метод task_options:: set_continuation_context (среда выполнения с параллелизмом)](#set_continuation_context)|Задает контекст данного продолжения в параметрах|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`task_options`

## <a name="requirements"></a>Требования

**Заголовок:** из ppltasks. h

**Пространство имен:** concurrency

## <a name="get_cancellation_token"></a>Метод task_options:: get_cancellation_token (среда выполнения с параллелизмом)

Возвращает токен отмены

```cpp
cancellation_token get_cancellation_token() const;
```

### <a name="return-value"></a>Возвращаемое значение

## <a name="get_continuation_context"></a>Метод task_options:: get_continuation_context (среда выполнения с параллелизмом)

Возвращает контекст продолжения

```cpp
task_continuation_context get_continuation_context() const;
```

### <a name="return-value"></a>Возвращаемое значение

## <a name="get_scheduler"></a>Метод task_options:: get_scheduler (среда выполнения с параллелизмом)

Возвращает планировщик

```cpp
scheduler_ptr get_scheduler() const;
```

### <a name="return-value"></a>Возвращаемое значение

## <a name="has_cancellation_token"></a>Метод task_options:: has_cancellation_token (среда выполнения с параллелизмом)

Показывает, был ли определен токен отмены пользователем

```cpp
bool has_cancellation_token() const;
```

### <a name="return-value"></a>Возвращаемое значение

## <a name="has_scheduler"></a>Метод task_options:: has_scheduler (среда выполнения с параллелизмом)

Показывает, был ли определен планировщик n пользователем

```cpp
bool has_scheduler() const;
```

### <a name="return-value"></a>Возвращаемое значение

## <a name="set_cancellation_token"></a>Метод task_options:: set_cancellation_token (среда выполнения с параллелизмом)

Задает токен в параметрах

```cpp
void set_cancellation_token(cancellation_token _Token);
```

### <a name="parameters"></a>Параметры

`_Token`

## <a name="set_continuation_context"></a>Метод task_options:: set_continuation_context (среда выполнения с параллелизмом)

Задает контекст данного продолжения в параметрах

```cpp
void set_continuation_context(task_continuation_context _ContinuationContext);
```

### <a name="parameters"></a>Параметры

`_ContinuationContext`

## <a name="ctor"></a>Конструктор task_options:: task_options (среда выполнения с параллелизмом)

Заданный по умолчанию список параметров создания задачи

```cpp
task_options();

task_options(
    cancellation_token _Token);

task_options(
    task_continuation_context _ContinuationContext);

task_options(
    cancellation_token _Token,
    task_continuation_context _ContinuationContext);

template<typename _SchedType>
task_options(
    std::shared_ptr<_SchedType> _Scheduler);

task_options(
    scheduler_interface& _Scheduler);

task_options(
    scheduler_ptr _Scheduler);

task_options(
    const task_options& _TaskOptions);
```

### <a name="parameters"></a>Параметры

`_SchedType`

`_Token`

`_ContinuationContext`

`_Scheduler`

`_TaskOptions`

## <a name="see-also"></a>См. также раздел

[Пространство имен concurrency](concurrency-namespace.md)
