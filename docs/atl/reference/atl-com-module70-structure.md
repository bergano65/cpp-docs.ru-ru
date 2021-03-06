---
title: Структура _ATL_COM_MODULE70
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
ms.openlocfilehash: c6361fc5374ed732cd9ccbfbbd1d3d1c2fc8f1f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261043"
---
# <a name="atlcommodule70-structure"></a>Структура _ATL_COM_MODULE70

Используемый код, связанный с COM в ATL

## <a name="syntax"></a>Синтаксис

```
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```

## <a name="members"></a>Участники

`cbSize`<br/>
Размер структуры, используемые для управления версиями.

`m_hInstTypeLib`<br/>
Дескриптор экземпляра, в библиотеку типов для этого модуля.

`m_ppAutoObjMapFirst`<br/>
Адрес элемента массива, который задает начало карты записей объект для этого модуля.

`m_ppAutoObjMapLast`<br/>
Адрес элемента массива, указывающий на конец записи сопоставления объекта для этого модуля.

`m_csObjMap`<br/>
Критический раздел для сериализации доступа к записям объекта карты. Используется системой ATL.

## <a name="remarks"></a>Примечания

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) определяется как typedef типа _ATL_COM_MODULE70.

## <a name="requirements"></a>Требования

**Заголовок:** atlbase.h

## <a name="see-also"></a>См. также

[Классы и структуры](../../atl/reference/atl-classes.md)
