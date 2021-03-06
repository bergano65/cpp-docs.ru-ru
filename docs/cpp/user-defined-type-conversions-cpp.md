---
title: Заданные пользователем преобразования типов (C++)
ms.date: 11/04/2016
f1_keywords:
- explicit_cpp
helpviewer_keywords:
- constructors [C++], and constants
- conversion functions [C++]
- explicit keyword [C++]
- type conversion
- constructors [C++], drawbacks
- conversion constructors
- type conversion [C++], explicit conversion
- coercion [C++]
- conversions [C++], explicit
- objects [C++], converting
- conversion functions [C++], rules for declaring
- declaring functions [C++], conversion functions
- functions [C++], conversion
- converting objects
- constructors [C++], conversion
- conversions [C++], by constructors
- data type conversion [C++], explicit
ms.assetid: d40e4310-a190-4e95-a34c-22c5c20aa0b9
ms.openlocfilehash: 2af30ad3d1244146f32bf2402ed7eccdc4785c1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244140"
---
# <a name="user-defined-type-conversions-c"></a>Заданные пользователем преобразования типов (C++)

Объект *преобразования* создает новое значение некоторого типа из значения другого типа. *Стандартные преобразования* встроены в языке C++ и поддерживают его встроенные типы и вы можете создать *заданные пользователем преобразования* для выполнения преобразований, из или между пользовательскими типами.

