---
title: Класс allocator_suballoc
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 3e5b69ef3f47a173ef768283bbae4f6e3b5f5190
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458143"
---
# <a name="allocatorsuballoc-class"></a>Класс allocator_suballoc

Описывает объект, управляющий выделением и освобождением памяти для объектов типа *Type* , использующих кэш типа [cache_suballoc](../standard-library/cache-suballoc-class.md).

## <a name="syntax"></a>Синтаксис

```cpp
template <class Type>
class allocator_suballoc;
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|*Type*|Тип элементов, распределяемых распределителем.|

## <a name="remarks"></a>Примечания

Макрос [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) передает этот класс в качестве параметра *Name* в следующей инструкции:`ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>Требования

**Заголовок:** \<allocators>

**Пространство имен:** stdext

## <a name="see-also"></a>См. также

[\<allocators>](../standard-library/allocators-header.md)
