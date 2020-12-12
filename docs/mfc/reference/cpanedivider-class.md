---
description: '자세히 알아보기: CPaneDivider 클래스'
title: CPaneDivider 클래스
ms.date: 11/04/2016
f1_keywords:
- CPaneDivider
- AFXPANEDIVIDER/CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::AddPaneContainer
- AFXPANEDIVIDER/CPaneDivider::AddPane
- AFXPANEDIVIDER/CPaneDivider::AddRecentPane
- AFXPANEDIVIDER/CPaneDivider::CalcExpectedDockedRect
- AFXPANEDIVIDER/CPaneDivider::CalcFixedLayout
- AFXPANEDIVIDER/CPaneDivider::CheckVisibility
- AFXPANEDIVIDER/CPaneDivider::CreateEx
- AFXPANEDIVIDER/CPaneDivider::DoesAllowDynInsertBefore
- AFXPANEDIVIDER/CPaneDivider::DoesContainFloatingPane
- AFXPANEDIVIDER/CPaneDivider::FindPaneContainer
- AFXPANEDIVIDER/CPaneDivider::FindTabbedPane
- AFXPANEDIVIDER/CPaneDivider::GetDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::GetFirstPane
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividerStyle
- AFXPANEDIVIDER/CPaneDivider::GetRootContainerRect
- AFXPANEDIVIDER/CPaneDivider::GetWidth
- AFXPANEDIVIDER/CPaneDivider::Init
- AFXPANEDIVIDER/CPaneDivider::InsertPane
- AFXPANEDIVIDER/CPaneDivider::IsAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::IsDefault
- AFXPANEDIVIDER/CPaneDivider::IsHorizontal
- AFXPANEDIVIDER/CPaneDivider::Move
- AFXPANEDIVIDER/CPaneDivider::NotifyAboutRelease
- AFXPANEDIVIDER/CPaneDivider::OnShowPane
- AFXPANEDIVIDER/CPaneDivider::ReleaseEmptyPaneContainers
- AFXPANEDIVIDER/CPaneDivider::RemovePane
- AFXPANEDIVIDER/CPaneDivider::ReplacePane
- AFXPANEDIVIDER/CPaneDivider::RepositionPanes
- AFXPANEDIVIDER/CPaneDivider::Serialize
- AFXPANEDIVIDER/CPaneDivider::SetAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::SetPaneContainerManager
- AFXPANEDIVIDER/CPaneDivider::ShowWindow
- AFXPANEDIVIDER/CPaneDivider::StoreRecentDockSiteInfo
- AFXPANEDIVIDER/CPaneDivider::StoreRecentTabRelatedInfo
- AFXPANEDIVIDER/CPaneDivider::GetPanes
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividers
- AFXPANEDIVIDER/CPaneDivider::m_nDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::m_pSliderRTC
helpviewer_keywords:
- CPaneDivider [MFC], CPaneDivider
- CPaneDivider [MFC], AddPaneContainer
- CPaneDivider [MFC], AddPane
- CPaneDivider [MFC], AddRecentPane
- CPaneDivider [MFC], CalcExpectedDockedRect
- CPaneDivider [MFC], CalcFixedLayout
- CPaneDivider [MFC], CheckVisibility
- CPaneDivider [MFC], CreateEx
- CPaneDivider [MFC], DoesAllowDynInsertBefore
- CPaneDivider [MFC], DoesContainFloatingPane
- CPaneDivider [MFC], FindPaneContainer
- CPaneDivider [MFC], FindTabbedPane
- CPaneDivider [MFC], GetDefaultWidth
- CPaneDivider [MFC], GetFirstPane
- CPaneDivider [MFC], GetPaneDividerStyle
- CPaneDivider [MFC], GetRootContainerRect
- CPaneDivider [MFC], GetWidth
- CPaneDivider [MFC], Init
- CPaneDivider [MFC], InsertPane
- CPaneDivider [MFC], IsAutoHideMode
- CPaneDivider [MFC], IsDefault
- CPaneDivider [MFC], IsHorizontal
- CPaneDivider [MFC], Move
- CPaneDivider [MFC], NotifyAboutRelease
- CPaneDivider [MFC], OnShowPane
- CPaneDivider [MFC], ReleaseEmptyPaneContainers
- CPaneDivider [MFC], RemovePane
- CPaneDivider [MFC], ReplacePane
- CPaneDivider [MFC], RepositionPanes
- CPaneDivider [MFC], Serialize
- CPaneDivider [MFC], SetAutoHideMode
- CPaneDivider [MFC], SetPaneContainerManager
- CPaneDivider [MFC], ShowWindow
- CPaneDivider [MFC], StoreRecentDockSiteInfo
- CPaneDivider [MFC], StoreRecentTabRelatedInfo
- CPaneDivider [MFC], GetPanes
- CPaneDivider [MFC], GetPaneDividers
- CPaneDivider [MFC], m_nDefaultWidth
- CPaneDivider [MFC], m_pSliderRTC
ms.assetid: 8e828a5d-232f-4127-b8e3-7fa45a7a476e
ms.openlocfilehash: f2541483f7881ab0b303750e69af776c2c3bc7a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301518"
---
# <a name="cpanedivider-class"></a>CPaneDivider 클래스

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

