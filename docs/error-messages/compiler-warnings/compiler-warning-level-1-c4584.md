---
title: Предупреждение компилятора (уровень 1) C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: 831789f5295fcf91e83de3bd0bba12c8429e9fa3
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966233"
---
# <a name="compiler-warning-level-1-c4584"></a>Предупреждение компилятора (уровень 1) C4584

"Class1": базовый класс "class2" уже является базовым классом для "Class3"

Определенный класс наследуется от двух классов, один из которых наследует от другого. Пример:

```cpp
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

В этом случае в классе C будет выдано предупреждение, так как он наследует как от класса A, так и от класса B, который также наследует от класса а. Это предупреждение служит в качестве напоминания о том, что необходимо полностью определить использование членов из этих базовых классов, иначе будет сформирована ошибка компилятора из-за неоднозначности в отношении того, на какой член класса вы ссылаетесь.