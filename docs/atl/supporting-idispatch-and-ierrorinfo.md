---
title: Поддержка IDispatch и IErrorInfo
ms.date: 11/04/2016
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
ms.openlocfilehash: 2dcebd215ff5e1bdf72323323dfbaebd16fa3403
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342027"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Поддержка IDispatch и IErrorInfo

Можно использовать класс шаблона [IDispatchImpl](../atl/reference/idispatchimpl-class.md) для предоставления реализацию по умолчанию `IDispatch Interface` часть любого сдвоенные интерфейсы в объекте.

Если объект использует `IErrorInfo` интерфейс сообщить ошибок обратно клиенту, а затем ваш объект должен поддерживать `ISupportErrorInfo Interface` интерфейс. Класс шаблона [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) предоставляет простой способ выполнить это, если имеется только один интерфейс, который выдает ошибки для объекта.

## <a name="see-also"></a>См. также

[Основы COM-объектов ATL](../atl/fundamentals-of-atl-com-objects.md)
