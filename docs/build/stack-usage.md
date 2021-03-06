---
title: Использование стека для 64-разрядных систем
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: 902e4304ac124be46c6edf0860118dc522b34890
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422754"
---
# <a name="x64-stack-usage"></a>Использование стека для 64-разрядных систем

Вся память за пределами текущего адреса RSP считается временной: операционная система или отладчик могут перезаписывать эту память во время сеанса отладки пользователя или обработчика прерываний. Таким словами, RSP всегда должен быть задан перед попыткой чтения или записи значений в кадр стека.

В этом разделе обсуждается выделение пространства стека для локальных переменных и встроенной функции **выделения** .

## <a name="stack-allocation"></a>Выделение стека

Пролог функции отвечает за выделение пространства стека для локальных переменных, сохраненных регистров, параметров стека и параметров регистрации.

Область параметров всегда находится в нижней части стека (даже если используется `alloca`), поэтому она всегда будет находиться рядом с адресом возврата во время любого вызова функции. Он содержит не менее четырех записей, но достаточно места для хранения всех параметров, необходимых любой функции, которую можно вызвать. Обратите внимание, что пространство всегда выделяется для параметров регистра, даже если сами параметры никогда не находятся в стеке. Вызываемый объект гарантирует, что пространство было выделено для всех его параметров. Домашние адреса необходимы для аргументов регистров, чтобы смежная область была доступна в случае, если вызываемая функция должна получить адрес списка аргументов (va_list) или отдельного аргумента. Эта область также предоставляет удобное место для сохранения аргументов регистров во время выполнения преобразователя и как параметр отладки (например, позволяет упростить поиск аргументов во время отладки, если они хранятся на их домашних адресах в коде пролога). Даже если вызываемая функция имеет менее 4 параметров, эти 4 расположения стека фактически принадлежат вызываемой функции и могут использоваться вызванной функцией для других целей, кроме сохранения значений регистров параметров.  Поэтому вызывающий объект не может сохранять информацию в этом регионе стека через вызов функции.

Если в функции динамически выделяется пространство (`alloca`), то для обозначения базового элемента фиксированной части стека в качестве указателя фрейма должен использоваться неизменяемый регистр, который помечается в прологе и должен быть сохранен и инициализирован. Обратите внимание, что при использовании `alloca` вызовы одного и того же вызываемого из одного и того же вызывающего объекта могут иметь разные домашние адреса для своих параметров регистрации.

Стек всегда будет поддерживаться в 16-байтном виде, за исключением того, что в прологе (например, после отправки обратного адреса) и за исключением случаев, указанных в [типах функций](#function-types) для определенного класса функций для работы с кадрами.

Ниже приведен пример макета стека, в котором функция A вызывает неконечную функцию б. в конце стека функции A уже выделено место для всех параметров Register и Stack, необходимых для B. При вызове отправляются адрес возврата, а в прологе б выделяется место для локальных переменных, неизменяемых регистров и пространство, необходимое для вызова функций. Если в B используется `alloca`, пространство выделяется между областью сохранения локальной переменной или неизменяемой регистрации и областью стека параметров.

![Пример преобразования AMD](../build/media/vcamd_conv_ex_5.png "Пример преобразования AMD")

Когда функция б вызывает другую функцию, обратный адрес помещается непосредственно под домашним адресом для РККС.

## <a name="dynamic-parameter-stack-area-construction"></a>Динамическое создание области стека параметров

Если используется указатель фрейма, существует параметр для динамического создания области стека параметров. В настоящее время это не сделано в компиляторе x64.

## <a name="function-types"></a>Типы функций

Существует по сути два типа функций. Функция, которая требует кадр стека, называется *функцией Frame*. Функция, которая не требует кадр стека, называется *конечной функцией*.

Функция Frame — это функция, которая выделяет пространство стека, вызывает другие функции, сохраняет неизменяемые регистры или использует обработку исключений. Также требуется запись в таблице функций. Для функции Frame требуется Пролог и эпилога. Функция Frame может динамически распределять пространство стека и может использовать указатель фрейма. Функция Frame обладает всеми возможностями этого вызывающего стандарта при его реализации.

Если функция Frame не вызывает другую функцию, то не требуется выделять стек (ссылка в [стеке](#stack-allocation)разделов).

Конечная функция не требует наличия записи в таблице функций. Он не может вносить изменения в любые неизменяемые регистры, включая RSP, что означает, что он не может вызвать какие-либо функции или выделить пространство стека. Можно оставить стек без согласования во время выполнения.

## <a name="malloc-alignment"></a>Выравнивание malloc

[malloc](../c-runtime-library/reference/malloc.md) гарантированно возвращает память, которая соответствующим образом выровнена для хранения любого объекта, имеющего фундаментальное выравнивание, который может попадать в объем выделяемой памяти. *Фундаментальное выравнивание* — это выравнивание, которое меньше или равно значению самого крупного выравнивания, которое поддерживается реализацией без спецификации выравнивания. (В визуальном C++элементе это выравнивание, необходимое для `double`или 8 байт. В коде, ориентированном на 64-разрядные платформы, это 16 байт.) Например, выделение с четырьмя байтами будет выделено на границе, которая поддерживает любой объект с четырьмя или более мелкими байтами.

Визуальный C++ элемент разрешает типы с *расширенным выравниванием*, которые также называются *перевыровненными* типами. Например, типы SSE [__m128](../cpp/m128.md) и `__m256`, а также типы, объявленные с помощью `__declspec(align( n ))`, где `n` больше 8, имеют расширенное выравнивание. Выравнивание памяти на границе, подходящей для объекта, требующего расширенного выравнивания, не гарантируется `malloc`. Чтобы выделить память для перераспределенных типов, используйте [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) и связанные функции.

## <a name="alloca"></a>alloca

для [_alloca](../c-runtime-library/reference/alloca.md) требуется выровняйте по 16 байт, а также для использования указателя фрейма.

Выделенный стек должен содержать пробел после него для параметров последовательного вызова функций, как описано в разделе [выделение стека](#stack-allocation).

## <a name="see-also"></a>См. также раздел

[Программные соглашения для 64-разрядных систем](../build/x64-software-conventions.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)
