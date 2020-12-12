---
description: '자세한 정보: 연결 요소 클래스'
title: 연결 요소 클래스 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
ms.openlocfilehash: 28d41f15aeafd98c8c9bcac27fde25d0b2037765
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148241"
---
# <a name="connection-points-classes"></a>연결 요소 클래스

다음 클래스는 연결 지점의 지원 기능을 제공 합니다.

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) 연결 지점 컨테이너를 구현 합니다.

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 연결 지점을 구현 합니다.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) 인터페이스를 나타내는 연결 지점을 구현 합니다.

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) 연결 지점과 해당 싱크 간의 무제한 연결을 관리 합니다.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) 연결 지점과 해당 싱크 간에 고정 된 수의 연결을 관리 합니다.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) 개체의 속성이 변경 되었거나 변경 될 것으로 클라이언트 싱크에 알립니다.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) ATL COM 개체에 대 한 연결 지점의 지원 기능을 제공 합니다. 이러한 연결 지점은 COM 개체에서 제공 하는 이벤트 싱크 맵과 함께 매핑됩니다.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 는 클래스의 이벤트 싱크 맵과 함께 작동 하 여 이벤트를 적절 한 처리기 함수로 라우팅합니다.

## <a name="related-articles"></a>관련 문서

[연결 요소](../atl/atl-connection-points.md)

[이벤트 처리 및 ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>참고 항목

[클래스 개요](../atl/atl-class-overview.md)<br/>
[연결 지점 매크로](../atl/reference/connection-point-macros.md)<br/>
[연결 지점 전역 함수](../atl/reference/connection-point-global-functions.md)
