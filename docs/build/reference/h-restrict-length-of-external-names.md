---
title: /H (ограничение длины внешних имен)
ms.date: 09/05/2018
f1_keywords:
- /h
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
ms.openlocfilehash: bdd3da8d3a5165262c00bc3475122e31f5770726
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270397"
---
# <a name="h-restrict-length-of-external-names"></a>/H (ограничение длины внешних имен)

Не рекомендуется. Ограничивает длину внешних имен.

## <a name="syntax"></a>Синтаксис

> **/H**<em>номер</em>

## <a name="arguments"></a>Аргументы

*номер*<br/>
Указывает максимальную длину внешних имен, допустимую в программе.

## <a name="remarks"></a>Примечания

По умолчанию длину внешних (открытых) имен является 2 047 символов. Это справедливо для программ C и C++. С помощью **/H** можно только уменьшить максимально допустимая длина идентификаторов, не увеличить его. Пробел между **/H** и *номер* является необязательным.

Если программа содержит внешние имена, превышающие *номер*, лишние символы игнорируются. При компиляции программы без **/H** и идентификатор содержит более 2 047 символов, компилятор выдаст [Неустранимая ошибка C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md).

Это ограничение на длину включает любого символа подчеркивания, создать компилятор (**\_**) или знак (**\@**). Эти символы являются частью идентификатора и занимают значительное место.

- Компилятор добавляет подчеркивания (**\_**) к именам, измененным `__cdecl` (по умолчанию) и `__stdcall` соглашения о вызовах и ведущий знак (**\@** ) для изменения имен `__fastcall` соглашение о вызовах.

- Компилятор добавляет сведения о размере аргумента к именам, измененным `__fastcall` и `__stdcall` соглашения о вызовах и добавляет сведения о типе имен C++.

Возможно, вам **/H** полезно:

- При создании смешанного портативных программ или программ.

- При использовании средства, которые накладывают ограничения на длину внешних идентификаторов.

- Если вы хотите ограничить объем пространства, занимаемого символами в отладочном построении.

В следующем примере показан как с помощью **/H** может внести ошибки, если длины идентификаторов слишком сильно ограничены:

```cpp
// compiler_option_H.cpp
// compile with: /H5
// processor: x86
// LNK2005 expected
void func1(void);
void func2(void);

int main() { func1(); }

void func1(void) {}
void func2(void) {}
```

Также следует соблюдать осторожность при использовании **/H** параметр предварительно определенных идентификаторов компилятора. Если максимальная длина идентификатора слишком мал, некоторые идентификаторы будет библиотека неразрешенных, а также определенные вызовы функций. Например если `printf` используется функция и параметр **/H5** указывается во время компиляции, символ **_prin** будет создан, чтобы ссылаться на `printf`, и это не будет найдена в библиотеке.

Использование **/H** несовместим с [/GL (оптимизация всей программы)](gl-whole-program-optimization.md).

**/H** параметр является устаревшим начиная с Visual Studio 2005; было увеличено максимальные пределы длины и **/H** больше не используется. Список параметров компилятора, см. в разделе **нерекомендуемые и удаленные параметры компилятора** в [параметры компилятора, упорядоченные по категориям](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [свойств компилятора и собранной задать C++ в Visual Studio](../working-with-project-properties.md).

1. Выберите **свойства конфигурации** > **C/C++** > **командной строки** страницу свойств.

1. Введите параметр компилятора в **Дополнительные параметры** поле.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>См. также

[Параметры компилятора MSVC](compiler-options.md)<br/>
[Синтаксис командной строки компилятора MSVC](compiler-command-line-syntax.md)
