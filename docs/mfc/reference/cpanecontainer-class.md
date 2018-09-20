---
title: CPaneContainer 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPaneContainer
- AFXPANECONTAINER/CPaneContainer
- AFXPANECONTAINER/CPaneContainer::CPaneContainer
- AFXPANECONTAINER/CPaneContainer::AddPane
- AFXPANECONTAINER/CPaneContainer::AddRef
- AFXPANECONTAINER/CPaneContainer::AddSubPaneContainer
- AFXPANECONTAINER/CPaneContainer::CalcAvailablePaneSpace
- AFXPANECONTAINER/CPaneContainer::CalcAvailableSpace
- AFXPANECONTAINER/CPaneContainer::CalculateRecentSize
- AFXPANECONTAINER/CPaneContainer::CheckPaneDividerVisibility
- AFXPANECONTAINER/CPaneContainer::Copy
- AFXPANECONTAINER/CPaneContainer::DeletePane
- AFXPANECONTAINER/CPaneContainer::FindSubPaneContainer
- AFXPANECONTAINER/CPaneContainer::FindTabbedPane
- AFXPANECONTAINER/CPaneContainer::GetAssociatedSiblingPaneIDs
- AFXPANECONTAINER/CPaneContainer::GetLeftPane
- AFXPANECONTAINER/CPaneContainer::GetLeftPaneContainer
- AFXPANECONTAINER/CPaneContainer::GetMinSize
- AFXPANECONTAINER/CPaneContainer::GetMinSizeLeft
- AFXPANECONTAINER/CPaneContainer::GetMinSizeRight
- AFXPANECONTAINER/CPaneContainer::GetNodeCount
- AFXPANECONTAINER/CPaneContainer::GetPaneDivider
- AFXPANECONTAINER/CPaneContainer::GetParentPaneContainer
- AFXPANECONTAINER/CPaneContainer::GetRecentPaneDividerRect
- AFXPANECONTAINER/CPaneContainer::GetRecentPaneDividerStyle
- AFXPANECONTAINER/CPaneContainer::GetRecentPercent
- AFXPANECONTAINER/CPaneContainer::GetRefCount
- AFXPANECONTAINER/CPaneContainer::GetResizeStep
- AFXPANECONTAINER/CPaneContainer::GetRightPane
- AFXPANECONTAINER/CPaneContainer::GetRightPaneContainer
- AFXPANECONTAINER/CPaneContainer::GetTotalReferenceCount
- AFXPANECONTAINER/CPaneContainer::GetWindowRect
- AFXPANECONTAINER/CPaneContainer::IsDisposed
- AFXPANECONTAINER/CPaneContainer::IsEmpty
- AFXPANECONTAINER/CPaneContainer::IsLeftPane
- AFXPANECONTAINER/CPaneContainer::IsLeftPaneContainer
- AFXPANECONTAINER/CPaneContainer::IsLeftPartEmpty
- AFXPANECONTAINER/CPaneContainer::IsRightPartEmpty
- AFXPANECONTAINER/CPaneContainer::IsVisible
- AFXPANECONTAINER/CPaneContainer::Move
- AFXPANECONTAINER/CPaneContainer::OnDeleteHidePane
- AFXPANECONTAINER/CPaneContainer::OnMoveInternalPaneDivider
- AFXPANECONTAINER/CPaneContainer::OnShowPane
- AFXPANECONTAINER/CPaneContainer::Release
- AFXPANECONTAINER/CPaneContainer::ReleaseEmptyPaneContainer
- AFXPANECONTAINER/CPaneContainer::RemoveNonValidPanes
- AFXPANECONTAINER/CPaneContainer::RemovePane
- AFXPANECONTAINER/CPaneContainer::Resize
- AFXPANECONTAINER/CPaneContainer::ResizePane
- AFXPANECONTAINER/CPaneContainer::ResizePartOfPaneContainer
- AFXPANECONTAINER/CPaneContainer::Serialize
- AFXPANECONTAINER/CPaneContainer::SetPane
- AFXPANECONTAINER/CPaneContainer::SetPaneContainer
- AFXPANECONTAINER/CPaneContainer::SetPaneDivider
- AFXPANECONTAINER/CPaneContainer::SetParentPaneContainer
- AFXPANECONTAINER/CPaneContainer::SetRecentPercent
- AFXPANECONTAINER/CPaneContainer::SetUpByID
- AFXPANECONTAINER/CPaneContainer::StoreRecentDockSiteInfo
- AFXPANECONTAINER/CPaneContainer::StretchPaneContainer
dev_langs:
- C++
helpviewer_keywords:
- CPaneContainer [MFC], CPaneContainer
- CPaneContainer [MFC], AddPane
- CPaneContainer [MFC], AddRef
- CPaneContainer [MFC], AddSubPaneContainer
- CPaneContainer [MFC], CalcAvailablePaneSpace
- CPaneContainer [MFC], CalcAvailableSpace
- CPaneContainer [MFC], CalculateRecentSize
- CPaneContainer [MFC], CheckPaneDividerVisibility
- CPaneContainer [MFC], Copy
- CPaneContainer [MFC], DeletePane
- CPaneContainer [MFC], FindSubPaneContainer
- CPaneContainer [MFC], FindTabbedPane
- CPaneContainer [MFC], GetAssociatedSiblingPaneIDs
- CPaneContainer [MFC], GetLeftPane
- CPaneContainer [MFC], GetLeftPaneContainer
- CPaneContainer [MFC], GetMinSize
- CPaneContainer [MFC], GetMinSizeLeft
- CPaneContainer [MFC], GetMinSizeRight
- CPaneContainer [MFC], GetNodeCount
- CPaneContainer [MFC], GetPaneDivider
- CPaneContainer [MFC], GetParentPaneContainer
- CPaneContainer [MFC], GetRecentPaneDividerRect
- CPaneContainer [MFC], GetRecentPaneDividerStyle
- CPaneContainer [MFC], GetRecentPercent
- CPaneContainer [MFC], GetRefCount
- CPaneContainer [MFC], GetResizeStep
- CPaneContainer [MFC], GetRightPane
- CPaneContainer [MFC], GetRightPaneContainer
- CPaneContainer [MFC], GetTotalReferenceCount
- CPaneContainer [MFC], GetWindowRect
- CPaneContainer [MFC], IsDisposed
- CPaneContainer [MFC], IsEmpty
- CPaneContainer [MFC], IsLeftPane
- CPaneContainer [MFC], IsLeftPaneContainer
- CPaneContainer [MFC], IsLeftPartEmpty
- CPaneContainer [MFC], IsRightPartEmpty
- CPaneContainer [MFC], IsVisible
- CPaneContainer [MFC], Move
- CPaneContainer [MFC], OnDeleteHidePane
- CPaneContainer [MFC], OnMoveInternalPaneDivider
- CPaneContainer [MFC], OnShowPane
- CPaneContainer [MFC], Release
- CPaneContainer [MFC], ReleaseEmptyPaneContainer
- CPaneContainer [MFC], RemoveNonValidPanes
- CPaneContainer [MFC], RemovePane
- CPaneContainer [MFC], Resize
- CPaneContainer [MFC], ResizePane
- CPaneContainer [MFC], ResizePartOfPaneContainer
- CPaneContainer [MFC], Serialize
- CPaneContainer [MFC], SetPane
- CPaneContainer [MFC], SetPaneContainer
- CPaneContainer [MFC], SetPaneDivider
- CPaneContainer [MFC], SetParentPaneContainer
- CPaneContainer [MFC], SetRecentPercent
- CPaneContainer [MFC], SetUpByID
- CPaneContainer [MFC], StoreRecentDockSiteInfo
- CPaneContainer [MFC], StretchPaneContainer
ms.assetid: beb79e08-f611-4d66-ba04-053baa79bf86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba6c46871a74a1c90de94621a81e46d320388221
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388111"
---
# <a name="cpanecontainer-class"></a>CPaneContainer 클래스

