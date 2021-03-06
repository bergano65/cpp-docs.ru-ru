---
title: Оператор return (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: 47bf9c50a2da039b0ffa074796a768290b732bb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268542"
---
# <a name="return-statement-c"></a>Оператор return (C++)

Завершает выполнение функции и возвращает элемент управления в вызывающую функцию (или в операционную систему при передаче управления из функции `main`). Выполнение возобновляется в вызывающей функции в точке сразу после вызова.

## <a name="syntax"></a>Синтаксис

```
return [expression];
```

## <a name="remarks"></a>Примечания

Предложение `expression`, при его наличии, преобразуется в тип, указанный в объявлении функции, как если бы выполнялась инициализация. Преобразование из типа выражения **возвращают** тип функции может создавать временные объекты. Дополнительные сведения о том, как и когда создания временных объектов, см. в разделе [временные объекты](../cpp/temporary-objects.md).

Значение предложения `expression` возвращается в вызывающую функцию. Если выражение пропущено, то возвращаемое значение функции не определено. Конструкторы и деструкторы и функции типа **void**, нельзя указать выражение в **возвращают** инструкции. Функции всех других типов необходимо указать выражение в **возвращают** инструкции.

Когда поток элемента управления выходит из блока, включающего определение функции, результат одинаков как бы Если **возвращают** бы был выполнен оператор без выражения. Это недопустимо для функций, объявленных как возвращающие значение.

Функция может иметь любое количество **возвращают** инструкций.

В следующем примере используется выражение с **возвращают** инструкции для получения наибольшего из двух целых чисел.

## <a name="example"></a>Пример

```cpp
// return_statement2.cpp
#include <stdio.h>

int max ( int a, int b )
{
   return ( a > b ? a : b );
}

int main()
{
    int nOne = 5;
    int nTwo = 7;

    printf_s("\n%d is bigger\n", max( nOne, nTwo ));
}
```

## <a name="see-also"></a>См. также

[Операторы перехода](../cpp/jump-statements-cpp.md)<br/>
[Ключевые слова](../cpp/keywords-cpp.md)