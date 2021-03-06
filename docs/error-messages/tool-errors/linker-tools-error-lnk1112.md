---
title: Ошибка средств компоновщика LNK1112
ms.date: 11/04/2016
f1_keywords:
- LNK1112
helpviewer_keywords:
- LNK1112
ms.assetid: 425793d8-37e6-4072-9b6e-c3d4e9c12562
ms.openlocfilehash: bc01d56fb8144d23b91c82a7f791a70a5dadb7ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255490"
---
# <a name="linker-tools-error-lnk1112"></a>Ошибка средств компоновщика LNK1112

> Тип компьютера модуля "*тип1*«противоречит типу целевого компьютера»*тип2*"

## <a name="remarks"></a>Примечания

Объектные файлы, указанные как входные, скомпилированы для разных типов компьютеров.

Например, при попытке связать объектный файл, скомпилированный с помощью **/clr** , и объектный файл, скомпилированный с помощью **/clr:pure** (тип компьютера CEE), компоновщик создаст ошибку LNK1112. **/CLR: pure** параметр компилятора в Visual Studio 2015 не рекомендуется и не поддерживается в Visual Studio 2017.

Аналогично Если создать один модуль с x64 компилятора и другой модуль с помощью x86 компилятор и попытаться связать их, компоновщик создаст ошибку LNK1112.

Возможные причины этой ошибки: при разработке 64-разрядного приложения не установлен один из 64-разрядных компиляторов Visual C++. В этом случае 64-разрядные конфигурации будут недоступны. Чтобы устранить эту проблему, запустите установщик для Visual Studio и установите недостающие компоненты C++.

Эта ошибка также может возникать при изменении **активной конфигурации решения** в **диспетчере конфигураций** и последующей попытке построения проекта до удаления промежуточных файлов проекта. Чтобы устранить эту ошибку, выберите в меню **Сборка** пункт **Перестроить решение** . Можно также выбрать в меню **Сборка** пункт **Очистить решение** , а затем выполнить сборку решения.

## <a name="see-also"></a>См. также

- [Ошибки и предупреждения средств компоновщика](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