`CPaneContainer` 클래스는 MFC에서 구현한 도킹 모델의 기본 구성 요소입니다. 이 클래스의 개체는 도킹 창 두 개 또는 `CPaneContainer.` 인스턴스 두 개를 가리키며 창이나 컨테이너를 나누는 구분선의 포인터를 저장합니다. 컨테이너 안에 컨테이너를 중첩하면 프레임워크에서 복잡한 도킹 레이아웃을 나타내는 이진 트리를 빌드할 수 있습니다. 이진 트리의 루트에 저장 되는 [CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md) 개체입니다.

자세한 세부 정보에 대 한 참조에 있는 소스 코드를 **VC\\atlmfc\\src\\mfc** Visual Studio 설치의 폴더입니다.

## <a name="syntax"></a>구문

```
class CPaneContainer : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CPaneContainer::CPaneContainer](#cpanecontainer)|기본 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPaneContainer::AddPane](#addpane)||
|[CPaneContainer::AddRef](#addref)||
|[CPaneContainer::AddSubPaneContainer](#addsubpanecontainer)||
|[CPaneContainer::CalcAvailablePaneSpace](#calcavailablepanespace)||
|[CPaneContainer::CalcAvailableSpace](#calcavailablespace)||
|[CPaneContainer::CalculateRecentSize](#calculaterecentsize)||
|[CPaneContainer::CheckPaneDividerVisibility](#checkpanedividervisibility)||
|[CPaneContainer::Copy](#copy)||
|[CPaneContainer::DeletePane](#deletepane)||
|[CPaneContainer::FindSubPaneContainer](#findsubpanecontainer)||
|[CPaneContainer::FindTabbedPane](#findtabbedpane)||
|[CPaneContainer::GetAssociatedSiblingPaneIDs](#getassociatedsiblingpaneids)||
|[CPaneContainer::GetLeftPane](#getleftpane)||
|[CPaneContainer::GetLeftPaneContainer](#getleftpanecontainer)||
|[CPaneContainer::GetMinSize](#getminsize)||
|[CPaneContainer::GetMinSizeLeft](#getminsizeleft)||
|[CPaneContainer::GetMinSizeRight](#getminsizeright)||
|[CPaneContainer::GetNodeCount](#getnodecount)||
|[CPaneContainer::GetPaneDivider](#getpanedivider)||
|[CPaneContainer::GetParentPaneContainer](#getparentpanecontainer)||
|[CPaneContainer::GetRecentPaneDividerRect](#getrecentpanedividerrect)||
|[CPaneContainer::GetRecentPaneDividerStyle](#getrecentpanedividerstyle)||
|[CPaneContainer::GetRecentPercent](#getrecentpercent)||
|[CPaneContainer::GetRefCount](#getrefcount)||
|[CPaneContainer::GetResizeStep](#getresizestep)||
|[CPaneContainer::GetRightPane](#getrightpane)||
|[CPaneContainer::GetRightPaneContainer](#getrightpanecontainer)||
|[CPaneContainer::GetTotalReferenceCount](#gettotalreferencecount)||
|[CPaneContainer::GetWindowRect](#getwindowrect)||
|[CPaneContainer::IsDisposed](#isdisposed)||
|[CPaneContainer::IsEmpty](#isempty)||
|[CPaneContainer::IsLeftPane](#isleftpane)||
|[CPaneContainer::IsLeftPaneContainer](#isleftpanecontainer)||
|[CPaneContainer::IsLeftPartEmpty](#isleftpartempty)||
|[CPaneContainer::IsRightPartEmpty](#isrightpartempty)||
|[CPaneContainer::IsVisible](#isvisible)||
|[CPaneContainer::Move](#move)||
|[CPaneContainer::OnDeleteHidePane](#ondeletehidepane)||
|[CPaneContainer::OnMoveInternalPaneDivider](#onmoveinternalpanedivider)||
|[CPaneContainer::OnShowPane](#onshowpane)||
|[CPaneContainer::Release](#release)||
|[CPaneContainer::ReleaseEmptyPaneContainer](#releaseemptypanecontainer)||
|[CPaneContainer::RemoveNonValidPanes](#removenonvalidpanes)||
|[CPaneContainer::RemovePane](#removepane)||
|[CPaneContainer::Resize](#resize)||
|[CPaneContainer::ResizePane](#resizepane)||
|[CPaneContainer::ResizePartOfPaneContainer](#resizepartofpanecontainer)||
|[CPaneContainer::Serialize](#serialize)|이 개체를 보관 저장소에서 읽어오거나 보관 저장소에 씁니다. ( [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)를 재정의합니다.)|
|[CPaneContainer::SetPane](#setpane)||
|[CPaneContainer::SetPaneContainer](#setpanecontainer)||
|[CPaneContainer::SetPaneDivider](#setpanedivider)||
|[CPaneContainer::SetParentPaneContainer](#setparentpanecontainer)||
|[CPaneContainer::SetRecentPercent](#setrecentpercent)||
|[CPaneContainer::SetUpByID](#setupbyid)||
|[CPaneContainer::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneContainer::StretchPaneContainer](#stretchpanecontainer)||

### <a name="remarks"></a>설명

`CPaneContainer` 개체는 프레임 워크에서 자동으로 생성 됩니다.

## <a name="example"></a>예제

다음 예제에서는의 인스턴스를 생성 하는 방법에 설명 합니다 `CPaneContainer` 클래스입니다. 이 코드 조각은의 일부인 합니다 [창 크기 설정 샘플](../../visual-cpp-samples.md)합니다.

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanecontainer-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#1](../../mfc/reference/codesnippet/cpp/cpanecontainer-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층

[CObject](../../mfc/reference/cobject-class.md)

[CPaneContainer](../../mfc/reference/cpanecontainer-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxpanecontainer.h

##  <a name="addpane"></a>  CPaneContainer::AddPane


```
CDockablePane* AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>매개 변수

