---
description: '자세한 정보: ATL 연결 지점 클래스'
title: ATL 연결 지점 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
ms.openlocfilehash: af3b52715d7aeca13a711557bdba2c9428d4bff5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165851"
---
# <a name="atl-connection-point-classes"></a>ATL 연결 지점 클래스

ATL은 다음 클래스를 사용 하 여 연결 요소를 지원 합니다.

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 는 연결 지점을 구현 합니다. 이 클래스에서 나타내는 나가는 인터페이스의 IID는 템플릿 매개 변수로 전달 됩니다.

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) 는 연결 지점 컨테이너를 구현 하 고 개체의 목록을 관리 합니다 `IConnectionPointImpl` .

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) 는 [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) 인터페이스를 나타내는 연결 지점을 구현 합니다.

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) 는 연결 지점과 해당 싱크 사이의 임의 연결 수를 관리 합니다.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) 는 템플릿 매개 변수에 지정 된 대로 미리 정의 된 수의 연결을 관리 합니다.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) 는 개체의 속성이 변경 되었거나 변경 될 것으로 클라이언트 싱크에 알립니다.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 는 ATL COM 개체에 대 한 연결 지점의 지원 기능을 제공 합니다. 이러한 연결 지점은 COM 개체에서 제공 하는 이벤트 싱크 맵과 함께 매핑됩니다.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 는 클래스의 이벤트 싱크 맵과 함께 작동 하 여 이벤트를 적절 한 처리기 함수로 라우팅합니다.

## <a name="see-also"></a>참고 항목

[연결점](../atl/atl-connection-points.md)
