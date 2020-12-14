---
description: '자세한 정보: CStatusBar 클래스'
title: CStatusBar 클래스
ms.date: 11/04/2016
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
helpviewer_keywords:
- CStatusBar [MFC], CStatusBar
- CStatusBar [MFC], CommandToIndex
- CStatusBar [MFC], Create
- CStatusBar [MFC], CreateEx
- CStatusBar [MFC], DrawItem
- CStatusBar [MFC], GetItemID
- CStatusBar [MFC], GetItemRect
- CStatusBar [MFC], GetPaneInfo
- CStatusBar [MFC], GetPaneStyle
- CStatusBar [MFC], GetPaneText
- CStatusBar [MFC], GetStatusBarCtrl
- CStatusBar [MFC], SetIndicators
- CStatusBar [MFC], SetPaneInfo
- CStatusBar [MFC], SetPaneStyle
- CStatusBar [MFC], SetPaneText
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
ms.openlocfilehash: 61f3c920c1607862ad0ddc1329293b7b67dcde90
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345084"
---
# <a name="cstatusbar-class"></a>CStatusBar 클래스

텍스트 출력 창의 행 또는 "지표"가 있는 컨트롤 막대입니다.

## <a name="syntax"></a>구문

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CStatusBar:: CStatusBar](#cstatusbar)|`CStatusBar` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CStatusBar:: CommandToIndex](#commandtoindex)|지정 된 표시기 ID의 인덱스를 가져옵니다.|
|[CStatusBar:: Create](#create)|상태 표시줄을 만들고, 개체에 연결 하 `CStatusBar` 고, 초기 글꼴 및 막대 높이를 설정 합니다.|
|[CStatusBar:: CreateEx](#createex)|포함 된 `CStatusBar` 개체에 대 한 추가 스타일을 사용 하 여 개체를 만듭니다 `CStatusBarCtrl` .|
|[CStatusBar::D rawItem](#drawitem)|소유자 그리기 상태 표시줄 컨트롤의 시각적 측면이 변경 될 때 호출 됩니다.|
|[CStatusBar:: GetItemID](#getitemid)|지정 된 인덱스에 대 한 표시기 ID를 가져옵니다.|
|[CStatusBar:: GetItemRect](#getitemrect)|지정 된 인덱스의 표시 사각형을 가져옵니다.|
|[CStatusBar:: GetPaneInfo](#getpaneinfo)|지정 된 인덱스에 대 한 표시기 ID, 스타일 및 너비를 가져옵니다.|
|[CStatusBar:: GetPaneStyle](#getpanestyle)|지정 된 인덱스에 대 한 표시기 스타일을 가져옵니다.|
|[CStatusBar:: GetPaneText](#getpanetext)|지정 된 인덱스에 대 한 표시기 텍스트를 가져옵니다.|
|[CStatusBar:: GetStatusBarCtrl](#getstatusbarctrl)|기본 공용 컨트롤에 직접 액세스할 수 있습니다.|
|[CStatusBar:: SetIndicators](#setindicators)|표시기 Id를 설정 합니다.|
|[CStatusBar:: SetPaneInfo](#setpaneinfo)|지정 된 인덱스에 대 한 표시기 ID, 스타일 및 두께를 설정 합니다.|
|[CStatusBar:: SetPaneStyle](#setpanestyle)|지정 된 인덱스에 대 한 표시기 스타일을 설정 합니다.|
|[CStatusBar:: SetPaneText](#setpanetext)|지정 된 인덱스에 대 한 표시기 텍스트를 설정 합니다.|

## <a name="remarks"></a>설명

출력 창은 일반적으로 메시지 선과 상태 표시기로 사용 됩니다. 예를 들어 선택한 메뉴 명령을 간략하게 설명 하는 메뉴 도움말 메시지 줄과 스크롤 잠금, NUM LOCK 및 기타 키의 상태를 표시 하는 표시기가 있습니다.

MFC 4.0의 새로운 멤버인 [Cstatusbar:: GetStatusBarCtrl](#getstatusbarctrl)를 사용 하면 상태 표시줄 사용자 지정 및 추가 기능에 대 한 Windows 공용 컨트롤의 지원을 활용할 수 있습니다. `CStatusBar` 멤버 함수는 Windows 공용 컨트롤의 기능을 대부분 제공 합니다. 그러나를 호출할 때 상태 표시줄에 `GetStatusBarCtrl` Windows 95/98 상태 표시줄의 특성을 더 많이 제공할 수 있습니다. 를 호출 하는 경우 `GetStatusBarCtrl` 개체에 대 한 참조를 반환 `CStatusBarCtrl` 합니다. Windows 공용 컨트롤을 사용 하 여 도구 모음 디자인에 대 한 자세한 내용은 [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) 를 참조 하세요. 공용 컨트롤에 대 한 일반적인 정보는 Windows SDK의 [공용 컨트롤](/windows/win32/Controls/common-controls-intro) 을 참조 하세요.

프레임 워크는 위치 0에서 맨 왼쪽 표시기가 있는 배열에 표시기 정보를 저장 합니다. 상태 표시줄을 만들 때 프레임 워크가 해당 표시기와 연결 하는 문자열 Id 배열을 사용 합니다. 그런 다음 문자열 ID 또는 인덱스를 사용 하 여 표시기에 액세스할 수 있습니다.

기본적으로 첫 번째 표시기는 "탄력적"입니다. 다른 표시기 창에서 사용 하지 않는 상태 표시줄 길이를 차지 하므로 다른 창이 오른쪽에 맞춰집니다.

상태 표시줄을 만들려면 다음 단계를 수행 합니다.

1. `CStatusBar` 개체를 생성합니다.

1. [Create](#create) (또는 [createex](#createex)) 함수를 호출 하 여 상태 표시줄 창을 만들고 개체에 연결 `CStatusBar` 합니다.

1. [Setindicators](#setindicators) 를 호출 하 여 각 표시기와 문자열 ID를 연결 합니다.

상태 표시줄 창에서 텍스트를 업데이트 하는 방법에는 다음 세 가지가 있습니다.

1. [CWnd:: SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) 를 호출 하 여 창 0 에서만 텍스트를 업데이트 합니다.

1. 상태 표시줄의 ON_UPDATE_COMMAND_UI 처리기에서 [CCmdUI:: SetText](../../mfc/reference/ccmdui-class.md#settext) 를 호출 합니다.

1. [SetPaneText](#setpanetext) 를 호출 하 여 모든 창에 대 한 텍스트를 업데이트 합니다.

[SetPaneStyle](#setpanestyle) 를 호출 하 여 상태 표시줄 창의 스타일을 업데이트 합니다.

사용에 대 한 자세한 내용은 `CStatusBar` [MFC의 상태 표시줄 구현](../../mfc/status-bar-implementation-in-mfc.md) 및 [기술 참고 31: 컨트롤 막대](../../mfc/tn031-control-bars.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>요구 사항

**헤더:** afxext.h

## <a name="cstatusbarcommandtoindex"></a><a name="commandtoindex"></a> CStatusBar:: CommandToIndex

지정 된 ID에 대 한 표시기 인덱스를 가져옵니다.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>매개 변수

*nIDFind*<br/>
인덱스를 검색할 표시기의 문자열 ID입니다.

### <a name="return-value"></a>반환 값

성공 하는 경우 표시기의 인덱스입니다. 성공 하지 않으면-1입니다.

### <a name="remarks"></a>설명

첫 번째 표시기의 인덱스는 0입니다.

## <a name="cstatusbarcreate"></a><a name="create"></a> CStatusBar:: Create

상태 표시줄 (자식 창)을 만들고이를 개체에 연결 `CStatusBar` 합니다.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
Windows 창이 상태 표시줄의 부모 인 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 포인터입니다.

*dwStyle*<br/>
상태 표시줄 스타일입니다. 표준 Windows [스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)외에도 이러한 스타일이 지원 됩니다.

- CBRS_TOP 컨트롤 막대는 프레임 창의 맨 위에 있습니다.

- CBRS_BOTTOM 컨트롤 막대는 프레임 창의 맨 아래에 있습니다.

- CBRS_NOALIGN 컨트롤 막대는 부모 크기를 조정할 때 위치가 변경 되지 않습니다.

*nID*<br/>
도구 모음의 자식 창 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

또한 초기 글꼴을 설정 하 고 상태 표시줄의 높이를 기본값으로 설정 합니다.

## <a name="cstatusbarcreateex"></a><a name="createex"></a> CStatusBar:: CreateEx

이 함수를 호출 하 여 상태 표시줄 (자식 창)을 만들고이를 개체에 연결 `CStatusBar` 합니다.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
Windows 창이 상태 표시줄의 부모 인 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 포인터입니다.

*dwCtrlStyle*<br/>
포함 된 [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) 개체 만들기에 대 한 추가 스타일입니다. 기본값은 크기 조정 그립 또는 도구 설명 지원 없이 상태 표시줄을 지정 합니다. 지원 되는 상태 표시줄 스타일은 다음과 같습니다.

- 상태 표시줄 컨트롤 SBARS_SIZEGRIP 상태 표시줄의 오른쪽 끝에 크기 조정 그립이 포함 됩니다. 크기 조정 그립은 크기 조정 테두리와 유사 합니다. 사용자가 클릭 하 고 끌어서 부모 창의 크기를 조정할 수 있는 사각형 영역입니다.

- SBT_TOOLTIPS 상태 표시줄에서 도구 설명을 지원 합니다.

이러한 스타일에 대 한 자세한 내용은 [CStatusBarCtrl에 대 한 설정](../../mfc/settings-for-the-cstatusbarctrl.md)을 참조 하세요.

*dwStyle*<br/>
상태 표시줄 스타일입니다. 기본값은 프레임 창 맨 아래에 표시 되는 상태 표시줄을 만들도록 지정 합니다. [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles) 및 [CDialogBar:: Create](../../mfc/reference/cdialogbar-class.md#create)에 나열 된 상태 표시줄 컨트롤 스타일의 조합을 적용 합니다. 그러나이 매개 변수는 항상 WS_CHILD 및 WS_VISIBLE 스타일을 포함 해야 합니다.

*nID*<br/>
상태 표시줄의 자식 창 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

또한이 함수는 초기 글꼴을 설정 하 고 상태 표시줄의 높이를 기본값으로 설정 합니다.

`CreateEx`포함 된 상태 표시줄 컨트롤을 만드는 동안 특정 스타일을 제공 해야 하는 경우 [Create](#create)대신를 사용 합니다. 예를 들어 *dwCtrlStyle* 를 SBT_TOOLTIPS 설정 하 여 상태 표시줄 개체에 도구 설명을 표시 합니다.

## <a name="cstatusbarcstatusbar"></a><a name="cstatusbar"></a> CStatusBar:: CStatusBar

개체를 생성 `CStatusBar` 하 고 필요한 경우 기본 상태 표시줄 글꼴을 만든 다음 글꼴 특성을 기본값으로 설정 합니다.

```
CStatusBar();
```

## <a name="cstatusbardrawitem"></a><a name="drawitem"></a> CStatusBar::D rawItem

이 멤버 함수는 소유자가 그린 상태 표시줄의 시각적 측면이 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>매개 변수

*lpDrawItemStruct*<br/>
필요한 그리기 형식에 대 한 정보를 포함 하는 [Drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) 구조체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`itemAction`구조체의 멤버는 `DRAWITEMSTRUCT` 수행할 그리기 작업을 정의 합니다. 소유자 그리기 개체에 대 한 그리기를 구현 하려면이 멤버 함수를 재정의 `CStatusBar` 합니다. 응용 프로그램은이 멤버 함수를 종료 하기 전에 *Lpdrawitemstruct* 에 제공 된 표시 컨텍스트에 대해 선택한 모든 GDI (그래픽 장치 인터페이스) 개체를 복원 해야 합니다.

## <a name="cstatusbargetitemid"></a><a name="getitemid"></a> CStatusBar:: GetItemID

*Nindex* 로 지정 된 표시기의 ID를 반환 합니다.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
ID를 검색할 표시기의 인덱스입니다.

### <a name="return-value"></a>반환 값

*Nindex* 로 지정 된 표시기의 ID입니다.

## <a name="cstatusbargetitemrect"></a><a name="getitemrect"></a> CStatusBar:: GetItemRect

*Nindex* 로 지정 된 표시기의 좌표를 *lpRect* 가 가리키는 구조체로 복사 합니다.

```cpp
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
사각형 좌표를 검색할 표시기의 인덱스입니다.

*lpRect*<br/>
*N index* 로 지정 된 표시기의 좌표를 수신 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 또는 [crect](../../atl-mfc-shared/reference/crect-class.md) 개체를 가리킵니다.

### <a name="remarks"></a>설명

좌표는 상태 표시줄의 왼쪽 위 모퉁이를 기준으로 하는 픽셀 단위입니다.

## <a name="cstatusbargetpaneinfo"></a><a name="getpaneinfo"></a> CStatusBar:: GetPaneInfo

*NID*, *Nstyle* 및 *Cxwidth* 를 *nstyle* 로 지정 된 위치에 있는 표시기 창의 ID, 스타일 및 너비로 설정 합니다.

```cpp
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
정보를 검색할 창의 인덱스입니다.

*nID*<br/>
창의 ID로 설정 된 UINT에 대 한 참조입니다.

*nStyle*<br/>
창의 스타일로 설정 된 UINT에 대 한 참조입니다.

*cxWidth*<br/>
창의 너비로 설정 된 정수에 대 한 참조입니다.

## <a name="cstatusbargetpanestyle"></a><a name="getpanestyle"></a> CStatusBar:: GetPaneStyle

상태 표시줄 창의 스타일을 검색 하려면이 멤버 함수를 호출 합니다.

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
스타일을 검색할 창의 인덱스입니다.

### <a name="return-value"></a>반환 값

*Nindex* 로 지정 된 상태 표시줄 창의 스타일입니다.

### <a name="remarks"></a>설명

창의 스타일은 창이 표시 되는 방식을 결정 합니다.

상태 표시줄에 사용할 수 있는 스타일 목록은 [Create](#create)를 참조 하세요.

## <a name="cstatusbargetpanetext"></a><a name="getpanetext"></a> CStatusBar:: GetPaneText

상태 표시줄 창에 표시 되는 텍스트를 검색 하려면이 멤버 함수를 호출 합니다.

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
텍스트를 검색할 창의 인덱스입니다.

*rString*<br/>
검색할 텍스트를 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

`CString`창의 텍스트를 포함 하는 개체입니다.

### <a name="remarks"></a>설명

이 멤버 함수의 두 번째 형태는 개체를 `CString` 문자열 텍스트로 채웁니다.

## <a name="cstatusbargetstatusbarctrl"></a><a name="getstatusbarctrl"></a> CStatusBar:: GetStatusBarCtrl

이 멤버 함수를 사용 하면 기본 공용 컨트롤에 직접 액세스할 수 있습니다.

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>반환 값

[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) 개체에 대 한 참조를 포함 합니다.

### <a name="remarks"></a>설명

`GetStatusBarCtrl`를 사용 하 여 Windows 상태 표시줄 공용 컨트롤의 기능을 활용 하 고, [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) 에서 제공 하는 지원 기능을 활용 하 여 상태 표시줄의 사용자 지정을 지원 합니다. 예를 들어 공용 컨트롤을 사용 하 여 상태 표시줄에 크기 조정 그립을 포함 하는 스타일을 지정 하거나, 부모 창의 클라이언트 영역 맨 위에 상태 표시줄을 표시 하도록 스타일을 지정할 수 있습니다.

공용 컨트롤에 대 한 일반적인 정보는 Windows SDK의 [공용 컨트롤](/windows/win32/Controls/common-controls-intro) 을 참조 하세요.

## <a name="cstatusbarsetindicators"></a><a name="setindicators"></a> CStatusBar:: SetIndicators

각 표시기의 ID를 *Lpidarray* 배열의 해당 요소로 지정 된 값으로 설정 하 고, 각 id로 지정 된 문자열 리소스를 로드 하 고, 표시기의 텍스트를 문자열로 설정 합니다.

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>매개 변수

*lpIDArray*<br/>
Id 배열에 대 한 포인터입니다.

*nIDCount*<br/>
*Lpidarray* 가 가리키는 배열의 요소 수입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="cstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a> CStatusBar:: SetPaneInfo

지정 된 표시기 창을 새 ID, 스타일 및 너비로 설정 합니다.

```cpp
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
스타일을 설정할 표시기 창의 인덱스입니다.

*nID*<br/>
표시기 창의 새 ID입니다.

*nStyle*<br/>
표시기 창의 새 스타일입니다.

*cxWidth*<br/>
표시기 창의 새 너비입니다.

### <a name="remarks"></a>설명

지원 되는 지표 스타일은 다음과 같습니다.

- 창 주위에 3 차원 테두리를 SBPS_NOBORDERS 합니다.

- 텍스트를 "팝 아웃" 하도록 반전 테두리를 SBPS_POPOUT 합니다.

- 텍스트를 그리지 SBPS_DISABLED 합니다.

- 사용 하지 않은 공간을 채우도록 스트레치 창을 SBPS_STRETCH 합니다. 상태 표시줄 마다 창 하나만이 스타일을 사용할 수 있습니다.

- 스트레치, 테두리 또는 팝아웃를 SBPS_NORMAL 합니다.

## <a name="cstatusbarsetpanestyle"></a><a name="setpanestyle"></a> CStatusBar:: SetPaneStyle

상태 표시줄 창의 스타일을 설정 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
스타일을 설정할 창의 인덱스입니다.

*nStyle*<br/>
스타일을 설정할 창의 스타일입니다.

### <a name="remarks"></a>설명

창의 스타일은 창이 표시 되는 방식을 결정 합니다.

상태 표시줄에 사용할 수 있는 스타일 목록은 [SetPaneInfo](#setpaneinfo)를 참조 하세요.

## <a name="cstatusbarsetpanetext"></a><a name="setpanetext"></a> CStatusBar:: SetPaneText

이 멤버 함수를 호출 하 여 *lpszNewText* 가 가리키는 문자열로 창 텍스트를 설정 합니다.

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
텍스트를 설정할 창의 인덱스입니다.

*lpszNewText*<br/>
새 창 텍스트에 대 한 포인터입니다.

*bUpdate*<br/>
TRUE 이면 텍스트가 설정 된 후 창이 무효화 됩니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

를 호출한 후에는 `SetPaneText` UI 업데이트 처리기를 추가 하 여 상태 표시줄에 새 텍스트를 표시 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC Sample DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 클래스](../../mfc/reference/ccontrolbar-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl 클래스](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar 클래스](../../mfc/reference/ccontrolbar-class.md)
