---
title: Определение встроенных функций C++ с помощью dllexport и dllimport
ms.date: 11/04/2016
helpviewer_keywords:
- inline functions [C++], defining
- functions [C++], defining inline
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
ms.openlocfilehash: 88fbb497aab4d794d3ef84a902a72c4e044e51de
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857571"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Определение встроенных функций C++ с помощью dllexport и dllimport

**Блок, относящийся только к системам Майкрософт**

Можно определить как встроенную функцию с атрибутом **dllexport** . В этом случае всегда создается экземпляр функции и она экспортируется независимо от того, ссылается ли на нее какой-либо модуль в программе. Предполагается, что функция должна импортироваться другой программой.

В качестве встроенной можно также определить функцию, объявленную с атрибутом **dllimport**. В этом случае функцию можно расширить (согласно спецификациям /Ob), но ее экземпляр никогда не создается. В частности, если принимается адрес встроенной импортированной функции, возвращается адрес функции, находящейся в библиотеке DLL. Это поведение аналогично получению адреса невстроенной импортированной функции.

Эти правила применяются для встраиваемых функций, определения которых отображаются внутри определения класса. Кроме того, локальные статические данные и строки во встроенных функциях поддерживают одинаковые идентификаторы между библиотекой DLL и клиентом так, как это было бы в одной программе (т. е. исполняемый файл без интерфейса DLL).

При предоставлении импортированных встроенных функций соблюдайте осторожность. Например, при обновлении библиотеки DLL не следует предполагать, что клиент использует ее измененную версию. Чтобы убедиться в загрузке правильной версии библиотеки DLL, перестройте также клиент этой библиотеки.

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также:

[dllexport, dllimport](../cpp/dllexport-dllimport.md)