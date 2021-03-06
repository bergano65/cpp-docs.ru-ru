---
title: Временные объекты
ms.date: 11/04/2016
helpviewer_keywords:
- temporary objects
- objects [C++], temporary
ms.assetid: 4c8cec02-391e-4225-9bc6-06d150201412
ms.openlocfilehash: 19fd21da09149e730aac9bd0fb2cde066043e030
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266807"
---
# <a name="temporary-objects"></a>Временные объекты

В некоторых случаях компилятору необходимо создавать временные объекты. Такие объекты могут создаваться по следующим причинам.

- Для инициализации **const** ссылку с помощью инициализатора типа, отличающемся от базового типа инициализируемой ссылки.

- Для сохранения возвращаемого значения функции, которая возвращает пользовательский тип. Эти временные объекты создаются только в том случае, если программа не копирует возвращаемое значение в объект. Пример:

    ```cpp
    UDT Func1();    //  Declare a function that returns a user-defined
                    //   type.

    ...

    Func1();        //  Call Func1, but discard return value.
                    //  A temporary object is created to store the return
                    //   value.
    ```

   Поскольку возвращаемое значение не копируется в другой объект, создается временный объект. Более распространенный случай создания временных объектов — во время вычисления выражения, где требуется вызов перегруженных функций оператора. Эти перегруженные функции возвращают пользовательский тип, который часто не копируется в другой объект.

   Рассмотрим выражение `ComplexResult = Complex1 + Complex2 + Complex3`. Сначала вычисляется выражение `Complex1 + Complex2`, и результат сохраняется во временном объекте. Далее, выражение *временные* `+ Complex3` вычисляется, и результат копируется в `ComplexResult` (при условии, что оператор присваивания не перегружен).

- Для сохранения результата приведения к пользовательскому типу. Когда объект заданного типа явно преобразуется в пользовательский тип, этот новый объект создается как временный.

Временные объекты имеют время жизни, определяемое точками их создания и удаления. Любое выражение, которое создает несколько временных объектов, в конечном счете удаляет их в порядке, обратном созданию. Точки, в которых происходит удаление, указаны в следующей таблице.

### <a name="destruction-points-for-temporary-objects"></a>Точки удаления временных объектов

|Причина создания временного объекта|Точка удаления|
|------------------------------|-----------------------|
|Результат вычисления выражения|Все временные, созданных в результате вычисления выражения, удаляются в конце оператора-выражения (то есть точкой с запятой), или в конце управляющих выражений **для**, **Если**, **хотя**, **сделать**, и **переключения** инструкций.|
|Инициализация **const** ссылки|Если инициализатором не является L-значение того же типа, что и инициализируемая ссылка, создается временный объект базового типа объекта, инициализируемый выражением инициализации. Этот временный объект удаляется сразу после удаления объекта ссылки, с которым он связан.|