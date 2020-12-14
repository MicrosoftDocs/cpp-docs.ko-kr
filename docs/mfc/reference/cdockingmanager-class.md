---
description: '자세히 알아보기: CDockingManager 클래스'
title: CDockingManager 클래스
ms.date: 11/04/2016
f1_keywords:
- CDockingManager
- AFXDOCKINGMANAGER/CDockingManager
- AFXDOCKINGMANAGER/CDockingManager::AddDockSite
- AFXDOCKINGMANAGER/CDockingManager::AddHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::AddMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::AddPane
- AFXDOCKINGMANAGER/CDockingManager::AdjustDockingLayout
- AFXDOCKINGMANAGER/CDockingManager::AdjustPaneFrames
- AFXDOCKINGMANAGER/CDockingManager::AdjustRectToClientArea
- AFXDOCKINGMANAGER/CDockingManager::AlignAutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::AutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::BringBarsToTop
- AFXDOCKINGMANAGER/CDockingManager::BuildPanesMenu
- AFXDOCKINGMANAGER/CDockingManager::CalcExpectedDockedRect
- AFXDOCKINGMANAGER/CDockingManager::Create
- AFXDOCKINGMANAGER/CDockingManager::DeterminePaneAndStatus
- AFXDOCKINGMANAGER/CDockingManager::DisableRestoreDockState
- AFXDOCKINGMANAGER/CDockingManager::DockPane
- AFXDOCKINGMANAGER/CDockingManager::DockPaneLeftOf
- AFXDOCKINGMANAGER/CDockingManager::EnableAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::EnableDocking
- AFXDOCKINGMANAGER/CDockingManager::EnableDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::EnablePaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::FindDockSite
- AFXDOCKINGMANAGER/CDockingManager::FindDockSiteByPane
- AFXDOCKINGMANAGER/CDockingManager::FindPaneByID
- AFXDOCKINGMANAGER/CDockingManager::FixupVirtualRects
- AFXDOCKINGMANAGER/CDockingManager::FrameFromPoint
- AFXDOCKINGMANAGER/CDockingManager::GetClientAreaBounds
- AFXDOCKINGMANAGER/CDockingManager::GetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::GetDockSiteFrameWnd
- AFXDOCKINGMANAGER/CDockingManager::GetEnabledAutoHideAlignment
- AFXDOCKINGMANAGER/CDockingManager::GetMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::GetOuterEdgeBounds
- AFXDOCKINGMANAGER/CDockingManager::GetPaneList
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManager
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManagerPermanent
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingTheme
- AFXDOCKINGMANAGER/CDockingManager::HideAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::InsertDockSite
- AFXDOCKINGMANAGER/CDockingManager::InsertPane
- AFXDOCKINGMANAGER/CDockingManager::IsDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::IsInAdjustLayout
- AFXDOCKINGMANAGER/CDockingManager::IsOLEContainerMode
- AFXDOCKINGMANAGER/CDockingManager::IsPointNearDockSite
- AFXDOCKINGMANAGER/CDockingManager::IsPrintPreviewValid
- AFXDOCKINGMANAGER/CDockingManager::LoadState
- AFXDOCKINGMANAGER/CDockingManager::LockUpdate
- AFXDOCKINGMANAGER/CDockingManager::OnActivateFrame
- AFXDOCKINGMANAGER/CDockingManager::OnClosePopupMenu
- AFXDOCKINGMANAGER/CDockingManager::OnMoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::OnPaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::PaneFromPoint
- AFXDOCKINGMANAGER/CDockingManager::ProcessPaneContextMenuCommand
- AFXDOCKINGMANAGER/CDockingManager::RecalcLayout
- AFXDOCKINGMANAGER/CDockingManager::ReleaseEmptyPaneContainers
- AFXDOCKINGMANAGER/CDockingManager::RemoveHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::RemoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::RemovePaneFromDockManager
- AFXDOCKINGMANAGER/CDockingManager::ReplacePane
- AFXDOCKINGMANAGER/CDockingManager::ResortMiniFramesForZOrder
- AFXDOCKINGMANAGER/CDockingManager::SaveState
- AFXDOCKINGMANAGER/CDockingManager::SendMessageToMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::Serialize
- AFXDOCKINGMANAGER/CDockingManager::SetAutohideZOrder
- AFXDOCKINGMANAGER/CDockingManager::SetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::SetDockState
- AFXDOCKINGMANAGER/CDockingManager::SetPrintPreviewMode
- AFXDOCKINGMANAGER/CDockingManager::SetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::ShowDelayShowMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::ShowPanes
- AFXDOCKINGMANAGER/CDockingManager::StartSDocking
- AFXDOCKINGMANAGER/CDockingManager::StopSDocking
- AFXDOCKINGMANAGER/CDockingManager::m_bHideDockingBarsInContainerMode
- AFXDOCKINGMANAGER/CDockingManager::m_dockModeGlobal
- AFXDOCKINGMANAGER/CDockingManager::m_nDockSensitivity
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeDockingBarDock
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeToolBarDock
helpviewer_keywords:
- CDockingManager [MFC], AddDockSite
- CDockingManager [MFC], AddHiddenMDITabbedBar
- CDockingManager [MFC], AddMiniFrame
- CDockingManager [MFC], AddPane
- CDockingManager [MFC], AdjustDockingLayout
- CDockingManager [MFC], AdjustPaneFrames
- CDockingManager [MFC], AdjustRectToClientArea
- CDockingManager [MFC], AlignAutoHidePane
- CDockingManager [MFC], AutoHidePane
- CDockingManager [MFC], BringBarsToTop
- CDockingManager [MFC], BuildPanesMenu
- CDockingManager [MFC], CalcExpectedDockedRect
- CDockingManager [MFC], Create
- CDockingManager [MFC], DeterminePaneAndStatus
- CDockingManager [MFC], DisableRestoreDockState
- CDockingManager [MFC], DockPane
- CDockingManager [MFC], DockPaneLeftOf
- CDockingManager [MFC], EnableAutoHidePanes
- CDockingManager [MFC], EnableDocking
- CDockingManager [MFC], EnableDockSiteMenu
- CDockingManager [MFC], EnablePaneContextMenu
- CDockingManager [MFC], FindDockSite
- CDockingManager [MFC], FindDockSiteByPane
- CDockingManager [MFC], FindPaneByID
- CDockingManager [MFC], FixupVirtualRects
- CDockingManager [MFC], FrameFromPoint
- CDockingManager [MFC], GetClientAreaBounds
- CDockingManager [MFC], GetDockingMode
- CDockingManager [MFC], GetDockSiteFrameWnd
- CDockingManager [MFC], GetEnabledAutoHideAlignment
- CDockingManager [MFC], GetMiniFrames
- CDockingManager [MFC], GetOuterEdgeBounds
- CDockingManager [MFC], GetPaneList
- CDockingManager [MFC], GetSmartDockingManager
- CDockingManager [MFC], GetSmartDockingManagerPermanent
- CDockingManager [MFC], GetSmartDockingParams
- CDockingManager [MFC], GetSmartDockingTheme
- CDockingManager [MFC], HideAutoHidePanes
- CDockingManager [MFC], InsertDockSite
- CDockingManager [MFC], InsertPane
- CDockingManager [MFC], IsDockSiteMenu
- CDockingManager [MFC], IsInAdjustLayout
- CDockingManager [MFC], IsOLEContainerMode
- CDockingManager [MFC], IsPointNearDockSite
- CDockingManager [MFC], IsPrintPreviewValid
- CDockingManager [MFC], LoadState
- CDockingManager [MFC], LockUpdate
- CDockingManager [MFC], OnActivateFrame
- CDockingManager [MFC], OnClosePopupMenu
- CDockingManager [MFC], OnMoveMiniFrame
- CDockingManager [MFC], OnPaneContextMenu
- CDockingManager [MFC], PaneFromPoint
- CDockingManager [MFC], ProcessPaneContextMenuCommand
- CDockingManager [MFC], RecalcLayout
- CDockingManager [MFC], ReleaseEmptyPaneContainers
- CDockingManager [MFC], RemoveHiddenMDITabbedBar
- CDockingManager [MFC], RemoveMiniFrame
- CDockingManager [MFC], RemovePaneFromDockManager
- CDockingManager [MFC], ReplacePane
- CDockingManager [MFC], ResortMiniFramesForZOrder
- CDockingManager [MFC], SaveState
- CDockingManager [MFC], SendMessageToMiniFrames
- CDockingManager [MFC], Serialize
- CDockingManager [MFC], SetAutohideZOrder
- CDockingManager [MFC], SetDockingMode
- CDockingManager [MFC], SetDockState
- CDockingManager [MFC], SetPrintPreviewMode
- CDockingManager [MFC], SetSmartDockingParams
- CDockingManager [MFC], ShowDelayShowMiniFrames
- CDockingManager [MFC], ShowPanes
- CDockingManager [MFC], StartSDocking
- CDockingManager [MFC], StopSDocking
- CDockingManager [MFC], m_bHideDockingBarsInContainerMode
- CDockingManager [MFC], m_dockModeGlobal
- CDockingManager [MFC], m_nDockSensitivity
- CDockingManager [MFC], m_nTimeOutBeforeDockingBarDock
- CDockingManager [MFC], m_nTimeOutBeforeToolBarDock
ms.assetid: 98e69c43-55d8-4f43-b861-4fda80ec1e32
ms.openlocfilehash: 5bbcc2a31739a5a81d66713bab47662b96c74e50
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185052"
---
# <a name="cdockingmanager-class"></a>CDockingManager 클래스

