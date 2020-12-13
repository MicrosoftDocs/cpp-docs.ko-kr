---
description: '자세한 정보: 이벤트 처리 원칙'
title: 이벤트 처리 원칙 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: 29b9542b4e026d320857990a0ef6253f310535e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147981"
---
# <a name="event-handling-principles"></a>이벤트 처리 원칙

모든 이벤트 처리에 공통 된 세 가지 단계가 있습니다. 다음 작업을 수행 해야 합니다.

- 개체에 이벤트 인터페이스를 구현 합니다.

- 개체에서 이벤트를 수신 하려고 하는 이벤트 소스에 대해 알립니다.

- 개체가 더 이상 이벤트를 수신 하지 않아도 되는 경우 이벤트 소스를 Unadvise 합니다.

이벤트 인터페이스를 구현 하는 방법은 해당 형식에 따라 달라 집니다. 이벤트 인터페이스는 vtable, dual 또는를 사용할 수 있습니다. 인터페이스를 정의 하는 것은 이벤트 소스의 디자이너에 게 있습니다. 인터페이스를 구현 하는 것은 사용자의 것입니다.

> [!NOTE]
> 이벤트 인터페이스를 이중으로 사용할 수 없다는 기술적 이유는 없지만 duals 사용을 방지 하기 위한 여러 가지 좋은 디자인 이유가 있습니다. 그러나이는 이벤트 *소스의* 디자이너/구현 자가 결정 하는 내용입니다. 이벤트의 관점에서 작업 하 고 있으므로 `sink` 선택 하지 않아도 되며 이중 이벤트 인터페이스를 구현 하는 것을 허용 해야 합니다. 이중 인터페이스에 대 한 자세한 내용은 [이중 인터페이스 및 ATL](../atl/dual-interfaces-and-atl.md)을 참조 하세요.

이벤트 소스를 세 단계로 나눌 수 있습니다.

- [IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)에 대 한 원본 개체를 쿼리 합니다.

- 관심 있는 이벤트 인터페이스의 IID를 전달 하는 [IConnectionPointContainer:: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) 를 호출 합니다. 성공 하면 연결 지점 개체에 대 한 [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) 인터페이스가 반환 됩니다.

- 이벤트 싱크의를 전달 하는 [IConnectionPoint:: Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) 를 호출 `IUnknown` 합니다. 성공 하면 `DWORD` 연결을 나타내는 쿠키가 반환 됩니다.

이벤트를 수신 하는 데 관심이 성공적으로 등록 되 면 소스 개체에서 발생 하는 이벤트에 따라 개체의 이벤트 인터페이스에 대 한 메서드가 호출 됩니다. 더 이상 이벤트를 수신 하지 않아도 되는 경우 [IConnectionPoint:: Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise)를 통해 다시 연결 지점에 쿠키를 전달할 수 있습니다. 이렇게 하면 원본 및 싱크 간의 연결이 끊어집니다.

이벤트를 처리할 때 참조 주기를 사용 하지 않도록 주의 해야 합니다.

## <a name="see-also"></a>참고 항목

[이벤트 처리](../atl/event-handling-and-atl.md)
