---
description: '자세히 알아보기: CPaneFrameWnd 클래스'
title: CPaneFrameWnd 클래스
ms.date: 11/04/2016
f1_keywords:
- CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd::AddPane
- AFXPANEFRAMEWND/CPaneFrameWnd::AddRemovePaneFromGlobalList
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustPaneFrames
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcBorderSize
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcExpectedDockedRect
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeAttached
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeDockedToPane
- AFXPANEFRAMEWND/CPaneFrameWnd::CheckGripperVisibility
- AFXPANEFRAMEWND/CPaneFrameWnd::ConvertToTabbedDocument
- AFXPANEFRAMEWND/CPaneFrameWnd::Create
- AFXPANEFRAMEWND/CPaneFrameWnd::CreateEx
- AFXPANEFRAMEWND/CPaneFrameWnd::DockPane
- AFXPANEFRAMEWND/CPaneFrameWnd::FindFloatingPaneByID
- AFXPANEFRAMEWND/CPaneFrameWnd::FrameFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionHeight
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionText
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingMode
- AFXPANEFRAMEWND/CPaneFrameWnd::GetFirstVisiblePane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::GetParent
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPinState
- AFXPANEFRAMEWND/CPaneFrameWnd::GetRecentFloatingRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetVisiblePaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::HitTest
- AFXPANEFRAMEWND/CPaneFrameWnd::IsCaptured
- AFXPANEFRAMEWND/CPaneFrameWnd::IsDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollDown
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollUp
- AFXPANEFRAMEWND/CPaneFrameWnd::KillDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::LoadState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnBeforeDock
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDockToRecentPos
- AFXPANEFRAMEWND/CPaneFrameWnd::OnKillRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnMovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::OnPaneRecalcLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::OnSetRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnShowPane
- AFXPANEFRAMEWND/CPaneFrameWnd::PaneFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::Pin
- AFXPANEFRAMEWND/CPaneFrameWnd::RedrawAll
- AFXPANEFRAMEWND/CPaneFrameWnd::RemoveNonValidPanes
- AFXPANEFRAMEWND/CPaneFrameWnd::RemovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::ReplacePane
- AFXPANEFRAMEWND/CPaneFrameWnd::SaveState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetCaptionButtons
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::SetPreDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SizeToContent
- AFXPANEFRAMEWND/CPaneFrameWnd::StartTearOff
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentDockSiteInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentTabRelatedInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::OnCheckRollState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDrawBorder
- AFXPANEFRAMEWND/CPaneFrameWnd::m_bUseSaveBits
helpviewer_keywords:
- CPaneFrameWnd [MFC], AddPane
- CPaneFrameWnd [MFC], AddRemovePaneFromGlobalList
- CPaneFrameWnd [MFC], AdjustLayout
- CPaneFrameWnd [MFC], AdjustPaneFrames
- CPaneFrameWnd [MFC], CalcBorderSize
- CPaneFrameWnd [MFC], CalcExpectedDockedRect
- CPaneFrameWnd [MFC], CanBeAttached
- CPaneFrameWnd [MFC], CanBeDockedToPane
- CPaneFrameWnd [MFC], CheckGripperVisibility
- CPaneFrameWnd [MFC], ConvertToTabbedDocument
- CPaneFrameWnd [MFC], Create
- CPaneFrameWnd [MFC], CreateEx
- CPaneFrameWnd [MFC], DockPane
- CPaneFrameWnd [MFC], FindFloatingPaneByID
- CPaneFrameWnd [MFC], FrameFromPoint
- CPaneFrameWnd [MFC], GetCaptionHeight
- CPaneFrameWnd [MFC], GetCaptionRect
- CPaneFrameWnd [MFC], GetCaptionText
- CPaneFrameWnd [MFC], GetDockingManager
- CPaneFrameWnd [MFC], GetDockingMode
- CPaneFrameWnd [MFC], GetFirstVisiblePane
- CPaneFrameWnd [MFC], GetHotPoint
- CPaneFrameWnd [MFC], GetPane
- CPaneFrameWnd [MFC], GetPaneCount
- CPaneFrameWnd [MFC], GetParent
- CPaneFrameWnd [MFC], GetPinState
- CPaneFrameWnd [MFC], GetRecentFloatingRect
- CPaneFrameWnd [MFC], GetVisiblePaneCount
- CPaneFrameWnd [MFC], HitTest
- CPaneFrameWnd [MFC], IsCaptured
- CPaneFrameWnd [MFC], IsDelayShow
- CPaneFrameWnd [MFC], IsRollDown
- CPaneFrameWnd [MFC], IsRollUp
- CPaneFrameWnd [MFC], KillDockingTimer
- CPaneFrameWnd [MFC], LoadState
- CPaneFrameWnd [MFC], OnBeforeDock
- CPaneFrameWnd [MFC], OnDockToRecentPos
- CPaneFrameWnd [MFC], OnKillRollUpTimer
- CPaneFrameWnd [MFC], OnMovePane
- CPaneFrameWnd [MFC], OnPaneRecalcLayout
- CPaneFrameWnd [MFC], OnSetRollUpTimer
- CPaneFrameWnd [MFC], OnShowPane
- CPaneFrameWnd [MFC], PaneFromPoint
- CPaneFrameWnd [MFC], Pin
- CPaneFrameWnd [MFC], RedrawAll
- CPaneFrameWnd [MFC], RemoveNonValidPanes
- CPaneFrameWnd [MFC], RemovePane
- CPaneFrameWnd [MFC], ReplacePane
- CPaneFrameWnd [MFC], SaveState
- CPaneFrameWnd [MFC], SetCaptionButtons
- CPaneFrameWnd [MFC], SetDelayShow
- CPaneFrameWnd [MFC], SetDockingManager
- CPaneFrameWnd [MFC], SetDockingTimer
- CPaneFrameWnd [MFC], SetDockState
- CPaneFrameWnd [MFC], SetHotPoint
- CPaneFrameWnd [MFC], SetPreDockState
- CPaneFrameWnd [MFC], SizeToContent
- CPaneFrameWnd [MFC], StartTearOff
- CPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
- CPaneFrameWnd [MFC], OnCheckRollState
- CPaneFrameWnd [MFC], OnDrawBorder
- CPaneFrameWnd [MFC], m_bUseSaveBits
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
ms.openlocfilehash: 49322fa5a4d4c053e950020161171fd1f8d3db3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345162"
---
# <a name="cpaneframewnd-class"></a>CPaneFrameWnd 클래스

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

