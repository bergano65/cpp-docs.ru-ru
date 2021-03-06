---
title: Предупреждение компилятора C4368
ms.date: 11/04/2016
f1_keywords:
- C4368
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
ms.openlocfilehash: b1870d076d21c02574793a8079c4658b39ebf121
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623636"
---
# <a name="compiler-warning-c4368"></a>Предупреждение компилятора C4368

невозможно определить "member" как член управляемого "типа": смешанные типы не поддерживаются

Нельзя внедрить собственный элемент данных в тип CLR.

Однако можно объявить указатель на собственный тип и управлять его временем существования в конструкторе, деструкторе и методе завершения управляемого класса. Дополнительные сведения см. в разделе [деструкторы и методы завершения](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Это предупреждение всегда выдается как ошибка. Чтобы отключить C4368, используйте прагма pragma [warning](../../preprocessor/warning.md) .

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C4368.

```cpp
// C4368.cpp
// compile with: /clr /c
struct N {};
ref struct O {};
ref struct R {
    R() : m_p( new N ) {}
    ~R() { delete m_p; }

   property N prop;   // C4368
   int i[10];   // C4368

   property O ^ prop2;   // OK
   N * m_p;   // OK
};
```