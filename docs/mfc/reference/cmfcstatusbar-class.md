---
title: CMFCStatusBar 클래스
ms.date: 11/19/2018
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
helpviewer_keywords:
- CMFCStatusBar [MFC], CalcFixedLayout
- CMFCStatusBar [MFC], CommandToIndex
- CMFCStatusBar [MFC], Create
- CMFCStatusBar [MFC], CreateEx
- CMFCStatusBar [MFC], DoesAllowDynInsertBefore
- CMFCStatusBar [MFC], EnablePaneDoubleClick
- CMFCStatusBar [MFC], EnablePaneProgressBar
- CMFCStatusBar [MFC], GetCount
- CMFCStatusBar [MFC], GetDrawExtendedArea
- CMFCStatusBar [MFC], GetExtendedArea
- CMFCStatusBar [MFC], GetItemID
- CMFCStatusBar [MFC], GetItemRect
- CMFCStatusBar [MFC], GetPaneInfo
- CMFCStatusBar [MFC], GetPaneProgress
- CMFCStatusBar [MFC], GetPaneStyle
- CMFCStatusBar [MFC], GetPaneText
- CMFCStatusBar [MFC], GetPaneWidth
- CMFCStatusBar [MFC], GetTipText
- CMFCStatusBar [MFC], InvalidatePaneContent
- CMFCStatusBar [MFC], PreCreateWindow
- CMFCStatusBar [MFC], SetDrawExtendedArea
- CMFCStatusBar [MFC], SetIndicators
- CMFCStatusBar [MFC], SetPaneAnimation
- CMFCStatusBar [MFC], SetPaneBackgroundColor
- CMFCStatusBar [MFC], SetPaneIcon
- CMFCStatusBar [MFC], SetPaneInfo
- CMFCStatusBar [MFC], SetPaneProgress
- CMFCStatusBar [MFC], SetPaneStyle
- CMFCStatusBar [MFC], SetPaneText
- CMFCStatusBar [MFC], SetPaneTextColor
- CMFCStatusBar [MFC], SetPaneWidth
- CMFCStatusBar [MFC], SetTipText
- CMFCStatusBar [MFC], OnDrawPane
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
ms.openlocfilehash: 004873ef2696eb9504cdd4df77e700c4a145e886
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686576"
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar 클래스

