---
title: wcrtomb_s
ms.date: 11/04/2016
api_name:
- wcrtomb_s
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: c1612e7fc4e40e05c46f06d8a29b69534c359421
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945849"
---
# <a name="wcrtomb_s"></a>wcrtomb_s

Преобразует расширенный символ в соответствующее представление многобайтового символа. Версия функции [wcrtomb](wcrtomb.md) с усовершенствованиями системы безопасности, описанными в разделе [Функции безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Синтаксис

```C
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char *mbchar,
   size_t sizeOfmbchar,
   wchar_t *wchar,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char (&mbchar)[size],
   wchar_t *wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Параметры

*претурнвалуе*<br/>
Возвращает записанное число символов или –1 в случае возникновения ошибки.

*мбчар*<br/>
Итоговый преобразованный многобайтовый символ.

*сизеофмбчар*<br/>
Размер переменной *мбчар* в байтах.

*wchar*<br/>
Расширенный символ для преобразования.

*мбстате*<br/>
Указатель на объект **mbstate_t** .

## <a name="return-value"></a>Возвращаемое значение

Возвращает нуль **или значение возврата** при возникновении ошибки.

## <a name="remarks"></a>Примечания

Функция **wcrtomb_s** преобразует расширенный символ, начиная с указанного состояния преобразования, содержащегося в *мбстате*, из значения, содержащегося в параметре *WCHAR*, в адрес, представленный в *мбчар*. Значением *претурнвалуе* будет число преобразованных байтов, но не более **MB_CUR_MAX** байт или значение-1, если произошла ошибка.

Если *мбстате* имеет значение null, используется внутреннее состояние преобразования **mbstate_t** . Если символ, содержащийся в параметре *WCHAR* , не имеет соответствующего многобайтового символа, значение *претурнвалуе* будет равно-1, а функция возвратит **значение** перекрывающегося **еилсек**.

Функция **wcrtomb_s** отличается от [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md) с ее возможной перезагрузкой. Состояние преобразования хранится в *мбстате* для последующих вызовов тех же или других перезапускаемых функций. При смешанном использовании перезапускаемых и неперезапускаемых функций результаты становятся неопределенными. Например, приложение будет использовать **вксрлен** , а не **wcslen**, если последующий вызов **wcsrtombs_s** использовался вместо **wcstombs_s**.

В C++ использование этой функции упрощено наличием шаблонных перегрузок; перегруженные методы могут автоматически определять длину буфера (что исключает необходимость указания аргумента с размером буфера), а также они могут автоматически заменять более старые, незащищенные функции их новыми безопасными аналогами. Дополнительные сведения см. в разделе [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Исключения

Функция **wcrtomb_s** является потокобезопасной, если ни одна из функций в текущем потоке не вызывает **setlocale** во время выполнения этой функции, а *мбстате* имеет значение null.

## <a name="example"></a>Пример

```C
// crt_wcrtomb_s.c
// This program converts a wide character
// to its corresponding multibyte character.
//

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    errno_t     returnValue;
    size_t      pReturnValue;
    mbstate_t   mbstate;
    size_t      sizeOfmbStr = 1;
    char        mbchar = 0;
    wchar_t*    wchar = L"Q\0";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),
                            *wchar, &mbstate);
    if (returnValue == 0) {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wchar);
        printf(" was converted to a the \"%c\" ", mbchar);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to a the "Q" multibyte character.
```

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**wcrtomb_s**|\<wchar.h>|

## <a name="see-also"></a>См. также

[Преобразование данных](../../c-runtime-library/data-conversion.md)<br/>
[Языковой стандарт](../../c-runtime-library/locale.md)<br/>
[Интерпретация последовательностей многобайтовых символов](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