주 프레임 창에서 도킹 레이아웃을 제어하는 핵심 기능을 구현합니다.

## <a name="syntax"></a>구문

```
class CDockingManager : public CObject
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDockingManager::AddDockSite](#adddocksite)|도킹 창을 만들어 컨트롤 막대 목록에 추가 합니다.|
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|숨겨진 MDI 탭 모음 창 목록에 막대 창에 핸들을 추가 합니다.|
|[CDockingManager::AddMiniFrame](#addminiframe)|미니 프레임 목록에 프레임을 추가 합니다.|
|[CDockingManager:: AddPane](#addpane)|도킹 관리자를 사용 하 여 창을 등록 합니다.|
|[CDockingManager:: AdjustDockingLayout](#adjustdockinglayout)|프레임 창에 있는 모든 창의 레이아웃을 다시 계산 하 고 조정 합니다.|
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|WM_NCCALCSIZE 메시지를 모든 창과 창으로 보냅니다 `CPaneFrameWnd` .|
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|사각형의 맞춤을 조정 합니다.|
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|도킹 창 크기를 자동으로 자동 숨기기 모드로 조정 하 여 프레임의 클라이언트 영역에 대 한 전체 너비나 높이를 dock 사이트에 적용 합니다.|
|[CDockingManager::AutoHidePane](#autohidepane)|자동 숨기기 도구 모음을 만듭니다.|
|[CDockingManager:: Bring바 Stotop](#bringbarstotop)|지정 된 맞춤을 가진 도킹 된 막대를 위쪽에 가져옵니다.|
|[CDockingManager:: BuildPanesMenu](#buildpanesmenu)|도킹 창 및 도구 모음의 이름을 메뉴에 추가 합니다.|
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|도킹 된 창의 예상 사각형을 계산 합니다.|
|[CDockingManager:: Create](#create)|도킹 관리자를 만듭니다.|
|[CDockingManager::D eterminePaneAndStatus](#determinepaneandstatus)|지정 된 지점 및 해당 도킹 상태를 포함 하는 창을 확인 합니다.|
|[CDockingManager::D isableRestoreDockState](#disablerestoredockstate)|레지스트리에서 도킹 레이아웃 로드를 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CDockingManager::D ockPane](#dockpane)|창을 다른 창이 나 프레임 창에 도킹 합니다.|
|[CDockingManager::D ockPaneLeftOf](#dockpaneleftof)|창을 다른 창의 왼쪽에 도킹합니다.|
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|주 프레임에 창을 도킹할 수 있도록 하 고 도킹 창을 만든 다음 컨트롤 막대 목록에 추가 합니다.|
|[CDockingManager:: EnableDocking](#enabledocking)|도킹 창을 만들고 창을 주 프레임에 도킹할 수 있도록 합니다.|
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|모든 도킹 창의 캡션에 팝업 메뉴를 여는 추가 단추를 표시 합니다.|
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|사용자가 마우스 오른쪽 단추를 클릭 하 고 라이브러리가 WM_CONTEXTMENU 메시지를 처리 하는 경우 응용 프로그램 도구 모음 및 도킹 창 목록이 있는 특수 상황에 맞는 메뉴를 표시 하도록 라이브러리에 지시 합니다.|
|[CDockingManager::FindDockSite](#finddocksite)|지정 된 위치에 있고 지정 된 맞춤이 있는 막대 창을 검색 합니다.|
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|대상 막대 창의 id가 있는 막대 창을 반환 합니다.|
|[CDockingManager::FindPaneByID](#findpanebyid)|지정 된 컨트롤 ID로 창을 찾습니다.|
|[CDockingManager:: FixupVirtualRects](#fixupvirtualrects)|모든 현재 도구 모음 위치를 가상 사각형에 커밋합니다.|
|[CDockingManager:: 프레임 위치](#framefrompoint)|지정 된 지점을 포함 하는 프레임을 반환 합니다.|
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|클라이언트 영역의 경계를 포함 하는 사각형을 가져옵니다.|
|[CDockingManager::GetDockingMode](#getdockingmode)|현재 도킹 모드를 반환 합니다.|
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|부모 창 프레임에 대 한 포인터를 가져옵니다.|
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|창의 설정 맞춤을 반환 합니다.|
|[CDockingManager:: Get미니 프레임](#getminiframes)|미니 프레임의 목록을 가져옵니다.|
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|프레임의 바깥쪽 가장자리를 포함 하는 사각형을 가져옵니다.|
|[CDockingManager::GetPaneList](#getpanelist)|도킹 관리자에 속한 창 목록을 반환 합니다. 여기에는 모든 부동 창이 포함 됩니다.|
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|스마트 도킹 관리자에 대 한 포인터를 검색 합니다.|
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|스마트 도킹 관리자에 대 한 포인터를 검색 합니다.|
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|도킹 관리자의 스마트 도킹 매개 변수를 반환 합니다.|
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|스마트 도킹 표식을 표시 하는 데 사용 되는 테마를 반환 하는 정적 메서드입니다.|
|[CDockingManager::HideAutoHidePanes](#hideautohidepanes)|자동 숨기기 모드인 창을 숨깁니다.|
|[CDockingManager::InsertDockSite](#insertdocksite)|도킹 창을 만들어 컨트롤 막대 목록에 삽입 합니다.|
|[CDockingManager:: InsertPane](#insertpane)|컨트롤 막대 목록에 컨트롤 창을 삽입 합니다.|
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|모든 창의 캡션에 팝업 메뉴를 표시할지 여부를 지정 합니다.|
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|모든 창의 레이아웃이 조정 되는지 여부를 결정 합니다.|
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|도킹 관리자가 OLE 컨테이너 모드에 있는지 여부를 지정 합니다.|
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|지정 된 지점이 dock 사이트 근처에 있는지 여부를 확인 합니다.|
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|인쇄 미리 보기 모드가 설정 되어 있는지 여부를 확인 합니다.|
|[CDockingManager:: LoadState](#loadstate)|레지스트리에서 도킹 관리자의 상태를 로드 합니다.|
|[CDockingManager:: LockUpdate](#lockupdate)|지정 된 창을 잠급니다.|
|[CDockingManager:: OnActivateFrame](#onactivateframe)|프레임 창이 활성화 되거나 비활성화 될 때 프레임 워크에서 호출 됩니다.|
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|활성 팝업 메뉴에서 WM_DESTROY 메시지를 처리할 때 프레임워크에서 호출됩니다.|
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|미니 프레임 창을 이동 하기 위해 프레임 워크에서 호출 됩니다.|
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|창 목록을 포함 하는 메뉴를 빌드할 때 프레임 워크에서 호출 됩니다.|
|[CDockingManager::P aneFromPoint](#panefrompoint)|지정 된 지점을 포함 하는 창을 반환 합니다.|
|[CDockingManager::P rocessPaneContextMenuCommand](#processpanecontextmenucommand)|지정 된 명령에 대 한 확인란을 선택 하거나 선택을 취소 하 고 표시 된 창의 레이아웃을 다시 계산 하기 위해 프레임 워크에서 호출 됩니다.|
|[CDockingManager:: RecalcLayout](#recalclayout)|컨트롤 목록에 있는 컨트롤의 내부 레이아웃을 다시 계산 합니다.|
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|빈 창 컨테이너를 해제 합니다.|
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|지정 된 숨겨진 막대 창을 제거 합니다.|
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|미니 프레임 목록에서 지정 된 프레임을 제거 합니다.|
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|창의 등록을 취소 하 고 도킹 관리자의 목록에서 제거 합니다.|
|[CDockingManager::ReplacePane](#replacepane)|한 창을 다른 창으로 대체합니다.|
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|미니 프레임 목록에서 프레임을 리조트 합니다.|
|[CDockingManager:: SaveState](#savestate)|도킹 관리자의 상태를 레지스트리에 저장 합니다.|
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|지정 된 메시지를 모든 미니 프레임으로 보냅니다.|
|[CDockingManager:: Serialize](#serialize)|도킹 관리자를 보관 파일에 씁니다. ( [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)를 재정의합니다.)|
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|컨트롤 막대와 지정 된 창의 크기, 너비 및 높이를 설정 합니다.|
|[CDockingManager::SetDockingMode](#setdockingmode)|도킹 모드를 설정 합니다.|
|[CDockingManager::SetDockState](#setdockstate)|컨트롤 막대, 미니 프레임 및 자동 숨기기 막대의 도킹 상태를 설정 합니다.|
|[CDockingManager:: SetPrintPreviewMode](#setprintpreviewmode)|인쇄 미리 보기에 표시 되는 막대의 인쇄 미리 보기 모드를 설정 합니다.|
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|스마트 도킹의 동작을 정의 하는 매개 변수를 설정 합니다.|
|[CDockingManager:: Showdelayshow미니 프레임](#showdelayshowminiframes)|미니 프레임의 창을 표시 하거나 숨깁니다.|
|[CDockingManager:: ShowPanes](#showpanes)|컨트롤의 창과 자동 숨기기 막대를 표시 하거나 숨깁니다.|
|[CDockingManager:: StartSDocking](#startsdocking)|스마트 도킹 관리자의 맞춤에 따라 지정 된 창의 스마트 도킹을 시작 합니다.|
|[CDockingManager:: StopSDocking](#stopsdocking)|스마트 도킹을 중지 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDockingManager:: m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|도킹 관리자가 OLE 컨테이너 모드에서 창을 숨길지 여부를 지정 합니다.|
|[CDockingManager:: m_dockModeGlobal](#m_dockmodeglobal)|전역 도킹 모드를 지정 합니다.|
|[CDockingManager:: m_nDockSensitivity](#m_ndocksensitivity)|도킹 민감도를 지정 합니다.|
|[CDockingManager:: m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|도킹 창이 즉시 도킹 모드로 도킹 되기 전의 시간 (밀리초)을 지정 합니다.|
|[CDockingManager:: m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|주 프레임 창에 도구 모음이 도킹 되기 전의 시간 (밀리초)을 지정 합니다.|

## <a name="remarks"></a>설명

주 프레임 창에서이 클래스를 자동으로 만들고 초기화 합니다.

도킹 관리자 개체는 도킹 레이아웃에 있는 모든 창의 목록과 주 프레임 창에 속하는 모든 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) 창 목록을 포함 합니다.

`CDockingManager`클래스는 창이 나 창을 찾는 데 사용할 수 있는 일부 서비스를 구현 `CPaneFrameWnd` 합니다. 일반적으로 이러한 서비스는 주 프레임 창 개체에 래핑되어 있으므로 직접 호출 하지 않습니다. 자세한 내용은 [CPaneFrameWnd 클래스](../../mfc/reference/cpaneframewnd-class.md)를 참조 하세요.

## <a name="customization-tips"></a>사용자 지정 팁

개체에 적용 되는 팁은 다음과 `CDockingManager` 같습니다.

- [CDockingManager 클래스](../../mfc/reference/cdockingmanager-class.md) 는 다음 도킹 모드를 지원 합니다.

  - `AFX_DOCK_TYPE::DT_IMMEDIATE`

  - `AFX_DOCK_TYPE::DT_STANDARD`

  - `AFX_DOCK_TYPE::DT_SMART`

  이러한 도킹 모드는 [CDockingManager:: m_dockModeGlobal](#m_dockmodeglobal) 에 의해 정의 되며 [CDockingManager:: SetDockingMode](#setdockingmode)를 호출 하 여 설정 됩니다.

- 부동 및 크기 조정이 불가능 한 창을 만들려면 [CDockingManager:: addpane](#addpane) 메서드를 호출 합니다. 이 메서드는 창의 레이아웃을 담당 하는 도킹 관리자를 사용 하 여 창을 등록 합니다.

## <a name="example"></a>예제

다음 예제에서는 클래스에서 다양 한 메서드를 사용 하 여 개체를 구성 하는 방법을 보여 줍니다 `CDockingManager` `CDockingManager` . 이 예제에서는 모든 도킹 창의 캡션에 팝업 메뉴를 여는 방법 및 개체의 도킹 모드를 설정 하는 방법에 대 한 추가 단추를 표시 하는 방법을 보여 줍니다. 이 코드 조각은 [Visual Studio Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CDockingManager](../../mfc/reference/cdockingmanager-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxDockingManager

## <a name="cdockingmanageradddocksite"></a><a name="adddocksite"></a> CDockingManager::AddDockSite

도킹 창을 만들어 컨트롤 막대 목록에 추가 합니다.

```
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>매개 변수

