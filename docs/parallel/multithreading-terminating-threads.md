---
title: Многопоточность. Завершение потоков в MFC
ms.date: 08/27/2018
helpviewer_keywords:
- premature thread termination
- starting threads
- threading [MFC], terminating threads
- multithreading [C++], terminating threads
- threading [C++], stopping threads
- terminating threads
- stopping threads
- AfxEndThread method
ms.assetid: 4c0a8c6d-c02f-456d-bd02-0a8c8d006ecb
ms.openlocfilehash: 60c60d1aedf19ade6c84dafacd7de7a2e650e6ca
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446269"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>Многопоточность. Завершение потоков в MFC

Две нормальные ситуации приводят к прерыванию потока: функция управления завершает работу или поток не может быть выполнен до завершения. Если текстовый процессор использовал поток для фоновой печати, функция управления будет завершаться нормально при успешном завершении печати. Однако, если пользователь хочет отменить печать, поток фоновой печати должен преждевременно завершиться. В этом разделе объясняется, как реализовать каждую ситуацию и как получить код выхода потока после его завершения.

- [Нормальное завершение потока](#_core_normal_thread_termination)

- [Преждевременное завершение потока](#_core_premature_thread_termination)

- [Получение кода выхода потока](#_core_retrieving_the_exit_code_of_a_thread)

## <a name="_core_normal_thread_termination"></a>Нормальное завершение потока

Для рабочего потока простое завершение потока является простым: выход из функции управления и возврат значения, обозначающего причину завершения. Можно использовать либо функцию [афксендсреад](../mfc/reference/application-information-and-management.md#afxendthread) , либо оператор **return** . Как правило, 0 означает успешное завершение, но это не так.

Для потока пользовательского интерфейса процесс выполняется так же просто: из потока пользовательского интерфейса вызовите [посткуитмессаже](/windows/win32/api/winuser/nf-winuser-postquitmessage) в Windows SDK. Единственный параметр, который `PostQuitMessage` принимает, — это код выхода потока. Как и для рабочих потоков, 0 обычно означает успешное завершение.

## <a name="_core_premature_thread_termination"></a>Преждевременное завершение потока

Преждевременное завершение потока почти так же просто: вызовите [афксендсреад](../mfc/reference/application-information-and-management.md#afxendthread) из потока. Передайте нужный код выхода в качестве единственного параметра. Это останавливает выполнение потока, освобождает стек потока, отсоединяет все библиотеки DLL, подключенные к потоку, и удаляет объект потока из памяти.

`AfxEndThread` должны вызываться из потока для завершения. Если вы хотите завершить поток из другого потока, необходимо настроить метод связи между двумя потоками.

## <a name="_core_retrieving_the_exit_code_of_a_thread"></a>Получение кода выхода потока

Чтобы получить код выхода рабочего процесса или потока пользовательского интерфейса, вызовите функцию [жетекситкодесреад](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread) . Дополнительные сведения об этой функции см. в Windows SDK. Эта функция принимает маркер в поток (хранящийся в `m_hThread`ном элементе данных `CWinThread` объектов) и адрес DWORD.

Если поток все еще активен, `GetExitCodeThread` помещает STILL_ACTIVE в указанный адрес DWORD. в противном случае код выхода помещается в этот адрес.

Получение кода выхода объектов [CWinThread](../mfc/reference/cwinthread-class.md) требует дополнительного шага. По умолчанию, когда `CWinThread` поток завершается, объект потока удаляется. Это означает, что вы не можете получить доступ к элементу данных `m_hThread`, так как объект `CWinThread` больше не существует. Чтобы избежать такой ситуации, выполните одно из следующих действий.

- Задайте для элемента данных `m_bAutoDelete` значение FALSE. Это позволяет `CWinThread` объект после завершения потока выдерживаться. После завершения потока можно получить доступ к элементу данных `m_hThread`. Однако при использовании этого метода вы несете ответственность за уничтожение объекта `CWinThread`, так как платформа не будет автоматически удалять его. Это является предпочтительным методом.

- Храните обработчик отдельного потока отдельно. После создания потока скопируйте его элемент данных `m_hThread` (с помощью `::DuplicateHandle`) в другую переменную и получите доступ к ней через эту переменную. Таким образом, объект автоматически удаляется при завершении работы, и вы можете определить причину завершения потока. Будьте внимательны, чтобы поток не завершался, прежде чем можно будет дублировать этот обработчик. Самый надежный способ сделать это — передать CREATE_SUSPENDED [афксбегинсреад](../mfc/reference/application-information-and-management.md#afxbeginthread), сохранить этот обработчик, а затем возобновить поток, вызвав [ресумесреад](../mfc/reference/cwinthread-class.md#resumethread).

Любой из этих методов позволяет определить причину завершения `CWinThread` объекта.

## <a name="see-also"></a>См. также раздел

[Реализация многопоточности на языке C++ с помощью классов MFC](multithreading-with-cpp-and-mfc.md)<br/>
[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread)
