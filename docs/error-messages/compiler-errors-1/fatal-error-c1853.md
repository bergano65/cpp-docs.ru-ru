---
title: Неустранимая ошибка C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: ec2d6bf6bac46cca8bdc2e3b8fe7cc6b7799d78a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165922"
---
# <a name="fatal-error-c1853"></a>Неустранимая ошибка C1853

> "*filename*" предкомпилированного файла заголовка с предыдущей версии компилятора или предкомпилированный заголовок является C++ и вы используете его из C (или наоборот)

Возможные причины:

- Предкомпилированный заголовок был скомпилирован с помощью предыдущей версии компилятора. Попробуйте перекомпилировать заголовок с текущим компилятором.

- Предкомпилированный заголовок является C++ и его использовании в C. Попробуйте перекомпилировать заголовок для использования в C, указав одно из [/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) параметры компилятора, или измените суффикс исходного файла на «c». Дополнительные сведения см. в разделе [два варианта предварительной компиляции кода](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code).