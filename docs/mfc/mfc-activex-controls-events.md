---
description: '자세한 정보: MFC ActiveX 컨트롤: 이벤트'
title: 'MFC ActiveX 컨트롤: 이벤트'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- notifications [MFC], notifying containers of events
- custom events [MFC], adding to ActiveX controls
- events [MFC], mapping
- COleControl class [MFC], handling of events
- mappings [MFC], events
- stock events [MFC]
- container events [MFC]
- events [MFC], ActiveX controls
- OLE events [MFC]
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
ms.openlocfilehash: 8a360931287432e9f0ee0fc55e7e5120bcbd390f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240691"
---
# <a name="mfc-activex-controls-events"></a>MFC ActiveX 컨트롤: 이벤트

ActiveX 컨트롤은 이벤트를 사용 하 여 컨트롤에 문제가 발생 했음을 컨테이너에 알립니다. 이벤트의 일반적인 예로는 컨트롤 클릭, 키보드를 사용 하 여 입력 한 데이터, 컨트롤 상태 변경 등이 있습니다. 이러한 작업이 발생 하면 컨트롤은 이벤트를 발생 하 여 컨테이너에 경고 합니다.

이벤트를 메시지 라고도 합니다.

MFC는 스톡 및 사용자 지정의 두 가지 이벤트를 지원 합니다. 스톡 이벤트는 [COleControl](reference/colecontrol-class.md) 클래스가 자동으로 처리 하는 이벤트입니다. 주식 이벤트의 전체 목록은 [MFC ActiveX 컨트롤: 스톡 이벤트 추가](mfc-activex-controls-adding-stock-events-to-an-activex-control.md)문서를 참조 하세요. 사용자 지정 이벤트를 사용 하면 해당 컨트롤과 관련 된 동작이 발생할 때 컨테이너에 알리는 기능을 제어할 수 있습니다. 일부 예는 컨트롤의 내부 상태가 변경 되거나 특정 창 메시지를 수신 하는 경우입니다.

컨트롤에서 이벤트를 제대로 발생 시키려면 컨트롤 클래스가 관련 이벤트가 발생할 때 호출 되어야 하는 멤버 함수에 컨트롤의 각 이벤트를 매핑해야 합니다. 이 매핑 메커니즘 (이벤트 맵 이라고 함)은 이벤트에 대 한 정보를 중앙 집중화 하 고 Visual Studio가 컨트롤의 이벤트를 쉽게 액세스 하 고 조작할 수 있도록 합니다. 이 이벤트 맵은 헤더에 있는 다음 매크로에 의해 선언 됩니다. H) 컨트롤 클래스 선언의 파일입니다.

[!code-cpp[NVC_MFC_AxUI#2](codesnippet/cpp/mfc-activex-controls-events_1.h)]

이벤트 맵이 선언 된 후에는 컨트롤의 구현 ()에서 정의 되어야 합니다. CPP) 파일입니다. 다음 코드 줄은 이벤트 맵을 정의 하 여 컨트롤이 특정 이벤트를 발생 시킬 수 있도록 합니다.

[!code-cpp[NVC_MFC_AxUI#3](codesnippet/cpp/mfc-activex-controls-events_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#4](codesnippet/cpp/mfc-activex-controls-events_3.cpp)]

MFC ActiveX 컨트롤 마법사를 사용 하 여 프로젝트를 만드는 경우 이러한 줄이 자동으로 추가 됩니다. MFC ActiveX 컨트롤 마법사를 사용 하지 않는 경우 이러한 줄을 수동으로 추가 해야 합니다.

클래스 뷰를 사용 하 여 클래스 `COleControl` 또는 정의한 사용자 지정 이벤트에서 지 원하는 스톡 이벤트를 추가할 수 있습니다. 각 새 이벤트에 대해 클래스 뷰는 컨트롤의 이벤트 맵과 컨트롤의에 적절 한 항목을 자동으로 추가 합니다. IDL 파일.

다른 두 문서에서는 이벤트에 대해 자세히 설명 합니다.

- [MFC ActiveX 컨트롤: 스톡 이벤트 추가](mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [MFC ActiveX 컨트롤: 사용자 지정 이벤트 추가](mfc-activex-controls-adding-custom-events.md)

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)<br/>
[MFC ActiveX 컨트롤: 메서드](mfc-activex-controls-methods.md)<br/>
[COleControl 클래스](reference/colecontrol-class.md)
