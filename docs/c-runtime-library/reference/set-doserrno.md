---
title: _set_doserrno
ms.date: 11/04/2016
api_name:
- _set_doserrno
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_doserrno
- set_doserrno
helpviewer_keywords:
- _set_doserrno function
- doserrno global variable
- set_doserrno function
- _doserrno global variable
ms.assetid: 8686c159-3797-4705-a53e-7457869ca6f3
ms.openlocfilehash: e4060992477e5d30dfad0725948cbc719b4d0270
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948617"
---
# <a name="_set_doserrno"></a>_set_doserrno

Задает значение глобальной переменной [_doserrno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="syntax"></a>Синтаксис

```C
errno_t _set_doserrno( int error_value );
```

### <a name="parameters"></a>Параметры

*error_value*<br/>
Новое значение **_doserrno**.

## <a name="return-value"></a>Возвращаемое значение

Возвращает нуль при успешном завершении.

## <a name="remarks"></a>Примечания

Возможные значения макроса определяются в Errno.h.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|Необязательный заголовок|
|-------------|---------------------|---------------------|
|**_set_doserrno**|\<stdlib.h>|\<errno.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также

[_get_doserrno](get-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