클래스는 두 개의 창을 `CPaneDivider` 나누고 창의 두 그룹을 분할 하거나 주 프레임 창의 클라이언트 영역에서 창 그룹을 분리 합니다.

## <a name="syntax"></a>구문

```
class CPaneDivider : public CBasePane
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CPaneDivider::CPaneDivider](#cpanedivider)||

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPaneDivider::AddPaneContainer](#addpanecontainer)||
|[CPaneDivider:: AddPane](#addpane)||
|[CPaneDivider::AddRecentPane](#addrecentpane)||
|[CPaneDivider::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CPaneDivider::CalcFixedLayout](#calcfixedlayout)|( [Cbasepane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)를 재정의 합니다.)|
|[CPaneDivider:: CheckVisibility](#checkvisibility)||
|[CPaneDivider:: CreateEx](#createex)|( [Cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)를 재정의 합니다.)|
|[CPaneDivider::D oesAllowDynInsertBefore](#doesallowdyninsertbefore)|[Cbasepane::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)를 재정의 합니다.|
|[CPaneDivider::D oesContainFloatingPane](#doescontainfloatingpane)||
|[CPaneDivider::FindPaneContainer](#findpanecontainer)||
|[CPaneDivider::FindTabbedPane](#findtabbedpane)||
|[CPaneDivider::GetDefaultWidth](#getdefaultwidth)||
|[CPaneDivider:: GetFirstPane](#getfirstpane)||
|[CPaneDivider::GetPaneDividerStyle](#getpanedividerstyle)||
|[CPaneDivider::GetRootContainerRect](#getrootcontainerrect)||
|[CPaneDivider::GetWidth](#getwidth)||
|[CPaneDivider:: Init](#init)||
|[CPaneDivider:: InsertPane](#insertpane)||
|[CPaneDivider::IsAutoHideMode](#isautohidemode)|( [Cbasepane:: IsAutoHideMode](../../mfc/reference/cbasepane-class.md#isautohidemode)를 재정의 합니다.)|
|[CPaneDivider:: IsDefault](#isdefault)||
|[CPaneDivider::IsHorizontal](#ishorizontal)|( [Cbasepane:: IsHorizontal](../../mfc/reference/cbasepane-class.md#ishorizontal)를 재정의 합니다.)|
|[CPaneDivider:: Move](#move)||
|[CPaneDivider::NotifyAboutRelease](#notifyaboutrelease)||
|[CPaneDivider:: OnShowPane](#onshowpane)||
|[CPaneDivider::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)||
|[CPaneDivider:: RemovePane](#removepane)||
|[CPaneDivider::ReplacePane](#replacepane)||
|[CPaneDivider::RepositionPanes](#repositionpanes)||
|[CPaneDivider:: Serialize](#serialize)|( `CBasePane::Serialize`을 재정의합니다.)|
|[CPaneDivider::SetAutoHideMode](#setautohidemode)||
|[CPaneDivider::SetPaneContainerManager](#setpanecontainermanager)||
|[CPaneDivider:: ShowWindow](#showwindow)||
|[CPaneDivider::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneDivider::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPaneDivider:: GetPanes](#getpanes)|[CPaneContainer 클래스](../../mfc/reference/cpanecontainer-class.md)에 있는 창 목록을 반환 합니다. 이 메서드는 기본 창 구분선에 대해서만 호출 해야 합니다.|
|[CPaneDivider::GetPaneDividers](#getpanedividers)|[CPaneContainer 클래스](../../mfc/reference/cpanecontainer-class.md)에 있는 창 분할자의 목록을 반환 합니다. 이 메서드는 기본 창 구분선에 대해서만 호출 해야 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CPaneDivider:: m_nDefaultWidth](#m_ndefaultwidth)|응용 프로그램에서 모든 창 구분선의 기본 너비 (픽셀)를 지정 합니다.|
|[CPaneDivider:: m_pSliderRTC](#m_psliderrtc)|파생 개체에 대 한 런타임 클래스 정보에 대 한 포인터를 보유 `CPaneDivider` 합니다.|

## <a name="remarks"></a>설명

프레임 워크는 `CPaneDivider` 창이 도킹 될 때 개체를 자동으로 만듭니다.

창 구분선에는 다음 두 가지 유형이 있습니다.

- 기본 창 구분선은 창 그룹이 주 프레임 창의 측면에 도킹 될 때 생성 됩니다. 기본 창 구분선은 [CPaneContainerManager 클래스](../../mfc/reference/cpanecontainermanager-class.md) 에 대 한 포인터를 보유 하 고 창 그룹에서 대부분의 작업 (예: 창 크기 조정 또는 다른 창 또는 컨테이너 도킹)을 컨테이너 관리자에 리디렉션합니다. 각 도킹 창에서는 기본 창 구분선에 대 한 포인터를 유지 합니다.

- 일반 창 구분선은 하나의 컨테이너에 두 개의 창을 나눕니다. 자세한 내용은 [CPaneContainer 클래스](../../mfc/reference/cpanecontainer-class.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 `CWorkspaceBar` 개체에서 `CPaneDivider` 개체를 가져오는 방법을 보여 줍니다. 이 코드 조각은 [MDI 탭 데모 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)\
└ &nbsp; [Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [Cbasepane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CPaneDivider](../../mfc/reference/cpanedivider-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxPaneDivider

## <a name="cpanedividersetautohidemode"></a><a name="setautohidemode"></a> CPaneDivider::SetAutoHideMode

```cpp
void SetAutoHideMode(BOOL bMode);
```

### <a name="parameters"></a>매개 변수

진행 *Bmode*<br/>

### <a name="remarks"></a>설명

## <a name="cpanedividersetpanecontainermanager"></a><a name="setpanecontainermanager"></a> CPaneDivider::SetPaneContainerManager

```cpp
void SetPaneContainerManager(CPaneContainerManager* p);
```

### <a name="parameters"></a>매개 변수

진행 *p*<br/>

### <a name="remarks"></a>설명

## <a name="cpanedivideraddpane"></a><a name="addpane"></a> CPaneDivider:: AddPane

```
virtual void AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>매개 변수

