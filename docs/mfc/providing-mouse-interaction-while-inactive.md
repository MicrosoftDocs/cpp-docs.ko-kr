---
description: '자세히 알아보기: 비활성화 되어 있는 동안 마우스 상호 작용 제공'
title: 비활성 상태 중 마우스 상호 작용 제공
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
ms.openlocfilehash: bd3c069b052b58059de5f311e4ead795400d32fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248738"
---
# <a name="providing-mouse-interaction-while-inactive"></a>비활성 상태 중 마우스 상호 작용 제공

컨트롤이 즉시 활성화 되지 않을 경우 컨트롤에 자체 창이 없더라도 WM_SETCURSOR 및 WM_MOUSEMOVE 메시지를 처리 하는 것이 좋습니다. 이는 `COleControl` `IPointerInactive` 기본적으로 사용 하지 않도록 설정 된 인터페이스의 구현을 사용 하 여 수행할 수 있습니다. 이 인터페이스에 대 한 설명은 *ACTIVEX SDK* 를 참조 하십시오. 이를 사용 하도록 설정 하려면 [COleControl:: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags)에서 반환 된 플래그 집합에 pointerInactive 플래그를 포함 합니다.

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]

**MFC ActiveX 컨트롤 마법사** 를 사용 하 여 컨트롤을 만들 때 [컨트롤 설정](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 페이지에서 **비활성 상태일 때 마우스 포인터 알림** 옵션을 선택 하면이 플래그를 포함 하는 코드가 자동으로 생성 됩니다.

인터페이스를 `IPointerInactive` 사용 하도록 설정 하면 컨테이너는 WM_SETCURSOR을 위임 하 고 메시지를 WM_MOUSEMOVE 합니다. `COleControl`의 구현은 `IPointerInactive` 마우스 좌표를 적절 하 게 조정한 후 컨트롤의 메시지 맵을 통해 메시지를 디스패치합니다. 메시지 맵에 해당 항목을 추가 하 여 일반 창 메시지와 동일한 메시지를 처리할 수 있습니다. 이러한 메시지에 대 한 처리기에서 먼저 해당 값이 **NULL** 이 아닌지 확인 하지 않고 *m_hWnd* 멤버 변수 (또는이를 사용 하는 멤버 함수)를 사용 하지 않도록 합니다.

비활성 컨트롤을 OLE 끌어서 놓기 작업의 대상으로 지정할 수도 있습니다. 이렇게 하려면 컨트롤의 창을 놓기 대상으로 등록할 수 있도록 사용자가 개체를 끌 때 컨트롤을 활성화 해야 합니다. 끌기 중에 활성화가 발생 하도록 하려면 [COleControl:: GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)를 재정의 하 고 POINTERINACTIVE_ACTIVATEONDRAG 플래그를 반환 합니다.

[!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]

일반적으로 인터페이스를 사용 하도록 설정 `IPointerInactive` 하면 컨트롤에서 마우스 메시지를 항상 처리할 수 있습니다. 인터페이스를 지원 하지 않는 컨테이너에서이 동작을 가져오려면 컨트롤이 `IPointerInactive` 표시 될 때 항상 활성화 되어 있어야 합니다. 즉, 컨트롤에 기타 플래그 사이에 OLEMISC_ACTIVATEWHENVISIBLE 플래그가 포함 되어야 합니다. 그러나이 플래그를 지 원하는 컨테이너에서이 플래그를 적용 하지 않으려면 `IPointerInactive` OLEMISC_IGNOREACTIVATEWHENVISIBLE 플래그를 지정 하면 됩니다.

[!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤: 최적화](../mfc/mfc-activex-controls-optimization.md)
