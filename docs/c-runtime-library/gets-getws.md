---
title: gets, _getws
ms.date: 11/04/2016
api_name:
- _getws
- gets
api_location:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getts
- gets
- _getws
helpviewer_keywords:
- getws function
- getts function
- _getws function
- lines, getting
- streams, getting lines
- _getts function
- gets function
- standard input, reading from
ms.assetid: 1ec2dd4b-f801-48ea-97c2-892590f16024
ms.openlocfilehash: f4e052f91dd2b4adfd5fd7e1ad7c81e0e5b07a11
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300278"
---
# <a name="gets-_getws"></a>gets, _getws

Получает строку из потока `stdin` . Существуют более безопасные версии этих функций; см. статью [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
>  Эти функции устарели. Начиная с Visual Studio 2015 они недоступны в CRT. Безопасные версии этих функций, gets_s и _getws_s, по-прежнему доступны. Сведения об этих альтернативных функциях см. в статье [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
>  Этот API нельзя использовать в приложениях, выполняемых в среде выполнения Windows. Дополнительные сведения: [Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Синтаксис

```
char *gets(
   char *buffer
);
wchar_t *_getws(
   wchar_t *buffer
);
template <size_t size>
char *gets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_getws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>Параметры

*buffer*<br/>
Место хранения входной строки.

## <a name="return-value"></a>Возвращаемое значение

В случае успеха возвращает свой аргумент. Указатель **NULL** указывает на ошибку или конец файла. Используйте [ferror](../c-runtime-library/reference/ferror.md) или [feof](../c-runtime-library/reference/feof.md) для определения того, что именно произошло. Если параметр `buffer` имеет значение **NULL**, вызывается обработчик недопустимых параметров, как описано в статье [Проверка параметров](../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эти функции возвращают **NULL** и устанавливают параметр errno в значение `EINVAL`.

## <a name="remarks"></a>Заметки

Функция `gets` считывает строку из стандартного потока ввода `stdin` и сохраняет ее в буфере `buffer`. Строка состоит из всех символов до первого символа новой строки ("\n"). Затем перед возвратом строки функция`gets` заменяет символ новой строки нуль-символом ("\0"). Напротив, функция `fgets` сохраняет символ новой строки. `_getws` — это версия функции `gets`для расширенных символов; ее аргумент и возвращаемое значение являются строками расширенных символов.

> [!IMPORTANT]
>  Поскольку нет возможности ограничить количество символов, считываемых функцией gets, недоверенный ввод может легко привести к переполнению буфера. Взамен рекомендуется использовать `fgets` .

В C++ эти функции имеют шаблонные перегрузки, которые вызывают более новые и безопасные аналоги этих функций. Дополнительные сведения см. в разделе [Безопасные перегрузки шаблонов](../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_getts`|`gets`|`gets`|`_getws`|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|`gets`|\<stdio.h>|
|`_getws`|\<stdio.h> или \<wchar.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```c
// crt_gets.c
// compile with: /WX /W3

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets( line );  // C4996
   // Danger: No way to limit input to 20 chars.
   // Consider using gets_s instead.
   printf( "The line entered was: %s\n", line );
}
```

Обратите внимание, что ввод более двадцати символов переполнит буфер строки и почти наверняка вызовет сбой программы.

```Output

Hello there!The line entered was: Hello there!
```

## <a name="see-also"></a>См. также:

[Потоковый ввод-вывод](../c-runtime-library/stream-i-o.md)<br/>
[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)<br/>
[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)<br/>
[puts, _putws](../c-runtime-library/reference/puts-putws.md)
