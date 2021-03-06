---
title: Класс CArchive
ms.date: 11/04/2016
f1_keywords:
- CArchive
- AFX/CArchive
- AFX/CArchive::CArchive
- AFX/CArchive::Abort
- AFX/CArchive::Close
- AFX/CArchive::Flush
- AFX/CArchive::GetFile
- AFX/CArchive::GetObjectSchema
- AFX/CArchive::IsBufferEmpty
- AFX/CArchive::IsLoading
- AFX/CArchive::IsStoring
- AFX/CArchive::MapObject
- AFX/CArchive::Read
- AFX/CArchive::ReadClass
- AFX/CArchive::ReadObject
- AFX/CArchive::ReadString
- AFX/CArchive::SerializeClass
- AFX/CArchive::SetLoadParams
- AFX/CArchive::SetObjectSchema
- AFX/CArchive::SetStoreParams
- AFX/CArchive::Write
- AFX/CArchive::WriteClass
- AFX/CArchive::WriteObject
- AFX/CArchive::WriteString
- AFX/CArchive::m_pDocument
helpviewer_keywords:
- CArchive [MFC], CArchive
- CArchive [MFC], Abort
- CArchive [MFC], Close
- CArchive [MFC], Flush
- CArchive [MFC], GetFile
- CArchive [MFC], GetObjectSchema
- CArchive [MFC], IsBufferEmpty
- CArchive [MFC], IsLoading
- CArchive [MFC], IsStoring
- CArchive [MFC], MapObject
- CArchive [MFC], Read
- CArchive [MFC], ReadClass
- CArchive [MFC], ReadObject
- CArchive [MFC], ReadString
- CArchive [MFC], SerializeClass
- CArchive [MFC], SetLoadParams
- CArchive [MFC], SetObjectSchema
- CArchive [MFC], SetStoreParams
- CArchive [MFC], Write
- CArchive [MFC], WriteClass
- CArchive [MFC], WriteObject
- CArchive [MFC], WriteString
- CArchive [MFC], m_pDocument
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
ms.openlocfilehash: 3cf5c3b7a79e846928b5a7ee0af12a3324e141a3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424629"
---
# <a name="carchive-class"></a>Класс CArchive

Позволяет сохранять сложную сеть объектов в виде постоянной двоичной формы (обычно это дисковый накопитель), которая сохраняется после удаления этих объектов.

## <a name="syntax"></a>Синтаксис