진행 *Pbar*<br/>

### <a name="remarks"></a>설명

## <a name="cpanedivideraddpanecontainer"></a><a name="addpanecontainer"></a> CPaneDivider::AddPaneContainer

```
virtual BOOL AddPaneContainer(
    CPaneContainerManager& barContainerManager,
    BOOL bOuterEdge);

virtual BOOL AddPaneContainer(
    CDockablePane* pTargetBar,
    CPaneContainerManager& barContainerManager,
    DWORD dwAlignment);
```

### <a name="parameters"></a>매개 변수

진행 *barContainerManager*<br/>
진행 *bOuterEdge*<br/>
진행 *Ptargetbar*<br/>
진행 *Dwalignment*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedivideraddrecentpane"></a><a name="addrecentpane"></a> CPaneDivider::AddRecentPane

```
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>매개 변수

진행 *Pbar*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a> CPaneDivider::CalcExpectedDockedRect

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>매개 변수

진행 *pWndToDock*<br/>
진행 *Ptmouse*<br/>
진행 *rectResult*<br/>
진행 *Bdrawtab*<br/>
진행 *Pptargetbar*<br/>

### <a name="remarks"></a>설명

## <a name="cpanedividercalcfixedlayout"></a><a name="calcfixedlayout"></a> CPaneDivider::CalcFixedLayout

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

## <a name="cpanedividercheckvisibility"></a><a name="checkvisibility"></a> CPaneDivider:: CheckVisibility

```
virtual BOOL CheckVisibility();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividercpanedivider"></a><a name="cpanedivider"></a> CPaneDivider::CPaneDivider

