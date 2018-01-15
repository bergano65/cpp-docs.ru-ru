---
title: "C2672 Ошибка компилятора | Документы Microsoft"
ms.date: 10/24/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords: C2672
dev_langs: C++
helpviewer_keywords: C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52663aed470aff254d07cba6a65f484269d8703d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2672"></a>C2672 ошибки компилятора

> "*функция*": нет соответствующего перегруженная функция найдена

Компилятору не удалось найти перегруженной функции, соответствующий указанной функции. Не была найдена функция наличие берет соответствующие параметры или ни одна из функций сопоставления необходимые специальные возможности в контексте.

При использовании определенных контейнеры стандартной библиотеки или алгоритмы, к типам необходимо предоставить доступные члены и дружественные функции, которые удовлетворяют требованиям контейнера или алгоритм. Например, типы итератора должен быть производным от `std::iterator<>`. Операции сравнения или использование других операторов на типом элемента контейнера, могут требоваться тип рассматриваться как левый и правый операнд. Использование типа как правый операнд может потребоваться реализация оператора как функцию не члена типа.

## <a name="example"></a>Пример

Версии компилятора до 2017 г. Visual Studio не удалось выполнить проверки на полных имен в некоторых контекстах шаблонов доступа. Это может помешать ожидаемой работе SFINAE там, где подстановка должна завершиться ошибкой из-за отсутствия доступа к имени. Такая ситуация может приводить к сбою или неожиданному поведению во время выполнения из-за того, что компилятор неправильно вызывает неверную перегрузку оператора. В Visual Studio 2017 выводится ошибка компилятора.

В этом примере компилировался в Visual Studio 2015, но вызывает ошибку в Visual Studio 2017 г. Чтобы устранить эту проблему, сделайте элемент параметра шаблона, доступного месте вычисления.

```cpp
#include <type_traits>

template <class T> class S {
// public:    // Uncomment this line to fix
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x)
{
    return (x == 0);
}

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```