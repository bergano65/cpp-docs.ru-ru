---
title: Класс Иатлмеммгр
ms.date: 11/04/2016
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
ms.openlocfilehash: a0d79ae95a0604ca75f03673873e99394a1bc295
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423090"
---
# <a name="iatlmemmgr-class"></a>Класс Иатлмеммгр

Этот класс представляет интерфейс для диспетчера памяти.

## <a name="syntax"></a>Синтаксис

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>Члены

### <a name="methods"></a>Методы

|||
|-|-|
|[Памяти](#allocate)|Вызовите этот метод, чтобы выделить блок памяти.|
|[Бесплатный](#free)|Вызовите этот метод, чтобы освободить блок памяти.|
|[GetSize](#getsize)|Вызовите этот метод, чтобы получить размер выделенного блока памяти.|
|[Перераспределения](#reallocate)|Вызовите этот метод, чтобы перераспределить блок памяти.|

## <a name="remarks"></a>Remarks

Этот интерфейс реализуется с помощью [ккомхеап](../../atl/reference/ccomheap-class.md), [ккрсеап](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CCRTHeap](../../atl/reference/cglobalheap-class.md)или [CWin32Heap](../../atl/reference/cwin32heap-class.md).

> [!NOTE]
>  Локальные и глобальные функции кучи выполняются медленнее, чем другие функции управления памятью, и не предоставляют столько функций. Поэтому новые приложения должны использовать [функции кучи](/windows/win32/Memory/heap-functions). Они доступны в классе [CWin32Heap](../../atl/reference/cwin32heap-class.md) .

## <a name="example"></a>Пример

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Требования

**Заголовок:** атлмем. h

##  <a name="allocate"></a>Иатлмеммгр:: allocate

Вызовите этот метод, чтобы выделить блок памяти.

```
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Параметры

*nBytes*<br/>
Запрошенное число байтов в новом блоке памяти.

### <a name="return-value"></a>Возвращаемое значение

Возвращает указатель на начало выделенного блока памяти.

### <a name="remarks"></a>Remarks

Вызовите метод [иатлмеммгр:: Free](#free) или [иатлмеммгр:: reallocate](#reallocate) , чтобы освободить память, выделенную этим методом.

### <a name="example"></a>Пример

Пример см. в [обзоре иатлмеммгр](../../atl/reference/iatlmemmgr-class.md).

##  <a name="free"></a>Иатлмеммгр:: Free

Вызовите этот метод, чтобы освободить блок памяти.

```
void Free(void* p) throw();
```

### <a name="parameters"></a>Параметры

*p*<br/>
Указатель на область памяти, выделенную ранее данным диспетчером памяти.

### <a name="remarks"></a>Remarks

Используйте этот метод для освобождения памяти, полученной с помощью [иатлмеммгр:: allocate](#allocate) или [иатлмеммгр:: reallocate](#reallocate).

### <a name="example"></a>Пример

Пример см. в [обзоре иатлмеммгр](../../atl/reference/iatlmemmgr-class.md).

##  <a name="getsize"></a>Иатлмеммгр:: DataSize

Вызовите этот метод, чтобы получить размер выделенного блока памяти.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Параметры

*p*<br/>
Указатель на область памяти, выделенную ранее данным диспетчером памяти.

### <a name="return-value"></a>Возвращаемое значение

Возвращает размер блока памяти в байтах.

### <a name="example"></a>Пример

Пример см. в [обзоре иатлмеммгр](../../atl/reference/iatlmemmgr-class.md).

##  <a name="reallocate"></a>Иатлмеммгр:: перераспределение

Вызовите этот метод для перераспределения памяти, выделенной данным диспетчером памяти.

```
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Параметры

*p*<br/>
Указатель на область памяти, выделенную ранее данным диспетчером памяти.

*nBytes*<br/>
Запрошенное число байтов в новом блоке памяти.

### <a name="return-value"></a>Возвращаемое значение

Возвращает указатель на начало выделенного блока памяти.

### <a name="remarks"></a>Remarks

Вызовите метод [иатлмеммгр:: Free](#free) или [иатлмеммгр:: reallocate](#reallocate) , чтобы освободить память, выделенную этим методом.

По сути, этот метод освобождает имеющуюся память и выделяет новый блок памяти. На практике существующая память может быть расширена или использована повторно.

### <a name="example"></a>Пример

Пример см. в [обзоре иатлмеммгр](../../atl/reference/iatlmemmgr-class.md).

##  <a name="get_allowcontextmenu"></a>Иаксвинамбиентдиспатч:: get_AllowContextMenu

Свойство `AllowContextMenu` указывает, разрешено ли размещенному элементу управления отображать собственное контекстное меню.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Параметры

*пбалловконтекстмену*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует VARIANT_TRUE в качестве значения этого свойства по умолчанию.

##  <a name="get_allowshowui"></a>Иаксвинамбиентдиспатч:: get_AllowShowUI

Свойство `AllowShowUI` указывает, разрешено ли размещенному элементу управления отображать собственный пользовательский интерфейс.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Параметры

*пбалловшовуи*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует VARIANT_FALSE в качестве значения этого свойства по умолчанию.

##  <a name="get_allowwindowlessactivation"></a>Иаксвинамбиентдиспатч:: get_AllowWindowlessActivation

Свойство `AllowWindowlessActivation` указывает, будет ли контейнер разрешать активацию без окон.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Параметры

*пбалловвиндовлесс*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует VARIANT_TRUE в качестве значения этого свойства по умолчанию.

##  <a name="get_backcolor"></a>Иаксвинамбиентдиспатч:: get_BackColor

Свойство `BackColor` задает цвет фона окружения для контейнера.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Параметры

*пклрбаккграунд*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует COLOR_BTNFACE или COLOR_WINDOW как значение этого свойства по умолчанию (в зависимости от того, является ли родительский элемент главного окна диалоговым окном или нет).

##  <a name="get_displayasdefault"></a>Иаксвинамбиентдиспатч:: get_DisplayAsDefault

`DisplayAsDefault` — это внешнее свойство, позволяющее элементу управления определить, является ли он элементом управления по умолчанию.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Параметры

*пбдисплайасдефаулт*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует VARIANT_FALSE в качестве значения этого свойства по умолчанию.

##  <a name="get_dochostdoubleclickflags"></a>Иаксвинамбиентдиспатч:: get_DocHostDoubleClickFlags

Свойство `DocHostDoubleClickFlags` указывает операцию, которая должна быть выполнена в ответ на двойной щелчок.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Параметры

*пдвдочостдаублекликкфлагс*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует DOCHOSTUIDBLCLK_DEFAULT в качестве значения этого свойства по умолчанию.

##  <a name="get_dochostflags"></a>Иаксвинамбиентдиспатч:: get_DocHostFlags

Свойство `DocHostFlags` указывает возможности пользовательского интерфейса для объекта узла.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Параметры

*пдвдочостфлагс*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует DOCHOSTUIFLAG_NO3DBORDER в качестве значения этого свойства по умолчанию.

##  <a name="get_font"></a>Иаксвинамбиентдиспатч:: get_Font

Свойство `Font` задает внешний шрифт контейнера.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Параметры

*пфонт*<br/>
заполняет Адрес указателя интерфейса `IFontDisp`, используемого для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует шрифт графического пользовательского интерфейса по умолчанию или системный шрифт в качестве значения по умолчанию для этого свойства.

##  <a name="get_forecolor"></a>Иаксвинамбиентдиспатч:: get_ForeColor

Свойство `ForeColor` задает цвет переднего плана окружения.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Параметры

*пклрфореграунд*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует цвет текста системного окна в качестве значения по умолчанию для этого свойства.

##  <a name="get_localeid"></a>Иаксвинамбиентдиспатч:: get_LocaleID

Свойство `LocaleID` указывает идентификатор локали для контейнера.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Параметры

*плЦидлокалеид*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует языковой стандарт по умолчанию пользователя в качестве значения этого свойства по умолчанию.

С помощью этого метода можно обнаружить внешний LocalID, т. е. LocaleID программы, в которой используется элемент управления. Зная LocaleID, вы можете вызвать код для загрузки заголовков для определенного языкового стандарта, текста сообщения об ошибке и т. д. из файла ресурсов или вспомогательной библиотеки DLL.

##  <a name="get_messagereflect"></a>Иаксвинамбиентдиспатч:: get_MessageReflect

Свойство внешнего `MessageReflect` указывает, будет ли контейнер отражать сообщения размещаемому элементу управления.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Параметры

*пбмессажерефлект*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует VARIANT_TRUE в качестве значения этого свойства по умолчанию.

##  <a name="get_optionkeypath"></a>Иаксвинамбиентдиспатч:: get_OptionKeyPath

Свойство `OptionKeyPath` указывает путь к разделу реестра для параметров пользователя.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Параметры

*пбстроптионкэйпас*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

##  <a name="get_showgrabhandles"></a>Иаксвинамбиентдиспатч:: get_ShowGrabHandles

Свойство окружения `ShowGrabHandles` позволяет элементу управления определить, должен ли он рисовать себя с маркерами захвата.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Параметры

*пбшовграбхандлес*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL всегда возвращает VARIANT_FALSE в качестве значения этого свойства.

##  <a name="get_showhatching"></a>Иаксвинамбиентдиспатч:: get_ShowHatching

`ShowHatching` свойство окружения позволяет элементу управления определить, должен ли он рисовать штриховой.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Параметры

*пбшовхатчинг*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL всегда возвращает VARIANT_FALSE в качестве значения этого свойства.

##  <a name="get_usermode"></a>Иаксвинамбиентдиспатч:: get_UserMode

Свойство `UserMode` указывает внешний пользовательский режим контейнера.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Параметры

*пбусермоде*<br/>
заполняет Адрес переменной для получения текущего значения этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует VARIANT_TRUE в качестве значения этого свойства по умолчанию.

##  <a name="put_allowcontextmenu"></a>Иаксвинамбиентдиспатч::p ut_AllowContextMenu

Свойство `AllowContextMenu` указывает, разрешено ли размещенному элементу управления отображать собственное контекстное меню.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Параметры

*балловконтекстмену*<br/>
окне Новое значение этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует VARIANT_TRUE в качестве значения этого свойства по умолчанию.

##  <a name="put_allowshowui"></a>Иаксвинамбиентдиспатч::p ut_AllowShowUI

Свойство `AllowShowUI` указывает, разрешено ли размещенному элементу управления отображать собственный пользовательский интерфейс.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Параметры

*балловшовуи*<br/>
окне Новое значение этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует VARIANT_FALSE в качестве значения этого свойства по умолчанию.

##  <a name="put_allowwindowlessactivation"></a>Иаксвинамбиентдиспатч::p ut_AllowWindowlessActivation

Свойство `AllowWindowlessActivation` указывает, будет ли контейнер разрешать активацию без окон.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Параметры

*балловвиндовлесс*<br/>
окне Новое значение этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует VARIANT_TRUE в качестве значения этого свойства по умолчанию.

##  <a name="put_backcolor"></a>Иаксвинамбиентдиспатч::p ut_BackColor

Свойство `BackColor` задает цвет фона окружения для контейнера.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Параметры

*клрбаккграунд*<br/>
окне Новое значение этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует COLOR_BTNFACE или COLOR_WINDOW как значение этого свойства по умолчанию (в зависимости от того, является ли родительский элемент главного окна диалоговым окном или нет).

##  <a name="put_displayasdefault"></a>Иаксвинамбиентдиспатч::p ut_DisplayAsDefault

`DisplayAsDefault` — это внешнее свойство, позволяющее элементу управления определить, является ли он элементом управления по умолчанию.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Параметры

*бдисплайасдефаулт*<br/>
окне Новое значение этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует VARIANT_FALSE в качестве значения этого свойства по умолчанию.

##  <a name="put_dochostdoubleclickflags"></a>Иаксвинамбиентдиспатч::p ut_DocHostDoubleClickFlags

Свойство `DocHostDoubleClickFlags` указывает операцию, которая должна быть выполнена в ответ на двойной щелчок.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Параметры

*двдочостдаублекликкфлагс*<br/>
окне Новое значение этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует DOCHOSTUIDBLCLK_DEFAULT в качестве значения этого свойства по умолчанию.

##  <a name="put_dochostflags"></a>Иаксвинамбиентдиспатч::p ut_DocHostFlags

Свойство `DocHostFlags` указывает возможности пользовательского интерфейса для объекта узла.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Параметры

*двдочостфлагс*<br/>
окне Новое значение этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует DOCHOSTUIFLAG_NO3DBORDER в качестве значения этого свойства по умолчанию.

##  <a name="put_font"></a>Иаксвинамбиентдиспатч::p ut_Font

Свойство `Font` задает внешний шрифт контейнера.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Параметры

*пфонт*<br/>
окне Новое значение этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует шрифт графического пользовательского интерфейса по умолчанию или системный шрифт в качестве значения по умолчанию для этого свойства.

##  <a name="put_forecolor"></a>Иаксвинамбиентдиспатч::p ut_ForeColor

Свойство `ForeColor` задает цвет переднего плана окружения.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Параметры

*клрфореграунд*<br/>
окне Новое значение этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует цвет текста системного окна в качестве значения по умолчанию для этого свойства.

##  <a name="put_localeid"></a>Иаксвинамбиентдиспатч::p ut_LocaleID

Свойство `LocaleID` указывает идентификатор локали для контейнера.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Параметры

*лЦидлокалеид*<br/>
окне Новое значение этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует языковой стандарт по умолчанию пользователя в качестве значения этого свойства по умолчанию.

##  <a name="put_messagereflect"></a>Иаксвинамбиентдиспатч::p ut_MessageReflect

Свойство внешнего `MessageReflect` указывает, будет ли контейнер отражать сообщения размещаемому элементу управления.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Параметры

*бмессажерефлект*<br/>
окне Новое значение этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует VARIANT_TRUE в качестве значения этого свойства по умолчанию.

##  <a name="put_optionkeypath"></a>Иаксвинамбиентдиспатч::p ut_OptionKeyPath

Свойство `OptionKeyPath` указывает путь к разделу реестра для параметров пользователя.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Параметры

*бстроптионкэйпас*<br/>
окне Новое значение этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

##  <a name="put_usermode"></a>Иаксвинамбиентдиспатч::p ut_UserMode

Свойство `UserMode` указывает внешний пользовательский режим контейнера.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Параметры

*бусермоде*<br/>
окне Новое значение этого свойства.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Реализация объекта узла ATL использует VARIANT_TRUE в качестве значения этого свойства по умолчанию.

##  <a name="setambientdispatch"></a>Иаксвинамбиентдиспатчекс:: Сетамбиентдиспатч

Этот метод вызывается для дополнения интерфейса внешнего свойства по умолчанию с определяемым пользователем интерфейсом.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Параметры

*пдиспатч*<br/>
Указатель на новый интерфейс.

### <a name="return-value"></a>Возвращаемое значение

Возвращает S_OK при успешном выполнении или ошибку HRESULT при сбое.

### <a name="remarks"></a>Remarks

При вызове `SetAmbientDispatch` с указателем на новый интерфейс этот новый интерфейс будет использоваться для вызова свойств или методов, запрашиваемых размещенным элементом управления, если эти свойства еще не предоставлены [иаксвинамбиентдиспатч](../../atl/reference/iaxwinambientdispatch-interface.md).

##  <a name="attachcontrol"></a>Иаксвинхоствиндов:: Аттачконтрол

Присоединяет существующий (и ранее инициализированный) элемент управления к объекту узла с помощью окна, идентифицируемого *HWND*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Параметры

*пункконтрол*<br/>
окне Указатель на интерфейс `IUnknown` элемента управления, который должен быть присоединен к объекту узла.

*hWnd*<br/>
окне Маркер окна, который будет использоваться для размещения.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

##  <a name="createcontrol"></a>Иаксвинхоствиндов:: CreateControl

Создает элемент управления, инициализирует его и размещает его в окне, определяемом *HWND*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Параметры

*лптриксдата*<br/>
окне Строка, идентифицирующая создаваемый элемент управления. Может быть идентификатором CLSID (должен содержать фигурные скобки), ProgID, URL-адрес или необработанный HTML (с префиксом **MSHTML:** ).

*hWnd*<br/>
окне Маркер окна, который будет использоваться для размещения.

*пстреам*<br/>
окне Указатель интерфейса для потока, содержащего данные инициализации для элемента управления. Может иметь значение NULL.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Это окно будет подклассировать объектом размещения, который предоставляет этот интерфейс, чтобы сообщения могли быть отражены в элементе управления, а другие функции контейнера будут работать.

Вызов этого метода эквивалентен вызову [иаксвинхоствиндов:: креатеконтролекс](#createcontrolex).

Сведения о создании лицензированного элемента управления ActiveX см. в разделе [иаксвинхоствиндовлик:: креатеконтроллик](#createcontrollicex).

##  <a name="createcontrolex"></a>Иаксвинхоствиндов:: Креатеконтролекс

Создает элемент управления ActiveX, инициализирует его и размещает его в указанном окне аналогично [иаксвинхоствиндов:: CreateControl](#createcontrol).

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>Параметры

*лптриксдата*<br/>
окне Строка, идентифицирующая создаваемый элемент управления. Может быть идентификатором CLSID (должен содержать фигурные скобки), ProgID, URL-адрес или необработанный HTML (с префиксом **MSHTML:** ).

*hWnd*<br/>
окне Маркер окна, который будет использоваться для размещения.

*пстреам*<br/>
окне Указатель интерфейса для потока, содержащего данные инициализации для элемента управления. Может иметь значение NULL.

*ппунк*<br/>
заполняет Адрес указателя, который получит интерфейс `IUnknown` созданного элемента управления. Может иметь значение NULL.

*риидадвисе*<br/>
окне Идентификатор интерфейса для исходящего интерфейса в автономном объекте. Можно IID_NULL.

*пункадвисе*<br/>
окне Указатель на интерфейс `IUnknown` объекта приемника, который подключается к точке подключения на содержащемся объекте, указанном `iidSink`.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

В отличие от метода `CreateControl` `CreateControlEx` также позволяет получить указатель интерфейса на вновь созданный элемент управления и настроить приемник событий для получения событий, инициированных элементом управления.

Сведения о создании лицензированного элемента управления ActiveX см. в разделе [иаксвинхоствиндовлик:: креатеконтроллицекс](#createcontrollicex).

##  <a name="querycontrol"></a>Иаксвинхоствиндов:: Куериконтрол

Возвращает указанный указатель интерфейса, предоставленный размещенным элементом управления.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Параметры

*riid*<br/>
окне Идентификатор интерфейса для запрашиваемого элемента управления.

*ппвобжект*<br/>
заполняет Адрес указателя, который получит указанный интерфейс созданного элемента управления.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

##  <a name="setexternaldispatch"></a>Иаксвинхоствиндов:: Сетекстерналдиспатч

Задает внешний диспетчерский интерфейс, доступный для вложенных элементов управления с помощью метода [идочостуихандлердиспатч:: External](../../atl/reference/idochostuihandlerdispatch-interface.md) .

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Параметры

*пдисп*<br/>
окне Указатель на интерфейс `IDispatch`.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

##  <a name="setexternaluihandler"></a>Иаксвинхоствиндов:: Сетекстерналуихандлер

Вызовите эту функцию, чтобы задать внешний интерфейс [идочостуихандлердиспатч](../../atl/reference/idochostuihandlerdispatch-interface.md) для объекта `CAxWindow`.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Параметры

*пдисп*<br/>
окне Указатель на интерфейс `IDocHostUIHandlerDispatch`.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Remarks

Эта функция используется элементами управления (например, элементом управления веб-браузера), которые запрашивают у узла узла интерфейс `IDocHostUIHandlerDispatch`.

##  <a name="createcontrollic"></a>Иаксвинхоствиндовлик:: Креатеконтроллик

Создает лицензированный элемент управления, инициализирует его и размещает его в окне, определяемом `hWnd`.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Параметры

*бстрлик*<br/>
окне Значение BSTR, содержащее лицензионный ключ для элемента управления.

### <a name="remarks"></a>Remarks

Описание оставшихся параметров и возвращаемого значения см. в разделе [иаксвинхоствиндов:: CreateControl](#createcontrol) .

Вызов этого метода эквивалентен вызову [иаксвинхоствиндовлик:: креатеконтроллицекс](#createcontrollicex)

### <a name="example"></a>Пример

Пример, в котором используется `IAxWinHostWindowLic::CreateControlLic`, см. в разделе [Размещение элементов управления ActiveX с помощью библиотеки ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) .

##  <a name="createcontrollicex"></a>Иаксвинхоствиндовлик:: Креатеконтроллицекс

Создает лицензированный элемент управления ActiveX, инициализирует его и размещает его в указанном окне аналогично [иаксвинхоствиндов:: CreateControl](#createcontrol).

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>Параметры

*бстрлик*<br/>
окне Значение BSTR, содержащее лицензионный ключ для элемента управления.

### <a name="remarks"></a>Remarks

Описание оставшихся параметров и возвращаемого значения см. в разделе [иаксвинхоствиндов:: креатеконтролекс](#createcontrolex) .

### <a name="example"></a>Пример

Пример, в котором используется `IAxWinHostWindowLic::CreateControlLicEx`, см. в разделе [Размещение элементов управления ActiveX с помощью библиотеки ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) .

## <a name="see-also"></a>См. также раздел

[Обзор класса](../../atl/atl-class-overview.md)