*나타납니다*<br/>
진행 도킹 창 맞춤을 포함 하는 정보 구조체에 대 한 참조입니다.

*ppDockBar*<br/>
제한이 새 도킹 창에 대 한 포인터에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

도킹 창이 성공적으로 만들어졌으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanageraddhiddenmditabbedbar"></a><a name="addhiddenmditabbedbar"></a> CDockingManager::AddHiddenMDITabbedBar

숨겨진 MDI 탭 모음 창 목록에 막대 창에 핸들을 추가 합니다.

```cpp
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
진행 막대 창에 대 한 포인터입니다.

## <a name="cdockingmanageraddpane"></a><a name="addpane"></a> CDockingManager:: AddPane

도킹 관리자를 사용 하 여 창을 등록 합니다.

```
BOOL AddPane(
    CBasePane* pWnd,
    BOOL bTail = TRUE,
    BOOL bAutoHide = FALSE,
    BOOL bInsertForOuterEdge = FALSE);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
[in, out] 도킹 관리자에 추가할 창을 지정 합니다.

*bTail*<br/>
진행 도킹 관리자에 대 한 창 목록의 끝에 창을 추가 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

*bAutoHide 숨기기*<br/>
진행 내부용 으로만 사용 됩니다. 항상 기본값 FALSE를 사용 합니다.

*bInsertForOuterEdge*<br/>
진행 내부용 으로만 사용 됩니다. 항상 기본값 FALSE를 사용 합니다.

### <a name="return-value"></a>반환 값

창이 도킹 관리자에 성공적으로 등록 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

도킹 관리자를 사용 하 여 부동 크기의 비 크기 조정 가능 창을 등록 하려면이 메서드를 호출 합니다. 창을 등록 하지 않으면 도킹 관리자가 배치 될 때 올바르게 표시 되지 않습니다.

## <a name="cdockingmanageradjustdockinglayout"></a><a name="adjustdockinglayout"></a> CDockingManager:: AdjustDockingLayout

프레임 창에 있는 모든 창의 레이아웃을 다시 계산 하 고 조정 합니다.

```
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```

### <a name="parameters"></a>매개 변수

*hdwp*<br/>
진행 지연 된 창 위치 구조를 지정 합니다. 자세한 내용은 [Windows 데이터 형식](/windows/win32/WinProg/windows-data-types)을 참조하세요.

### <a name="remarks"></a>설명

## <a name="cdockingmanageraddminiframe"></a><a name="addminiframe"></a> CDockingManager::AddMiniFrame

미니 프레임 목록에 프레임을 추가 합니다.

```
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 프레임에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

프레임이 미니 프레임 목록에 없고 성공적으로 추가 되었으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanageradjustpaneframes"></a><a name="adjustpaneframes"></a> CDockingManager::AdjustPaneFrames

WM_NCCALCSIZE 메시지를 모든 창과 창으로 보냅니다 `CPaneFrameWnd` .

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>설명

## <a name="cdockingmanageradjustrecttoclientarea"></a><a name="adjustrecttoclientarea"></a> CDockingManager::AdjustRectToClientArea

사각형의 맞춤을 조정 합니다.

```
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,
    DWORD dwAlignment);
```

### <a name="parameters"></a>매개 변수

*rectResult*<br/>
진행 개체에 대 한 참조입니다. `CRect`

*dwAlignment*<br/>
진행 개체의 맞춤입니다. `CRect`

### <a name="return-value"></a>반환 값

개체 맞춤이 조정 되었으면 TRUE `CRect` 이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

*Dwalignment* 매개 변수는 다음 값 중 하나를 가질 수 있습니다.

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

## <a name="cdockingmanageralignautohidepane"></a><a name="alignautohidepane"></a> CDockingManager::AlignAutoHidePane

도킹 창 크기를 자동으로 자동 숨기기 모드로 조정 하 여 프레임의 클라이언트 영역에 대 한 전체 너비나 높이를 dock 사이트에 적용 합니다.

```cpp
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,
    BOOL bIsVisible = TRUE);