하나의 창이 포함된 미니 프레임 창을 구현합니다. 창은 창의 클라이언트 영역을 채웁니다.

## <a name="syntax"></a>구문

```
class CPaneFrameWnd : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPaneFrameWnd::AddPane](#addpane)|창을 추가합니다.|
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|전역 목록에서 창을 추가하거나 제거합니다.|
|[CPaneFrameWnd::AdjustLayout](#adjustlayout)|미니 프레임 창의 레이아웃을 조정합니다.|
|[CPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)||
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|미니 프레임 창의 테두리 크기를 계산합니다.|
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|도킹된 창의 예상 사각형을 계산합니다.|
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|현재 창을 다른 창이나 프레임 창에 도킹할 수 있는지 여부를 결정합니다.|
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|미니 프레임 창을 창에 도킹할 수 있는지 여부를 결정합니다.|
|[CPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)||
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|창을 탭된 문서로 변환합니다.|
|[CPaneFrameWnd::Create](#create)|미니 프레임 창을 만들고 `CPaneFrameWnd` 개체에 연결합니다.|
|[CPaneFrameWnd::CreateEx](#createex)|미니 프레임 창을 만들고 `CPaneFrameWnd` 개체에 연결합니다.|
|[CPaneFrameWnd::DockPane](#dockpane)|창을 도킹합니다.|
|[CPaneFrameWnd::FindFloatingPaneByID](#findfloatingpanebyid)|부동 창의 전역 목록에서 지정된 컨트롤 ID를 가진 창을 찾습니다.|
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|사용자가 제공한 지점을 포함하는 미니 프레임 창을 찾습니다.|
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|미니 프레임 창 캡션의 높이를 반환합니다.|
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|미니 프레임 창 캡션의 경계 사각형을 계산합니다.|
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|캡션 텍스트를 반환합니다.|
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|도킹 모드를 반환합니다.|
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|미니 프레임 창에 포함된 첫 번째 표시 창을 반환합니다.|
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||
|[CPaneFrameWnd::GetPane](#getpane)|미니 프레임 창에 포함된 창을 반환합니다.|
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|미니 프레임 창에 포함된 창 수를 반환합니다.|
|[CPaneFrameWnd::GetParent](#getparent)||
|[CPaneFrameWnd::GetPinState](#getpinstate)||
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|미니 프레임 창에 포함된 표시 창 수를 반환합니다.|
|[CPaneFrameWnd::HitTest](#hittest)|미니 프레임 창의 어떤 부분이 지정된 지점에 있는지 결정합니다.|
|[CPaneFrameWnd::IsCaptured](#iscaptured)||
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||
|[CPaneFrameWnd::IsRollDown](#isrolldown)|미니 프레임 창이 롤다운되어야 하는지 여부를 결정합니다.|
|[CPaneFrameWnd::IsRollUp](#isrollup)|미니 프레임 창이 롤업되어야 하는지 여부를 결정합니다.|
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|도킹 타이머를 중지합니다.|
|[CPaneFrameWnd::LoadState](#loadstate)|레지스트리에서 창의 상태를 로드합니다.|
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|도킹 가능한지 여부를 결정합니다.|
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|가장 최근 위치에 미니 프레임 창을 도킹합니다.|
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|롤업 타이머를 중지합니다.|
|[CPaneFrameWnd::OnMovePane](#onmovepane)|지정된 오프셋만큼 미니 프레임 창을 이동합니다.|
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|포함된 창의 레이아웃을 조정합니다.|
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|롤업 타이머를 설정합니다.|
|[CPaneFrameWnd::OnShowPane](#onshowpane)|미니 프레임 창의 창이 숨겨지거나 표시될 때 프레임워크에서 호출됩니다.|
|[CPaneFrameWnd::PaneFromPoint](#panefrompoint)|미니 프레임 창 안에 사용자가 제공한 지점을 포함하는 경우 창을 반환합니다.|
|[CPaneFrameWnd::Pin](#pin)||
|`CPaneFrameWnd::PreTranslateMessage`|창 메시지가 [TranslateMessage](../../mfc/reference/cwinapp-class.md) 및 [DispatchMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) Windows 함수로 디스패치되기 전에 [CWinApp](/windows/win32/api/winuser/nf-winuser-dispatchmessage) 클래스가 이 메시지를 해석하는 데 사용됩니다.|
|[CPaneFrameWnd::RedrawAll](#redrawall)|모든 미니 프레임 창을 다시 그립니다.|
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|잘못된 창을 제거하기 위해 프레임워크에서 호출됩니다.|
|[CPaneFrameWnd::RemovePane](#removepane)|미니 프레임 창에서 창을 제거합니다.|
|[CPaneFrameWnd::ReplacePane](#replacepane)|한 창을 다른 창으로 대체합니다.|
|[CPaneFrameWnd::SaveState](#savestate)|레지스트리에 창의 상태를 저장합니다.|
|`CPaneFrameWnd::Serialize`|이 개체를 보관 저장소에서 읽어오거나 보관 저장소에 씁니다.|
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|캡션 단추를 설정합니다.|
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|도킹 타이머를 설정합니다.|
|[CPaneFrameWnd::SetDockState](#setdockstate)|도킹 상태를 설정합니다.|
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|사전 도킹 상태를 설정하기 위해 프레임워크에서 호출됩니다.|
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|포함된 창과 크기가 같도록 미니 프레임 창의 크기를 조정합니다.|
|[CPaneFrameWnd::StartTearOff](#starttearoff)|메뉴를 분리합니다.|
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|미니 프레임 창이 롤업 또는 롤다운되어야 하는지를 결정합니다.|
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|미니 프레임 창의 테두리를 그립니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|CS_SAVEBITS 클래스 스타일을 사용 하 여 창 클래스를 등록할지 여부를 지정 합니다.|

## <a name="remarks"></a>설명

창이 도킹된 상태에서 부동 상태로 전환되면 프레임워크에서 자동으로 `CPaneFrameWnd` 개체를 만듭니다.

내용을 표시(즉시 도킹)하거나 끌기 사각형을 사용하여(표준 도킹) 미니 프레임 창을 끌 수 있습니다. 미니 프레임 컨테이너 창의 도킹 모드에 따라 미니 프레임의 끌기 동작이 결정됩니다. 자세한 내용은 [Cbasepane:: GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode)를 참조 하세요.

미니 프레임 창에 포함된 창 스타일에 따라 캡션에 단추가 표시됩니다. 창을 닫을 수 있는 경우 ( [Cbasepane:: CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)) 닫기 단추를 표시 합니다. 창에 AFX_CBRS_AUTO_ROLLUP 스타일이 있으면 pin이 표시 됩니다.

`CPaneFrameWnd`에서 클래스를 파생하는 경우 프레임워크에 만드는 방법을 알려야 합니다. [Cpane:: CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe)를 재정의 하 여 클래스를 만들거나 `CPane::m_pMiniFrameRTC` 클래스의 런타임 클래스 정보를 가리키도록 멤버를 설정 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>요구 사항

**헤더:** afxPaneFrameWnd

## <a name="cpaneframewndaddpane"></a><a name="addpane"></a> CPaneFrameWnd:: AddPane

창을 추가합니다.

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 추가할 창입니다.

## <a name="cpaneframewndaddremovepanefromgloballist"></a><a name="addremovepanefromgloballist"></a> CPaneFrameWnd:: AddRemovePaneFromGlobalList

전역 목록에서 창을 추가하거나 제거합니다.

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 추가 하거나 제거할 창입니다.

*bAdd*<br/>
진행 0이 아닌 경우 창을 추가 합니다. 0 인 경우 창을 제거 합니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="cpaneframewndadjustlayout"></a><a name="adjustlayout"></a> CPaneFrameWnd:: AdjustLayout

미니 프레임 창의 레이아웃을 조정합니다.

```
virtual void AdjustLayout();
```

## <a name="cpaneframewndadjustpaneframes"></a><a name="adjustpaneframes"></a> CPaneFrameWnd:: AdjustPaneFrames

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>설명

## <a name="cpaneframewndcalcbordersize"></a><a name="calcbordersize"></a> CPaneFrameWnd:: CalcBorderSize

미니 프레임 창의 테두리 크기를 계산 합니다.

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>매개 변수

*rectBorderSize*<br/>
제한이 미니 프레임 창의 테두리 크기 (픽셀)를 포함 합니다.

### <a name="remarks"></a>설명

이 메서드는 미니 프레임 창의 테두리 크기를 계산 하기 위해 프레임 워크에서 호출 됩니다. 반환 되는 크기는 미니 프레임 창에 도구 모음이 포함 되어 있는지 아니면 [CDockablePane](../../mfc/reference/cdockablepane-class.md)에 포함 되는지에 따라 달라 집니다.

## <a name="cpaneframewndcalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a> CPaneFrameWnd:: CalcExpectedDockedRect

도킹된 창의 예상 사각형을 계산합니다.

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>매개 변수

*pWndToDock*<br/>
진행 도킹할 창에 대 한 포인터입니다.

*ptMouse*<br/>
진행 마우스 위치입니다.

*rectResult*<br/>
제한이 계산 된 사각형입니다.

*bDrawTab*<br/>
제한이 TRUE 이면 탭을 그립니다. FALSE 이면 탭을 그리지 않습니다.

*ppTargetBar*<br/>
제한이 대상 창에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 사용자가 *단추를 ptmouse* 에서 지정한 지점으로 끌고 거기에 도킹 한 경우 창이 차지할 사각형을 계산 합니다.

## <a name="cpaneframewndcanbeattached"></a><a name="canbeattached"></a> CPaneFrameWnd:: CanBeAttached

현재 창을 다른 창이나 프레임 창에 도킹할 수 있는지 여부를 결정합니다.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>반환 값

창을 다른 창이 나 프레임 창에 도킹할 수 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cpaneframewndcanbedockedtopane"></a><a name="canbedockedtopane"></a> CPaneFrameWnd:: CanBeDockedToPane

미니 프레임 창을 창에 도킹할 수 있는지 여부를 결정합니다.

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>매개 변수

*pDockingBar*<br/>
진행 창입니다.

### <a name="return-value"></a>반환 값

미니 프레임을 *pDockingBar* 에 도킹할 수 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

## <a name="cpaneframewndcheckgrippervisibility"></a><a name="checkgrippervisibility"></a> CPaneFrameWnd:: CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>설명

## <a name="cpaneframewndconverttotabbeddocument"></a><a name="converttotabbeddocument"></a> CPaneFrameWnd:: ConvertToTabbedDocument

창을 탭된 문서로 변환합니다.

```
virtual void ConvertToTabbedDocument();
```

## <a name="cpaneframewndcreate"></a><a name="create"></a> CPaneFrameWnd:: Create

미니 프레임 창을 만들어 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) 개체에 연결 합니다.

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszWindowName*<br/>
진행 미니 프레임 창에 표시할 텍스트를 지정 합니다.

*dwStyle*<br/>
진행 창 스타일을 지정 합니다. 자세한 내용은 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)을 참조 하세요.

*rect*<br/>
진행 미니 프레임 창의 초기 크기와 위치를 지정 합니다.

*pParentWnd*<br/>
[in, out] 미니 프레임 창의 부모 프레임을 지정 합니다. 이 값은 NULL이 아니어야 합니다.

*pContext*<br/>
[in, out] 사용자 정의 컨텍스트를 지정 합니다.

### <a name="return-value"></a>반환 값

창이 성공적으로 만들어졌으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

미니 프레임 창은 두 단계로 생성 됩니다. 먼저 프레임 워크에서 개체를 만듭니다 `CPaneFrameWnd`  . 두 번째로를 호출 `Create` 하 여 Windows 미니 프레임 창을 만들고 개체에 연결 `CPaneFrameWnd` 합니다.

## <a name="cpaneframewndcreateex"></a><a name="createex"></a> CPaneFrameWnd:: CreateEx

미니 프레임 창을 만들어 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) 개체에 연결 합니다.

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>매개 변수

*dwStyleEx*<br/>
진행 확장 창 스타일을 지정 합니다. 자세한 내용은 [확장 창 스타일](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) 을 참조 하세요.

*lpszWindowName*<br/>
진행 미니 프레임 창에 표시할 텍스트를 지정 합니다.

*dwStyle*<br/>
진행 창 스타일을 지정 합니다. 자세한 내용은 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)을 참조 하세요.

*rect*<br/>
진행 미니 프레임 창의 초기 크기와 위치를 지정 합니다.

*pParentWnd*<br/>
[in, out] 미니 프레임 창의 부모 프레임을 지정 합니다. 이 값은 NULL이 아니어야 합니다.

*pContext*<br/>
[in, out] 사용자 정의 컨텍스트를 지정 합니다.

### <a name="return-value"></a>반환 값

창이 성공적으로 만들어졌으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

미니 프레임 창은 두 단계로 생성 됩니다. 먼저 프레임 워크에서 개체를 만듭니다 `CPaneFrameWnd`  . 두 번째로를 호출 `Create` 하 여 Windows 미니 프레임 창을 만들고 개체에 연결 `CPaneFrameWnd` 합니다.

## <a name="cpaneframewnddockpane"></a><a name="dockpane"></a> CPaneFrameWnd::D ockPane

창을 도킹합니다.

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>매개 변수

*bWasDocked*<br/>
제한이 창이 이미 도킹 되었으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

작업이 성공적으로 수행 `CDockablePane` 되 면 창이 도킹 된이 고, 그렇지 않으면 NULL입니다.

## <a name="cpaneframewndfindfloatingpanebyid"></a><a name="findfloatingpanebyid"></a> CPaneFrameWnd:: FindFloatingPaneByID

부동 창의 전역 목록에서 지정된 컨트롤 ID를 가진 창을 찾습니다.

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
진행 찾을 창의 컨트롤 ID를 나타냅니다.

### <a name="return-value"></a>반환 값

지정 된 컨트롤 ID를 사용 하는 창 지정 된 컨트롤 ID를 가진 창이 없으면 NULL이 고, 그렇지 않으면 NULL입니다.

## <a name="cpaneframewndframefrompoint"></a><a name="framefrompoint"></a> CPaneFrameWnd:: 프레임 위치

지정 된 지점이 포함 된 미니 프레임 창을 찾습니다.

```
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,
    int nSensitivity,
    CPaneFrameWnd* pFrameToExclude = NULL,
    BOOL bFloatMultiOnly = FALSE);
