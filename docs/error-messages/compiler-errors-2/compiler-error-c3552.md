---
title: Ошибка компилятора C3552
ms.date: 11/04/2016
f1_keywords:
- C3552
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
ms.openlocfilehash: 27c4707097f43266a3be57ad6dc9591ab6f34e97
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375942"
---
# <a name="compiler-error-c3552"></a>Ошибка компилятора C3552

"имя_типа": тип возвращаемого значения с поздним заданием не может содержать "auto"

Если вы используете ключевое слово `auto` для типа возвращаемого значения функции, необходимо использовать тип возвращаемого значения с поздним заданием. Однако нельзя использовать другое ключевое слово `auto` для указания типа возвращаемого значения с поздним заданием. Например, представленный ниже фрагмент кода приводит к возникновению ошибки C3552.

`auto myFunction->auto; // C3552`