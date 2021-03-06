---
title: gmtime_s, _gmtime32_s, _gmtime64_s
ms.date: 11/04/2016
api_name:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
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
- api-ms-win-crt-time-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _gmtime_s
- gmtime64_s
- gmtime32_s
- _gmtime64_s
- gmtime_s
- _gmtime32_s
helpviewer_keywords:
- gmtime_s function
- gmtime32_s function
- time functions
- gmtime64_s function
- _gmtime64_s function
- time structure conversion
- _gmtime_s function
- _gmtime32_s function
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
ms.openlocfilehash: bcfc512022393c6a3e8a9cd97efe96d03b4877ab
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954843"
---
# <a name="gmtime_s-_gmtime32_s-_gmtime64_s"></a>gmtime_s, _gmtime32_s, _gmtime64_s

Преобразует значение времени в структуру **TM** . Это версии функций [_gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md) с усовершенствованной безопасностью, как описано в разделе [Усовершенствования безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Синтаксис

```C
errno_t gmtime_s(
   struct tm* tmDest,
   const __time_t* sourceTime
);
errno_t _gmtime32_s(
   struct tm* tmDest,
   const __time32_t* sourceTime
);
errno_t _gmtime64_s(
   struct tm* tmDest,
   const __time64_t* sourceTime
);
```

### <a name="parameters"></a>Параметры

*тмдест*<br/>
Указатель на структуру [TM](../../c-runtime-library/standard-types.md) . Поля возвращаемой структуры содержат вычисленное значение аргумента *таймера* в формате UTC, а не в местном времени.

*саурцетиме*<br/>
Указатель на сохраненное время. Время представляется в виде секунд, истекших после полуночи (00:00:00) 1-го января 1970 года, время в формате UTC.

## <a name="return-value"></a>Возвращаемое значение

Нуль при успешном завершении. В случае сбоя возвращаемое значение представляет собой код ошибки. Коды ошибок определены в файле Errno.h; список этих ошибок см. в разделе [errno](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Условия ошибок

|*тмдест*|*саурцетиме*|Назад|Значение в *тмдест*|
|-----------|------------|------------|--------------------|
|**NULL**|Любое действие|**EINVAL**|Без изменений.|
|Not **null** (указывает на допустимый объем памяти)|**NULL**|**EINVAL**|Во всех полях заданы значения –1.|
|не **null**|< 0|**EINVAL**|Во всех полях заданы значения –1.|

В случае первых двух условий ошибки вызывается обработчик недопустимого параметра, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эти функции **устанавливают** значение **еинвал** и возвращают **еинвал**.

## <a name="remarks"></a>Примечания

Функция **_gmtime32_s** разбивает значение *саурцетиме* и сохраняет его в структуре типа **TM**, определенной в Time. h. Адрес структуры передается в *тмдест*. Значение *саурцетиме* обычно получается из вызова функции [времени](time-time32-time64.md) .

> [!NOTE]
> Целевая среда должна попытаться определить, действует ли летнее время. Библиотека времени выполнения C принимает правила США для реализации вычисления летнего времени.

Каждое из полей структуры имеет тип **int**, как показано в следующей таблице.

|Поле|Описание|
|-|-|
|**tm_sec**|Секунд после минуты (0-59).|
|**tm_min**|Минут после часа (0-59).|
|**tm_hour**|Часы с полуночи (0-23).|
|**tm_mday**|День месяца (1-31).|
|**tm_mon**|Месяц (0-11; Январь = 0).|
|**tm_year**|Год (текущий год минус 1900).|
|**tm_wday**|День недели (0-6; Воскресенье = 0).|
|**tm_yday**|День года (0-365; 1 января = 0).|
|**tm_isdst**|Значение всегда равно 0 для **gmtime_s**.|

**_gmtime64_s**, который использует структуру **__time64_t** , позволяет выражать даты до 23:59:59, 31 декабря 3000, UTC; в то время как **gmtime32_s** представляют даты только до 23:59:59 18 января 2038, UTC. Полночь 1-го января 1970 года — нижняя граница диапазона дат для обеих функций.

**gmtime_s** — это встроенная функция, которая возвращает **_gmtime64_s** и **time_t** эквивалентна **__time64_t**. Если необходимо заставить компилятор интерпретировать **time_t** как старый 32-разрядный **time_t**, можно определить **_USE_32BIT_TIME_T**. Это приведет к тому, что **gmtime_s** будет встроен в **_gmtime32_s**. Это не рекомендуется, поскольку приложение может завершиться с ошибкой после 18-го января 2038 года, и не поддерживается на 64-разрядных платформах.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок C|Обязательный заголовок C++|
|-------------|---------------------|-|
|**gmtime_s**, **_gmtime32_s**, **_gmtime64_s**|\<time.h>|\<CTime > или \<Time. h >|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_gmtime64_s.c
// This program uses _gmtime64_s to convert a 64-bit
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime_s to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm newtime;
   __int64 ltime;
   char buf[26];
   errno_t err;

   _time64( &ltime );

   // Obtain coordinated universal time:
   err = _gmtime64_s( &newtime, &ltime );
   if (err)
   {
      printf("Invalid Argument to _gmtime64_s.");
   }

   // Convert to an ASCII representation
   err = asctime_s(buf, 26, &newtime);
   if (err)
   {
      printf("Invalid Argument to asctime_s.");
   }

   printf( "Coordinated universal time is %s\n",
           buf );
}
```

```Output
Coordinated universal time is Fri Apr 25 20:12:33 2003
```

## <a name="see-also"></a>См. также

[Управление временем](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