[in] *pBar*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="addref"></a>  CPaneContainer::AddRef


```
void AddRef();
```

### <a name="remarks"></a>설명

##  <a name="addsubpanecontainer"></a>  CPaneContainer::AddSubPaneContainer


```
BOOL AddSubPaneContainer(
    CPaneContainer* pContainer,
    BOOL bRightNodeNew);
```

### <a name="parameters"></a>매개 변수

*pContainer*<br/>
[in] [in] *bRightNodeNew*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="calcavailablepanespace"></a>  CPaneContainer::CalcAvailablePaneSpace


```
virtual int CalcAvailablePaneSpace(
    int nRequiredOffset,
    CPane* pBar,
    CPaneContainer* pContainer,
    BOOL bLeftBar);
```

### <a name="parameters"></a>매개 변수

*nRequiredOffset*<br/>
[in] [in] *pBar*
*pContainer*<br/>
[in] [in] *bLeftBar*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="calcavailablespace"></a>  CPaneContainer::CalcAvailableSpace


```
virtual CSize CalcAvailableSpace(
    CSize sizeStretch,
    BOOL bLeftBar);
```

### <a name="parameters"></a>매개 변수

*sizeStretch*<br/>
[in] [in] *bLeftBar*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="calculaterecentsize"></a>  CPaneContainer::CalculateRecentSize


