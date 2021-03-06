---
title: Работа с библиотеками импорта и файлами экспорта
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
ms.openlocfilehash: 6f6f2d5c48c63ba6d8a8a7f67a98b949b32a8afa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316526"
---
# <a name="working-with-import-libraries-and-export-files"></a>Работа с библиотеками импорта и файлами экспорта

LIB можно использовать с параметром/DEF для создания библиотеки импорта и файла экспорта. LINK использует файл экспорта для построения программы, содержащей экспортирует (обычно динамически подключаемой библиотеки (DLL)), и он использует библиотеку импорта для разрешения ссылок на объекты экспорта в другие программы.

Обратите внимание на то, что при создании библиотеки импорта в предварительном перед созданием файла DLL, необходимо передать тот же набор объектных файлов при построении библиотеки DLL, как Вы передали при сборке библиотеки импорта.

В большинстве случаев вам не обязательно должны использовать LIB для создания библиотеки импорта. При связывании программу (исполняемый файл или библиотеку DLL), содержащую экспорты, ссылка автоматически создает библиотеку импорта, описывающий экспортов. Позже при связывании программу, которая ссылается на объекты экспорта, укажите библиотеку импорта.

Тем не менее когда библиотека DLL экспортирует в программу, она также импортирует, прямо или косвенно, необходимо использование LIB для создания одной из библиотек импорта. Когда LIB создает библиотеку импорта, она также создает файл экспорта. При связывании одну из библиотек, необходимо использовать файл экспорта.

## <a name="see-also"></a>См. также

[Справочник по LIB](lib-reference.md)
