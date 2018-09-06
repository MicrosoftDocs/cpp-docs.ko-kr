---
title: 연결 지점 클래스 (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.connection
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e24d6333faee842227edb09ea05aa6a1f8b0d9a0
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763603"
---
# <a name="connection-points-classes"></a>연결 지점 클래스

연결 지점에 대 한 지원을 제공 하는 다음 클래스:

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) 연결 지점 컨테이너를 구현 합니다.

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 연결 지점을 구현 합니다.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) 연결 지점을 나타내는 구현 합니다 [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) 인터페이스입니다.

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) 연결 지점 및 해당 싱크 간의 무제한 연결을 관리 합니다.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) 고정된 된 수의 연결 지점 및 해당 싱크 간의 연결을 관리 합니다.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) 개체 속성 변경 되었거나 변경 되려고 하는 클라이언트의 싱크를에 알립니다.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) ATL COM 개체에 대 한 연결 지점에 대 한 지원을 제공 합니다. 이러한 연결점은 COM 개체에서 제공 하는 이벤트 싱크 맵과 매핑됩니다.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 에 적절 한 처리기 함수로 이벤트를 라우팅하도록 클래스에서 이벤트 싱크 함께 매핑합니다.

## <a name="related-articles"></a>관련 문서

[연결 지점](../atl/atl-connection-points.md)

[이벤트 처리 및 ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>참고 항목

[클래스 개요](../atl/atl-class-overview.md)   
[연결 지점 매크로](../atl/reference/connection-point-macros.md)   
[연결 지점 전역 함수](../atl/reference/connection-point-global-functions.md)