```
CPaneDivider();

CPaneDivider(
    BOOL bDefaultSlider,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>매개 변수

진행 *Bdefaultslider*<br/>
진행 *Pparent*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividercreateex"></a><a name="createex"></a> CPaneDivider:: CreateEx

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext);
```

### <a name="parameters"></a>매개 변수

진행 *dwStyleEx*<br/>
진행 *Dwstyle*<br/>
[in] *rect*<br/>
진행 *pParentWnd*<br/>
진행 *nID*<br/>
진행 *pContext*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividerdoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a> CPaneDivider::D oesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividerdoescontainfloatingpane"></a><a name="doescontainfloatingpane"></a> CPaneDivider::D oesContainFloatingPane

```
virtual BOOL DoesContainFloatingPane();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividerfindpanecontainer"></a><a name="findpanecontainer"></a> CPaneDivider::FindPaneContainer

```
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,
    BOOL& bLeftBar);
```

### <a name="parameters"></a>매개 변수

진행 *Pbar*<br/>
진행 *B왼쪽 막대*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividerfindtabbedpane"></a><a name="findtabbedpane"></a> CPaneDivider::FindTabbedPane

```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>매개 변수

진행 *nID*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividergetdefaultwidth"></a><a name="getdefaultwidth"></a> CPaneDivider::GetDefaultWidth

```
static int __stdcall GetDefaultWidth();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividergetfirstpane"></a><a name="getfirstpane"></a> CPaneDivider:: GetFirstPane

```
const CBasePane* GetFirstPane() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividergetpanedividers"></a><a name="getpanedividers"></a> CPaneDivider::GetPaneDividers

[CPaneContainer 클래스](../../mfc/reference/cpanecontainer-class.md)에 있는 창 분할자의 목록을 반환 합니다. 이 메서드는 기본 창 구분선에 대해서만 호출 해야 합니다.

```cpp
void GetPaneDividers(CObList& lstSliders);
```

### <a name="parameters"></a>매개 변수

*lstSliders*<br/>
제한이 창 컨테이너에 있는 창 분할자의 목록을 포함 합니다.

### <a name="remarks"></a>설명

이 메서드는 기본 창 구분선에 대해서만 호출 해야 합니다. 기본 창 구분선은 전체 창 컨테이너의 크기를 조정 하는 구분선입니다.

## <a name="cpanedividergetpanedividerstyle"></a><a name="getpanedividerstyle"></a> CPaneDivider::GetPaneDividerStyle

```
DWORD GetPaneDividerStyle() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividergetpanes"></a><a name="getpanes"></a> CPaneDivider:: GetPanes

[CPaneContainer 클래스](../../mfc/reference/cpanecontainer-class.md)에 있는 창 목록을 반환 합니다. 이 메서드는 기본 창 구분선을 검색 하는 경우에만 호출 해야 합니다.

```cpp
void GetPanes(CObList& lstBars);
```

### <a name="parameters"></a>매개 변수

*lstBars*<br/>
제한이 창 컨테이너에 있는 창 목록을 포함 합니다.

### <a name="remarks"></a>설명

이 메서드는 기본 창 구분선에 대해서만 호출 해야 합니다. 기본 창 구분선은 전체 창 컨테이너의 크기를 조정 하는 구분선입니다.

## <a name="cpanedividergetrootcontainerrect"></a><a name="getrootcontainerrect"></a> CPaneDivider::GetRootContainerRect

```
CRect GetRootContainerRect();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividergetwidth"></a><a name="getwidth"></a> CPaneDivider::GetWidth

