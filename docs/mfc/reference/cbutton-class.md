---
title: Класс Кбуттон
ms.date: 11/04/2016
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
ms.openlocfilehash: 669bdb18e378c4dc39bdc6d51ca1ebe7f93fa839
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424575"
---
# <a name="cbutton-class"></a>Класс Кбуттон

Предоставляет функциональные возможности кнопочных элементов управления Windows.

## <a name="syntax"></a>Синтаксис

```
class CButton : public CWnd
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Description|
|----------|-----------------|
|[Кбуттон:: Кбуттон](#cbutton)|Формирует объект `CButton`.|

### <a name="public-methods"></a>Открытые методы

|Имя|Description|
|----------|-----------------|
|[Кбуттон:: Create](#create)|Создает элемент управления "кнопка Windows" и прикрепляет его к объекту `CButton`.|
|[Кбуттон::D Равитем](#drawitem)|Переопределение для рисования рисуемого владельцем объекта `CButton`.|
|[Кбуттон::/Bitmap](#getbitmap)|Получает маркер точечного рисунка, установленный ранее с помощью [сетбитмап](#setbitmap).|
|[Кбуттон:: Жетбуттонстиле](#getbuttonstyle)|Извлекает сведения о стиле элемента управления "Кнопка".|
|[Кбуттон:: Check](#getcheck)|Возвращает состояние проверки элемента управления "Кнопка".|
|[Кбуттон:: oncursor](#getcursor)|Получает маркер изображения курсора, установленного ранее с помощью [сеткурсор](#setcursor).|
|[Кбуттон:: "Icon"](#geticon)|Получает маркер значка, установленного ранее с помощью [сетикон](#seticon).|
|[Кбуттон:: Жетидеалсизе](#getidealsize)|Получает идеальный размер элемента управления "Кнопка".|
|[Кбуттон::/ImageList](#getimagelist)|Извлекает список изображений элемента управления "Кнопка".|
|[Кбуттон:: Note](#getnote)|Извлекает компонент примечания текущего элемента управления ссылки на команду.|
|[Кбуттон:: Жетнотеленгс](#getnotelength)|Извлекает длину текста примечания для текущего элемента управления ссылки на команду.|
|[Кбуттон:: Жетсплитглиф](#getsplitglyph)|Извлекает глиф, связанный с текущим элементом управления "кнопка разделения".|
|[Кбуттон:: Жетсплитимажелист](#getsplitimagelist)|Извлекает список изображений для текущего элемента управления "кнопка разделения".|
|[Кбуттон:: Жетсплитинфо](#getsplitinfo)|Извлекает сведения, определяющие текущий элемент управления "кнопка разделения".|
|[Кбуттон:: Жетсплитсизе](#getsplitsize)|Извлекает ограничивающий прямоугольник из раскрывающегося компонента элемента управления текущей кнопки разделения.|
|[Кбуттон:: Жетсплитстиле](#getsplitstyle)|Извлекает стили разворачивающейся кнопки, которые определяют текущий элемент управления "кнопка разделения".|
|[Кбуттон:: State](#getstate)|Извлекает состояние проверки, выделение и состояние фокуса для элемента управления "Кнопка".|
|[Кбуттон:: Жеттекстмаргин](#gettextmargin)|Извлекает текстовое поле элемента управления "Кнопка".|
|[Кбуттон:: Сетбитмап](#setbitmap)|Задает точечный рисунок, отображаемый на кнопке.|
|[Кбуттон:: Сетбуттонстиле](#setbuttonstyle)|Изменяет стиль кнопки.|
|[Кбуттон:: Сетчекк](#setcheck)|Задает состояние проверки элемента управления "Кнопка".|
|[Кбуттон:: Сеткурсор](#setcursor)|Указывает изображение курсора, которое будет отображаться на кнопке.|
|[Кбуттон:: Сетдропдовнстате](#setdropdownstate)|Задает состояние раскрывающегося списка текущего элемента управления "кнопка разворачивающейся кнопки".|
|[Кбуттон:: Сетикон](#seticon)|Задает значок, отображаемый на кнопке.|
|[Кбуттон:: Сетимажелист](#setimagelist)|Задает список изображений для элемента управления "Кнопка".|
|[Кбуттон:: Сетноте](#setnote)|Задает Примечание для текущего элемента управления ссылками на команды.|
|[Кбуттон:: Сетсплитглиф](#setsplitglyph)|Связывает указанный глиф с текущим элементом управления "кнопка разделения".|
|[Кбуттон:: Сетсплитимажелист](#setsplitimagelist)|Связывает список изображений с текущим элементом управления "кнопка разделения".|
|[Кбуттон:: Сетсплитинфо](#setsplitinfo)|Задает сведения, определяющие текущий элемент управления "кнопка разделения".|
|[Кбуттон:: Сетсплитсизе](#setsplitsize)|Задает ограничивающий прямоугольник для компонента раскрывающегося списка текущего элемента управления "кнопка разворачивающейся кнопки".|
|[Кбуттон:: Сетсплитстиле](#setsplitstyle)|Задает стиль текущего элемента управления "кнопка разворачивающейся кнопки".|
|[Кбуттон:: SetState](#setstate)|Задает состояние выделения для элемента управления "Кнопка".|
|[Кбуттон:: Сеттекстмаргин](#settextmargin)|Задает текстовое поле элемента управления "Кнопка".|

## <a name="remarks"></a>Remarks

Элемент управления "Кнопка" — это небольшое прямоугольное дочернее окно, которое можно щелкнуть или выключить. Кнопки могут использоваться отдельно или в группах и могут быть помечены или отображаться без текста. Как правило, кнопка изменяет внешний вид, когда пользователь щелкает его.

Обычные кнопки — это флажок, переключатель и кнопка. Объект `CButton` может быть любым из них в соответствии с [стилем кнопки](../../mfc/reference/styles-used-by-mfc.md#button-styles) , заданным в его инициализации функцией [создания](#create) члена.

Кроме того, класс [кбитмапбуттон](../../mfc/reference/cbitmapbutton-class.md) , производный от `CButton`, поддерживает создание элементов управления "Кнопка", помеченных растровыми изображениями, а не текстом. `CBitmapButton` может иметь отдельные растровые изображения для состояний кнопки "вверх", "вниз", "с сортировкой" и "отключено".

Элемент управления "Кнопка" можно создать либо из шаблона диалогового окна, либо непосредственно в коде. В обоих случаях сначала вызовите конструктор `CButton`, чтобы создать `CButton` объект. затем вызовите функцию члена `Create`, чтобы создать элемент управления "кнопка Windows" и присоединить его к объекту `CButton`.

Построение может быть одноэтапным процессом в классе, производном от `CButton`. Напишите конструктор для производного класса и вызовите `Create` в конструкторе.

Если требуется работать с сообщениями уведомлений Windows, отправленными элементом управления "Кнопка" в родительский элемент (обычно это класс, производный от класса [CDialog](../../mfc/reference/cdialog-class.md)), добавьте запись схемы сообщений и функцию-член обработчика сообщений в родительский класс для каждого сообщения.

Каждая запись схемы сообщений имеет следующий вид:

_Уведомление_ об\_ **(** _ID_, _мемберфксн_ **)**

где *ID* указывает идентификатор дочернего окна элемента управления, отправляющего уведомление, а *мемберфксн* — имя родительской функции-члена, написанной для работы с уведомлением.

Прототип родительской функции выглядит следующим образом:

`afx_msg void memberFxn();`

Возможны следующие записи схемы сообщений:

|Запись Map|Отправлено в родительский объект при...|
|---------------|----------------------------|
|ON_BN_CLICKED|Пользователь нажимает кнопку.|
|ON_BN_DOUBLECLICKED|Пользователь дважды нажимает кнопку.|

При создании `CButton` объекта из диалогового ресурса `CButton` объект автоматически уничтожается, когда пользователь закрывает диалоговое окно.

При создании объекта `CButton` в окне может потребоваться его уничтожить. При создании объекта `CButton` в куче с помощью **новой** функции необходимо вызвать метод **Delete** для объекта, чтобы уничтожить его, когда пользователь закроет элемент управления Windows Button. Если создать объект `CButton` в стеке или он внедрен в родительский объект диалогового окна, он уничтожается автоматически.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Требования

**Заголовок:** afxwin.h

##  <a name="cbutton"></a>Кбуттон:: Кбуттон

Формирует объект `CButton`.

```
CButton();
```

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

##  <a name="create"></a>Кбуттон:: Create

Создает элемент управления "кнопка Windows" и прикрепляет его к объекту `CButton`.

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Параметры

*лпсзкаптион*<br/>
Задает текст элемента управления "Кнопка".

*двстиле*<br/>
Задает стиль элемента управления "Кнопка". Примените любую комбинацию [стилей кнопок](../../mfc/reference/styles-used-by-mfc.md#button-styles) к кнопке.

*rect*<br/>
Задает размер и расположение элемента управления "Кнопка". Это может быть либо `CRect`ный объект, либо структура `RECT`.

*ппарентвнд*<br/>
Задает родительское окно элемента управления "Кнопка", обычно `CDialog`. Оно не должно иметь значение NULL.

*nID*<br/>
Задает идентификатор элемента управления "Кнопка".

### <a name="return-value"></a>Возвращаемое значение

Имеет ненулевое значение в случае успешного выполнения, иначе — 0.

### <a name="remarks"></a>Remarks

Объект `CButton` создается в два этапа. Сначала вызовите конструктор, а затем вызовите `Create`, который создает элемент управления "кнопка Windows" и присоединяет его к объекту `CButton`.

Если задан стиль WS_VISIBLE, Windows отправляет элементу управления "Кнопка" все сообщения, необходимые для активации и отображения кнопки.

Применить следующие [стили окна](../../mfc/reference/styles-used-by-mfc.md#window-styles) к элементу управления "Кнопка":

- WS_CHILD всегда

- WS_VISIBLE обычно

- WS_DISABLED редко

- WS_GROUP к группам элементов управления

- WS_TABSTOP для включения кнопки в порядок перехода

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

##  <a name="drawitem"></a>Кбуттон::D Равитем

Вызывается структурой при изменении визуального аспекта рисуемой владельцем кнопки.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Параметры

*лпдравитемструкт*<br/>
Длинный указатель на структуру [дравитемструкт](/windows/win32/api/winuser/ns-winuser-drawitemstruct) . Структура содержит сведения о рисуемом элементе и требуемом типе рисования.

### <a name="remarks"></a>Remarks

Для кнопки, рисуемой владельцем, задан стиль BS_OWNERDRAW. Переопределите эту функцию-член, чтобы реализовать Рисование для объекта `CButton`, рисуемого владельцем. Приложение должно восстановить все объекты интерфейса графических устройств (GDI), выбранные для контекста вывода, указанного в *лпдравитемструкт* , перед завершением функции-члена.

Также см. [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) значений стилей.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

##  <a name="getbitmap"></a>Кбуттон::/Bitmap

Вызовите эту функцию-член для получения маркера точечного рисунка, установленного ранее с помощью [сетбитмап](#setbitmap), связанного с кнопкой.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Возвращаемое значение

Маркер точечного рисунка. NULL, если точечный рисунок не указан ранее.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="getbuttonstyle"></a>Кбуттон:: Жетбуттонстиле

Извлекает сведения о стиле элемента управления "Кнопка".

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает стили кнопок для данного объекта `CButton`. Эта функция возвращает только значения стилей [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) , а не другие стили окна.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="getcheck"></a>Кбуттон:: Check

Получает состояние флажка для переключателя или флажка.

```
int GetCheck() const;
```

### <a name="return-value"></a>Возвращаемое значение

Возвращаемое значение из элемента управления "Кнопка", созданного с помощью BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON или BS_3STATE Style, имеет одно из следующих значений:

|Значение|Значение|
|-----------|-------------|
|BST_UNCHECKED|Состояние кнопки не отмечено.|
|BST_CHECKED|Состояние кнопки — checked.|
|BST_INDETERMINATE|Состояние кнопки является неопределенным (применяется только в том случае, если кнопка имеет стиль BS_3STATE или BS_AUTO3STATE).|

Если у кнопки есть другой стиль, возвращаемое значение будет BST_UNCHECKED.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="getcursor"></a>Кбуттон:: oncursor

Вызовите эту функцию-член для получения маркера курсора, установленного ранее с помощью [сеткурсор](#setcursor), связанного с кнопкой.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на изображение курсора. Значение NULL, если курсор не был указан ранее.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="geticon"></a>Кбуттон:: "Icon"

Вызовите эту функцию-член для получения маркера значка, ранее установленного с помощью [сетикон](#seticon), связанного с кнопкой.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Возвращаемое значение

Дескриптор для значка. NULL, если значок не указан ранее.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="getidealsize"></a>Кбуттон:: Жетидеалсизе

Получает идеальный размер для элемента управления "Кнопка".

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>Параметры

*псизе*<br/>
Указатель на текущий размер кнопки.

### <a name="return-value"></a>Возвращаемое значение

Имеет ненулевое значение в случае успешного выполнения, иначе — 0.

### <a name="remarks"></a>Remarks

Эта функция члена эмулирует функциональность BCM_GETIDEALSIZE сообщения, как описано в разделе [кнопки](/windows/win32/controls/buttons) Windows SDK.

##  <a name="getimagelist"></a>Кбуттон::/ImageList

Вызовите этот метод, чтобы получить список изображений из элемента управления "Кнопка".

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Параметры

*пбуттонимажелист*<br/>
Указатель на список изображений объекта `CButton`.

### <a name="return-value"></a>Возвращаемое значение

Имеет ненулевое значение в случае успешного выполнения, иначе — 0.

### <a name="remarks"></a>Remarks

Эта функция члена эмулирует функциональность BCM_GETIMAGELIST сообщения, как описано в разделе [кнопки](/windows/win32/controls/buttons) Windows SDK.

##  <a name="getnote"></a>Кбуттон:: Note

Извлекает текст примечания, связанный с текущим элементом управления ссылки на команду.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>Параметры

|Параметр|Description|
|---------------|-----------------|
|*лпсзноте*|заполняет Указатель на буфер, который вызывающий объект отвечает за выделение и отмену выделения. Если возвращаемое значение равно TRUE, буфер содержит текст примечания, связанного с текущим элементом управления ссылки на команду; в противном случае буфер не изменяется.|
|*кчноте*|[вход, выход] Указатель на целочисленную переменную без знака.<br /><br /> При вызове этого метода переменная содержит размер буфера, указанного параметром *лпсзноте* .<br /><br /> Если возвращаемое значение равно TRUE, то при возврате из этого метода переменная содержит размер заметки, связанной с текущим элементом управления ссылки на команду. Если возвращаемое значение равно FALSE, переменная содержит размер буфера, необходимый для хранения примечания.|

### <a name="return-value"></a>Возвращаемое значение

В первой перегрузке объект [CString](../../atl-mfc-shared/using-cstring.md) , содержащий текст примечания, связанный с текущим элементом управления ссылки на команду.

-или-

Во второй перегрузке значение TRUE, если этот метод выполнен успешно; в противном случае — значение FALSE.

### <a name="remarks"></a>Remarks

Этот метод следует использовать только с элементами управления, стиль кнопки которых BS_COMMANDLINK или BS_DEFCOMMANDLINK.

Этот метод отправляет [BCM_GETNOTE](/windows/win32/Controls/bcm-getnote) сообщение, описанное в Windows SDK.

##  <a name="getnotelength"></a>Кбуттон:: Жетнотеленгс

Извлекает длину текста примечания для текущего элемента управления ссылки на команду.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Возвращаемое значение

Длина текста примечания в 16-разрядных символах Юникода для текущего элемента управления ссылками на команды.

### <a name="remarks"></a>Remarks

Этот метод следует использовать только с элементами управления, стиль кнопки которых BS_COMMANDLINK или BS_DEFCOMMANDLINK.

Этот метод отправляет [BCM_GETNOTELENGTH](/windows/win32/Controls/bcm-getnotelength) сообщение, описанное в Windows SDK.

##  <a name="getsplitglyph"></a>Кбуттон:: Жетсплитглиф

Извлекает глиф, связанный с текущим элементом управления "кнопка разделения".

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Возвращаемое значение

Символ глифа, связанный с текущим элементом управления "кнопка разделения".

### <a name="remarks"></a>Remarks

Глиф — это физическое представление символа в определенном шрифте. Например, элемент управления "разворачивающаяся кнопка" может быть снабжен глифом символа галочки в Юникоде (U + 2713).

Этот метод следует использовать только с элементами управления, стиль кнопки которых BS_SPLITBUTTON или BS_DEFSPLITBUTTON.

Этот метод инициализирует `mask` элемент структуры [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) с флагом BCSIF_GLYPH, а затем отправляет эту структуру в сообщение [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , описанное в Windows SDK. Когда функция Message возвращает, этот метод извлекает глиф из `himlGlyph` элемента структуры.

##  <a name="getsplitimagelist"></a>Кбуттон:: Жетсплитимажелист

Извлекает [список изображений](../../mfc/reference/cimagelist-class.md) для текущего элемента управления "кнопка разделения".

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на объект [CImageList](../../mfc/reference/cimagelist-class.md) .

### <a name="remarks"></a>Remarks

Этот метод следует использовать только с элементами управления, стиль кнопки которых BS_SPLITBUTTON или BS_DEFSPLITBUTTON.

Этот метод инициализирует `mask` элемент структуры [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) с флагом BCSIF_IMAGE, а затем отправляет эту структуру в сообщение [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , описанное в Windows SDK. Когда функция Message возвращает, этот метод извлекает список изображений из `himlGlyph` элемента структуры.

##  <a name="getsplitinfo"></a>Кбуттон:: Жетсплитинфо

Извлекает параметры, определяющие, как Windows рисует текущий элемент управления "кнопка разделения".

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Параметры

|Параметр|Description|
|---------------|-----------------|
|*пинфо*|заполняет Указатель на структуру [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) , которая получает сведения о текущем элементе управления "кнопка разделения". Вызывающий объект отвечает за выделение структуры.|

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

### <a name="remarks"></a>Remarks

Этот метод следует использовать только с элементами управления, стиль кнопки которых BS_SPLITBUTTON или BS_DEFSPLITBUTTON.

Этот метод отправляет [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) сообщение, описанное в Windows SDK.

##  <a name="getsplitsize"></a>Кбуттон:: Жетсплитсизе

Извлекает ограничивающий прямоугольник из раскрывающегося компонента элемента управления текущей кнопки разделения.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Параметры

|Параметр|Description|
|---------------|-----------------|
|*псизе*|заполняет Указатель на структуру [размера](/windows/win32/api/windef/ns-windef-size) , которая получает описание прямоугольника.|

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

### <a name="remarks"></a>Remarks

Этот метод следует использовать только с элементами управления, стиль кнопки которых BS_SPLITBUTTON или BS_DEFSPLITBUTTON.

Когда элемент управления "разворачивающаяся кнопка" развернут, он может отображать раскрывающийся компонент, например элемент управления "список" или "страничный навигатор". Этот метод извлекает ограничивающий прямоугольник, который содержит раскрывающийся компонент.

Этот метод инициализирует `mask` элемент структуры [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) с флагом BCSIF_SIZE, а затем отправляет эту структуру в сообщение [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , описанное в Windows SDK. Когда функция Message возвращает, этот метод извлекает ограничивающий прямоугольник из `size` элемента структуры.

##  <a name="getsplitstyle"></a>Кбуттон:: Жетсплитстиле

Извлекает стили разворачивающейся кнопки, которые определяют текущий элемент управления "кнопка разделения".

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Возвращаемое значение

Побитовое сочетание стилей разворачивающейся кнопки. Дополнительные сведения см. в описании элемента `uSplitStyle` структуры [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .

### <a name="remarks"></a>Remarks

Этот метод следует использовать только с элементами управления, стиль кнопки которых BS_SPLITBUTTON или BS_DEFSPLITBUTTON.

Стили разворачивающейся кнопки определяют выравнивание, пропорции и графический формат, с помощью которого Windows рисует значок разворачивающейся кнопки.

Этот метод инициализирует `mask` элемент структуры [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) с флагом BCSIF_STYLE, а затем отправляет эту структуру в сообщение [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , описанное в Windows SDK. Когда функция Message возвращает, этот метод извлекает стили разворачивающейся кнопки из `uSplitStyle` элемента структуры.

##  <a name="getstate"></a>Кбуттон:: State

Получает состояние элемента управления "Кнопка".

```
UINT GetState() const;
```

### <a name="return-value"></a>Возвращаемое значение

Битовое поле, содержащее сочетание значений, которое указывает текущее состояние элемента управления "Кнопка". В следующей таблице перечислены возможные значения.

|Состояние кнопки|Значение|Description|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|Начальное состояние.|
|BST_CHECKED|0x0001|Элемент управления "Кнопка" установлен.|
|BST_INDETERMINATE|0x0002|Состояние является неопределенным (возможно только в том случае, если элемент управления "Кнопка" имеет три состояния).|
|BST_PUSHED|0x0004|Нажата кнопка управления Button.|
|BST_FOCUS|0x0008|Фокус находится на элементе управления "Кнопка".|

### <a name="remarks"></a>Remarks

Элемент управления "Кнопка" с стилем BS_3STATE или BS_AUTO3STATE создает флажок с третьим состоянием с именем "неопределенное состояние". Неопределенное состояние указывает, что флажок не установлен и не снят.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="gettextmargin"></a>Кбуттон:: Жеттекстмаргин

Вызовите этот метод, чтобы получить текстовое поле объекта `CButton`.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Параметры

*пмаргин*<br/>
Указатель на текстовое поле объекта `CButton`.

### <a name="return-value"></a>Возвращаемое значение

Возвращает текстовое поле.

### <a name="remarks"></a>Remarks

Имеет ненулевое значение в случае успешного выполнения, иначе — 0.

### <a name="remarks"></a>Remarks

Эта функция члена эмулирует функциональность BCM_GETTEXTMARGIN сообщения, как описано в разделе [кнопки](/windows/win32/controls/buttons) Windows SDK.

##  <a name="setbitmap"></a>Кбуттон:: Сетбитмап

Вызовите эту функцию-член, чтобы связать новое растровое изображение с кнопкой.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Параметры

*хбитмап*<br/>
Маркер точечного рисунка.

### <a name="return-value"></a>Возвращаемое значение

Маркер точечного рисунка, ранее связанный с кнопкой.

### <a name="remarks"></a>Remarks

Точечный рисунок будет автоматически размещается на лицевой стороне кнопки по умолчанию. Если точечный рисунок слишком велик для кнопки, он будет обрезан с любой стороны. Можно выбрать другие параметры выравнивания, включая следующие.

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

В отличие от [кбитмапбуттон](../../mfc/reference/cbitmapbutton-class.md), которая использует четыре точечных рисунка для кнопки, `SetBitmap` использует только одно растровое изображение для кнопки. При нажатии кнопки точечный рисунок будет перемещен вниз и вправо.

Вы несете ответственность за освобождение точечного рисунка по завершении его действий.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="setbuttonstyle"></a>Кбуттон:: Сетбуттонстиле

Изменяет стиль кнопки.

```
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Параметры

