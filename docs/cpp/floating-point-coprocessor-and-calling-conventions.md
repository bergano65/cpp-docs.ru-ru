---
title: Сопроцессор для вычислений с плавающей запятой и соглашения о вызовах
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: 7e9184d66bde26ab0e2b345f8f10c2e28619fd2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154247"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Сопроцессор для вычислений с плавающей запятой и соглашения о вызовах

При создании сборки подпрограммы для вычислений с плавающей точки сопроцессора, которые необходимо сохранить вычислений с плавающей точки управления word и очистить стек сопроцессора в том случае, если вы возвращаете **float** или **двойные** значение (которое функция должна возвращать в ST(0)).

## <a name="see-also"></a>См. также

[Соглашения о вызовах](../cpp/calling-conventions.md)