```

### <a name="parameters"></a>매개 변수

*pt*<br/>
진행 화면 좌표에 있는 점입니다.

*nSensitivity*<br/>
진행 미니 프레임 창의 검색 영역을이 크기로 늘립니다. 지정 된 지점이 증가 하는 영역에 있으면 미니 프레임 창이 검색 조건을 충족 합니다.

*pFrameToExclude*<br/>
진행 검색에서 제외할 미니 프레임 창을 지정 합니다.

*bFloatMultiOnly*<br/>
진행 TRUE 이면 CBRS_FLOAT_MULTI 스타일이 있는 미니 프레임 파일만 검색 합니다. FALSE 이면 모든 미니 프레임 창을 검색 합니다.

### <a name="return-value"></a>반환 값

*Pt* 를 포함 하는 미니 프레임 창에 대 한 포인터입니다. 그렇지 않으면 NULL입니다.

## <a name="cpaneframewndgetcaptionheight"></a><a name="getcaptionheight"></a> CPaneFrameWnd:: GetCaptionHeight

미니 프레임 창 캡션의 높이를 반환합니다.

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>반환 값

미니 프레임 창의 높이 (픽셀)입니다.

### <a name="remarks"></a>설명

미니 프레임 창의 높이를 확인 하려면이 메서드를 호출 합니다. 기본적으로 높이는 SM_CYSMCAPTION로 설정 됩니다. 자세한 내용은 [Getsystemmetrics 함수](/windows/win32/api/winuser/nf-winuser-getsystemmetrics)를 참조 하세요.

## <a name="cpaneframewndgetcaptionrect"></a><a name="getcaptionrect"></a> CPaneFrameWnd:: GetCaptionRect

미니 프레임 창 캡션의 경계 사각형을 계산합니다.

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>매개 변수

*rectCaption*<br/>
제한이 화면 좌표에 있는 미니 프레임 창 캡션의 크기와 위치를 포함 합니다.

### <a name="remarks"></a>설명

이 메서드는 미니 프레임 창 캡션의 경계 사각형을 계산 하기 위해 프레임 워크에서 호출 됩니다.

## <a name="cpaneframewndgetcaptiontext"></a><a name="getcaptiontext"></a> CPaneFrameWnd:: GetCaptionText

캡션 텍스트를 반환합니다.

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>반환 값

미니 프레임 창의 캡션 텍스트입니다.

### <a name="remarks"></a>설명

이 메서드는 캡션 텍스트가 표시 될 때 프레임 워크에서 호출 됩니다.

## <a name="cpaneframewndgetdockingmanager"></a><a name="getdockingmanager"></a> CPaneFrameWnd:: GetDockingManager

```
CDockingManager* GetDockingManager() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpaneframewndgetdockingmode"></a><a name="getdockingmode"></a> CPaneFrameWnd:: GetDockingMode

