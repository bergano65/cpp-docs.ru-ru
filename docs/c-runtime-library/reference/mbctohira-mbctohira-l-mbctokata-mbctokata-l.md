---
title: _mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l
ms.date: 11/04/2016
api_name:
- _mbctohira
- _mbctohira_l
- _mbctokata
- _mbctokata_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbctokata
- mbctohira
- _mbctohira
- _mbctohira_l
- mbctokata
- mbctokata_l
- mbctohira_l
- _mbctokata_l
helpviewer_keywords:
- _mbctokata function
- _mbctokata_l function
- _mbctohira_l function
- mbctohira_l function
- mbctohira function
- mbctokata_l function
- _mbctohira function
- mbctokata function
ms.assetid: f949afd7-44d4-4f08-ac8f-1fef2c915a1c
ms.openlocfilehash: 6e158e933442256b1d712ba42afc28b94e2b123c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952548"
---
# <a name="_mbctohira-_mbctohira_l-_mbctokata-_mbctokata_l"></a>_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l

Преобразует символы хирагана в катакана и наоборот.

> [!IMPORTANT]
> Этот API нельзя использовать в приложениях, выполняемых в среде выполнения Windows. Дополнительные сведения: [Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Синтаксис

```C
unsigned int _mbctohira(
   unsigned int c
);
unsigned int _mbctohira_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbctokata(
   unsigned int c
);
unsigned int _mbctokata_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Параметры

*c*<br/>
Многобайтовый символ для преобразования.

*locale*<br/>
Используемый языковой стандарт.

## <a name="return-value"></a>Возвращаемое значение

Каждая из этих функций возвращает преобразованный символ *c*, если это возможно. В противном случае возвращается символ *c* без изменений.

## <a name="remarks"></a>Примечания

Функции **_mbctohira** и **_mbctokata** проверяют символ *c* и, если это возможно, применяют одно из следующих преобразований.

|Подпрограммы|Преобразования|
|--------------|--------------|
|**_mbctohira**, **_mbctohira_l**|Многобайтовые символы катакана в многобайтовые символы хирагана.|
|**_mbctokata**, **_mbctokata_l**|Многобайтовые символы хирагана в многобайтовые символы катакана.|

Выходное значение зависит от настройки категории **LC_CTYPE** языкового стандарта; дополнительные сведения см. в разделе [setlocale](setlocale-wsetlocale.md). Версии этих функций идентичны, за исключением того, что не имеют суффикса **_l** , используют текущий языковой стандарт для этого поведения, зависящего от языкового стандарта, и те, у которых есть суффикс **_l** , вместо этого используют переданный параметр языкового стандарта. Для получения дополнительной информации см. [Locale](../../c-runtime-library/locale.md).

В более ранних версиях **_mbctohira** назывался **жтохира** и **_mbctokata** назывался **жтоката**. В новом коде используйте новые имена.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_mbctohira**|\<mbstring.h>|
|**_mbctohira_l**|\<mbstring.h>|
|**_mbctokata**|\<mbstring.h>|
|**_mbctokata_l**|\<mbstring.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также

[Преобразование данных](../../c-runtime-library/data-conversion.md)<br/>
[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>
[_mbctombb, _mbctombb_l](mbctombb-mbctombb-l.md)<br/>
