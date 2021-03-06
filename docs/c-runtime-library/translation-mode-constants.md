---
title: Константы режима трансляции
ms.date: 11/04/2016
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
ms.openlocfilehash: a86c0c1a0b70613c6e7749c78f58f6dfb3602d4d
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376280"
---
# <a name="translation-mode-constants"></a>Константы режима трансляции

## <a name="syntax"></a>Синтаксис

```
#include <fcntl.h>
```

## <a name="remarks"></a>Примечания

Константы манифеста `_O_BINARY` и `_O_TEXT` определяют режим преобразования файлов (`_open` и `_sopen`) или потоков (`_setmode`).

Допустимые значения:

|||
|-|-|
`_O_TEXT`  | Открывает файл в текстовом режиме (с преобразованием). Во время ввода сочетание символов возврата каретки и перевода строки (CR-LF) преобразуется в один символ перевода строки (LF). Символы перевода строки преобразуются в комбинацию CR-LF в выводе. Кроме того, при вводе символ CTRL+Z интерпретируется как символ конца файла. В файлах, открытых для чтения и чтения и записи, функция `fopen` проверяет наличие CTRL+Z в конце файла и удаляет его, если это возможно. Это делается потому, что использование функций `fseek` и `ftell` для перемещения в файле, который заканчивается символом CTRL+Z, может вызвать неправильное поведение функции `fseek` в области конца файла.
`_O_BINARY`  | Открывает файл в двоичном (непреобразованном) режиме. Вышеописанные преобразования отключены.
`_O_RAW`  | Эквивалентно `_O_BINARY`. Поддерживается для обеспечения совместимости с C 2.0.

(Дополнительные сведения см. в разделах [Файловый ввод-вывод в текстовом и двоичном режиме](../c-runtime-library/text-and-binary-mode-file-i-o.md) и [Преобразование файлов](../c-runtime-library/file-translation-constants.md).

## <a name="see-also"></a>См. также

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_pipe](../c-runtime-library/reference/pipe.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_setmode](../c-runtime-library/reference/setmode.md)<br/>
[Глобальные константы](../c-runtime-library/global-constants.md)