```

### <a name="parameters"></a>매개 변수

*pDefaultSlider*<br/>
진행 도킹 슬라이더 창입니다.

*bIsVisible*<br/>
진행 도킹 창이 표시 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanagerautohidepane"></a><a name="autohidepane"></a> CDockingManager::AutoHidePane

자동 숨기기 도구 모음을 만듭니다.

```
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
진행 막대 창에 대 한 포인터입니다.

*pCurrAutoHideToolBar*<br/>
진행 자동 숨기기 도구 모음에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

자동 숨기기 도구 모음을 만들지 않은 경우 NULL입니다. 그렇지 않으면 새 도구 모음에 대 한 포인터입니다.

## <a name="cdockingmanagerbringbarstotop"></a><a name="bringbarstotop"></a> CDockingManager:: Bring바 Stotop

지정 된 맞춤을 가진 도킹 된 막대를 위쪽에 가져옵니다.

```cpp
void BringBarsToTop(
    DWORD dwAlignment = 0,
    BOOL bExcludeDockedBars = TRUE);
```

### <a name="parameters"></a>매개 변수

*dwAlignment*<br/>
진행 다른 창의 맨 위에 가져오는 도크 막대의 맞춤입니다.

*bExcludeDockedBars*<br/>
진행 도킹 된 막대가 맨 위에 있지 않도록 하려면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanagerbuildpanesmenu"></a><a name="buildpanesmenu"></a> CDockingManager:: BuildPanesMenu

도킹 창 및 도구 모음의 이름을 메뉴에 추가 합니다.

```cpp
void BuildPanesMenu(
    CMenu& menu,
    BOOL bToolbarsOnly);
```

### <a name="parameters"></a>매개 변수

*메뉴가*<br/>
진행 도킹 창 및 도구 모음의 이름을 추가 하는 메뉴입니다.

*Bo s a s만*<br/>
진행 메뉴에 도구 모음 이름만 추가 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanagercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a> CDockingManager::CalcExpectedDockedRect

도킹 된 창의 예상 사각형을 계산 합니다.

```cpp
void CalcExpectedDockedRect(
    CWnd* pWnd,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 도킹할 창에 대 한 포인터입니다.

*ptMouse*<br/>
진행 마우스 위치입니다.

*rectResult*<br/>
제한이 계산 된 사각형입니다.

*bDrawTab*<br/>
진행 탭을 그리려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

*ppTargetBar*<br/>
제한이 대상 창에 대 한 포인터에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 사용자가 *단추를 ptmouse* 에서 지정한 지점으로 끌고 거기에 도킹 한 경우 창이 차지할 사각형을 계산 합니다.

## <a name="cdockingmanagercreate"></a><a name="create"></a> CDockingManager:: Create

도킹 관리자를 만듭니다.

```
BOOL Create(CFrameWnd* pParentWnd);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
진행 도킹 관리자의 부모 프레임에 대 한 포인터입니다. 이 값은 NULL이 아니어야 합니다.

### <a name="return-value"></a>반환 값

항상 TRUE입니다.

## <a name="cdockingmanagerdeterminepaneandstatus"></a><a name="determinepaneandstatus"></a> CDockingManager::D eterminePaneAndStatus

지정 된 지점 및 해당 도킹 상태를 포함 하는 창을 확인 합니다.

```
virtual AFX_CS_STATUS DeterminePaneAndStatus(
    CPoint pt,
    int nSensitivity,
    DWORD dwEnabledAlignment,
    CBasePane** ppTargetBar,
    const CBasePane* pBarToIgnore,
    const CBasePane* pBarToDock);
```

### <a name="parameters"></a>매개 변수

*pt*<br/>
진행 확인할 창의 위치입니다.

*nSensitivity*<br/>
진행 선택 된 각 창의 창 사각형을 증가 시킬 값입니다. 지정 된 지점이이 증가 하는 영역에 있는 경우 창은 검색 조건을 충족 합니다.

*dwEnabledAlignment*<br/>
진행 도킹 창의 맞춤입니다.

*ppTargetBar*<br/>
제한이 대상 창에 대 한 포인터에 대 한 포인터입니다.

*pBarToIgnore*<br/>
진행 메서드가 무시 하는 창입니다.

*P바 Todock*<br/>
진행 도킹 된 창입니다.

### <a name="return-value"></a>반환 값

도킹 상태입니다.

### <a name="remarks"></a>설명

도킹 상태는 다음 값 중 하나일 수 있습니다.

|AFX_CS_STATUS 값|의미|
|---------------------------|-------------|
|CS_NOTHING|포인터가 도크 사이트를 벗어났습니다. 따라서 창을 부동 상태로 유지 합니다.|
|CS_DOCK_IMMEDIATELY|포인터가 직접 실행 모드 (DT_IMMEDIATE 스타일 사용)에서 도킹 사이트 위에 있으므로 창을 즉시 도킹 해야 합니다.|
|CS_DELAY_DOCK|포인터는 다른 도킹 창이 나 주 프레임의 가장자리에 해당 하는 도크 사이트 위에 있습니다.|
|CS_DELAY_DOCK_TO_TAB|포인터가 탭 창에 도킹 되는 도킹 사이트 위에 있습니다. 이는 마우스가 다른 도킹 창이 나 탭 창에 있는 탭 영역의 캡션에 있을 때 발생 합니다.|

## <a name="cdockingmanagerdisablerestoredockstate"></a><a name="disablerestoredockstate"></a> CDockingManager::D isableRestoreDockState

레지스트리에서 도킹 레이아웃 로드를 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void DisableRestoreDockState(BOOL bDisable = TRUE);
```

### <a name="parameters"></a>매개 변수

*함*<br/>
진행 레지스트리에서 도킹 레이아웃 로드를 사용 하지 않도록 설정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

응용 프로그램 상태를 로드할 때 도킹 창 및 도구 모음의 현재 레이아웃을 유지 해야 하는 경우이 메서드를 호출 합니다.

## <a name="cdockingmanagerdockpane"></a><a name="dockpane"></a> CDockingManager::D ockPane

창을 다른 창이 나 프레임 창에 도킹 합니다.

```cpp
void DockPane(
    CBasePane* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
진행 도킹할 막대 창에 대 한 포인터입니다.

*nDockBarID*<br/>
진행 도킹할 막대의 id입니다.

*lpRect*<br/>
진행 대상 사각형입니다.

## <a name="cdockingmanagerdockpaneleftof"></a><a name="dockpaneleftof"></a> CDockingManager::D ockPaneLeftOf

창을 다른 창의 왼쪽에 도킹합니다.

```
BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>매개 변수

*P바 Todock*<br/>
진행 *Ptargetbar* 왼쪽에 도킹할 창에 대 한 포인터입니다.

*pTargetBar*<br/>
진행 대상 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

창이 성공적으로 도킹 되었으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanagerenableautohidepanes"></a><a name="enableautohidepanes"></a> CDockingManager::EnableAutoHidePanes

주 프레임에 창을 도킹할 수 있도록 하 고 도킹 창을 만든 다음 컨트롤 막대 목록에 추가 합니다.

```
BOOL EnableAutoHidePanes(DWORD dwStyle);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
진행 도킹 맞춤입니다.

### <a name="return-value"></a>반환 값

도킹 창이 성공적으로 만들어졌으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanagerenabledocking"></a><a name="enabledocking"></a> CDockingManager:: EnableDocking

도킹 창을 만들고 창을 주 프레임에 도킹할 수 있도록 합니다.

```
BOOL EnableDocking(DWORD dwStyle);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
진행 도킹 맞춤입니다.

### <a name="return-value"></a>반환 값

도킹 창이 성공적으로 만들어졌으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanagerenabledocksitemenu"></a><a name="enabledocksitemenu"></a> CDockingManager::EnableDockSiteMenu

모든 도킹 창의 캡션에 팝업 메뉴를 여는 추가 단추를 표시 합니다.

```
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 Dock 사이트 메뉴를 사용 하도록 설정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

Dock 사이트 메뉴에는 창의 도킹 상태를 변경 하는 다음과 같은 옵션이 표시 됩니다.

- `Floating` -창을 부동으로 만듭니다.

- `Docking` -창이 마지막으로 도킹 된 위치의 주 프레임에서 창을 도킹 합니다.

- `AutoHide` -창을 자동 숨기기 모드로 전환 합니다.

- `Hide` -창을 숨깁니다.

기본적으로이 메뉴는 표시 되지 않습니다.

## <a name="cdockingmanagerenablepanecontextmenu"></a><a name="enablepanecontextmenu"></a> CDockingManager::EnablePaneContextMenu

사용자가 마우스 오른쪽 단추를 클릭 하 고 라이브러리가 WM_CONTEXTMENU 메시지를 처리 하는 경우 응용 프로그램 도구 모음 및 도킹 창 목록이 있는 특수 상황에 맞는 메뉴를 표시 하도록 라이브러리에 지시 합니다.

```cpp
void EnablePaneContextMenu(
    BOOL bEnable,
    UINT uiCustomizeCmd,
    const CString& strCustomizeText,
    BOOL bToolbarsOnly = FALSE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 TRUE 이면 라이브러리가 자동 상황에 맞는 메뉴에 대 한 지원을 설정 합니다. FALSE 이면 라이브러리가 자동 상황에 맞는 메뉴에 대 한 지원 기능을 해제 합니다.

*uiCustomizeCmd*<br/>
진행 메뉴의 **사용자 지정** 항목에 대 한 명령 id입니다.

*strCustomizeText*<br/>
진행 **사용자 지정** 항목의 텍스트입니다.

*Bo s a s만*<br/>
진행 TRUE 이면 메뉴에 응용 프로그램 도구 모음 목록만 표시 됩니다. FALSE 이면 라이브러리는 응용 프로그램 도킹 창을이 목록에 추가 합니다.

## <a name="cdockingmanagerfinddocksite"></a><a name="finddocksite"></a> CDockingManager::FindDockSite

지정 된 위치에 있고 지정 된 맞춤이 있는 막대 창을 검색 합니다.

```
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,
    BOOL bOuter);
