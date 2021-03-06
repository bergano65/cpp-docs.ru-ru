---
title: Проблемы при миграции с плавающей запятой
ms.date: 05/17/2017
ms.assetid: 36a1b552-2f2b-4919-bc9d-c17f42434954
ms.openlocfilehash: 0a84b764d395063f38cae299cff75437318b024e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626978"
---
# <a name="floating-point-migration-issues"></a>Проблемы при миграции с плавающей запятой

Иногда при обновлении проектов до более новой версии Visual Studio, может оказаться, что были изменены результаты отдельных операций с плавающей запятой. Обычно это происходит по одной из двух причин: изменения создания кода, когда более эффективно используются доступные ресурсы процессора, и исправления ошибок или изменения в алгоритмах, используемых в математических функциях в библиотеке среды выполнения C (CRT). Как правило, новые результаты верны в рамках ограничений, установленных языковым стандартом. Ознакомьтесь с изменениями и, если для вас это важно, узнайте, как получать прежние результаты.

## <a name="new-math-functions-and-universal-crt-changes"></a>Новые математические функции и изменения в универсальной CRT

Большая часть математических функций CRT была доступна в Visual Studio в течение многих лет, но начиная с Visual Studio 2013, добавляются все функции, необходимые согласно стандарту ISO C99. Эти функции предназначены для балансировки производительности и правильности. Так как получение правильно округленного результата в каждом случае может оказаться неоправданно дорогим, эти функции позволяют получить значение, максимально приближенное к правильно округленному результату. В большинстве случаев результат будет соответствовать правильно округленному значению +/-1 *ulp*, хотя в некоторых случаях погрешность может быть выше. Если для получения этих функций вы раньше использовали другую математическую библиотеку, возможно, изменение в результатах связано с различиями в реализации.

Когда математические функции были перемещены в универсальную CRT в Visual Studio 2015, использовались некоторые новые алгоритмы и был исправлен ряд ошибок в реализации функций, впервые появившихся в Visual Studio 2013. Эти изменения могут привести к заметным отличиям в результатах вычислений с плавающей запятой, где используются эти функции. Ошибки возникали в функциях erf, exp2, remainder, remquo, scalbln и scalbn и их вариантах float и long double.  Другие изменения в Visual Studio 2015 привели к устранению проблем с сохранением слова, обозначающего статус плавающей запятой, и сведений о состоянии исключения в функциях _clear87, _clearfp, fegetenv, fesetenv и feholdexcept.

## <a name="processor-differences-and-compiler-flags"></a>Различия процессоров и флаги компилятора

Во многих функциях математической библиотеки с плавающей точкой используются различные реализации разной архитектуры ЦП. Например, в 32-разрядных CRT x86 могут использоваться не такие реализации, как в 64-разрядных CRT x64. Кроме того, некоторые функции могут содержать сразу несколько реализаций заданной архитектуры ЦП. Наиболее эффективная реализация выбирается в среде выполнения динамически в зависимости от того, какие наборы инструкций поддерживает ЦП. Например, в 32-разрядных CRT x86 некоторые функции включают сразу две реализации — x87 и SSE2. При работе на ЦП, который поддерживает SSE2, используется более быстрая реализация SSE2. При работе на ЦП, который не поддерживает SSE2, используется более медленная реализация x87. Это можно заметить при миграции старого кода, так как заданный по умолчанию параметр архитектуры компилятора x86 изменен на [/arch:SSE2](../build/reference/arch-x86.md) в Visual Studio 2012. Так как различные реализации функций математической библиотеки могут использовать для получения результатов различные инструкции ЦП и разнообразные алгоритмы, эти функции могут давать различные результаты на разных платформах. В большинстве случаев результаты находятся в пределах +/–1 ULP от правильно округленного результата, но фактические результаты могут отличаться в зависимости от ЦП.

Усовершенствования правильности создания кода в различных режимах с плавающей запятой в Visual Studio также могут повлиять на результаты операций с плавающей запятой при сравнении старого кода с новым даже при использовании тех же флагов компилятора. Например, код, созданный в Visual Studio 2010 с указанием [/fp:precise](../build/reference/fp-specify-floating-point-behavior.md) (по умолчанию) или `/fp:strict`, мог неправильно распространять промежуточные не являющиеся числами значения (NaN) значений с помощью выражений. Таким образом, некоторые выражения, которые выдавали числовой результат в старых компиляторах, теперь могут правильно давать результат NaN. Кроме того, различия существуют в связи с тем, что для оптимизаций кода, включенных для `/fp:fast`, теперь доступны дополнительные функции процессора. Эти оптимизации могут использовать меньше инструкций, но не исключают влияние на полученные результаты, так как были удалены некоторые ранее видимые промежуточные операции.

## <a name="how-to-get-identical-results"></a>Получение одинаковых результатов

В большинстве случаев изменения операций с плавающей запятой в новейших компиляторах и библиотеках приводят к более быстрому и правильному выполнению действий. При замене инструкций x87 на инструкции SSE2 наблюдается повышение производительности процессора. Но если у вас есть код, который должен точно реплицировать поведение вычислений с плавающей запятой в более старой версии компилятора, рассмотрите возможность использования собственного многоплатформенного нацеливания в Visual Studio и сборки затронутых проектов с помощью старого набора инструментов. Дополнительные сведения см. в разделе [Использование собственного многоплатформенного нацеливания в Visual Studio для сборки старых проектов](use-native-multi-targeting.md).

## <a name="see-also"></a>См. также

[Обновление проектов с более ранних версий VisualC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Общие сведения о возможных проблемах, возникающих при обновлении (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Журнал изменений Visual C++ 2003–2015](visual-cpp-change-history-2003-2015.md)