---
title: Класс Context
ms.date: 11/04/2016
f1_keywords:
- Context
- CONCRT/concurrency::Context
- CONCRT/concurrency::Context::Block
- CONCRT/concurrency::Context::CurrentContext
- CONCRT/concurrency::Context::GetId
- CONCRT/concurrency::Context::GetScheduleGroupId
- CONCRT/concurrency::Context::GetVirtualProcessorId
- CONCRT/concurrency::Context::Id
- CONCRT/concurrency::Context::IsCurrentTaskCollectionCanceling
- CONCRT/concurrency::Context::IsSynchronouslyBlocked
- CONCRT/concurrency::Context::Oversubscribe
- CONCRT/concurrency::Context::ScheduleGroupId
- CONCRT/concurrency::Context::Unblock
- CONCRT/concurrency::Context::VirtualProcessorId
- CONCRT/concurrency::Context::Yield
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
ms.openlocfilehash: 7c47d9db64b0af7d5413abed3f85e9d41a591fa2
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427407"
---
# <a name="context-class"></a>Класс Context

Представляет абстракцию для контекста выполнения.

## <a name="syntax"></a>Синтаксис

```cpp
class Context;
```

## <a name="members"></a>Члены

### <a name="protected-constructors"></a>Защищенные конструкторы