```

### <a name="parameters"></a>매개 변수

*dwAlignment*<br/>
진행 막대 창의 맞춤입니다.

*bOuter*<br/>
진행 TRUE 이면 컨트롤 막대 목록에서 위쪽 위치의 막대를 검색 합니다. 그렇지 않으면 컨트롤 막대 목록에서 꼬리 위치의 막대를 검색 합니다.

### <a name="return-value"></a>반환 값

지정 된 맞춤이 지정 된 도킹 창 그렇지 않으면 NULL입니다.

## <a name="cdockingmanagerfindpanebyid"></a><a name="findpanebyid"></a> CDockingManager::FindPaneByID

지정 된 컨트롤 ID로 창을 찾습니다.

```
virtual CBasePane* FindPaneByID(
    UINT uBarID,
    BOOL bSearchMiniFrames = FALSE);
```

### <a name="parameters"></a>매개 변수

*U바 Id*<br/>
진행 찾을 창의 컨트롤 ID를 지정 합니다.

*Bsearch미니 프레임*<br/>
진행 검색에 모든 부동 창을 포함 하려면 TRUE로 설정 합니다. FALSE 이면 도킹 된 창만 포함 합니다.

### <a name="return-value"></a>반환 값

지정 된 컨트롤 ID를 가진 [Cbasepane](../../mfc/reference/cbasepane-class.md) 개체 이거나, 지정 된 창을 찾을 수 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

## <a name="cdockingmanagerfinddocksitebypane"></a><a name="finddocksitebypane"></a> CDockingManager::FindDockSiteByPane

대상 막대 창의 id가 있는 막대 창을 반환 합니다.

```
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```

### <a name="parameters"></a>매개 변수

*pTargetBar*<br/>
진행 대상 막대 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

대상 막대 창의 id가 있는 막대 창 이러한 막대 창이 없으면 NULL입니다.

## <a name="cdockingmanagerfixupvirtualrects"></a><a name="fixupvirtualrects"></a> CDockingManager:: FixupVirtualRects

모든 현재 도구 모음 위치를 가상 사각형에 커밋합니다.

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>설명

사용자가 도구 모음을 끌기 시작할 때 응용 프로그램은 *가상 사각형* 의 원래 위치를 기억 합니다. 사용자가 도킹 사이트에서 도구 모음을 이동 하면 도구 모음에서 다른 도구 모음이 이동 될 수 있습니다. 다른 도구 모음의 원래 위치는 해당 가상 사각형에 저장 됩니다.

## <a name="cdockingmanagerframefrompoint"></a><a name="framefrompoint"></a> CDockingManager:: 프레임 위치

지정 된 지점을 포함 하는 프레임을 반환 합니다.

```
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,
    CPaneFrameWnd* pFrameToExclude,
    BOOL bFloatMultiOnly) const;
```

### <a name="parameters"></a>매개 변수

*pt*<br/>
진행 확인할 지점을 화면 좌표로 지정 합니다.

*pFrameToExclude*<br/>
진행 제외할 프레임에 대 한 포인터입니다.

*bFloatMultiOnly*<br/>
진행 인스턴스가 아닌 프레임을 제외 하려면 TRUE로 설정 합니다 `CMultiPaneFrameWnd` . 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

지정 된 지점을 포함 하는 프레임입니다. 그렇지 않으면 NULL입니다.

## <a name="cdockingmanagergetclientareabounds"></a><a name="getclientareabounds"></a> CDockingManager::GetClientAreaBounds

클라이언트 영역의 경계를 포함 하는 사각형을 가져옵니다.

```
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```

### <a name="parameters"></a>매개 변수

*rcClient*<br/>
제한이 클라이언트 영역의 경계를 포함 하는 사각형에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

클라이언트 영역의 경계를 포함 하는 사각형입니다.

## <a name="cdockingmanagergetdockingmode"></a><a name="getdockingmode"></a> CDockingManager::GetDockingMode

현재 도킹 모드를 반환 합니다.

```
static AFX_DOCK_TYPE GetDockingMode();
```

### <a name="return-value"></a>반환 값

현재 도킹 모드를 나타내는 열거자 값입니다. 다음 값 중 하나일 수 있습니다.

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

### <a name="remarks"></a>설명

도킹 모드를 설정 하려면 [CDockingManager:: SetDockingMode](#setdockingmode)를 호출 합니다.

## <a name="cdockingmanagergetdocksiteframewnd"></a><a name="getdocksiteframewnd"></a> CDockingManager::GetDockSiteFrameWnd

부모 창 프레임에 대 한 포인터를 가져옵니다.

```
CFrameWnd* GetDockSiteFrameWnd() const;
```

### <a name="return-value"></a>반환 값

부모 창 프레임에 대 한 포인터입니다.

## <a name="cdockingmanagergetenabledautohidealignment"></a><a name="getenabledautohidealignment"></a> CDockingManager::GetEnabledAutoHideAlignment

창의 설정 맞춤을 반환 합니다.

```
DWORD GetEnabledAutoHideAlignment() const;
```

### <a name="return-value"></a>반환 값

CBRS_ALIGN_ 플래그의 비트 조합 이거나, 자동 숨기기 창이 사용 되지 않는 경우 0입니다. 자세한 내용은 [CFrameWnd:: EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking)를 참조 하세요.

### <a name="remarks"></a>설명

메서드는 자동 숨기기 컨트롤 막대에 대해 사용 하도록 설정 된 맞춤을 반환 합니다. 자동 숨기기 막대를 사용 하려면 [CFrameWndEx:: EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)를 호출 합니다.

## <a name="cdockingmanagergetminiframes"></a><a name="getminiframes"></a> CDockingManager:: Get미니 프레임

미니 프레임의 목록을 가져옵니다.

```
const CObList& GetMiniFrames() const;
```

### <a name="return-value"></a>반환 값

도킹 관리자에 속하는 컨트롤 막대를 포함 하는 미니 프레임의 목록입니다.

## <a name="cdockingmanagergetouteredgebounds"></a><a name="getouteredgebounds"></a> CDockingManager::GetOuterEdgeBounds

프레임의 바깥쪽 가장자리를 포함 하는 사각형을 가져옵니다.

```
CRect GetOuterEdgeBounds() const;
```

### <a name="return-value"></a>반환 값

프레임의 바깥쪽 가장자리를 포함 하는 사각형입니다.

## <a name="cdockingmanagergetpanelist"></a><a name="getpanelist"></a> CDockingManager::GetPaneList

도킹 관리자에 속한 창 목록을 반환 합니다. 여기에는 모든 부동 창이 포함 됩니다.

```cpp
void GetPaneList(
    CObList& lstBars,
    BOOL bIncludeAutohide = FALSE,
    CRuntimeClass* pRTCFilter = NULL,
    BOOL bIncludeTabs = FALSE);
