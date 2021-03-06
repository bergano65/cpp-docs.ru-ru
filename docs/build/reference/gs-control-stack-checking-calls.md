---
title: /Gs (управлять вызовами проверки стека)
ms.date: 10/25/2018
f1_keywords:
- /GS
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
ms.openlocfilehash: e31b42c1d9422d44c5f106f40c4a60a38f23425b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270852"
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (управлять вызовами проверки стека)

Определяет пороговое значение для стековые зонды.

## <a name="syntax"></a>Синтаксис

> **/ GS**[*размер*]

## <a name="arguments"></a>Аргументы

*size*<br/>
(Необязательно) Число байтов, которое могут занимать локальные переменные перед инициацией стекового зонда. Не должно быть пробела между **/GS** и *размер*.

## <a name="remarks"></a>Примечания

Объект *стековый зонд* — это последовательность кода, который компилятор вставляет в начале вызова функции. При активации стекового зонда он занимает количество памяти, требуемое для хранения локальных переменных функции. Это вынуждает операционную систему для разбиения на страницы прозрачно в дополнительных стековой памяти при необходимости, до конца функции.

По умолчанию компилятор создает код, который активирует стековый зонд, если функции требуется более одной страницы стека. Это аналогично параметру компилятора **/Gs4096** для x86, x 64, ARM, ARM64 платформах и. Это значение позволяет приложению и диспетчеру памяти Windows динамически увеличивать количество памяти, выделенной стеку программы, во время выполнения.

> [!NOTE]
> Значение по умолчанию **/Gs4096** позволяет стеку программы приложений для Windows увеличиваться соответствующим образом во время выполнения. Мы рекомендуем не изменять значение по умолчанию, если вы не уверены, что это необходимо.

Некоторым программам, таким как драйверы виртуальных устройств, не требуется этот механизм увеличения стека по умолчанию. В таких случаях стековые зонды не обязательны, и вы можете остановить их создание, задав компилятором *размер* значение больше требуемого любой функции для хранения локальных переменных.

**/ Gs0** инициирует стека проб для каждого вызова функции, в которой требуется хранилище для локальных переменных. Это может отрицательно сказываться на производительности.

Для x64 предназначено, если **/GS** указан без *размер* аргумент, он является таким же, как **/Gs0**. Если *размер* аргумент — от 1 до 9, выдается предупреждение D9014, и действует аналогично указанию **/Gs0**.

Для x86, ARM, ARM64 целевые показатели и **/GS** параметр без *размер* аргумент совпадает со значением **/Gs4096**. Если *размер* аргумент — от 1 до 9, выдается предупреждение D9014, и действует аналогично указанию **/Gs4096**.

Для всех целей *размер* аргумент от 10 до 2147485647 Задает пороговое значение по указанному значению. Объект *размер* из 2147485648 или более поздней версии причины Неустранимая ошибка C1049.

Можно отключить стековые зонды можно включить или отключить с помощью [check_stack](../../preprocessor/check-stack.md) директива. **/ GS** и `check_stack` директива pragma не оказывают влияния на стандартные подпрограммы библиотеки C; они влияют только на компилируемые функции.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [свойств компилятора и собранной задать C++ в Visual Studio](../working-with-project-properties.md).

1. Выберите **свойства конфигурации** > **C/C++** > **командной строки** страницу свойств.

1. Введите **/GS** параметр компилятора и требуемый размер в **Дополнительные параметры**. Выберите **ОК** или **применить** для сохранения изменений.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>См. также

[Параметры компилятора MSVC](compiler-options.md)<br/>
[Синтаксис командной строки компилятора MSVC](compiler-command-line-syntax.md)
