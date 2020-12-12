---
description: '자세히 알아보기: AFX 메시지'
title: AFX 메시지
ms.date: 11/04/2016
f1_keywords:
- SB_LINELEFT
- SB_THUMBTRACK
- AFX_TOOLTIP_TYPE_EDIT
- AFX_WM_ON_HSCROLL
- SB_PAGERIGHT
- AFX_WM_RESETPROMPT
- AFX_WM_CHANGE_RIBBON_CATEGORY
- AFX_TOOLTIP_TYPE_MINIFRAME
- AFX_WM_CUSTOMIZETOOLBAR
- AFX_WM_CHANGE_ACTIVE_TAB
- AFX_WM_ACCGETOBJECT
- AFX_WM_TOOLBARMENU
- AFX_TOOLTIP_TYPE_DOCKBAR
- AFX_WM_CUSTOMIZEHELP
- AFX_WM_ON_GET_TAB_TOOLTIP
- AFX_WM_ON_RIBBON_CUSTOMIZE
- AFX_WM_ON_DRAGCOMPLETE
- AFX_WM_RESETTOOLBAR
- AFX_WM_ON_MOVETOTABGROUP
- AFX_WM_CHECKEMPTYMINIFRAME
- AFX_WM_GETDOCUMENTCOLORS
- SB_RIGHT
- AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU
- AFX_WM_ACCGETSTATE
- SB_PAGELEFT
- SB_ENDSCROLL
- AFX_WM_ON_CANCELTABMOVE
- AFX_TOOLTIP_TYPE_TAB
- AFX_WM_WINDOW_HELP
- AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM
- AFX_WM_SHOWREGULARMENU
- AFX_TOOLTIP_TYPE_TOOLBAR
- AFX_WM_CHANGE_CURRENT_FOLDER
- AFX_WM_UPDATETOOLTIPS
- AFX_WM_ON_MOVE_TAB
- AFX_WM_CHANGING_ACTIVE_TAB
- AFX_WM_RESETMENU
- AFX_WM_GETDRAGBOUNDS
- AFX_WM_RESETCONTEXTMENU
- AFX_TOOLTIP_TYPE_BUTTON
- AFX_WM_ON_CLOSEPOPUPWINDOW
- AFX_TOOLTIP_TYPE_TOOLBOX
- AFX_WM_CHANGEVISUALMANAGER
- SB_LINERIGHT
- AFX_WM_ON_RENAME_TAB
- AFX_TOOLTIP_TYPE_DEFAULT
- AFX_WM_ON_TABGROUPMOUSEMOVE
- SB_LEFT
- AFX_WM_DELETETOOLBAR
- AFX_WM_PROPERTY_CHANGED
- AFX_TOOLTIP_TYPE_ALL
- AFX_WM_ACCHITTEST
- AFX_WM_ON_AFTER_SHELL_COMMAND
- AFX_WM_ON_PRESS_CLOSE_BUTTON
- AFX_WM_RESETKEYBOARD
- AFX_WM_ON_MOVETABCOMPLETE
- AFX_WM_CREATETOOLBAR
- SB_THUMBPOSITION
- AFX_WM_POSTSETPREVIEWFRAME
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
ms.openlocfilehash: edda0bffd7077a9898a83ff1a530145a008d2d94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322839"
---
# <a name="afx-messages"></a>AFX 메시지

이러한 메시지는 MFC에서 사용 됩니다.

## <a name="messages"></a>메시지

다음 표에서는 MFC 라이브러리에서 사용 되는 메시지를 나열 합니다.

