---
title: Работа с потоками и маршалинг (C++/CX)
ms.date: 12/30/2016
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
ms.openlocfilehash: 05601367b6907e34d9d67364d35988a37ceae40c
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741126"
---
# <a name="threading-and-marshaling-ccx"></a>Работа с потоками и маршалинг (C++/CX)

В подавляющем большинстве случаев экземпляры среда выполнения Windows классов, такие как стандартные C++ объекты, могут быть доступны из любого потока. Такие классы называются "гибкими". Однако небольшое количество среда выполнения Windows классов, поставляемых с Windows, не является гибким, и их необходимо использовать больше, как объекты COM, чем стандартные C++ объекты. Для работы с негибкими классами не нужно быть специалистом по COM, однако нужно учитывать модель потоков классов и их механизмы маршалинга. В этой статье приведены общие сведения и инструкции по реализации редких сценариев, в которых приходится использовать экземпляры негибких классов.

## <a name="threading-model-and-marshaling-behavior"></a>Модель потоков и механизмы маршалинга

Класс среда выполнения Windows может поддерживать параллельный доступ к потокам различными способами, как указано двумя атрибутами, которые применяются к нему:

- Атрибут`ThreadingModel` может иметь одно из следующих значений: STA, MTA или Both, которые определены в перечислении `ThreadingModel` .

- Атрибут`MarshallingBehavior` может иметь одно из следующих значений: Agile, None или Standard, которые определены в перечислении `MarshallingType` .

Атрибут `ThreadingModel` определяет, где загружается класс при активации: только в контексте потока пользовательского интерфейса (STA), только в контексте фонового потока (MTA) или в контексте потока, создающего объект (Both). Значения атрибутов `MarshallingBehavior` определяют поведение объекта в контекстах различных потоков; в большинстве случаев не требуется подробно разбираться в этих значениях.  Среди классов, предоставляемых API Windows, около 90 процентов имеют значения атрибутов `ThreadingModel`=Both и `MarshallingType`=Agile. Это означает, что они могут обрабатывать низкоуровневые сведения потоков прозрачно и эффективно.   Если создать гибкий класс с помощью ключевого слова `ref new` , его методы можно из основного потока приложения или из одного или нескольких рабочих потоков.  Иначе говоря, гибкий класс можно использовать из любого места в коде, независимо от того, предоставляется ли он Windows или сторонними разработчиками. О потоковой модели класса и его поведении маршалинга можно не беспокоиться.

## <a name="consuming-windows-runtime-components"></a>Использование компонентов среда выполнения Windows

При создании универсальная платформа Windows приложения вы можете взаимодействовать с гибкими и негибкими компонентами. При работе с негибкими компонентами может возникнуть следующее предупреждение.

### <a name="compiler-warning-c4451-when-consuming-non-agile-classes"></a>Предупреждение компилятора C4451 при использовании негибких классов

По различным причинам некоторые классы не могут быть гибкими. Если вы обращаетесь к экземплярам негибких классов и из потока пользовательского интерфейса, и из фонового потока, необходимо уделить особое внимание тому, чтобы обеспечить правильное поведение во время выполнения. Компилятор Майкрософт C++ выдает предупреждения при создании экземпляра негибкого класса времени выполнения в глобальной области или при объявлении негибкого типа как члена класса в классе ссылки, который сам помечен как гибкий.

Из негибких классов проще всего работать с теми, у которых `ThreadingModel`=Both и `MarshallingType`=Standard.  Эти классы можно сделать гибкими с помощью вспомогательного класса `Agile<T>` .   В следующем примере показано объявление негибкого объекта типа `Windows::Security::Credentials::UI::CredentialPickerOptions^`и результирующее предупреждение компилятора.

```

ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return _myOptions;
            }
        }
    private:
        Windows::Security::Credentials::UI::CredentialPickerOptions^ _myOptions;
    };
```

Выдается следующее предупреждение:

> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`

При добавлении ссылки — в области члена или глобальной области, в объект, имеющий поведение маршалинга "Standard", компилятор выдает предупреждение о том, что тип можно заключить в `Platform::Agile<T>`: `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`При использовании вы `Agile<T>`можете использовать класс, как и любой другой гибкий класс. Используйте `Platform::Agile<T>` в следующих ситуациях:

- Негибкая переменная объявляется в глобальной области.

- Негибкая переменная объявляется в области класса, и существует возможность того, что код использует указатель в другом подразделении без надлежащего маршалинга.

Если ни одно из этих условий не выполняется, можно пометить содержащий класс как негибкий. Иными словами, следует напрямую хранить негибкие объекты только в классах, не являющихся гибкими, и хранить негибкие объекты с помощью Platform:: Agile\<T > в классах Agile.

В следующем примере показано, как благодаря `Agile<T>` можно пропустить это предупреждение без последствий.

```

#include <agile.h>
ref class MyOptions
    {
    public:
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options

        {
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()
            {
                return m_myOptions.Get();
            }
        }
    private:
        Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions^> m_myOptions;

    };
```

Обратите внимание, что `Agile` нельзя передавать в качестве возвращаемого значения или параметра в классе ссылки. Метод `Agile<T>::Get()` возвращает дескриптор объекта (^), который можно передать через границу интерфейса ABI в открытом методе или свойстве.

При создании ссылки на внутрипроцессный среда выполнения Windows класс, имеющий поведение маршалинга "None", компилятор выдает предупреждение C4451, но не предлагает использовать `Platform::Agile<T>`.  Компилятор не может ничем помочь помимо этого предупреждения, поэтому вам необходимо самостоятельно обеспечить надлежащую работу класса и убедиться, что код вызывает компоненты однопотокового подразделения (STA) только из потока пользовательского интерфейса, а компоненты многопотокового подразделения (MTA) — только из фонового потока.

## <a name="authoring-agile-windows-runtime-components"></a>Создание гибких компонентов среда выполнения Windows

При определении класса ссылки в C++классе/CX он является гибким по умолчанию, т. е. он имеет `ThreadingModel`= и, и `MarshallingType`= Agile.  Если вы используете библиотеку шаблонов среда выполнения Windows C++ , можно сделать класс гибким, производным от `FtmBase` `FreeThreadedMarshaller`, который использует.  Создавая класс с атрибутами `ThreadingModel`=Both или `ThreadingModel`=MTA, убедитесь, что он является потокобезопасным.

Потоковую модель и поведение маршалинга класса ссылки можно изменять. Однако если внести изменения, которые делают класс негибким, необходимо четко понимать их последствия.

В следующем примере показано, как применять `MarshalingBehavior` атрибуты `ThreadingModel` и к классу среды выполнения в библиотеке классов среда выполнения Windows. Если приложение использует библиотеку DLL и в нем активируется объект класса `ref new` с помощью ключевого слова `MySTAClass` , этот объект активируется в однопотоковом подразделении и не поддерживает маршалинг.

```
using namespace Windows::Foundation::Metadata;
using namespace Platform;

[Threading(ThreadingModel::STA)]
[MarshalingBehavior(MarshalingType::None)]
public ref class MySTAClass
{
};
```

Незапечатанный класс должен иметь атрибуты маршалинга и потоковой модели, чтобы компилятор мог проверить, что производные классы имеют такие же значения этих атрибутов. Если эти параметры не заданы для класса явным образом, компилятор выдает ошибку и не выполняет компиляцию. Любой класс, производный от незапечатанного класса, выдает ошибку компилятора в каждом из следующих случаев:

- Атрибуты `ThreadingModel` и `MarshallingBehavior` не определены в производном классе.

- Значения атрибутов `ThreadingModel` и `MarshallingBehavior` в производном классе не соответствуют аналогичным атрибутам базового класса.

Сведения о потоках и упаковке, необходимые для компонента среда выполнения Windows стороннего производителя, указываются в сведениях о регистрации манифеста приложения для компонента. Рекомендуется сделать все компоненты среда выполнения Windows гибкими. Это гарантирует, что клиентский код сможет вызывать компонент из любого потока приложения, и улучшает производительность таких вызовов, поскольку они являются прямыми вызовами без маршалирования. Если создать класс таким образом, клиентскому коду не придется применять `Platform::Agile<T>` , чтобы использовать этот класс.

## <a name="see-also"></a>См. также

[ThreadingModel](/uwp/api/Windows.Foundation.Metadata.ThreadingModel)<br/>
[MarshallingBehavior](/uwp/api/windows.foundation.metadata.marshalingbehaviorattribute)
