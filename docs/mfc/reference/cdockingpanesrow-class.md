---
description: '자세히 알아보기: CDockingPanesRow 클래스'
title: CDockingPanesRow 클래스
ms.date: 10/18/2018
f1_keywords:
- CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPane
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPaneFromRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ArrangePanes
- AFXDOCKINGPANESROW/CDockingPanesRow::CalcFixedLayout
- AFXDOCKINGPANESROW/CDockingPanesRow::Create
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanesRect
- AFXDOCKINGPANESROW/CDockingPanesRow::FixupVirtualRects
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableLength
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetClientRect
- AFXDOCKINGPANESROW/CDockingPanesRow::GetDockSite
- AFXDOCKINGPANESROW/CDockingPanesRow::GetExtraSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetGroupFromPane
- AFXDOCKINGPANESROW/CDockingPanesRow::GetID
- AFXDOCKINGPANESROW/CDockingPanesRow::GetMaxPaneSize
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneList
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowAlignment
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowHeight
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowOffset
- AFXDOCKINGPANESROW/CDockingPanesRow::GetVisibleCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetWindowRect
- AFXDOCKINGPANESROW/CDockingPanesRow::HasPane
- AFXDOCKINGPANESROW/CDockingPanesRow::IsEmpty
- AFXDOCKINGPANESROW/CDockingPanesRow::IsExclusiveRow
- AFXDOCKINGPANESROW/CDockingPanesRow::IsHorizontal
- AFXDOCKINGPANESROW/CDockingPanesRow::IsVisible
- AFXDOCKINGPANESROW/CDockingPanesRow::Move
- AFXDOCKINGPANESROW/CDockingPanesRow::MovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::OnResizePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RedrawAll
- AFXDOCKINGPANESROW/CDockingPanesRow::RemovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::ReplacePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RepositionPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::Resize
- AFXDOCKINGPANESROW/CDockingPanesRow::ResizeByPaneDivider
- AFXDOCKINGPANESROW/CDockingPanesRow::ScreenToClient
- AFXDOCKINGPANESROW/CDockingPanesRow::SetExtra
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowDockSiteRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowPane
- AFXDOCKINGPANESROW/CDockingPanesRow::UpdateVisibleState
helpviewer_keywords:
- CDockingPanesRow [MFC], AddPane
- CDockingPanesRow [MFC], AddPaneFromRow
- CDockingPanesRow [MFC], ArrangePanes
- CDockingPanesRow [MFC], CalcFixedLayout
- CDockingPanesRow [MFC], Create
- CDockingPanesRow [MFC], ExpandStretchedPanes
- CDockingPanesRow [MFC], ExpandStretchedPanesRect
- CDockingPanesRow [MFC], FixupVirtualRects
- CDockingPanesRow [MFC], GetAvailableLength
- CDockingPanesRow [MFC], GetAvailableSpace
- CDockingPanesRow [MFC], GetClientRect
- CDockingPanesRow [MFC], GetDockSite
- CDockingPanesRow [MFC], GetExtraSpace
- CDockingPanesRow [MFC], GetGroupFromPane
- CDockingPanesRow [MFC], GetID
- CDockingPanesRow [MFC], GetMaxPaneSize
- CDockingPanesRow [MFC], GetPaneCount
- CDockingPanesRow [MFC], GetPaneList
- CDockingPanesRow [MFC], GetRowAlignment
- CDockingPanesRow [MFC], GetRowHeight
- CDockingPanesRow [MFC], GetRowOffset
- CDockingPanesRow [MFC], GetVisibleCount
- CDockingPanesRow [MFC], GetWindowRect
- CDockingPanesRow [MFC], HasPane
- CDockingPanesRow [MFC], IsEmpty
- CDockingPanesRow [MFC], IsExclusiveRow
- CDockingPanesRow [MFC], IsHorizontal
- CDockingPanesRow [MFC], IsVisible
- CDockingPanesRow [MFC], Move
- CDockingPanesRow [MFC], MovePane
- CDockingPanesRow [MFC], OnResizePane
- CDockingPanesRow [MFC], RedrawAll
- CDockingPanesRow [MFC], RemovePane
- CDockingPanesRow [MFC], ReplacePane
- CDockingPanesRow [MFC], RepositionPanes
- CDockingPanesRow [MFC], Resize
- CDockingPanesRow [MFC], ResizeByPaneDivider
- CDockingPanesRow [MFC], ScreenToClient
- CDockingPanesRow [MFC], SetExtra
- CDockingPanesRow [MFC], ShowDockSiteRow
- CDockingPanesRow [MFC], ShowPane
- CDockingPanesRow [MFC], UpdateVisibleState
ms.assetid: e7a17832-0ebb-4bce-b799-cec9b60f76fe
ms.openlocfilehash: bf031b19c25cde36705333feb3baa3af9e1932ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185013"
---
# <a name="cdockingpanesrow-class"></a>CDockingPanesRow 클래스