```

### <a name="parameters"></a>매개 변수

*lstBars*<br/>
[in, out] 현재 도킹 관리자의 모든 창을 포함 합니다.

*bIncludeAutohide 숨기기*<br/>
진행 자동 숨기기 모드에 있는 창을 포함 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

*pRTCFilter 필터*<br/>
진행 NULL이 아닌 경우 반환 되는 목록에는 지정 된 런타임 클래스의 창만 포함 됩니다.

*bIncludeTabs*<br/>
진행 탭을 포함 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

도킹 관리자에 탭 창이 있으면 메서드가 [CBaseTabbedPane 클래스](../../mfc/reference/cbasetabbedpane-class.md) 개체에 대 한 포인터를 반환 하며, 탭을 명시적으로 열거 해야 합니다.

*Prtcfilter* 를 사용 하 여 특정 창 클래스를 가져옵니다. 예를 들어이 값을 적절 하 게 설정 하 여 도구 모음만 가져올 수 있습니다.

## <a name="cdockingmanagergetsmartdockingmanager"></a><a name="getsmartdockingmanager"></a> CDockingManager::GetSmartDockingManager

스마트 도킹 관리자에 대 한 포인터를 검색 합니다.

```
CSmartDockingManager* GetSmartDockingManager();
```

### <a name="return-value"></a>반환 값

스마트 도킹 관리자에 대 한 포인터입니다.

## <a name="cdockingmanagergetsmartdockingmanagerpermanent"></a><a name="getsmartdockingmanagerpermanent"></a> CDockingManager::GetSmartDockingManagerPermanent

스마트 도킹 관리자에 대 한 포인터를 검색 합니다.

```
CSmartDockingManager* GetSmartDockingManagerPermanent() const;
```

### <a name="return-value"></a>반환 값

스마트 도킹 관리자에 대 한 포인터입니다.

## <a name="cdockingmanagergetsmartdockingparams"></a><a name="getsmartdockingparams"></a> CDockingManager::GetSmartDockingParams

도킹 관리자의 스마트 도킹 매개 변수를 반환 합니다.

```
static CSmartDockingInfo& GetSmartDockingParams();
```

### <a name="return-value"></a>반환 값

현재 도킹 관리자의 스마트 도킹 매개 변수를 포함 하는 클래스입니다. 자세한 내용은 [CSmartDockingInfo 클래스](../../mfc/reference/csmartdockinginfo-class.md)를 참조 하세요.

### <a name="remarks"></a>설명

## <a name="cdockingmanagerhideautohidepanes"></a><a name="hideautohidepanes"></a> CDockingManager::HideAutoHidePanes

자동 숨기기 모드인 창을 숨깁니다.

```cpp
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,
    BOOL bImmediately = FALSE);
```

### <a name="parameters"></a>매개 변수

*P바 Toexclude*<br/>
진행 숨기기에서 제외할 막대에 대 한 포인터입니다.

*bImmediately*<br/>
진행 창을 즉시 숨기려면 TRUE로 설정 합니다. FALSE 이면 자동 숨기기 효과가 적용 된 창이 숨겨집니다.

## <a name="cdockingmanagerinsertdocksite"></a><a name="insertdocksite"></a> CDockingManager::InsertDockSite

도킹 창을 만들어 컨트롤 막대 목록에 삽입 합니다.

```
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,
    DWORD dwAlignToInsertAfter,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>매개 변수

*나타납니다*<br/>
진행 도킹 창에 대 한 맞춤 정보를 포함 하는 구조체입니다.

*dwAlignToInsertAfter*<br/>
진행 도크 창의 맞춤입니다.

*ppDockBar*<br/>
제한이 도킹 창에 대 한 포인터에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

도킹 창이 성공적으로 만들어졌으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanagerinsertpane"></a><a name="insertpane"></a> CDockingManager:: InsertPane

컨트롤 막대 목록에 컨트롤 창을 삽입 합니다.

```
BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter = TRUE);
```

### <a name="parameters"></a>매개 변수

*pControlBar*<br/>
진행 컨트롤 창에 대 한 포인터입니다.

*pTarget*<br/>
진행 대상 창에 대 한 포인터입니다.

*bAfter*<br/>
진행 대상 창의 위치 뒤에 창을 삽입 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

컨트롤 창이 컨트롤 막대 목록에 성공적으로 추가 되었으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 컨트롤 창이 컨트롤 막대 목록에 이미 있거나 대상 창이 컨트롤 막대 목록에 없는 경우 false를 반환 합니다.

## <a name="cdockingmanagerisdocksitemenu"></a><a name="isdocksitemenu"></a> CDockingManager::IsDockSiteMenu

모든 창의 캡션에 팝업 메뉴를 표시할지 여부를 지정 합니다.

```
static BOOL IsDockSiteMenu();
```

### <a name="return-value"></a>반환 값

도킹 사이트 메뉴가 모든 도킹 창의 캡션에 표시 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

[CDockingManager:: EnableDockSiteMenu](#enabledocksitemenu)를 호출 하 여 dock 사이트 메뉴를 사용 하도록 설정할 수 있습니다.

## <a name="cdockingmanagerisinadjustlayout"></a><a name="isinadjustlayout"></a> CDockingManager::IsInAdjustLayout

모든 창의 레이아웃이 조정 되는지 여부를 결정 합니다.

```
BOOL IsInAdjustLayout() const;
```

### <a name="return-value"></a>반환 값

모든 창의 레이아웃이 조정 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanagerisolecontainermode"></a><a name="isolecontainermode"></a> CDockingManager::IsOLEContainerMode

도킹 관리자가 OLE 컨테이너 모드에 있는지 여부를 지정 합니다.

```
BOOL IsOLEContainerMode() const;
```

### <a name="return-value"></a>반환 값

도킹 관리자가 OLE 컨테이너 모드에 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

OLE 컨테이너 모드에서는 모든 도킹 창과 응용 프로그램 도구 모음이 숨겨집니다. [CDockingManager:: m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode) 을 TRUE로 설정한 경우에도이 모드에서 창이 숨겨집니다.

## <a name="cdockingmanagerispointneardocksite"></a><a name="ispointneardocksite"></a> CDockingManager::IsPointNearDockSite

지정 된 지점이 dock 사이트 근처에 있는지 여부를 확인 합니다.

```
BOOL IsPointNearDockSite(
    CPoint point,
    DWORD& dwBarAlignment,
    BOOL& bOuterEdge) const;
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
진행 지정 된 지점입니다.

*Dw바 맞춤*<br/>
제한이 점이 근처에 있는 가장자리를 지정 합니다. 가능한 값은 CBRS_ALIGN_LEFT, CBRS_ALIGN_RIGHT, CBRS_ALIGN_TOP 및 CBRS_ALIGN_BOTTOM입니다.

*bOuterEdge*<br/>
제한이 지점이 dock 사이트의 외부 테두리 근처에 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

지점이 dock 사이트 근처에 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanagerisprintpreviewvalid"></a><a name="isprintpreviewvalid"></a> CDockingManager::IsPrintPreviewValid

인쇄 미리 보기 모드가 설정 되어 있는지 여부를 확인 합니다.

```
BOOL IsPrintPreviewValid() const;
```

### <a name="return-value"></a>반환 값

인쇄 미리 보기 모드가 설정 되어 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanagerloadstate"></a><a name="loadstate"></a> CDockingManager:: LoadState

레지스트리에서 도킹 관리자의 상태를 로드 합니다.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 프로필 이름입니다.

*uiID*<br/>
진행 도킹 관리자의 id입니다.

### <a name="return-value"></a>반환 값

도킹 관리자 상태가 성공적으로 로드 되었으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanagerlockupdate"></a><a name="lockupdate"></a> CDockingManager:: LockUpdate

지정 된 창을 잠급니다.

```cpp
void LockUpdate(BOOL bLock);
```

### <a name="parameters"></a>매개 변수

*거부*<br/>
진행 창이 잠겨 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

잠긴 창은 이동할 수 없으며 다시 그릴 수 없습니다.

## <a name="cdockingmanagerm_bhidedockingbarsincontainermode"></a><a name="m_bhidedockingbarsincontainermode"></a> CDockingManager:: m_bHideDockingBarsInContainerMode

도킹 관리자가 OLE 컨테이너 모드에서 창을 숨길지 여부를 지정 합니다.

```
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;
```

### <a name="remarks"></a>설명

응용 프로그램이 OLE 컨테이너 모드일 때 주 프레임에 도킹 된 모든 창을 계속 표시 하려면이 값을 FALSE로 설정 합니다. 기본적으로이 값은 TRUE입니다.

## <a name="cdockingmanagerm_dockmodeglobal"></a><a name="m_dockmodeglobal"></a> CDockingManager:: m_dockModeGlobal

전역 도킹 모드를 지정 합니다.

```
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;
```

### <a name="remarks"></a>설명

기본적으로 각 도킹 창에서는이 도킹 모드를 사용 합니다. 이 필드를로 설정할 수 있는 값에 대 한 자세한 내용은 [Cbasepane:: GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode)를 참조 하세요.

## <a name="cdockingmanagerm_ndocksensitivity"></a><a name="m_ndocksensitivity"></a> CDockingManager:: m_nDockSensitivity

도킹 민감도를 지정 합니다.

```
AFX_IMPORT_DATA static int m_nDockSensitivity;
```

### <a name="remarks"></a>설명

도킹 민감도는 프레임 워크가 상태를 도킹 된 상태로 변경 하기 전에 부동 창이 도킹 창, 도킹 사이트 또는 다른 창에 접근 하는 방법을 정의 합니다.

## <a name="cdockingmanagerm_ntimeoutbeforedockingbardock"></a><a name="m_ntimeoutbeforedockingbardock"></a> CDockingManager:: m_nTimeOutBeforeDockingBarDock

도킹 창이 즉시 도킹 모드로 도킹 되기 전의 시간 (밀리초)을 지정 합니다.

```
static UINT m_nTimeOutBeforeDockingBarDock;
```

### <a name="remarks"></a>설명

창이 도킹 되기 전에 프레임 워크는 지정 된 시간 동안 대기 합니다. 이렇게 하면 사용자가 창을 끌어 놓는 동안 창이 실수로 위치에 도킹 되지 않습니다.

## <a name="cdockingmanagerm_ntimeoutbeforetoolbardock"></a><a name="m_ntimeoutbeforetoolbardock"></a> CDockingManager:: m_nTimeOutBeforeToolBarDock

주 프레임 창에 도구 모음이 도킹 되기 전의 시간 (밀리초)을 지정 합니다.

```
static UINT m_nTimeOutBeforeToolBarDock;
```

### <a name="remarks"></a>설명

도구 모음이 도킹 되기 전에 프레임 워크는 지정 된 시간 동안 대기 합니다. 이렇게 하면 사용자가 계속 끌고 있는 동안 도구 모음이 실수로 위치에 도킹 되지 않습니다.

## <a name="cdockingmanageronactivateframe"></a><a name="onactivateframe"></a> CDockingManager:: OnActivateFrame

프레임 창이 활성화 되거나 비활성화 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnActivateFrame(BOOL bActivate);
```

### <a name="parameters"></a>매개 변수

*bActivate*<br/>
진행 TRUE 이면 프레임 창이 활성 상태가 됩니다. FALSE 이면 프레임 창이 비활성화 됩니다.

## <a name="cdockingmanageronclosepopupmenu"></a><a name="onclosepopupmenu"></a> CDockingManager::OnClosePopupMenu

활성 팝업 메뉴에서 WM_DESTROY 메시지를 처리할 때 프레임워크에서 호출됩니다.

```cpp
void OnClosePopupMenu();
```

### <a name="remarks"></a>설명

프레임 워크는 현재 주 창을 닫으려고 할 때 WM_DESTROY 메시지를 보냅니다. `CMFCPopupMenu`개체가 WM_DESTROY 메시지를 처리할 때 프레임 창에 속하는 개체의 알림을 처리 하려면이 메서드를 재정의 `CMFCPopupMenu` 합니다.

## <a name="cdockingmanageronmoveminiframe"></a><a name="onmoveminiframe"></a> CDockingManager::OnMoveMiniFrame

미니 프레임 창을 이동 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```

### <a name="parameters"></a>매개 변수

*pFrame*<br/>
진행 미니 프레임 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanageronpanecontextmenu"></a><a name="onpanecontextmenu"></a> CDockingManager::OnPaneContextMenu

창 목록을 포함 하는 메뉴를 빌드할 때 프레임 워크에서 호출 됩니다.

```cpp
void OnPaneContextMenu(CPoint point);
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
진행 메뉴의 위치를 지정 합니다.

## <a name="cdockingmanagerpanefrompoint"></a><a name="panefrompoint"></a> CDockingManager::P aneFromPoint

지정 된 지점을 포함 하는 창을 반환 합니다.

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    bool bExactBar = false,
    CRuntimeClass* pRTCBarType = NULL,
    BOOL bCheckVisibility = FALSE,
    const CBasePane* pBarToIgnore = NULL) const;

virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    DWORD& dwAlignment,
    CRuntimeClass* pRTCBarType = NULL,
    const CBasePane* pBarToIgnore = NULL) const;
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
진행 확인할 지점을 화면 좌표로 지정 합니다.

*nSensitivity*<br/>
진행 선택한 각 창의 창 사각형을 확장할 값입니다. 지정 된 지점이이 팽창 영역에 있는 경우 창은 검색 조건을 충족 합니다.

*bExactBar*<br/>
진행 *Nsensitivity* 매개 변수를 무시 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

*Prtc바 형식*<br/>
진행 NULL이 아닌 경우 메서드는 지정 된 형식의 요소만 검색 합니다.

*bCheckVisibility*<br/>
진행 표시 되는 창만 확인 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

*dwAlignment*<br/>
제한이 지정 된 지점에 창이 있으면이 매개 변수에는 지정 된 지점에 가장 가까운 창의 측면이 포함 됩니다. 자세한 내용은 설명 섹션을 참조하세요.

*pBarToIgnore*<br/>
진행 NULL이 아닌 경우이 메서드는이 매개 변수로 지정 된 창을 무시 합니다.

### <a name="return-value"></a>반환 값

지정 된 지점을 포함 하는 [Cbasepane](../../mfc/reference/cbasepane-class.md)파생 개체 이거나, 창이 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

함수에서를 반환 하 고 창을 찾았으면 *Dwalignment* 에 지정 된 점의 맞춤을 포함 합니다. 예를 들어 점이 창의 맨 위에 가장 가까이 있는 경우 *Dwalignment* 는 CBRS_ALIGN_TOP로 설정 됩니다.

## <a name="cdockingmanagerprocesspanecontextmenucommand"></a><a name="processpanecontextmenucommand"></a> CDockingManager::P rocessPaneContextMenuCommand

지정 된 명령에 대 한 확인란을 선택 하거나 선택을 취소 하 고 표시 된 창의 레이아웃을 다시 계산 하기 위해 프레임 워크에서 호출 됩니다.

```
BOOL ProcessPaneContextMenuCommand(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
진행 메뉴에 있는 컨트롤 막대의 id입니다.

*nCode*<br/>
진행 명령 알림 코드입니다.

*pExtra*<br/>
진행 `CCmdUI` *Ncode* 가 CN_UPDATE_COMMAND_UI 경우에 대 한 포인터로 캐스팅 된 void에 대 한 포인터입니다.

*pHandlerInfo*<br/>
진행 정보 구조체에 대 한 포인터입니다. 이 매개 변수는 사용되지 않습니다.

### <a name="return-value"></a>반환 값

*Pextra* 가 NULL이 아니고 *ncode* 가 CN_UPDATE_COMMAND_UI와 일치 하는 경우 TRUE이 고, 지정 된 *nID* 가 있는 컨트롤 모음이 있으면 TRUE입니다.

## <a name="cdockingmanagerrecalclayout"></a><a name="recalclayout"></a> CDockingManager:: RecalcLayout

컨트롤 목록에 있는 컨트롤의 내부 레이아웃을 다시 계산 합니다.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>매개 변수

*bNotify*<br/>
진행 이 매개 변수는 사용 되지 않습니다.

## <a name="cdockingmanagerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a> CDockingManager::ReleaseEmptyPaneContainers

빈 창 컨테이너를 해제 합니다.

```cpp
void ReleaseEmptyPaneContainers();
```

## <a name="cdockingmanagerremovehiddenmditabbedbar"></a><a name="removehiddenmditabbedbar"></a> CDockingManager::RemoveHiddenMDITabbedBar

지정 된 숨겨진 막대 창을 제거 합니다.

```cpp
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
진행 제거할 막대 창에 대 한 포인터입니다.

## <a name="cdockingmanagerremoveminiframe"></a><a name="removeminiframe"></a> CDockingManager::RemoveMiniFrame

미니 프레임 목록에서 지정 된 프레임을 제거 합니다.

```
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 제거할 프레임에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

지정 된 프레임이 제거 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanagerremovepanefromdockmanager"></a><a name="removepanefromdockmanager"></a> CDockingManager::RemovePaneFromDockManager

창의 등록을 취소 하 고 도킹 관리자의 목록에서 제거 합니다.

```cpp
void RemovePaneFromDockManager(
    CBasePane* pWnd,
    BOOL bDestroy,
    BOOL bAdjustLayout,
    BOOL bAutoHide = FALSE,
    CBasePane* pBarReplacement = NULL);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
진행 제거할 창에 대 한 포인터입니다.

*bDestroy*<br/>
진행 TRUE 이면 제거 된 창이 제거 됩니다.

*bAdjustLayout*<br/>
진행 TRUE 이면 도킹 레이아웃을 즉시 조정 합니다.

