---
title: InP, _inp, инпв, _inpw, _inpd
description: Описывает устаревшие и удаленные функции InP, _inp, инпв, _inpw и _inpd библиотеки времени выполнения Microsoft C (CRT).
ms.date: 12/09/2019
api_name:
- inp
- inpw
- _inp
- _inpw
- _inpd
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- inp
- inpw
- _inp
- _inpw
- _inpd
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
ms.openlocfilehash: 48e0e58d2886c5a8bb90a86c81cb785d364666e8
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988711"
---
# <a name="inp-_inp-inpw-_inpw-_inpd"></a>InP, _inp, инпв, _inpw, _inpd

Входные данные, из порта, байт (`inp`, `_inp`), слово (`inpw`, `_inpw`) или двойное слово (`_inpd`).

> [!IMPORTANT]
> Эти функции устарели. Начиная с Visual Studio 2015 они недоступны в CRT.  
> Этот API нельзя использовать в приложениях, выполняемых в среде выполнения Windows. Дополнительные сведения: [Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Синтаксис

```cpp
int _inp(
   unsigned short port
);
unsigned short _inpw(
   unsigned short port
);
unsigned long _inpd(
   unsigned short port
);
```

### <a name="parameters"></a>Параметры

\ *порта*
Номер порта ввода-вывода.

## <a name="return-value"></a>Возвращаемое значение

Эти функции возвращают байт, слово или двойное слово, прочитанное из порта `port`. Ошибка не возвращается.

## <a name="remarks"></a>Заметки

Функции `_inp`, `_inpw`и `_inpd` считывают из указанного порта байт, слово и двойное слово соответственно. Входное значение может быть любым беззнаковым коротким целым числом в диапазоне от 0 до 65535.

Поскольку эти функции считывают непосредственно с порта ввода-вывода, они не могут использоваться в пользовательском коде.

Имена `inp` и `inpw` являются устаревшими, нерекомендуемыми именами для функций `_inp` и `_inpw`. Дополнительные сведения см. в разделе [имена функций POSIX](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|`_inp`|\<conio.h>|
|`_inpw`|\<conio.h>|
|`_inpd`|\<conio.h>|

Дополнительные сведения о совместимости см. в разделе [Compatibility](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Библиотеки

Все версии [библиотек времени выполнения языка C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>См. также:

[Ввод-вывод на консоль и порт](../c-runtime-library/console-and-port-i-o.md)\
[ыходной, аутпв, _outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)