`CMFCStatusBar`클래스는 클래스와 유사한 상태 표시줄을 구현 합니다 `CStatusBar` . 그러나 `CMFCStatusBar` 클래스에는 `CStatusBar` 클래스에 의해 제공되지 않는 기능(예: 이미지, 애니메이션 및 진행률 표시줄을 표시하는 기능 및 마우스 두 번 클릭에 응답하는 기능)이 포함되어 있습니다.

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|Description|
|----------|-----------------|
|[CMFCStatusBar:: CalcFixedLayout](#calcfixedlayout)|( [Cbasepane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)를 재정의 합니다.)|
|[CMFCStatusBar:: CommandToIndex](#commandtoindex)||
|[CMFCStatusBar:: Create](#create)|컨트롤 막대를 만들어 [Cpane](../../mfc/reference/cpane-class.md) 개체에 연결 합니다. ( [Cpane:: Create](../../mfc/reference/cpane-class.md#create)를 재정의 합니다.)|
|[CMFCStatusBar:: CreateEx](#createex)|컨트롤 막대를 만들어 [Cpane](../../mfc/reference/cpane-class.md) 개체에 연결 합니다. ( [Cpane:: CreateEx](../../mfc/reference/cpane-class.md#createex)를 재정의 합니다.)|
|[CMFCStatusBar::D oesAllowDynInsertBefore](#doesallowdyninsertbefore)|이 창과 부모 프레임 사이에 다른 창이 동적으로 삽입 될 수 있는지 여부를 결정 합니다. [Cbasepane::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)를 재정의 합니다.|
|[CMFCStatusBar:: EnablePaneDoubleClick](#enablepanedoubleclick)|상태 표시줄에서 마우스를 두 번 클릭 하는 처리를 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CMFCStatusBar:: EnablePaneProgressBar](#enablepaneprogressbar)|지정 된 창에 진행률 표시줄을 표시 합니다.|
|[CMFCStatusBar:: GetCount](#getcount)|상태 표시줄의 창 수를 반환 합니다.|
|[CMFCStatusBar:: GetDrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar:: GetExtendedArea](#getextendedarea)||
|[CMFCStatusBar:: GetItemID](#getitemid)||
|[CMFCStatusBar:: GetItemRect](#getitemrect)||
|[CMFCStatusBar:: GetPaneInfo](#getpaneinfo)||
|[CMFCStatusBar:: GetPaneProgress](#getpaneprogress)||
|[CMFCStatusBar:: GetPaneStyle](#getpanestyle)|창 스타일을 반환 합니다. ( [Cbasepane:: GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle)를 재정의 합니다.)|
|[CMFCStatusBar:: GetPaneText](#getpanetext)||
|[CMFCStatusBar:: GetPaneWidth](#getpanewidth)|상태 표시줄에서 지정 된 창의 너비 (픽셀)를 반환 합니다.|
|[CMFCStatusBar:: GetTipText](#gettiptext)|상태 표시줄의 지정 된 창에 대 한 도구 설명 텍스트를 반환 합니다.|
|[CMFCStatusBar:: InvalidatePaneContent](#invalidatepanecontent)|지정 된 창을 무효화 하 고 해당 콘텐츠를 다시 그립니다.|
|[CMFCStatusBar::P reCreateWindow](#precreatewindow)|이 개체에 연결 된 Windows 창을 만들기 전에 프레임 워크에서 호출 `CWnd` 됩니다. ( [CWnd::P reCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)를 재정의 합니다.)|
|[CMFCStatusBar:: SetDrawExtendedArea](#setdrawextendedarea)||
|[CMFCStatusBar:: SetIndicators](#setindicators)||
|[CMFCStatusBar:: SetPaneAnimation](#setpaneanimation)|지정 된 창에 애니메이션을 할당 합니다.|
|[CMFCStatusBar:: SetPaneBackgroundColor](#setpanebackgroundcolor)|상태 표시줄의 지정 된 창에 대 한 배경색을 설정 합니다.|
|[CMFCStatusBar:: SetPaneIcon](#setpaneicon)|상태 표시줄의 지정 된 창에 대 한 표시기 아이콘을 설정 합니다.|
|[CMFCStatusBar:: SetPaneInfo](#setpaneinfo)||
|[CMFCStatusBar:: SetPaneProgress](#setpaneprogress)|상태 표시줄의 지정 된 창에 대 한 진행률 표시줄의 현재 진행률을 설정 합니다.|
|[CMFCStatusBar:: SetPaneStyle](#setpanestyle)|창 스타일을 설정 합니다. ( [Cbasepane:: SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle)를 재정의 합니다.)|
|[CMFCStatusBar:: SetPaneText](#setpanetext)||
|[CMFCStatusBar:: SetPaneTextColor](#setpanetextcolor)|상태 표시줄의 지정 된 창에 대 한 텍스트 색을 설정 합니다.|
|[CMFCStatusBar:: SetPaneWidth](#setpanewidth)|상태 표시줄에서 지정 된 창의 너비 (픽셀)를 설정 합니다.|
|[CMFCStatusBar:: SetTipText](#settiptext)|상태 표시줄의 지정 된 창에 대 한 도구 설명 텍스트를 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|Description|
|----------|-----------------|
|[CMFCStatusBar:: OnDrawPane](#ondrawpane)|상태 표시줄의 창을 다시 그리면 프레임 워크에서 호출 됩니다.|

## <a name="remarks"></a>설명

다음 다이어그램은 [상태 표시줄 데모 샘플](../../overview/visual-cpp-samples.md) 응용 프로그램의 상태 표시줄 그림을 보여 줍니다.

![CMFCStatusBar의 예제](../../mfc/reference/media/cmfcstatusbar.png "CMFCStatusBar의 예제")

## <a name="examples"></a>예제

다음 예제에서는 응용 프로그램이 클래스에서 다양 한 메서드를 호출 하는 데 사용 하는 지역 변수를 보여 줍니다 `CMFCStatusBar` . 이러한 변수는 StatusBarDemoView에서 선언 됩니다. 주 프레임은 Mainfrm.cpp에서 선언 되 고 문서는 StatusBarDemoDoc에서 선언 되며 뷰는 StatusBarDemoView에 선언 됩니다. 이 코드 조각은 [상태 표시줄 데모 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

다음 예제에서는 `CMFCStatusBar` `GetStatusBar` mainfrm.cpp에서 메서드를 소개 하 고 `GetStatusBar` StatusBarDemoView의 메서드에서이 메서드를 호출 하 여 개체에 대 한 참조를 가져오는 방법을 보여 줍니다. 이 코드 조각은 [상태 표시줄 데모 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

다음 예제에서는 StatusBarDemoView의 클래스에서 다양 한 메서드를 호출 하는 방법을 보여 줍니다 `CMFCStatusBar` . 상수는 Mainfrm.cpp에서 선언 됩니다. 이 예에서는 아이콘을 설정 하 고, 상태 표시줄 창의 도구 설명 텍스트를 설정 하 고, 지정 된 창에 진행률 표시줄을 표시 하 고, 지정 된 창에 애니메이션을 할당 하 고, 상태 표시줄 창의 텍스트와 너비를 설정 하 고, 상태 표시줄 창에 대 한 진행률 표시줄의 현재 진행률 표시기를 설정 하는 방법을 보여 줍니다. 이 코드 조각은 [상태 표시줄 데모 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxstatusbar

## <a name="cmfcstatusbarcalcfixedlayout"></a><a name="calcfixedlayout"></a> CMFCStatusBar:: CalcFixedLayout

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

## <a name="cmfcstatusbarcommandtoindex"></a><a name="commandtoindex"></a> CMFCStatusBar:: CommandToIndex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>매개 변수

진행 *nIDFind*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcstatusbarcreate"></a><a name="create"></a> CMFCStatusBar:: Create

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>매개 변수

진행 *pParentWnd*<br/>
진행 *Dwstyle*<br/>
진행 *nID*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcstatusbarcreateex"></a><a name="createex"></a> CMFCStatusBar:: CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>매개 변수

진행 *pParentWnd*<br/>
진행 *dwCtrlStyle*<br/>
진행 *Dwstyle*<br/>
진행 *nID*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcstatusbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a> CMFCStatusBar::D oesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcstatusbarenablepanedoubleclick"></a><a name="enablepanedoubleclick"></a> CMFCStatusBar:: EnablePaneDoubleClick

상태 표시줄에서 마우스를 두 번 클릭 하는 처리를 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 TRUE 이면 마우스를 두 번 클릭 하 여 처리할 수 있습니다. 그렇지 않으면 마우스를 두 번 클릭 하 여 처리를 사용 하지 않도록 설정 합니다.

### <a name="remarks"></a>설명

두 번 클릭을 처리 하기 위해 상태 표시줄을 사용 하도록 설정 하면 Windows에서 사용자가 상태 표시줄 창을 두 번 클릭할 때마다 리소스 ID와 함께 WM_COMMAND 알림을 상태 표시줄의 소유자에 게 보냅니다.

## <a name="cmfcstatusbarenablepaneprogressbar"></a><a name="enablepaneprogressbar"></a> CMFCStatusBar:: EnablePaneProgressBar

지정 된 창에 진행률 표시줄을 표시 합니다.

```cpp
void EnablePaneProgressBar(
    int nIndex,
    long nTotal=100,
    BOOL bDisplayText=FALSE,
    COLORREF clrBar=-1,
    COLORREF clrBarDest=-1,
    COLORREF clrProgressText=-1);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 진행률 표시줄이 활성화 될 창의 인덱스를 지정 합니다.

*총 n*<br/>
진행 진행률 표시줄의 최대값을 지정 합니다.

*bDisplayText*<br/>
진행 진행률 표시줄에 현재 진행 값을 표시할지 여부를 지정 합니다.

*clrBar*<br/>
진행 진행률 표시줄의 배경색을 지정 합니다.

*clrBarDest*<br/>
진행 진행률 표시줄 배경의 보조 색을 지정 합니다. 색 혼합을 그라데이션으로 채우려면 *Clrbar* 와 다른 값을 사용 합니다.

*clrProgressText*<br/>
진행 진행률 표시줄의 텍스트 색을 지정 합니다.

### <a name="remarks"></a>설명

`EnablePaneProgressBar` *Ntotal* 이-1로 설정 된 상태에서 진행률 표시줄 호출을 사용 하지 않도록 설정 하려는 경우 기본적으로 *Ntotal* 은 100로 설정 됩니다. 따라서 진행률을 백분율로 표시 하는 추가 계산은 필요 하지 않습니다.

진행률 표시줄의 배경색에 그라데이션으로 혼합 된 색이 표시 되도록 *Clrbar* 및 *clrbar dest* 에 대해 다른 값을 전달 해야 합니다. .

현재 진행률을 설정 하려면 [Cmfcstatusbar:: SetPaneProgress](#setpaneprogress) 메서드를 호출 합니다.

## <a name="cmfcstatusbargetcount"></a><a name="getcount"></a> CMFCStatusBar:: GetCount

상태 표시줄의 창 수를 검색 합니다.

```
int GetCount() const;
```

### <a name="return-value"></a>반환 값

상태 표시줄의 창 수입니다.

## <a name="cmfcstatusbargetdrawextendedarea"></a><a name="getdrawextendedarea"></a> CMFCStatusBar:: GetDrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcstatusbargetextendedarea"></a><a name="getextendedarea"></a> CMFCStatusBar:: GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>매개 변수

[in] *rect*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcstatusbargetitemid"></a><a name="getitemid"></a> CMFCStatusBar:: GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

진행 *n 인덱스*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcstatusbargetitemrect"></a><a name="getitemrect"></a> CMFCStatusBar:: GetItemRect

```cpp
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>매개 변수

진행 *n 인덱스*<br/>
진행 *lpRect*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcstatusbargetpaneinfo"></a><a name="getpaneinfo"></a> CMFCStatusBar:: GetPaneInfo

```cpp
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>매개 변수

진행 *n 인덱스*<br/>
진행 *nID*<br/>
진행 *Nstyle*<br/>
진행 *Cxwidth*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcstatusbargetpaneprogress"></a><a name="getpaneprogress"></a> CMFCStatusBar:: GetPaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

진행 *n 인덱스*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcstatusbargetpanestyle"></a><a name="getpanestyle"></a> CMFCStatusBar:: GetPaneStyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

진행 *n 인덱스*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcstatusbargetpanetext"></a><a name="getpanetext"></a> CMFCStatusBar:: GetPaneText

```cpp
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

진행 *n 인덱스*<br/>
진행 *s*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcstatusbargetpanewidth"></a><a name="getpanewidth"></a> CMFCStatusBar:: GetPaneWidth

상태 표시줄 창의 너비를 검색 합니다.

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 상태 표시줄 창의 인덱스를 지정 합니다.

### <a name="return-value"></a>반환 값

*Nindex* 가 지정 하는 상태 표시줄 창의 너비입니다. 그렇지 않으면 상태 표시줄 창이 없는 경우 0입니다.

## <a name="cmfcstatusbargettiptext"></a><a name="gettiptext"></a> CMFCStatusBar:: GetTipText

상태 표시줄 창의 도구 설명 텍스트를 검색 합니다.

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 도구 설명 텍스트를 검색할 창의 인덱스를 지정 합니다.

### <a name="return-value"></a>반환 값

*Nindex* 가 지정 하는 상태 표시줄 창의 도구 설명 텍스트입니다. 지정 된 *n 인덱스* 에 대해 상태 표시줄 창이 없거나 도구 설명 텍스트가 비어 있는 경우 빈 문자열이 고, 그렇지 않으면입니다.

## <a name="cmfcstatusbarinvalidatepanecontent"></a><a name="invalidatepanecontent"></a> CMFCStatusBar:: InvalidatePaneContent

상태 표시줄 창을 무효화 하 고 해당 콘텐츠를 다시 그립니다.

```cpp
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 내용을 무효화 하 고 다시 그릴 창의 인덱스를 지정 합니다.

### <a name="remarks"></a>설명

상태 표시줄이 무효화 되 면 다시 그리기로 표시 됩니다. `UpdateWindow`메서드가 메서드에 WM_PAINT 메시지를 보낼 때 Windows에서이를 다시 그립니다 `OnPaint` .

## <a name="cmfcstatusbarondrawpane"></a><a name="ondrawpane"></a> CMFCStatusBar:: OnDrawPane

상태 표시줄의 창을 다시 그립니다.

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 그리기를 위한 장치 컨텍스트에 대 한 포인터입니다.

*pPane*<br/>
진행 다시 `CMFCStatusBarPaneInfo` 그릴 창에 대 한 정보를 포함 하는 구조체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

기본적으로는 `OnDrawPane` 창의 스타일 및 내용에 따라 장치 컨텍스트 *pDC* 를 사용 하 여 창을 다시 그립니다.

파생 클래스에서이 메서드 `CMFCStatusBar` 를 재정의 하 여 창의 모양을 사용자 지정 합니다.

## <a name="cmfcstatusbarprecreatewindow"></a><a name="precreatewindow"></a> CMFCStatusBar::P reCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>매개 변수

진행 *cs*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcstatusbarsetdrawextendedarea"></a><a name="setdrawextendedarea"></a> CMFCStatusBar:: SetDrawExtendedArea

```cpp
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>매개 변수

진행 *bSet*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcstatusbarsetindicators"></a><a name="setindicators"></a> CMFCStatusBar:: SetIndicators

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>매개 변수

진행 *Lpidarray*<br/>
진행 *nIDCount*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcstatusbarsetpaneanimation"></a><a name="setpaneanimation"></a> CMFCStatusBar:: SetPaneAnimation

지정 된 창에 애니메이션을 할당 합니다.

```cpp
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 애니메이션에 할당 하려는 창의 인덱스를 지정 합니다.

*hImageList*<br/>
진행 애니메이션 프레임을 보유 하는 이미지 목록에 대 한 핸들을 지정 합니다.

*nFrameRate 속도*<br/>
진행 애니메이션의 프레임 주기 (밀리초)를 지정 합니다.

*bUpdate*<br/>
진행 TRUE 이면 창 콘텐츠를 즉시 업데이트 합니다. 그렇지 않으면 창 콘텐츠가 무효화 되 면 업데이트 됩니다.

### <a name="remarks"></a>설명

현재 애니메이션을 사용 하지 않도록 설정 하려면를 `SetPaneAnimation` NULL로 설정 하 여를 호출 `hImageList` 합니다.

## <a name="cmfcstatusbarsetpanebackgroundcolor"></a><a name="setpanebackgroundcolor"></a> CMFCStatusBar:: SetPaneBackgroundColor

상태 표시줄 창의 배경색을 설정 합니다.

```cpp
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 새 배경색을 설정할 창의 인덱스를 지정 합니다.

*clrBackground*<br/>
[in] 새 배경색을 지정합니다.

*bUpdate*<br/>
진행 TRUE 이면 창 콘텐츠를 즉시 업데이트 합니다. 그렇지 않으면 창이 다른 메서드에 의해 무효화 될 때까지 창 내용을 업데이트 하지 마십시오.

## <a name="cmfcstatusbarsetpaneicon"></a><a name="setpaneicon"></a> CMFCStatusBar:: SetPaneIcon

상태 표시줄 창의 아이콘을 설정 합니다.

```cpp
void SetPaneIcon(
    int nIndex,
    HICON hIcon,
    BOOL bUpdate=TRUE);

void SetPaneIcon(
    int nIndex,
    HBITMAP hBmp,
    COLORREF clrTransparent=RGB(255, 0, 255),
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 이미지를 설정할 창의 인덱스를 지정 합니다.

*hIcon*<br/>
진행 창 이미지로 설정할 아이콘에 대 한 핸들을 지정 합니다.

*bUpdate*<br/>
진행 창 콘텐츠를 즉시 업데이트할지 여부를 지정 합니다.

*hBmp*<br/>
진행 창 이미지로 설정 될 비트맵에 대 한 핸들을 지정 합니다.

*clrTransparent*<br/>
진행 *HBmp* 가 나타내는 비트맵의 투명 한 색을 지정 합니다.

### <a name="remarks"></a>설명

HICON 또는 HBITMAP을 투명 색과 함께 전달 하 여 창의 이미지를 설정할 수 있습니다. 이미지를 더 이상 표시 하지 않으려면 NULL 값을 이미지 핸들로 전달 합니다.

[Cmfcstatusbar:: SetPaneAnimation](#setpaneanimation) 가 설정 되어 있는 실행 중인 애니메이션이 있는 경우 애니메이션은 중지 됩니다.

## <a name="cmfcstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a> CMFCStatusBar:: SetPaneInfo

```cpp
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>매개 변수

진행 *n 인덱스*<br/>
진행 *nID*<br/>
진행 *Nstyle*<br/>
진행 *Cxwidth*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcstatusbarsetpaneprogress"></a><a name="setpaneprogress"></a> CMFCStatusBar:: SetPaneProgress

지정 된 창에 대 한 진행률 표시줄의 현재 진행률 표시기를 설정 합니다.

```cpp
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 진행률 표시기를 업데이트할 창의 인덱스를 지정 합니다.

*nCurr*<br/>
진행 진행률 표시기의 현재 값을 지정 합니다.

*bUpdate*<br/>
진행 창을 즉시 업데이트할지 여부를 지정 합니다.

### <a name="remarks"></a>설명

지정 된 창에서 진행률 표시줄의 진행률 표시기를 업데이트 하려는 경우이 메서드를 호출 합니다.

지정 된 창에이 함수를 사용 하려면 먼저 [Cmfcstatusbar:: EnablePaneProgressBar](#enablepaneprogressbar) 를 호출 해야 합니다.

## <a name="cmfcstatusbarsetpanestyle"></a><a name="setpanestyle"></a> CMFCStatusBar:: SetPaneStyle

```cpp
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>매개 변수

진행 *n 인덱스*<br/>
진행 *Nstyle*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcstatusbarsetpanetext"></a><a name="setpanetext"></a> CMFCStatusBar:: SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>매개 변수

진행 *n 인덱스*<br/>
진행 *lpszNewText*<br/>
진행 *bUpdate*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcstatusbarsetpanetextcolor"></a><a name="setpanetextcolor"></a> CMFCStatusBar:: SetPaneTextColor

지정 된 창의 텍스트 색을 설정 합니다.

```cpp
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 새 텍스트 색을 할당 하려는 창의 인덱스를 지정 합니다.

*clrText*<br/>
진행 텍스트 색을 지정 합니다.

*bUpdate*<br/>
진행 TRUE 이면 창 콘텐츠를 즉시 업데이트 합니다. 그렇지 않으면 창이 다른 메서드에 의해 무효화 될 때까지 창 내용을 업데이트 하지 마십시오.

## <a name="cmfcstatusbarsetpanewidth"></a><a name="setpanewidth"></a> CMFCStatusBar:: SetPaneWidth

상태 표시줄 창의 너비를 설정 합니다.

```cpp
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 새 너비를 설정할 상태 표시줄 창의 인덱스입니다.

*cx*<br/>
진행 상태 표시줄 창의 새 너비 (픽셀)입니다.

## <a name="cmfcstatusbarsettiptext"></a><a name="settiptext"></a> CMFCStatusBar:: SetTipText

상태 표시줄 창의 도구 설명 텍스트를 설정 합니다.

```cpp
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
진행 도구 설명 텍스트를 할당 하려는 창의 인덱스입니다.

*pszTipText*<br/>
진행 새 도구 설명 텍스트입니다.

## <a name="see-also"></a>추가 정보

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CPane 클래스](../../mfc/reference/cpane-class.md)<br/>
[CStatusBar 클래스](../../mfc/reference/cstatusbar-class.md)
