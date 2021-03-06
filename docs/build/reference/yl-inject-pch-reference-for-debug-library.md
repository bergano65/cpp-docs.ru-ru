---
title: Параметр /Yl (вставка ссылки на PCH-файл для библиотеки отладки)
ms.date: 01/29/2018
f1_keywords:
- /yl
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
ms.openlocfilehash: 92e47836e0fdae077defa0fe35b515ab4ca20a66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316253"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>Параметр /Yl (вставка ссылки на PCH-файл для библиотеки отладки)

**/Yl** создает уникальный символ в файл предкомпилированного заголовка и ссылку на этот символ вставляется во всех объектных файлах, использующих предкомпилированного заголовка.

## <a name="syntax"></a>Синтаксис

>**/Yl**
> **/Yl**_имя_
> **/Yl-**

### <a name="arguments"></a>Аргументы

*name*<br/>
Необязательное имя используется как часть уникальный символ.

*\-*<br/>
Явно отменяет дефисом (-) **/Yl** параметр компилятора.

## <a name="remarks"></a>Примечания

**/Yl** параметр компилятора создает определение уникальных символов в файл предкомпилированного заголовка, созданные с помощью [/Yc](yc-create-precompiled-header-file.md) параметр. Во всех файлах, которые включают предкомпилированного заголовка с помощью автоматически добавляются ссылки на этот символ [/Yu](yu-use-precompiled-header-file.md) параметр компилятора. **/Yl** параметр включен по умолчанию при **/Yc** используется для создания файла предкомпилированного заголовка.

**/Yl**_имя_ параметр используется для создания символ характера в предкомпилированного файла заголовка. Компилятор использует *имя* аргумент в составе декорированного имени, он создает, аналогичную `__@@_PchSym_@00@...@name`, где строка символов представляет кнопку с многоточием (...), уникальный компилятором. Если *имя* аргумент указан, компилятор автоматически создает имя символа. Как правило не нужно знать имя символа. Тем не менее, в том случае, если проект использует более одного файла предкомпилированного заголовка, **/Yl**_имя_ можно использовать определить, какой объект файлы использовать предварительно скомпилированные заголовки. Можно использовать *имя* как строку поиска, чтобы найти ссылки на символ в файле дампа.

**/Yl-** отключает поведение по умолчанию и не стоит символ идентифицирующий в предкомпилированного файла заголовка. Справочник по общим символ получали только скомпилированные файлы, которые включают предкомпилированного заголовка.

При **/Yc** не задан, любой **/Yl** параметр не оказывает влияния, но если указан, должны соответствовать любые **/Yl** параметр переданного, когда **/Yc** — указан.

Если вы используете **/Yl-**, **/Yc** и [/Z7](z7-zi-zi-debug-information-format.md) параметры для построения файла предкомпилированного заголовка, отладочная информация хранится в файле объекта для исходного файла, используемый для создания предкомпилированный заголовок, а не отдельные PDB-файл. Если этот файл объекта становятся частью библиотеки, [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) ошибки или [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) предупреждения могут возникнуть в сборки, использующие эту библиотеку и предкомпилированного файла заголовка, если исходный файл создан файл предкомпилированного заголовка определялась любых символов. Компоновщик может исключить объектный файл по ссылке, а также связанные параметры отладки, когда ничего в объектном файле упоминается в клиенте библиотеки. Чтобы решить эту проблему, укажите **/Yl** (или удалить **/Yl-** параметра) при использовании **/Yc** создаваемого предкомпилированного файла заголовка. Это гарантирует, что объектный файл из библиотеки, который содержит отладочную информацию связывается в сборке.

Дополнительные сведения о предкомпилированных заголовках см. в разделе:

- [/Y (предкомпилированные заголовки)](y-precompiled-headers.md)

- [Файлы предварительно скомпилированных заголовков](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [свойств компилятора и собранной задать C++ в Visual Studio](../working-with-project-properties.md).

1. Выберите **свойства конфигурации** > **C/C++** > **командной строки** страницу свойств.

1. Добавить **/Yl**_имя_ параметр компилятора в **Дополнительные параметры** поле. Выберите **ОК** для сохранения внесенных изменений.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>См. также

[Параметры компилятора MSVC](compiler-options.md)<br/>
[Синтаксис командной строки компилятора MSVC](compiler-command-line-syntax.md)