```
void CalculateRecentSize();
```

### <a name="remarks"></a>설명

##  <a name="checkpanedividervisibility"></a>  CPaneContainer::CheckPaneDividerVisibility


```
void CheckPaneDividerVisibility();
```

### <a name="remarks"></a>설명

##  <a name="copy"></a>  CPaneContainer::Copy


```
virtual CPaneContainer* Copy(CPaneContainer* pParentContainer);
```

### <a name="parameters"></a>매개 변수

[in] *pParentContainer*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="cpanecontainer"></a>  CPaneContainer::CPaneContainer


```
CPaneContainer(
    CPaneContainerManager* pManager = NULL,
    CDockablePane* pLeftBar = NULL,
    CDockablePane* pRightBar = NULL,
    CPaneDivider* pSlider = NULL);
```

### <a name="parameters"></a>매개 변수

*pManager*<br/>
[in] [in] *pLeftBar*
*pRightBar*<br/>
[in] [in] *pSlider*

### <a name="remarks"></a>설명

##  <a name="deletepane"></a>  CPaneContainer::DeletePane


```
virtual void DeletePane(
    CDockablePane* pBar,
    BC_FIND_CRITERIA barType);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
[in] [in] *barType*

### <a name="remarks"></a>설명

##  <a name="findsubpanecontainer"></a>  CPaneContainer::FindSubPaneContainer


```
CPaneContainer* FindSubPaneContainer(
    const CObject* pObject,
    BC_FIND_CRITERIA findCriteria);
```

### <a name="parameters"></a>매개 변수

*pObject*<br/>
[in] [in] *findCriteria*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="findtabbedpane"></a>  CPaneContainer::FindTabbedPane


```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>매개 변수

[in] *nID*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getassociatedsiblingpaneids"></a>  CPaneContainer::GetAssociatedSiblingPaneIDs


```
CList<UINT, UINT>* GetAssociatedSiblingPaneIDs(CDockablePane* pBar);
```

### <a name="parameters"></a>매개 변수

[in] *pBar*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getleftpane"></a>  CPaneContainer::GetLeftPane


```
const CDockablePane* GetLeftPane() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getleftpanecontainer"></a>  CPaneContainer::GetLeftPaneContainer


```
const CPaneContainer* GetLeftPaneContainer() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getminsize"></a>  CPaneContainer::GetMinSize


