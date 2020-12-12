---
description: '자세히 알아보기: 창 없는 활성화 제공'
title: 창 없는 활성화 제공
ms.date: 11/04/2016
helpviewer_keywords:
- windowless activation of MFC ActiveX controls
- activation [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], activate options
- activation [MFC], windowless
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
ms.openlocfilehash: ea9b86c977926e57bd3593ec861498eb5d909f37
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248634"
---
# <a name="providing-windowless-activation"></a>창 없는 활성화 제공

창 생성 코드 (즉,를 호출할 때 발생 하는 모든 항목 `CreateWindow` )는 실행 비용이 많이 듭니다. 화면 상의 창을 유지 관리하는 컨트롤은 창에 대한 메시지를 관리해야 합니다. 따라서 창 없는 컨트롤은 창을 포함하는 컨트롤 보다 더 빠릅니다.

창 없는 컨트롤의 또 다른 장점은 창 있는 컨트롤과 달리 투명한 칠하기 및 비직사각형 화면 영역을 지원한다는 점입니다. 일반적인 투명한 컨트롤의 예는 투명한 배경의 텍스트 컨트롤입니다. 컨트롤은 배경이 아닌 텍스트를 칠합니다. 따라서 텍스트 아래에 무엇이 있든 배경이 통과해서 보여집니다. 새로운 폼에서는 화살표 및 원형 단추 등의 비직사각형 컨트롤이 자주 사용됩니다.

종종, 컨트롤은 고유 창이 필요하지 않으며, 컨테이너가 창 없는 개체를 지원하도록 작성된 경우, 대신 해당 컨테이너의 창 서비스를 사용할 수 있습니다. 창 없는 컨트롤은 이전 컨테이너와 호환됩니다. 창 없는 컨트롤을 지원하도록 작성되지 않은 오래된 컨테이너의 경우, 창 없는 컨트롤은 활성화될 때 창을 만듭니다.

창 없는 컨트롤은 고유 창을 갖지 않으므로 창 있는 컨테이너는 그렇지 않은 경우 컨트롤의 고유 창으로 제공되어야 할 서비스를 제공해야 합니다. 예를 들어 컨트롤이 키보드 포커스를 쿼리하거나, 마우스를 캡처하거나, 디바이스 컨텍스트를 가져와야 할 경우, 이러한 작업이 컨테이너에서 관리됩니다. 컨테이너는 `IOleInPlaceObjectWindowless` 인터페이스를 사용해서 해당 창에 전송된 사용자 입력 메시지를 적절한 창 없는 컨트롤로 라우팅합니다. 이 인터페이스에 대 한 설명은 *ACTIVEX SDK* 를 참조 하십시오. `COleControl` 멤버 함수는 컨테이너에서 이러한 서비스를 호출 합니다.

컨트롤이 창 없는 활성화를 사용 하도록 하려면 [COleControl:: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags)에서 반환 된 플래그 집합에 **windowlessActivate** 플래그를 포함 합니다. 예를 들어:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-windowless-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/cpp/providing-windowless-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-windowless-activation_3.cpp)]

MFC ActiveX 컨트롤 마법사의 [컨트롤 설정](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 페이지에서 **창 없는 활성화** 옵션을 선택한 경우이 플래그를 포함 하는 코드가 자동으로 생성 됩니다.

창 없는 활성화가 사용하도록 설정되었으면, 컨테이너가 입력 메시지를 컨트롤의 `IOleInPlaceObjectWindowless` 인터페이스에 위임합니다. 이 인터페이스에 대해 `COleControl`을 구현하면 마우스 좌표를 적절히 조정한 후 컨트롤의 메시지 맵을 통해 메시지가 분리됩니다. 해당 항목을 메시지 맵에 추가하여 일반적인 창 메시지와 같이 메시지를 처리할 수 있습니다. 이러한 메시지에 대 한 처리기에서 먼저 해당 값이 **NULL** 이 아닌지 확인 하지 않고 *m_hWnd* 멤버 변수 (또는이를 사용 하는 멤버 함수)를 사용 하지 않도록 합니다.

`COleControl`은 다음을 포함해서 마우스 캡처, 키보드 포커스, 스크롤 및 컨테이너의 다른 창 서비스를 호출하는 멤버 함수를 적절히 제공합니다.

- [GetFocus](../mfc/reference/colecontrol-class.md#getfocus), [SetFocus](../mfc/reference/colecontrol-class.md#setfocus)

- [Getcapture](../mfc/reference/colecontrol-class.md#getcapture), [setcapture](../mfc/reference/colecontrol-class.md#setcapture), [ReleaseCapture](../mfc/reference/colecontrol-class.md#releasecapture)

- [GetDC](../mfc/reference/colecontrol-class.md#getdc), [releasedc](../mfc/reference/colecontrol-class.md#releasedc)

- [InvalidateRgn](../mfc/reference/colecontrol-class.md#invalidatergn)

- [ScrollWindow](../mfc/reference/colecontrol-class.md#scrollwindow)

- [GetClientRect](../mfc/reference/colecontrol-class.md#getclientrect)

창 없는 컨트롤에서는 해당 `COleControl` 멤버 함수 또는 관련 Win32 API 함수 대신 항상 `CWnd` 멤버 함수를 사용해야 합니다.

창 없는 컨트롤을 OLE 끌어서 놓기 작업의 대상으로 지정할 수 있습니다. 일반적으로 이를 위해서는 컨트롤의 창이 놓기 대상으로 등록되어야 합니다. 컨트롤에는 고유 창이 없으므로 컨테이너가 고유 창을 놓기 대상으로 사용합니다. 컨트롤은 컨테이너가 적절한 시간에 호출을 위임할 수 있는 `IDropTarget` 인터페이스의 구현을 제공합니다. 컨테이너에이 인터페이스를 노출 하려면 [COleControl:: GetWindowlessDropTarget](../mfc/reference/colecontrol-class.md#getwindowlessdroptarget)를 재정의 합니다. 예를 들어:

[!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/cpp/providing-windowless-activation_4.cpp)]

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤: 최적화](../mfc/mfc-activex-controls-optimization.md)
