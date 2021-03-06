---
title: log2, log2f, log2l
ms.date: 04/05/2018
api_name:
- log2
- log2l
- log2f
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: bf1734ea2f96fa1c09b3b0d1f43b681fc31c8f9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953159"
---
# <a name="log2-log2f-log2l"></a>log2, log2f, log2l

Определяет двоичный логарифм (по основанию 2) для указанного значения.

## <a name="syntax"></a>Синтаксис

```C
double log2(
   double x
);

float log2(
   float x
); //C++ only

long double log2(
   long double x
); //C++ only

float log2f(
   float x
);

long double log2l(
   long double x
);
```

### <a name="parameters"></a>Параметры

*x*<br/>
Значение, для которого вычисляется логарифм по основанию 2.

## <a name="return-value"></a>Возвращаемое значение

При успешном выполнении возвращает значение log2 *x*.

В случае неудачи может возвращать одно из следующих значений:

|Проблемы|Назад|
|-----------|------------|
|*x* < 0|NaN|
|*x* = ± 0|-INFINITY|
|*x* = 1|+0|
|+INFINITY|+INFINITY|
|NaN|NaN|
|ошибка домена|NaN|
|Ошибка полюса|-HUGE_VAL, -HUGE_VALF или -HUGE_VALL|

Ошибки сообщаются, как указано в [_matherr](matherr.md).

## <a name="remarks"></a>Примечания

Если x является целым числом, эта функция фактически возвращает отсчитываемый от нуля индекс наиболее значимого 1 бита *x*.

## <a name="requirements"></a>Требования

|Функция|Заголовок C|Заголовок C++|
|--------------|--------------|------------------|
|**log2**, **log2f**, **log2l**|\<math.h>|\<cmath>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также

[Алфавитный указатель функций](crt-alphabetical-function-reference.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
