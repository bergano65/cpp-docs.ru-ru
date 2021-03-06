---
title: Пошаговое руководство. Обновление приложения MFC Scribble (часть 2)
ms.date: 04/25/2019
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: d4655c0a4a8847642b75575e324a291e39bbf42a
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64558165"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Пошаговое руководство. Обновление приложения MFC Scribble (часть 2)

[Часть 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) данного пошагового руководства, показал, как добавить ленту Office Fluent классической Scribble приложения. Эта часть демонстрирует добавление панелей ленты и элементы управления, которые пользователи могут использовать вместо меню и команд.

## <a name="prerequisites"></a>Предварительные требования

[Примеры кода на Visual C++](../overview/visual-cpp-samples.md)

##  <a name="top"></a> Разделы

Этой части пошагового руководства состоит из следующих разделов:

- [Добавление новых элементов управления на ленту](#addnewpanel)

- [Добавление в ленту панель справки](#addhelppanel)

- [Добавление панели пера на ленту](#addpenpanel)

- [Добавление цвет кнопки на ленту](#addcolorbutton)

- [Добавление члена цвета классе документа](#addcolormember)

- [Инициализация перья и сохранении предпочтений](#initpensave)

##  <a name="addnewpanel"></a> Добавление новых элементов управления на ленту

Ниже показано, как добавить **представление** панель, которая содержит два флажка, управляющие видимостью панели инструментов и строки состояния, а также **окно** панель, которая содержит вертикальный разбиения Кнопка, которая управляет созданием и расположении окон многодокументного интерфейса (MDI).

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Чтобы добавить панель представления и панели окна на панель ленты

1. Создание панели с именем `View`, который имеет два флажка, Переключить строку состояния и панель инструментов.

   1. Из **элементов**, перетащите **панели** для **Главная** категории. Затем перетащите два **флажки** панели.

   1. Щелкните на панели, чтобы изменить его свойства. Изменение **заголовок** для `View`.

   1. Щелкните первый флажок, чтобы изменить его свойства. Изменение **идентификатор** для `ID_VIEW_TOOLBAR` и **заголовок** для `Toolbar`.

   1. Щелкните второй флажок, чтобы изменить его свойства. Изменение **идентификатор** для `ID_VIEW_STATUS_BAR` и **заголовок** для `Status Bar`.

1. Создание панели с именем `Window` , имеет разворачивающуюся кнопку. Когда пользователь щелкает Разворачивающаяся кнопка, контекстное меню отображает три команды, которые уже определены в приложении Scribble.

   1. Из **элементов**, перетащите **панели** для **Главная** категории. Затем перетащите **кнопку** панели.

   1. Щелкните на панели, чтобы изменить его свойства. Изменение **заголовок** для `Window`.

   1. Нажмите кнопку. Изменение **заголовок** для `Windows`, **ключи** для `w`, **индекс большое изображение** для `1`, и **режим разбиения** Чтобы `False`. Нажмите кнопку обзора (**...** ) рядом с полем **пунктов меню** открыть **редактор элементов** диалоговое окно.

   1. Нажмите кнопку **добавить** три раза, чтобы добавить три кнопки.

   1. Нажмите первую кнопку, а затем измените **заголовок** для `New Window`, и **идентификатор** для `ID_WINDOW_NEW`.

   1. Нажмите вторую кнопку, а затем измените **заголовок** для `Cascade`, и **идентификатор** для `ID_WINDOW_CASCADE`.

   1. Нажмите третью кнопку, а затем измените **заголовок** для `Tile`, и **идентификатор** для `ID_WINDOW_TILE_HORZ`.

1. Сохраните изменения и затем постройте и запустите приложение. **Представление** и **окно** панели должна отображаться. Нажмите кнопки, чтобы убедиться, что они правильно функционируют.

##  <a name="addhelppanel"></a> Добавление в ленту панель справки

Теперь можно назначить два элемента меню, которые определены в приложении Scribble кнопок ленты, которые называются **разделы справки** и **о Scribble**. Новая панель с именем добавляются кнопки **помочь**.

### <a name="to-add-a-help-panel"></a>Чтобы добавить панель справки

1. Из **элементов**, перетащите **панели** для **Главная** категории. Затем перетащите два **кнопки** панели.

1. Щелкните на панели, чтобы изменить его свойства. Изменение **заголовок** для `Help`.

1. Нажмите первую кнопку. Изменение **заголовок** для `Help Topics`, и **идентификатор** для `ID_HELP_FINDER`.

1. Нажмите вторую кнопку. Изменение **заголовок** для `About Scribble...`, и **идентификатор** для `ID_APP_ABOUT`.

1. Сохраните изменения и затем постройте и запустите приложение. Объект **помочь** должна отображаться панель, которая содержит две кнопки ленты.

   > [!IMPORTANT]
   > При нажатии кнопки **разделы справки** кнопка, приложения Scribble Открывает сжатый файл справки HTML (.chm) с именем *your_project_name*. chm. Следовательно Если проект не называется Scribble, необходимо переименовать файл справки на имя вашего проекта.

##  <a name="addpenpanel"></a> Добавление панели пера на ленту

Теперь добавьте панель для отображения кнопки, управляющие толщину и цвет пера. Эта панель содержит флажок, который служит для переключения между «толстый» и тонкой перья. Аналогично его функциональность **толстой линией** пункт меню в приложении Scribble.

В исходном приложении Scribble позволяет пользователю выбрать ширину пера в диалоговом окне, которое появляется при нажатии **толщины** меню. Так как лента имеет достаточно места для новых элементов управления, можно заменить диалоговом окне, используя два поля со списком на ленте. Одно поле со списком Корректирует ширину пера, тонкий и поле со списком Корректирует ширину пера, «толстый».

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Чтобы добавить поля пера на панели "и" поле со списком на ленте

1. Из **элементов**, перетащите **панели** для **Главная** категории. Затем перетащите **флажок** и два **списком** панели.

1. Щелкните на панели, чтобы изменить его свойства. Изменение **заголовок** для `Pen`.

1. Установите флажок. Изменение **заголовок** для `Use Thick`, и **идентификатор** для `ID_PEN_THICK_OR_THIN`.

1. Щелкните первое поле со списком. Изменение **заголовок** для `Thin Pen`, **идентификатор** для `ID_PEN_THIN_WIDTH`, **тип** для `Drop List`, **данных** для `1;2;3;4;5;6;7;8;9;`, и **текст** для `2`.

1. Щелкните второе поле со списком. Изменение **заголовок** для `Thick Pen`, **идентификатор** для `ID_PEN_THICK_WIDTH`, **тип** для `Drop List`, **данных** для `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`, и **текст** для `5`.

1. Новые поля со списком не соответствуют все существующие элементы меню, поэтому вам необходимо создать пункт меню для каждого параметра пера.

   1. В **представление ресурсов** открытое окно **IDR_SCRIBBTYPE** ресурса меню.

   1. Нажмите кнопку **пера** чтобы открыть меню «перо». Нажмите кнопку **введите здесь** и тип `Thi&n Pen`.

   1. Щелкните правой кнопкой мыши текст, который вы ввели, чтобы открыть **свойства** окна, а затем изменить идентификатор свойства `ID_PEN_THIN_WIDTH`.

   1. Создайте обработчик событий для всех элементов меню пера. Щелкните правой кнопкой мыши **э & n пера** пункт меню, который вы создали и нажмите кнопку **добавить обработчик событий**. **Мастер обработчика события** отображается.

   1. В **список классов** поле в мастере выберите **CScribbleDoc** и нажмите кнопку **добавлять и редактировать**. Команда создает обработчик событий с именем `CScribbleDoc::OnPenThinWidth`.

   1. Добавьте следующий код к `CScribbleDoc::OnPenThinWidth`.

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        // Get a pointer to the Thin Width combo box
        CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
        CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THIN_WIDTH));

        //Get the selected value
        int nCurSel = pThinComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThinWidth = atoi(CStringA(pThinComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. Создайте меню элемента и обработчики событий для толстых пера.

   1. В **представление ресурсов** открытое окно **IDR_SCRIBBTYPE** ресурса меню.

   1. Нажмите кнопку **пера** чтобы открыть меню «перо». Нажмите кнопку **введите здесь** и тип `Thic&k Pen`.

   1. Щелкните правой кнопкой мыши текст, который вы ввели для отображения **свойства** окна. Измените значение свойства ID на `ID_PEN_THICK_WIDTH`.

   1. Щелкните правой кнопкой мыши **толстых пера** пункт меню, который вы создали и нажмите кнопку **добавить обработчик событий**. **Мастер обработчика события** отображается.

   1. В **список классов** мастера, выберите **CScribbleDoc** и нажмите кнопку **добавлять и редактировать**. Команда создает обработчик событий с именем `CScribbleDoc::OnPenThickWidth`.

   1. Добавьте следующий код к `CScribbleDoc::OnPenThickWidth`.

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
            CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
        // Get the selected value
        int nCurSel = pThickComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThickWidth = atoi(CStringA(pThickComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. Сохраните изменения и затем постройте и запустите приложение. Отображать новые кнопки и поля со списком. Попробуйте использовать другое перо ширины для scribble.

##  <a name="addcolorbutton"></a> Добавление цвет кнопки на панель «перо»

Затем добавьте [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) объект, который позволяет пользователю scribble цветом.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>Чтобы добавить кнопку цвета на панель «перо»

1. Прежде чем добавить кнопку цвета, создайте пункт меню для него. В **представление ресурсов** открытое окно **IDR_SCRIBBTYPE** ресурса меню. Нажмите кнопку **пера** элемент меню, чтобы открыть меню «перо». Нажмите кнопку **введите здесь** и тип `&Color`. Щелкните правой кнопкой мыши текст, который вы ввели для отображения **свойства** окна. Измените идентификатор на `ID_PEN_COLOR`.

1. Теперь добавьте кнопку цвета. Из **элементов**, перетащите **кнопка цвета** для **пера** панели.

1. Нажмите кнопку цвета. Изменение **заголовок** для `Color`, **идентификатор** для `ID_PEN_COLOR`, **упрощенный вид** для `True`, **индекс большое изображение** для `1`, и **режим разбиения** для `False`.

1. Сохраните изменения и затем постройте и запустите приложение. Новый цвет кнопки должны быть видимы в **пера** панели. Тем не менее он не может использоваться, так как он еще не содержит обработчик событий. Далее показано, как добавить обработчик событий для кнопки "цвет".

##  <a name="addcolormember"></a> Добавление члена цвета классе документа

Так как в исходном приложении Scribble не имеет цвет перья, необходимо написать реализацию для них. Для хранения цвета пера документа, добавьте новый элемент в класс документа `CscribbleDoc`.

### <a name="to-add-a-color-member-to-the-document-class"></a>Добавление члена цвет класс документа

1. В scribdoc.h в `CScribbleDoc` класса, найти `// Attributes` раздел. Добавьте следующие строки кода после определения `m_nThickWidth` элемент данных.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. Каждый документ содержит список штрихов, что пользователь уже рисуется. Каждый штрих определяется `CStroke` объекта. `CStroke` Класс не содержит сведения о цвет пера, поэтому необходимо изменить класс. В scribdoc.h в `CStroke` добавьте следующие строки кода после определения `m_nPenWidth` элемент данных.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. В scribdoc.h, добавьте новый `CStroke` конструктор, параметры которого укажите ширину и цвет. Добавьте следующую строку кода после `CStroke(UINT nPenWidth);` инструкции.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. В scribdoc.cpp, добавьте реализацию нового `CStroke` конструктор. Добавьте следующий код после реализации `CStroke::CStroke(UINT nPenWidth)` конструктор.

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. Измените вторую строку `CStroke::DrawStroke` метод следующим образом.

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. Установите цвет пера по умолчанию для класса документа. В scribdoc.cpp, добавьте следующие строки в `CScribbleDoc::InitDocument`после `m_nThickWidth = 5;` инструкции.

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. В scribdoc.cpp, измените первую строку `CScribbleDoc::NewStroke` метод следующего.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. Измените последнюю строку из `CScribbleDoc::ReplacePen` метод следующего.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. Вы добавили `m_penColor` члена на предыдущем шаге. Теперь создайте обработчик событий для кнопку цвета, который задает элемент.

   1. В **представление ресурсов** окно, откройте меню IDR_SCRIBBTYPE ресурс.

   1. Щелкните правой кнопкой мыши **цвет** пункта меню и нажмите кнопку **добавить обработчик событий**. **Мастер обработчика события** отображается.

   1. В **список классов** поле в мастере выберите **CScribbleDoc** и нажмите кнопку **добавлять и редактировать** кнопки. Эта команда создает `CScribbleDoc::OnPenColor` заглушки обработчика события.

1. Замените заглушку для `CScribbleDoc::OnPenColor` обработчик событий следующим кодом.

   ```cpp
   void CScribbleDoc::OnPenColor()
   {
       // Change pen color to reflect color button's current selection
       CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
       ASSERT_VALID(pRibbon);

       CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
           CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

       m_penColor = pColorBtn->GetColor();
       // Create new pen using the selected color
       ReplacePen();
   }
   ```

1. Сохраните изменения и затем постройте и запустите приложение. Теперь можно нажать кнопку цвет и цвет пера.

##  <a name="initpensave"></a> Инициализация перья и сохранении предпочтений

Затем инициализируйте, цвет и ширину пера. Наконец сохранять и загружать цвет рисования из файла.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Для инициализации элементов управления на ленте

1. Инициализируйте перья на панели ленты.

   Добавьте следующий код к scribdoc.cpp, в `CScribbleDoc::InitDocument` метод после `m_sizeDoc = CSize(200,200)` инструкции.

   ```cpp
   // Reset the ribbon UI to its initial values
   CMFCRibbonBar* pRibbon =
       ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
   ASSERT_VALID(pRibbon);

   CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
       CMFCRibbonColorButton,
       pRibbon->FindByID(ID_PEN_COLOR));

   // Set ColorButton to black
   pColorBtn->SetColor(RGB(0, 0, 0));

   CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THIN_WIDTH));

   // Set Thin pen combobox to 2
   pThinComboBox->SelectItem(1);

   CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THICK_WIDTH));

   // Set Thick pen combobox to 5
   pThickComboBox->SelectItem(0);
   ```

1. Сохраните цвет рисования в файл. Добавьте следующую инструкцию, чтобы scribdoc.cpp, в `CStroke::Serialize` метод после `ar << (WORD)m_nPenWidth;` инструкции.

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. Наконец Загрузите цвет рисования из файла. Добавьте следующую строку кода, в `CStroke::Serialize` метод после `m_nPenWidth = w;` инструкции.

   ```cpp
   ar >> m_penColor;
   ```

1. Теперь scribble цветом и сохраните документ в файл.

## <a name="conclusion"></a>Заключение

После обновления приложения MFC Scribble. Используйте в этом пошаговом руководстве в качестве руководства при изменении существующих приложений.

## <a name="see-also"></a>См. также

[Пошаговые руководства](../mfc/walkthroughs-mfc.md)<br/>
[Пошаговое руководство: Обновление приложения MFC Scribble (часть 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
