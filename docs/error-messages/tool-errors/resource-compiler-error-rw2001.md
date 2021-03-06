---
title: Ошибка компилятора ресурсов RW2001
ms.date: 11/04/2016
f1_keywords:
- RW2001
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
ms.openlocfilehash: 4d298cdd9d96c55f283ce7f0e2ba04dd664941f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226511"
---
# <a name="resource-compiler-error-rw2001"></a>Ошибка компилятора ресурсов RW2001

Недопустимая директива в предварительно обработанный RC-файле

RC-файл содержит **#pragma** директива.

Используйте **#ifndef** директива препроцессора с **RC_INVOKED** константы, что компилятор ресурсов определяет, при обработке файла включения. Место **#pragma** директив в блок кода, не обрабатываются, если **RC_INVOKED** констант определена. Код в блоке обрабатывается только компилятором C или C++ и не компилятором ресурсов. Этот метод продемонстрирован в следующем примере кода:

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma** директиве препроцессора не имеет смысла в. RC-файле. **#Include** часто используется директива препроцессора. RC-файле для включения файла заголовка (файл пользовательского заголовка на основе проекта или файл стандартный заголовок, предоставляемые корпорацией Майкрософт, с помощью одного из своих продуктов). Некоторые из этих включаемых файлов содержат **#pragma** директива. Поскольку файл заголовка может включать один или несколько других файлов заголовков, файла, содержащего вызвавший ошибку **#pragma** директива может показаться неочевидными.

**#Ifndef RC_INVOKED** методика можно управлять включением файлов заголовков в файлы заголовков проекта.