---
title: Извлечение двоичного объекта (BLOB)
ms.date: 10/24/2018
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
ms.openlocfilehash: 23bc20355e1e2b17ac20cf975df2ff58d6553ef9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404550"
---
# <a name="retrieving-a-blob"></a>Извлечение двоичного объекта (BLOB)

Можно получить большой двоичный объект (BLOB) по-разному. Можно использовать `DBTYPE_BYTES` для получения большого двоичного ОБЪЕКТА как последовательность байтов, или использовать интерфейс, как `ISequentialStream`. Дополнительные сведения см. в разделе [большие двоичные ОБЪЕКТЫ и объекты OLE](/previous-versions/windows/desktop/ms711511(v=vs.85)) в **Справочник программиста OLE DB по**.

Следующий код показывает способ получения BLOB-ОБЪЕКТОВ с помощью `ISequentialStream`. Макрос [BLOB_ENTRY](../../data/oledb/blob-entry.md) позволяет указать интерфейс и флаги, используемые для интерфейса. После открытия таблицы, код вызывает `Read` несколько раз на `ISequentialStream` для чтения байтов из большого двоичного ОБЪЕКТА. Этот код вызывает `Release` для указателя интерфейса, перед вызовом dispose `MoveNext` для получения следующей записи.

```cpp
class CCategories
{
public:
   ISequentialStream* pPicture;

BEGIN_COLUMN_MAP(CCategories)
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)
END_COLUMN_MAP()
};
```

После этого используется следующий код:

```cpp
CTable<CAccessor<CCategories>> categories;
ULONG cb;
BYTE myBuffer[65536];

categories.Open(session, "Categories");

while (categories.MoveNext() == S_OK)
{
   do
   {
      categories.pPicture->Read(myBuffer, 65536, &cb);
      // Do something with the buffer
   } while (cb > 0);
   categories.pPicture->Release();
}
```

Дополнительные сведения о макросах, которые обрабатывают данные больших двоичных ОБЪЕКТОВ см. в разделе **макросы сопоставления столбца** в [макросы и глобальные функции для шаблонов потребителей OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

## <a name="see-also"></a>См. также

[Использование методов доступа](../../data/oledb/using-accessors.md)<br/>
[Макросы и глобальные функции для шаблонов объектов-получателей OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
