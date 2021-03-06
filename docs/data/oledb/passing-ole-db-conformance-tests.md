---
title: Проверка на совместимость с OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
ms.openlocfilehash: 9f78b16bc30651560137a39286460a8e5ceccd40
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282820"
---
# <a name="passing-ole-db-conformance-tests"></a>Проверка на совместимость с OLE DB

Чтобы сделать более согласованным поставщиков, Data Access SDK предоставляет набор тестов на совместимость с OLE DB. Тесты проверяют все аспекты вашего поставщика и дают возможность степени быть уверены, функционирует как ожидалось. Проверка на совместимость OLE DB можно найти на Microsoft Data Access SDK. В этом разделе описываются действия, которые следует выполнить для проверки на совместимость. Сведения о выполнении тестов на совместимость OLE DB см. в SDK.

## <a name="running-the-conformance-tests"></a>Выполнение тестов на совместимость

В Visual C++ 6.0 шаблоны поставщика OLE DB добавлен ряд функций привязки, которые позволяют проверять значения и свойства. Большая часть этих функций были добавлены в ответ тестов на совместимость.

> [!NOTE]
> Необходимо добавить несколько функций проверки для поставщика для проверки на совместимость OLE DB.

Для этого поставщика требуется две процедуры проверки. Первая программа, `CRowsetImpl::ValidateCommandID`, является частью класса набора строк. Она вызывается во время создания набора строк с помощью шаблонов поставщика. В образце используется эта подпрограмма для информирования потребителей, что он не поддерживает индексы. Первый вызов направляется `CRowsetImpl::ValidateCommandID` (Обратите внимание, что поставщик использует `_RowsetBaseClass` typedef, добавлены в схему интерфейсов для `CCustomRowset` в [Поддержка закладок поставщиками](../../data/oledb/provider-support-for-bookmarks.md), поэтому нет необходимости необходимость ввода длинной строки шаблона аргументы). Возвращается значение DB_E_NOINDEX Далее, в том случае, если параметр индекса не принимают значение NULL, (это означает, что потребитель будет использовать индекс). Дополнительные сведения о идентификаторы команд см. в спецификации OLE DB и найдите `IOpenRowset::OpenRowset`.

В следующем коде приведен `ValidateCommandID` процедуры проверки:

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H
// Class: CCustomRowset

HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)
{
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);
   if (hr != S_OK)
      return hr;

   if (pIndexID != NULL)
      return DB_E_NOINDEX;    // Doesn't support indexes

   return S_OK;
}
```

Шаблоны поставщика вызывают `OnPropertyChanged` метод всякий раз, когда кто-то изменяет свойство на группе DBPROPSET_ROWSET. Если вы хотите обрабатывать свойства для других групп, можно добавить их в соответствующий объект (то есть DBPROPSET_SESSION проверок перейдите `CCustomSession` класса).

Код сначала проверяет, связано ли свойство в другой. Если свойство является, оно устанавливает свойство DBPROP_BOOKMARKS `True`. Приложение В спецификации OLE DB содержит сведения о свойствах. Эти сведения также сообщает ли свойство привязанной к другой.

Вы также можете добавить `IsValidValue` в код. Шаблоны вызывают `IsValidValue` при попытке задать свойство. Нужно переопределить этот метод, если требуется дополнительная обработка при задании значения свойства. Вы может иметь одно из этих методов для каждого набора свойств.

## <a name="see-also"></a>См. также

[Дополнительные способы использования поставщика](../../data/oledb/advanced-provider-techniques.md)