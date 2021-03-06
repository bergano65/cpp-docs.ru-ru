---
title: Обработка уведомляющих сообщений в элементах управления "Расширенное поле со списком"
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 044cef644f746f7cb70944805882bd8e2f2806b4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908109"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Обработка уведомляющих сообщений в элементах управления "Расширенное поле со списком"

По мере того как пользователи взаимодействуют с расширенным полем со списком, элемент управления (`CComboBoxEx`) отправляет сообщения уведомления своему родительскому окну (обычно это объект представления или диалогового окна). Обрабатывайте эти сообщения, если требуется сделать что-нибудь в ответе. Например, когда пользователь активирует раскрывающийся список или щелкает поле ввода элемента управления, отправляется уведомление CBEN_BEGINEDIT.

Используйте [мастер классов](reference/mfc-class-wizard.md) для добавления обработчиков уведомлений в родительский класс для тех сообщений, которые требуется реализовать.

В списке ниже приведены различные уведомления, отправляемые элементом управления "Расширенное поле со списком".

- CBEN_BEGINEDIT отправляется, когда пользователь активирует раскрывающийся список или щелкает поле ввода элемента управления.

- CBEN_DELETEITEM, отправленный при удалении элемента.

- CBEN_DRAGBEGIN отправляется, когда пользователь начинает перетаскивать изображение элемента, отображаемого в области редактирования элемента управления.

- CBEN_ENDEDIT отправляется, когда пользователь завершает операцию в поле ввода или выбрал элемент из раскрывающегося списка элемента управления.

- CBEN_GETDISPINFO отправляется для получения отображаемой информации о элементе обратного вызова.

- CBEN_INSERTITEM отправляется при вставке нового элемента в элемент управления.

## <a name="see-also"></a>См. также

[Использование CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Элементы управления](../mfc/controls-mfc.md)