도킹 모드를 반환합니다.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>반환 값

도킹 모드입니다. 다음 값 중 하나입니다.

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

## <a name="cpaneframewndgetfirstvisiblepane"></a><a name="getfirstvisiblepane"></a> CPaneFrameWnd:: GetFirstVisiblePane

미니 프레임 창에 포함된 첫 번째 표시 창을 반환합니다.

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>반환 값

미니 프레임 창의 첫 번째 창 이거나 미니 프레임 창에 창이 없는 경우 NULL입니다.

## <a name="cpaneframewndgethotpoint"></a><a name="gethotpoint"></a> CPaneFrameWnd:: GetHotPoint

```
CPoint GetHotPoint() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpaneframewndgetpane"></a><a name="getpane"></a> CPaneFrameWnd:: GetPane

미니 프레임 창에 포함된 창을 반환합니다.

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>반환 값

미니 프레임에 포함 된 창 이거나 미니 프레임 창에 창이 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cpaneframewndgetpanecount"></a><a name="getpanecount"></a> CPaneFrameWnd:: Get팬 Ecount

미니 프레임 창에 포함된 창 수를 반환합니다.

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>반환 값

미니 프레임 창의 창 수입니다. 이 값은 0일 수 있습니다.

### <a name="remarks"></a>설명

## <a name="cpaneframewndgetparent"></a><a name="getparent"></a> CPaneFrameWnd:: GetParent

```
CWnd* GetParent();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpaneframewndgetpinstate"></a><a name="getpinstate"></a> CPaneFrameWnd:: GetPinState

