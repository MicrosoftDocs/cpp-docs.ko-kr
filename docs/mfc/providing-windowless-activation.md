---
title: "창 없는 활성화 제공 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- windowless activation of MFC ActiveX controls
- activation [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], activate options
- activation [MFC], windowless
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb33f1dd9f8be8cb06cdfcc2aeecb653c2762410
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="providing-windowless-activation"></a>창 없는 활성화 제공
창 생성 코드 (호출할 때 발생 하는, 즉 모든 **CreateWindow**) 실행 하는 데 비용이 많이 듭니다. 화면 상의 창을 유지 관리하는 컨트롤은 창에 대한 메시지를 관리해야 합니다. 따라서 창 없는 컨트롤은 창을 포함하는 컨트롤 보다 더 빠릅니다.  
  
 창 없는 컨트롤의 또 다른 장점은 창 있는 컨트롤과 달리 투명한 칠하기 및 비직사각형 화면 영역을 지원한다는 점입니다. 일반적인 투명한 컨트롤의 예는 투명한 배경의 텍스트 컨트롤입니다. 컨트롤은 배경이 아닌 텍스트를 칠합니다. 따라서 텍스트 아래에 무엇이 있든 배경이 통과해서 보여집니다. 새로운 폼에서는 화살표 및 원형 단추 등의 비직사각형 컨트롤이 자주 사용됩니다.  
  
 종종, 컨트롤은 고유 창이 필요하지 않으며, 컨테이너가 창 없는 개체를 지원하도록 작성된 경우, 대신 해당 컨테이너의 창 서비스를 사용할 수 있습니다. 창 없는 컨트롤은 이전 컨테이너와 호환됩니다. 창 없는 컨트롤을 지원하도록 작성되지 않은 오래된 컨테이너의 경우, 창 없는 컨트롤은 활성화될 때 창을 만듭니다.  
  
 창 없는 컨트롤은 고유 창을 갖지 않으므로 창 있는 컨테이너는 그렇지 않은 경우 컨트롤의 고유 창으로 제공되어야 할 서비스를 제공해야 합니다. 예를 들어 컨트롤이 키보드 포커스를 쿼리하거나, 마우스를 캡처하거나, 장치 컨텍스트를 가져와야 할 경우, 이러한 작업이 컨테이너에서 관리됩니다. 컨테이너는 `IOleInPlaceObjectWindowless` 인터페이스를 사용해서 해당 창에 전송된 사용자 입력 메시지를 적절한 창 없는 컨트롤로 라우팅합니다. (참조는 *ActiveX SDK* 이 인터페이스의 설명에 대 한 합니다.) `COleControl` 멤버 함수는 컨테이너에서 이러한 서비스를 호출 합니다.  
  
 창 없는 활성화를 사용 하 여 컨트롤을 포함 된 **windowlessActivate** 에서 반환 하는 플래그 집합에서 플래그 [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags)합니다. 예:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-windowless-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/cpp/providing-windowless-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-windowless-activation_3.cpp)]  
  
 선택 하는 경우이 플래그를 포함 하는 코드는 자동으로 생성 됩니다는 **창 없는 활성화** 옵션에 [제어 설정](../mfc/reference/control-settings-mfc-activex-control-wizard.md) MFC ActiveX 컨트롤 마법사의 페이지입니다.  
  
 창 없는 활성화가 사용하도록 설정되었으면, 컨테이너가 입력 메시지를 컨트롤의 `IOleInPlaceObjectWindowless` 인터페이스에 위임합니다. 이 인터페이스에 대해 `COleControl`을 구현하면 마우스 좌표를 적절히 조정한 후 컨트롤의 메시지 맵을 통해 메시지가 분리됩니다. 해당 항목을 메시지 맵에 추가하여 일반적인 창 메시지와 같이 메시지를 처리할 수 있습니다. 이러한 메시지에 대 한 처리기를 사용 하지 않습니다는 `m_hWnd` 멤버 변수 (또는 모든 멤버 함수를 사용)이 아닌 값 아님을 **NULL**합니다.  
  
 `COleControl`은 다음을 포함해서 마우스 캡처, 키보드 포커스, 스크롤 및 컨테이너의 다른 창 서비스를 호출하는 멤버 함수를 적절히 제공합니다.  
  
-   [포커스 받기](../mfc/reference/colecontrol-class.md#getfocus), [SetFocus](../mfc/reference/colecontrol-class.md#setfocus)  
  
-   [GetCapture](../mfc/reference/colecontrol-class.md#getcapture), [SetCapture](../mfc/reference/colecontrol-class.md#setcapture), [ReleaseCapture](../mfc/reference/colecontrol-class.md#releasecapture)  
  
-   [GetDC](../mfc/reference/colecontrol-class.md#getdc), [ReleaseDC](../mfc/reference/colecontrol-class.md#releasedc)  
  
-   [InvalidateRgn](../mfc/reference/colecontrol-class.md#invalidatergn)  
  
-   [ScrollWindow](../mfc/reference/colecontrol-class.md#scrollwindow)  
  
-   [GetClientRect](../mfc/reference/colecontrol-class.md#getclientrect)  
  
 창 없는 컨트롤에서는 해당 `COleControl` 멤버 함수 또는 관련 Win32 API 함수 대신 항상 `CWnd` 멤버 함수를 사용해야 합니다.  
  
 창 없는 컨트롤을 OLE 끌어서 놓기 작업의 대상으로 지정할 수 있습니다. 일반적으로 이를 위해서는 컨트롤의 창이 놓기 대상으로 등록되어야 합니다. 컨트롤에는 고유 창이 없으므로 컨테이너가 고유 창을 놓기 대상으로 사용합니다. 컨트롤은 컨테이너가 적절한 시간에 호출을 위임할 수 있는 `IDropTarget` 인터페이스의 구현을 제공합니다. 이 인터페이스를 컨테이너에 노출 하기 위해 재정의 [colecontrol:: Getwindowlessdroptarget](../mfc/reference/colecontrol-class.md#getwindowlessdroptarget)합니다. 예:  
  
 [!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/cpp/providing-windowless-activation_4.cpp)]  
  
## <a name="see-also"></a>참고 항목  
 [MFC ActiveX 컨트롤: 최적화](../mfc/mfc-activex-controls-optimization.md)