*нстиле*<br/>
Задает [стиль кнопки](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*bRedraw*<br/>
Указывает, следует ли перерисовать кнопку. Ненулевое значение перерисовывает кнопку. Значение 0 не рисует кнопку повторно. По умолчанию кнопка перерисовывается.

### <a name="remarks"></a>Remarks

Используйте функцию члена `GetButtonStyle`, чтобы получить стиль кнопки. Слово полного стиля кнопки "полный" является стилем для определенной кнопки.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="setcheck"></a>Кбуттон:: Сетчекк

Задает или сбрасывает состояние флажка для переключателя или флажка.

```
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Параметры

*nДополнительные*<br/>
Задает состояние проверки. Возможные значения этого параметра:

|Значение|Значение|
|-----------|-------------|
|BST_UNCHECKED|Установите для кнопки состояние "снят".|
|BST_CHECKED|Установите состояние кнопки "установлен".|
|BST_INDETERMINATE|Задайте для кнопки состояние неопределенное. Это значение можно использовать, только если кнопка имеет стиль BS_3STATE или BS_AUTO3STATE.|

### <a name="remarks"></a>Remarks

Эта функция-член не влияет на команду.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="setcursor"></a>Кбуттон:: Сеткурсор

Вызовите эту функцию-член, чтобы связать новый курсор с кнопкой.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Параметры

*хкурсор*<br/>
Указатель курсора.

### <a name="return-value"></a>Возвращаемое значение

Маркер курсора, который ранее был связан с кнопкой.

### <a name="remarks"></a>Remarks

Курсор будет автоматически размещается на лицевой стороне кнопки по умолчанию. Если курсор слишком велик для кнопки, он будет обрезан с любой стороны. Можно выбрать другие параметры выравнивания, включая следующие.

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

В отличие от [кбитмапбуттон](../../mfc/reference/cbitmapbutton-class.md), которая использует четыре точечных рисунка для каждой кнопки, `SetCursor` использует только один курсор для кнопки. При нажатии кнопки курсор перемещается вниз и вправо.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="setdropdownstate"></a>Кбуттон:: Сетдропдовнстате

Задает состояние раскрывающегося списка текущего элемента управления "кнопка разворачивающейся кнопки".

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Параметры

|Параметр|Description|
|---------------|-----------------|
|*фдропдовн*|окне Значение TRUE, чтобы задать BST_DROPDOWNPUSHED состояние; в противном случае — значение FALSE.|

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

### <a name="remarks"></a>Remarks

Элемент управления "разворачивающаяся кнопка" имеет стиль BS_SPLITBUTTON или BS_DEFSPLITBUTTON и состоит из кнопки и стрелки раскрывающегося списка справа. Дополнительные сведения см. в разделе [стили кнопок](/windows/win32/Controls/button-styles). Как правило, раскрывающийся список задается, когда пользователь щелкает стрелку раскрывающегося списка. Этот метод используется для программного задания состояния раскрывающегося списка элемента управления. Стрелка раскрывающегося списка отображается затененной, чтобы показать состояние.

Этот метод отправляет [BCM_SETDROPDOWNSTATE](/windows/win32/Controls/bcm-setdropdownstate) сообщение, описанное в Windows SDK.

### <a name="example"></a>Пример

В следующем примере кода определяется переменная, *m_splitButton*, которая используется для программного доступа к элементу управления "кнопка разделения". Эта переменная используется в следующем примере.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Пример

В следующем примере кода задается состояние элемента управления "разворачивающаяся кнопка", чтобы показать, что стрелка раскрывающегося списка отправлена.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

##  <a name="setelevationrequired"></a>Кбуттон:: Сетелеватионрекуиред

Устанавливает состояние текущего элемента управления "Кнопка" в значение `elevation required`, которое необходимо для отображения значка безопасности с повышенными привилегиями.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Параметры

|Параметр|Description|
|---------------|-----------------|
|*фелеватионрекуиред*|окне Значение TRUE, чтобы задать `elevation required` состояние; в противном случае — значение FALSE.|

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

### <a name="remarks"></a>Remarks

Если элементу управления "Кнопка" или "ссылка на команду" требуется повышенная безопасность для выполнения действия, задайте для элемента управления состояние `elevation required`. В дальнейшем Windows отображает значок щита контроля учетных записей (UAC) на элементе управления. Дополнительные сведения см. в разделе "контроль учетных записей пользователей" на [сайте MSDN](https://go.microsoft.com/fwlink/p/?linkid=18507).

Этот метод отправляет [BCM_SETSHIELD](/windows/win32/Controls/bcm-setshield) сообщение, описанное в Windows SDK.

##  <a name="seticon"></a>Кбуттон:: Сетикон

Вызовите эту функцию-член, чтобы связать новый значок с кнопкой.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Параметры

*hIcon*<br/>
Маркер значка.

### <a name="return-value"></a>Возвращаемое значение

Маркер значка, который ранее был связан с кнопкой.

### <a name="remarks"></a>Remarks

Значок будет автоматически размещается на лицевой стороне кнопки и выравнивается по умолчанию. Если значок слишком велик для кнопки, он будет обрезан с любой стороны. Можно выбрать другие параметры выравнивания, включая следующие.

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

В отличие от [кбитмапбуттон](../../mfc/reference/cbitmapbutton-class.md), которая использует четыре точечных рисунка для каждой кнопки, `SetIcon` использует только один значок для кнопки. При нажатии кнопки значок отображается, чтобы сдвинуться вниз и вправо.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="setimagelist"></a>Кбуттон:: Сетимажелист

Вызовите этот метод, чтобы задать список изображений для объекта `CButton`.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Параметры

*пбуттонимажелист*<br/>
Указатель на новый список изображений.

### <a name="return-value"></a>Возвращаемое значение

Возвращает TRUE при успешном выполнении, FALSE в случае сбоя.

### <a name="remarks"></a>Remarks

Эта функция члена эмулирует функциональность BCM_SETIMAGELIST сообщения, как описано в разделе [кнопки](/windows/win32/controls/buttons) Windows SDK.

##  <a name="setnote"></a>Кбуттон:: Сетноте

Задает текст примечания для текущего элемента управления ссылки на команду.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Параметры

|Параметр|Description|
|---------------|-----------------|
|*лпсзноте*|окне Указатель на строку в Юникоде, заданную как текст примечания для элемента управления ссылки на команду.|

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

### <a name="remarks"></a>Remarks

Этот метод следует использовать только с элементами управления, стиль кнопки которых BS_COMMANDLINK или BS_DEFCOMMANDLINK.

Этот метод отправляет [BCM_SETNOTE](/windows/win32/Controls/bcm-setnote) сообщение, описанное в Windows SDK.

### <a name="example"></a>Пример

В следующем примере кода определяется переменная *m_cmdLink*, которая используется для программного доступа к элементу управления ссылками на команды. Эта переменная используется в следующем примере.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Пример

В следующем примере кода задается текст примечания для элемента управления "ссылка на команду".

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

##  <a name="setsplitglyph"></a>Кбуттон:: Сетсплитглиф

Связывает указанный глиф с текущим элементом управления "кнопка разделения".

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Параметры

|Параметр|Description|
|---------------|-----------------|
|*чглиф*|окне Символ, указывающий глиф, используемый в качестве раскрывающегося списка для кнопки разделения.|

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

### <a name="remarks"></a>Remarks

Этот метод следует использовать только с элементами управления, имеющими стиль кнопки BS_SPLITBUTTON или BS_DEFSPLITBUTTON.

Глиф — это физическое представление символа в определенном шрифте. Параметр *чглиф* не используется в качестве глифа, а используется для выбора глифа из набора определенных системой глифов. Значок стрелки раскрывающегося списка по умолчанию задается символом "6" и напоминает символ Юникода с ЧЕРНым НАПРАВЛЕНным вниз ТРЕУГОЛЬНИКом (U + 25BC).

Этот метод инициализирует `mask` член структуры [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) с флагом BCSIF_GLYPH и элементом `himlGlyph` с параметром *чглиф* , а затем отправляет эту структуру в сообщении [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , описанном в Windows SDK.

##  <a name="setsplitimagelist"></a>Кбуттон:: Сетсплитимажелист

Связывает [список изображений](../../mfc/reference/cimagelist-class.md) с текущим элементом управления "кнопка разделения".

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Параметры

|Параметр|Description|
|---------------|-----------------|
|*псплитимажелист*|окне Указатель на объект [CImageList](../../mfc/reference/cimagelist-class.md) , присваиваемый текущему элементу управления кнопки разделения.|

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

### <a name="remarks"></a>Remarks

Этот метод следует использовать только с элементами управления, стиль кнопки которых BS_SPLITBUTTON или BS_DEFSPLITBUTTON.

Этот метод инициализирует `mask` член структуры [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) с флагом BCSIF_IMAGE и элементом `himlGlyph` с параметром *псплитимажелист* , а затем отправляет эту структуру в сообщении [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , описанном в Windows SDK.

##  <a name="setsplitinfo"></a>Кбуттон:: Сетсплитинфо

Задает параметры, определяющие, как Windows рисует текущий элемент управления "кнопка разделения".

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Параметры

|Параметр|Description|
|---------------|-----------------|
|*пинфо*|окне Указатель на структуру [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) , которая определяет текущий элемент управления "кнопка разделения".|

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

### <a name="remarks"></a>Remarks

Этот метод следует использовать только с элементами управления, стиль кнопки которых BS_SPLITBUTTON или BS_DEFSPLITBUTTON.

Этот метод отправляет [BCM_SETSPLITINFO](/windows/win32/Controls/bcm-setsplitinfo) сообщение, описанное в Windows SDK.

### <a name="example"></a>Пример

В следующем примере кода определяется переменная, `m_splitButton`, которая используется для программного доступа к элементу управления "кнопка разделения".

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Пример

В следующем примере кода изменяется глиф, используемый для стрелки раскрывающегося списка для кнопки разделения. В этом примере заменяется значок, указывающий вверх, для глифа, указывающего вниз по умолчанию. Отображаемый глиф зависит от символа, указанного в `himlGlyph` элемента структуры `BUTTON_SPLITINFO`. Значок треугольника, указывающий вниз, задается символом «6», а глифом, направленным вверх, задается символ «5». Для сравнения см. удобный метод [кбуттон:: сетсплитглиф](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

##  <a name="setsplitsize"></a>Кбуттон:: Сетсплитсизе

Задает ограничивающий прямоугольник для компонента раскрывающегося списка текущего элемента управления "кнопка разворачивающейся кнопки".

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Параметры

|Параметр|Description|
|---------------|-----------------|
|*псизе*|окне Указатель на структуру [размера](/windows/win32/api/windef/ns-windef-size) , описывающую ограничивающий прямоугольник.|

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

### <a name="remarks"></a>Remarks

Этот метод следует использовать только с элементами управления, стиль кнопки которых BS_SPLITBUTTON или BS_DEFSPLITBUTTON.

Когда элемент управления "разворачивающаяся кнопка" развернут, он может отображать раскрывающийся компонент, например элемент управления "список" или "страничный навигатор". Этот метод задает размер ограничивающего прямоугольника, содержащего раскрывающийся компонент.

Этот метод инициализирует `mask` член структуры [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) с флагом BCSIF_SIZE и элементом `size` с параметром *псизе* , а затем отправляет эту структуру в сообщении [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , описанном в Windows SDK.

### <a name="example"></a>Пример

В следующем примере кода определяется переменная, `m_splitButton`, которая используется для программного доступа к элементу управления "кнопка разделения". Эта переменная используется в следующем примере.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Пример

В следующем примере кода удваивается размер стрелки раскрывающегося списка в разворачивающейся кнопке.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

##  <a name="setsplitstyle"></a>Кбуттон:: Сетсплитстиле

Задает стиль текущего элемента управления "кнопка разворачивающейся кнопки".

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Параметры

|Параметр|Description|
|---------------|-----------------|
|*усплитстиле*|окне Побитовое сочетание стилей разворачивающейся кнопки. Дополнительные сведения см. в описании элемента `uSplitStyle` структуры [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .|

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

### <a name="remarks"></a>Remarks

Этот метод следует использовать только с элементами управления, стиль кнопки которых BS_SPLITBUTTON или BS_DEFSPLITBUTTON.

Стили разворачивающейся кнопки определяют выравнивание, пропорции и графический формат, с помощью которого Windows рисует значок разворачивающейся кнопки. Дополнительные сведения см. в описании элемента `uSplitStyle` структуры [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .

Этот метод инициализирует `mask` член структуры [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) с флагом BCSIF_STYLE и элементом `uSplitStyle` с параметром *усплитстиле* , а затем отправляет эту структуру в сообщении [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , описанном в Windows SDK.

### <a name="example"></a>Пример

В следующем примере кода определяется переменная, `m_splitButton`, которая используется для программного доступа к элементу управления "кнопка разделения".

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Пример

В следующем примере кода задается стиль стрелки раскрывающегося списка для кнопки разделения. BCSS_ALIGNLEFT стиль отображает стрелку в левой части кнопки, а стиль BCSS_STRETCH при изменении размера кнопки удерживает пропорции стрелки раскрывающегося списка.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

##  <a name="setstate"></a>Кбуттон:: SetState

Определяет, выделен ли элемент управления "Кнопка".

```
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Параметры

*бхигхлигхт*<br/>
Указывает, следует ли выделять кнопку. Ненулевое значение выделяет кнопку. значение 0 удаляет все выделения.

### <a name="remarks"></a>Remarks

Выделение влияет на наружную часть элемента управления "Кнопка". Он не влияет на состояние флажка переключателя или на флажок.

Элемент управления "Кнопка" автоматически выделяется, когда пользователь нажимает и удерживает левую кнопку мыши. Выделение удаляется, когда пользователь отпускает кнопку мыши.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="settextmargin"></a>Кбуттон:: Сеттекстмаргин

Вызовите этот метод, чтобы задать текстовое поле объекта `CButton`.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Параметры

*пмаргин*<br/>
Указатель на новое текстовое поле.

### <a name="return-value"></a>Возвращаемое значение

Возвращает TRUE при успешном выполнении, FALSE в случае сбоя.

### <a name="remarks"></a>Remarks

Эта функция члена эмулирует функциональность BCM_SETTEXTMARGIN сообщения, как описано в разделе [кнопки](/windows/win32/controls/buttons) Windows SDK.

## <a name="see-also"></a>См. также раздел

[Класс CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Диаграмма иерархии](../../mfc/hierarchy-chart.md)<br/>
[Класс CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Класс CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Класс CEdit](../../mfc/reference/cedit-class.md)<br/>
[Класс CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Класс CScrollBar](../../mfc/reference/cscrollbar-class.md)<br/>
[Класс CStatic](../../mfc/reference/cstatic-class.md)<br/>
[Класс CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)<br/>
[Класс CDialog](../../mfc/reference/cdialog-class.md)
