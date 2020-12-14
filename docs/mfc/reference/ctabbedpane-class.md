---
description: '자세히 알아보기: CTabbedPane 클래스'
title: CTabbedPane 클래스
ms.date: 11/04/2016
f1_keywords:
- CTabbedPane
- AFXTABBEDPANE/CTabbedPane
- AFXTABBEDPANE/CTabbedPane::DetachPane
- AFXTABBEDPANE/CTabbedPane::EnableTabAutoColor
- AFXTABBEDPANE/CTabbedPane::FloatTab
- AFXTABBEDPANE/CTabbedPane::GetTabArea
- AFXTABBEDPANE/CTabbedPane::GetTabWnd
- AFXTABBEDPANE/CTabbedPane::HasAutoHideMode
- AFXTABBEDPANE/CTabbedPane::IsTabLocationBottom
- AFXTABBEDPANE/CTabbedPane::ResetTabs
- AFXTABBEDPANE/CTabbedPane::SetTabAutoColors
- AFXTABBEDPANE/CTabbedPane::m_bTabsAlwaysTop
- AFXTABBEDPANE/CTabbedPane::m_pTabWndRTC
helpviewer_keywords:
- CTabbedPane [MFC], DetachPane
- CTabbedPane [MFC], EnableTabAutoColor
- CTabbedPane [MFC], FloatTab
- CTabbedPane [MFC], GetTabArea
- CTabbedPane [MFC], GetTabWnd
- CTabbedPane [MFC], HasAutoHideMode
- CTabbedPane [MFC], IsTabLocationBottom
- CTabbedPane [MFC], ResetTabs
- CTabbedPane [MFC], SetTabAutoColors
- CTabbedPane [MFC], m_bTabsAlwaysTop
- CTabbedPane [MFC], m_pTabWndRTC
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
ms.openlocfilehash: a337a68cdeadfec229b24e10a615ba49145ec1ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264481"
---
# <a name="ctabbedpane-class"></a>CTabbedPane 클래스

분리 가능한 탭이 포함된 창의 기능을 구현합니다.

또는 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CTabbedPane : public CBaseTabbedPane
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CTabbedPane::CTabbedPane`|기본 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CTabbedPane::DetachPane](#detachpane)|[:D CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane)를 재정의 합니다.|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|탭의 자동 색 지정을 사용하거나 사용하지 않도록 설정합니다.|
|[CTabbedPane::FloatTab](#floattab)|창이 현재 분리 가능한 탭에 있는 경우에만 창을 부동 합니다. ( [CBaseTabbedPane:: FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)를 재정의 합니다.)|
|[CTabbedPane::GetTabArea](#gettabarea)|탭 창 내 탭 영역의 크기와 위치를 반환합니다.|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|탭 창을 자동 숨기기 모드로 전환할 수 있는지 여부를 결정합니다. [CBaseTabbedPane:: HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode)를 재정의 합니다.|
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|탭이 창의 맨 아래에 있는지 여부를 결정합니다.|
|[CTabbedPane::ResetTabs](#resettabs)|모든 탭 창을 기본 상태로 다시 설정합니다.|
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|자동 색 기능이 사용되는 경우 사용할 수 있는 사용자 지정 색 목록을 설정합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|애플리케이션에서 탭의 기본 위치입니다.|
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|사용자 지정 `CMFCTabCtrl` 파생 개체에 대한 런타임 클래스 정보입니다.|

## <a name="remarks"></a>설명

사용자가 두 번째 창의 캡션을 가리켜서 한 창을 다른 창에 연결하는 경우 프레임워크에서 자동으로 이 클래스의 인스턴스를 만듭니다. 프레임워크에서 만든 모든 탭 창의 ID는 -1입니다.

Outlook 스타일 탭 대신 일반 탭을 지정 하려면 AFX_CBRS_REGULAR_TABS 스타일을 [CDockablePane:: CreateEx](../../mfc/reference/cdockablepane-class.md#createex) 메서드에 전달 합니다.

분리 가능한 탭을 포함하는 탭 창을 만드는 경우 프레임워크에서 자동으로 창을 삭제할 수 있으므로 포인터를 저장하면 안 됩니다. 탭 창에 대한 포인터를 가져오려면 `CBasePane::GetParentTabbedPane` 메서드를 호출합니다.

## <a name="examples"></a>예제

이 예제에서는 `CTabbedPane` 개체를 만듭니다. 다음으로, [CBaseTabbedPane:: AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) 을 사용 하 여 다른 탭을 연결 합니다.

```cpp
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);

if (!pTabbededBar->Create (_T(""),
    this,
    CRect (0,
    0,
    200,
    200),
    TRUE,
    (UINT) -1,
    WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |
    WS_CLIPCHILDREN | CBRS_LEFT |
    CBRS_FLOAT_MULTI))
{
    TRACE0("Failed to create Solution Explorer bar\n");

    return FALSE;      // fail to create
}

pTabbededBar->AddTab (&m_wndClassView);
pTabbededBar->AddTab (&m_wndResourceView);

pTabbededBar->AddTab (&m_wndFileView);
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);

DockPane(pTabbededBar);
```

[CDockablePane:: AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd)를 사용 하 여 탭 컨트롤 막대 개체를 만들 수도 있습니다. `AttachToTabWnd`메서드는 [CDockablePane:: SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc)에 의해 설정 된 런타임 클래스 정보를 사용 하 여 탭 창 개체를 동적으로 만듭니다.

이 예제에서는 탭 창을 동적으로 만들고 두 탭을 연결한 다음 두 번째 탭을 분리 불가능하게 만듭니다.

```cpp
DockPane(&m_wndClassView);

