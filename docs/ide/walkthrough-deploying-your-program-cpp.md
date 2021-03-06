---
title: Пошаговое руководство. Развертывание программы (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: 5cc4ead7aaef2ffa56870a374b0b73d16eb31521
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400961"
---
# <a name="walkthrough-deploying-your-program-c"></a>Пошаговое руководство. Развертывание программы (C++)

Теперь, когда вы создали свое приложение, выполнив описанные ранее пошаговые руководства, необходимо выполнить последний шаг — создать установщик, чтобы другие пользователи могли установить программу на своих компьютерах. Для создания установщика следует добавить новый проект в имеющееся решение. Выходным файлом этого проекта будет являться файл setup.exe, который служит для установки приложения на другом компьютере.

В этом пошаговом руководстве показано, как развернуть приложение с помощью установщика Windows. Кроме того, для развертывания приложения может использоваться ClickOnce. Дополнительные сведения см. в разделе [ClickOnce Deployment for Visual C++ Applications](../windows/clickonce-deployment-for-visual-cpp-applications.md). Дополнительные общие сведения о развертывании см. в разделе [Развертывание приложений, служб и компонентов](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="prerequisites"></a>Предварительные требования

- В этом пошаговом руководство предполагается, что вы знакомы с основами языка C++.

- В нем также предполагается, что вы выполнили инструкции из предыдущих руководств, перечисленных в статье [Использование интегрированной среды разработки Visual Studio для разработки приложений для настольных систем на языке C++](using-the-visual-studio-ide-for-cpp-desktop-development.md).

- Инструкции этого руководства невозможно выполнить в выпусках Express среды Visual Studio.

## <a name="install-the-visual-studio-setup-and-deployment-project-template"></a>Установка шаблона проекта установки и развертывания Visual Studio

Инструкции в этом разделе отличаются в зависимости от установленной версии Visual Studio. Убедитесь в том, что в средстве выбора версии в левом верхнем углу этой страницы выбрана правильная версия.

::: moniker range="vs-2019"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2019"></a>Установка шаблона проекта установки и развертывания для Visual Studio 2019

1. Если вы еще не скачали расширения проектов установщика Microsoft Visual Studio, сделайте это сейчас. Это расширение предоставляется использующим Visual Studio разработчикам бесплатно. Оно добавляет в Visual Studio функции шаблонов для проектов установки и развертывания. Если вы подключены к Интернету, выберите в Visual Studio **Расширения** > **Управление расширениями**. В диалоговом окне **Расширения и обновления** выберите вкладку **В сети** и введите в поле поиска строку *проекты установщика Microsoft Visual Studio*. Нажмите клавишу **ВВОД**, выберите **Проекты установщика Microsoft Visual Studio \<номер_версии>** и щелкните **Скачать**. Выберите запуск и установку расширения, а затем перезапустите Visual Studio.

1. В строке меню Visual Studio последовательно выберите **Файл** > **Последние проекты и решения**, а затем действие открытия проекта.

1. В строке меню выберите **Файл** > **Создать** > **Проект**, чтобы открыть диалоговое окно **Создание проекта**. В поле поиска введите "Установка" и выберите в списке результатов пункт **Проект установки**.

1. В поле **Имя** введите имя проекта установки. В раскрывающемся списке **Решение** выберите пункт **Добавить в решение**. Нажмите кнопку **ОК**, чтобы создать проект установки. В окне редактора откроется вкладка **File Assistant (ProjectName)** (Помощник по файлам (имя проекта)).

1. Щелкните правой кнопкой мыши узел **Папка приложения** и последовательно выберите **Добавить** > **Выходной элемент проекта**, чтобы открыть диалоговое окно **Добавление выходной группы проекта**.

1. В этом диалоговом окне выберите **Основные выходные файлы** и щелкните **OK**. Появится новый элемент с именем **Primary Output from Game (Active)** (Основные выходные файлы игры (активно)).

1. Выберите этот элемент **Primary Output from Game (Active)** (Основные выходные файлы игры (активно)), щелкните его правой кнопкой мыши и выберите пункт **Create Shortcut to Primary Output from Game (Active)** (Создать ярлык на основные выходные файлы игры (активно)). Появится новый элемент с именем **Shortcut to Primary Output from Game (Active)** (Ярлык на основные выходные файлы игры (активно)).

1. Присвойте этому ярлыку имя *Игра*, затем перетащите его в узел **User's Programs Menu** (Пользовательское меню "Программы") в левой части окна.

1. В **обозревателе решений** выберите проект **Установщик игры**, а затем **Представление** > **Окно "Свойства"** или нажмите клавишу **F4**, чтобы открыть окно **Свойства**.

1. Укажите дополнительные сведения, которые вы хотите отображать в установщике.  Например, укажите *Contoso* в поле **Производитель**, *Установщик игры* в поле **Название продукта** и *http\://www.contoso.com* в поле **SupportUrl** (URL-адрес поддержки).

1. В строке меню последовательно выберите пункты **Сборка** > **Диспетчер конфигураций**. В таблице **Проект** установите флажок в столбце **Сборка** для элемента **Установщик игры**. Нажмите кнопку **Закрыть**.

1. В строке меню выберите **Сборка** > **Собрать решение**, чтобы выполнить сборку проекта "Игра" и проекта "Установщик игры".

1. В папке решения найдите программу setup.exe, собранную из проекта "Установщик игры", и запустите ее, чтобы установить приложение "Игра" на компьютере. Можно скопировать этот файл (вместе с GameInstaller.msi), чтобы установить приложение и все необходимые файлы библиотеки на другом компьютере.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2017-and-earlier"></a>Установка шаблона проекта установки и развертывания для Visual Studio 2017 и более ранних версий

1. Если вы подключены к Интернету, выберите в Visual Studio **Сервис** > **Расширения и обновления**.

1. В разделе **Расширения и обновления** выберите вкладку **В Интернете** и введите в поле поиска строку *проекты установщика Microsoft Visual Studio*. Нажмите клавишу **ВВОД**, выберите **Проекты установщика Microsoft Visual Studio \<номер_версии>** и щелкните **Скачать**.

1. Выберите установку расширения, а затем перезапустите Visual Studio.

1. В строке меню последовательно выберите **Файл** > **Последние проекты и решения** и щелкните решение **Игра**, чтобы снова открыть его.

### <a name="to-create-a-setup-project-and-install-your-program"></a>Создание проекта установки и установка программы

1. Измените активную конфигурацию решения, указав значение Выпуск. В строке меню последовательно выберите пункты **Сборка** > **Диспетчер конфигураций**. В диалоговом окне **Диспетчер конфигураций** выберите в раскрывающемся списке **Активная конфигурация решения** пункт **Выпуск**. Нажмите кнопку **Закрыть**, чтобы сохранить конфигурацию.

1. В строке меню выберите **Файл**  > **Создать** > **Проект**, чтобы открыть диалоговое окно **Новый проект**.

1. В левой области диалогового окна разверните узлы **Установленные** > **Другие типы проектов**, а затем выберите пункт **Visual Studio Installer**. В центральной области выберите **Настройка проекта**.

1. В поле **Имя** введите имя проекта установки. Для этого примера введите *Установщик игры*. В раскрывающемся списке **Решение** выберите пункт **Добавить в решение**. Нажмите кнопку **ОК**, чтобы создать проект установки. В окне редактора откроется вкладка **File Assistant (Game Installer)** (Помощник по файлам (установщик игры)).

1. Щелкните правой кнопкой мыши узел **Папка приложения** и последовательно выберите **Добавить** > **Выходной элемент проекта**, чтобы открыть диалоговое окно **Добавление выходной группы проекта**.

1. В этом диалоговом окне выберите **Основные выходные файлы** и щелкните **OK**. Появится новый элемент с именем **Primary Output from Game (Active)** (Основные выходные файлы игры (активно)).

1. Выберите этот элемент **Primary Output from Game (Active)** (Основные выходные файлы игры (активно)), щелкните его правой кнопкой мыши и выберите пункт **Create Shortcut to Primary Output from Game (Active)** (Создать ярлык на основные выходные файлы игры (активно)). Появится новый элемент с именем **Shortcut to Primary Output from Game (Active)** (Ярлык на основные выходные файлы игры (активно)).

1. Присвойте этому ярлыку имя *Игра*, затем перетащите его в узел **User's Programs Menu** (Пользовательское меню "Программы") в левой части окна.

1. В **обозревателе решений** выберите проект **Установщик игры**, а затем **Представление** > **Окно "Свойства"** или нажмите клавишу **F4**, чтобы открыть окно **Свойства**.

1. Укажите дополнительные сведения, которые вы хотите отображать в установщике.  Например, укажите *Contoso* в поле **Производитель**, *Установщик игры* в поле **Название продукта** и *http\://www.contoso.com* в поле **SupportUrl** (URL-адрес поддержки).

1. В строке меню последовательно выберите пункты **Сборка** > **Диспетчер конфигураций**. В таблице **Проект** установите флажок в столбце **Сборка** для элемента **Установщик игры**. Нажмите кнопку **Закрыть**.

1. В строке меню выберите **Сборка** > **Собрать решение**, чтобы выполнить сборку проекта "Игра" и проекта "Установщик игры".

1. В папке решения найдите программу setup.exe, собранную из проекта "Установщик игры", и запустите ее, чтобы установить приложение "Игра" на компьютере. Можно скопировать этот файл (вместе с GameInstaller.msi), чтобы установить приложение и все необходимые файлы библиотеки на другом компьютере.

::: moniker-end

## <a name="next-steps"></a>Следующие шаги

**Предыдущая статья:** [Пошаговое руководство: Отладка проекта (C++)](walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>См. также

[Справочник по языку C++](../cpp/cpp-language-reference.md)<br/>
[Проекты и системы сборки](../build/projects-and-build-systems-cpp.md)<br/>
[Развертывание классических приложений](../windows/deploying-native-desktop-applications-visual-cpp.md)<br/>
