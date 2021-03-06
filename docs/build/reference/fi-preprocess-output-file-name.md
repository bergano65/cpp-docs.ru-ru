---
title: /Fi (предварительная обработка имени выходного файла)
ms.date: 11/04/2016
f1_keywords:
- /Fi
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
ms.openlocfilehash: 990c48a72c3f6017d893ddf9b46bcbb737bfb634
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271259"
---
# <a name="fi-preprocess-output-file-name"></a>/Fi (предварительная обработка имени выходного файла)

Задает имя выходного файла, к которому [/P (Предварительная обработка в файл)](p-preprocess-to-a-file.md) параметр компилятора записывает предварительно обработанные выходные данные.

## <a name="syntax"></a>Синтаксис

```
/Fipathname
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|`pathname`|Имя и путь выходного файла, созданного **/P** параметр компилятора.|

## <a name="remarks"></a>Примечания

Используйте **/Fi** параметр компилятора в сочетании с **/P** параметр компилятора.

Если указывается только путь для `pathname` параметр, базовое имя исходного файла используется в качестве базового имени файла предварительно обработанные выходные данные. `pathname` Параметра не требуется расширение имени определенного файла. Тем не менее если не указать расширение имени файла, используется расширение «i».

## <a name="example"></a>Пример

Следующая командная строка предварительно обрабатывает PROGRAM.cpp, сохраняет комментарии, добавляет [#line](../../preprocessor/hash-line-directive-c-cpp.md) директивы и записывает результат в файл MYPROCESS.i.

```
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

## <a name="see-also"></a>См. также

[Параметры компилятора MSVC](compiler-options.md)<br/>
[/P (вывод результатов предварительной обработки в файл)](p-preprocess-to-a-file.md)<br/>
[Указание пути](specifying-the-pathname.md)