도크 사이트의 동일한 수평 또는 수직 행(열)에 위치한 창 목록을 관리합니다.

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CDockingPanesRow : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CDockingPanesRow::CDockingPanesRow`|기본 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDockingPanesRow::AddPane](#addpane)||
|[CDockingPanesRow::AddPaneFromRow](#addpanefromrow)||
|[CDockingPanesRow:: ArrangePanes](#arrangepanes)|지정된 여백 및 간격 매개 변수에 따라 창을 일렬로 정렬합니다.|
|[CDockingPanesRow::CalcFixedLayout](#calcfixedlayout)||
|[CDockingPanesRow::Create](#create)||
|[CDockingPanesRow::ExpandStretchedPanes](#expandstretchedpanes)||
|[CDockingPanesRow::ExpandStretchedPanesRect](#expandstretchedpanesrect)||
|[CDockingPanesRow::FixupVirtualRects](#fixupvirtualrects)||
|[CDockingPanesRow::GetAvailableLength](#getavailablelength)||
|[CDockingPanesRow::GetAvailableSpace](#getavailablespace)||
|[CDockingPanesRow::GetClientRect](#getclientrect)||
|[CDockingPanesRow::GetDockSite](#getdocksite)||
|[CDockingPanesRow::GetExtraSpace](#getextraspace)||
|[CDockingPanesRow::GetGroupFromPane](#getgroupfrompane)||
|[CDockingPanesRow::GetID](#getid)||
|[CDockingPanesRow::GetMaxPaneSize](#getmaxpanesize)||
|[CDockingPanesRow::GetPaneCount](#getpanecount)||
|[CDockingPanesRow::GetPaneList](#getpanelist)||
|[CDockingPanesRow::GetRowAlignment](#getrowalignment)||
|[CDockingPanesRow::GetRowHeight](#getrowheight)||
|[CDockingPanesRow::GetRowOffset](#getrowoffset)||
|[CDockingPanesRow::GetVisibleCount](#getvisiblecount)||
|[CDockingPanesRow::GetWindowRect](#getwindowrect)||
|[CDockingPanesRow::HasPane](#haspane)||
|[CDockingPanesRow::IsEmpty](#isempty)||
|[CDockingPanesRow::IsExclusiveRow](#isexclusiverow)||
|[CDockingPanesRow::IsHorizontal](#ishorizontal)||
|[CDockingPanesRow::IsVisible](#isvisible)||
|[CDockingPanesRow::Move](#move)||
|[CDockingPanesRow::MovePane](#movepane)||
|[CDockingPanesRow::OnResizePane](#onresizepane)||
|[CDockingPanesRow::RedrawAll](#redrawall)||
|[CDockingPanesRow::RemovePane](#removepane)||
|[CDockingPanesRow::ReplacePane](#replacepane)||
|[CDockingPanesRow::RepositionPanes](#repositionpanes)||
|[CDockingPanesRow::Resize](#resize)||
|[CDockingPanesRow::ResizeByPaneDivider](#resizebypanedivider)||
|[CDockingPanesRow::ScreenToClient](#screentoclient)||
|[CDockingPanesRow::SetExtra](#setextra)||
|[CDockingPanesRow::ShowDockSiteRow](#showdocksiterow)||
|[CDockingPanesRow::ShowPane](#showpane)||
|[CDockingPanesRow::UpdateVisibleState](#updatevisiblestate)||

## <a name="remarks"></a>설명

`CDockingPanesRow` 개체는 도킹 사이트 개체에 의해 내부적으로 만들어집니다.

## <a name="example"></a>예제

다음 예제에서는 `CMFCAutoHideBar` 개체에서 `CDockingPanesRow` 개체를 가져오는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cdockingpanesrow-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxDockingPanesRow

## <a name="cdockingpanesrowaddpane"></a><a name="addpane"></a> CDockingPanesRow:: AddPane

```
virtual void AddPane(
    CPane* pControlBar,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL,
    BOOL bAddLast = FALSE);