```
class CArchive
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Description|
|----------|-----------------|
|[CArchive:: CArchive](#carchive)|Создает объект `CArchive`.|

### <a name="public-methods"></a>Открытые методы

|Имя|Description|
|----------|-----------------|
|[CArchive:: Abort](#abort)|Закрывает Архив без возникновения исключения.|
|[CArchive:: Close](#close)|Очищает незаписанные данные и отключается от `CFile`.|
|[CArchive:: Flush](#flush)|Очищает незаписанные данные из буфера архива.|
|[CArchive:: onfile](#getfile)|Возвращает указатель на объект `CFile` для этого архива.|
|[CArchive:: Жетобжектсчема](#getobjectschema)|Вызывается из функции `Serialize` для определения версии десериализуемого объекта.|
|[CArchive:: Исбуфферемпти](#isbufferempty)|Определяет, очищается ли буфер во время процесса получения сокетов Windows.|
|[CArchive:: Load](#isloading)|Определяет, загружается ли Архив.|
|[CArchive:: для сохранения](#isstoring)|Определяет, хранится ли Архив.|
|[CArchive:: Мапобжект](#mapobject)|Помещает в карту объекты, которые не сериализуются в файл, но доступны для ссылок на подобъекты.|
|[CArchive:: Read](#read)|Считывает необработанные байты.|
|[CArchive:: Реадкласс](#readclass)|Считывает ссылку на класс, сохраненную ранее с помощью `WriteClass`.|
|[CArchive:: вызове ReadObject](#readobject)|Вызывает функцию `Serialize` объекта для загрузки.|
|[CArchive:: ReadString](#readstring)|Считывает одну строку текста.|
|[CArchive:: Сериализекласс](#serializeclass)|Считывает или записывает ссылку на класс `CArchive` объект в зависимости от направления `CArchive`.|
|[CArchive:: Сетлоадпарамс](#setloadparams)|Задает размер, до которого растет массив загрузки. Метод должен вызываться перед загрузкой любого объекта или до вызова `MapObject` или `ReadObject`.|
|[CArchive:: Сетобжектсчема](#setobjectschema)|Задает схему объекта, хранимую в объекте архива.|
|[CArchive:: Сетсторепарамс](#setstoreparams)|Задает размер хэш-таблицы и размер блока для схемы, используемые для обнаружения уникальных объектов в процессе сериализации.|
|[CArchive:: Write](#write)|Записывает необработанные байты.|
|[CArchive:: Вритекласс](#writeclass)|Записывает ссылку на `CRuntimeClass` в `CArchive`.|
|[CArchive:: WriteObject](#writeobject)|Вызывает функцию `Serialize` объекта для хранения.|
|[CArchive:: WriteString](#writestring)|Записывает одну строку текста.|

### <a name="public-operators"></a>Открытые операторы

|Имя|Description|
|----------|-----------------|
|[CArchive:: operator &lt;&lt;](#operator_lt_lt)|Сохраняет объекты и примитивные типы в архив.|
|[CArchive:: operator &gt;&gt;](#operator_gt_gt)|Загружает объекты и примитивные типы из архива.|

### <a name="public-data-members"></a>Открытые элементы данных

|Имя|Description|
|----------|-----------------|
|[CArchive:: m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Remarks

`CArchive` не имеет базового класса.

Позже можно будет загрузить объекты из постоянного хранилища, восстановить их в памяти. Этот процесс создания хранимых данных называется "сериализацией".

Объект архива можно представить как тип двоичного потока. Как и поток ввода-вывода, Архив связан с файлом и позволяет выполнять буферизацию записи и чтения данных в хранилище и из него. Поток ввода-вывода обрабатывает последовательности символов ASCII, но Архив обрабатывает данные двоичных объектов в эффективном, неизбыточном формате.

Необходимо создать объект [кфиле](../../mfc/reference/cfile-class.md) , прежде чем можно будет создать объект `CArchive`. Кроме того, необходимо убедиться, что состояние загрузки или хранения архива совместимо с режимом открытия файла. Вы ограничены одним активным архивом для каждого файла.

При создании объекта `CArchive` он присоединяется к объекту класса `CFile` (или производного класса), который представляет открытый файл. Вы также указываете, будет ли Архив использоваться для загрузки или хранения. Объект `CArchive` может обрабатывать не только примитивные типы, но также объекты производных от [CObject](../../mfc/reference/cobject-class.md)классов, предназначенных для сериализации. Сериализуемый класс обычно имеет `Serialize` функцию-член, которая обычно использует макросы [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) и [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) , как описано в разделе `CObject`класса.

Перегруженные операторы извлечения ( **>>** ) и вставки ( **<<** ) являются удобными интерфейсами программирования архивов, поддерживающими как простые типы, так и классы, производные от `CObject`.

`CArchive` также поддерживает программирование с помощью классов сокетов Windows MFC [CSocket](../../mfc/reference/csocket-class.md) и [CSocketFile](../../mfc/reference/csocketfile-class.md). Функция члена [исбуфферемпти](#isbufferempty) поддерживает это использование.

Дополнительные сведения о `CArchive`см. в статьях [сериализация](../../mfc/serialization-in-mfc.md) и [сокеты Windows. Использование сокетов с архивами](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`CArchive`

## <a name="requirements"></a>Требования

**Заголовок:** afx.h

##  <a name="abort"></a>CArchive:: Abort

Вызовите эту функцию, чтобы закрыть архив, не вызывая исключение.

```
void Abort ();
```

### <a name="remarks"></a>Remarks

Деструктор `CArchive` обычно вызывает `Close`, что приведет к сбросу всех данных, которые не были сохранены в связанный объект `CFile`. Это может вызвать исключения.

При перехвате этих исключений рекомендуется использовать `Abort`, чтобы деструктурировать объект `CArchive` не приводит к дальнейшим исключениям. При обработке исключений `CArchive::Abort` не будет вызывать исключение в случае сбоев, так как, в отличие от [CArchive:: Close](#close), `Abort` игнорирует сбои.

Если вы использовали **New** для выделения объекта `CArchive` в куче, то после закрытия файла его необходимо удалить.

### <a name="example"></a>Пример

  См. пример для [CArchive:: вритекласс](#writeclass).

##  <a name="carchive"></a>CArchive:: CArchive

Конструирует объект `CArchive` и указывает, будет ли он использоваться для загрузки или хранения объектов.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Параметры

*pFile*<br/>
Указатель на объект `CFile`, являющийся конечным источником или назначением постоянных данных.

*нмоде*<br/>
Флаг, указывающий, будут ли объекты загружены из архива или сохранены в нем. Параметр *нмоде* должен иметь одно из следующих значений:

- `CArchive::load` загружает данные из архива. Требуется только `CFile` разрешение на чтение.

- `CArchive::store` сохраняет данные в архив. Требуется `CFile` разрешение на запись.

- `CArchive::bNoFlushOnDelete` не дает архиву автоматически вызывать `Flush` при вызове деструктора архива. Если установить этот флаг, вы несете ответственность за явный вызов `Close` перед вызовом деструктора. В противном случае данные будут повреждены.

*нбуфсизе*<br/>
Целое число, указывающее размер внутреннего буферного файла в байтах. Обратите внимание, что размер буфера по умолчанию составляет 4 096 байт. При обычной архивации больших объектов производительность повышается, если используется больший размер буфера, кратный размеру буфера файла.

*лпбуф*<br/>
Необязательный указатель на предоставляемый пользователем буфер размера *нбуфсизе*. Если этот параметр не указан, Архив выделяет буфер из локальной кучи и освобождает его при уничтожении объекта. Архив не освобождает указанный пользователем буфер.

### <a name="remarks"></a>Remarks

Вы не сможете изменить эту спецификацию после создания архива.

Вы не можете использовать операции `CFile` для изменения состояния файла, пока вы не закроете Архив. Любая такая операция приведет к повреждению целостности архива. Вы можете обращаться к положению указателя файла в любое время во время сериализации, получая объект файла архива из функции [члена GetObject, а](#getfile) затем используя функцию [Кфиле:: Disposition](../../mfc/reference/cfile-class.md#getposition) . Перед получением позиции указателя файла следует вызвать метод [CArchive:: Flush](#flush) .

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

##  <a name="close"></a>CArchive:: Close

Очищает все оставшиеся данные в буфере, закрывает Архив и отключает Архив из файла.

```
void Close();
```

### <a name="remarks"></a>Remarks

Дальнейшие операции с архивом не разрешены. После закрытия архива можно создать другой Архив для того же файла или закрыть файл.

Функция-член `Close` гарантирует, что все данные передаются из архива в файл, а Архив становится недоступным. Чтобы завершить перенос данных из файла на носитель, необходимо сначала использовать [кфиле:: Close](../../mfc/reference/cfile-class.md#close) , а затем уничтожить объект `CFile`.

### <a name="example"></a>Пример

  См. пример для [CArchive:: WriteString](#writestring).

##  <a name="flush"></a>CArchive:: Flush

Принудительная запись всех данных, остающихся в буфере архивации, в файл.

```
void Flush();
```

### <a name="remarks"></a>Remarks

Функция-член `Flush` гарантирует, что все данные передаются из архива в файл. Чтобы завершить перенос данных из файла на носитель, необходимо вызвать метод [кфиле:: Close](../../mfc/reference/cfile-class.md#close) .

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

##  <a name="getfile"></a>CArchive:: onfile

Возвращает указатель на объект `CFile` для этого архива.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Возвращаемое значение

Постоянный указатель на используемый объект `CFile`.

### <a name="remarks"></a>Remarks

Необходимо очистить Архив перед использованием `GetFile`.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

##  <a name="getobjectschema"></a>CArchive:: Жетобжектсчема

Вызовите эту функцию из функции `Serialize`, чтобы определить версию объекта, десериализуемый в данный момент.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Возвращаемое значение

При десериализации версия считываемого объекта.

### <a name="remarks"></a>Remarks

Вызов этой функции допустим только при загрузке объекта `CArchive` ( [CArchive:: Load](#isloading) возвращает ненулевое значение). Он должен быть первым вызовом функции `Serialize` и вызываться только один раз. Возвращаемое значение (UINT)-1 указывает, что номер версии неизвестен.

Класс, производный от `CObject`, может использовать VERSIONABLE_SCHEMA вместе (с помощью битового **или**) с самой версией схемы (в макросе IMPLEMENT_SERIAL) для создания "объекта с поддержкой версии", т. е. объекта, у которого функция-член `Serialize` может считывать несколько версий. Функциональные возможности платформы по умолчанию (без VERSIONABLE_SCHEMA) вызовут исключение при несовпадении версии.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

##  <a name="isbufferempty"></a>CArchive:: Исбуфферемпти

Вызовите эту функцию-член, чтобы определить, является ли пустой внутренний буфер объекта архива.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если буфер архива пуст; в противном случае — 0.

### <a name="remarks"></a>Remarks

Эта функция предоставляется для поддержки программирования с помощью класса сокетов Windows для MFC `CSocketFile`. Его не нужно использовать для архива, связанного с объектом `CFile`.

Причина использования `IsBufferEmpty` с архивом, связанным с объектом `CSocketFile`, заключается в том, что буфер архива может содержать более одного сообщения или записи. После получения одного сообщения следует использовать `IsBufferEmpty` для управления циклом, который возобновляет получение данных до тех пор, пока буфер не будет пустым. Дополнительные сведения см. в описании функции [получения](../../mfc/reference/casyncsocket-class.md#receive) члена класса `CAsyncSocket`, в котором показано, как использовать `IsBufferEmpty`.

Дополнительные сведения см. в разделе [сокеты Windows: Использование сокетов с архивами](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isloading"></a>CArchive:: Load

Определяет, загружает ли Архив данные.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если архив используется в данный момент для загрузки; в противном случае — 0.

### <a name="remarks"></a>Remarks

Эта функция-член вызывается `Serialize`ными функциями архивных классов.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

##  <a name="isstoring"></a>CArchive:: для сохранения

Определяет, хранятся ли в архиве данные.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если архив используется в настоящее время для хранения; в противном случае — 0.

### <a name="remarks"></a>Remarks

Эта функция-член вызывается `Serialize`ными функциями архивных классов.

Если `IsStoring` состояние архива не равно нулю, его `IsLoading` состояние равно 0, и наоборот.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

##  <a name="mapobject"></a>CArchive:: Мапобжект

Вызовите эту функцию члена, чтобы поместить объекты в карту, которые не были сериализованы в файл, но доступны для ссылок на подобъекты.

```
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Параметры

