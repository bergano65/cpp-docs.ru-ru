---
title: Установка Visual C++ для разработки кроссплатформенных мобильных приложений на языке C++
ms.date: 10/17/2019
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
ms.openlocfilehash: 0304bd9aaf4194e7dd785b1293f59624ba365f8a
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "79469935"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>Установка Visual C++ для разработки кроссплатформенных мобильных приложений на языке C++

В Visual Studio C++ можно использовать для создания классических приложений Windows, приложений универсальная платформа Windows (UWP) и приложений Linux. Теперь вы можете создавать C++ приложения для Android и iOS. **Разработка мобильных приложений с C++**  рабочей нагрузкой — это устанавливаемый набор компонентов в Visual Studio. Он включает в себя межплатформенные шаблоны iOS, Android и UWP Visual Studio. Рабочая нагрузка устанавливает кросс-платформенные средства и пакеты SDK, необходимые для быстрого начала работы. Вам не придется самостоятельно определять, скачивать и настраивать их. С помощью этих средств в Visual Studio можно быстро создавать, редактировать, отлаживать и тестировать кроссплатформенные проекты.

В этой статье описывается установка средств и программного обеспечения сторонних разработчиков, необходимых для разработки кроссплатформенных приложений на языке C++с помощью Visual Studio. Обзор см. на странице [Кроссплатформенная разработка для мобильных устройств на Visual C++](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/).

## <a name="requirements"></a>Требования

::: moniker range="vs-2017"

- Требования для установки семейства продуктов Visual Studio см. в [этой статье](/visualstudio/productinfo/vs2017-system-requirements-vs).

   > [!IMPORTANT]
   > Если вы используете Windows 7 или Windows Server 2008 R2, вы можете писать код для классических приложений для Windows, приложений и библиотек Android Native Activity, а также приложений и библиотек кода для iOS, но не для Windows Store и приложений UWP.

::: moniker-end
::: moniker range=">=vs-2019"

- Требования для установки семейства продуктов Visual Studio см. в [этой статье](/visualstudio/releases/2019/system-requirements).

   > [!IMPORTANT]
   > Если вы используете Windows 7 или Windows Server 2008 R2, вы можете писать код для классических приложений Windows, приложений и библиотек Android Native Activity, а также приложений и библиотек кода для iOS, но не для приложений Windows Phone и UWP.

::: moniker-end

Применительно к созданию приложений для определенных платформ устройств существует несколько дополнительных требований.

- Эмуляторы Android x86, которые поставляются с пакетом SDK для Android, лучше всего работают на компьютерах, которые могут использовать аппаратное ускорение, таких как Intel Hardware Accelerated Execution Manager (HAXM). Дополнительные сведения см. в статье [Аппаратное ускорение для производительной работы эмулятора (Hyper-V и HAXM)](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin&pivots=windows).