```
BOOL GetPinState() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpaneframewndgetrecentfloatingrect"></a><a name="getrecentfloatingrect"></a> CPaneFrameWnd:: GetRecentFloatingRect

```
CRect GetRecentFloatingRect() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpaneframewndgetvisiblepanecount"></a><a name="getvisiblepanecount"></a> CPaneFrameWnd:: GetVisiblePaneCount

미니 프레임 창에 포함된 표시 창 수를 반환합니다.

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>반환 값

표시 되는 창의 수입니다.

### <a name="remarks"></a>설명

## <a name="cpaneframewndhittest"></a><a name="hittest"></a> CPaneFrameWnd:: System.windows.media.visualtreehelper.hittest

미니 프레임 창의 어떤 부분이 지정된 지점에 있는지 결정합니다.

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
[in] 테스트할 지점입니다.

*bDetectCaption*<br/>
진행 TRUE 이면 캡션에 대 한 점을 확인 합니다. FALSE 이면 캡션을 무시 합니다.

### <a name="return-value"></a>반환 값

다음 값 중 하나입니다.

|값|의미|
|-----------|-------------|
|HTNOWHERE|점이 미니 프레임 창 외부에 있습니다.|
|HTCLIENT|지점은 클라이언트 영역에 있습니다.|
|HTCAPTION|점이 캡션에 있습니다.|
|HTTOP|지점은 맨 위에 있습니다.|
|HTTOPLEFT|지점은 왼쪽 위에 있습니다.|
|HTTOPRIGHT|지점은 오른쪽 위에 있습니다.|
|HTLEFT|지점은 왼쪽에 있습니다.|
|HTRIGHT|지점은 오른쪽에 있습니다.|
|HTBOTTOM|지점은 맨 아래에 있습니다.|
|HTBOTTOMLEFT|지점은 왼쪽 아래에 있습니다.|
|HTBOTTOMRIGHT|지점은 오른쪽 아래에 있습니다.|