|메시지|Description|진행 *wParam*|*lParam* (별도로 지정 하지 않는 한 모든 매개 변수는 [in]입니다.)|반환 값|
|-|-|-|-|-|
|AFX_WM_ACCGETOBJECT|사용되지 않습니다.|사용되지 않습니다.|해당 사항 없음|해당 사항 없음|
|AFX_WM_ACCGETSTATE|내게 필요한 옵션 지원에 사용 됩니다. `CMFCPopupMenu` `CMFCRibbonPanelMenu` 현재 요소의 상태를 검색 하려면이 메시지를 또는에 보냅니다.|메뉴 단추나 구분 기호 일 수 있는 요소의 인덱스입니다.|사용되지 않습니다.|요소 상태입니다. 인덱스가 잘못 된 경우에는-1이 고, 메뉴 단추에 특별 한 특성이 없으면 0입니다. 그렇지 않으면 다음 플래그의 조합입니다.<br /><br /> TBBS_DISABLED-항목을 사용할 수 없습니다.<br /><br /> TBBS_CHECKED-항목이 선택 됨<br /><br /> TBBS_BUTTON-항목이 표준 누름 단추입니다.<br /><br /> TBBS_PRESSED-단추가 눌러져 있습니다.<br /><br /> TBBS_INDETERMINATE-정의 되지 않은 상태<br /><br /> TBBS_SEPARATOR-이 요소는 메뉴 단추 대신 다른 메뉴 항목 간의 분리를 형성 합니다.|
|AFX_WM_CHANGE_ACTIVE_TAB|프레임 워크는 크기 조정 가능한 컨트롤 막대 컨트롤로이 메시지를 보냅니다. `CMFCTabCtrl`사용자가 활성 탭을 변경할 때 개체에서 알림을 받으려면이 메시지를 처리 합니다.|탭의 인덱스입니다.|사용되지 않습니다.|0이 아닌.|
|AFX_WM_CHANGE_CURRENT_FOLDER|`CMFCShellListCtrl`사용자가 현재 폴더를 변경한 경우 프레임 워크는이 메시지를의 부모로 보냅니다.|사용되지 않습니다.|사용되지 않습니다.|사용되지 않습니다.|
|AFX_WM_CHANGEVISUALMANAGER|사용자가 현재 비주얼 관리자를 변경 하면 프레임 워크는이 메시지를 모든 프레임 창으로 보냅니다. 이 메시지에 대 한 응답으로 프레임 창은 해당 영역을 다시 계산 하 고 필요에 따라 다른 매개 변수를 조정 합니다. 이 이벤트에 대 한 알림이 필요한 경우 응용 프로그램에서 AFX_WM_CHANGEVISUALMANAGER 메시지를 처리할 수 있습니다. `OnChangeVisualManager`이 이벤트의 내부 처리가 수행 되도록 하려면 기본 클래스 처리기 ()를 호출 해야 합니다.|사용되지 않습니다.|사용되지 않습니다.|사용되지 않습니다.|
|AFX_WM_CHANGING_ACTIVE_TAB|개체의 부모에 전송 `CMFCTabCtrl` 됩니다.  `CMFCTabCtrl`사용자가 탭을 다시 설정할 때 개체에서 알림을 받으려는 경우이 메시지를 처리 합니다.|활성화 되는 탭의 인덱스입니다.|사용되지 않습니다.|0이 아닌.|
|AFX_WM_CHECKEMPTYMINIFRAME|내부 전용입니다.|해당 사항 없음|해당 사항 없음|해당 사항 없음|
|AFX_WM_CREATETOOLBAR|`CMFCToolBarsListPropertyPage`사용자가 사용자 지정 프로세스 중에 새 도구 모음을 만들 때에서 전송 됩니다. 이 메시지를 처리 하 여 사용자 지정 CMFCToolBar 파생 개체를 인스턴스화할 수 있습니다. 이 메시지를 처리 하 고 사용자 고유의 도구 모음을 만드는 경우 기본 처리기에 대 한 호출을 생략 합니다.|사용되지 않습니다.|도구 모음의 이름을 포함 하는 문자열에 대 한 포인터입니다.|새로 만든 도구 모음에 대 한 포인터입니다. NULL은 도구 모음 만들기가 취소 되었음을 나타냅니다.|
|AFX_WM_CUSTOMIZEHELP|`CMFCToolbarCustomize Dialog`사용자가 **도움말** 단추 또는 F1 키를 누를 때 사용자 지정 속성 시트에서 주 프레임 창으로 보냅니다.|사용자 지정 속성 시트의 활성 페이지를 지정 합니다.|`CMFCToolbarCustomize Dialog` 개체에 대한 포인터입니다.|단계 없음.|
|AFX_WM_CUSTOMIZETOOLBAR|는 `CMFCToolbarCustomize Dialog` 사용자가 새 도구 모음을 만들고 있음을 부모 프레임에 알리기 위해이 메시지를 보냅니다.|사용자 지정이 시작 되 면 TRUE이 고, 사용자 지정이 완료 되 면 FALSE입니다.|사용되지 않습니다.|단계 없음.|
|AFX_WM_DELETETOOLBAR|사용자 지정 모드에서 도구 모음을 삭제 하려고 할 때 주 프레임 창으로 보냅니다.<br /><br /> 사용자 지정 모드에서 도구 모음을 삭제 하는 경우이 메시지를 처리 하 여 추가 작업을 수행 합니다. 또한 도구 모음을 삭제 하는 기본 처리기 ()를 호출 해야 합니다 `OnToolbarDelete` . 기본 처리기는 도구 모음을 삭제할 수 있는지 여부를 나타내는 값을 반환 합니다.|사용되지 않습니다.|삭제할 개체에 대 한 포인터 `CMFCToolBar` 입니다.|도구 모음을 삭제할 수 없는 경우 0이 아닙니다. 그렇지 않으면 0입니다.|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton` 문서 색을 검색 하기 위해이 메시지를 주 프레임 창으로 보냅니다.|사용되지 않습니다.|[in, out] 개체에 대 한 포인터 `CList<COLORREF, COLORREF>` 입니다.|단계 없음.|
|AFX_WM_GETDRAGBOUNDS|내부 전용입니다.|해당 사항 없음|해당 사항 없음|해당 사항 없음|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|사용자가 리본 목록 항목을 강조 표시할 때 주 프레임 창으로 전송 됩니다.|강조 표시 된 항목의 인덱스입니다.|에 대 한 포인터입니다. `CMFCBaseRibbonElement`|사용되지 않습니다.|
|AFX_WM_ON_AFTER_SHELL_COMMAND|`CMFCShellListCtrl` `CMFCShellTreeCtrl` 사용자가 셸 명령 실행을 완료 하면의 부모 또는 컨트롤으로 전송 됩니다.|사용자가 실행 한 명령의 ID입니다.|사용되지 않습니다.|응용 프로그램에서이 메시지를 처리 하는 경우 0을 반환 해야 합니다.|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|프레임 워크는 팝업 메뉴를 표시 하기 전에 리본의 부모에이 메시지를 보냅니다. 언제 든 지이 메시지를 처리 하 고 팝업 메뉴를 수정할 수 있습니다.|사용되지 않습니다.|에 대 한 포인터입니다. `CMFCBaseRibbonElement`|사용되지 않습니다.|
|AFX_WM_ON_CANCELTABMOVE|내부 전용입니다.|해당 사항 없음|해당 사항 없음||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|사용자가 활성 리본 컨트롤 범주를 변경할 때 프레임 워크는이 메시지를 주 프레임으로 보냅니다.|사용되지 않습니다.|범주가 변경 된에 대 한 포인터입니다 `CMFCRibbonBar` .|사용되지 않습니다.|
|AFX_WM_ON_CLOSEPOPUPWINDOW|프레임 워크는 소유자에 게 `CMFCDesktopAlertWnd` 창이 닫 혔 음을 알리기 위해이 메시지를 보냅니다.|사용되지 않습니다.|개체에 대 한 포인터 `CMFCDesktopAlertWnd` 입니다.|사용되지 않습니다.|
|AFX_WM_ON_DRAGCOMPLETE|내부 전용입니다.|해당 사항 없음|해당 사항 없음|해당 사항 없음|
|AFX_WM_ON_GET_TAB_TOOLTIP|사용자 지정 도구 설명이 활성화 된 경우 탭 창에서 탭에 대 한 도구 설명을 표시 하려고 할 때 주 프레임 창으로 보냅니다.|사용되지 않습니다.|구조체에 대 한 포인터 `CMFCTabToolTipInfo` 입니다.|사용되지 않습니다.|
|AFX_WM_ON_HSCROLL|크기 조정 가능한 컨트롤 막대 컨트롤로 보냅니다. `CMFCTabCtrl`탭 위젯 가로 스크롤 막대에서 스크롤 이벤트가 발생 하는 경우 개체에서 알림을 받도록이 메시지를 처리 합니다.|하위 단어는 사용자의 스크롤 요청을 나타내는 스크롤 막대 값을 지정 합니다.  자세한 내용은 이 항목 뒷부분에 나오는 표를 참조하십시오.|사용되지 않습니다.|0이 아닌.|
|AFX_WM_ON_MOVE_TAB|사용자가 탭을 새 위치로 끌 때 탭 창의 부모로 보냅니다.|원래 위치에 있는 탭의 인덱스 (0부터 시작)입니다.|제한이 새 위치에 있는 탭의 인덱스 (0부터 시작)입니다.|단계 없음.|
|AFX_WM_ON_MOVETABCOMPLETE|내부 전용입니다.|해당 사항 없음|해당 사항 없음|해당 사항 없음|
|AFX_WM_ON_MOVETOTABGROUP|사용자가 MDI 자식 창을 한 탭 그룹에서 다른 그룹으로 이동할 때 주 프레임 창으로 보냅니다.|MDI 자식 창이 제거 된 탭 창 ()에 대 한 핸들 `CMFCTabCtrl` 입니다.|제한이 MDI 자식 창이 삽입 된 탭 창 ()에 대 한 핸들입니다 `CMFCTabCtrl` .|무시됩니다.|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|`CDockablePane`사용자가 컨트롤 막대 캡션에 있는 **닫기** 단추를 클릭 하면의 부모로 전송 됩니다.|사용되지 않습니다.|사용자가 **닫기** 단추를 클릭 한 도킹 가능한 창에 대 한 포인터입니다.|창을 닫을 수 없으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.|
|AFX_WM_ON_RENAME_TAB|사용자가 편집 가능한 탭의 이름을 바꾼 후 탭 창의 부모에 보냅니다.|이름이 바뀐 탭의 인덱스 (0부터 시작)입니다.|제한이 새 탭 이름을 포함 하는 문자열에 대 한 포인터입니다.|응용 프로그램에서이 메시지를 처리 하는 경우 0이 아닙니다. 프레임 워크는에 대 한 호출을 표시 하지 않습니다 `CMFCBaseTabCtrl::SetTabLabel` .  0이 반환 되 면 `CMFCBaseTabCtrl::SetTabLabel` 이 프레임 워크에서 호출 됩니다.|
|AFX_WM_ON_RIBBON_CUSTOMIZE|사용자 지정을 시작 하면 부모 프레임으로 전송 됩니다. 사용자 지정 대화 상자를 표시 하려면이 메시지를 처리 합니다.|사용되지 않습니다.|사용자 지정할 리본 컨트롤에 대 한 포인터입니다.|응용 프로그램에서이 메시지를 처리 하 고 자체 사용자 지정 대화 상자를 표시 하는 경우 0이 아닙니다. 응용 프로그램에서 0을 반환 하면 프레임 워크에 기본 제공 사용자 지정 대화 상자가 표시 됩니다.|
|AFX_WM_ON_TABGROUPMOUSEMOVE|내부 전용입니다.|해당 사항 없음|해당 사항 없음|해당 사항 없음|
|AFX_WM_POSTSETPREVIEWFRAME|사용자가 인쇄 미리 보기 모드를 변경 했음을 주 프레임에 알리기 위해 전송 됩니다.|TRUE 이면 인쇄 미리 보기 모드가 설정 되어 있음을 나타냅니다. FALSE는 인쇄 미리 보기 모드가 꺼져 있음을 나타냅니다.|사용되지 않습니다.|사용되지 않습니다.|
|AFX_WM_PROPERTY_CHANGED|`CMFCPropertyGridCtrl`사용자가 선택한 속성의 값을 변경할 때 속성 그리드 컨트롤의 소유자에 게 전송 됩니다 ().|속성 목록의 컨트롤 ID입니다.|변경 된 속성 ()에 대 한 포인터 `CMFCPropertyGridProperty` 입니다.|사용되지 않습니다.|
|AFX_WM_RESETCONTEXTMENU|사용자 지정 하는 동안 사용자가 상황에 맞는 메뉴를 다시 설정할 때 주 프레임 창으로 전송 됩니다.|상황에 맞는 메뉴의 리소스 ID입니다.|현재 상황에 맞는 메뉴에 대 한 포인터 `CMFCPopupMenu` 입니다.|사용되지 않습니다.|
|AFX_WM_RESETKEYBOARD|사용자가 사용자 지정 하는 동안 모든 키보드 액셀러레이터를 다시 설정할 때 프레임 워크는이 메시지를 주 프레임 창으로 보냅니다.|사용되지 않습니다.|사용되지 않습니다.|사용되지 않습니다.|
|AFX_WM_RESETMENU|사용자가 사용자 지정 중에 응용 프로그램 프레임 메뉴를 다시 설정할 때 프레임 워크는이 메시지를 메뉴 소유자 (프레임 창)로 보냅니다.|메뉴 리소스 ID입니다.|사용되지 않습니다.|사용되지 않습니다.|
|AFX_WM_RESETPROMPT|사용자가 도구 모음 사용자 지정 대화 상자에서 도구 모음을 다시 설정할 때 프레임 워크는이 메시지를 보냅니다. 기본 처리기는 사용자가 도구 모음을 다시 설정할지 여부를 묻는 메시지 상자를 표시 합니다.|사용되지 않습니다.|사용되지 않습니다.|사용되지 않습니다.|
|AFX_WM_RESETTOOLBAR|`CMFCToolBar`도구 모음이 원래 상태로 복원 되는 경우 (즉, 리소스에서 로드 되는 경우) 개체는이 메시지를 보냅니다. 클래스가에서 파생 되는 도구 모음 단추를 다시 삽입 하려면이 메시지를 처리 `CMFCToolbarButton` 합니다. 자세한 내용은 `CMFCToolbarComboBoxButton`를 참조하세요.|해당 상태가 복원 된 도구 모음의 리소스 ID입니다.|사용되지 않습니다.|단계 없음.|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton` 사용자가 일반 메뉴 단추를 클릭 하면 개체가 소유자에 게이 메시지를 보냅니다. `CMFCToolbarMenuButton`사용자가 단추를 클릭할 때 팝업 메뉴를 표시 하는 데 사용할 때마다이 메시지를 처리 합니다.|메시지를 보내는 단추의 명령 ID입니다.|커서의 화면 좌표입니다. 하위 단어는 x 좌표를 지정 합니다. 상위 단어는 y 좌표를 지정 합니다.|사용되지 않습니다.|
|AFX_WM_TOOLBARMENU|마우스 포인터가 창의 클라이언트 또는 비클라이언트 영역에 있는 동안 사용자가 마우스 오른쪽 단추를 놓을 때 주 프레임 창으로 보냅니다.|사용되지 않습니다.|마우스 포인터의 화면 좌표입니다. 하위 단어는 x 좌표를 지정 합니다. 상위 단어는 y 좌표를 지정 합니다.|응용 프로그램에서이 메시지를 처리 하는 경우 0입니다. 그렇지 않으면 0이 아닙니다.|
|AFX_WM_UPDATETOOLTIPS|도구 설명 컨트롤을 다시 만들어야 함을 나타내기 위해 모든 도구 설명 소유자에 게 보냅니다.|이 메시지를 처리 해야 하는 컨트롤의 형식입니다. 가능한 값 목록은이 항목의 뒷부분에 나오는 표를 참조 하세요.|사용되지 않습니다.|사용되지 않습니다.|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog` 사용자가 **도움말** 단추를 클릭 하거나 도움말 캡션 단추 또는 F1 **키를 클릭** 하 여 도움말 모드로 전환 하면이 메시지를 부모 프레임으로 보냅니다.|사용되지 않습니다.|인스턴스에 대 한 포인터 `CMFCWindowsManagerDialog` 입니다.|사용되지 않습니다.|

다음 표에서는 AFX_WM_HSCROLL 메서드의 *lParam* 매개 변수의 하위 단어에 대 한 값을 보여 줍니다.

|값|의미|
|-|-|
|SB_ENDSCROLL|사용자가 스크롤을 종료 합니다.|
|SB_LEFT|사용자가 왼쪽 위로 스크롤합니다.|
|SB_RIGHT|사용자가 오른쪽 아래로 스크롤합니다.|
|SB_LINELEFT|사용자가 한 단위 만큼 왼쪽으로 스크롤됩니다.|
|SB_LINERIGHT|사용자가 한 단위 만큼 오른쪽으로 스크롤합니다.|
|SB_PAGELEFT|사용자가 창 너비 만큼 왼쪽으로 스크롤합니다.|
|SB_PAGERIGHT|사용자가 창의 너비 만큼 오른쪽으로 스크롤합니다.|
|SB_THUMBPOSITION|사용자가 스크롤 상자 (thumb)를 끌고 마우스 단추를 놓았습니다. 상위 단어는 끌기 작업 끝에서 스크롤 상자의 위치를 나타냅니다.|
|SB_THUMBTRACK|사용자가 스크롤 상자를 끌고 있습니다. AFX_WM_ON_HSCROLL 메시지는 사용자가 마우스 단추를 놓을 때까지이 값으로 반복적으로 전송 됩니다. 상위 단어는 스크롤 상자를 끌고 있는 위치를 나타냅니다.|

> [!NOTE]
> *LParam* 매개 변수의 상위 단어는 하위 단어가 SB_THUMBPOSITION 되거나 SB_THUMBTRACK 경우 스크롤 상자의 현재 위치를 지정 합니다. 그렇지 않으면이 단어는 사용 되지 않습니다.

다음 표에서는 AFX_WM_UPDATETOOLTIPS 메시지의 *lParam* 매개 변수에 대 한 플래그 값을 나열 합니다.

|플래그|값|
|-|-|
|AFX_TOOLTIP_TYPE_DEFAULT|0x0001|
|AFX_TOOLTIP_TYPE_TOOLBAR|0x0002|
|AFX_TOOLTIP_TYPE_TAB|0x0004|
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|
|AFX_TOOLTIP_TYPE_EDIT|0x0020|
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|
|AFX_TOOLTIP_TYPE_TOOLBOX|0x0080|
|AFX_TOOLTIP_TYPE_ALL|0xFFFF|

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
