---
description: '자세히 알아보기: CMFCOutlookBar 클래스'
title: CMFCOutlookBar 클래스
ms.date: 06/25/2018
f1_keywords:
- CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar::AllowDestroyEmptyTabbedPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanAcceptPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanSetCaptionTextToTabName
- AFXOUTLOOKBAR/CMFCOutlookBar::Create
- AFXOUTLOOKBAR/CMFCOutlookBar::CreateCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::DoesAllowDynInsertBefore
- AFXOUTLOOKBAR/CMFCOutlookBar::FloatTab
- AFXOUTLOOKBAR/CMFCOutlookBar::GetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::GetTabArea
- AFXOUTLOOKBAR/CMFCOutlookBar::IsMode2003
- AFXOUTLOOKBAR/CMFCOutlookBar::OnAfterAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnBeforeAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnScroll
- AFXOUTLOOKBAR/CMFCOutlookBar::RemoveCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::SetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::SetMode2003
helpviewer_keywords:
- CMFCOutlookBar [MFC], AllowDestroyEmptyTabbedPane
- CMFCOutlookBar [MFC], CanAcceptPane
- CMFCOutlookBar [MFC], CanSetCaptionTextToTabName
- CMFCOutlookBar [MFC], Create
- CMFCOutlookBar [MFC], CreateCustomPage
- CMFCOutlookBar [MFC], DoesAllowDynInsertBefore
- CMFCOutlookBar [MFC], FloatTab
- CMFCOutlookBar [MFC], GetButtonsFont
- CMFCOutlookBar [MFC], GetTabArea
- CMFCOutlookBar [MFC], IsMode2003
- CMFCOutlookBar [MFC], OnAfterAnimation
- CMFCOutlookBar [MFC], OnBeforeAnimation
- CMFCOutlookBar [MFC], OnScroll
- CMFCOutlookBar [MFC], RemoveCustomPage
- CMFCOutlookBar [MFC], SetButtonsFont
- CMFCOutlookBar [MFC], SetMode2003
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
ms.openlocfilehash: e54e44e702aaf8d6883ada6be9c127f63ecee97d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265040"
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar 클래스

Microsoft Outlook 2000 또는 Outlook 2003의 **탐색 창** 과 시각적으로 유사한 탭 창입니다. 개체에는 `CMFCOutlookBar` [CMFCOutlookBarTabCtrl 클래스](../../mfc/reference/cmfcoutlookbartabctrl-class.md) 개체와 일련의 탭이 포함 되어 있습니다. 탭은 [CMFCOutlookBarPane 클래스](../../mfc/reference/cmfcoutlookbarpane-class.md) 개체 또는 파생 개체 중 하나일 수 있습니다 `CWnd` . Outlook 표시줄은 사용자에게 일련의 단추와 표시 영역으로 나타납니다. 사용자가 단추를 클릭하면 해당 컨트롤 또는 단추 창이 표시됩니다.

## <a name="syntax"></a>구문

