---
description: '자세한 정보: MFC ActiveX 컨트롤: 사용자 지정 이벤트 추가'
title: 'MFC ActiveX 컨트롤: 사용자 지정 이벤트 추가'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], events [MFC]
- EVENT_CUSTOM prefix [MFC]
- custom events [MFC], adding to ActiveX controls
- EVENT_CUSTOM macro [MFC]
- InCircle method [MFC]
- ClickIn event
- FireClickIn event
- COleControl class [MFC], custom events [MFC]
- Click event, custom events [MFC]
- events [MFC], ActiveX controls
- custom events [MFC]
- FireEvent method, adding custom events
ms.assetid: c584d053-1e34-47aa-958e-37d3e9b85892
ms.openlocfilehash: 1c41db073e5cfd74861a1ca836916c2b4bfdc9b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203044"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC ActiveX 컨트롤: 사용자 지정 이벤트 추가

사용자 지정 이벤트는 클래스에 의해 자동으로 발생 하지 않는의 스톡 이벤트와 다릅니다 `COleControl` . 사용자 지정 이벤트는 컨트롤 개발자에 의해 결정 되는 특정 작업을 이벤트로 인식 합니다. 사용자 지정 이벤트에 대 한 이벤트 맵 항목은 EVENT_CUSTOM 매크로로 표시 됩니다. 다음 섹션에서는 ActiveX 컨트롤 마법사를 사용 하 여 만든 ActiveX 컨트롤 프로젝트에 대 한 사용자 지정 이벤트를 구현 합니다.

## <a name="adding-a-custom-event-with-the-add-event-wizard"></a><a name="_core_adding_a_custom_event_with_classwizard"></a> 이벤트 추가 마법사를 사용 하 여 사용자 지정 이벤트 추가

다음 절차에서는 특정 사용자 지정 이벤트 ClickIn를 추가 합니다. 이 절차를 사용 하 여 다른 사용자 지정 이벤트를 추가할 수 있습니다. ClickIn 이벤트 이름 및 매개 변수에 대 한 사용자 지정 이벤트 이름 및 매개 변수를 대체 합니다.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>이벤트 추가 마법사를 사용 하 여 ClickIn 사용자 지정 이벤트를 추가 하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. **클래스 뷰** 에서 ActiveX 컨트롤 클래스를 마우스 오른쪽 단추로 클릭 하 여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **이벤트 추가** 를 클릭 합니다.

   그러면 이벤트 추가 마법사가 열립니다.

1. **이벤트 이름** 상자에서 먼저 기존 이벤트를 선택 하 고 **사용자 지정** 라디오 단추를 클릭 한 다음 *ClickIn* 을 입력 합니다.

1. **내부 이름** 상자에 이벤트의 발생 함수 이름을 입력 합니다. 이 예에서는 이벤트 추가 마법사 ()에서 제공 하는 기본값을 사용 `FireClickIn` 합니다.

1. 매개 변수 **이름** 및 **매개 변수 형식** 컨트롤을 사용 하 여 *xCoord* (형식 *OLE_XPOS_PIXELS*) 이라는 매개 변수를 추가 합니다.

1. *YCoord* (type *OLE_YPOS_PIXELS*) 라는 두 번째 매개 변수를 추가 합니다.

1. **마침** 을 클릭 하 여 이벤트를 만듭니다.

## <a name="add-event-wizard-changes-for-custom-events"></a><a name="_core_classwizard_changes_for_custom_events"></a> 사용자 지정 이벤트에 대 한 이벤트 추가 마법사 변경

사용자 지정 이벤트를 추가 하면 이벤트 추가 마법사가 컨트롤 클래스를 변경 합니다. H,. CPP, 및 IDL 파일. 다음 코드 샘플은 ClickIn 이벤트와 관련 되어 있습니다.

헤더에는 다음 줄이 추가 됩니다. H) 컨트롤 클래스의 파일:

[!code-cpp[NVC_MFC_AxUI#7](codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

이 코드 `FireClickIn` 는 이벤트 추가 마법사를 사용 하 여 정의한 ClickIn 이벤트와 매개 변수를 사용 하 여 [COleControl:: FireEvent](reference/colecontrol-class.md#fireevent) 를 호출 하는 라는 인라인 함수를 선언 합니다.

또한 다음 줄은 구현 ()에 있는 컨트롤에 대 한 이벤트 맵에 추가 됩니다. CPP) 컨트롤 클래스의 파일입니다.

[!code-cpp[NVC_MFC_AxUI#8](codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

이 코드는 이벤트 ClickIn를 인라인 함수에 매핑하고 `FireClickIn` 이벤트 추가 마법사를 사용 하 여 정의한 매개 변수를 전달 합니다.

마지막으로 다음 줄이 컨트롤의에 추가 됩니다. IDL 파일:

[!code-cpp[NVC_MFC_AxUI#9](codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

이 줄은 이벤트 추가 마법사 이벤트 목록의 이벤트 위치에서 가져온 특정 ID 번호를 ClickIn 이벤트에 할당 합니다. 이벤트 목록의 항목을 통해 컨테이너는 이벤트를 예상할 수 있습니다. 예를 들어 이벤트가 발생 하는 경우 실행 되는 처리기 코드를 제공할 수 있습니다.

## <a name="calling-fireclickin"></a><a name="_core_calling_fireclickin"></a> FireClickIn 호출

이벤트 추가 마법사를 사용 하 여 ClickIn 사용자 지정 이벤트를 추가 했으므로이 이벤트를 발생 시킬 시기를 결정 해야 합니다. 이렇게 하려면 `FireClickIn` 적절 한 작업이 발생할 때를 호출 합니다. 이 설명에서 컨트롤은 메시지 처리기 내에서 함수를 사용 하 여 `InCircle` `WM_LBUTTONDOWN` 사용자가 원형 또는 원형 영역 내부를 클릭할 때 ClickIn 이벤트를 발생 시킵니다. 다음 절차에서는 처리기를 추가 합니다 `WM_LBUTTONDOWN` .

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>이벤트 추가 마법사를 사용 하 여 메시지 처리기를 추가 하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. **클래스 뷰** 에서 ActiveX 컨트롤 클래스를 선택 합니다.

1. **속성** 창에 ActiveX 컨트롤에서 처리할 수 있는 메시지의 목록이 표시 됩니다. 굵게 표시 된 모든 메시지에는 이미 할당 된 처리기 함수가 있습니다.

1. 처리 하려는 메시지를 선택 합니다. 이 예에서는를 선택 `WM_LBUTTONDOWN` 합니다.

1. 오른쪽의 드롭다운 목록 상자에서 **\<Add> onlbuttondown** 을 선택 합니다.

1. **클래스 뷰** 에서 새 처리기 함수를 두 번 클릭 하 여 구현 (의 메시지 처리기 코드로 이동 합니다. CPP) 파일을 관리 합니다.

다음 코드 샘플은 `InCircle` 컨트롤 창에서 마우스 왼쪽 단추를 클릭할 때마다 함수를 호출 합니다. 이 샘플은 `WM_LBUTTONDOWN` `OnLButtonDown` [Circ 샘플](../overview/visual-cpp-samples.md) abstract의 처리기 함수에서 찾을 수 있습니다.

[!code-cpp[NVC_MFC_AxUI#10](codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
> 이벤트 추가 마법사에서 마우스 단추 동작에 대 한 메시지 처리기를 만들 때 기본 클래스의 동일한 메시지 처리기에 대 한 호출이 자동으로 추가 됩니다. 이 호출을 제거 하지 마십시오. 컨트롤에서 스톡 마우스 메시지를 사용 하는 경우 기본 클래스의 메시지 처리기를 호출 하 여 마우스 캡처가 제대로 처리 되도록 해야 합니다.

다음 예제에서 이벤트는 컨트롤이 컨트롤 내의 원형 또는 원형 영역 내부에서 발생 하는 경우에만 발생 합니다. 이 동작을 수행 하기 위해 `InCircle` 컨트롤의 구현 ()에 함수를 추가할 수 있습니다. CPP) 파일:

[!code-cpp[NVC_MFC_AxUI#11](codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

또한 다음 `InCircle` 함수 선언을 컨트롤의 헤더 (에 추가 해야 합니다. H) 파일:

[!code-cpp[NVC_MFC_AxUI#12](codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

## <a name="custom-events-with-stock-names"></a><a name="_core_custom_events_with_stock_names"></a> 재고 이름이 있는 사용자 지정 이벤트

스톡 이벤트와 동일한 이름을 사용 하 여 사용자 지정 이벤트를 만들 수 있지만 동일한 컨트롤에서 둘 다를 구현할 수는 없습니다. 예를 들어, 스톡 이벤트 클릭이 일반적으로 발생 될 때 발생 하지 않는 클릭 이라는 사용자 지정 이벤트를 만들 수 있습니다. 그런 다음 발생 하는 함수를 호출 하 여 언제 든 지 Click 이벤트를 발생 시킬 수 있습니다.

다음 절차에서는 사용자 지정 Click 이벤트를 추가 합니다.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>스톡 이벤트 이름을 사용 하는 사용자 지정 이벤트를 추가 하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. **클래스 뷰** 에서 ActiveX 컨트롤 클래스를 마우스 오른쪽 단추로 클릭 하 여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **이벤트 추가** 를 클릭 합니다.

   그러면 이벤트 추가 마법사가 열립니다.

1. **이벤트 이름** 드롭다운 목록에서 스톡 이벤트 이름을 선택 합니다. 이 예에서는 **클릭** 을 선택 합니다.

1. **이벤트 유형** 으로 **사용자 지정** 을 선택 합니다.

1. **마침** 을 클릭 하 여 이벤트를 만듭니다.

1. `FireClick`코드의 적절 한 위치에서를 호출 합니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)<br/>
[MFC ActiveX 컨트롤: 메서드](mfc-activex-controls-methods.md)<br/>
[COleControl 클래스](reference/colecontrol-class.md)
