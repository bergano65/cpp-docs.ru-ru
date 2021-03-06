---
title: Класс CDatabase
ms.date: 11/04/2016
f1_keywords:
- CDatabase
- AFXDB/CDatabase
- AFXDB/CDatabase::CDatabase
- AFXDB/CDatabase::BeginTrans
- AFXDB/CDatabase::BindParameters
- AFXDB/CDatabase::Cancel
- AFXDB/CDatabase::CanTransact
- AFXDB/CDatabase::CanUpdate
- AFXDB/CDatabase::Close
- AFXDB/CDatabase::CommitTrans
- AFXDB/CDatabase::ExecuteSQL
- AFXDB/CDatabase::GetBookmarkPersistence
- AFXDB/CDatabase::GetConnect
- AFXDB/CDatabase::GetCursorCommitBehavior
- AFXDB/CDatabase::GetCursorRollbackBehavior
- AFXDB/CDatabase::GetDatabaseName
- AFXDB/CDatabase::IsOpen
- AFXDB/CDatabase::OnSetOptions
- AFXDB/CDatabase::Open
- AFXDB/CDatabase::OpenEx
- AFXDB/CDatabase::Rollback
- AFXDB/CDatabase::SetLoginTimeout
- AFXDB/CDatabase::SetQueryTimeout
- AFXDB/CDatabase::m_hdbc
helpviewer_keywords:
- CDatabase [MFC], CDatabase
- CDatabase [MFC], BeginTrans
- CDatabase [MFC], BindParameters
- CDatabase [MFC], Cancel
- CDatabase [MFC], CanTransact
- CDatabase [MFC], CanUpdate
- CDatabase [MFC], Close
- CDatabase [MFC], CommitTrans
- CDatabase [MFC], ExecuteSQL
- CDatabase [MFC], GetBookmarkPersistence
- CDatabase [MFC], GetConnect
- CDatabase [MFC], GetCursorCommitBehavior
- CDatabase [MFC], GetCursorRollbackBehavior
- CDatabase [MFC], GetDatabaseName
- CDatabase [MFC], IsOpen
- CDatabase [MFC], OnSetOptions
- CDatabase [MFC], Open
- CDatabase [MFC], OpenEx
- CDatabase [MFC], Rollback
- CDatabase [MFC], SetLoginTimeout
- CDatabase [MFC], SetQueryTimeout
- CDatabase [MFC], m_hdbc
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
ms.openlocfilehash: ebc36d82af9bfe12ab30a86214e58610b5eaab95
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424509"
---
# <a name="cdatabase-class"></a>Класс CDatabase

Представляет подключение к источнику данных, с помощью которого можно получить доступ к данным.

## <a name="syntax"></a>Синтаксис