```
int GetWidth() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividerinit"></a><a name="init"></a> CPaneDivider:: Init

```cpp
void Init(
    BOOL bDefaultSlider = FALSE,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>매개 변수

진행 *Bdefaultslider*<br/>
진행 *Pparent*<br/>

### <a name="remarks"></a>설명

## <a name="cpanedividerinsertpane"></a><a name="insertpane"></a> CPaneDivider:: InsertPane

```
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,
    CDockablePane* pTargetBar,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>매개 변수

진행 *P바 Toinsert*<br/>
진행 *Ptargetbar*<br/>
진행 *Dwalignment*<br/>
진행 *lpRect*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividerisautohidemode"></a><a name="isautohidemode"></a> CPaneDivider::IsAutoHideMode

```
BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividerisdefault"></a><a name="isdefault"></a> CPaneDivider:: IsDefault

```
BOOL IsDefault() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividerishorizontal"></a><a name="ishorizontal"></a> CPaneDivider::IsHorizontal

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividerm_ndefaultwidth"></a><a name="m_ndefaultwidth"></a> CPaneDivider:: m_nDefaultWidth

응용 프로그램에 있는 모든 창 구분선의 기본 너비 (픽셀 단위)를 지정 합니다.

```
AFX_IMPORT_DATA static int m_nDefaultWidth;
```

## <a name="cpanedividermove"></a><a name="move"></a> CPaneDivider:: Move

```
virtual void Move(
    CPoint& ptOffset,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>매개 변수

진행 *Ptoffset*<br/>
진행 *bAdjustLayout*<br/>

### <a name="remarks"></a>설명

## <a name="cpanedividerm_psliderrtc"></a><a name="m_psliderrtc"></a> CPaneDivider:: m_pSliderRTC

파생 개체에 대 한 런타임 클래스 정보에 대 한 포인터를 보유 `CPaneDivider` 합니다.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;
```

### <a name="remarks"></a>설명

사용자 지정 창 구분선을 만드는 경우이 멤버 변수를 설정 합니다. 이를 통해 프레임 워크는 창을 그릴 때 창 구분선을 만들 수 있습니다.

### <a name="example"></a>예제

다음 예제에서는 멤버 변수를 설정 하는 방법을 보여 줍니다 `m_pSliderRTC` .

```
class CMySplitter : public CPaneDivider
{
...
};

CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```

## <a name="cpanedividernotifyaboutrelease"></a><a name="notifyaboutrelease"></a> CPaneDivider::NotifyAboutRelease

```
virtual void NotifyAboutRelease();
```

### <a name="remarks"></a>설명

## <a name="cpanedivideronshowpane"></a><a name="onshowpane"></a> CPaneDivider:: OnShowPane

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>매개 변수

진행 *Pbar*<br/>
진행 *Bshow*<br/>

### <a name="remarks"></a>설명

## <a name="cpanedividerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a> CPaneDivider::ReleaseEmptyPaneContainers

```cpp
void ReleaseEmptyPaneContainers();
```

### <a name="remarks"></a>설명

## <a name="cpanedividerremovepane"></a><a name="removepane"></a> CPaneDivider:: RemovePane

```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>매개 변수

진행 *Pbar*<br/>

### <a name="remarks"></a>설명

## <a name="cpanedividerreplacepane"></a><a name="replacepane"></a> CPaneDivider::ReplacePane

```
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,
    CDockablePane* pBarToReplaceWith);
```

### <a name="parameters"></a>매개 변수

진행 *pBarToReplace*<br/>
진행 *pBarToReplaceWith*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cpanedividerrepositionpanes"></a><a name="repositionpanes"></a> CPaneDivider::RepositionPanes

```
virtual void RepositionPanes(
    CRect& rectNew,
    HDWP& hdwp);
```

### <a name="parameters"></a>매개 변수

진행 *rectNew*<br/>
진행 *hdwp*<br/>

### <a name="remarks"></a>설명

## <a name="cpanedividerserialize"></a><a name="serialize"></a> CPaneDivider:: Serialize

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>매개 변수

[in] *ar*<br/>

### <a name="remarks"></a>설명

## <a name="cpanedividershowwindow"></a><a name="showwindow"></a> CPaneDivider:: ShowWindow

```cpp
void ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>매개 변수

진행 *Ncmdshow*<br/>

### <a name="remarks"></a>설명

## <a name="cpanedividerstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a> CPaneDivider::StoreRecentDockSiteInfo

```cpp
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>매개 변수

진행 *Pbar*<br/>

### <a name="remarks"></a>설명

## <a name="cpanedividerstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a> CPaneDivider::StoreRecentTabRelatedInfo

```cpp
void StoreRecentTabRelatedInfo(
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
[CPaneContainerManager 클래스](../../mfc/reference/cpanecontainermanager-class.md)<br/>
[CPaneContainer 클래스](../../mfc/reference/cpanecontainer-class.md)<br/>
[CDockingManager 클래스](../../mfc/reference/cdockingmanager-class.md)<br/>
[CBasePane 클래스](../../mfc/reference/cbasepane-class.md)
