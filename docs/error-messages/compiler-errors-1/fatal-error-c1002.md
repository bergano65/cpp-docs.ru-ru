---
title: Неустранимая ошибка C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: 0588da99994be547742cc530ba435002a2d73359
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344836"
---
# <a name="fatal-error-c1002"></a>Неустранимая ошибка C1002

не хватает размера кучи на 2-ом проходе компилятора

Компилятор не хватило места динамической памяти во время второго прохода, возможно, из-за программа с слишком много символов или сложные выражения.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Возможные способы устранения этой ошибки

1. Разделите исходный файл на несколько небольших файлов.

1. Разделите выражения в виде небольших частей.

1. Удалите другие программы или драйверы, использующие память.