---
description: '자세히 알아보기: CMFCAutoHideBar 클래스'
title: CMFCAutoHideBar 클래스
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AddAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AllowShowOnPaneMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CalcFixedLayout
- AFXAUTOHIDEBAR/CMFCAutoHideBar::Create
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetFirstAHWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetVisibleCount
- AFXAUTOHIDEBAR/CMFCAutoHideBar::OnShowControlBarMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::RemoveAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetActiveInGroup
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetRecentVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::ShowAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::StretchPane
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UnSetAutoHideMode
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UpdateVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::m_nShowAHWndDelay
helpviewer_keywords:
- CMFCAutoHideBar [MFC], CMFCAutoHideBar
- CMFCAutoHideBar [MFC], AddAutoHideWindow
- CMFCAutoHideBar [MFC], AllowShowOnPaneMenu
- CMFCAutoHideBar [MFC], CalcFixedLayout
- CMFCAutoHideBar [MFC], Create
- CMFCAutoHideBar [MFC], GetFirstAHWindow
- CMFCAutoHideBar [MFC], GetVisibleCount
- CMFCAutoHideBar [MFC], OnShowControlBarMenu
- CMFCAutoHideBar [MFC], RemoveAutoHideWindow
- CMFCAutoHideBar [MFC], SetActiveInGroup
- CMFCAutoHideBar [MFC], SetRecentVisibleState
- CMFCAutoHideBar [MFC], ShowAutoHideWindow
- CMFCAutoHideBar [MFC], StretchPane
- CMFCAutoHideBar [MFC], UnSetAutoHideMode
- CMFCAutoHideBar [MFC], UpdateVisibleState
- CMFCAutoHideBar [MFC], m_nShowAHWndDelay
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
ms.openlocfilehash: d7cea85a71b8390520d1345e12000aa700026269
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336604"
---
# <a name="cmfcautohidebar-class"></a>CMFCAutoHideBar 클래스