```

### <a name="parameters"></a>매개 변수

진행 *Pcontrolbar*<br/>

진행 *dockMethod*<br/>

진행 *lpRect*<br/>

진행 *Baddlast*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowaddpanefromrow"></a><a name="addpanefromrow"></a> CDockingPanesRow:: AddPaneFromRow

```
virtual void AddPaneFromRow(
    CPane* pControlBar,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>매개 변수

진행 *Pcontrolbar*<br/>

진행 *dockMethod*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowarrangepanes"></a><a name="arrangepanes"></a> CDockingPanesRow:: ArrangePanes

지정 된 여백 및 간격 매개 변수에 따라 행의 도킹 창을 정렬 합니다.

```
virtual void ArrangePanes(
    int nMargin,
    int nSpacing);
```

### <a name="parameters"></a>매개 변수

*nMargin*<br/>
진행 행의 왼쪽 위 모퉁이에서 첫 번째 창의 오프셋 (픽셀)을 지정 합니다.

*n 간격*<br/>
진행 창 사이의 간격 (픽셀)을 지정 합니다.

### <a name="remarks"></a>설명

도킹 되는 행의 창을 정렬 하려면이 메서드를 호출 합니다. 이 메서드를 호출한 후에는를 호출 해야 `CDockingPanesRow::FixupVirtualRects(FALSE, NULL)` 합니다.

## <a name="cdockingpanesrowcalcfixedlayout"></a><a name="calcfixedlayout"></a> CDockingPanesRow:: CalcFixedLayout

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

## <a name="cdockingpanesrowcdockingpanesrow"></a><a name="cdockingpanesrow"></a> CDockingPanesRow:: CDockingPanesRow

```
CDockingPanesRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nHeight);
```

### <a name="parameters"></a>매개 변수

진행 *pParentDockBar*<br/>

진행 *Noffset*<br/>

진행 *Nheight*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowcreate"></a><a name="create"></a> CDockingPanesRow:: Create

```
virtual BOOL Create();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowexpandstretchedpanes"></a><a name="expandstretchedpanes"></a> CDockingPanesRow:: ExpandStretchedPanes

```cpp
void ExpandStretchedPanes();
```

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowexpandstretchedpanesrect"></a><a name="expandstretchedpanesrect"></a> CDockingPanesRow:: ExpandStretchedPanesRect

```cpp
void ExpandStretchedPanesRect();
```

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowfixupvirtualrects"></a><a name="fixupvirtualrects"></a> CDockingPanesRow:: FixupVirtualRects

```cpp
void FixupVirtualRects(
    bool bMoveBackToVirtualRect,
    CPane* pBarToExclude = NULL);
```

### <a name="parameters"></a>매개 변수

진행 *Bmovebacktovirtualrect*<br/>

진행 *P바 Toexclude*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetavailablelength"></a><a name="getavailablelength"></a> CDockingPanesRow:: GetAvailableLength

```
virtual int GetAvailableLength(BOOL bUseVirtualRect = FALSE) const;
```

### <a name="parameters"></a>매개 변수

진행 *Busevirtualrect*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetavailablespace"></a><a name="getavailablespace"></a> CDockingPanesRow:: GetAvailableSpace

```
virtual void GetAvailableSpace(CRect& rect);
```

### <a name="parameters"></a>매개 변수

[in] *rect*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetclientrect"></a><a name="getclientrect"></a> CDockingPanesRow:: GetClientRect

```cpp
void GetClientRect(CRect& rect) const;
```

### <a name="parameters"></a>매개 변수

[in] *rect*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetdocksite"></a><a name="getdocksite"></a> CDockingPanesRow:: GetDockSite

```
CDockSite* GetDockSite() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetextraspace"></a><a name="getextraspace"></a> CDockingPanesRow:: GetExtraSpace

```
int GetExtraSpace() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetgroupfrompane"></a><a name="getgroupfrompane"></a> CDockingPanesRow:: GetGroupFromPane

```cpp
void GetGroupFromPane(
    CPane* pBar,
    CObList& lst);
```

### <a name="parameters"></a>매개 변수

진행 *Pbar*<br/>

진행 *.lst*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetid"></a><a name="getid"></a> CDockingPanesRow:: GetID

```
int GetID() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetmaxpanesize"></a><a name="getmaxpanesize"></a> CDockingPanesRow:: Getmaxesize Esize

```
int GetMaxPaneSize(BOOL bSkipHiddenBars = TRUE) const;
```

### <a name="parameters"></a>매개 변수

진행 *bSkipHiddenBars*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetpanecount"></a><a name="getpanecount"></a> CDockingPanesRow:: Get팬 Ecount

```
int GetPaneCount() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetpanelist"></a><a name="getpanelist"></a> CDockingPanesRow:: GetPaneList

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetrowalignment"></a><a name="getrowalignment"></a> CDockingPanesRow:: GetRowAlignment

```
DWORD GetRowAlignment() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetrowheight"></a><a name="getrowheight"></a> CDockingPanesRow:: GetRowHeight

```
int GetRowHeight() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetrowoffset"></a><a name="getrowoffset"></a> CDockingPanesRow:: GetRowOffset

```
int GetRowOffset() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetvisiblecount"></a><a name="getvisiblecount"></a> CDockingPanesRow:: GetVisibleCount

```
virtual int GetVisibleCount();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowgetwindowrect"></a><a name="getwindowrect"></a> CDockingPanesRow:: GetWindowRect

```cpp
void GetWindowRect(CRect& rect) const;
```

### <a name="parameters"></a>매개 변수

[in] *rect*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowhaspane"></a><a name="haspane"></a> CDockingPanesRow:: HasPane

```
BOOL HasPane(CBasePane* pControlBar);
```

### <a name="parameters"></a>매개 변수

진행 *Pcontrolbar*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowisempty"></a><a name="isempty"></a> CDockingPanesRow:: IsEmpty

```
virtual BOOL IsEmpty() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowisexclusiverow"></a><a name="isexclusiverow"></a> CDockingPanesRow:: IsExclusiveRow

```
virtual BOOL IsExclusiveRow() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowishorizontal"></a><a name="ishorizontal"></a> CDockingPanesRow:: IsHorizontal

```
bool IsHorizontal() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowisvisible"></a><a name="isvisible"></a> CDockingPanesRow:: IsVisible

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowmove"></a><a name="move"></a> CDockingPanesRow:: Move

```
virtual void Move(int nOffset);
```

### <a name="parameters"></a>매개 변수

진행 *Noffset*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowmovepane"></a><a name="movepane"></a> CDockingPanesRow:: movepmov

```cpp
void MovePane(
    CPane* pControlBar,
    CPoint ptOffset,
    BOOL bSwapControlBars,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    CRect rectTarget,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    int nOffset,
    bool bForward,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    int nAbsolutOffset,
    HDWP& hdwp);
```

### <a name="parameters"></a>매개 변수

진행 *Pcontrolbar*<br/>

진행 *Ptoffset*<br/>

진행 *Bswapcontrolbars*<br/>

진행 *hdwp*<br/>

진행 *rectTarget*<br/>

진행 *Noffset*<br/>

진행 *Bforward*<br/>

진행 *nAbsolutOffset*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowonresizepane"></a><a name="onresizepane"></a> CDockingPanesRow:: OnResizePane

```
virtual void OnResizePane(CBasePane* pControlBar);
```

### <a name="parameters"></a>매개 변수

진행 *Pcontrolbar*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowredrawall"></a><a name="redrawall"></a> CDockingPanesRow:: RedrawAll

```cpp
void RedrawAll();
```

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowremovepane"></a><a name="removepane"></a> CDockingPanesRow:: RemovePane

```
virtual void RemovePane(CPane* pControlBar);
```

### <a name="parameters"></a>매개 변수

진행 *Pcontrolbar*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowreplacepane"></a><a name="replacepane"></a> CDockingPanesRow:: ReplacePane

```
virtual BOOL ReplacePane(
    CPane* pBarOld,
    CPane* pBarNew);
```

### <a name="parameters"></a>매개 변수

진행 *P바 오래*<br/>

진행 *P바 새로운*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowrepositionpanes"></a><a name="repositionpanes"></a> CDockingPanesRow:: RepositionPanes

```
virtual void RepositionPanes(
    CRect& rectNewParentBarArea,
    UINT nSide = (UINT)-1,
    BOOL bExpand = FALSE,
    int nOffset = 0);
```

### <a name="parameters"></a>매개 변수

진행 *rectNewParentBarArea*<br/>

진행 *Nside*<br/>

진행 *Bexpand*<br/>

진행 *Noffset*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowresize"></a><a name="resize"></a> CDockingPanesRow:: Resize

```
virtual int Resize(int nOffset);
```

### <a name="parameters"></a>매개 변수

진행 *Noffset*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowresizebypanedivider"></a><a name="resizebypanedivider"></a> CDockingPanesRow:: ResizeByPaneDivider

```
virtual int ResizeByPaneDivider(int /*ignored*/);
```

### <a name="parameters"></a>매개 변수

진행 *무시* 됨<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowscreentoclient"></a><a name="screentoclient"></a> CDockingPanesRow:: ScreenToClient

```cpp
void ScreenToClient(CRect& rect) const;
```

### <a name="parameters"></a>매개 변수

[in] *rect*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowsetextra"></a><a name="setextra"></a> CDockingPanesRow:: SetExtra

```cpp
void SetExtra(
    int nExtraSpace,
    AFX_ROW_ALIGNMENT rowExtraAlign);
```

### <a name="parameters"></a>매개 변수

진행 *nExtraSpace*<br/>

진행 *rowExtraAlign*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowshowdocksiterow"></a><a name="showdocksiterow"></a> CDockingPanesRow:: ShowDockSiteRow

```
virtual void ShowDockSiteRow(
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>매개 변수

진행 *Bshow*<br/>

진행 *Bdelay*<br/>

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowshowpane"></a><a name="showpane"></a> CDockingPanesRow:: ShowPane

```
virtual BOOL ShowPane(
    CPane* pControlBar,
    BOOL bShow,
    BOOL bDelay = FALSE);
```

### <a name="parameters"></a>매개 변수

진행 *Pcontrolbar*<br/>

진행 *Bshow*<br/>

진행 *Bdelay*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cdockingpanesrowupdatevisiblestate"></a><a name="updatevisiblestate"></a> CDockingPanesRow:: UpdateVisibleState

```
virtual void UpdateVisibleState(BOOL bDelay);
```

### <a name="parameters"></a>매개 변수

진행 *Bdelay*<br/>

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[CDockSite 클래스](../../mfc/reference/cdocksite-class.md)<br/>
[CPane 클래스](../../mfc/reference/cpane-class.md)