Стандартные преобразования выполняют преобразование между встроенными типами, между указателями или ссылками на типы, связанные наследованием, в и из указателей void и в пустой указатель. Дополнительные сведения см. в разделе [стандартные преобразования](../cpp/standard-conversions.md). Пользовательские преобразования выполняют преобразование между пользовательскими типами или между пользовательскими и встроенными типами. Вы можете реализовать их в виде [конструкторы преобразования](#ConvCTOR) или как [функции преобразования](#ConvFunc).

Преобразования могут быть явными, когда программист вызывает преобразование одного типа в другой (как в приведении или прямой инициализации) или неявными, когда язык или программа вызывают типы, которые отличаются от заданных программистом.

Попытка неявного преобразования выполняется, когда

- тип аргумента, предоставленного для функции, не совпадает с соответствующим параметром;

- тип значения, возвращаемого функцией, не совпадает с типом возвращаемого значения функции;

- тип выражения инициализатора не совпадает с типом инициализируемого объекта;

- тип результата выражения, которое управляет условным оператором, циклической конструкцией или параметром, не совпадает с тем, который требуется для управления;

- тип операнда, предоставленного для оператора, не совпадает с соответствующим параметром операнда. Для встроенных операторов тип обоих операндов должен совпадать; он преобразуется в общий тип, который может представлять оба операнда. Дополнительные сведения см. в разделе [стандартные преобразования](standard-conversions.md). Для пользовательских операторов тип каждого операнда должен совпадать с соответствующим параметром операнда.

Если не удается выполнить неявное преобразование с помощью стандартного преобразования, компилятор может использовать пользовательское преобразование, за которым (при необходимости) будет следовать дополнительное стандартное преобразование.

Если на сайте преобразования есть два и более пользовательских преобразования, выполняющих одно преобразование, преобразование называется неоднозначным. Неоднозначность подразумевает ошибку, так как компилятор не может определить, какое из доступных преобразований выбрать. Тем не менее, не будет ошибкой определить несколько способов выполнения одного преобразования, так как набор доступных преобразований может отличаться в разных участках исходного кода, например в зависимости от того, какие файлы заголовков входят в исходный файл. Пока на сайте преобразования доступно только одно преобразование, о неоднозначности речь не идет. Существует несколько путей возникновения неоднозначных преобразований, однако самые распространенные перечислены ниже.

- Множественное наследование. Преобразование определено в нескольких базовых классах.

- Вызов неоднозначной функции. Преобразование определено как конструктор преобразования типа целевого объекта и как функция преобразования типа источника. Дополнительные сведения см. в разделе [функции преобразования](#ConvFunc).

Неоднозначность, как правило, можно устранить, просто более полно указав имя соответствующего типа или выполнив явное приведение для пояснения намерения.

Конструкторы преобразования и функции преобразования подчиняются правилам управления доступом членов, однако доступность преобразований учитывается, только если можно определить неоднозначное преобразование. Это означает, что преобразование может быть неоднозначным, даже если уровень доступа конкурирующего преобразования будет блокировать его использование. Дополнительные сведения о доступности членов см. в разделе [управление доступом к членам](../cpp/member-access-control-cpp.md).

## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>Ключевое слово explicit и проблемы с неявным преобразованием

По умолчанию при создании пользовательского преобразования компилятор может использовать его для выполнения неявных преобразований. Иногда это совпадает с вашими намерениями, но в других случаях простые правила, которые определяют выполнение неявных преобразований компилятором, могут привести к тому, что он примет нежелательный код.

Одним из хорошо известных примеров неявное преобразование, которое может вызвать проблемы является преобразование в **bool**. Есть много причин, которые может потребоваться создать тип класса, который может использоваться в логическом контексте — например, так что он может использоваться для управления **Если** инструкции или цикла — но когда компилятор выполняет пользовательское преобразование в встроенный тип, компилятор может применить дополнительное стандартное преобразование позже. Цель этого дополнительного преобразования состоит в том, чтобы разрешить для реализация таких возможностей, **короткий** для **int**, но он также открывает для менее очевидных преобразований — например, из  **bool** для **int**, что позволяет тип класса для использования в контексте целых значений, которые не предназначены. Эта конкретная проблема известна как *проблеме Safe Bool*. Проблемы такого рода именно **явные** может помочь ключевое слово.

**Явные** ключевое слово указывает компилятору, что указанное преобразование не может использоваться для выполнения неявных преобразований. Если вы хотели воспользоваться неявных преобразований до **явные** слова, необходимо было принять непредвиденные последствия, неявное преобразование, которое иногда создан или использовать менее удобную, с именем функции преобразования в качестве обходного решения. Теперь, с помощью **явные** ключевое слово, можно создавать удобные преобразования, который может использоваться только для выполнения явного приведения или прямой инициализации, и, не приведет к возникновения проблем, например, проблема Safe Bool.

**Явные** ключевое слово может применяться к конструкторам преобразования с версии C ++ 98 и к функциям преобразования с версии C ++ 11. В следующих разделах содержатся дополнительные сведения об использовании **явные** ключевое слово.

## <a name="ConvCTOR"></a> Конструкторы преобразований

Конструкторы преобразования определяют преобразование из пользовательских или встроенных типов в пользовательские типы. В следующем примере демонстрируется конструктор преобразования, который преобразует встроенный тип **двойные** для определяемого пользователем типа `Money`.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance.amount << std::endl;
}

int main(int argc, char* argv[])
{
    Money payable{ 79.99 };

    display_balance(payable);
    display_balance(49.95);
    display_balance(9.99f);

    return 0;
}
```

Обратите внимание, что первый вызов функции `display_balance`, которая принимает аргументы типа `Money`, не требует преобразования, так как аргумент принадлежит к правильному типу. Однако при втором вызове `display_balance`, преобразование требуется, так как тип аргумента, **двойные** со значением `49.95`, — не ожидаемому функцией. Функция не может использовать это значение напрямую, однако поскольку выполняется преобразование из типа аргумента —**двойные**— к типу соответствующего параметра —`Money`— временное значение типа `Money` создан на основе аргумент и используется для завершения вызова функции. В третьем вызове `display_balance`, обратите внимание, что аргумент не **двойные**, а вместо этого является **float** со значением `9.99`— и еще вызова функции можно по-прежнему выполнить, так как компилятор может выполнить стандартное преобразование — в этом случае из **float** для **двойные**— и затем выполнить определенное пользователем преобразование из **двойные** для `Money` выполнить необходимые преобразования.

### <a name="declaring-conversion-constructors"></a>Объявление конструкторов преобразования

Следующие правила применяются к объявлению конструктора преобразования.

- Целевым типом преобразования является сконструированный пользовательский тип.

- Конструкторы преобразований, как правило, принимают только один аргумент типа источника. Однако конструктор преобразования может указывать дополнительные параметры, если у каждого из них есть значение по умолчанию. Тип источника остается типом первого параметра.

- Конструкторы преобразований, как и все конструкторы, не указывают тип возвращаемого значения. Указание типа возвращаемого значения в объявлении является ошибкой.

- Конструкторы преобразования могут быть явными.

### <a name="explicit-conversion-constructors"></a>Явные конструкторы преобразования

Путем объявления конструктора преобразования как **явные**, он может использоваться только для выполнения прямой инициализации объекта или явного приведения. Это не дает функциям, которые принимают аргумент типа класса, также неявно принимать аргументы типа источника конструктора преобразования, а также блокирует инициализацию копирования типа класса из значения типа источника. В следующем примере демонстрируется определение явного конструктора преобразования и влияние на правильный синтаксис кода.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    explicit Money(double _amount) : amount{ _amount } {};

    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance.amount << std::endl;
}

int main(int argc, char* argv[])
{
    Money payable{ 79.99 };        // Legal: direct initialization is explicit.

    display_balance(payable);      // Legal: no conversion required
    display_balance(49.95);        // Error: no suitable conversion exists to convert from double to Money.
    display_balance((Money)9.99f); // Legal: explicit cast to Money

    return 0;
}
```

В этом примере обратите внимание, что явный конструктор преобразования можно использовать для выполнения прямой инициализации типа `payable`. Если же вы попытаетесь выполнить инициализацию копирования `Money payable = 79.99;`, это приведет к ошибке. Первый вызов `display_balance` не включает преобразование, так как указан аргумент правильного типа. Второй вызов `display_balance` является ошибкой, так как конструктор преобразования нельзя использовать для выполнения неявного преобразования. Третий вызов `display_balance` допустим, так как явное приведение к `Money`, но Обратите внимание, что компилятор по-прежнему помогло выполнить приведение, вставив неявное приведение из **float** для **двойной**.

Несмотря на то, что использование неявных преобразований кажется удобным, в результате могут возникать трудновыявляемые ошибки. Как показывает опыт, лучше всего объявлять все конструкторы преобразований явными за исключением тех случаев, когда необходимо, чтобы определенное преобразование выполнялось неявно.

##  <a name="ConvFunc"></a> Функции преобразования

Функции преобразования определяют преобразования из пользовательского в другие типы. Эти функции иногда называют "операторами приведения", так как они, наряду с конструкторами преобразования, вызываются, когда значение приводится к другому типу. В следующем примере демонстрируется функция преобразования, который преобразует пользовательский тип, `Money`, во встроенный тип **double**:

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    operator double() const { return amount; }
private:
    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance << std::endl;
}
```

Обратите внимание, что переменная-член `amount` private и что открытая функция преобразования в тип **двойные** добавлена только для возврата значения `amount`. В функции `display_balance` неявное преобразование возникает, когда значение `balance` направляется в стандартный вывод с помощью оператора вставки в поток `<<`. Поскольку оператор вставки в поток не был определен для определяемого пользователем типа `Money`, но имеется еще один для встроенного типа **двойные**, компилятор может использовать функцию преобразования `Money` для **двойной** для удовлетворения оператор вставки в поток.

Функции преобразования наследуются производными классами. Функции преобразования в производном классе переопределяют наследуемую функцию преобразования, только когда выполняют преобразование в точно такой же тип. Например, функция пользовательского преобразования производного класса **int оператор** не переопределяет — или даже вообще не влияет — определенное пользователем преобразование функции базового класса **оператор короткий**, даже Хотя стандартное преобразование определяет отношение преобразования между **int** и **короткие**.

### <a name="declaring-conversion-functions"></a>Объявление функций преобразования

Следующие правила применяются к объявлению функции преобразования.

- Целевой тип преобразования должен быть объявлен до объявления функции преобразования. Классы, структуры, перечисления и определения типа нельзя объявлять в объявлении функции преобразования.

    ```cpp
    operator struct String { char string_storage; }() // illegal
    ```

- Функции преобразования не принимают аргументов. Указание любых параметров в объявлении является ошибкой.

- Функции преобразования имеют тип возвращаемого значения, задаваемый именем функции преобразования, которое также является именем типа целевого объекта преобразования. Указание типа возвращаемого значения в объявлении является ошибкой.

- Функции преобразования могут быть виртуальными.

- Функции преобразования могут быть явными.

### <a name="explicit-conversion-functions"></a>Явные функции преобразования

Если функция преобразования объявлена как явная, ее можно использовать только для выполнения явного приведения. Это не дает функциям, которые принимают аргумент типа целевого объекта функции преобразования, также неявно принимать аргументы типа класса, а также блокирует инициализацию копирования экземпляров типа целевого объекта из значения типа класса. В следующем примере демонстрируется определение явной функции преобразования и влияние на правильный синтаксис кода.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    explicit operator double() const { return amount; }
private:
    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << (double)balance << std::endl;
}
```

Здесь функцию преобразования **double-оператор** была объявлена явной, а явное приведение к типу **двойные** был введен в функции `display_balance` для выполнения преобразования. Если пропустить это преобразование, компилятор не сможет найти подходящий оператор вставки в поток `<<` для типа `Money` и может возникнуть ошибка.