`CMFCAutoHideBar` 클래스는 자동 숨기기 기능을 구현하는 특수 도구 모음 클래스입니다.

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CMFCAutoHideBar : public CPane
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|( `CPane::AllowShowOnPaneMenu`을 재정의합니다.)|
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|( [Cbasepane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)를 재정의 합니다.)|
|[CMFCAutoHideBar::Create](#create)|컨트롤 막대를 만들어 [Cpane](../../mfc/reference/cpane-class.md) 개체에 연결 합니다. ( [Cpane:: Create](../../mfc/reference/cpane-class.md#create)를 재정의 합니다.)|
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||
|[CMFCAutoHideBar::GetVisibleCount](#getvisiblecount)||
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|특수 창 메뉴를 표시하려고 할 때 프레임워크에서 호출됩니다. [Cpane:: OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu)를 재정의 합니다.|
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|( [Cpane:: SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup)을 재정의 합니다.)|
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||
|[CMFCAutoHideBar::StretchPane](#stretchpane)|창을 가로 또는 세로로 확장합니다. ( [Cbasepane:: StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane)를 재정의 합니다.)|
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|사용자가 [CMFCAutoHideButton 클래스](../../mfc/reference/cmfcautohidebutton-class.md) 위에 마우스 커서를 놓고 프레임 워크에 연결 된 창이 표시 되는 순간 사이의 지연 시간입니다.|

## <a name="remarks"></a>설명

사용자가 도킹 창을 자동 숨기기 모드로 전환하면 프레임워크에서 자동으로 `CMFCAutoHideBar` 개체를 만듭니다. 또한 필요한 [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) 및 [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) 개체를 만듭니다. 각 `CAutoHideDockSite` 개체는 개별 `CMFCAutoHideButton`에 연결됩니다.

`CMFCAutoHideBar` 클래스는 사용자의 마우스로 `CMFCAutoHideButton`을 가리킬 때 `CAutoHideDockSite`의 표시를 구현합니다. 도구 모음에서 WM_MOUSEMOVE 메시지를 받으면 `CMFCAutoHideBar`에서 타이머를 시작합니다. 타이머가 완료되면 도구 모음에 WM_TIMER 이벤트 알림을 보냅니다. 도구 모음은 마우스 포인터가 타이머가 시작될 때 배치되었던 것과 동일한 자동 숨기기 단추에 배치되었는지 확인하여 이 이벤트를 처리합니다. 그럴 경우 연결된 `CAutoHideDockSite`가 표시됩니다.

`m_nShowAHWndDelay`를 설정하여 타이머의 지연 길이를 제어할 수 있습니다. 기본값은 400ms입니다.

## <a name="example"></a>예제

다음 예제에서는 `CMFCAutoHideBar` 개체를 생성하고 해당 `GetDockSiteRow` 메서드를 사용하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxautohidebar.h

## <a name="cmfcautohidebaraddautohidewindow"></a><a name="addautohidewindow"></a> CMFCAutoHideBar:: AddAutoHideWindow

자동으로 숨길 수 있도록 하는 기능을 `CDockablePane` 창에 추가합니다.

```
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>매개 변수

*pAutoHideWnd*<br/>
진행 숨기려는 창입니다.

*dwAlignment*<br/>
진행 응용 프로그램 창과 함께 자동 숨기기 단추의 맞춤을 지정 하는 값입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

*Dwalignment* 매개 변수는 자동 숨기기 단추가 응용 프로그램에 상주 하는 위치를 나타냅니다. 이 매개 변수는 다음 값 중 하나가 될 수 있습니다.

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a> CMFCAutoHideBar:: AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcautohidebarcalcfixedlayout"></a><a name="calcfixedlayout"></a> CMFCAutoHideBar:: CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>매개 변수

진행 *Bstretch*<br/>

진행 *Bhorz*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcautohidebarcmfcautohidebar"></a><a name="cmfcautohidebar"></a> CMFCAutoHideBar:: CMFCAutoHideBar

CMFCAutoHideBar 개체를 생성합니다.

```
CMFCAutoHideBar();
```

### <a name="remarks"></a>설명

## <a name="cmfcautohidebarcreate"></a><a name="create"></a> CMFCAutoHideBar:: Create

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszClassName*<br/>

*dwStyle*<br/>

*rect*<br/>

*pParentWnd*<br/>

*nID*<br/>

*Dwcontrol바 스타일*<br/>

*pContext*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcautohidebargetfirstahwindow"></a><a name="getfirstahwindow"></a> CMFCAutoHideBar:: GetFirstAHWindow

애플리케이션의 첫 번째 자동 숨기기 창에 대한 포인터를 반환합니다.

```
CDockablePane* GetFirstAHWindow();
```

### <a name="return-value"></a>반환 값

애플리케이션의 첫 번째 자동 숨기기 창이거나, 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cmfcautohidebargetvisiblecount"></a><a name="getvisiblecount"></a> CMFCAutoHideBar:: GetVisibleCount

표시되는 자동 숨기기 단추 수를 가져옵니다.

```
int GetVisibleCount();
```

### <a name="return-value"></a>반환 값

표시되는 자동 숨기기 단추 수를 반환합니다.

### <a name="remarks"></a>설명

## <a name="cmfcautohidebarm_nshowahwnddelay"></a><a name="m_nshowahwnddelay"></a> CMFCAutoHideBar:: m_nShowAHWndDelay

사용자가 [CMFCAutoHideButton 클래스](../../mfc/reference/cmfcautohidebutton-class.md) 위에 마우스 커서를 놓고 프레임 워크에 연결 된 창이 표시 되는 순간 사이의 지연 시간입니다.

```
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;
```

### <a name="remarks"></a>설명

사용자가 마우스 커서를 위로 가져가면 `CMFCAutoHideButton` 프레임 워크에서 연결 된 창이 표시 되기 전에 약간의 지연이 발생 합니다. 이 매개 변수는 지연 시간 (밀리초)을 결정 합니다.

## <a name="cmfcautohidebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a> CMFCAutoHideBar:: OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>매개 변수

[in] *CPoint*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcautohidebarremoveautohidewindow"></a><a name="removeautohidewindow"></a> CMFCAutoHideBar:: RemoveAutoHideWindow

자동 숨기기 창을 제거하고 삭제합니다.

```
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```

### <a name="parameters"></a>매개 변수

CDockablePane * *pAutoHideWnd* 자동 숨기기 창을 제거 합니다.

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 실패하면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcautohidebarsetactiveingroup"></a><a name="setactiveingroup"></a> CMFCAutoHideBar:: SetActiveInGroup

자동 숨기기 막대에 활성으로 플래그를 지정합니다.

```
virtual void SetActiveInGroup(BOOL bActive);
```

### <a name="parameters"></a>매개 변수

진행 BOOL *bactive* TRUE를 활성으로 설정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

[CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup)을 참조하세요.

## <a name="cmfcautohidebarsetrecentvisiblestate"></a><a name="setrecentvisiblestate"></a> CMFCAutoHideBar:: SetRecentVisibleState

```cpp
void SetRecentVisibleState(BOOL bState);
```

### <a name="parameters"></a>매개 변수

*bState*<br/>
진행 설정할 상태입니다.

### <a name="remarks"></a>설명

## <a name="cmfcautohidebarshowautohidewindow"></a><a name="showautohidewindow"></a> CMFCAutoHideBar:: ShowAutoHideWindow

자동 숨기기 창을 표시합니다.

```
BOOL ShowAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>매개 변수

*pAutoHideWnd*<br/>
진행 표시할 창입니다.

*bShow*<br/>
진행 창을 표시 하려면 TRUE입니다.

*bDelay*<br/>
진행 이 매개 변수는 무시 됩니다.

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 실패하면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcautohidebarstretchpane"></a><a name="stretchpane"></a> CMFCAutoHideBar:: StretchPane

`CMFCAutoHideButton` 개체에 맞게 자동 숨기기 막대의 크기를 축소된 상태로 조정합니다.

```
virtual CSize StretchPane(
    int nLength,
    BOOL bVert);
```

### <a name="parameters"></a>매개 변수

*nLength*<br/>
진행 값이 기본 구현에서 사용 되지 않습니다. 파생된 구현에서는 이 값을 사용하여 크기 조정된 창의 길이를 나타냅니다.

*bVert*<br/>
진행 값이 기본 구현에서 사용 되지 않습니다. 파생 된 구현에서는 TRUE를 사용 하 여 자동 숨기기 막대가 세로로 축소 되는 경우를 처리 하 고, 자동 숨기기 막대가 가로로 축소 되는 경우에는 FALSE를 사용 합니다.

### <a name="return-value"></a>반환 값

크기 조정된 창의 결과 크기입니다.

### <a name="remarks"></a>설명

파생된 클래스는 이 메서드를 재정의하여 동작을 사용자 지정할 수 있습니다.

## <a name="cmfcautohidebarunsetautohidemode"></a><a name="unsetautohidemode"></a> CMFCAutoHideBar:: UnSetAutoHideMode

자동 숨기기 막대의 그룹에 대해 자동 숨기기 모드를 사용하지 않도록 설정합니다.

```cpp
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)
```

### <a name="parameters"></a>매개 변수

[in] 그룹의 첫 번째 자동 숨기기 막대에 대 한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="cmfcautohidebarupdatevisiblestate"></a><a name="updatevisiblestate"></a> CMFCAutoHideBar:: UpdateVisibleState

자동 숨기기 막대를 다시 그려야 할 때 프레임워크에서 호출됩니다.

```cpp
void UpdateVisibleState();
```

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CPane 클래스](../../mfc/reference/cpane-class.md)<br/>
[CAutoHideDockSite 클래스](../../mfc/reference/cautohidedocksite-class.md)<br/>
[CMFCAutoHideButton 클래스](../../mfc/reference/cmfcautohidebutton-class.md)
