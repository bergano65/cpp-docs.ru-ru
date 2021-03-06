---
title: Общая последовательность создания окна
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: 949cf72910654b502ca4b57be72bedc2db63c315
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219571"
---
# <a name="general-window-creation-sequence"></a>Общая последовательность создания окна

При создании собственных, например дочернего окна для окна, инфраструктура использует гораздо тот же процесс, описанного в [создание документов и представлений](../mfc/document-view-creation.md).

Все классы окон, предоставляемые MFC используют [конструкции двухэтапное](../mfc/one-stage-and-two-stage-construction-of-objects.md). То есть во время вызова C++ **новый** оператора, конструктор выделяет и инициализирует объект с ++, но не создает соответствующее окно Windows. Можно впоследствии сделать, вызвав [создать](../mfc/reference/cwnd-class.md#create) функция-член объекта window.

`Create` Функция-член делает окно Windows и сохраняет его `HWND` в C++ объекта открытый элемент данных [m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd). `Create` позволяет выполнить гибкость через параметры создания. Перед вызовом `Create`, может потребоваться зарегистрировать класс окна с помощью глобальной функции [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) Чтобы задать значок и класс стили рамки.

Для окна фрейма, можно использовать [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) функция-член вместо `Create`. `LoadFrame` делает окно Windows, с помощью меньшим числом параметров. Он получает множество значений по умолчанию из ресурсов, включая заголовок, значок, таблицу сочетаний клавиш и меню фрейма.

> [!NOTE]
>  Вашей значок, таблицу сочетаний клавиш и ресурсов меню должны иметь общие Идентификаторы ресурсов, таких как **IDR_MAINFRAME**, для них загружаемых LoadFrame.

## <a name="what-do-you-want-to-know-more-about"></a>Выберите для получения дополнительных сведений

- [Объекты окон](../mfc/window-objects.md)

- [Регистрация классов «window»](../mfc/registering-window-classes.md)

- [Уничтожение объектов окон](../mfc/destroying-window-objects.md)

- [Создание окон фрейма документа](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>См. также

[Создание окон](../mfc/creating-windows.md)
