---
title: Предупреждения компилятора с C4800 по C5999
ms.date: 04/21/2019
f1_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4916
- C4921
- C4934
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5106
- C5107
helpviewer_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4916
- C4921
- C4934
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5106
- C5107
ms.openlocfilehash: 4d349ba8a51b324b5262e3e38506015ea198d5e3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438275"
---
# <a name="compiler-warnings-c4800-through-c5999"></a>Предупреждения компилятора с C4800 по C5999

В статьях этого раздела документации описывается подмножество предупреждающих сообщений, созданных компилятором.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Предупреждающие сообщения

|Предупреждение|Сообщение|
|-------------|------------|
|[Предупреждение компилятора (уровень 4) C4800](compiler-warning-level-3-c4800.md)| Неявное преобразование из*типа "тип*" в bool. Возможная утрата информации |
|[Предупреждение компилятора (уровень 1) C4803](compiler-warning-level-1-c4803.md)|"*метод*": метод Raise имеет другой класс хранения из этого события, "*event*"|
|[Предупреждение компилятора (уровень 1) C4804](compiler-warning-level-1-c4804.md)|"*Операция*": ненадежное использование типа "bool" в операции|
|[Предупреждение компилятора (уровень 1) C4805](compiler-warning-level-1-c4805.md)|"*Операция*": ненадежное смешение типа "*тип1*" и типа "*тип2*" в операции|
|[Предупреждение компилятора (уровень 1) C4806](compiler-warning-level-1-c4806.md)|"*Операция*": ненадежная операция: ни одно значение типа "*тип1*", повышенное до типа "*тип2*", не может равняться заданной константе|
|[Предупреждение компилятора (уровень 1) C4807](compiler-warning-level-1-c4807.md)|"*Операция*": ненадежное смешение типа "*тип1*" и битового поля со знаком типа "*тип2*"|
|Предупреждение компилятора (уровень 1) C4808|Case "*значение*" не является допустимым значением для условия switch типа "bool"|
|Предупреждение компилятора (уровень 1) C4809|Оператор Switch имеет избыточную метку "default"; все возможные метки "Case" заданы|
|[Предупреждение компилятора (уровень 1) C4810](compiler-warning-level-1-c4810.md)|значение прагмы pack(show) == n|
|[Предупреждение компилятора (уровень 1) C4811](compiler-warning-level-1-c4811.md)|value of pragma conform(forScope, show) == value|
|[Предупреждение компилятора (уровень 1) C4812](compiler-warning-level-1-c4812.md)|устаревший стиль объявления: используйте вместо него "*new_syntax*".|
|[Предупреждение компилятора (уровень 1) C4813](compiler-warning-level-1-c4813.md)|"*функция*": дружественная функция локального класса должна быть объявлена ранее|
|[Предупреждение компилятора (уровень 4) C4816](compiler-warning-level-4-c4816.md)|"*param*": параметр имеет массив нулевого размера, который будет обрезан (если объект не передается по ссылке)|
|[Предупреждение компилятора (уровень 1) C4817](compiler-warning-level-1-c4817.md)|"*член*": недопустимое использование "." для доступа к этому члену; компилятор заменен на "->"|
|[Предупреждение компилятора (уровень 1) C4819](compiler-warning-level-1-c4819.md)|Файл содержит символ, который нельзя отобразить с помощью текущей кодовой страницы (номер). Сохраните файл в формате Юникод, чтобы предотвратить потери данных|
|[Предупреждение компилятора (уровень 4) C4820](compiler-warning-level-4-c4820.md)|"*байт*" байтов, добавленных после конструкции "*MEMBER_NAME*"|
|[Предупреждение компилятора (уровень 1) C4821](compiler-warning-level-1-c4821.md)|Не удается определить тип кодирования Юникода. Сохраните файл с подписью (BOM)|
|[Предупреждение компилятора (уровень 1) C4822](compiler-warning-level-1-c4822.md)|"функция-член": функция-член локального класса не имеет тела|
|[Предупреждение компилятора (уровень 3) C4823](compiler-warning-level-3-c4823.md)|"*функция*": использует закрепленные указатели, но семантика очистки не включена. Рекомендуется использовать/EHa|
|Предупреждение компилятора (уровень 2) C4826|Преобразование из "*тип1*" в "*тип2*" является расширенным входом. Это может привести к непредвиденному поведению во время выполнения.|
|Предупреждение компилятора (уровень 3) C4827|Открытый метод ToString с 0 параметров должен быть помечен как Virtual и override|
|[Предупреждение компилятора (уровень 1) C4829](compiler-warning-level-1-c4829.md)|Возможно, неверные параметры для функции main. Рассмотрим "int main (платформа:: массив\<платформа:: строка ^ > ^ argv)"|
|[Предупреждение компилятора (уровень 1) C4835](compiler-warning-level-1-c4835.md)|"*переменная*": инициализатор экспортируемых данных не будет выполняться до первого выполнения управляемого кода в сборке узла|
|Предупреждение компилятора (уровень 4) C4837|обнаружен триграф: "?? *символ*"заменен*символом*"|
|[Предупреждение компилятора (уровень 1) C4838](compiler-warning-level-1-c4838.md)|для преобразования из "*type_1*" в "*type_2*" требуется понижающие преобразования|
|[Предупреждение компилятора (уровень 3) C4839](compiler-warning-level-3-c4839.md)|нестандартное использование класса "*Type*" в качестве аргумента функции Variadic|
|[Предупреждение компилятора (уровень 4) C4840](compiler-warning-level-4-c4840.md)|непереносимое использование класса "*Type*" в качестве аргумента функции Variadic|
|Предупреждение компилятора (уровень 4) C4841|использовано нестандартное расширение: обозначение составного элемента, используемое в offsetof|
|Предупреждение компилятора (уровень 4) C4842|результат применения "offsetof" к типу, использующему множественное наследование, не гарантирует согласованность между выпусками компилятора|
|Предупреждение компилятора C4843|"*тип1*": обработчик исключений ссылки на тип массива или функции недоступен, используйте "*тип2*"|
|Предупреждение компилятора C4844|"экспорт модуля *module_name*;" теперь является предпочтительным синтаксисом для объявления интерфейса модуля|
| Предупреждение компилятора (уровень 4) C4845 | "\_\_declspec (без\_init\_ALL)" игнорируется, если "/d1initall\[0\|1\|2\|3]" не был указан в командной строке |
| Предупреждение компилятора (уровень 4) C4846 | "*значение*" не является допустимым аргументом для "/d1initall": флаг командной строки проигнорирован |
| Предупреждение компилятора (уровень 4) C4847 | "\_\_declspec (No\_init\_все)" может быть применен только к функции, типу класса или локальной переменной: игнорируется |
| Предупреждение компилятора (уровень 1) C4848 | Поддержка стандартного атрибута "нет\_уникальный\_адрес" в C++ 17 и более ранних версий является расширением поставщика |
|[Предупреждение компилятора (уровень 4) C4866](c4866.md)| компилятор не может применить порядок вычисления слева направо для вызова *operator_name*|
|[Предупреждение компилятора (ошибка) C4867](compiler-warning-c4867.md)|"*функция*": в вызове функции отсутствует список аргументов; Используйте "*Call*" для создания указателя на член|
|[Предупреждение компилятора (уровень 4) C4868](compiler-warning-c4868.md)|Компилятор "_File_(*line_number*)" не может применить порядок вычисления слева направо в списке инициализации в фигурных скобках|
|Предупреждение компилятора (уровень 2) C4872|обнаружено деление на ноль с плавающей запятой при компиляции графа вызовов для Concurrency::p arallel_for_each в: "*Location*"|
|Предупреждение компилятора (уровень 1) C4880|приведение типа "const *type_1*" к "*type_2*": приведение const к указателю или ссылке может привести к неопределенному поведению в функции, ограниченной amp|
|Предупреждение компилятора (уровень 4) C4881|Конструктор и (или) деструктор не будут вызываться для tile_static переменной "*variable*"|
|Предупреждение компилятора (уровень 1) C4882|передача операторов с операторами вызова, не являющимися константами, в Concurrency::p arallel_for_each является устаревшим|
|[Предупреждение компилятора C4900](compiler-warning-level-1-c4900.md)|Несоответствие Il между "*средство1*" версии "*версии 1*" и "*средство2*" версии "*версия2*"|
|[Предупреждение компилятора (уровень 1) C4905](compiler-warning-level-1-c4905.md)|приведение двухбайтового строкового литерала к "LPSTR"|
|[Предупреждение компилятора (уровень 1) C4906](compiler-warning-level-1-c4906.md)|строковой литерал приведен к "LPWSTR"|
|[Предупреждение компилятора (уровень 1) C4910](compiler-warning-level-1-c4910.md)|"\<идентификатор >:" __declspec (dllexport) "и" extern "несовместимы при явном создании экземпляра|
|[Предупреждение компилятора (уровень 1) C4912](compiler-warning-level-1-c4912.md)|"*атрибут*": поведение атрибута не определено для вложенного определяемого пользователем типа|
|[Предупреждение компилятора (уровень 4) C4913](compiler-warning-level-4-c4913.md)|пользовательский двоичный оператор "," существует, но ни одной перегрузке не удалось преобразовать все операнды, по умолчанию использован встроенный двоичный оператор ","|
|Предупреждение компилятора (уровень 1) C4916|чтобы иметь DISPID, "*Description*": должен быть введен интерфейсом|
|[Предупреждение компилятора (уровень 1) C4917](compiler-warning-level-1-c4917.md)|"*декларатор*": GUID может быть связан только с классом, интерфейсом или пространством имен|
|[Предупреждение компилятора (уровень 4) C4918](compiler-warning-level-4-c4918.md)|"*символ*": недопустимый символ в списке оптимизации директивы pragma|
|[Предупреждение компилятора (уровень 1) C4920](compiler-warning-level-1-c4920.md)|Enum Member enum member_1 = value_1 уже встречались в enum enum как member_2 = value_2|
|Предупреждение компилятора (уровень 3) C4921|"*Описание*": значение атрибута "*Attribute*" не должно быть указано в множители|
|[Предупреждение компилятора (уровень 1) C4925](compiler-warning-level-1-c4925.md)|"*метод*": метод disp не может быть вызван из скрипта|
|[Предупреждение компилятора (уровень 1) C4926](compiler-warning-level-1-c4926.md)|"*идентификатор*": символ уже определен: атрибуты пропущены|
|[Предупреждение компилятора (уровень 1) C4927](compiler-warning-level-1-c4927.md)|Недопустимое преобразование; неявно применено несколько пользовательских преобразований|
|[Предупреждение компилятора (уровень 1) C4928](compiler-warning-level-1-c4928.md)|недопустимая инициализация копии; неявно применено несколько пользовательских преобразований|
|[Предупреждение компилятора (уровень 1) C4929](compiler-warning-level-1-c4929.md)|"*файл*": библиотеку типов содержит объединение; пропуск квалификатора "embedded_idl"|
|[Предупреждение компилятора (уровень 1) C4930](compiler-warning-level-1-c4930.md)|"*прототип*": функция с прототипом не вызвана (предполагалось определение переменной?)|
|[Предупреждение компилятора (уровень 4) C4931](compiler-warning-level-4-c4931.md)|предполагается, что при построении библиотека типов была рассчитана на "число"-разрядные указатели|
|[Предупреждение компилятора (уровень 4) C4932](compiler-warning-level-4-c4932.md)|__identifier (*идентификатор*) и \__identifier (*идентификатор*) неразличимы|
|Предупреждение компилятора (уровень 1) C4934|"__delegate (многоадресная рассылка)" является устаревшим, используйте вместо него "\__delegate"|
|[Предупреждение компилятора (уровень 1) C4935](compiler-warning-level-1-c4935.md)|спецификатор доступа сборки изменен из "*Access*"|
|[Предупреждение компилятора (уровень 1, ошибка) C4936](compiler-warning-c4936.md)|Данный __declspec поддерживается только при компиляции с параметрами /clr или /clr:pure|
|[Предупреждение компилятора (уровень 4) C4937](compiler-warning-level-4-c4937.md)|"*Text1*" и "*Текст2*" неразличимы в качестве аргументов для "*директивы*"|
|[Предупреждение компилятора (уровень 4) C4938](compiler-warning-level-4-c4938.md)|"*var*": переменная сокращения числа с плавающей запятой может привести к непротиворечивым результатам в/fp: #pragma fenv_access|
|[Предупреждение компилятора C4939](compiler-warning-level-1-c4939.md)|не рекомендуется использовать директиву #pragma vtordisp, в следующих версиях Visual C++ ее не будет|
|[Предупреждение компилятора (уровень 1) C4944](compiler-warning-level-1-c4944.md)|"*символ*": невозможно импортировать символ из "*сборка Assembly1*": "*symbol*" уже существует в текущей области видимости|
|[Предупреждение компилятора (уровень 1) C4945](compiler-warning-level-1-c4945.md)|"*символ*": невозможно импортировать символ из "*сборка Assembly1*": AS "*symbol*" уже был импортирован из другой сборки "*Assembly2*"|
|[Предупреждение компилятора (уровень 1) C4946](compiler-warning-level-1-c4946.md)|reinterpret_cast, используемые между связанными классами: "*Class1*" и "*Class2*"|
|[Предупреждение компилятора (уровень 1) C4947](compiler-warning-level-1-c4947.md)|"*type_or_member*": помечен как устаревший|
|[Предупреждение компилятора (уровень 2) C4948](compiler-warning-level-2-c4948.md)|Тип возвращаемого значения "*метод доступа*" не соответствует последнему типу параметра соответствующего метода задания|
|[Предупреждение компилятора (уровень 1 и уровень 4) C4949](compiler-warning-level-1-and-level-4-c4949.md)|директивы pragma "Managed" и "unmanaged" имеют смысл только при компиляции с параметром "/CLR [: Option]"|
|[Предупреждение компилятора (уровень 1, ошибка) C4950](compiler-warning-c4950.md)|"*type_or_member*": помечен как устаревший|
|[Предупреждение компилятора (уровень 1) C4951](compiler-warning-level-1-c4951.md)|"*функция*" была изменена после сбора данных профиля, данные профиля функции не используются|
|[Предупреждение компилятора (уровень 1) C4952](compiler-warning-level-1-c4952.md)|"*функция*": данные профилирования не найдены в базе данных программы "*pgd_file*"|
|[Предупреждение компилятора (уровень 1) C4953](compiler-warning-level-1-c4953.md)|Встраивание "*функция*" было изменено после сбора данных профилирования, данные профилирования не используются|
|Предупреждение компилятора C4954|"*функция*": не профилировано (содержит выражение switch __int64)|
|Предупреждение компилятора C4955|"*import2*": импорт проигнорирован; уже импортировано из "*import1*"|
|[Предупреждение компилятора (уровень 1, ошибка) C4956](compiler-warning-c4956.md)|"*тип*": этот тип не поддается проверке|
|[Предупреждение компилятора (уровень 1, ошибка) C4957](compiler-warning-c4957.md)|"*приведение*": явное приведение "*cast_from*" к "*cast_to*" не поддается проверке|
|[Предупреждение компилятора (уровень 1, ошибка) C4958](compiler-warning-c4958.md)|"*Операция*": арифметика указателей не поддается проверке|
|[Предупреждение компилятора (уровень 1, ошибка) C4959](compiler-warning-c4959.md)|не удается определить неуправляемый тип "*тип*" в/CLR: безопасно, так как доступ к его членам дает непроверяемый код|
|[Предупреждение компилятора (уровень 4) C4960](compiler-warning-level-4-c4960.md)|"*функция*" слишком велика для профилирования|
|[Предупреждение компилятора (уровень 1) C4961](compiler-warning-c4961.md)|Данные профиля не были включены в "PGD-файл", профильная оптимизация отключена|
|[Предупреждение компилятора (уровень 4) C4962](compiler-warning-c4962.md)|"*функция*": Оптимизация с профилем отключена, так как оптимизация привела к несогласованности данных профиля|
|Предупреждение компилятора (уровень 1) C4963|"*Описание*": данные профилирования не найдены; для инструментированной сборки использовались разные параметры компилятора|
|[Предупреждение компилятора (уровень 1) C4964](compiler-warning-level-1-c4964.md)|Параметры оптимизации не указаны. сведения о профиле не будут собраны|
|[Предупреждение компилятора (уровень 1) C4965](compiler-warning-level-1-c4965.md)|Неявная рамка целого числа 0; Используйте nullptr или явное приведение|
|Предупреждение компилятора (уровень 1) C4966|"*функция*" имеет __code_seg аннотации с неподдерживаемым именем сегмента, аннотация игнорируется|
|Предупреждение компилятора C4970|конструктор делегата: целевой объект проигнорирован, так как "*тип*" является статическим|
|Предупреждение компилятора (уровень 1) C4971|Порядок аргументов: \<целевого объекта >, \<целевой функции > для конструктора делегата является устаревшим, используйте \<целевую функцию >, \<целевой объект = "" >|
|[Предупреждение компилятора (уровень 1, ошибка) C4972](compiler-warning-c4972.md)|Прямое изменение или обработка результатов операции распаковки в виде левостороннего значения недоступны для проверки|
|Предупреждение компилятора (уровень 1) C4973|"*символ*": помечен как устаревший|
|Предупреждение компилятора (уровень 1) C4974|"*символ*": помечен как устаревший|
|Предупреждение компилятора (уровень 3) C4981|Warbird: функция "*функция*", помеченная как __forceinline, не встроена, так как она содержит семантику исключения|
|[Предупреждение компилятора C4984](compiler-warning-c4984.md)|"If constexpr" — расширение языка C++ 17|
|[Предупреждение компилятора (уровень 4) C4985](compiler-warning-level-4-c4985.md)|"*symbol_name*": атрибуты не существуют в предыдущем объявлении.|
|[Предупреждение компилятора C4986](compiler-warning-c4986.md)|"*объявление*": спецификация исключения не соответствует предыдущему объявлению|
|Предупреждение компилятора (уровень 4) C4987|используется нестандартное расширение: throw (...)|
|Предупреждение компилятора (уровень 4) C4988|"*переменная*": переменная объявлена вне области видимости класса или функции|
|Предупреждение компилятора (уровень 4) C4989|"*тип*": тип имеет конфликтующие определения.|
|Предупреждение компилятора (уровень 3) C4990|Warbird: *сообщение*|
|Предупреждение компилятора (уровень 3) C4991|Warbird: функция "*функция*", помеченная как __forceinline, не встроена, так как уровень защиты встраивания больше родительского|
|Предупреждение компилятора (уровень 3) C4992|Warbird: функция "*функция*", помеченная как __forceinline, не встроена, так как она содержит встроенную сборку, которая не может быть защищена|
|[Предупреждение компилятора (уровень 3) C4995](compiler-warning-level-3-c4995.md)|"*функция*": имя помечено как #pragma устарело|
|[Предупреждение компилятора (уровень 3) C4996](compiler-warning-level-3-c4996.md)|"*устаревшее объявление*": *устаревшее сообщение* (или "объявлено как устаревшее")|
|[Предупреждение компилятора (уровень 1) C4997](compiler-warning-level-1-c4997.md)|"*класс*": coclass не реализует COM-интерфейс или псевдо-интерфейс|
|Предупреждение компилятора (уровень 1) C4998|СБОЙ ожидания: *Ожидание*(*значение*)|
|[Предупреждение компилятора C4999](compiler-warning-level-1-c4999.md)|Неизвестное предупреждение выберите команду "Техническая поддержка" в C++ меню "Справка" или откройте справочный файл технической поддержки для получения дополнительных сведений|
|Предупреждение компилятора C5022|"*тип*": задано несколько конструкторов перемещения|
|Предупреждение компилятора C5023|"*тип*": задано несколько операторов присваивания перемещения|
|Предупреждение компилятора (уровень 4) C5024|"*тип*": конструктор перемещения неявно определен как удаленный|
|Предупреждение компилятора (уровень 4) C5025|"*тип*": оператор присваивания перемещения неявно определен как удаленный|
|Предупреждение компилятора (уровень 1 и уровень 4) C5026|"*тип*": конструктор перемещения неявно определен как удаленный|
|Предупреждение компилятора (уровень 1 и уровень 4) C5027|"*тип*": оператор присваивания перемещения неявно определен как удаленный|
|Предупреждение компилятора (уровень 1) C5028|"*имя*": выравнивание, указанное в предыдущем объявлении (*число*), не указано в определении|
|Предупреждение компилятора (уровень 4) C5029|нестандартное расширение: атрибуты выравнивания C++ в применяются только к переменным, элементам данных и типам тегов|
|Предупреждение компилятора (уровень 3) C5030|атрибут "*атрибут*" не распознан|
|Предупреждение компилятора (уровень 4) C5031|предупреждение #pragma (POP): вероятно несоответствие, выявление состояния предупреждения, помещенное в другой файл|
|Предупреждение компилятора (уровень 4) C5032|обнаружено #pragma предупреждение (Push) без соответствующего #pragma предупреждения (POP)|
|Предупреждение компилятора (уровень 1) C5033|"*хранилище-класс*" больше не является поддерживаемым классом хранения|
|Предупреждение компилятора C5034|Использование встроенного "*встроенного*" приводит к компиляции *функции* функции в виде гостевого кода|
|Предупреждение компилятора C5035|Использование функции "*Feature*" приводит к компиляции *функции* функции в виде гостевого кода|
|Предупреждение компилятора (уровень 1) C5036|преобразование указателя функции varargs при компиляции с/Hybrid: x86arm64 "*тип1*" в "*тип2*"|
|Предупреждение компилятора (ошибка) C5037|"*член-функция*": внешнее определение члена шаблона класса не может иметь аргументы по умолчанию|
|[Предупреждение компилятора (уровень 4) C5038](c5038.md)|элемент данных "*member1*" будет инициализирован после элемента данных "*член2*"|
|Предупреждение компилятора (уровень 4) C5039|"*функция*": указатель или ссылка на потенциально вызывающую функцию, переданную в внешнюю функцию C в разделе-ЕХК. Если эта функция создает исключение, может возникнуть неопределенное поведение.|
|Предупреждение компилятора (уровень 3) C5040|спецификации динамических исключений допустимы только в C++ 14 и более ранних версиях. рассматривать как "только" (false)|
|Предупреждение компилятора (уровень 1) C5041|"*Определение*": нестандартное определение для статических данных-члена constexpr не требуется и является устаревшим в c++ 17|
|Предупреждение компилятора (уровень 3) C5042|"*объявление*": объявления функций в области видимости блока не могут быть указаны "inline" в C++стандарте; удалить спецификатор "inline"|
|Предупреждение компилятора (уровень 2) C5043|"*Спецификация*": спецификация исключения не соответствует предыдущему объявлению|
|Предупреждение компилятора (уровень 4) C5044|Аргумент *параметра командной строки указывает на* несуществующий путь "*path*"|
| [Предупреждение компилятора C5045](c5045.md) | Компилятор вставит устранением рисков Spectre смягчения для загрузки памяти, если указан параметр/Qspectre |
| [Предупреждение компилятора (уровень 2) C5046](c5046.md) | "*функция*": символ, включающий тип с внутренней компоновкой, не определен |
| Предупреждение компилятора (уровень 1) C5047 | Использование нестандартного \_\_, если\_существует с модулями, не поддерживается |
| Предупреждение компилятора (уровень 1) C5048 | Использование макроса "*имяМакроса*" может привести к недетерминированному результату |
| Предупреждение компилятора (уровень 1) C5049 | "*строка*": внедрение полного пути может привести к выходным данным, зависящим от компьютера |
| Предупреждение компилятора (уровень 1) C5050 | Возможна несовместимость окружения при импорте модуля "*module_name*": *Ошибка* |
| Предупреждение компилятора (уровень 1) C5100 | \_\_ва\_ARGSs\_\_ зарезервировано для использования в макросах Variadic |
| Предупреждение компилятора (уровень 1) C5101 | использование директивы препроцессора в списке аргументов макроса, подобной функции, не определено |
| Предупреждение компилятора (уровень 1) C5102 | Пропуск недопустимого определения макроопределения в командной строке "*значение*" |
| Предупреждение компилятора (уровень 1) C5103 | При вставлении "*токен1*" и "*токен2*" не создается допустимый токен предварительной обработки |
| Предупреждение компилятора (уровень 1) C5104 | найден "*строка1*#*строка2*" в списке замены макросов, возможно, имелось в виду "*строка1*" "#*строка2*"? |
| [Предупреждение компилятора (уровень 1) C5105](c5105.md) | расширение макроса, создающее "defined", имеет неопределенное поведение |
| Предупреждение компилятора (уровень 1) C5106 | макрос переопределен с разными именами параметров |
| Предупреждение компилятора (уровень 1) C5107 | Отсутствует завершающий символ "*char*" |

## <a name="see-also"></a>См. также раздел

[Ошибки иC++ предупреждения средств разработки C/компилятора и сборки](../compiler-errors-1/c-cpp-build-errors.md) \
[Предупреждения компилятора C4000-C5999](compiler-warnings-c4000-c5999.md)