```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>매개 변수

[in] *크기*

### <a name="remarks"></a>설명

##  <a name="getminsizeleft"></a>  CPaneContainer::GetMinSizeLeft


```
virtual void GetMinSizeLeft(CSize& size) const;
```

### <a name="parameters"></a>매개 변수

[in] *크기*

### <a name="remarks"></a>설명

##  <a name="getminsizeright"></a>  CPaneContainer::GetMinSizeRight


```
virtual void GetMinSizeRight(CSize& size) const;
```

### <a name="parameters"></a>매개 변수

[in] *크기*

### <a name="remarks"></a>설명

##  <a name="getnodecount"></a>  CPaneContainer::GetNodeCount


```
int GetNodeCount() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getpanedivider"></a>  CPaneContainer::GetPaneDivider


```
const CPaneDivider* GetPaneDivider() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getparentpanecontainer"></a>  CPaneContainer::GetParentPaneContainer


```
CPaneContainer* GetParentPaneContainer() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getrecentpanedividerrect"></a>  CPaneContainer::GetRecentPaneDividerRect


```
CRect GetRecentPaneDividerRect() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getrecentpanedividerstyle"></a>  CPaneContainer::GetRecentPaneDividerStyle


```
DWORD GetRecentPaneDividerStyle() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getrecentpercent"></a>  CPaneContainer::GetRecentPercent


```
int GetRecentPercent();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getrefcount"></a>  CPaneContainer::GetRefCount


```
LONG GetRefCount();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getresizestep"></a>  CPaneContainer::GetResizeStep


```
virtual int GetResizeStep() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getrightpane"></a>  CPaneContainer::GetRightPane


```
const CDockablePane* GetRightPane() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getrightpanecontainer"></a>  CPaneContainer::GetRightPaneContainer


```
const CPaneContainer* GetRightPaneContainer() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="gettotalreferencecount"></a>  CPaneContainer::GetTotalReferenceCount


```
int GetTotalReferenceCount() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="getwindowrect"></a>  CPaneContainer::GetWindowRect


```
virtual void GetWindowRect(
    CRect& rect,
    BOOL bIgnoreVisibility = FALSE) const;
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
[in] [in] *bIgnoreVisibility*

### <a name="remarks"></a>설명

##  <a name="isdisposed"></a>  CPaneContainer::IsDisposed


```
BOOL IsDisposed() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="isempty"></a>  CPaneContainer::IsEmpty


```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="isleftpane"></a>  CPaneContainer::IsLeftPane


```
BOOL IsLeftPane(CDockablePane* pBar) const;
```

### <a name="parameters"></a>매개 변수

[in] *pBar*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="isleftpanecontainer"></a>  CPaneContainer::IsLeftPaneContainer


```
BOOL IsLeftPaneContainer() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="isleftpartempty"></a>  CPaneContainer::IsLeftPartEmpty


```
BOOL IsLeftPartEmpty(BOOL bCheckVisibility = FALSE) const;
```

### <a name="parameters"></a>매개 변수

[in] *bCheckVisibility*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="isrightpartempty"></a>  CPaneContainer::IsRightPartEmpty


```
BOOL IsRightPartEmpty(BOOL bCheckVisibility = FALSE) const;
```

### <a name="parameters"></a>매개 변수

[in] *bCheckVisibility*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="isvisible"></a>  CPaneContainer::IsVisible


```
BOOL IsVisible() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="move"></a>  CPaneContainer::Move


```
virtual void Move(CPoint ptNewLeftTop);
```

### <a name="parameters"></a>매개 변수

[in] *ptNewLeftTop*

### <a name="remarks"></a>설명

##  <a name="ondeletehidepane"></a>  CPaneContainer::OnDeleteHidePane


```
void OnDeleteHidePane(
    CDockablePane* pBar,
    BOOL bHide);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
[in] [in] *bHide*

### <a name="remarks"></a>설명

##  <a name="onmoveinternalpanedivider"></a>  CPaneContainer::OnMoveInternalPaneDivider


```
virtual int OnMoveInternalPaneDivider(
    int nOffset,
    HDWP& hdwp);
```

### <a name="parameters"></a>매개 변수

*nOffset*<br/>
[in] [in] *hdwp*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="onshowpane"></a>  CPaneContainer::OnShowPane


