---
title: Класс Фронтендфиле
description: Справочник C++ по классу SDK для Build Insights фронтендфиле.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFile
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 094b1326765e0e8edb00534ecb3d94c46702d4ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334796"
---
# <a name="frontendfile-class"></a>Класс Фронтендфиле

::: moniker range="<=vs-2015"

Пакет C++ SDK для Build Insights совместим с Visual Studio 2017 и более поздних версий. Чтобы просмотреть документацию по этим версиям, присвойте элементу управления "Выбор версий Visual Studio" для этой статьи значение Visual Studio 2017 или Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Класс `FrontEndFile` используется с функциями [матчевент](../functions/match-event.md), [матчевентинмемберфунктион](../functions/match-event-in-member-function.md), [матчевентстакк](../functions/match-event-stack.md)и [матчевентстаккинмемберфунктион](../functions/match-event-stack-in-member-function.md) . Используйте его для сопоставления [FRONT_END_FILEного](../event-table.md#front-end-file) события.

## <a name="syntax"></a>Синтаксис

```cpp
class FrontEndFile : public Activity
{
public:
    FrontEndFile(const RawEvent& event);

    const char* Path() const;
};
```

## <a name="members"></a>Члены

Наряду с наследуемыми членами от базового класса [Activity](activity.md) класс `FrontEndFile` содержит следующие члены:

### <a name="constructors"></a>Конструкторы

[фронтендфиле](#front-end-file)

### <a name="functions"></a>Функции

[Путь](#path)

## <a name="front-end-file"></a>фронтендфиле

```cpp
FrontEndFile(const RawEvent& event);
```

### <a name="parameters"></a>Параметры

*event*\
Событие [FRONT_END_FILE](../event-table.md#front-end-file) .

## <a name="path"></a> Path

```cpp
const char* Path() const;
```

### <a name="return-value"></a>Возвращаемое значение

Абсолютный путь к файлу в кодировке UTF-8.

::: moniker-end
