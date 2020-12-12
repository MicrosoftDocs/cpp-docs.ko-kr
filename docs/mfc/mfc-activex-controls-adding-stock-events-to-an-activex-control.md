---
description: 'MFC ActiveX 컨트롤: ActiveX 컨트롤에 스톡 이벤트 추가에 대해 자세히 알아보세요.'
title: 'MFC ActiveX 컨트롤: ActiveX 컨트롤에 스톡 이벤트 추가'
ms.date: 11/04/2016
f1_keywords:
- EVENT__STOCK_ERROR
- EVENT__STOCK_READYSTATECHANGE
- ReadyStateChange
- EVENT__STOCK_MOUSEMOVE
- EVENT__STOCK_MOUSEUP
- EVENT__STOCK_DBLCLICK
- KeyPress
- EVENT__STOCK_KEYDOWN
- EVENT__STOCK
- EVENT__STOCK_MOUSEDOWN
- EVENT__STOCK_KEYPRESS
- EVENT__STOCK_CLICK
- EVENT__STOCK_KEYUP
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- KeyPress event
- FireDblClick event
- FireMouseDown event
- events [MFC], stock
- FireKeyPress event
- EVENT_STOCK_MOUSEMOVE event
- EVENT_STOCK_CLICK event
- FireClick event
- FireKeyUp event
- FireMouseUp event
- EVENT_STOCK_ERROREVENT event
- EVENT_STOCK_KEYDOWN event
- EVENT_STOCK_MOUSEDOWN event
- EVENT_STOCK_KEYPRESS macro [MFC]
- EVENT_STOCK_KEYUP event
- EVENT_STOCK_DBLCLICK event
- FireError event
- FireKeyDown event
- ReadyStateChange event
- EVENT_STOCK_MOUSEUP event
- FireMouseMove event
- EVENT_STOCK prefix
- EVENT_STOCK_READYSTATECHANGE event
- EVENT_STOCK_KEYPRESS event
ms.assetid: 3eeadc67-4b3d-4444-8caa-53054073988a
ms.openlocfilehash: e5b99ca2cd8675ab133f56d0e815abe0829867eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202901"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC ActiveX 컨트롤: ActiveX 컨트롤에 스톡 이벤트 추가

스톡 이벤트는 [COleControl](reference/colecontrol-class.md)클래스에서 자동으로 발생 한다는 점에서 사용자 지정 이벤트와 다릅니다. `COleControl` 일반적인 동작에서 발생 하는 이벤트를 발생 시키는 미리 정의 된 멤버 함수를 포함 합니다. 에서 구현 하는 몇 가지 일반적인 작업 `COleControl` 에는 컨트롤에 대 한 한 번 및 두 번 클릭, 키보드 이벤트 및 마우스 단추 상태의 변경 내용이 포함 됩니다. 스톡 이벤트의 이벤트 맵 항목 앞에는 항상 EVENT_STOCK 접두사가 옵니다.

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a> 이벤트 추가 마법사에서 지 원하는 스톡 이벤트