```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
[in] [in] *bShow*

### <a name="remarks"></a>설명

##  <a name="release"></a>  CPaneContainer::Release


```
DWORD Release();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="releaseemptypanecontainer"></a>  CPaneContainer::ReleaseEmptyPaneContainer


```
void ReleaseEmptyPaneContainer();
```

### <a name="remarks"></a>설명

##  <a name="removenonvalidpanes"></a>  CPaneContainer::RemoveNonValidPanes


```
void RemoveNonValidPanes();
```

### <a name="remarks"></a>설명

##  <a name="removepane"></a>  CPaneContainer::RemovePane


```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>매개 변수

[in] *pBar*

### <a name="remarks"></a>설명

##  <a name="resize"></a>  CPaneContainer::Resize


```
virtual void Resize(
    CRect rect,
    HDWP& hdwp,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
[in] [in] *hdwp* [in] *bRedraw*

### <a name="remarks"></a>설명

##  <a name="resizepane"></a>  CPaneContainer::ResizePane


```
virtual void ResizePane(
    int nOffset,
    CPane* pBar,
    CPaneContainer* pContainer,
    BOOL bHorz,
    BOOL bLeftBar,
    HDWP& hdwp);
```

### <a name="parameters"></a>매개 변수

*nOffset*<br/>
[in] [in] *pBar*
*pContainer*<br/>
[in] [in] *bHorz*
*bLeftBar*<br/>
[in] [in] *hdwp*

### <a name="remarks"></a>설명

##  <a name="resizepartofpanecontainer"></a>  CPaneContainer::ResizePartOfPaneContainer


```
virtual void ResizePartOfPaneContainer(
    int nOffset,
    BOOL bLeftPart,
    HDWP& hdwp);
```

### <a name="parameters"></a>매개 변수

*nOffset*<br/>
[in] [in] *bLeftPart* [in] *hdwp*

### <a name="remarks"></a>설명

##  <a name="serialize"></a>  CPaneContainer::Serialize


```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>매개 변수

[in] *ar*

### <a name="remarks"></a>설명

##  <a name="setpane"></a>  CPaneContainer::SetPane


```
void SetPane(
    CDockablePane* pBar,
    BOOL bLeft);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
[in] [in] *bLeft*

### <a name="remarks"></a>설명

##  <a name="setpanecontainer"></a>  CPaneContainer::SetPaneContainer


```
void SetPaneContainer(
    CPaneContainer* pContainer,
    BOOL bLeft);
```

### <a name="parameters"></a>매개 변수

*pContainer*<br/>
[in] [in] *bLeft*

### <a name="remarks"></a>설명

##  <a name="setpanedivider"></a>  CPaneContainer::SetPaneDivider


```
void SetPaneDivider(CPaneDivider* pSlider);
```

### <a name="parameters"></a>매개 변수

[in] *pSlider*

### <a name="remarks"></a>설명

##  <a name="setparentpanecontainer"></a>  CPaneContainer::SetParentPaneContainer


```
void SetParentPaneContainer(CPaneContainer* p);
```

### <a name="parameters"></a>매개 변수

[in] *p*

### <a name="remarks"></a>설명

##  <a name="setrecentpercent"></a>  CPaneContainer::SetRecentPercent


```
void SetRecentPercent(int nRecentPercent);
```

### <a name="parameters"></a>매개 변수

[in] *nRecentPercent*

### <a name="remarks"></a>설명

##  <a name="setupbyid"></a>  CPaneContainer::SetUpByID


```
BOOL SetUpByID(
    UINT nID,
    CDockablePane* pBar);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
[in] [in] *pBar*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

##  <a name="storerecentdocksiteinfo"></a>  CPaneContainer::StoreRecentDockSiteInfo


```
virtual void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>매개 변수

[in] *pBar*

### <a name="remarks"></a>설명

##  <a name="stretchpanecontainer"></a>  CPaneContainer::StretchPaneContainer


```
virtual int StretchPaneContainer(
    int nOffset,
    BOOL bStretchHorz,
    BOOL bLeftBar,
    BOOL bMoveSlider,
    HDWP& hdwp);
```

### <a name="parameters"></a>매개 변수

*nOffset*<br/>
[in] [in] *bStretchHorz*
*bLeftBar*<br/>
[in] [in] *bMoveSlider* [in] *hdwp*

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[CPaneContainerManager 클래스](../../mfc/reference/cpanecontainermanager-class.md)