*bAutoHide 숨기기*<br/>
진행 TRUE 이면 자동 숨기기 막대 목록에서 창이 제거 됩니다. FALSE 이면 창이 일반 창 목록에서 제거 됩니다.

*P바 대체*<br/>
진행 제거 된 창을 대체 하는 창에 대 한 포인터입니다.

## <a name="cdockingmanagerreplacepane"></a><a name="replacepane"></a> CDockingManager::ReplacePane

한 창을 다른 창으로 대체합니다.

```
BOOL ReplacePane(
    CDockablePane* pOriginalBar,
    CDockablePane* pNewBar);
```

### <a name="parameters"></a>매개 변수

*폰 바*<br/>
진행 원래 창에 대 한 포인터입니다.

*pNewBar*<br/>
진행 원본 창을 대체 하는 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

창이 성공적으로 교체 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cdockingmanagerresortminiframesforzorder"></a><a name="resortminiframesforzorder"></a> CDockingManager::ResortMiniFramesForZOrder

미니 프레임 목록에서 프레임을 리조트 합니다.

```cpp
void ResortMiniFramesForZOrder();
```

## <a name="cdockingmanagersavestate"></a><a name="savestate"></a> CDockingManager:: SaveState

도킹 관리자의 상태를 레지스트리에 저장 합니다.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>매개 변수

*lpszProfileName*<br/>
진행 레지스트리 키에 대 한 경로입니다.

*uiID*<br/>
진행 도킹 관리자 ID입니다.

### <a name="return-value"></a>반환 값

상태가 성공적으로 저장 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

도킹 관리자의 상태를 레지스트리에 저장 하려면 컨트롤 막대의 상태, 자동 숨기기 막대의 상태, 도킹 관리자에 있는 미니 프레임의 상태를 저장 해야 합니다.

## <a name="cdockingmanagersendmessagetominiframes"></a><a name="sendmessagetominiframes"></a> CDockingManager::SendMessageToMiniFrames

지정 된 메시지를 모든 미니 프레임으로 보냅니다.

```
BOOL SendMessageToMiniFrames(
    UINT uMessage,
    WPARAM wParam = 0,
    LPARAM lParam = 0);
```

### <a name="parameters"></a>매개 변수

*uMessage*<br/>
진행 보낼 메시지입니다.

*wParam*<br/>
진행 추가 메시지 종속 정보입니다.

*lParam*<br/>
진행 추가 메시지 종속 정보입니다.

### <a name="return-value"></a>반환 값

항상 TRUE입니다.

## <a name="cdockingmanagerserialize"></a><a name="serialize"></a> CDockingManager:: Serialize

도킹 관리자를 보관 파일에 씁니다.

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>매개 변수

*ar*<br/>
진행 보관 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

도킹 관리자를 보관에 쓰려면 도킹 컨트롤 막대와 슬라이더의 수를 결정 하 고 컨트롤 막대, 미니 프레임, 자동 숨기기 막대 및 MDI 탭 막대를 보관에 써야 합니다.

## <a name="cdockingmanagersetautohidezorder"></a><a name="setautohidezorder"></a> CDockingManager::SetAutohideZOrder

컨트롤 막대와 지정 된 창의 크기, 너비 및 높이를 설정 합니다.

```cpp
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```

### <a name="parameters"></a>매개 변수

*pAHDockingBar*<br/>
진행 도킹 가능한 창에 대 한 포인터입니다.

## <a name="cdockingmanagersetdockingmode"></a><a name="setdockingmode"></a> CDockingManager::SetDockingMode

도킹 모드를 설정 합니다.

```
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```

### <a name="parameters"></a>매개 변수

*dockMode*<br/>
새 도킹 모드를 지정 합니다. 자세한 내용은 설명 섹션을 참조하세요.

*테마나*<br/>
스마트 도킹 표식에 사용할 테마를 지정 합니다. AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008 열거 된 값 중 하나일 수 있습니다.

### <a name="remarks"></a>설명

도킹 모드를 설정 하려면이 정적 메서드를 호출 합니다.

*dockMode* 은 다음 값 중 하나일 수 있습니다.

- DT_STANDARD-Visual Studio .NET 2003에서 구현 된 표준 도킹 모드입니다. 끌기 컨텍스트 없이 창을 끕니다.

- Microsoft Visio에서 구현 된 DT_IMMEDIATE 즉시 도킹 모드입니다. 끌기 컨텍스트를 사용 하 여 창을 끌고 있지만 표식이 표시 되지 않습니다.

- DT_SMART-Visual Studio 2005에서 구현 된 스마트 도킹 모드입니다. 창이 도킹 될 수 있는 위치를 보여 주는 끌기 컨텍스트 및 스마트 마커가 표시 됩니다.

## <a name="cdockingmanagersetdockstate"></a><a name="setdockstate"></a> CDockingManager::SetDockState

컨트롤 막대, 미니 프레임 및 자동 숨기기 막대의 도킹 상태를 설정 합니다.

```
virtual void SetDockState();
```

## <a name="cdockingmanagersetprintpreviewmode"></a><a name="setprintpreviewmode"></a> CDockingManager:: SetPrintPreviewMode

인쇄 미리 보기에 표시 되는 막대의 인쇄 미리 보기 모드를 설정 합니다.

```cpp
void SetPrintPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>매개 변수

*bPreview*<br/>
진행 인쇄 미리 보기 모드가 설정 되어 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

*pState*<br/>
진행 미리 보기 상태에 대 한 포인터입니다. 이 매개 변수는 사용되지 않습니다.

## <a name="cdockingmanagersetsmartdockingparams"></a><a name="setsmartdockingparams"></a> CDockingManager::SetSmartDockingParams

스마트 도킹의 동작을 정의 하는 매개 변수를 설정 합니다.

```
static void SetSmartDockingParams(CSmartDockingInfo& params);
```

### <a name="parameters"></a>매개 변수

*params*<br/>
[in, out] 스마트 도킹에 대 한 매개 변수를 정의 합니다.

### <a name="remarks"></a>설명

스마트 도킹 표식의 모양, 색 또는 모양을 사용자 지정 하려면이 메서드를 호출 합니다.

기본 모양에 대 한 기본 고정 표식을 사용 하려면 [CSmartDockingInfo 클래스](../../mfc/reference/csmartdockinginfo-class.md) 의 초기화 되지 않은 인스턴스를 *params* 에 전달 합니다.

## <a name="cdockingmanagershowdelayshowminiframes"></a><a name="showdelayshowminiframes"></a> CDockingManager:: Showdelayshow미니 프레임

미니 프레임의 창을 표시 하거나 숨깁니다.

```cpp
void ShowDelayShowMiniFrames(BOOL bshow);
```

### <a name="parameters"></a>매개 변수

*bShow*<br/>
진행 표시 된 프레임의 창을 활성화 하려면 TRUE로 설정 합니다. FALSE 이면 프레임의 창을 숨깁니다.

## <a name="cdockingmanagershowpanes"></a><a name="showpanes"></a> CDockingManager:: ShowPanes

컨트롤의 창과 자동 숨기기 막대를 표시 하거나 숨깁니다.

```
virtual BOOL ShowPanes(BOOL bShow);
```

### <a name="parameters"></a>매개 변수

*bShow*<br/>
진행 창을 표시 하려면 TRUE로 설정 합니다. 창을 숨기려면 FALSE입니다.

### <a name="return-value"></a>반환 값

항상 FALSE입니다.

## <a name="cdockingmanagerstartsdocking"></a><a name="startsdocking"></a> CDockingManager:: StartSDocking

스마트 도킹 관리자의 맞춤에 따라 지정 된 창의 스마트 도킹을 시작 합니다.

```cpp
void StartSDocking(CWnd* pDockingWnd);
```

### <a name="parameters"></a>매개 변수

*pDockingWnd*<br/>
진행 도킹할 창에 대 한 포인터입니다.

## <a name="cdockingmanagerstopsdocking"></a><a name="stopsdocking"></a> CDockingManager:: StopSDocking

스마트 도킹을 중지 합니다.

```cpp
void StopSDocking();
```

## <a name="cdockingmanagergetsmartdockingtheme"></a><a name="getsmartdockingtheme"></a> CDockingManager::GetSmartDockingTheme

스마트 도킹 표식을 표시 하는 데 사용 되는 테마를 반환 하는 정적 메서드입니다.

```
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```

### <a name="return-value"></a>반환 값

AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008 열거 된 값 중 하나를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[CFrameWndEx 클래스](../../mfc/reference/cframewndex-class.md)<br/>
[CDockablePane 클래스](../../mfc/reference/cdockablepane-class.md)<br/>
[CPaneFrameWnd 클래스](../../mfc/reference/cpaneframewnd-class.md)