- Создание кода для iOS требует наличия Apple ID, учетной записи программы для разработчиков iOS и компьютера Mac, на котором может выполняться [Xcode](https://developer.apple.com/xcode/) версии 10.2 или выше в OS X Mavericks (версии 10.9) или более поздней. Ссылку на инструкции по установке см. в разделе [Установка инструментов для iOS](#install-tools-for-ios).

- Эмуляторам Windows Phone требуется компьютер, на котором можно запускать Hyper-V. Чтобы установить и запустить эмуляторы, в Windows должен быть включен компонент Hyper-V. Дополнительные сведения см. в разделе [Системные требования эмулятора](/visualstudio/cross-platform/system-requirements-for-the-visual-studio-emulator-for-android).

## <a name="get-the-tools"></a>Получить инструменты

Рабочая нагрузка "Разработка мобильных приложений на языке C++" доступна в выпусках Visual Studio Community, Professional и Enterprise. Чтобы получить Visual Studio, перейдите на страницу [скачиваемых файлов этого продукта](https://visualstudio.microsoft.com/downloads/). Средства разработки кроссплатформенных мобильных приложений доступны в Visual Studio 2015 и последующих версиях.

## <a name="install-the-tools"></a>Установка инструментов

Visual Studio Installer содержит рабочую нагрузку **Разработка мобильных приложений на C++** . Эта рабочая нагрузка устанавливает инструменты языка C++, шаблоны и компоненты, необходимые для разработки Android и iOS в Visual Studio. Он включает наборы инструментов GCC и Clang, необходимые для сборок и отладки Android. Рабочая нагрузка устанавливает пакет SDK для Android и компоненты для взаимодействия с компьютером Mac для разработки с iOS. Он также устанавливает сторонние средства и пакеты средств разработки программного обеспечения, необходимые для поддержки разработки приложений iOS и Android. В основном это программное обеспечение с открытым исходным кодом, необходимое для поддержки платформы Android.

- Для построения C++ кода, ориентированного на платформу Android, необходимы нативный пакет средств разработки для Android (NDK), Apache Ant и инструменты разработки C++ Android.

- Эмулятор Google Android и Intel Hardware Accelerated Execution Manager (HAXM) являются дополнительными, но рекомендуемыми компонентами. (Драйверы Intel HAXM работают только на процессорах Intel и несовместимы с некоторыми виртуальными машинами, включая Hyper-V.) Вы можете разрабатывать и выполнять отладку непосредственно на устройстве Android, но для отладки часто бывает проще использовать эмулятор на рабочем столе.

- Инструменты разработки C++ iOS необходимы для создания кода C++, ориентированного на платформу iOS.

> [!NOTE]
> Если вы используете Visual Studio 2015, см. статью [Установка Visual C++ для разработки кроссплатформенных мобильных приложений на языке C++](install-visual-cpp-for-cross-platform-mobile-development.md?view=vs-2015).

### <a name="install-the-mobile-development-with-c-workload"></a>Установка рабочей нагрузки "Разработка мобильных приложений на языке C++"

1. Запустите **Visual Studio Installer** **Пуск**.

1. Если вы установили Visual Studio, нажмите кнопку **Изменить**, чтобы изменить установленную версию. В противном случае выберите **Установить**, чтобы установить Visual Studio.

1. Выберите вкладку **Рабочие нагрузки**, прокрутите вниз, а затем в установщике Visual Studio Installer выберите рабочую нагрузку **Разработка мобильных приложений на языке C++** . При выборе этой рабочей нагрузки также выбираются другие необходимые компоненты для разработки на языке C++. Ви можете также установить другие рабочие нагрузки и отдельные компоненты. Чтобы создать кроссплатформенный код, который также ориентирован на приложения UWP, выберите рабочую нагрузку **Разработка приложений для универсальной платформы Windows**.

1. В области **Сведения об установке** разверните узел **Разработка мобильных приложений на языке C++** . В разделе **Необязательное** можно выбрать дополнительные версии NDK, эмулятор Google Android Emulator, Intel Hardware Accelerated Execution Manager и средство ускорения сборки IncrediBuild.

1. По умолчанию один или несколько компонентов программы установки пакетов SDK для Android включены в рабочей нагрузке. Доступны также дополнительные версии пакета SDK для Android. Чтобы добавить их к установке, перейдите на вкладку **Отдельные компоненты**, а затем прокрутите вниз до раздела **Пакеты SDK, библиотеки и платформы** и выберите нужные.

1. Нажмите кнопку **Изменить** или **Установить**, чтобы установить рабочую нагрузку **Разработка мобильных приложений на языке C++** и другие выбранные рабочие нагрузки и дополнительные компоненты.

   После завершения установки закройте установщик и перезагрузите компьютер. Некоторые действия по настройке сторонних компонентов не вступают в силу до перезагрузки компьютера.

   > [!IMPORTANT]
   > Перезагрузка необходима для того, чтобы проверить, все ли установлено правильно.

1. Запустите Visual Studio.

## <a name="install-tools-for-ios"></a>Install tools for iOS

Visual Studio можно использовать для изменения, отладки и развертывания кода iOS в симуляторе iOS. Или на устройство iOS. Из-за ограничений лицензирования код должен быть создан удаленно на компьютере Mac. Чтобы создать и запустить приложения iOS с помощью Visual Studio, сначала настройте и настройте удаленный агент на компьютере Mac. Подробные инструкции по установке, а также сведения о необходимых компонентах и параметрах настройки см. в статье [Установка и настройка средств для разработки с помощью iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Если вы не выполняете сборку для iOS, этот шаг можно пропустить.

## <a name="install-or-update-dependencies-manually"></a>Установка или обновление зависимостей вручную

Не нужно устанавливать все сторонние зависимости при установке **разработки мобильных приложений с C++**  рабочей нагрузкой (или в Visual Studio 2015, вариант разработки Visual C++ Mobile). Установите их позже, выполнив действия, описанные в [статье Установка средств](#install-the-tools). Установщик Visual Studio Installer регулярно обновляется, что позволяет устанавливать последние компоненты сторонних разработчиков. Используйте его для установки обновленных пакетов SDK и Ндкс. Их также можно установить или обновить отдельно от Visual Studio.

Вы можете снова запустить приложение диспетчера пакетов SDK в каталоге пакет SDK для Android, чтобы обновить пакет SDK. И, чтобы установить дополнительные средства и дополнительные уровни API. Если запустить диспетчер пакетов SDK, не используя команду **Запуск от имени администратора** , обновления могут не установиться. Если при сборке приложений Android возникают проблемы, проверьте наличие обновлений для установленных пакетов SDK в диспетчере пакетов SDK.

Чтобы использовать некоторые эмуляторы пакет SDK для Android, может потребоваться настроить аппаратное ускорение. Дополнительные сведения см. в статье [Аппаратное ускорение для производительной работы эмулятора (Hyper-V и HAXM)](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

В большинстве случаев Visual Studio может обнаружить конфигурации для установленного стороннего программного обеспечения. Пути установки сохраняются во внутренних переменных среды. Вы можете переопределить пути по умолчанию для этих средств разработки кроссплатформенных приложений в интегрированной среде разработки Visual Studio.

### <a name="to-set-the-paths-for-third-party-tools"></a>Задание путей для средств сторонних разработчиков

1. В строке меню Visual Studio выберите **Сервис** > **Параметры**.

1. В диалоговом окне **Параметры** выберите **Кроссплатформенный** > **C++**  > **Android**.

   ![Параметры пути средства Android](../cross-platform/media/cppmdd-options-android.png "Параметры пути к средствам Android")

1. Чтобы изменить путь, используемый средством, установите флажок рядом с ним и измените путь к папке в текстовом поле. Кроме того, можно нажать кнопку обзора ( **...** ), чтобы открыть диалоговое окно **Выберите местоположение** и выбрать папку.

1. Чтобы сохранить настраиваемое расположение средства, нажмите кнопку **ОК** .

## <a name="see-also"></a>См. также раздел

[Установка и настройка средств для разработки с помощью iOS](install-and-configure-tools-to-build-using-ios.md)\
[Visual C++ для разработки кросс-платформенных мобильных приложений](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)