## <a name="cpaneframewndiscaptured"></a><a name="iscaptured"></a> CPaneFrameWnd:: IsCaptured

```
BOOL IsCaptured() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpaneframewndisdelayshow"></a><a name="isdelayshow"></a> CPaneFrameWnd:: IsDelayShow

```
BOOL IsDelayShow() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpaneframewndisrolldown"></a><a name="isrolldown"></a> CPaneFrameWnd:: IsRollDown

미니 프레임 창이 롤다운되어야 하는지 여부를 결정합니다.

```
virtual BOOL IsRollDown() const;
```

### <a name="return-value"></a>반환 값

미니 프레임 창을 겹쳐서 표시 해야 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 미니 프레임 창을 롤백해야 하는지 여부를 확인 하기 위해 프레임 워크에서 호출 됩니다. Rollup/rolldown 기능은 미니 프레임 창에 AFX_CBRS_AUTO_ROLLUP 플래그가 있는 창이 하나 이상 포함 된 경우에만 사용할 수 있습니다. 이 플래그는 창을 만들 때 설정 됩니다. 자세한 내용은 [Cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)를 참조 하세요.

기본적으로 프레임 워크는 마우스 포인터가 미니 프레임 창 경계 사각형 안에 있는지 확인 하 여 창을 롤백해야 하는지 여부를 확인 합니다. 파생 클래스에서이 동작을 재정의할 수 있습니다.

## <a name="cpaneframewndisrollup"></a><a name="isrollup"></a> CPaneFrameWnd:: IsRollUp

미니 프레임 창이 롤업되어야 하는지 여부를 결정합니다.

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>반환 값

미니 프레임 창을 겹쳐서 표시 해야 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 미니 프레임 창을 롤백해야 하는지 여부를 확인 하기 위해 프레임 워크에서 호출 됩니다. Rollup/rolldown 기능은 미니 프레임 창에 AFX_CBRS_AUTO_ROLLUP 플래그가 있는 창이 하나 이상 포함 된 경우에만 사용할 수 있습니다. 이 플래그는 창을 만들 때 설정 됩니다. 자세한 내용은 [Cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)를 참조 하세요.

기본적으로 프레임 워크는 마우스 포인터가 미니 프레임 창 경계 사각형 안에 있는지 확인 하 여 창을 롤백해야 하는지 여부를 확인 합니다. 파생 클래스에서이 동작을 재정의할 수 있습니다.

## <a name="cpaneframewndkilldockingtimer"></a><a name="killdockingtimer"></a> CPaneFrameWnd:: KillDockingTimer

도킹 타이머를 중지합니다.

```cpp
void KillDockingTimer();
```

## <a name="cpaneframewndloadstate"></a><a name="loadstate"></a> CPaneFrameWnd:: LoadState

레지스트리에서 창의 상태를 로드합니다.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 프로필 이름입니다.

*uiID*<br/>
진행 창 ID입니다.

### <a name="return-value"></a>반환 값

창 상태가 성공적으로 로드 되었으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cpaneframewndm_busesavebits"></a><a name="m_busesavebits"></a> CPaneFrameWnd:: m_bUseSaveBits

CS_SAVEBITS 클래스 스타일을 포함 하는 창 클래스를 등록할지 여부를 지정 합니다.

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>설명

CS_SAVEBITS 스타일이 있는 미니 프레임 창 클래스를 등록 하려면이 정적 멤버를 TRUE로 설정 합니다. 이렇게 하면 사용자가 미니 프레임 창을 끌 때 깜박임을 줄일 수 있습니다.

## <a name="cpaneframewndonbeforedock"></a><a name="onbeforedock"></a> CPaneFrameWnd:: OnBeforeDock

도킹 가능한지 여부를 결정합니다.

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>반환 값

도킹을 사용할 수 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cpaneframewndoncheckrollstate"></a><a name="oncheckrollstate"></a> CPaneFrameWnd:: OnCheckRollState

미니 프레임 창이 롤업 또는 롤다운되어야 하는지를 결정합니다.

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>설명