|Имя|Description|
|----------|-----------------|
|[Деструктор контекста ~](#dtor)||

### <a name="public-methods"></a>Открытые методы

|Имя|Description|
|----------|-----------------|
|[Block](#block)|Блокирует текущий контекст.|
|[CurrentContext](#currentcontext)|Возвращает указатель на текущий контекст.|
|[GetId](#getid)|Возвращает идентификатор для контекста, уникального внутри планировщика, которому принадлежит контекст.|
|[жетсчедулеграупид](#getschedulegroupid)|Возвращает идентификатор для группы расписаний, над которой в данный момент работает контекст.|
|[жетвиртуалпроцессорид](#getvirtualprocessorid)|Возвращает идентификатор виртуального процессора, на котором в данный момент выполняется контекст.|
|[Id](#id)|Возвращает идентификатор для текущего контекста, уникального в пределах планировщика, к которому принадлежит текущий контекст.|
|[искурренттаскколлектионканцелинг](#iscurrenttaskcollectioncanceling)|Возвращает значение, указывающее, находится ли коллекция задач, которая сейчас выполняется в текущем контексте, в состоянии активной отмены (или вскоре).|
|[иссинчронауслиблоккед](#issynchronouslyblocked)|Определяет, является ли контекст синхронно заблокированным. Контекст считается синхронно заблокированным, если он явно выполнил действие, которое привело к блокировке.|
|[Превысить предел подписок](#oversubscribe)|Внедряет дополнительный виртуальный процессор в планировщик на время выполнения блока кода при вызове в контексте, выполняемом на одном из виртуальных процессоров в этом планировщике.|
|[счедулеграупид](#schedulegroupid)|Возвращает идентификатор для группы расписаний, над которой работает текущий контекст.|
|[Внести](#unblock)|Разблокирует контекст и приводит к его готовности к запуску.|
|[виртуалпроцессорид](#virtualprocessorid)|Возвращает идентификатор виртуального процессора, на котором исполняется текущий контекст.|
|[Yield](#yield)|Уступает выполнение, чтобы мог выполняться другой контекст. Если доступных контекстов для уступки выполнения нет, планировщик может уступить выполнение другому потоку операционной системы.|

## <a name="remarks"></a>Remarks

Планировщик среда выполнения с параллелизмом (см. раздел [планировщик](scheduler-class.md)) использует контексты выполнения для выполнения работы, поставленной в очередь приложением. Поток Win32 — это пример контекста выполнения в операционной системе Windows.

В любое время уровень параллелизма планировщика равен числу виртуальных процессоров, предоставленных ему диспетчер ресурсов. Виртуальный процессор является абстракцией для обрабатывающего ресурса и сопоставляется аппаратному потоку в базовой системе. Только один контекст планировщика может выполняться на виртуальном процессоре в определенный момент времени.

По сути, планировщик работает совместно, и выполняющийся контекст может в любое время передавать свой виртуальный процессор другому контексту, если он хочет перейти в состояние ожидания. Когда оно будет удовлетворено, оно не сможет возобновиться, пока доступный виртуальный процессор от планировщика не начнет его выполнение.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`Context`

## <a name="requirements"></a>Требования

**Заголовок:** ConcRT. h

**Пространство имен:** concurrency

## <a name="block"></a>Блок

Блокирует текущий контекст.

```cpp
static void __cdecl Block();
```

### <a name="remarks"></a>Remarks

В результате этого метода в процессе будет создан планировщик по умолчанию и/или присоединен к вызывающему контексту, если отсутствует планировщик, в данный момент связанный с вызывающим контекстом.

Если вызывающий контекст выполняется на виртуальном процессоре, виртуальный процессор обнаружит еще один запускаемый контекст для выполнения или может создать новый.

После вызова или вызова метода `Block` необходимо связать его с вызовом метода [Unblock](#unblock) из другого контекста выполнения, чтобы он снова выполнялся. Имейте в виду, что существует важный период между точкой, где код публикует свой контекст для другого потока, чтобы иметь возможность вызвать метод `Unblock` и точку, в которой выполняется фактический вызов метода `Block`. Во время этого периода не следует вызывать ни один метод, который может блокировать и разблокировать по своим собственным причинам (например, получение блокировки). Вызовы метода `Block` и `Unblock` не отписывают причины блокировки и разблокировки. Только один объект должен быть владельцем пары `Block`- `Unblock`.

Этот метод может вызывать различные исключения, в том числе [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md).

## <a name="dtor"></a>~ Context

```cpp
virtual ~Context();
```

## <a name="currentcontext"></a>CurrentContext

Возвращает указатель на текущий контекст.

```cpp
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на текущий контекст.

### <a name="remarks"></a>Remarks

В результате этого метода в процессе будет создан планировщик по умолчанию и/или присоединен к вызывающему контексту, если отсутствует планировщик, в данный момент связанный с вызывающим контекстом.

## <a name="getid"></a>GetId

Возвращает идентификатор для контекста, уникального внутри планировщика, которому принадлежит контекст.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Возвращаемое значение

Идентификатор контекста, уникальный в пределах планировщика, которому принадлежит контекст.

## <a name="getschedulegroupid"></a>жетсчедулеграупид

Возвращает идентификатор для группы расписаний, над которой в данный момент работает контекст.

```cpp
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>Возвращаемое значение

Идентификатор группы расписаний, в которой сейчас работает контекст.

### <a name="remarks"></a>Remarks

Возвращаемое значение этого метода — это выборка для группы расписаний, на которой выполняются контекст. Если этот метод вызывается в контексте, отличном от текущего контекста, значение может быть устаревшим в момент возврата и полагаться на него нельзя. Как правило, этот метод используется только в целях отладки или трассировки.

## <a name="getvirtualprocessorid"></a>жетвиртуалпроцессорид

Возвращает идентификатор виртуального процессора, на котором в данный момент выполняется контекст.

```cpp
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>Возвращаемое значение

Если контекст в данный момент выполняется на виртуальном процессоре, идентификатор виртуального процессора, на котором в данный момент выполняется контекст; в противном случае значение `-1`.

### <a name="remarks"></a>Remarks

Возвращаемое значение этого метода — это выборка для виртуального процессора, на котором выполняются контекст. Это значение может быть устаревшим в момент возврата, и на него нельзя полагаться. Как правило, этот метод используется только в целях отладки или трассировки.

## <a name="id"></a>Удостоверения

Возвращает идентификатор для текущего контекста, уникального в пределах планировщика, к которому принадлежит текущий контекст.

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Возвращаемое значение

Если текущий контекст присоединен к планировщику, идентификатор текущего контекста, уникальный в пределах планировщика, к которому принадлежит текущий контекст; в противном случае значение `-1`.

## <a name="iscurrenttaskcollectioncanceling"></a>искурренттаскколлектионканцелинг

Возвращает значение, указывающее, находится ли коллекция задач, которая сейчас выполняется в текущем контексте, в состоянии активной отмены (или вскоре).

```cpp
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>Возвращаемое значение

Если планировщик присоединен к вызывающему контексту, а группа задач исполняет задачу в этом контексте, указывает, находится ли эта группа задач в состоянии активной отмены (или будет вскоре); в противном случае значение `false`.

## <a name="issynchronouslyblocked"></a>иссинчронауслиблоккед

Определяет, является ли контекст синхронно заблокированным. Контекст считается синхронно заблокированным, если он явно выполнил действие, которое привело к блокировке.

```cpp
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>Возвращаемое значение

Указывает, синхронно ли блокируется контекст.

### <a name="remarks"></a>Remarks

Контекст считается синхронно заблокированным, если он явно выполнил действие, которое привело к блокировке. В планировщике потоков это означает прямой вызов метода `Context::Block` или объекта синхронизации, который был создан с помощью метода `Context::Block`.

Возвращаемое значение этого метода — это мгновенное указание того, блокируется ли контекст синхронно. Это значение может быть устаревшим, когда оно возвращается и может использоваться только в особых обстоятельствах.

## <a name="operator_delete"></a>оператор DELETE

Объект `Context` внутренне уничтожается средой выполнения. Его невозможно удалить явно.

```cpp
void operator delete(void* _PObject);
```

### <a name="parameters"></a>Параметры

*_PObject*<br/>
Указатель на удаляемый объект.

## <a name="oversubscribe"></a>Превысить предел подписок

Внедряет дополнительный виртуальный процессор в планировщик на время выполнения блока кода при вызове в контексте, выполняемом на одном из виртуальных процессоров в этом планировщике.

```cpp
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>Параметры

*_BeginOversubscription*<br/>
При **значении true**указывает, что дополнительный виртуальный процессор следует добавить в течение превышения лимита подписки. **Значение false**указывает, что превышение лимита подписки завершается, а ранее добавленный виртуальный процессор должен быть удален.

## <a name="schedulegroupid"></a>счедулеграупид

Возвращает идентификатор для группы расписаний, над которой работает текущий контекст.

```cpp
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>Возвращаемое значение

Если текущий контекст присоединен к планировщику и работает над группой расписаний, идентификатор группы планировщика, на котором работает текущий контекст; в противном случае значение `-1`.

## <a name="unblock"></a>Внести

Разблокирует контекст и приводит к его готовности к запуску.

```cpp
virtual void Unblock() = 0;
```

### <a name="remarks"></a>Remarks

Вполне допустимо, чтобы вызов метода `Unblock` был получен перед вызовом метода [Block](#block) . При условии, что вызовы методов `Block` и `Unblock` должным образом связаны, среда выполнения правильно обрабатывает естественную конкуренцию любого порядка. Вызов `Unblock`, идущий перед вызовом `Block`, просто инвертирует результат вызова `Block`.

Существует несколько исключений, которые могут быть вызваны из этого метода. Если контекст пытается вызвать метод `Unblock` на самом себе, будет выдано исключение [context_self_unblock](context-self-unblock-class.md) . Если вызовы `Block` и `Unblock` не связаны должным образом (например, два вызова `Unblock` выполняются для контекста, который выполняется в данный момент), будет создано исключение [context_unblock_unbalanced](context-unblock-unbalanced-class.md) .

Имейте в виду, что существует важный период между точкой, где код публикует свой контекст для другого потока, чтобы иметь возможность вызвать метод `Unblock` и точку, в которой выполняется фактический вызов метода `Block`. Во время этого периода не следует вызывать ни один метод, который может блокировать и разблокировать по своим собственным причинам (например, получение блокировки). Вызовы метода `Block` и `Unblock` не отписывают причины блокировки и разблокировки. Только один объект должен иметь права владельца `Block` и `Unblock` пары.

## <a name="virtualprocessorid"></a>виртуалпроцессорид

Возвращает идентификатор виртуального процессора, на котором исполняется текущий контекст.

```cpp
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>Возвращаемое значение

Если текущий контекст присоединен к планировщику, идентификатор виртуального процессора, на котором выполняются текущие контексты; в противном случае значение `-1`.

### <a name="remarks"></a>Remarks

Возвращаемое значение этого метода — это выборка мгновенного значения виртуального процессора, на котором выполняются текущие контексты. Это значение может быть устаревшим в момент возврата, и на него нельзя полагаться. Как правило, этот метод используется только в целях отладки или трассировки.

## <a name="yield"></a>Получает

Уступает выполнение, чтобы мог выполняться другой контекст. Если доступных контекстов для уступки выполнения нет, планировщик может уступить выполнение другому потоку операционной системы.

```cpp
static void __cdecl Yield();
```

### <a name="remarks"></a>Remarks

В результате этого метода в процессе будет создан планировщик по умолчанию и/или присоединен к вызывающему контексту, если отсутствует планировщик, в данный момент связанный с вызывающим контекстом.

## <a name="yieldexecution"></a>YieldExecution

Уступает выполнение, чтобы мог выполняться другой контекст. Если доступных контекстов для уступки выполнения нет, планировщик может уступить выполнение другому потоку операционной системы.

```cpp
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>Remarks

В результате этого метода в процессе будет создан планировщик по умолчанию и/или присоединен к вызывающему контексту, если отсутствует планировщик, в данный момент связанный с вызывающим контекстом.

Эта функция является новой в Visual Studio 2015 и идентична функции [yield](#yield) , но не конфликтует с макросом yield в Windows. h.

## <a name="see-also"></a>См. также раздел

[Пространство имен concurrency](concurrency-namespace.md)<br/>
[Класс Scheduler](scheduler-class.md)<br/>
[Планировщик заданий](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