```
class CDatabase : public CObject
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Description|
|----------|-----------------|
|[CDatabase:: CDatabase](#cdatabase)|Формирует объект `CDatabase`. Необходимо инициализировать объект, вызвав `OpenEx` или `Open`.|

### <a name="public-methods"></a>Открытые методы

|Имя|Description|
|----------|-----------------|
|[CDatabase:: примеры BeginTrans](#begintrans)|Запускает "транзакцию" — серию обратимых вызовов функций-членов `AddNew`, `Edit`, `Delete`и `Update` класса `CRecordset` — в подключенном источнике данных. Источник данных должен поддерживать транзакции, чтобы `BeginTrans` могли действовать.|
|[CDatabase:: Биндпараметерс](#bindparameters)|Позволяет привязывать параметры перед вызовом `CDatabase::ExecuteSQL`.|
|[CDatabase:: Cancel](#cancel)|Отменяет асинхронную операцию или процесс из второго потока.|
|[CDatabase:: Кантрансакт](#cantransact)|Возвращает ненулевое значение, если источник данных поддерживает транзакции.|
|[CDatabase:: Канупдате](#canupdate)|Возвращает ненулевое значение, если объект `CDatabase` является обновляемым (не только для чтения).|
|[CDatabase:: Close](#close)|Закрывает соединение с источником данных.|
|[CDatabase:: CommitTrans](#committrans)|Завершает транзакцию, начатую `BeginTrans`. Команды в транзакции, которые изменяют источник данных.|
|[CDatabase:: ExecuteSQL](#executesql)|Выполняет инструкцию SQL. Записи данных не возвращаются.|
|[CDatabase:: Жетбукмаркперсистенце](#getbookmarkpersistence)|Определяет операции, с помощью которых закладки сохраняются в объектах набора записей.|
|[CDatabase:: соединение](#getconnect)|Возвращает строку соединения ODBC, используемую для соединения объекта `CDatabase` с источником данных.|
|[CDatabase:: Жеткурсоркоммитбехавиор](#getcursorcommitbehavior)|Определяет результат фиксации транзакции в открытом объекте набора записей.|
|[CDatabase:: Жеткурсорроллбаккбехавиор](#getcursorrollbackbehavior)|Определяет результат отката транзакции в открытом объекте набора записей.|
|[CDatabase:: GetDatabaseName](#getdatabasename)|Возвращает имя используемой в данный момент базы данных.|
|[CDatabase:: OnOpen](#isopen)|Возвращает ненулевое значение, если объект `CDatabase` в настоящее время подключен к источнику данных.|
|[CDatabase:: Онсетоптионс](#onsetoptions)|Вызывается платформой для задания стандартных параметров соединения. Реализация по умолчанию задает значение времени ожидания запроса. Эти параметры можно установить заранее, вызвав `SetQueryTimeout`.|
|[CDatabase:: Open](#open)|Устанавливает соединение с источником данных (с помощью драйвера ODBC).|
|[CDatabase:: Опенекс](#openex)|Устанавливает соединение с источником данных (с помощью драйвера ODBC).|
|[CDatabase:: ROLLBACK](#rollback)|Изменяет изменения, внесенные во время текущей транзакции. Источник данных возвращается к предыдущему состоянию, как определено в `BeginTrans` вызове без изменений.|
|[CDatabase:: SetLoginTimeout](#setlogintimeout)|Задает время ожидания в секундах, по истечении которого произойдет тайм-аут попытки подключения к источнику данных.|
|[CDatabase:: Getquerytimeout](#setquerytimeout)|Задает время ожидания в секундах, по истечении которого операции запроса базы данных будут истекает. Влияет на все последующие вызовы `Open`набора записей, `AddNew`, `Edit`и `Delete`.|

### <a name="public-data-members"></a>Открытые элементы данных

|Имя|Description|
|----------|-----------------|
|[CDatabase:: m_hdbc](#m_hdbc)|Подключение к источнику данных по протоколу ODBC. Введите *хдбк*.|

## <a name="remarks"></a>Remarks

Источник данных — это конкретный экземпляр данных, размещенный в какой-либо системе управления базами данных (СУБД). К примерам относятся Microsoft SQL Server, Microsoft Access, Borland dBASE и xBASE. В приложении одновременно может быть активно один или несколько объектов `CDatabase`.

> [!NOTE]
>  Если вы работаете с классами объектов доступа к данным (DAO), а не с классами ODBC, используйте вместо этого класс [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) . Дополнительные сведения см. в статье [Общие сведения о программировании баз данных](../../data/data-access-programming-mfc-atl.md).

Чтобы использовать `CDatabase`, создайте объект `CDatabase` и вызовите его `OpenEx` функцию-член. Откроется подключение. После создания `CRecordset` объектов для работы в подключенном источнике данных передайте конструктору набора записей указатель на объект `CDatabase`. По завершении использования соединения вызовите функцию члена `Close` и удалите объект `CDatabase`. `Close` закрывает все наборы записей, которые ранее не были закрыты.

Дополнительные сведения о `CDatabase`см. в статьях [источник данных (ODBC)](../../data/odbc/data-source-odbc.md) и [Обзор: программирование баз данных](../../data/data-access-programming-mfc-atl.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Требования

**Заголовок:** афксдб. h

##  <a name="begintrans"></a>CDatabase:: примеры BeginTrans

Вызовите эту функцию-член, чтобы начать транзакцию с подключенным источником данных.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если вызов был успешным, и изменения фиксируются только вручную; в противном случае — 0.

### <a name="remarks"></a>Remarks

Транзакция состоит из одного или нескольких вызовов `AddNew`, `Edit`, `Delete`и `Update` функций-членов объекта `CRecordset`. Перед началом транзакции объект `CDatabase` должен быть уже подключен к источнику данных путем вызова его `OpenEx` или `Open` функции-члена. Чтобы завершить транзакцию, вызовите [CommitTrans](#committrans) , чтобы принять все изменения в источнике данных (и выполнить их), или вызовите [ROLLBACK](#rollback) , чтобы прервать всю транзакцию. Вызовите `BeginTrans` после открытия любых наборов записей, вовлеченных в транзакцию, и как можно ближе к фактическим операциям обновления.

> [!CAUTION]
>  В зависимости от драйвера ODBC открытие набора записей перед вызовом `BeginTrans` может вызвать проблемы при вызове `Rollback`. Следует проверить конкретный драйвер, который вы используете. Например, при использовании драйвера Microsoft Access, включенного в пакет драйверов Microsoft ODBC для настольных компьютеров 3,0, необходимо учитывать необходимость использования ядра СУБД Jet, что не следует начинать транзакцию в любой базе данных с открытым курсором. В классах базы данных MFC открытый курсор означает открытый `CRecordset` объект. Дополнительные сведения см. в [техническом примечании 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans` также может блокировать записи данных на сервере в зависимости от запрашиваемого параллелизма и возможностей источника данных. Сведения о блокировке данных см. в статье [набор записей: Блокировка записей (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Определяемые пользователем транзакции объясняются в статье [транзакция (ODBC)](../../data/odbc/transaction-odbc.md).

`BeginTrans` устанавливает состояние, в которое может быть выполнен откат последовательности транзакций (в обратном порядке). Чтобы установить новое состояние для отката, зафиксируйте текущую транзакцию, а затем снова вызовите `BeginTrans`.

> [!CAUTION]
>  Повторный вызов `BeginTrans` без вызова `CommitTrans` или `Rollback` является ошибкой.

Вызовите функцию-член [кантрансакт](#cantransact) , чтобы определить, поддерживает ли драйвер транзакции для заданной базы данных. Также следует вызвать [жеткурсоркоммитбехавиор](#getcursorcommitbehavior) и [жеткурсорроллбаккбехавиор](#getcursorrollbackbehavior) , чтобы определить поддержку сохранения курсора.

Дополнительные сведения о транзакциях см. в описании [транзакции статьи (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Пример

  См. статью [транзакция: выполнение транзакции в наборе записей (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="bindparameters"></a>CDatabase:: Биндпараметерс

Переопределите `BindParameters`, когда необходимо привязать параметры перед вызовом [CDatabase:: ExecuteSQL](#executesql).

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Параметры

*хстмт*<br/>
Обработчик инструкций ODBC, для которого необходимо выполнить привязку параметров.

### <a name="remarks"></a>Remarks

Этот подход полезен, если результирующий набор из хранимой процедуры не нужен.

В переопределении вызовите `SQLBindParameters` и связанные функции ODBC для привязки параметров. MFC вызывает переопределение перед вызовом `ExecuteSQL`. Вам не нужно вызывать `SQLPrepare`; `ExecuteSQL` вызывает `SQLExecDirect` и уничтожает *хстмт*, который используется только один раз.

##  <a name="cancel"></a>CDatabase:: Cancel

Вызовите эту функцию-член, чтобы запросить, что источник данных отменит асинхронную операцию или процесс из второго потока.

```
void Cancel();
```

### <a name="remarks"></a>Remarks

Обратите внимание, что классы ODBC MFC больше не используют асинхронную обработку. для выполнения асинхронной операции необходимо напрямую вызвать функцию API ODBC [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function). Дополнительные сведения см. в разделе [Асинхронное выполнение](/sql/odbc/reference/develop-app/asynchronous-execution).

##  <a name="cantransact"></a>CDatabase:: Кантрансакт

Вызовите эту функцию члена, чтобы определить, допускает ли база данных транзакции.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если наборы записей, использующие этот объект `CDatabase`, допускают транзакции. в противном случае — 0.

### <a name="remarks"></a>Remarks

Дополнительные сведения о транзакциях см. в разделе [транзакция статьи (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="canupdate"></a>CDatabase:: Канупдате

Вызовите эту функцию члена, чтобы определить, допускает ли объект `CDatabase` обновления.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если объект `CDatabase` допускает обновления; в противном случае — значение 0, указывающее, что вы передали TRUE в *бреадонли* при открытии объекта `CDatabase` или что сам источник данных доступен только для чтения. Источник данных доступен только для чтения, если вызов функции API ODBC `SQLGetInfo` для SQL_DATASOURCE_READ_ONLY возвращает значение "y".

### <a name="remarks"></a>Remarks

Не все драйверы поддерживают обновления.

##  <a name="cdatabase"></a>CDatabase:: CDatabase

Формирует объект `CDatabase`.

```
CDatabase();
```

### <a name="remarks"></a>Remarks

После создания объекта необходимо вызвать его `OpenEx` или `Open` функцию-член, чтобы установить соединение с указанным источником данных.

Может оказаться удобным внедрить объект `CDatabase` в класс документа.

### <a name="example"></a>Пример

В этом примере показано использование `CDatabase` в классе, производном от `CDocument`.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

##  <a name="close"></a>CDatabase:: Close

Вызовите эту функцию-член, если требуется отключиться от источника данных.

```
virtual void Close();
```

### <a name="remarks"></a>Remarks

Прежде чем вызывать эту функцию члена, необходимо закрыть все наборы записей, связанные с объектом `CDatabase`. Поскольку `Close` не уничтожает объект `CDatabase`, можно повторно использовать объект, открыв новое соединение с тем же источником данных или другим источником данных.

Все ожидающие `AddNew` или `Edit` инструкции для наборов записей, использующих базу данных, отменяются, а все ожидающие транзакции откатываются. Все наборы записей, зависящие от объекта `CDatabase`, остаются в неопределенном состоянии.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

##  <a name="committrans"></a>CDatabase:: CommitTrans

Вызывайте эту функцию члена после завершения транзакций.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если обновления были успешно зафиксированы; в противном случае — 0. Если `CommitTrans` происходит сбой, состояние источника данных не определено. Необходимо проверить данные, чтобы определить его состояние.

### <a name="remarks"></a>Remarks

Транзакция состоит из ряда вызовов `AddNew`, `Edit`, `Delete`и `Update` функций-членов объекта `CRecordset`, который начался с помощью вызова функции-члена [примеры BeginTrans](#begintrans) . `CommitTrans` фиксирует транзакцию. По умолчанию обновления фиксируются немедленно; вызов `BeginTrans` вызывает отложенную фиксацию обновлений до вызова `CommitTrans`.

До вызова `CommitTrans` для завершения транзакции можно вызвать функцию-член [ROLLBACK](#rollback) , чтобы прервать транзакцию и оставить источник данных в исходном состоянии. Чтобы начать новую транзакцию, вызовите `BeginTrans` еще раз.

Дополнительные сведения о транзакциях см. в описании [транзакции статьи (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Пример

  См. статью [транзакция: выполнение транзакции в наборе записей (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="executesql"></a>CDatabase:: ExecuteSQL

Вызывайте эту функцию-член, если требуется выполнить команду SQL напрямую.

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Параметры

*lpszSQL*<br/>
Указатель на строку, завершающуюся нулем, которая содержит допустимую команду SQL для выполнения. Можно передать [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Remarks

Создайте команду как строку, завершающуюся нулем. `ExecuteSQL` не возвращает записи данных. Если вы хотите работать с записями, используйте вместо этого объект Recordset.

Большинство команд для источника данных выдаются с помощью объектов Recordset, которые поддерживают команды для выбора данных, вставки новых записей, удаления записей и редактирования записей. Однако не все функции ODBC напрямую поддерживаются классами базы данных, поэтому иногда может потребоваться выполнить прямой вызов SQL с `ExecuteSQL`.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

##  <a name="getbookmarkpersistence"></a>CDatabase:: Жетбукмаркперсистенце

Вызовите эту функцию-член, чтобы определить наличие закладок в объекте recordset после определенных операций.

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>Возвращаемое значение

Битовая маска, определяющая операции, при выполнении которых закладки сохраняются в объекте recordset. Дополнительные сведения см. в разделе "Заметки".

### <a name="remarks"></a>Remarks

Например, если вызвать метод `CRecordset::GetBookmark`, а затем вызвать`CRecordset::Requery`, закладка, полученная от `GetBookmark`, может быть недействительной. Перед вызовом `GetBookmarkPersistence` следует вызвать метод `CRecordset::SetBookmark`.

В следующей таблице перечислены значения битовой маски, которые можно объединять для возвращаемого значения `GetBookmarkPersistence`.

|Значение битовой маски|Сохранение закладки|
|-------------------|--------------------------|
|SQL_BP_CLOSE|Закладки действительны после операции `Requery`.|
|SQL_BP_DELETE|Закладка для строки допустима после `Delete` операции над этой строкой.|
|SQL_BP_DROP|Закладки действительны после операции `Close`.|
|SQL_BP_SCROLL|Закладки действительны после любой операции `Move`. Этот параметр просто определяет, поддерживаются ли закладки для объекта recordset в соответствии со значением, возвращенным `CRecordset::CanBookmark`.|
|SQL_BP_TRANSACTION|Закладки являются действительными после фиксации или отката транзакции.|
|SQL_BP_UPDATE|Закладка для строки допустима после операции `Update` в этой строке.|
|SQL_BP_OTHER_HSTMT|Закладки, связанные с одним объектом recordset, действительны для второго объекта recordset.|

Дополнительные сведения об этом возвращаемом значении см. в разделе Функция API ODBC `SQLGetInfo` в Windows SDK. Дополнительные сведения о закладках см. в статье [набор записей: закладки и абсолютные позиции (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="getconnect"></a>CDatabase:: соединение

Вызовите эту функцию-член для получения строки подключения, используемой во время вызова `OpenEx` или `Open`, который подключил объект `CDatabase` к источнику данных.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Возвращаемое значение

**Const**[CString](../../atl-mfc-shared/reference/cstringt-class.md) , содержащий строку подключения, если был вызван `OpenEx` или `Open`; в противном случае — пустая строка.

### <a name="remarks"></a>Remarks

Описание того, как создается строка подключения, см. в разделе [CDatabase:: Open](#open) .

##  <a name="getcursorcommitbehavior"></a>CDatabase:: Жеткурсоркоммитбехавиор

Вызовите эту функцию-член, чтобы определить, как операция [CommitTrans](#committrans) влияет на курсоры на открытые объекты Recordset.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение, указывающее воздействие транзакций на открытые объекты набора записей. Дополнительные сведения см. в разделе "Заметки".

### <a name="remarks"></a>Remarks

В следующей таблице перечислены возможные возвращаемые значения для `GetCursorCommitBehavior` и соответствующие действия с открытым набором записей.

|Возвращаемое значение|Воздействие на объекты CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Вызовите `CRecordset::Requery` сразу после фиксации транзакции.|
|SQL_CB_DELETE|Вызовите `CRecordset::Close` сразу после фиксации транзакции.|
|SQL_CB_PRESERVE|Продолжайте работу обычно с операциями `CRecordset`.|

Дополнительные сведения об этом возвращаемом значении см. в разделе Функция API ODBC `SQLGetInfo` в Windows SDK. Дополнительные сведения о транзакциях см. в описании [транзакции статьи (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getcursorrollbackbehavior"></a>CDatabase:: Жеткурсорроллбаккбехавиор

Вызовите эту функцию-член, чтобы определить, как операция [отката](#rollback) влияет на курсоры на открытые объекты Recordset.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение, указывающее воздействие транзакций на открытые объекты набора записей. Дополнительные сведения см. в разделе "Заметки".

### <a name="remarks"></a>Remarks

В следующей таблице перечислены возможные возвращаемые значения для `GetCursorRollbackBehavior` и соответствующие действия с открытым набором записей.

|Возвращаемое значение|Воздействие на объекты CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Вызовите `CRecordset::Requery` сразу после отката транзакции.|
|SQL_CB_DELETE|Вызовите `CRecordset::Close` сразу после отката транзакции.|
|SQL_CB_PRESERVE|Продолжайте работу обычно с операциями `CRecordset`.|

Дополнительные сведения об этом возвращаемом значении см. в разделе Функция API ODBC `SQLGetInfo` в Windows SDK. Дополнительные сведения о транзакциях см. в описании [транзакции статьи (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getdatabasename"></a>CDatabase:: GetDatabaseName

Вызовите эту функцию-член, чтобы получить имя подключенной в настоящее время базы данных (при условии, что источник данных определяет именованный объект с именем "Database").

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение [CString](../../atl-mfc-shared/reference/cstringt-class.md) , содержащее имя базы данных в случае успеха; в противном случае — пустая `CString`.

### <a name="remarks"></a>Remarks

Это не то же самое, что имя источника данных (DSN), указанное в `OpenEx` или вызове `Open`. Возвращаемые `GetDatabaseName` зависит от ODBC. Как правило, база данных — это коллекция таблиц. Если у сущности есть имя, `GetDatabaseName` возвращает ее.

Например, вы должны отобразить это имя в заголовке. Если при получении имени из ODBC возникает ошибка, `GetDatabaseName` возвращает пустой `CString`.

##  <a name="isopen"></a>CDatabase:: OnOpen

Вызовите эту функцию-член, чтобы определить, подключен ли в настоящее время объект `CDatabase` к источнику данных.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если объект `CDatabase` в данный момент подключен; в противном случае — 0.

##  <a name="m_hdbc"></a>CDatabase:: m_hdbc

Содержит открытый обработчик для соединения с источником данных ODBC — "обработчик подключения".

### <a name="remarks"></a>Remarks

Обычно нет необходимости обращаться к этой переменной члена напрямую. Вместо этого, платформа выделяет этот обработчик при вызове `OpenEx` или `Open`. Платформа освобождает этот обработчик при вызове оператора **Delete** для объекта `CDatabase`. Обратите внимание, что функция члена `Close` не освобождает маркер.

Однако в некоторых случаях может потребоваться использовать этот обработчик напрямую. Например, если необходимо вызывать функции API ODBC напрямую, а не с помощью класса `CDatabase`, то для передачи в качестве параметра может потребоваться маркер соединения. См. пример кода ниже.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

##  <a name="onsetoptions"></a>CDatabase:: Онсетоптионс

Платформа вызывает эту функцию-член при непосредственном выполнении инструкции SQL с функцией-членом `ExecuteSQL`.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Параметры

*хстмт*<br/>
Обработчик инструкций ODBC, для которого задаются параметры.

### <a name="remarks"></a>Remarks

`CRecordset::OnSetOptions` также вызывает эту функцию члена.

`OnSetOptions` задает значение времени ожидания входа. При наличии предыдущих вызовов функции `SetQueryTimeout` и члена `OnSetOptions` отражает текущие значения. в противном случае устанавливаются значения по умолчанию.

> [!NOTE]
>  До MFC 4,2 `OnSetOptions` также установить режим обработки сничронаус или асинхронный. Начиная с MFC 4,2, все операции являются синхронными. Для выполнения асинхронной операции необходимо выполнить прямой вызов функции API ODBC `SQLSetPos`.

Для изменения значения времени ожидания переопределение `OnSetOptions` не требуется. Вместо этого для настройки значения времени ожидания запроса вызовите `SetQueryTimeout` перед созданием набора записей. `OnSetOptions` будет использовать новое значение. Набор значений применяется к следующим операциям со всеми наборами записей или прямыми вызовами SQL.

Переопределите `OnSetOptions`, если требуется задать дополнительные параметры. Переопределение должно вызывать базовый класс `OnSetOptions` либо до, либо после вызова функции API ODBC `SQLSetStmtOption`. Выполните метод, показанный в реализации платформы по умолчанию `OnSetOptions`.

##  <a name="open"></a>CDatabase:: Open

Вызовите эту функцию-член для инициализации вновь созданного объекта `CDatabase`.

```
virtual BOOL Open(
    LPCTSTR lpszDSN,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T("ODBC;"),
    BOOL bUseCursorLib = TRUE);
```

### <a name="parameters"></a>Параметры

*лпсздсн*<br/>
Указывает имя источника данных — имя, зарегистрированное в ODBC с помощью программы администрирования ODBC. Если значение DSN указано в *лпсзконнект* (в формате dsn =\<Data-Source > "), оно не должно быть указано повторно в *лпсздсн*. В этом случае *лпсздсн* должно иметь значение null. В противном случае можно передать значение NULL, если необходимо предоставить пользователю диалоговое окно Источник данных, в котором пользователь может выбрать источник данных. Дополнительные сведения см. в разделе Примечания.

*бексклусиве*<br/>
Не поддерживается в этой версии библиотеки классов. В настоящее время утверждение не выполняется, если этот параметр имеет значение TRUE. Источник данных всегда открывается как общий (не эксклюзивный).

*бреадонли*<br/>
Значение TRUE, если необходимо, чтобы соединение было доступно только для чтения и запрещено обновление источника данных. Этот атрибут наследуется всеми зависимыми наборами записей. Значение по умолчанию — FALSE.

*лпсзконнект*<br/>
Задает строку подключения. Строка подключения объединяет сведения, возможно, включая имя источника данных, идентификатор пользователя, допустимый в источнике данных, строку проверки подлинности пользователя (пароль, если источник данных требует один) и другие сведения. Строка подключения целиком должна иметь префикс "ODBC;" (прописные или строчные буквы). Строка "ODBC;" используется, чтобы указать, что соединение относится к источнику данных ODBC. Это обеспечивает совместимость с предыдущими версиями, когда в будущих версиях библиотеки классов могут поддерживаться источники данных, не относящиеся к ODBC.

*бусекурсорлиб*<br/>
Значение TRUE, если требуется загрузить библиотеку DLL ODBC Cursor. Библиотека курсоров маскирует некоторые функциональные возможности базового драйвера ODBC, что позволяет избежать использования динамических подмножеств (если они поддерживаются драйвером). Единственными курсорами, поддерживаемыми при загрузке библиотеки курсоров, являются статические моментальные снимки и однопроходные курсоры. Значение по умолчанию — TRUE. Если вы планируете создать объект набора записей непосредственно из `CRecordset` без наследования от него, то не следует загружать библиотеку курсора.

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если соединение установлено успешно; в противном случае 0, если пользователь выбрал Cancel (Отмена) при отображении диалогового окна с запросом на дополнительные сведения о подключении. Во всех остальных случаях платформа создает исключение.

### <a name="remarks"></a>Remarks

Объект базы данных должен быть инициализирован, прежде чем его можно будет использовать для создания объекта набора записей.

> [!NOTE]
>  Вызов функции-члена [опенекс](#openex) является предпочтительным способом подключения к источнику данных и инициализации объекта базы данных.

Если параметры в вызове `Open` не содержат достаточно сведений для подключения, драйвер ODBC открывает диалоговое окно для получения необходимых сведений от пользователя. При вызове `Open`строка подключения *лпсзконнект*сохраняется в частном порядке в объекте `CDatabase` и доступна путем вызова функции-члена [соединения](#getconnect) .

При желании можно открыть собственное диалоговое окно перед вызовом `Open` для получения сведений от пользователя, например пароля, а затем добавить эти сведения в строку подключения, которая передается `Open`. Вы также можете сохранить переданную строку подключения, чтобы ее можно было повторно использовать при следующем вызове приложения `Open` для объекта `CDatabase`.

Можно также использовать строку подключения для нескольких уровней авторизации имени входа (для каждого другого объекта `CDatabase`) или для передачи других сведений, относящихся к источнику данных. Дополнительные сведения о строках подключения см. в главе 5 в Windows SDK.

Время ожидания соединения может истекает, если, например, узел СУБД недоступен. Если попытка подключения завершается неудачей, `Open` создает исключение `CDBException`.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

##  <a name="openex"></a>CDatabase:: Опенекс

Вызовите эту функцию-член для инициализации вновь созданного объекта `CDatabase`.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>Параметры

*лпсзконнектстринг*<br/>
Указывает строку подключения ODBC. Сюда входит имя источника данных, а также другие дополнительные сведения, такие как идентификатор пользователя и пароль. Например, "DSN = SQLServer_Source; UID = SA; PWD = abc123 "— это возможная строка подключения. Обратите внимание, что при передаче значения NULL для *лпсзконнектстринг*диалоговое окно Источник данных предложит пользователю выбрать источник данных.

*двоптионс*<br/>
Битовая маска, которая задает сочетание следующих значений. Значение по умолчанию равно 0, что означает, что база данных будет открываться совместно с доступом для записи, Библиотека DLL курсора ODBC не будет загружена, а диалоговое окно соединение ODBC отобразится только в том случае, если не хватает сведений для подключения.

- `CDatabase::openExclusive` не поддерживается в этой версии библиотеки классов. Источник данных всегда открывается как общий (не эксклюзивный). В настоящее время утверждение не выполняется, если указан этот параметр.

- `CDatabase::openReadOnly` открыть источник данных как "только для чтения".

- `CDatabase::useCursorLib` загрузить библиотеку DLL ODBC Cursor. Библиотека курсоров маскирует некоторые функциональные возможности базового драйвера ODBC, что позволяет избежать использования динамических подмножеств (если они поддерживаются драйвером). Единственными курсорами, поддерживаемыми при загрузке библиотеки курсоров, являются статические моментальные снимки и однопроходные курсоры. Если вы планируете создать объект набора записей непосредственно из `CRecordset` без наследования от него, то не следует загружать библиотеку курсора.

- `CDatabase::noOdbcDialog` не отображать диалоговое окно соединение ODBC, независимо от того, задано ли достаточное количество сведений о соединении.

- `CDatabase::forceOdbcDialog` всегда отображать диалоговое окно соединение ODBC.

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если соединение установлено успешно; в противном случае 0, если пользователь выбрал Cancel (Отмена) при отображении диалогового окна с запросом на дополнительные сведения о подключении. Во всех остальных случаях платформа создает исключение.

### <a name="remarks"></a>Remarks

Объект базы данных должен быть инициализирован, прежде чем его можно будет использовать для создания объекта набора записей.

Если параметр *лпсзконнектстринг* в вызове `OpenEx` не содержит достаточно сведений для подключения, драйвер ODBC открывает диалоговое окно для получения необходимых сведений от пользователя при условии, что в параметре *двоптионс* не задано `CDatabase::noOdbcDialog` или `CDatabase::forceOdbcDialog`. При вызове `OpenEx`строка подключения *лпсзконнектстринг*сохраняется в частном порядке в объекте `CDatabase` и доступна путем вызова функции-члена [соединения](#getconnect) .

При желании можно открыть собственное диалоговое окно перед вызовом `OpenEx` для получения сведений от пользователя, например пароля, а затем добавить эти сведения в строку подключения, которая передается `OpenEx`. Вы также можете сохранить переданную строку подключения, чтобы ее можно было повторно использовать при следующем вызове приложения `OpenEx` для объекта `CDatabase`.

Можно также использовать строку подключения для нескольких уровней авторизации имени входа (для каждого другого объекта `CDatabase`) или для передачи других сведений, относящихся к источнику данных. Дополнительные сведения о строках подключения см. в главе 6 *Справочника программиста по ODBC*.

Время ожидания соединения может истекает, если, например, узел СУБД недоступен. Если попытка подключения завершается неудачей, `OpenEx` создает исключение `CDBException`.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

##  <a name="rollback"></a>CDatabase:: ROLLBACK

Вызовите эту функцию-член, чтобы отменить изменения, внесенные во время транзакции.

```
BOOL Rollback();
```

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если транзакция была успешно отменена. в противном случае — 0. Если `Rollback` вызов завершается неудачей, источник данных и состояния транзакции не определены. Если `Rollback` возвращает значение 0, необходимо проверить источник данных, чтобы определить его состояние.

### <a name="remarks"></a>Remarks

Все вызовы `CRecordset` `AddNew`, `Edit`, `Delete`и `Update`, выполненные с момента последнего [примеры BeginTrans](#begintrans) , откатываются в состояние, существовавшее во время этого вызова.

После вызова `Rollback`транзакция превышена, и необходимо вызвать `BeginTrans` еще раз для другой транзакции. Запись, которая была текущей до вызова `BeginTrans`, снова станет текущей записью после `Rollback`.

После отката запись, которая была текущей до отката, остается актуальной. Дополнительные сведения о состоянии набора записей и источника данных после отката см. в разделе [транзакция статьи (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Пример

  См. статью [транзакция: выполнение транзакции в наборе записей (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="setlogintimeout"></a>CDatabase:: SetLoginTimeout

Вызовите эту функцию-член — перед вызовом `OpenEx` или `Open` — для переопределения количества секунд, разрешенного по умолчанию до истечения времени ожидания соединения с источником данных.

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Параметры

*двсекондс*<br/>
Количество секунд, которое необходимо разрешить до истечения времени ожидания попытки соединения.

### <a name="remarks"></a>Remarks

Возможно, время ожидания попытки соединения истекает, если, например, СУБД недоступна. Вызовите `SetLoginTimeout` после создания неинициализированного `CDatabase` объекта, но перед вызовом `OpenEx` или `Open`.

Значение по умолчанию для времени ожидания входа составляет 15 секунд. Не все источники данных поддерживают возможность указания значения времени ожидания входа. Если источник данных не поддерживает время ожидания, вы получаете выходные данные трассировки, но не исключение. Значение 0 означает «бесконечность».

##  <a name="setquerytimeout"></a>CDatabase:: Getquerytimeout

Вызовите эту функцию члена, чтобы переопределить количество секунд по умолчанию, которое будет разрешено до истечения времени ожидания последующих операций в подключенном источнике данных.

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Параметры

*двсекондс*<br/>
Количество секунд, которое необходимо разрешить до истечения времени ожидания попытки запроса.

### <a name="remarks"></a>Remarks

Время ожидания операции может истекает из-за проблем с доступом к сети, чрезмерного времени обработки запросов и т. д. Вызовите `SetQueryTimeout` перед открытием набора записей или до вызова функций `AddNew`, `Update` или `Delete` набора записей, если требуется изменить значение времени ожидания запроса. Этот параметр влияет на все последующие `Open`, `AddNew`, `Update`и `Delete` вызовы к любым наборам записей, связанным с этим объектом `CDatabase`. Изменение значения времени ожидания запроса после открытия не приводит к изменению значения для набора записей. Например, последующие операции `Move` не используют новое значение.

Значение времени ожидания запроса по умолчанию — 15 секунд. Не все источники данных поддерживают возможность установки значения времени ожидания запроса. Если задать значение времени ожидания запроса 0, время ожидания не произойдет; связь с источником данных может перестать отвечать на запросы. Такое поведение может быть полезно во время разработки. Если источник данных не поддерживает время ожидания, вы получаете выходные данные трассировки, но не исключение.

## <a name="see-also"></a>См. также раздел

[Класс CObject](../../mfc/reference/cobject-class.md)<br/>
[Диаграмма иерархии](../../mfc/hierarchy-chart.md)<br/>
[Класс CRecordset](../../mfc/reference/crecordset-class.md)
