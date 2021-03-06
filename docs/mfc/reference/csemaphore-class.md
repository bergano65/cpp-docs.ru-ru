---
title: Класс Ксемафоре
ms.date: 11/04/2016
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
ms.openlocfilehash: d5a0e4187107aaab7cedf4e7a0e2fc47b9f9f305
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502587"
---
# <a name="csemaphore-class"></a>Класс Ксемафоре

Объект класса `CSemaphore` представляет "семафор" — объект синхронизации, который позволяет ограниченному числу потоков в одном или нескольких процессах обращаться к объекту, который поддерживает количество потоков, обращающихся к указанному ресурсу в данный момент.

## <a name="syntax"></a>Синтаксис

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[Ксемафоре:: Ксемафоре](#csemaphore)|Создает объект `CSemaphore`.|

## <a name="remarks"></a>Примечания

Семафоры полезны при управлении доступом к общему ресурсу, который может поддерживать только ограниченное число пользователей. Текущее `CSemaphore` число объектов — число разрешенных дополнительных пользователей. Если счетчик достигнет нуля, все попытки использования ресурса, управляемого `CSemaphore` объектом, будут вставлены в системную очередь и ожидать истечения времени ожидания, либо значение счетчика превысит 0. Максимальное число пользователей, которые могут получить доступ к контролируемому ресурсу за один раз, задается `CSemaphore` во время создания объекта.

Чтобы использовать `CSemaphore` объект, `CSemaphore` создайте объект при необходимости. Укажите имя семафора, который вы хотите подождать, и ваше приложение должно его изначально владеть. Затем можно получить доступ к семафору при возврате из конструктора. По завершении доступа к контролируемому ресурсу вызовите метод [ксинкобжект:: Unlock](../../mfc/reference/csyncobject-class.md#unlock) .

Альтернативный способ использования `CSemaphore` объектов — добавить переменную типа `CSemaphore` в качестве члена данных в класс, которым вы хотите управлять. Во время создания управляемого объекта вызовите конструктор `CSemaphore` элемента данных, указав начальное число доступа, максимальное число доступов, имя семафора (если оно будет использоваться в границах процесса) и требуемые атрибуты безопасности.

Для доступа к ресурсам, `CSemaphore` управляемым объектами таким способом, сначала создайте переменную типа [ксинглелокк](../../mfc/reference/csinglelock-class.md) или [кмултилокк](../../mfc/reference/cmultilock-class.md) в функции-члене доступа ресурса. Затем вызовите функцию- `Lock` член объекта Lock (например, [ксинглелокк:: Lock](../../mfc/reference/csinglelock-class.md#lock)). На этом этапе ваш поток будет либо получать доступ к ресурсу, дожидаться освобождения ресурса и получения доступа, либо дожидаться освобождения и истечения времени ожидания ресурса и не сможет получить доступ к ресурсу. В любом случае доступ к ресурсу осуществляется потокобезопасным способом. Чтобы освободить ресурс, используйте функцию- `Unlock` член объекта Lock (например, [ксинглелокк:: Unlock](../../mfc/reference/csinglelock-class.md#unlock)) или разрешите, что объект блокировки выходит за пределы области.

Кроме того, можно создать `CSemaphore` изолированный объект и обращаться к нему явным образом, прежде чем пытаться получить доступ к контролируемому ресурсу. Этот метод, хотя очевидно, что кто-то читает исходный код, более подвержен ошибке.

Дополнительные сведения об использовании `CSemaphore` объектов см. в статье [многопоточность. Использование классов](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)синхронизации.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[ксинкобжект](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>Требования

**Заголовок:** афксмт. h

##  <a name="csemaphore"></a>Ксемафоре:: Ксемафоре

Конструирует именованный или безымянный `CSemaphore` объект.

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>Параметры

*линитиалкаунт*<br/>
Начальное значение счетчика использования семафора. Должно быть больше или равно 0 и меньше или равно значению *лмакскаунт*.

*лмакскаунт*<br/>
Максимальное число использований семафора. Должно быть больше 0.

*пстрнаме*<br/>
Имя семафора. Должен быть предоставлен, если доступ к семафору будет осуществляться через границы процесса. Если `NULL`значение равно, объект будет безымянным. Если имя совпадает с существующим семафором, конструктор создает новый `CSemaphore` объект, который ссылается на семафор этого имени. Если имя совпадает с существующим объектом синхронизации, который не является семафором, построение завершится ошибкой.

*лпсааттрибутес*<br/>
Атрибуты безопасности для объекта семафора. Полное описание этой структуры см. в разделе [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) в Windows SDK.

### <a name="remarks"></a>Примечания

Чтобы получить `CSemaphore` доступ к объекту или освободить его, создайте объект [кмултилокк](../../mfc/reference/cmultilock-class.md) или [ксинглелокк](../../mfc/reference/csinglelock-class.md) и вызовите его функции-члены [Lock](../../mfc/reference/csinglelock-class.md#lock) и [Unlock](../../mfc/reference/csinglelock-class.md#unlock) .

> [!IMPORTANT]
>  После создания `CSemaphore` объекта используйте [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , чтобы убедиться, что мьютекс еще не существовал. Если мьютекс был неожиданно существовал, это может указывать на то, что случайный процесс занят и может полагаться на использование мьютекса злонамеренно. В этом случае рекомендуемой процедурой безопасности является закрытие обработчика и продолжение работы так, как если бы при создании объекта произошел сбой.

## <a name="see-also"></a>См. также

[Класс CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Диаграмма иерархии](../../mfc/hierarchy-chart.md)
