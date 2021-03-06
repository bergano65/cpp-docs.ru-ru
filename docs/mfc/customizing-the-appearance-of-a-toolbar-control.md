---
title: Настройка внешнего вида элементов управления панели инструментов
ms.date: 11/04/2016
f1_keywords:
- TBSTYLE_
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
ms.openlocfilehash: 590f0dce6c50ee6d0ca30c4c68e21787563bd686
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508725"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Настройка внешнего вида элементов управления панели инструментов

Класс `CToolBarCtrl` предоставляет множество стилей, влияющих на внешний вид (и иногда, поведение) объекта ToolBar. Измените объект панели инструментов, установив `dwCtrlStyle` параметр `CToolBarCtrl::Create` функции-члена (или `CToolBar::CreateEx`) при первом создании элемента управления ToolBar.

Следующие стили влияют на трехмерный аспект кнопок панели инструментов и размещение текста кнопки:

- **TBSTYLE_FLAT** Создает плоскую панель инструментов, в которой и панель инструментов, и кнопки являются прозрачными. Текст кнопки отображается под точечными рисунками кнопки. При использовании этого стиля кнопка под курсором автоматически выделяется.

- **TBSTYLE_TRANSPARENT** Создает прозрачную панель инструментов. На прозрачной панели инструментов панель инструментов прозрачна, а кнопки — нет. Текст кнопки отображается под точечными рисунками кнопки.

- **TBSTYLE_LIST** Размещает текст кнопки справа от точечных рисунков кнопки.

> [!NOTE]
>  Чтобы избежать проблем с перерисовкой, стили **TBSTYLE_FLAT** и **TBSTYLE_TRANSPARENT** должны быть установлены до того, как объект панели инструментов станет видимым.

Следующие стили определяют, позволяет ли панель инструментов пользователя изменять расположение отдельных кнопок в объекте ToolBar с помощью перетаскивания.

- **TBSTYLE_ALTDRAG** Позволяет пользователям изменять расположение кнопок на панели инструментов, перетаскивая его, удерживая нажатой клавишу ALT. Если этот стиль не указан, пользователь должен удерживать нажатой клавишу SHIFT при перетаскивании кнопки.

    > [!NOTE]
    >  Чтобы разрешить перетаскивание кнопок панели инструментов, необходимо указать стиль **CCS_ADJUSTABLE** .

- **TBSTYLE_REGISTERDROP** Создает сообщения уведомления **TBN_GETOBJECT** для запроса целевых объектов Drop, когда указатель мыши проходит над кнопками панели инструментов.

Остальные стили влияют на визуальные и невизуальные аспекты объекта ToolBar:

- **TBSTYLE_WRAPABLE** Создает панель инструментов, которая может содержать несколько строк кнопок. Кнопки панели инструментов могут переноситься на следующую строку, когда панель инструментов оказывается слишком узким, чтобы включить все кнопки в той же строке. Перенос происходит при разделении и негруппировании границ.

- **TBSTYLE_CUSTOMERASE** Создает сообщения уведомления **NM_CUSTOMDRAW** при обработке сообщений **WM_ERASEBKGND** .

- **TBSTYLE_TOOLTIPS** Создает элемент управления "всплывающая подсказка", который приложение может использовать для вывода описательного текста для кнопок на панели инструментов.

Полный список стилей панелей инструментов и расширенных стилей см. в разделе [стили элементов управления и кнопок панели инструментов](/windows/win32/Controls/toolbar-control-and-button-styles) и [Расширенные стили панели инструментов](/windows/win32/Controls/toolbar-extended-styles) в Windows SDK.

## <a name="see-also"></a>См. также

[Использование CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Элементы управления](../mfc/controls-mfc.md)
