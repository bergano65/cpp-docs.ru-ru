---
title: Добавление метода
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.method.overview
- vc.codewiz.method.idlattrib
helpviewer_keywords:
- add method wizard [C++]
- methods [C++], adding
- methods [C++], adding using wizards
- IDL attributes, add method wizard
ms.assetid: 4ba4e45f-fa38-4d5e-af44-cbec0a7ab558
ms.openlocfilehash: b0c8ddabc4ed08fd217545bad269f0b2e48dd49e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509535"
---
# <a name="add-a-method"></a>Добавление метода

Вы можете использовать [мастер добавления метода](#add-method-wizard) для добавления метода в интерфейс в проекте. Если проект содержит класс, сопоставленный с интерфейсом, мастер изменяет и этот класс.

**Добавление метода в объект**

1. В **представлении классов** разверните узел проекта, чтобы отобразить интерфейс, в который нужно добавить метод.

   > [!NOTE]
   > Вы также можете добавлять методы в disp-интерфейсы, которые, если только проект не имеет атрибуты, находятся в узле библиотеки.

1. Щелкните имя интерфейса правой кнопкой мыши.

1. В контекстном меню выберите команду **Добавить**, а затем нажмите **Добавить метод**.

1. В мастере добавления метода укажите сведения для создания метода.

1. Задайте параметры IDL для этого метода на странице [Атрибуты IDL](#idl-attributes-add-method-wizard) мастера.

1. Нажмите кнопку **Готово**, чтобы добавить метод.

## <a name="in-this-section"></a>Содержание раздела

- [Мастер добавления метода](#add-method-wizard)
- [Атрибуты IDL, мастер добавления метода](#idl-attributes-add-method-wizard)

## <a name="add-method-wizard"></a>Мастер добавления метода

Этот мастер используется для добавления метода в интерфейс. В зависимости от типа проекта или интерфейса, к которому добавляется метод, мастер отображает различные параметры.

### <a name="names"></a>Имена

- **Return Type** (Возвращаемый тип)

  Тип данных, возвращаемых методом. `HRESULT` рекомендуется для всех типов интерфейса, так как предоставляет стандартный способ возврата ошибок.

  |Тип интерфейса|ОПИСАНИЕ|
  |--------------------|-----------------|
  |Двойной интерфейс|`HRESULT`. Неизменяемый.|
  |Настраиваемый интерфейс|`HRESULT`. Неизменяемый.|
  |Локальный настраиваемый интерфейс|Укажите собственный тип возвращаемого значения или выберите его в списке.|
  |Disp-интерфейс|Укажите собственный тип возвращаемого значения или выберите его в списке.|
  |Disp-интерфейс элементов управления ActiveX MFC|Если вы реализуете стандартный метод, для типа возвращаемого значения задается соответствующее значение, которое является неизменяемым. Если вы выбираете метод в списке **Имя метода** и выбираете элемент **Настраиваемый** в области **Выберите тип метода**, выберите в списке тип возвращаемого значения.|

- **Имя метода**

  Задает имя метода.

  |Тип интерфейса|ОПИСАНИЕ|
  |--------------------|-----------------|
  |Двойной интерфейс ATL, настраиваемый интерфейс и локальный настраиваемый интерфейс|Укажите собственное имя метода.|
  |Disp-интерфейс MFC|Укажите собственное имя метода или выберите предложенное имя из списка. При выборе имени из списка соответствующее значение отображается в поле **Тип возвращаемого значения** и является неизменяемым.|
  |Disp-интерфейс элементов управления ActiveX MFC|Укажите свой собственный метод или выберите один из стандартных методов [DoClick](../mfc/reference/colecontrol-class.md#doclick) и [Refresh](../mfc/reference/colecontrol-class.md#refresh). Дополнительные сведения см. в разделе [Элементы управления ActiveX MFC. Добавление стандартных методов](../mfc/mfc-activex-controls-adding-stock-methods.md).|

- **Тип метода**

  Доступен только для элементов управления ActiveX MFC. Если вы указываете имя метода в поле **Имя метода**, а не выбираете его из списка, это поле недоступно.

  Если вы выбираете один из методов в поле **Имя метода**, выберите стандартную или настраиваемую реализацию.

  |Тип метода|ОПИСАНИЕ|
  |-----------------|-----------------|
  |**Биржевая**|По умолчанию. Вставляет стандартную реализацию метода, выбранного из списка **Имя метода**. При выборе параметра **Биржевая** значение **Тип возвращаемого значения** является неизменяемым.|
  |**Пользовательский**|Вставляет реализацию-заглушку метода, выбранного из списка **Имя метода**. Для пользовательских типов методов вы можете указать собственный тип возвращаемого значения или выбрать его из списка **Тип возвращаемого значения**.|

- **Внутреннее имя**

  Доступно только для пользовательских методов, добавленных в disp-интерфейс MFC. Задает имя, используемое в схеме диспетчеризации, файле заголовка (H) и файле реализации (CPP). По умолчанию это имя совпадает со значением **Имя метода**. Вы можете изменить имя метода при работе с disp-интерфейсом MFC или при добавлении пользовательского метода в disp-интерфейс элемента управления ActiveX MFC.

  |Тип интерфейса|ОПИСАНИЕ|
  |--------------------|-----------------|
  |Двойной интерфейс ATL, настраиваемый интерфейс и локальный настраиваемый интерфейс|Недоступно.|
  |Disp-интерфейс MFC|Задайте имя метода по умолчанию. Вы можете изменить внутреннее имя.|
  |Disp-интерфейс элементов управления ActiveX MFC|Вы можете задать внутреннее имя только для пользовательских методов. Стандартные методы не используют внутреннее имя.|

- **Атрибуты параметра**

  Задает дополнительные атрибуты для параметра, указанного в поле **Имя параметра**.

  |Атрибут параметра|ОПИСАНИЕ|Допустимые сочетания|
  |-------------------------|-----------------|--------------------------|
  |**In**|Указывает, что параметр передается из вызывающей процедуры в вызываемую.|Только `in`<br /><br /> `in` и `out`|
  |**Out**|Указывает, что параметр-указатель возвращается из вызываемой процедуры в вызывающую (от сервера к клиенту).|Только `out`<br /><br /> `in` и `out`<br /><br /> `out` и `retval`|
  |**Retval**|Указывает, что параметр принимает значение, возвращаемое членом.|`retval` и `out`|

- **Тип параметра**

  Задает тип данных для параметра. Выберите тип из списка.

- **Имя параметра**

  Задает имя параметра для передачи через ваш метод. После ввода имени нужно нажать кнопку **Добавить**, чтобы добавить его в список параметров, передаваемых через метод. Если имя параметра не указано, мастер игнорирует любые атрибуты параметра (ATL) или выбранные элементы в поле **Тип параметра**.

  После нажатия кнопки **Добавить** имя параметра отображается в области **Список параметров**.

  > [!NOTE]
  > Если задать имя параметра и нажать кнопку **Готово** перед нажатием кнопки **Добавить**, то параметр не добавится в метод. Нужно найти метод и вставить параметр вручную.

- **Добавить**

  Добавляет параметр, указанный в поле **Имя параметра**, а также его тип и атрибуты в **Список параметров**. Выберите **Добавить**, чтобы добавить параметр в список.

- **Remove**

  Удаляет параметр, выбранный в области **Список параметров**, из списка.

- **Список параметров**

  Отображает все параметры, а также их модификаторы и типы, добавленные для метода в настоящий момент. По мере добавления параметров мастер обновляет **Список параметров**, отображая каждый параметр вместе с его модификатором и типом.

## <a name="idl-attributes-add-method-wizard"></a>Атрибуты IDL, мастер добавления метода

Используйте эту страницу мастера добавления метода, чтобы указать все параметры IDL для этого метода.

- `id`

  Задает числовой идентификатор, который определяет этот метод. Дополнительные сведения см. в разделе, посвященном атрибуту [id](/windows/win32/Midl/id), *справочника по MIDL*.

  Это поле недоступно для настраиваемых интерфейсов и disp-интерфейсов MFC.

- `call_as`

  Указывает имя удаленного метода, с которым можно сопоставить этот локальный метод. Дополнительные сведения см. в разделе, посвященном атрибуту [call_as](/windows/win32/Midl/call-as), *справочника по MIDL*.

  Недоступно для disp-интерфейсов MFC.

- `helpcontext`

  Задает идентификатор контекста, позволяющий пользователю просматривать в файле справки информацию об этом методе. Дополнительные сведения см. в разделе, посвященном атрибуту [helpcontext](/windows/win32/Midl/helpcontext), *справочника по MIDL*.

  Недоступно для disp-интерфейсов MFC.

- `helpstring`

  Определяет строку символов, используемую для описания элемента, к которому оно применяется. По умолчанию имеет значение "method *имя метода*". Дополнительные сведения см. в разделе, посвященном атрибуту [helpstring](/windows/win32/Midl/helpstring), *справочника по MIDL*.

  Недоступно для disp-интерфейсов MFC.

- **Дополнительные атрибуты**

  Недоступно для disp-интерфейсов MFC.

  |Атрибут|ОПИСАНИЕ|
  |---------------|-----------------|
  |`hidden`|Указывает, что метод существует, но не должен отображаться в пользовательском браузере. Дополнительные сведения см. в разделе, посвященном атрибуту [hidden](/windows/win32/Midl/hidden), *справочника по MIDL*.|
  |`source`|Указывает, что член метода является источником событий. Дополнительные сведения см. в разделе, посвященном атрибуту [source](/windows/win32/Midl/source), *справочника по MIDL*.|
  |`local`|Указывает компилятору MIDL, что метод не является удаленным. Дополнительные сведения см. в разделе, посвященном атрибуту [local](/windows/win32/Midl/local), *справочника по MIDL*.|
  |`restricted`|Указывает, что метод не может вызываться произвольным образом. Дополнительные сведения см. в разделе, посвященном атрибуту [restricted](/windows/win32/Midl/restricted), *справочника по MIDL*.|
  |`vararg`|Указывает, что метод принимает переменное число аргументов. В этом случае последний аргумент должен быть безопасным массивом типа `VARIANT`, содержащим остальные аргументы. Дополнительные сведения см. в разделе, посвященном атрибуту [vararg](/windows/win32/Midl/vararg), *справочника по MIDL*.|