`COleControl`클래스는 다음 표에 나열 된 10 개의 스톡 이벤트를 제공 합니다. [이벤트 추가 마법사](../ide/adding-an-event-visual-cpp.md#add-event-wizard)를 사용 하 여 컨트롤에 원하는 이벤트를 지정할 수 있습니다.

### <a name="stock-events"></a>스톡 이벤트

|이벤트|실행 함수|의견|
|-----------|---------------------|--------------|
|사이드바에서|**void FireClick ()**|컨트롤에서 마우스를 캡처할 때 발생 합니다. 단추 **위로** (왼쪽, 중간 또는 오른쪽) 메시지가 수신 되 고 단추는 컨트롤을 통해 릴리스됩니다. 스톡 MouseDown 및 MouseUp 이벤트는이 이벤트 보다 먼저 발생 합니다.<br /><br /> 이벤트 맵 항목: **EVENT_STOCK_CLICK ()**|
|DblClick|**void FireDblClick ()**|클릭과 유사 하지만 **BUTTONDBLCLK** 메시지를 받을 때 발생 합니다.<br /><br /> 이벤트 맵 항목: **EVENT_STOCK_DBLCLICK ()**|
|오류|**void FireError (** * **lpcstr** , `lpszDescription` **UINT** `nHelpID` **= 0)**        |메서드 호출 또는 속성 액세스 범위 밖의 ActiveX 컨트롤 내에서 오류가 발생할 때 발생 합니다.<br /><br /> 이벤트 맵 항목: **EVENT_STOCK_ERROREVENT ()**|
|KeyDown|**void FireKeyDown (short** `nChar` **, short** `nShiftState` **)**      |`WM_SYSKEYDOWN`또는 메시지를 받을 때 발생 `WM_KEYDOWN` 합니다.<br /><br /> 이벤트 맵 항목: **EVENT_STOCK_KEYDOWN ()**|
|KeyPress|**Void FireKeyPress (short)** <strong>\*</strong> `pnChar` **)**    |메시지를 받을 때 발생 `WM_CHAR` 합니다.<br /><br /> 이벤트 맵 항목: **EVENT_STOCK_KEYPRESS ()**|
|KeyUp|**void FireKeyUp (short** `nChar` **, short** `nShiftState` **)**      |`WM_SYSKEYUP`또는 메시지를 받을 때 발생 `WM_KEYUP` 합니다.<br /><br /> 이벤트 맵 항목: **EVENT_STOCK_KEYUP ()**|
|MouseDown|**void FireMouseDown (short** `nButton` **, short** `nShiftState` **, float***x* **, float***y***)**          |**Buttondown** (left, 중간 또는 right)을 받는 경우 발생 합니다. 이 이벤트가 발생 하기 직전에 마우스가 캡처됩니다.<br /><br /> 이벤트 맵 항목: **EVENT_STOCK_MOUSEDOWN ()**|
|MouseMove|**void FireMouseMove (short** `nButton` **, short** `nShiftState` **, float***x* **, float***y***)**          |WM_MOUSEMOVE 메시지를 받을 때 발생 합니다.<br /><br /> 이벤트 맵 항목: **EVENT_STOCK_MOUSEMOVE ()**|
|System.windows.uielement.mouseup>|**void FireMouseUp (short** `nButton` **, short** `nShiftState` **, float***x* **, float***y***)**          |**Buttonup** (left, middle 또는 right)를 받는 경우 발생 합니다. 이 이벤트가 발생 하기 전에 마우스 캡처가 해제 됩니다.<br /><br /> 이벤트 맵 항목: **EVENT_STOCK_MOUSEUP ()**|
|ReadyStateChange|**void FireReadyStateChange ()**|수신 된 데이터의 양으로 인해 컨트롤이 다음 준비 상태로 전환 될 때 발생 합니다.<br /><br /> 이벤트 맵 항목: **EVENT_STOCK_READYSTATECHANGE ()**|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a> 이벤트 추가 마법사를 사용 하 여 스톡 이벤트 추가

실제 이벤트의 발생은 기본 클래스에 의해 자동으로 처리 되기 때문에 스톡 이벤트를 추가 하려면 사용자 지정 이벤트를 추가 하는 것 보다 더 많은 작업이 필요 `COleControl` 합니다. 다음 절차에서는 [MFC ActiveX 컨트롤 마법사](reference/mfc-activex-control-wizard.md)를 사용 하 여 개발 된 컨트롤에 스톡 이벤트를 추가 합니다. KeyPress 라는 이벤트는 키를 누르고 컨트롤이 활성화 될 때 발생 합니다. 이 프로시저를 사용 하 여 다른 스톡 이벤트를 추가할 수도 있습니다. 선택한 스톡 이벤트 이름을 키로 대체 합니다.

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>이벤트 추가 마법사를 사용 하 여 KeyPress 스톡 이벤트를 추가 하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. 클래스 뷰에서 ActiveX 컨트롤 클래스를 마우스 오른쪽 단추로 클릭 하 여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **이벤트 추가** 를 클릭 합니다.

   그러면 이벤트 추가 마법사가 열립니다.

1. **이벤트 이름** 드롭다운 목록에서을 선택 `KeyPress` 합니다.

1. **Finish** 를 클릭합니다.

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a> 스톡 이벤트에 대 한 이벤트 추가 마법사 변경

스톡 이벤트는 컨트롤의 기본 클래스에서 처리 되기 때문에 이벤트 추가 마법사는 어떤 방식으로든 클래스 선언을 변경 하지 않습니다. 컨트롤의 이벤트 맵에 이벤트를 추가 하 고에 항목을 만듭니다. IDL 파일. 다음 줄은 컨트롤 클래스 구현 ()에 있는 컨트롤의 이벤트 맵에 추가 됩니다. CPP) 파일:

[!code-cpp[NVC_MFC_AxUI#5](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

이 코드를 추가 하면 WM_CHAR 메시지를 받고 컨트롤이 활성화 될 때 KeyPress 이벤트가 발생 합니다. KeyPress 이벤트는 `FireKeyPress` 컨트롤 코드 내에서 발생 하는 함수 (예:)를 호출 하 여 다른 시간에 발생 시킬 수 있습니다.

이벤트 추가 마법사는 컨트롤의에 다음 코드 줄을 추가 합니다. IDL 파일:

[!code-cpp[NVC_MFC_AxUI#6](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

이 줄은 KeyPress 이벤트를 표준 디스패치 ID와 연결 하 고 컨테이너가 KeyPress 이벤트를 예상할 수 있도록 합니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)<br/>
[MFC ActiveX 컨트롤: 메서드](mfc-activex-controls-methods.md)<br/>
[COleControl 클래스](reference/colecontrol-class.md)
