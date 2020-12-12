---
description: '자세한 정보: ATL 연결 지점의'
title: ATL 연결 지점
ms.date: 11/04/2016
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
ms.openlocfilehash: 60b9018185bea2af26407ee9d7a203148c8dc477
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165825"
---
# <a name="atl-connection-points"></a>ATL 연결 지점

연결 가능 개체는 송신 인터페이스를 지원합니다. 송신 인터페이스에서는 개체가 클라이언트와 통신할 수 있습니다. 연결 가능 개체는 각 송신 인터페이스에 대해 연결 지점을 노출합니다. 각 송신 인터페이스는 싱크라는 개체에서 클라이언트에 의해 구현됩니다.

![연결 지점](../atl/media/vc2zw31.gif "연결 지점")

각 연결 지점은 [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) 인터페이스를 지원 합니다. 연결 가능 개체는 [IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer) 인터페이스를 통해 해당 연결 요소를 클라이언트에 노출 합니다.

## <a name="in-this-section"></a>섹션 내용

[ATL 연결 지점 클래스](../atl/atl-connection-point-classes.md)<br/>
연결 지점을 지원하는 ATL 클래스에 대해 간략하게 설명합니다.

[개체에 연결 요소 추가](../atl/adding-connection-points-to-an-object.md)<br/>
개체에 연결 지점을 추가하는 데 사용되는 단계에 대해 설명합니다.

[ATL 연결 지점 예제](../atl/atl-connection-point-example.md)<br/>
연결 지점 선언 예제를 제공합니다.

## <a name="related-sections"></a>관련 단원

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
액티브 템플릿 라이브러리를 사용하여 프로그래밍하는 방법에 대한 개념 항목의 링크를 제공합니다.

## <a name="see-also"></a>참고 항목

[개념](../atl/active-template-library-atl-concepts.md)
