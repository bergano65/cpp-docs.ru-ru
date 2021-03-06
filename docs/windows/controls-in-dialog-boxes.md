---
title: Элементам управления диалоговыми (C++) | Документация Майкрософт
ms.date: 02/15/2019
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls [C++], about dialog box controls
- dialog box controls
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
ms.openlocfilehash: 568754bc514ae017293805fab1b25849d5ffe5f8
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400884"
---
# <a name="dialog-box-controls-c"></a>Элементам управления диалоговыми (C++)

Можно добавить элементы управления в диалоговое окно с помощью **редактор диалоговых окон** вкладке [окно панели элементов](/visualstudio/ide/reference/toolbox) , позволяющий выбрать элемент управления и перетащите его в диалоговом окне. По умолчанию **элементов** будет задано окно автоматического скрытия. Он отображается как вкладка в левой области решения при **редактор диалоговых окон** открыт. Тем не менее, вы можете закрепить **элементов** в позиции, выбрав окно **автоматическое скрытие** кнопки в правом верхнем углу окна. Дополнительные сведения о том, как управлять поведением этого окна см. в разделе [Управление окнами](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Самый быстрый способ добавить элементы управления в диалоговое окно, элемент или переместить элементы управления из одного диалогового окна в другое, является использование метода перетаскивания и вставки. Положение элемента управления представлен в пунктирной линией, до своего удаления в диалоговом окне. При добавлении элемента управления в диалоговое окно с помощью метода перетаскивания и вставки, присваивается стандартной высоте, соответствующие типу элемента управления.

При добавлении элемента управления в диалоговое окно или переместить, окончательная позиция может определяться руководства или поля, или имеется сетка макета, включен.

После добавления элемента управления в диалоговое окно, можно изменить свойства, такие как фактически [окно "Свойства"](/visualstudio/ide/reference/properties-window). Также можно выбрать несколько элементов управления и изменить их свойства одновременно.

Дополнительные сведения о **редактор диалоговых окон**, см. в разделе Практическое [добавить, изменить или удалить элементы управления](adding-editing-or-deleting-controls.md), [элементов управления макетом](../windows/arrangement-of-controls-on-dialog-boxes.md), и [определить управление доступом и значения](../windows/defining-mnemonics-access-keys.md).

Дополнительные сведения о элементы управления и диалоговых окон, см. в разделе [классы элементов управления](../mfc/control-classes.md), [классы диалоговых окон](../mfc/dialog-box-classes.md), и [стили полосы прокрутки](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

Стандартные элементы управления в **элементов** имеет значения по умолчанию события являются:

|Имя элемента управления|Событие по умолчанию|
|---|---|
|[Элемент управления Button](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Элемент управления "флажок"](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Поле со списком](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Изменение элемента управления](../mfc/reference/cedit-class.md)|СОБЫТИЕ EN_CHANGE|
|Группа|(неприменимо)|
|[Окно списка](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Управления "переключатель"](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Статический элемент управления текст](../mfc/reference/cstatic-class.md)|(неприменимо)|
|[Управления изображения](../mfc/reference/cpictureholder-class.md)|(неприменимо)|
|[Элемент управления Rich Edit 2.0](../mfc/using-cricheditctrl.md)|СОБЫТИЕ EN_CHANGE|
|[Полосы прокрутки](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> Дополнительные сведения об использовании **RichEdit 1.0** управления с MFC, см. в разделе [использование элемента управления RichEdit 1.0 с MFC](../windows/using-the-richedit-1-0-control-with-mfc.md) и [примеры элемента управления Правка Rich](../mfc/rich-edit-control-examples.md).

[Стандартных элементов управления Windows](../mfc/controls-mfc.md) в **элементов** для предоставления являются расширенные функциональные возможности:

|Имя элемента управления|Событие по умолчанию|
|---|---|
|[Элемент управления "ползунок"](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Элемент управления "Счетчик"](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Элемент управления хода выполнения](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|["Горячий" ключа управления](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[Управления "список"](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[Дерево](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[Набор вкладок](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[Анимация элемента управления](../mfc/using-an-animation-control.md)|ACN_START|
|[Элемент управления даты средство выбора времени](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[Элемент управления месячного календаря](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[IP-адрес управления](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[Расширенного элемента управления списком](../mfc/creating-an-extended-combo-box-control.md)||
|Пользовательский элемент управления|TTN_GETDISPINFO|

## <a name="custom-controls"></a>Пользовательские элементы управления

**Редактор диалоговых окон** позволяет использовать существующие пользовательские или пользовательских элементов управления в шаблон диалогового окна.

> [!NOTE]
> Не следует путать с элементами управления ActiveX являются пользовательские элементы управления в этом смысле. Элементы управления ActiveX иногда называют пользовательских элементов управления OLE. Кроме того не следует путать эти элементы управления с пользовательскими элементами управления в Windows.

Эта функция позволяет использовать элементы управления, кроме тех, предоставляемые Windows. Во время выполнения элемент управления, связанный с класс окна (который отличается от класса C++). Для установки любого элемента управления, таких как статический элемент управления диалогового окна является более распространенный способ выполнения той же задачи. Затем во время выполнения, в [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) функционировать, удалите этот элемент управления и замените его собственный пользовательский элемент управления.

> [!NOTE]
> Это техника устарела. Сегодня рекомендуется в большинстве случаев для записи элемент управления ActiveX или подкласс общего элемента управления Windows.

Для этих пользовательских элементов управления можно использовать:

- Задание расположения в диалоговом окне.

- Введите заголовок.

- Так как код приложения должен зарегистрировать элемент управления с таким именем, определяющий имя класса элемента управления Windows.

- Введите 32-разрядное шестнадцатеричное значение, которое задает стиль элемента управления.

- Установив расширенный стиль.

## <a name="requirements"></a>Требования

Win32

## <a name="see-also"></a>См. также

[Редактор диалоговых окон](../windows/dialog-editor.md)

<!--
[Adding Event Handlers for Dialog Box Controls](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->