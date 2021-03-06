---
title: _isatty
ms.date: 11/04/2016
api_name:
- _isatty
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _isatty
helpviewer_keywords:
- isatty function
- character device checking
- _isatty function
- checking character devices
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
ms.openlocfilehash: 2d2ba2fdfeb1c8bffe47b0953f0629746d2eb599
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954556"
---
# <a name="_isatty"></a>_isatty

Определяет, связан ли дескриптор файла с устройством символьного ввода-вывода.

## <a name="syntax"></a>Синтаксис

```C
int _isatty( int fd );
```

### <a name="parameters"></a>Параметры

*fd*<br/>
Дескриптор файла, ссылающийся на проверяемое устройство.

## <a name="return-value"></a>Возвращаемое значение

**_isatty** возвращает ненулевое значение, если дескриптор связан с символьным устройством. В противном случае **_isatty** возвращает 0.

## <a name="remarks"></a>Примечания

Функция **_isatty** определяет, связана ли *демон* установки с символьным устройством (терминалом, консолью, принтером или последовательным портом).

Эта функция проверяет параметр *демона* . Если « *демон* » является неверным указателем на файл, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, функция возвращает 0 **и устанавливает для** **значение EBADF**значение.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_isatty**|\<io.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Библиотеки

Все версии [библиотек времени выполнения языка C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Пример

```C
// crt_isatty.c
/* This program checks to see whether
* stdout has been redirected to a file.
*/

#include <stdio.h>
#include <io.h>

int main( void )
{
   if( _isatty( _fileno( stdout ) ) )
      printf( "stdout has not been redirected to a file\n" );
   else
      printf( "stdout has been redirected to a file\n");
}
```

### <a name="sample-output"></a>Пример результатов выполнения

```Output
stdout has not been redirected to a file
```

## <a name="see-also"></a>См. также

[Обработка файлов](../../c-runtime-library/file-handling.md)<br/>
