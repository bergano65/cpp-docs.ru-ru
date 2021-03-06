---
title: Редактирование меток древовидного элемента управления
ms.date: 11/04/2016
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
ms.openlocfilehash: 4b53d2c8e5a26a4dc37dfd7ae0710748bcd27bf6
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741222"
---
# <a name="tree-control-label-editing"></a>Редактирование меток древовидного элемента управления

Пользователь может напрямую изменять метки элементов в элементе управления "дерево" ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)), который имеет стиль **TVS_EDITLABELS** . Пользователь начинает редактирование, щелкая метку элемента, который находится в фокусе. Приложение начинает редактирование с помощью функции члена [едитлабел](../mfc/reference/ctreectrl-class.md#editlabel) . Элемент управления "дерево" отправляет уведомление при начале редактирования, а также при его отмене или завершении. По завершении редактирования вы несете ответственность за обновление метки элемента, если это уместно.

Когда начинается редактирование метки, элемент управления "дерево" отправляет сообщение уведомления [TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit) . Обрабатывая это уведомление, можно разрешить редактирование некоторых меток и запретить редактирование других. Возврат 0 позволяет изменять и возвращать ненулевой запрет.

Когда изменение метки отменено или завершено, элемент управления "дерево" отправляет сообщение уведомления [TVN_ENDLABELEDIT](/windows/win32/Controls/tvn-endlabeledit) . Параметр *lParam* является адресом структуры [нмтвдиспинфо](/windows/win32/api/commctrl/ns-commctrl-nmtvdispinfow) . Элемент **Item** является структурой [твитем](/windows/win32/api/commctrl/ns-commctrl-tvitemw) , определяющей элемент и включающей редактируемый текст. Вы несете ответственность за обновление метки элемента (при необходимости), возможно, после проверки измененной строки. Если редактирование отменено `TV_ITEM` , член псзтекст имеет значение 0.

Во время редактирования метки, как правило, в ответ на сообщение уведомления [TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit) можно получить указатель на элемент управления Edit, используемый для редактирования меток, с помощью функции-члена [жетедитконтрол](../mfc/reference/ctreectrl-class.md#geteditcontrol) . Вы можете вызвать функцию-член [сетлимиттекст](../mfc/reference/cedit-class.md#setlimittext) элемента управления Edit, чтобы ограничить объем текста, который пользователь может ввести или подкласс элемента управления Edit для перехвата и удаления недопустимых символов. Однако обратите внимание, что элемент управления "поле ввода" отображается только *после* отправки **TVN_BEGINLABELEDIT** .

## <a name="see-also"></a>См. также

[Использование CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Элементы управления](../mfc/controls-mfc.md)