CTabbedPane* pTabbedBar = NULL;
m_wndResourceView.AttachToTabWnd (&m_wndClassView,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

m_wndFileView.AttachToTabWnd (pTabbedBar,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1,
    FALSE);
```

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxTabbedPane

## <a name="ctabbedpanedetachpane"></a><a name="detachpane"></a> CTabbedPane::D etachPane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>매개 변수

진행 *Pbar*<br/>

진행 *Bhide*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="ctabbedpaneenabletabautocolor"></a><a name="enabletabautocolor"></a> CTabbedPane:: EnableTabAutoColor

탭의 자동 색 지정을 사용하거나 사용하지 않도록 설정합니다.

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 탭의 자동 색 지정을 사용 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 정적 메서드를 사용 하 여 응용 프로그램의 모든 탭 창에서 탭의 자동 색 지정을 사용 하거나 사용 하지 않도록 설정할 수 있습니다. 이 기능을 사용 하는 경우 각 탭은 고유한 색으로 채워집니다. [CMFCBaseTabCtrl:: GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) 메서드를 호출 하 여 탭의 색을 표시 하는 데 사용 되는 색 목록을 찾을 수 있습니다.

[CTabbedPane:: SetTabAutoColors](#settabautocolors)를 호출 하 여 탭에 사용 되는 색 목록을 지정할 수 있습니다.

이 옵션은 기본적으로 사용되지 않습니다.

## <a name="ctabbedpanefloattab"></a><a name="floattab"></a> CTabbedPane::FloatTab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>매개 변수

진행 *Pbar*<br/>
진행 *Ntabid*<br/>
진행 *dockMethod*<br/>
진행 *Bhide*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="ctabbedpanegettabarea"></a><a name="gettabarea"></a> CTabbedPane:: GetTabArea

탭 창에 있는 탭 영역의 크기와 위치를 반환 합니다.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>매개 변수

*rectTabAreaTop*<br/>
제한이 위쪽 탭 영역의 크기와 위치 (화면 좌표)를 포함 합니다.

*rectTabAreaBottom*<br/>
제한이 아래쪽 탭 영역의 크기와 위치 (화면 좌표)를 포함 합니다.

### <a name="remarks"></a>설명

프레임 워크는이 메서드를 호출 하 여 사용자가 끌고 있는 창을 도킹 하는 방법을 결정 합니다. 사용자가 대상 창의 탭 영역 위로 창을 끌면 프레임 워크에서 창을 대상 창의 새 탭으로 추가 하려고 합니다. 그렇지 않으면 창을 대상 창의 측면에 도킹 하려고 시도 합니다. 여기에는 두 창을 구분 하는 창 구분선을 사용 하 여 새 창 컨테이너를 만드는 작업이 포함 됩니다.

파생 클래스에서이 메서드 `CTabbedPane` 를 재정의 하 여이 동작을 변경 합니다.

## <a name="ctabbedpanegettabwnd"></a><a name="gettabwnd"></a> CTabbedPane::GetTabWnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="ctabbedpanehasautohidemode"></a><a name="hasautohidemode"></a> CTabbedPane::HasAutoHideMode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="ctabbedpaneistablocationbottom"></a><a name="istablocationbottom"></a> CTabbedPane:: IsTabLocationBottom

탭이 창의 맨 아래에 있는지 여부를 결정합니다.

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>반환 값

탭 영역이 탭 창 맨 아래에 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="ctabbedpanem_btabsalwaystop"></a><a name="m_btabsalwaystop"></a> CTabbedPane:: m_bTabsAlwaysTop

애플리케이션에서 탭의 기본 위치입니다.

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>설명

응용 프로그램의 모든 탭이 탭 창의 맨 위에 표시 되도록 하려면이 정적 멤버를 TRUE로 설정 합니다.

탭 창을 만들기 전에이 값을 설정 해야 합니다.

기본값은 FALSE입니다.

## <a name="ctabbedpanem_ptabwndrtc"></a><a name="m_ptabwndrtc"></a> CTabbedPane:: m_pTabWndRTC

사용자 지정 `CMFCTabCtrl` 파생 개체에 대한 런타임 클래스 정보입니다.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>설명

`CMFCTabCtrl`탭 창 내에서 사용자 지정 탭 창을 사용 하는 경우이 정적 멤버 변수를 파생 개체의 런타임 클래스 정보에 대 한 포인터로 설정 합니다.

## <a name="ctabbedpaneresettabs"></a><a name="resettabs"></a> CTabbedPane::ResetTabs

모든 탭 창을 기본 상태로 다시 설정합니다.

```
static void ResetTabs();
```

### <a name="remarks"></a>설명

모든 탭 창을 기본 상태로 되돌리려면이 메서드를 호출 합니다. 이 메서드는 호출 되 면 모든 탭 창의 테두리 크기와 자동 색 상태를 다시 설정 합니다.

## <a name="ctabbedpanesettabautocolors"></a><a name="settabautocolors"></a> CTabbedPane:: SetTabAutoColors

자동 색 기능을 사용 하도록 설정할 때 사용 되는 사용자 지정 색 목록을 설정 합니다.

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>매개 변수

*arColors*<br/>
진행 설정할 색의 배열을 포함 합니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 자동 색 기능을 사용 하도록 설정 된 경우 사용 되는 색 목록을 사용자 지정할 수 있습니다. 이 함수는 정적 함수 이며 응용 프로그램의 모든 탭 창에 영향을 줍니다.

[CTabbedPane:: EnableTabAutoColor](#enabletabautocolor) 를 사용 하 여 자동 색 기능을 사용 하거나 사용 하지 않도록 설정할 수 있습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 클래스](../../mfc/reference/cdockablepane-class.md)<br/>
[CBaseTabbedPane 클래스](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBar 클래스](../../mfc/reference/cmfcoutlookbar-class.md)
