---
title: Platform::IDisposable - интерфейс
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
ms.openlocfilehash: f114959321c0ed3879a089b944a5ff1b19843118
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257833"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable - интерфейс

Используется для освобождения неуправляемых ресурсов.

## <a name="syntax"></a>Синтаксис

```cpp
public interface class IDisposable
```

## <a name="attributes"></a>Атрибуты

**GuidAttribute**(«de0cbaea-8065-4a45-b196-c9d443f9bab3»)

**VersionAttribute**(NTDDI_WIN8)

### <a name="members"></a>Участники

Интерфейс IDisposable наследует от интерфейса IUnknown. Интерфейс IDisposable также имеет следующие типы членов.

**Методы**

Интерфейс IDisposable содержит следующие методы.

|Метод|Описание|
|------------|-----------------|
|Ликвидировать|Используется для освобождения неуправляемых ресурсов.|

### <a name="requirements"></a>Требования

**Минимальный поддерживаемый клиент:** Windows 8

**Минимальный поддерживаемый сервер:** Windows Server 2012

**Пространство имен:** Platform