```cpp
class CMFCOutlookBar : public CBaseTabbedPane
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CMFCOutlookBar::CMFCOutlookBar`|기본 생성자입니다.|
|`CMFCOutlookBar::~CMFCOutlookBar`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|빈 탭 창을 제거할 수 있는지 여부를 지정 합니다. [CBaseTabbedPane:: AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane)를 재정의 합니다.|
|[CMFCOutlookBar:: CanAcceptPane](#canacceptpane)|다른 창을 Outlook 표시줄 창에 도킹할 수 있는지 여부를 결정 합니다. (CDockablePane:: CanAcceptPane을 재정의 합니다.)|
|[CMFCOutlookBar:: CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|탭 창의 캡션에 활성 탭과 동일한 텍스트가 표시 되는지 여부를 결정 합니다. ( [CBaseTabbedPane:: CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname)을 재정의 합니다.)|
|[CMFCOutlookBar:: Create](#create)|Outlook bar 컨트롤을 만듭니다.|
|[CMFCOutlookBar:: CreateCustomPage](#createcustompage)|사용자 지정 Outlook 표시줄 탭을 만듭니다.|
|`CMFCOutlookBar::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|[CMFCOutlookBar::D oesAllowDynInsertBefore](#doesallowdyninsertbefore)|사용자가 Outlook 표시줄의 외부 가장자리에 컨트롤 막대를 도킹할 수 있는지 여부를 결정 합니다.|
|[CMFCOutlookBar:: FloatTab](#floattab)|창이 현재 분리 가능한 탭에 있는 경우에만 창을 부동 합니다. ( [CBaseTabbedPane:: FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)를 재정의 합니다.)|
|[CMFCOutlookBar:: GetButtonsFont](#getbuttonsfont)|Outlook 표시줄의 단추에 표시 되는 텍스트의 글꼴을 반환 합니다.|
|[CMFCOutlookBar:: GetTabArea](#gettabarea)|Outlook 표시줄에서 탭 영역의 크기와 위치를 반환 합니다. [CBaseTabbedPane:: GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea)를 재정의 합니다.|
|`CMFCOutlookBar::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCOutlookBar:: IsMode2003](#ismode2003)|Outlook 표시줄의 동작이 Outlook 2003 Microsoft Office와 유사한 지 여부를 확인 합니다 (설명 참조).|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|애니메이션을 사용 하 여 활성 탭이 설정 된 후 [CMFCOutlookBarTabCtrl:: SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) 에 의해 호출 됩니다.|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|애니메이션을 사용 하 여 탭 페이지가 활성 탭으로 설정 되기 전에 [CMFCOutlookBarTabCtrl:: SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) 에 의해 호출 됩니다.|
|[CMFCOutlookBar::OnScroll](#onscroll)|Outlook 표시줄이 위나 아래로 스크롤 하는 경우 프레임 워크에서 호출 됩니다.|
|[CMFCOutlookBar:: RemoveCustomPage](#removecustompage)|사용자 지정 Outlook 표시줄 탭을 제거 합니다.|
|[CMFCOutlookBar:: SetButtonsFont](#setbuttonsfont)|Outlook 표시줄의 단추에 표시 되는 텍스트의 글꼴을 설정 합니다.|
|[CMFCOutlookBar:: SetMode2003](#setmode2003)|Outlook 표시줄의 동작이 Outlook 2003와 유사한 지 여부를 지정 합니다 (설명 참조).|

## <a name="remarks"></a>설명

Outlook 표시줄의 예는 [OutlookDemo 샘플: MFC OutlookDemo 응용 프로그램](../../overview/visual-cpp-samples.md)을 참조 하세요.

## <a name="implementing-the-outlook-bar"></a>Outlook 표시줄 구현

애플리케이션에서 `CMFCOutlookBar` 컨트롤을 사용하려면 다음 단계를 수행합니다.

1. `CMFCOutlookBar` 개체를 주 프레임 창 클래스에 포함합니다.

    ```cpp
    class CMainFrame : public CMDIFrameWnd
    {
        // ...
        CMFCOutlookBar m_wndOutlookBar;
        CMFCOutlookBarPane m_wndOutlookPane;
        // ...
    };
    ```

1. 주 프레임에서 WM_CREATE 메시지를 처리할 때 [CMFCOutlookBar:: CREATE](#create) 메서드를 호출 하 여 Outlook 표시줄 탭 컨트롤을 만듭니다.

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. `CMFCOutlookBarTabCtrl` [CBaseTabbedPane:: GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)를 사용 하 여 내부에 대 한 포인터를 가져옵니다.

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. 단추가 포함 된 각 탭에 대해 [CMFCOutlookBarPane 클래스](../../mfc/reference/cmfcoutlookbarpane-class.md) 개체를 만듭니다.

    ```cpp
    m_wndOutlookPane.Create(&m_wndOutlookBar,
        AFX_DEFAULT_TOOLBAR_STYLE,
        ID_OUTLOOK_PANE_GENERAL,
        AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);

    // make the Outlook pane detachable (enable docking)
    m_wndOutlookPane.EnableDocking(CBRS_ALIGN_ANY);

    // add buttons
    m_wndOutlookPane.AddButton(theApp.LoadIcon (IDR_MAINFRAME),
        "About",
        ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON),
        "Open",
        ID_FILE_OPEN);
    ```

1. [CMFCOutlookBarTabCtrl:: addtab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) 을 호출 하 여 각각의 새 탭을 추가 합니다. *Bdetachable* 가능 매개 변수를 FALSE로 설정 하 여 페이지를 분리 하지 않도록 설정 합니다. 또는 [CMFCOutlookBarTabCtrl:: AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) 를 사용 하 여 분리 가능한 페이지를 추가 합니다.

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. `CWnd`파생 컨트롤 (예: [CMFCShellTreeCtrl 클래스](../../mfc/reference/cmfcshelltreectrl-class.md))을 탭으로 추가 하려면 컨트롤을 만들고 [CMFCOutlookBarTabCtrl:: addtab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) 을 호출 하 여 Outlook 표시줄에 추가 합니다.

> [!NOTE]
> 각 [CMFCOutlookBarPane 클래스](../../mfc/reference/cmfcoutlookbarpane-class.md) 개체와 각 파생 개체에 대해 고유한 컨트롤 id를 사용 해야 합니다 `CWnd` .

런타임에 새 페이지를 동적으로 추가 하거나 삭제 하려면 [CMFCOutlookBar:: CreateCustomPage](#createcustompage) 및 [CMFCOutlookBar:: RemoveCustomPage](#removecustompage)를 사용 합니다.

## <a name="outlook-2003-mode"></a>Outlook 2003 모드

Outlook 2003 모드에서 탭 단추는 Outlook 표시줄 창의 아래쪽에 배치 됩니다. 단추를 표시 하는 데 충분 한 공간이 없는 경우 창의 아래쪽에 있는 도구 모음과 같은 영역에 아이콘으로 표시 됩니다.

[CMFCOutlookBar:: SetMode2003](#setmode2003) 를 사용 하 여 Outlook 2003 모드를 사용 하도록 설정 합니다. [CMFCOutlookBarTabCtrl:: set도구 모음 imagelist](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) 를 사용 하 여 Outlook 표시줄의 아래쪽에 표시 되는 아이콘을 포함 하는 비트맵을 설정 합니다. 비트맵의 아이콘은 탭 인덱스를 기준으로 정렬 되어야 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxoutlookbar

## <a name="cmfcoutlookbarallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a> CMFCOutlookBar:: AllowDestroyEmptyTabbedPane

빈 탭 창을 제거할 수 있는지 여부를 지정 합니다.

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>반환 값

빈 탭 창을 제거할 수 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다. 기본 구현에서는 항상 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

빈 탭 창을 제거할 수 없는 경우 프레임 워크에서 해당 창을 숨깁니다.

## <a name="cmfcoutlookbarcanacceptpane"></a><a name="canacceptpane"></a> CMFCOutlookBar:: CanAcceptPane

다른 창을 Outlook 표시줄 창에 도킹할 수 있는지 여부를 결정 합니다.

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
진행 이 창에 도킹 되는 다른 창에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

Outlook 표시줄 창에 다른 창을 도킹할 수 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

Outlook 표시줄이 Outlook 2003 모드에 있는 경우에는 도킹이 지원 되지 않으므로 반환 값은 FALSE입니다.

*Pbar* 매개 변수가 NULL 이면이 메서드는 FALSE를 반환 합니다.

그렇지 않으면이 메서드는 기본 메서드인 [Cbasepane:: CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane)으로 동작 합니다. 단, 도킹을 사용 하지 않는 경우에도 outlook 표시줄에서 다른 outlook 표시줄을 계속 도킹할 수 있습니다.

## <a name="cmfcoutlookbarcansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a> CMFCOutlookBar:: CanSetCaptionTextToTabName

탭 창의 캡션에 활성 탭과 동일한 텍스트가 표시 되는지 여부를 결정 합니다.

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>반환 값

Outlook 표시줄 창 캡션이 자동으로 활성 탭의 텍스트로 설정 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 기능을 사용 하거나 사용 하지 않도록 설정 하려면 [CBaseTabbedPane:: EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) 을 사용 합니다.

Outlook 2003 모드에서이 설정은 항상 사용 하도록 설정 되어 있습니다.

## <a name="cmfcoutlookbarcreate"></a><a name="create"></a> CMFCOutlookBar:: Create

Outlook bar 컨트롤을 만듭니다.

```cpp
virtual BOOL Create(
    LPCTSTR lpszCaption,
    CWnd* pParentWnd,
    const RECT& rect,
    UINT nID,
    DWORD dwStyle,
    DWORD dwControlBarStyle=AFX_CBRS_RESIZE,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>매개 변수

*lpszCaption*<br/>
진행 창 캡션을 지정 합니다.

*pParentWnd*<br/>
진행 부모 창에 대 한 포인터를 지정 합니다. NULL이 아니어야 합니다.

*rect*<br/>
진행 Outlook 표시줄 크기와 위치 (픽셀)를 지정 합니다.

*nID*<br/>
진행 컨트롤 ID를 지정 합니다. 응용 프로그램에서 사용 되는 다른 컨트롤 Id와는 달라 야 합니다.

*dwStyle*<br/>
진행 원하는 컨트롤 막대 스타일을 지정 합니다. 가능한 값은 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)을 참조 하세요.

*Dwcontrol바 스타일*<br/>
진행 특수 라이브러리 정의 스타일을 지정 합니다.

*pContext*<br/>
진행 컨텍스트를 만듭니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CMFCOutlookBar`두 단계로 개체를 구성 합니다. 먼저 생성자를 호출한 다음을 호출 하 여 `Create` outlook 표시줄 컨트롤을 만들고이를 개체에 연결 `CMFCOutlookBar` 합니다.

*Dwcontrolbarstyle* 에서 지정 하는 사용 가능한 라이브러리 정의 스타일의 목록은 [Cbasepane:: createex](../../mfc/reference/cbasepane-class.md#createex) 를 참조 하세요.

### <a name="example"></a>예제

다음 예제에서는 클래스의 메서드를 사용 하는 방법을 보여 줍니다 `Create` `CMFCOutlookBar` . 이 코드 조각은 [Outlook 다중 보기 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

## <a name="cmfcoutlookbarcreatecustompage"></a><a name="createcustompage"></a> CMFCOutlookBar:: CreateCustomPage

사용자 지정 Outlook 표시줄 탭을 만듭니다.

```cpp
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,
    BOOL bActivatePage=TRUE,
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,
    BOOL bEnableTextLabels=TRUE);
```

### <a name="parameters"></a>매개 변수

*lpszPageName*<br/>
진행 페이지 레이블입니다.

*bActivatePage*<br/>
진행 TRUE 이면 페이지를 만들 때 활성화 됩니다.

*dwEnabledDocking*<br/>
진행 페이지가 분리 될 때 사용 되는 도킹 면을 지정 하는 CBRS_ALIGN_ 플래그의 조합입니다.

*bEnableTextLabels*<br/>
진행 TRUE 이면 페이지에 있는 단추에 대해 텍스트 레이블이 사용 됩니다.

### <a name="return-value"></a>반환 값

새로 만든 페이지에 대 한 포인터 이거나, 만들지 못한 경우 NULL입니다.

### <a name="remarks"></a>설명

사용자가 사용자 지정 Outlook 표시줄 페이지를 만들 수 있도록 하려면이 메서드를 사용 합니다. 응용 프로그램당 최대 100 페이지를 만들 수 있습니다. 페이지 컨트롤 Id는 0xF000부터 시작 합니다. 사용자 지정 Outlook 표시줄 페이지의 총 수가 100을 초과 하면 생성이 실패 합니다.

[CMFCOutlookBar:: RemoveCustomPage](#removecustompage) 를 사용 하 여 사용자 지정 페이지를 삭제 합니다.

## <a name="cmfcoutlookbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a> CMFCOutlookBar::D oesAllowDynInsertBefore

사용자가 Outlook 표시줄의 외부 가장자리에 창을 도킹할 수 있는지 여부를 지정 합니다.

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>반환 값

기본 구현에서는 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

프레임 워크는 `DoesAllowDynInsertBefore` 동적 창을 도킹할 위치를 찾을 때 메서드를 호출 합니다. 함수가 FALSE를 반환 하는 경우 프레임 워크는 창의 외부 가장자리에 있는 동적 창의 도킹을 허용 하지 않습니다.

일반적으로 Outlook 표시줄을 정적 부동 컨트롤로 만듭니다. 파생 클래스에서이 함수를 재정의 하 고 TRUE를 반환 하 여이 동작을 변경할 수 있습니다.

> [!NOTE]
> 동적 창이 도킹 될 때 도킹 된 정적 창의 상태를 확인 하므로 가능 하면 항상 정적 창 다음에 동적 창을 도킹 해야 합니다.

## <a name="cmfcoutlookbarfloattab"></a><a name="floattab"></a> CMFCOutlookBar:: FloatTab

창을 부동 합니다.

```cpp
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide);
```

### <a name="parameters"></a>매개 변수

*pBar*<br/>
진행 부동 창에 대 한 포인터입니다.

*nTabID*<br/>
진행 부동 소수점 탭의 인덱스 (0부터 시작)입니다.

*dockMethod*<br/>
진행 창을 부동으로 만드는 데 사용할 메서드를 지정 합니다.  자세한 내용은 [CBaseTabbedPane:: FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)를 참조 하세요.

*bHide*<br/>
진행 창을 부동 소수점 앞으로 숨기려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 이 메서드의 기본 클래스 버전과 달리이 매개 변수에는 기본값이 없습니다.

### <a name="return-value"></a>반환 값

창이 부동이 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Outlook bar 컨트롤의 마지막 남은 탭을 부동으로 설정 하지 않는다는 점을 제외 하 고는 [CBaseTabbedPane:: FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab) 와 비슷합니다.

## <a name="cmfcoutlookbargetbuttonsfont"></a><a name="getbuttonsfont"></a> CMFCOutlookBar:: GetButtonsFont

Outlook 표시줄의 페이지 단추 탭에 있는 텍스트의 글꼴을 반환 합니다.

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>반환 값

Outlook 표시줄 페이지 단추 탭에 텍스트를 표시 하는 데 사용 되는 글꼴 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여 Outlook 페이지 단추 탭에서 텍스트를 표시 하는 데 사용 되는 글꼴을 검색 합니다. [CMFCOutlookBar:: SetButtonsFont](#setbuttonsfont)에서를 호출 하 여 글꼴을 설정할 수 있습니다.

## <a name="cmfcoutlookbargettabarea"></a><a name="gettabarea"></a> CMFCOutlookBar:: GetTabArea

Outlook 표시줄에서 탭 영역의 크기와 위치를 결정 합니다.

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>매개 변수

*rectTabAreaTop*<br/>
제한이 함수가 반환 될 때 위쪽 탭 영역의 크기와 위치 (클라이언트 좌표)를 포함 합니다.

*rectTabAreaBottom*<br/>
제한이 함수가 반환 될 때 아래쪽 탭 영역의 크기와 위치 (클라이언트 좌표)를 포함 합니다.

### <a name="remarks"></a>설명

프레임 워크는이 메서드를 호출 하 여 대상 창에 대 한 도킹 형식을 결정 합니다. 프레임 워크에서 사용자가 창을 대상 창의 탭 영역을 통해 도킹 되도록 끌면 대상 창의 새 탭으로 첫 번째 창을 추가 하려고 시도 합니다. 그렇지 않으면 대상 창의 적절 한 쪽에 첫 번째 창을 도킹 하려고 시도 합니다. 프레임 워크는 추가 도킹 된 창을 수용할 수 있는 슬라이더를 사용 하 여 새 컨테이너를 만듭니다.

의 기본 구현은 outlook 표시줄이 `GetTabArea` 정적인 경우 outlook 표시줄의 전체 클라이언트 영역을 반환 합니다. 즉, outlook 표시줄이 부동으로 표시 되지 않습니다. 그렇지 않으면 페이지 단추가 Outlook bar 컨트롤의 위쪽과 아래쪽에 표시 되는 영역을 반환 합니다.

이 동작을 변경 하려면에서 파생 된 클래스의이 메서드를 재정의 `CMFCOutlookBar` 합니다.

## <a name="cmfcoutlookbarismode2003"></a><a name="ismode2003"></a> CMFCOutlookBar:: IsMode2003

Outlook 표시줄의 동작이 Outlook 2003 Microsoft Office의 동작을 모방 하는지 여부를 지정 합니다.

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>반환 값

Outlook 표시줄이 Microsoft Office 2003 모드로 실행 되는 경우 0이 아님 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[CMFCOutlookBar:: SetMode2003](#setmode2003)를 사용 하 여이 모드를 사용 하도록 설정할 수 있습니다.

## <a name="cmfcoutlookbaronafteranimation"></a><a name="onafteranimation"></a> CMFCOutlookBar:: OnAfterAnimation

애니메이션을 사용 하 여 활성 탭이 설정 된 후 [CMFCOutlookBarTabCtrl:: SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) 에 의해 호출 됩니다.

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>매개 변수

*nPage*<br/>
진행 활성 상태로 설정 된 탭 페이지의 인덱스 (0부터 시작)입니다.

### <a name="remarks"></a>설명

활성 탭을 설정 하는 시각적 효과는 애니메이션을 사용 하도록 설정 했는지 여부에 따라 달라 집니다. 자세한 내용은 [CMFCOutlookBarTabCtrl:: EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation)를 참조 하세요.

## <a name="cmfcoutlookbaronbeforeanimation"></a><a name="onbeforeanimation"></a> CMFCOutlookBar:: OnBeforeAnimation

애니메이션을 사용 하 여 탭 페이지가 활성 탭으로 설정 되기 전에 [CMFCOutlookBarTabCtrl:: SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) 에 의해 호출 됩니다.

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>매개 변수

*nPage*<br/>
진행 활성 상태로 설정 될 탭 페이지의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

새 활성 탭을 설정 하는 데 애니메이션을 사용 해야 하면 TRUE를 반환 하 고, 애니메이션을 사용 하지 않도록 설정 하려면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

## <a name="cmfcoutlookbaronscroll"></a><a name="onscroll"></a> CMFCOutlookBar:: OnScroll

Outlook 표시줄이 위나 아래로 스크롤 하는 경우 프레임 워크에서 호출 됩니다.

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>매개 변수

*bDown*<br/>
진행 Outlook 표시줄이 스크롤 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="cmfcoutlookbarremovecustompage"></a><a name="removecustompage"></a> CMFCOutlookBar:: RemoveCustomPage

사용자 지정 Outlook 표시줄 탭 페이지를 제거 합니다.

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>매개 변수

*uiPage*<br/>
진행 부모 Outlook 창에 있는 페이지의 인덱스 (0부터 시작)입니다.

*pTargetWnd*<br/>
진행 부모 Outlook 창으로 이동할 수 있습니다.

### <a name="return-value"></a>반환 값

사용자 지정 페이지가 성공적으로 제거 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

사용자 지정 페이지를 삭제 하려면이 함수를 호출 합니다. 페이지를 제거 하면 해당 컨트롤 ID가 사용 가능한 Id의 풀로 반환 됩니다.

현재 제거 될 페이지가 있는 [CMFCOutlookBarTabCtrl 클래스](../../mfc/reference/cmfcoutlookbartabctrl-class.md) 개체에 대 한 포인터를 제공 해야 합니다. 사용자는 서로 다른 Outlook 표시줄 사이에서 분리 가능한 페이지를 이동할 수 있지만 사용자 지정 페이지에 대 한 정보는 [CMFCOutlookBar:: CreateCustomPage](#createcustompage)를 호출한 Outlook bar 개체에 있습니다.

[CBaseTabbedPane:: GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) 를 사용 하 여 Outlook 창에 대 한 포인터를 가져옵니다.

## <a name="cmfcoutlookbarsetbuttonsfont"></a><a name="setbuttonsfont"></a> CMFCOutlookBar:: SetButtonsFont

Outlook 표시줄의 단추에 표시 되는 텍스트의 글꼴을 설정 합니다.

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>매개 변수

*pFont*<br/>
진행 새 글꼴을 지정 합니다.

*bRedraw*<br/>
진행 TRUE 이면 Outlook 표시줄이 다시 그려집니다.

### <a name="remarks"></a>설명

Outlook 탭 페이지 단추에 표시 되는 텍스트의 글꼴을 설정 하려면이 메서드를 사용 합니다.

## <a name="cmfcoutlookbarsetmode2003"></a><a name="setmode2003"></a> CMFCOutlookBar:: SetMode2003

Outlook 표시줄의 동작이 Outlook 2003와 유사한 지 여부를 지정 합니다.

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>매개 변수

*bMode2003*<br/>
진행 TRUE 이면 Office 2003 모드가 사용 됩니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여 Office 2003 모드를 사용 하거나 사용 하지 않도록 설정 합니다. 이 모드에서 Outlook 표시줄에는 사용자 지정 단추를 포함 하는 추가 도구 모음이 있습니다. Outlook 표시줄의 동작은 Microsoft Office 2003의 Outlook 표시줄 동작을 따릅니다.

기본적으로이 모드는 비활성화 되어 있습니다.

> [!NOTE]
> 이 함수는 [CMFCOutlookBar:: Create](#create)전에 호출 해야 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CBaseTabbedPane 클래스](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBarTabCtrl 클래스](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[CMFCOutlookBarPane 클래스](../../mfc/reference/cmfcoutlookbarpane-class.md)