이 메서드는 미니 프레임 창을 롤백해야 할지 여부를 결정 하기 위해 프레임 워크에서 호출 됩니다.

기본적으로 프레임 워크는 [CPaneFrameWnd:: IsRollUp](#isrollup) 및 [CPaneFrameWnd:: IsRollDown](#isrolldown) 를 호출 하 고 미니 프레임 창을 늘이거나 복원 합니다. 파생 클래스에서이 메서드를 재정의 하 여 다른 시각적 효과를 사용할 수 있습니다.

## <a name="cpaneframewndondocktorecentpos"></a><a name="ondocktorecentpos"></a> CPaneFrameWnd:: OnDockToRecentPos

가장 최근 위치에 미니 프레임 창을 도킹합니다.

```
virtual void OnDockToRecentPos();
```

## <a name="cpaneframewndondrawborder"></a><a name="ondrawborder"></a> CPaneFrameWnd:: OnDrawBorder

미니 프레임 창의 테두리를 그립니다.

```
virtual void OnDrawBorder(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 테두리를 그리는 데 사용 되는 장치 컨텍스트입니다.

### <a name="remarks"></a>설명

이 메서드는 미니 프레임 창의 테두리를 그리기 위해 프레임 워크에서 호출 됩니다.

## <a name="cpaneframewndonkillrolluptimer"></a><a name="onkillrolluptimer"></a> CPaneFrameWnd:: OnKillRollUpTimer

롤업 타이머를 중지합니다.

```
virtual void OnKillRollUpTimer();
```

## <a name="cpaneframewndonmovepane"></a><a name="onmovepane"></a> CPaneFrameWnd:: onmovepmov

지정된 오프셋만큼 미니 프레임 창을 이동합니다.

```
virtual void OnMovePane(
    CPane* pBar,
    CPoint ptOffset);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
진행 창에 대 한 포인터입니다 (무시 됨).

*ptOffset*<br/>
진행 창을 이동 하는 기준이 되는 오프셋입니다.

## <a name="cpaneframewndonpanerecalclayout"></a><a name="onpanerecalclayout"></a> CPaneFrameWnd:: OnPaneRecalcLayout

미니 프레임 창 안에 있는 창의 레이아웃을 조정 합니다.

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>설명

프레임 워크는 미니 프레임 창 내에서 창의 레이아웃을 조정 해야 하는 경우이 메서드를 호출 합니다.

기본적으로이 창은 미니 프레임 창의 전체 클라이언트 영역을 포함 하는 위치에 배치 됩니다.

## <a name="cpaneframewndonsetrolluptimer"></a><a name="onsetrolluptimer"></a> CPaneFrameWnd:: OnSetRollUpTimer

롤업 타이머를 설정합니다.

```
virtual void OnSetRollUpTimer();
```

## <a name="cpaneframewndonshowpane"></a><a name="onshowpane"></a> CPaneFrameWnd:: OnShowPane

미니 프레임 창의 창이 숨겨지거나 표시될 때 프레임워크에서 호출됩니다.

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
진행 표시 하거나 숨기는 창입니다.

*bShow*<br/>
진행 창이 표시 되는 경우 TRUE입니다. 창을 숨기면 FALSE이 고,

### <a name="remarks"></a>설명

미니 프레임 창의 창이 표시 되거나 숨겨질 때 프레임 워크에서 호출 됩니다. 기본 구현은 아무 작업도 수행하지 않습니다.

## <a name="cpaneframewndpin"></a><a name="pin"></a> CPaneFrameWnd::P

```cpp
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>매개 변수

진행 *Bpin*<br/>

### <a name="remarks"></a>설명

## <a name="cpaneframewndpanefrompoint"></a><a name="panefrompoint"></a> CPaneFrameWnd::P aneFromPoint

미니 프레임 창 안에 사용자가 제공한 지점을 포함하는 경우 창을 반환합니다.

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
진행 사용자가 화면 좌표에서 클릭 한 지점입니다.

*nSensitivity*<br/>
진행 이 매개 변수는 사용 되지 않습니다.

*bCheckVisibility*<br/>
진행 표시 되는 창만 반환 되도록 지정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

사용자가 클릭 한 창 이거나, 해당 위치에 창이 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

지정 된 지점을 포함 하는 창을 가져오려면이 메서드를 호출 합니다.

## <a name="cpaneframewndredrawall"></a><a name="redrawall"></a> CPaneFrameWnd:: RedrawAll

모든 미니 프레임 창을 다시 그립니다.

```
static void RedrawAll();
```

### <a name="remarks"></a>설명

이 메서드는 각 창에 대해 [CWnd:: RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) 를 호출 하 여 모든 미니 프레임 창을 업데이트 합니다.

## <a name="cpaneframewndremovenonvalidpanes"></a><a name="removenonvalidpanes"></a> CPaneFrameWnd:: Removenon유효한 창

잘못된 창을 제거하기 위해 프레임워크에서 호출됩니다.

```
virtual void RemoveNonValidPanes();
```

## <a name="cpaneframewndremovepane"></a><a name="removepane"></a> CPaneFrameWnd:: RemovePane

미니 프레임 창에서 창을 제거합니다.

```
virtual void RemovePane(
    CBasePane* pWnd,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = FALSE);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 제거할 창에 대 한 포인터입니다.

*bDestroy*<br/>
진행 미니 프레임 창에서 발생 하는 결과를 지정 합니다. *Bdestroy* 이 TRUE 이면이 메서드는 미니 프레임 창을 즉시 소멸 시킵니다. FALSE 인 경우이 메서드는 특정 지연 후 미니 프레임 창을 소멸 시킵니다.

*bNoDelayedDestroy*<br/>
진행 TRUE 이면 지연 된 소멸을 사용할 수 없습니다. FALSE 이면 지연 된 소멸이 사용 됩니다.

### <a name="remarks"></a>설명

프레임 워크는 미니 프레임 창을 즉시 제거 하거나 특정 지연 후에 제거할 수 있습니다. 미니 프레임 창의 소멸을 지연 시키려면 *Bnodelayeddestroy* 매개 변수에서 FALSE를 전달 합니다. 지연 된 소멸은 프레임 워크가 AFX_WM_CHECKEMPTYMINIFRAME 메시지를 처리할 때 발생 합니다.

## <a name="cpaneframewndreplacepane"></a><a name="replacepane"></a> CPaneFrameWnd:: ReplacePane

한 창을 다른 창으로 대체합니다.

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>매개 변수

*P바 조직*<br/>
진행 원래 창에 대 한 포인터입니다.

*pBarReplaceWith*<br/>
진행 원본 창을 대체 하는 창에 대 한 포인터입니다.

## <a name="cpaneframewndsavestate"></a><a name="savestate"></a> CPaneFrameWnd:: SaveState

레지스트리에 창의 상태를 저장합니다.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 프로필 이름입니다.

*uiID*<br/>
진행 창 ID입니다.

### <a name="return-value"></a>반환 값

창 상태가 성공적으로 저장 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cpaneframewndsetcaptionbuttons"></a><a name="setcaptionbuttons"></a> CPaneFrameWnd:: SetCaptionButtons

캡션 단추를 설정합니다.

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>매개 변수

*dwButtons*<br/>
진행 다음 값의 비트 OR 조합입니다.

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

## <a name="cpaneframewndsetdelayshow"></a><a name="setdelayshow"></a> CPaneFrameWnd:: SetDelayShow

```cpp
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>매개 변수

진행 *Bdelayshow*<br/>

### <a name="remarks"></a>설명

## <a name="cpaneframewndsetdockingmanager"></a><a name="setdockingmanager"></a> CPaneFrameWnd:: SetDockingManager

```cpp
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>매개 변수

진행 *Pmanager*<br/>

### <a name="remarks"></a>설명

## <a name="cpaneframewndsetdockingtimer"></a><a name="setdockingtimer"></a> CPaneFrameWnd:: SetDockingTimer

도킹 타이머를 설정합니다.

```cpp
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>매개 변수

*nTimeOut*<br/>
진행 시간 제한 값 (밀리초)입니다.

## <a name="cpaneframewndsetdockstate"></a><a name="setdockstate"></a> CPaneFrameWnd:: SetDockState

도킹 상태를 설정합니다.

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>매개 변수

*pDockManager*<br/>
진행 도킹 관리자에 대 한 포인터입니다.

## <a name="cpaneframewndsethotpoint"></a><a name="sethotpoint"></a> CPaneFrameWnd:: SetHotPoint

```cpp
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>매개 변수

진행 *Ptnew*<br/>

### <a name="remarks"></a>설명

## <a name="cpaneframewndsetpredockstate"></a><a name="setpredockstate"></a> CPaneFrameWnd:: SetPreDockState

사전 도킹 상태를 설정하기 위해 프레임워크에서 호출됩니다.

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>매개 변수

*preDockState*<br/>
진행 가능한 값:

- PDS_NOTHING,

- PDS_DOCK_REGULAR,

- PDS_DOCK_TO_TAB

*P바 Todock*<br/>
진행 도킹할 창에 대 한 포인터입니다.

*dockMethod*<br/>
진행 도킹 메서드입니다. 이 매개 변수는 무시 됩니다.

### <a name="return-value"></a>반환 값

미니 프레임 창이 도킹 해제 되어 있으면 TRUE이 고, 도킹 된 경우 FALSE입니다.

## <a name="cpaneframewndsizetocontent"></a><a name="sizetocontent"></a> CPaneFrameWnd:: System.windows.window.sizetocontent

포함 된 창과 동일 하도록 미니 프레임 창의 크기를 조정 합니다.

```
virtual void SizeToContent();
```

### <a name="remarks"></a>설명

미니 프레임 창의 크기를 포함 된 창의 크기로 조정 하려면이 메서드를 호출 합니다.

## <a name="cpaneframewndstarttearoff"></a><a name="starttearoff"></a> CPaneFrameWnd:: StartTearOff

메뉴를 분리합니다.

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>매개 변수

*pMenu*<br/>
진행 메뉴에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cpaneframewndstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a> CPaneFrameWnd:: StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>매개 변수

진행 *Pbar*<br/>

### <a name="remarks"></a>설명

## <a name="cpaneframewndstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a> CPaneFrameWnd:: StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>매개 변수

진행 *pDockingBar*<br/>
진행 *pTabbedBar*<br/>

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)