*поб*<br/>
Постоянный указатель на Сохраняемый объект.

### <a name="remarks"></a>Remarks

Например, вы можете не сериализовать документ, но можно сериализовать элементы, которые являются частью документа. Вызывая `MapObject`, вы разрешаете этим элементам или подобъектам ссылаться на документ. Кроме того, сериализованные подэлементы могут сериализовать свои *m_pDocument* указателя назад.

Можно вызвать `MapObject` при сохранении и загрузке из объекта `CArchive`. `MapObject` добавляет указанный объект к внутренним структурам данных, поддерживаемым `CArchive`ным объектом во время сериализации и десериализации, но в отличие от [вызове ReadObject](#readobject) и [WriteObject](#writeobject), он не вызывает сериализацию для объекта.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

##  <a name="m_pdocument"></a>CArchive:: m_pDocument

По умолчанию задано значение NULL. этому указателю на `CDocument` можно присвоить значение любому пользователю экземпляра `CArchive`.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Remarks

Обычно этот указатель используется для передачи дополнительных сведений о процессе сериализации всем сериализуемым объектам. Это достигается путем инициализации указателя с документом (производным от `CDocument`классом), который сериализуется таким образом, что объекты в документе могут получить доступ к документу, если это необходимо. Этот указатель также используется объектами `COleClientItem` во время сериализации.

Платформа задает *m_pDocument* для документа, сериализуемого, когда пользователь выдает команду открытия или сохранения файла. При сериализации документа-контейнера связывания и внедрения объектов (OLE) по причинам, отличным от открытия или сохранения файла, необходимо явно задать *m_pDocument*. Например, это можно сделать при сериализации документа-контейнера в буфер обмена.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

##  <a name="operator_lt_lt"></a>CArchive:: operator &lt;&lt;

Сохраняет указанный объект или тип примитива в архив.

```
friend CArchive& operator<<(
    CArchive& ar,
    const CObject* pOb);

throw(
    CArchiveException*,
    CFileException*);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator<<(
    const ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator<<(BYTE by);
CArchive& operator<<(WORD w);
CArchive& operator<<(LONG l);
CArchive& operator<<(DWORD dw);
CArchive& operator<<(float f);
CArchive& operator<<(double d);
CArchive& operator<<(int i);
CArchive& operator<<(short w);
CArchive& operator<<(char ch);
CArchive& operator<<(wchar_t ch);
CArchive& operator<<(unsigned u);
CArchive& operator<<(bool b);
CArchive& operator<<(ULONGLONG dwdw);
CArchive& operator<<(LONGLONG dwdw);
```

### <a name="return-value"></a>Возвращаемое значение

Ссылка на `CArchive`, включающая несколько операторов вставки в одной строке.

### <a name="remarks"></a>Remarks

Последние две указанные выше версии предназначены специально для хранения 64-разрядных целых чисел.

Если вы использовали макрос IMPLEMENT_SERIAL в реализации класса, то оператор вставки, перегруженный для `CObject`, вызывает защищенный `WriteObject`. Эта функция, в свою очередь, вызывает функцию `Serialize` класса.

Оператор вставки [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (< <) поддерживает диагностический дамп и сохранение в архиве.

### <a name="example"></a>Пример

В этом примере демонстрируется использование оператора вставки `CArchive` < < с типами **int** и **Long** .

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Пример

В этом примере 2 демонстрируется использование оператора вставки `CArchive` < < с типом `CStringT`.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

##  <a name="operator_gt_gt"></a>CArchive:: operator &gt;&gt;

Загружает указанный объект или тип-примитив из архива.

```
friend CArchive& operator>>(
    CArchive& ar,
    CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

friend CArchive& operator>>(
    CArchive& ar,
    const CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator>>(
    ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator>>(BYTE& by);
CArchive& operator>>(WORD& w);
CArchive& operator>>(int& i);
CArchive& operator>>(LONG& l);
CArchive& operator>>(DWORD& dw);
CArchive& operator>>(float& f);
CArchive& operator>>(double& d);
CArchive& operator>>(short& w);
CArchive& operator>>(char& ch);
CArchive& operator>>(wchar_t& ch);
CArchive& operator>>(unsigned& u);
CArchive& operator>>(bool& b);
CArchive& operator>>(ULONGLONG& dwdw);
CArchive& operator>>(LONGLONG& dwdw);
```

### <a name="return-value"></a>Возвращаемое значение

Ссылка на `CArchive`, которая включает несколько операторов извлечения в одной строке.

### <a name="remarks"></a>Remarks

Последние две указанные выше версии предназначены специально для загрузки 64-разрядных целых чисел.

Если вы использовали макрос IMPLEMENT_SERIAL в реализации класса, то операторы извлечения, перегруженные для `CObject`, вызывают защищенную функцию `ReadObject` (с ненулевым указателем на класс времени выполнения). Эта функция, в свою очередь, вызывает функцию `Serialize` класса.

Оператор извлечения [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (> >) поддерживает загрузку из архива.

### <a name="example"></a>Пример

В этом примере демонстрируется использование оператора извлечения `CArchive` > > с типом **int** .

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Пример

В этом примере демонстрируется использование операторов вставки и извлечения `CArchive` <\< и > > с типом `CStringT`.

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

##  <a name="read"></a>CArchive:: Read

Считывает указанное число байтов из архива.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Параметры

*лпбуф*<br/>
Указатель на предоставляемый пользователем буфер, который получает данные, считанные из архива.

*Nмакс.*<br/>
Целое число без знака, указывающее количество байтов, считываемых из архива.

### <a name="return-value"></a>Возвращаемое значение

Целое число без знака, содержащее число фактически считанных байтов. Если возвращаемое значение меньше запрошенного числа, достигнут конец файла. Исключение в условии конца файла не создается.

### <a name="remarks"></a>Remarks

Этот архив не интерпретирует байты.

Функцию члена `Read` в функции `Serialize` можно использовать для чтения обычных структур, содержащихся в объектах.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

##  <a name="readclass"></a>CArchive:: Реадкласс

Вызовите эту функцию-член для чтения ссылки на класс, который ранее хранился с помощью [вритекласс](#writeclass).

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Параметры

*пклассрефрекуестед*<br/>
Указатель на структуру [крунтимекласс](../../mfc/reference/cruntimeclass-structure.md) , соответствующую запрошенной ссылке на класс. Может иметь значение NULL.

*псчема*<br/>
Указатель на схему ранее сохраненного класса времени выполнения.

*побтаг*<br/>
Число, которое ссылается на уникальный тег объекта. Используется для внутренних целей реализацией [вызове ReadObject](#readobject). Предоставляется только для расширенного программирования; *побтаг* обычно должен иметь значение null.

### <a name="return-value"></a>Возвращаемое значение

Указатель на структуру [крунтимекласс](../../mfc/reference/cruntimeclass-structure.md) .

### <a name="remarks"></a>Remarks

Если *пклассрефрекуестед* не равно NULL, `ReadClass` проверяет, совместимы ли архивные сведения о классе с вашим классом среды выполнения. Если он несовместим, `ReadClass` выдаст исключение [карчивиксцептион](../../mfc/reference/carchiveexception-class.md).

Класс среды выполнения должен использовать [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) и [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); в противном случае `ReadClass` выдаст исключение [кнотсуппортедексцептион](../../mfc/reference/cnotsupportedexception-class.md).

Если *псчема* имеет значение null, схему хранимого класса можно получить путем вызова [CArchive:: жетобжектсчема](#getobjectschema); в противном случае <strong>\*</strong> *псчема* будет содержать схему ранее сохраненного класса времени выполнения.

Можно использовать [сериализекласс](#serializeclass) вместо `ReadClass`, который обрабатывает чтение и запись ссылки на класс.

### <a name="example"></a>Пример

  См. пример для [CArchive:: вритекласс](#writeclass).

##  <a name="readobject"></a>CArchive:: вызове ReadObject

Считывает данные объекта из архива и конструирует объект соответствующего типа.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Параметры

*пкласс*<br/>
Постоянный указатель на структуру [крунтимекласс](../../mfc/reference/cruntimeclass-structure.md) , соответствующую объекту, который вы хотите считать.

### <a name="return-value"></a>Возвращаемое значение

Указатель [CObject](../../mfc/reference/cobject-class.md) , который должен быть безопасно приведен к правильному производному классу с помощью [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof).

### <a name="remarks"></a>Remarks

Эта функция обычно вызывается оператором извлечения `CArchive` ( **>>** ), перегруженным для указателя [CObject](../../mfc/reference/cobject-class.md) . `ReadObject`, в свою очередь, вызывает функцию `Serialize` архивированного класса.

При указании ненулевого параметра *пкласс* , полученного с помощью макроса [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) , функция проверяет класс времени выполнения архивного объекта. Предполагается, что вы использовали макрос IMPLEMENT_SERIAL в реализации класса.

### <a name="example"></a>Пример

  См. пример для [CArchive:: WriteObject](#writeobject).

##  <a name="readstring"></a>CArchive:: ReadString

Вызовите эту функцию-член для считывания текстовых данных в буфер из файла, связанного с объектом `CArchive`.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Параметры

*rStr*<br/>
Ссылка на [CString](../../atl-mfc-shared/reference/cstringt-class.md) , которая будет содержать результирующую строку после считывания из файла, связанного с объектом CArchive.

*лпсз*<br/>
Задает указатель на предоставляемый пользователем буфер, который будет принимать текстовую строку, завершающуюся нулем.

*Nмакс.*<br/>
Указывает максимальное число считываемых символов. Значение должно быть на единицу меньше размера буфера *лпсз* .

### <a name="return-value"></a>Возвращаемое значение

В версии, возвращающей логическое значение, TRUE в случае успеха; В противном случае — значение FALSE.

В версии, возвращающей `LPTSTR`, указатель на буфер, содержащий текстовые данные; Значение NULL, если конец файла был достигнут.

### <a name="remarks"></a>Remarks

В версии функции-члена с параметром *nмакс.* буфер будет содержать ограничение в *nмакс.* -1 символов. Чтение остановлено парой символов возврата каретки и перевода строки. Завершающие символы новой строки всегда удаляются. В любом случае добавляется символ null ("\ 0").

[CArchive:: Read](#read) также доступен для ввода в текстовом режиме, но не заканчивается на паре символов возврата каретки и перевода строки.

### <a name="example"></a>Пример

  См. пример для [CArchive:: WriteString](#writestring).

##  <a name="serializeclass"></a>CArchive:: Сериализекласс

Вызывайте эту функцию-член, если требуется сохранить и загрузить сведения о версии базового класса.

```
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Параметры

*пклассреф*<br/>
Указатель на объект класса времени выполнения для базового класса.

### <a name="remarks"></a>Remarks

`SerializeClass` считывает или записывает ссылку на класс в объект `CArchive` в зависимости от направления `CArchive`. Используйте `SerializeClass` вместо [реадкласс](#readclass) и [вритекласс](#writeclass) в качестве удобного способа сериализации объектов базового класса. `SerializeClass` требует меньше кода и меньше параметров.

Как и `ReadClass`, `SerializeClass` проверяет, совместимы ли архивные сведения о классе с вашим классом среды выполнения. Если он несовместим, `SerializeClass` выдаст исключение [карчивиксцептион](../../mfc/reference/carchiveexception-class.md).

Класс среды выполнения должен использовать [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) и [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); в противном случае `SerializeClass` выдаст исключение [кнотсуппортедексцептион](../../mfc/reference/cnotsupportedexception-class.md).

Используйте макрос [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) , чтобы получить значение для параметра *прунтимекласс* . Базовый класс должен использовать макрос [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) .

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

##  <a name="setloadparams"></a>CArchive:: Сетлоадпарамс

Вызовите `SetLoadParams`, когда вы собираетесь считать большое количество объектов, производных от `CObject`, из архива.

```
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Параметры

*нгровби*<br/>
Минимальное число слотов элементов для выделения при необходимости увеличения размера.

### <a name="remarks"></a>Remarks

`CArchive` использует массив нагрузки для разрешения ссылок на объекты, хранящиеся в архиве. `SetLoadParams` позволяет задать размер, до которого увеличивается нагрузка на массив.

Не следует вызывать `SetLoadParams` после загрузки любого объекта или после вызова [мапобжект](#mapobject) или [вызове ReadObject](#readobject) .

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="setobjectschema"></a>CArchive:: Сетобжектсчема

Вызовите эту функцию члена, чтобы задать схему объекта, сохраненную в объекте архива, в *нсчема*.

```
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Параметры

*нсчема*<br/>
Указывает схему объекта.

### <a name="remarks"></a>Remarks

При следующем вызове функции [жетобжектсчема](#getobjectschema) будет возвращено значение, хранящееся в *нсчема*.

Используйте `SetObjectSchema` для расширенного управления версиями; Например, если требуется принудительно прочитать конкретную версию в `Serialize`ной функции производного класса.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

##  <a name="setstoreparams"></a>CArchive:: Сетсторепарамс

Используйте `SetStoreParams` при хранении большого числа объектов, производных от `CObject`, в архиве.

```
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Параметры

*нхашсизе*<br/>
Размер хэш-таблицы для карт указателя интерфейса. Должно быть простым числом.

*нблокксизе*<br/>
Задает гранулярность выделения памяти для расширения параметров. Для наилучшей производительности должна быть степень 2.

### <a name="remarks"></a>Remarks

`SetStoreParams` позволяет задать размер хэш-таблицы и размер блока для схемы, используемые для обнаружения уникальных объектов в процессе сериализации.

Не следует вызывать `SetStoreParams` после того, как будут сохранены какие-либо объекты, или после вызова [мапобжект](#mapobject) или [WriteObject](#writeobject) .

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="write"></a>CArchive:: Write

Записывает указанное число байтов в архив.

```
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Параметры

*лпбуф*<br/>
Указатель на предоставляемый пользователем буфер, содержащий данные, записываемые в архив.

*Nмакс.*<br/>
Целое число, указывающее количество байтов, записываемых в архив.

### <a name="remarks"></a>Remarks

Этот архив не форматирует байты.

Функцию члена `Write` в функции `Serialize` можно использовать для записи обычных структур, содержащихся в объектах.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

##  <a name="writeclass"></a>CArchive:: Вритекласс

Используйте `WriteClass` для хранения сведений о версии и классе базового класса во время сериализации производного класса.

```
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Параметры

*пклассреф*<br/>
Указатель на структуру [крунтимекласс](../../mfc/reference/cruntimeclass-structure.md) , соответствующую запрошенной ссылке на класс.

### <a name="remarks"></a>Remarks

`WriteClass` записывает ссылку на [крунтимекласс](../../mfc/reference/cruntimeclass-structure.md) для базового класса в `CArchive`. Чтобы получить ссылку, используйте [CArchive:: реадкласс](#readclass) .

`WriteClass` проверяет, совместимы ли архивные сведения о классе с вашим классом среды выполнения. Если он несовместим, `WriteClass` выдаст исключение [карчивиксцептион](../../mfc/reference/carchiveexception-class.md).

Класс среды выполнения должен использовать [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) и [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); в противном случае `WriteClass` выдаст исключение [кнотсуппортедексцептион](../../mfc/reference/cnotsupportedexception-class.md).

Можно использовать [сериализекласс](#serializeclass) вместо `WriteClass`, который обрабатывает чтение и запись ссылки на класс.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

##  <a name="writeobject"></a>CArchive:: WriteObject

Сохраняет указанный `CObject` в архив.

```
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Параметры

*поб*<br/>
Постоянный указатель на Сохраняемый объект.

### <a name="remarks"></a>Remarks

Эта функция обычно вызывается оператором `CArchive` вставки ( **<<** ), перегруженным для `CObject`. `WriteObject`, в свою очередь, вызывает функцию `Serialize` архивированного класса.

Для включения архивации необходимо использовать макрос IMPLEMENT_SERIAL. `WriteObject` записывает имя класса ASCII в архив. Это имя класса проверяется позже в процессе загрузки. Специальная схема кодирования предотвращает ненужное дублирование имени класса для нескольких объектов класса. Эта схема также предотвращает избыточное хранение объектов, предназначенных более чем одному указателю.

Точный метод кодирования объектов (включая присутствие имени класса ASCII) является подробным описанием реализации и может измениться в будущих версиях библиотеки.

> [!NOTE]
>  Завершите создание, удаление и обновление всех объектов, прежде чем приступать к их архивированию. При использовании архивации с изменением объектов ваш архив будет поврежден.

### <a name="example"></a>Пример

Определение класса `CAge`см. в примере для [коблист:: коблист](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

##  <a name="writestring"></a>CArchive:: WriteString

Используйте эту функцию-член для записи данных из буфера в файл, связанный с объектом `CArchive`.

```
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Параметры

*лпсз*<br/>
Указывает указатель на буфер, содержащий строку текста, завершающуюся нулем.

### <a name="remarks"></a>Remarks

Завершающий нуль-символ ("\ 0") не записывается в файл; и не является автоматическим написанием новой строки.

`WriteString` создает исключение в ответ на несколько условий, включая полное состояние диска.

`Write` также доступен, но вместо завершения на нуль-символе он записывает запрошенное число байтов в файл.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>См. также раздел

[Диаграмма иерархии](../../mfc/hierarchy-chart.md)<br/>
[Класс CFile](../../mfc/reference/cfile-class.md)<br/>
[Класс CObject](../../mfc/reference/cobject-class.md)<br/>
[Класс CSocket](../../mfc/reference/csocket-class.md)<br/>
[Класс CSocketFile](../../mfc/reference/csocketfile-class.md)
