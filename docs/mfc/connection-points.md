---
description: '자세한 정보: 연결 요소'
title: 연결 지점
ms.date: 11/19/2018
f1_keywords:
- IConnectionPoint
helpviewer_keywords:
- IConnectionPoint interface
- connections, connection points
- OLE COM connection points
- MFC COM, connection points
- COM, connection points
- interfaces, IConnectionPoint
- MFC, COM support
- connection points [MFC]
- CCmdTarget class [MFC], and connection points
- sinks, connection points
ms.assetid: bc9fd7c7-8df6-4752-ac8c-0b177442c88d
ms.openlocfilehash: 721f35ea1737bf8e49f8b802b5382687a848c084
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310553"
---
# <a name="connection-points"></a>연결 지점

이 문서에서는 MFC 클래스 및를 사용 하 여 연결 요소 (이전의 OLE 연결점)를 구현 하는 방법을 설명 합니다 `CCmdTarget` `CConnectionPoint` .

이전에 COM (구성 요소 개체 모델)은 `IUnknown::QueryInterface` 개체가 인터페이스에서 기능을 구현 하 고 노출할 수 있도록 하는 일반적인 메커니즘 (*)을 정의 했습니다. 그러나 개체가 특정 인터페이스를 호출 하는 기능을 노출 하도록 허용 하는 해당 메커니즘은 정의 되지 않았습니다. 즉, COM은 개체에 대 한 들어오는 포인터 (해당 개체의 인터페이스에 대 한 포인터)가 처리 되었지만 나가는 인터페이스에 대 한 명시적 모델이 없는 경우 (개체가 다른 개체의 인터페이스에 대 한 포인터)를 정의 했습니다. 이제 COM에는이 기능을 지 원하는 연결 요소 라고 하는 모델이 있습니다.

연결에는 인터페이스를 호출 하는 개체 (소스 라고 함)와 인터페이스를 구현 하는 개체 (싱크 라고 함) 라는 두 부분이 있습니다. 연결 지점은 원본에서 노출 하는 인터페이스입니다. 원본에서 연결 지점을 노출 하 여 싱크는 자체 (원본)에 대 한 연결을 설정할 수 있습니다. 연결 지점 메커니즘 ( `IConnectionPoint` 인터페이스)을 통해 싱크 인터페이스에 대 한 포인터가 원본 개체에 전달 됩니다. 이 포인터는 소스에 멤버 함수 집합의 싱크 구현에 대 한 액세스를 제공 합니다. 예를 들어 싱크에 의해 구현 되는 이벤트를 발생 시키려면 소스가 싱크의 구현에 적절 한 메서드를 호출할 수 있습니다. 다음 그림은 위에서 설명한 연결 지점을 보여 줍니다.

![구현된 연결 지점](../mfc/media/vc37lh1.gif "구현된 연결 지점") <br/>
구현된 연결 지점

MFC는 [CConnectionPoint](reference/cconnectionpoint-class.md) 및 [ccmdtarget](reference/ccmdtarget-class.md) 클래스에서이 모델을 구현 합니다. 에서 파생 된 클래스 `CConnectionPoint` `IConnectionPoint` 는 다른 개체에 대 한 연결 요소를 노출 하는 데 사용 되는 인터페이스를 구현 합니다. 에서 파생 된 클래스는 `CCmdTarget` `IConnectionPointContainer` 개체의 사용 가능한 모든 연결 지점을 열거 하거나 특정 연결 지점을 찾을 수 있는 인터페이스를 구현 합니다.

클래스에서 구현 되는 각 연결 지점에 대해 연결 지점을 구현 하는 연결 부분을 선언 해야 합니다. 하나 이상의 연결 지점은 구현 하는 경우 클래스에서 단일 연결 맵도 선언 해야 합니다. 연결 맵은 ActiveX 컨트롤에서 지 원하는 연결 지점의 테이블입니다.

다음 예에서는 간단한 연결 맵과 하나의 연결 지점을 보여 줍니다. 첫 번째 예제에서는 연결 맵과 점을 선언 합니다. 두 번째 예제에서는 맵과 점을 구현 합니다. 는 `CMyClass` 파생 클래스 여야 합니다 `CCmdTarget` . 첫 번째 예제에서 코드는 클래스 선언에서 섹션 아래에 삽입 됩니다 **`protected`** .

[!code-cpp[NVC_MFCConnectionPoints#1](codesnippet/cpp/connection-points_1.h)]

**BEGIN_CONNECTION_PART** 및 **END_CONNECTION_PART** 매크로는 `XSampleConnPt` `CConnectionPoint` 이 특정 연결 지점을 구현 하는 포함 클래스 (에서 파생 됨)를 선언 합니다. `CConnectionPoint`멤버 함수를 재정의 하거나 고유한 멤버 함수를 추가 하려면 이러한 두 매크로 사이에 멤버 함수를 선언 합니다. 예를 들어 `CONNECTION_IID` 매크로는 `CConnectionPoint::GetIID` 두 매크로 사이에 배치 될 때 멤버 함수를 재정의 합니다.

두 번째 예제에서는 코드를 컨트롤의 구현 파일 (.cpp 파일)에 삽입 합니다. 이 코드는 연결 지점을 포함 하는 연결 맵을 구현 합니다 `SampleConnPt` .

[!code-cpp[NVC_MFCConnectionPoints#2](codesnippet/cpp/connection-points_2.cpp)]

클래스에 연결 지점이 둘 이상 있는 경우 **BEGIN_CONNECTION_MAP** 와 **END_CONNECTION_MAP** 매크로 사이에 **CONNECTION_PART** 매크로를 추가로 삽입 합니다.

마지막으로 클래스의 생성자에서에 대 한 호출을 추가 `EnableConnections` 합니다. 예를 들어:

[!code-cpp[NVC_MFCConnectionPoints#3](codesnippet/cpp/connection-points_3.cpp)]

이 코드가 삽입 되 면 `CCmdTarget` 파생 클래스는 인터페이스에 대 한 연결 지점을 노출 `ISampleSink` 합니다. 다음 그림에서는이 예제를 보여 줍니다.

![MFC를 사용하여 구현된 연결 지점](../mfc/media/vc37lh2.gif "MFC를 사용하여 구현된 연결 지점") <br/>
MFC를 사용 하 여 구현 된 연결 지점

일반적으로 연결 지점은 동일한 인터페이스에 연결 된 여러 싱크에 브로드캐스트할 수 있는 "멀티 캐스팅"을 지원 합니다. 다음 예제 조각에서는 연결 지점에서 각 싱크를 반복 하 여 멀티 캐스트 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFCConnectionPoints#4](codesnippet/cpp/connection-points_4.cpp)]

이 예에서는를 호출 하 여 연결 지점에서 현재 연결 집합을 검색 `SampleConnPt` `CConnectionPoint::GetConnections` 합니다. 그런 다음 `ISampleSink::SinkFunc` 모든 활성 연결에 대 한 연결 및 호출을 반복 합니다.

## <a name="see-also"></a>참고 항목

[MFC COM](mfc-com.md)
