---
title: _spawnle, _wspawnle
ms.date: 11/04/2016
api_name:
- _spawnle
- _wspawnle
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
- api-ms-win-crt-process-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _spawnle
- wspawnle
- _wspawnle
helpviewer_keywords:
- spawnle function
- processes, creating
- _wspawnle function
- processes, executing new
- process creation
- wspawnle function
- _spawnle function
ms.assetid: 80308892-2815-49b1-8cca-53894c366f5a
ms.openlocfilehash: 9d3c97f5fb7f98a2c045b3f5657211b3866c4b78
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442727"
---
# <a name="_spawnle-_wspawnle"></a>_spawnle, _wspawnle

Создает и выполняет новый процесс.

> [!IMPORTANT]
> Этот API нельзя использовать в приложениях, выполняемых в среде выполнения Windows. Дополнительные сведения: [Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Синтаксис

```C
intptr_t _spawnle(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wspawnle(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Параметры

*mode*<br/>
Режим выполнения для вызывающего процесса.

*кмднаме*<br/>
Путь к выполняемому файлу.

*arg0*, *arg1*,... *argN*<br/>
Список указателей на аргументы. Аргумент *arg0* обычно является указателем на *кмднаме*. Аргументы *arg1* – *argN* — это указатели на символьные строки, формирующие новый список аргументов. В *следующих случаях*для обозначения конца списка аргументов должен быть **пустой** указатель.

*envp*<br/>
Массив указателей на параметры среды.

## <a name="return-value"></a>Возвращаемое значение

Возвращаемое значение из синхронного **_spawnle** или **_wspawnle** ( **_P_WAIT** , заданное для *режима*) — это состояние выхода нового процесса. Возвращаемое значение из асинхронного **_spawnle** или **_wspawnle** ( **_P_NOWAIT** или **_P_NOWAITO** , заданное для *режима*) — это обработчик процесса. Состояние выхода имеет значение 0, если процесс завершился обычным образом. Можно задать для состояния выхода ненулевое значение, если порожденный процесс явно вызывает процедуру **выхода** с ненулевым аргументом. Если новый процесс не задал положительное состояние выхода в явном виде, положительное состояние выхода указывает на аварийный выход по отмене или прерыванию. Возвращаемое значение, равное-1, указывает на ошибку (новый процесс не запущен). В этом случае для **параметра «значение возврата»** задается одно из следующих значений.

|||
|-|-|
| **E2BIG** | Длина списка аргументов превышает 1024 байта. |
| **EINVAL** | Недопустимый аргумент *mode* . |
| **ENOENT** | Файл или путь не найден. |
| **ENOEXEC** | Указанный файл не является исполняемым или имеет недопустимый формат исполняемого файла. |
| **ENOMEM** | Недостаточно памяти для выполнения нового процесса. |

Дополнительные сведения об этих и других кодах возврата см. в разделе [_doserrno, errno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Remarks

Каждая из этих функций создает и выполняет новый процесс и передает каждый аргумент командной строки как отдельный параметр, а также передает массив указателей на параметры среды.

Эти функции проверяют свои параметры. Если *кмднаме* или *arg0* является пустой строкой или пустым указателем, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эти функции **устанавливают** значение **еинвал**и возвращают-1. Нет порожденных новых процессов.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_spawnle**|\<process.h>|
|**_wspawnle**|\<stdio.h> или \<wchar.h>|

Дополнительные сведения о совместимости см. в статье [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

См. пример в разделе [Функции _spawn, _wspawn](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>См. также раздел

[Управление процессами и средой](../../c-runtime-library/process-and-environment-control.md)<br/>
[Функции _spawn, _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[Функции _exec, _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
