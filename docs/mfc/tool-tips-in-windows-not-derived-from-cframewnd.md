---
title: Всплывающие подсказки в Windows, не являющиеся производными CFrameWnd
ms.date: 11/04/2016
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
ms.openlocfilehash: 1f68fb62335219ea498163e6124c8e91e49f2938
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511035"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Всплывающие подсказки в Windows, не являющиеся производными CFrameWnd

В этом семействе статей описывается включение подсказок для элементов управления, содержащихся в окне, которые не являются производными от [CFrameWnd](../mfc/reference/cframewnd-class.md). Советы по работе с [панелями инструментов](../mfc/toolbar-tool-tips.md) в статье содержат сведения о подсказках для элементов управления в `CFrameWnd`.

В этом семействе статей рассматриваются следующие темы:

- [Включение подсказок](../mfc/enabling-tool-tips.md)

- [Обработка уведомления TTN_NEEDTEXT для подсказок](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [Структура TOOLTIPTEXT](../mfc/tooltiptext-structure.md)

Всплывающие подсказки автоматически отображаются для кнопок и других элементов управления, содержащихся в родительском `CFrameWnd`окне, производном от. Это связано с `CFrameWnd` тем, что имеет обработчик по умолчанию для уведомления [TTN_GETDISPINFO](/windows/win32/Controls/ttn-getdispinfo) , который обрабатывает уведомления **TTN_NEEDTEXT** от элементов управления подсказки, связанных с элементами управления.

Однако этот обработчик по умолчанию не вызывается, когда уведомление **TTN_NEEDTEXT** отправляется из элемента управления "всплывающая подсказка", связанного с элементом управления `CFrameWnd`в окне, который не является, например, элементом управления в диалоговом окне или представлении формы. Таким образом, для вывода всплывающих подсказок для дочерних элементов управления необходимо предоставить функцию обработчика для сообщения уведомления **TTN_NEEDTEXT** .

В подсказках инструментов по умолчанию, предоставленных для окна с помощью [CWnd:: енаблетултипс](../mfc/reference/cwnd-class.md#enabletooltips) , отсутствует связанный с ними текст. Чтобы получить текст подсказок для отображения, уведомление **TTN_NEEDTEXT** отправляется в родительское окно элемента управления всплывающей подсказки непосредственно перед отображением окна подсказки. Если для этого сообщения нет обработчика, чтобы присвоить какое-либо значение элементу *псзтекст* структуры **ToolTipText** , для всплывающей подсказки не будет отображаться текст.

## <a name="see-also"></a>См. также

[Подсказки](../mfc/tool-tips.md)
