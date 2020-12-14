---
description: '자세히 알아보기: CToolBar 클래스'
title: CToolBar 클래스
ms.date: 11/04/2016
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
ms.openlocfilehash: a4b100af3bcd4aac57cee19bbba9aaded3248188
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345045"
---
# <a name="ctoolbar-class"></a>CToolBar 클래스

비트맵 단추의 행과 구분 기호(선택 사항)가 있는 컨트롤 막대입니다.

## <a name="syntax"></a>구문

```
class CToolBar : public CControlBar
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CToolBar:: CToolBar](#ctoolbar)|`CToolBar` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CToolBar:: CommandToIndex](#commandtoindex)|지정 된 명령 ID를 가진 단추의 인덱스를 반환 합니다.|
|[CToolBar:: Create](#create)|Windows 도구 모음을 만들고 개체에 연결 `CToolBar` 합니다.|
|[CToolBar:: CreateEx](#createex)|포함 된 `CToolBar` 개체에 대 한 추가 스타일을 사용 하 여 개체를 만듭니다 `CToolBarCtrl` .|
|[CToolBar:: GetButtonInfo](#getbuttoninfo)|단추의 ID, 스타일 및 이미지 번호를 검색 합니다.|
|[CToolBar:: GetButtonStyle](#getbuttonstyle)|단추의 스타일을 검색 합니다.|
|[CToolBar:: GetButtonText](#getbuttontext)|단추에 표시 되는 텍스트를 검색 합니다.|
|[CToolBar:: GetItemID](#getitemid)|지정 된 인덱스의 단추 또는 구분 기호에 대 한 명령 ID를 반환 합니다.|
|[CToolBar:: GetItemRect](#getitemrect)|지정 된 인덱스에 있는 항목의 표시 사각형을 검색 합니다.|
|[CToolBar:: GetToolBarCtrl](#gettoolbarctrl)|기본 공용 컨트롤에 직접 액세스할 수 있습니다.|
|[CToolBar:: LoadBitmap](#loadbitmap)|비트맵 단추 이미지를 포함 하는 비트맵을 로드 합니다.|
|[CToolBar:: LoadToolBar](#loadtoolbar)|리소스 편집기를 사용 하 여 만든 도구 모음 리소스를 로드 합니다.|
|[CToolBar:: SetBitmap](#setbitmap)|비트맵 이미지를 설정 합니다.|
|[CToolBar:: SetButtonInfo](#setbuttoninfo)|단추의 ID, 스타일 및 이미지 번호를 설정 합니다.|
|[CToolBar:: SetButtons](#setbuttons)|비트맵 내에서 단추 스타일과 단추 이미지의 인덱스를 설정 합니다.|
|[CToolBar:: SetButtonStyle](#setbuttonstyle)|단추에 대 한 스타일을 설정 합니다.|
|[CToolBar:: SetButtonText](#setbuttontext)|단추에 표시 되는 텍스트를 설정 합니다.|
|[CToolBar:: SetHeight](#setheight)|도구 모음의 높이를 설정 합니다.|
|[CToolBar:: SetSizes](#setsizes)|단추 크기와 비트맵 크기를 설정 합니다.|

## <a name="remarks"></a>설명

단추는 누름 단추, 확인란 단추 또는 라디오 단추와 같은 역할을 할 수 있습니다. `CToolBar` 개체는 일반적으로 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 또는 [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)클래스에서 파생 된 프레임 창 개체의 포함 된 멤버입니다.

MFC 4.0에 새로 추가 된 멤버 함수인 [CToolBar:: GetToolBarCtrl](#gettoolbarctrl)를 사용 하 여 도구 모음 사용자 지정 및 추가 기능에 대 한 Windows 공용 컨트롤의 지원을 활용할 수 있습니다. `CToolBar` 멤버 함수는 Windows 공용 컨트롤의 기능을 대부분 제공 합니다. 그러나를 호출 하면 `GetToolBarCtrl` 도구 모음에 Windows 95/98 도구 모음의 특성을 더 많이 제공할 수 있습니다. 를 호출 하는 경우 `GetToolBarCtrl` 개체에 대 한 참조를 반환 `CToolBarCtrl` 합니다. Windows 공용 컨트롤을 사용 하 여 도구 모음 디자인에 대 한 자세한 내용은 [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) 를 참조 하세요. 공용 컨트롤에 대 한 일반적인 정보는 Windows SDK의 [공용 컨트롤](/windows/win32/Controls/common-controls-intro) 을 참조 하세요.

Visual C++ 도구 모음을 만드는 두 가지 방법을 제공 합니다. 리소스 편집기를 사용 하 여 도구 모음 리소스를 만들려면 다음 단계를 수행 합니다.

1. 도구 모음 리소스를 만듭니다.

1. `CToolBar` 개체를 생성합니다.

1. [Create](#create) (또는 [createex](#createex)) 함수를 호출 하 여 Windows 도구 모음을 만들고 개체에 연결 `CToolBar` 합니다.

1. [Loadtoolbar](#loadtoolbar) 를 호출 하 여 도구 모음 리소스를 로드 합니다.

액세스 권한이 없는 경우 다음 단계를 수행하세요.

1. `CToolBar` 개체를 생성합니다.

1. [Create](#create) (또는 [createex](#createex)) 함수를 호출 하 여 Windows 도구 모음을 만들고 개체에 연결 `CToolBar` 합니다.

1. [Loadbitmap](#loadbitmap) 을 호출 하 여 도구 모음 단추 이미지를 포함 하는 비트맵을 로드 합니다.

1. [Setbuttons](#setbuttons) 를 호출 하 여 단추 스타일을 설정 하 고 각 단추를 비트맵의 이미지와 연결 합니다.

도구 모음의 모든 단추 이미지는 각 단추에 대해 하나의 이미지를 포함 해야 하는 하나의 비트맵에서 가져옵니다. 모든 이미지는 크기가 같아야 합니다. 기본값은 16 픽셀이 고 높이는 15 픽셀입니다. 이미지는 비트맵에서 나란히 있어야 합니다.

`SetButtons`함수는 컨트롤 id 배열에 대 한 포인터와 배열의 요소 수를 지정 하는 정수를 사용 합니다. 함수는 각 단추의 ID를 배열의 해당 요소에 대 한 값으로 설정 하 고 각 단추에 이미지 인덱스를 할당 합니다 .이 인덱스는 비트맵에서 단추의 이미지 위치를 지정 합니다. 배열 요소의 값이 ID_SEPARATOR 이면 이미지 인덱스가 할당 되지 않습니다.

비트맵의 이미지 순서는 일반적으로 화면에 그려지는 순서 이지만, [Setbuttoninfo](#setbuttoninfo) 함수를 사용 하 여 이미지 순서와 그리기 순서 간의 관계를 변경할 수 있습니다.

도구 모음의 모든 단추 크기가 동일 합니다. 기본값은 *소프트웨어 디자인을 위한 Windows 인터페이스 지침* 에 따라 24 x 22 픽셀입니다. 이미지와 단추 차원 사이의 추가 공간은 이미지 주위에 테두리를 형성 하는 데 사용 됩니다.

각 단추에는 하나의 이미지가 있습니다. 다양 한 단추 상태 및 스타일 (누름, 위쪽, 아래쪽, 사용 안 함, 사용 안 함, 사용 안 함)이 해당 이미지에서 생성 됩니다. 비트맵이 임의의 색 일 수 있지만 이미지를 흑백으로 표시 하 고 회색 음영을 사용 하 여 최상의 결과를 달성할 수 있습니다.

> [!WARNING]
> `CToolBar` 최대 16 색의 비트맵을 지원 합니다. 이미지를 도구 모음 편집기에 로드 하면 Visual Studio에서 이미지를 자동으로 16 색 비트맵으로 변환 하 고 (필요한 경우) 이미지가 변환 되 면 경고 메시지를 표시 합니다. 16 개 이상의 색이 있는 이미지를 사용 하는 경우 (외부 편집기를 사용 하 여 이미지 편집) 응용 프로그램이 예기치 않게 동작할 수 있습니다.

도구 모음 단추는 기본적으로 누름 단추를 모방 합니다. 그러나 도구 모음 단추는 확인란 단추나 라디오 단추를 모방 하는 경우도 있습니다. 확인란 단추에는 세 가지 상태 즉, 선택 됨, 선택 취소 됨 및 결정 안 함이 있습니다. 라디오 단추에는 두 가지 상태만 있습니다. 선택 및 선택 취소 합니다.

배열을 가리키지 않고 개별 단추나 구분 기호 스타일을 설정 하려면 [Getbuttonstyle](#getbuttonstyle) 을 호출 하 여 스타일을 검색 한 다음 대신 [setbuttonstyle](#setbuttonstyle) 을 호출 `SetButtons` 합니다. `SetButtonStyle` 는 런타임에 단추의 스타일을 변경 하려는 경우에 가장 유용 합니다.

단추에 표시할 텍스트를 할당 하려면 [Getbuttontext](#getbuttontext) 를 호출 하 여 단추에 표시할 텍스트를 검색 한 다음 [setbuttontext](#setbuttontext) 를 호출 하 여 텍스트를 설정 합니다.

확인란 단추를 만들려면 스타일 TBBS_CHECKBOX 할당 하거나 `CCmdUI` `SetCheck` ON_UPDATE_COMMAND_UI 처리기에서 개체의 멤버 함수를 사용 합니다. `SetCheck`를 호출 하면 누름 단추가 확인란 단추로 전환 됩니다. 확인 되지 않은 경우 0의 인수를 전달 하 고 확인 된 경우 1을 전달 `SetCheck` 하거나 결정 되지 않은 경우 2를 전달 합니다.

라디오 단추를 만들려면 ON_UPDATE_COMMAND_UI 처리기에서 [CCmdUI](../../mfc/reference/ccmdui-class.md) 개체의 [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) 멤버 함수를 호출 합니다. `SetRadio`확인 되지 않았거나 0이 아닌 값의 인수를 전달 합니다. 라디오 그룹의 상호 배타적인 동작을 제공 하려면 그룹의 모든 단추에 대 한 ON_UPDATE_COMMAND_UI 처리기가 있어야 합니다.

사용에 대 한 자세한 내용은 `CToolBar` [MFC 도구 모음 구현](../../mfc/mfc-toolbar-implementation.md) 및 [기술 참고 31: 컨트롤 막대](../../mfc/tn031-control-bars.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>요구 사항

**헤더:** afxext.h

## <a name="ctoolbarcommandtoindex"></a><a name="commandtoindex"></a> CToolBar:: CommandToIndex

이 멤버 함수는 위치 0에서 시작 하 여 명령 ID가 일치 하는 첫 번째 도구 모음 단추의 인덱스를 반환 `nIDFind` 합니다.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>매개 변수

*nIDFind*<br/>
도구 모음 단추의 명령 ID입니다.

### <a name="return-value"></a>반환 값

단추의 인덱스 이거나, 지정 된 명령 ID를 가진 단추가 없는 경우-1입니다.

## <a name="ctoolbarcreate"></a><a name="create"></a> CToolBar:: Create

이 멤버 함수는 Windows 도구 모음 (자식 창)을 만들고이를 개체에 연결 `CToolBar` 합니다.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
도구 모음의 부모 창에 대 한 포인터입니다.

*dwStyle*<br/>
도구 모음 스타일입니다. 지원 되는 추가 도구 모음 스타일은 다음과 같습니다.

- CBRS_TOP 컨트롤 막대는 프레임 창의 맨 위에 있습니다.

- CBRS_BOTTOM 컨트롤 막대는 프레임 창의 맨 아래에 있습니다.

- CBRS_NOALIGN 컨트롤 막대는 부모 크기를 조정할 때 위치가 변경 되지 않습니다.

- CBRS_TOOLTIPS 컨트롤 막대는 도구 설명을 표시 합니다.

- CBRS_SIZE_DYNAMIC 컨트롤 막대는 동적입니다.

- CBRS_SIZE_FIXED 컨트롤 표시줄이 고정 되어 있습니다.

- CBRS_FLOATING 컨트롤 막대의 부동 소수점입니다.

- 상태 표시줄 CBRS_FLYBY 단추에 대 한 정보를 표시 합니다.

- CBRS_HIDE_INPLACE 컨트롤 막대는 사용자에 게 표시 되지 않습니다.

*nID*<br/>
도구 모음의 자식 창 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

또한 도구 모음 높이를 기본값으로 설정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

## <a name="ctoolbarcreateex"></a><a name="createex"></a> CToolBar:: CreateEx

이 함수를 호출 하 여 Windows 도구 모음 (자식 창)을 만들고이를 개체에 연결 `CToolBar` 합니다.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,
    CRect rcBorders = CRect(
    0,
    0,
    0,
    0),
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>매개 변수

*pParentWnd*<br/>
도구 모음의 부모 창에 대 한 포인터입니다.

*dwCtrlStyle*<br/>
포함 된 [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) 개체 만들기에 대 한 추가 스타일입니다. 기본적으로이 값은 TBSTYLE_FLAT로 설정 됩니다. 도구 모음 스타일의 전체 목록은 *Dwstyle* 을 참조 하세요.

*dwStyle*<br/>
도구 모음 스타일입니다. 적절 한 스타일 목록은 Windows SDK의 [Toolbar 컨트롤 및 단추 스타일](/windows/win32/Controls/toolbar-control-and-button-styles) 을 참조 하세요.

*rcBorders*<br/>
도구 모음 창 테두리의 너비를 정의 하는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체입니다. 이러한 테두리는 기본적으로 0, 0, 0, 0으로 설정 되므로 테두리가 없는 도구 모음 창이 생성 됩니다.

*nID*<br/>
도구 모음의 자식 창 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

또한 도구 모음 높이를 기본값으로 설정 합니다.

`CreateEx`포함 된 도구 모음 컨트롤을 만드는 동안 특정 스타일을 제공 해야 하는 경우 [Create](#create)대신를 사용 합니다. 예를 들어 *dwCtrlStyle* 를 TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT으로 설정 하 여 Internet Explorer 4 도구 모음과 유사한 도구 모음을 만들 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

## <a name="ctoolbarctoolbar"></a><a name="ctoolbar"></a> CToolBar:: CToolBar

이 멤버 함수는 개체를 생성 `CToolBar` 하 고 기본 크기를 설정 합니다.

```
CToolBar();
```

### <a name="remarks"></a>설명

[Create](#create) member 함수를 호출 하 여 도구 모음 창을 만듭니다.

## <a name="ctoolbargetbuttoninfo"></a><a name="getbuttoninfo"></a> CToolBar:: GetButtonInfo

이 멤버 함수는 *Nindex* 로 지정 된 위치에서 도구 모음 단추 또는 구분 기호에 대 한 컨트롤 ID, 스타일 및 이미지 인덱스를 검색 합니다.

```cpp
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
검색할 정보를 포함 하는 도구 모음 단추 또는 구분 기호의 인덱스입니다.

*nID*<br/>
단추의 명령 ID로 설정 된 UINT에 대 한 참조입니다.

*nStyle*<br/>
단추의 스타일로 설정 된 UINT에 대 한 참조입니다.

*iImage*<br/>
비트맵 내에서 단추 이미지의 인덱스로 설정 된 정수에 대 한 참조입니다.

### <a name="remarks"></a>설명

이러한 값은 *nID*, *Nstyle* 및 *iimage* 에서 참조 하는 변수에 할당 됩니다. 이미지 인덱스는 비트맵 내에서 모든 도구 모음 단추에 대 한 이미지를 포함 하는 이미지의 위치입니다. 첫 번째 이미지는 위치 0에 있습니다.

*Nindex* 가 구분 기호를 지정 하는 경우 *iimage* 는 픽셀 단위의 구분 기호 너비로 설정 됩니다.

## <a name="ctoolbargetbuttonstyle"></a><a name="getbuttonstyle"></a> CToolBar:: GetButtonStyle

이 멤버 함수를 호출 하 여 도구 모음에서 단추나 구분선의 스타일을 검색 합니다.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
검색할 도구 모음 단추 또는 구분 기호 스타일의 인덱스입니다.

### <a name="return-value"></a>반환 값

*Nindex* 로 지정 된 단추나 구분 기호의 스타일입니다.

### <a name="remarks"></a>설명

단추의 스타일은 단추가 표시 되는 방법과 사용자 입력에 응답 하는 방법을 결정 합니다. 단추 스타일의 예제는 [Setbuttonstyle](#setbuttonstyle) 을 참조 하세요.

## <a name="ctoolbargetbuttontext"></a><a name="getbuttontext"></a> CToolBar:: GetButtonText

단추에 표시 되는 텍스트를 검색 하려면이 멤버 함수를 호출 합니다.

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
검색할 텍스트의 인덱스입니다.

*rString*<br/>
검색할 텍스트를 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

`CString`단추 텍스트를 포함 하는 개체입니다.

### <a name="remarks"></a>설명

이 멤버 함수의 두 번째 형태는 개체를 `CString` 문자열 텍스트로 채웁니다.

## <a name="ctoolbargetitemid"></a><a name="getitemid"></a> CToolBar:: GetItemID

이 멤버 함수는 *Nindex* 로 지정 된 단추나 구분 기호의 명령 ID를 반환 합니다.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
ID를 검색할 항목의 인덱스입니다.

### <a name="return-value"></a>반환 값

*Nindex* 로 지정 된 단추나 구분 기호의 명령 ID입니다.

### <a name="remarks"></a>설명

구분 기호는 ID_SEPARATOR 반환 합니다.

## <a name="ctoolbargetitemrect"></a><a name="getitemrect"></a> CToolBar:: GetItemRect

이 멤버 함수는 `RECT` *lpRect* 에 포함 된 주소가 *n 인덱스* 에 의해 지정 된 단추 또는 구분 기호와 함께 포함 된 구조를 채웁니다.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
사각형 좌표를 검색할 항목 (단추 또는 구분 기호)의 인덱스입니다.

*lpRect*<br/>
항목의 좌표를 포함 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조의 주소입니다.

### <a name="remarks"></a>설명

좌표는 도구 모음의 왼쪽 위 모퉁이를 기준으로 하는 픽셀 단위입니다.

을 사용 `GetItemRect` 하 여 콤보 상자 또는 기타 컨트롤로 바꾸려는 구분 기호의 좌표를 가져옵니다.

### <a name="example"></a>예제

  [CToolBar:: SetSizes](#setsizes)의 예제를 참조 하세요.

## <a name="ctoolbargettoolbarctrl"></a><a name="gettoolbarctrl"></a> CToolBar:: GetToolBarCtrl

이 멤버 함수를 사용 하면 기본 공용 컨트롤에 직접 액세스할 수 있습니다.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>반환 값

`CToolBarCtrl` 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

`GetToolBarCtrl`를 사용 하 여 Windows 도구 모음 공용 컨트롤의 기능을 활용 하 고 도구 모음 사용자 지정을 위한 지원 [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) 을 활용할 수 있습니다.

공용 컨트롤을 사용 하는 방법에 대 한 자세한 내용은 Windows SDK의 [컨트롤](../../mfc/controls-mfc.md) 및 [공용 컨트롤](/windows/win32/Controls/common-controls-intro) 문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

## <a name="ctoolbarloadbitmap"></a><a name="loadbitmap"></a> CToolBar:: LoadBitmap

이 멤버 함수를 호출 하 여 또는로 지정 된 비트맵을 로드 합니다 `lpszResourceName` `nIDResource` .

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>매개 변수

*lpszResourceName*<br/>
로드할 비트맵의 리소스 이름에 대 한 포인터입니다.

*nIDResource*<br/>
로드할 비트맵의 리소스 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

비트맵에는 각 도구 모음 단추에 대 한 이미지가 하나씩 있어야 합니다. 이미지가 표준 크기 (16 픽셀 너비와 15 픽셀 높음)가 아닌 경우 [setsizes](#setsizes) 를 호출 하 여 단추 크기와 해당 이미지를 설정 합니다.

> [!WARNING]
> `CToolBar` 최대 16 색의 비트맵을 지원 합니다. 이미지를 도구 모음 편집기에 로드 하면 Visual Studio에서 이미지를 자동으로 16 색 비트맵으로 변환 하 고 (필요한 경우) 이미지가 변환 되 면 경고 메시지를 표시 합니다. 16 개 이상의 색이 있는 이미지를 사용 하는 경우 (외부 편집기를 사용 하 여 이미지 편집) 응용 프로그램이 예기치 않게 동작할 수 있습니다.

## <a name="ctoolbarloadtoolbar"></a><a name="loadtoolbar"></a> CToolBar:: LoadToolBar

*LpszResourceName* 또는 *nIDResource* 에 지정 된 도구 모음을 로드 하려면이 멤버 함수를 호출 합니다.

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>매개 변수

*lpszResourceName*<br/>
로드할 도구 모음의 리소스 이름에 대 한 포인터입니다.

*nIDResource*<br/>
로드할 도구 모음의 리소스 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

도구 모음 리소스를 만드는 방법에 대 한 자세한 내용은의 [도구 모음 편집기](../../windows/toolbar-editor.md) 를 참조 하십시오.

### <a name="example"></a>예제

  [CToolBar:: CreateEx](#createex)의 예제를 참조 하세요.

## <a name="ctoolbarsetbitmap"></a><a name="setbitmap"></a> CToolBar:: SetBitmap

이 멤버 함수를 호출 하 여 도구 모음에 대 한 비트맵 이미지를 설정 합니다.

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>매개 변수

*hbmImageWell*<br/>
도구 모음과 연결 된 비트맵 이미지의 핸들입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

예를 들어를 호출 `SetBitmap` 하 여 사용자가 단추 작업을 변경 하는 문서에 대 한 작업을 수행한 후 비트맵 이미지를 변경 합니다.

## <a name="ctoolbarsetbuttoninfo"></a><a name="setbuttoninfo"></a> CToolBar:: SetButtonInfo

단추의 명령 ID, 스타일 및 이미지 번호를 설정 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
정보를 설정할 단추나 구분 기호의 0부터 시작 하는 인덱스입니다.

*nID*<br/>
단추의 명령 ID가 설정 된 값입니다.

*nStyle*<br/>
새 단추 스타일입니다. 지원 되는 단추 스타일은 다음과 같습니다.

- TBBS_BUTTON 표준 누름 단추 (기본값)

- TBBS_SEPARATOR 구분 기호

- TBBS_CHECKBOX 자동 확인란 단추

- TBBS_GROUP 그룹의 시작을 표시 합니다.

- TBBS_CHECKGROUP 확인란 단추 그룹의 시작을 표시 합니다.

- TBBS_DROPDOWN 드롭다운 목록 단추를 만듭니다.

- 단추 너비는 이미지 크기가 아니라 단추의 텍스트를 기준으로 계산 됩니다 TBBS_AUTOSIZE.

- TBBS_NOPREFIX 단추 텍스트에는 연결 된 액셀러레이터 접두사가 없습니다.

*iImage*<br/>
비트맵 내에서 단추의 이미지에 대 한 새 인덱스입니다.

### <a name="remarks"></a>설명

스타일 TBBS_SEPARATOR 있는 구분 기호의 경우이 함수는 구분 기호의 너비 (픽셀)를 *Iimage* 에 저장 된 값으로 설정 합니다.

> [!NOTE]
> *Nstyle* 매개 변수를 사용 하 여 단추 상태를 설정할 수도 있습니다. 그러나 단추 상태는 [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) 처리기에 의해 제어 되므로를 사용 하 여 설정한 모든 상태는 `SetButtonInfo` 다음 유휴 처리 중에 손실 됩니다. 자세한 내용은 [User-Interface 개체를 업데이트 하는 방법](../../mfc/how-to-update-user-interface-objects.md) 및 [TN031: 컨트롤 막대](../../mfc/tn031-control-bars.md) 를 참조 하세요.

비트맵 이미지 및 단추에 대 한 자세한 내용은 [CToolBar](../../mfc/reference/ctoolbar-class.md) Overview 및 [CToolBar:: loadbitmap](#loadbitmap)을 참조 하세요.

## <a name="ctoolbarsetbuttons"></a><a name="setbuttons"></a> CToolBar:: SetButtons

이 멤버 함수는 각 도구 모음 단추의 명령 ID를 *Lpidarray* 배열의 해당 요소로 지정 된 값으로 설정 합니다.

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>매개 변수

*lpIDArray*<br/>
명령 Id 배열에 대 한 포인터입니다. 빈 단추를 할당 하려면 NULL 일 수 있습니다.

*nIDCount*<br/>
*Lpidarray* 가 가리키는 배열의 요소 수입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

배열의 요소에 ID_SEPARATOR 값이 있는 경우 도구 모음의 해당 위치에 구분 기호가 만들어집니다. 또한이 함수는 각 단추의 스타일을 TBBS_BUTTON 및 각 구분 기호의 스타일을 TBBS_SEPARATOR 설정 하 고 각 단추에 이미지 인덱스를 할당 합니다. 이미지 인덱스는 비트맵 내에서 단추의 이미지 위치를 지정 합니다.

이 함수는 구분 기호에 대 한 이미지 인덱스를 할당 하지 않으므로 비트맵에서 구분 기호를 고려 하지 않아도 됩니다. 도구 모음에 0, 1, 3 위치에 있는 단추가 있고 위치 2에 구분 기호가 있는 경우 비트맵의 위치 0, 1, 2에 있는 이미지는 각각 0, 1, 3 위치의 단추에 할당 됩니다.

*Lpidarray* 가 NULL 인 경우이 함수는 *nIDCount* 로 지정 된 항목 수에 대 한 공간을 할당 합니다. [Setbuttoninfo](#setbuttoninfo) 를 사용 하 여 각 항목의 특성을 설정 합니다.

## <a name="ctoolbarsetbuttonstyle"></a><a name="setbuttonstyle"></a> CToolBar:: SetButtonStyle

이 멤버 함수를 호출 하 여 단추나 구분 기호의 스타일을 설정 하거나 그룹 단추를 클릭 합니다.

```cpp
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
정보를 설정할 단추나 구분 기호의 인덱스입니다.

*nStyle*<br/>
단추 스타일입니다. 지원 되는 단추 스타일은 다음과 같습니다.

- TBBS_BUTTON 표준 누름 단추 (기본값)

- TBBS_SEPARATOR 구분 기호

- TBBS_CHECKBOX 자동 확인란 단추

- TBBS_GROUP 그룹의 시작을 표시 합니다.

- TBBS_CHECKGROUP 확인란 단추 그룹의 시작을 표시 합니다.

- 드롭다운 목록 단추를 만드는 TBBS_DROPDOWN

- 단추 너비는 이미지 크기가 아니라 단추의 텍스트를 기준으로 계산 됩니다 TBBS_AUTOSIZE

- TBBS_NOPREFIX 단추 텍스트에는 연결 된 액셀러레이터 접두사가 없습니다.

### <a name="remarks"></a>설명

단추의 스타일은 단추가 표시 되는 방법과 사용자 입력에 응답 하는 방법을 결정 합니다.

를 호출 하기 전에 `SetButtonStyle` [getbuttonstyle](#getbuttonstyle) 멤버 함수를 호출 하 여 단추나 구분 기호 스타일을 검색 합니다.

> [!NOTE]
> *Nstyle* 매개 변수를 사용 하 여 단추 상태를 설정할 수도 있습니다. 그러나 단추 상태는 [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) 처리기에 의해 제어 되므로를 사용 하 여 설정한 모든 상태는 `SetButtonStyle` 다음 유휴 처리 중에 손실 됩니다. 자세한 내용은 [User-Interface 개체를 업데이트 하는 방법](../../mfc/how-to-update-user-interface-objects.md) 및 [TN031: 컨트롤 막대](../../mfc/tn031-control-bars.md) 를 참조 하세요.

## <a name="ctoolbarsetbuttontext"></a><a name="setbuttontext"></a> CToolBar:: SetButtonText

단추에 텍스트를 설정 하려면이 함수를 호출 합니다.

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
텍스트를 설정할 단추의 인덱스입니다.

*lpszText*<br/>
단추에 설정할 텍스트를 가리킵니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

  [CToolBar:: GetToolBarCtrl](#gettoolbarctrl)의 예제를 참조 하세요.

## <a name="ctoolbarsetheight"></a><a name="setheight"></a> CToolBar:: SetHeight

이 멤버 함수는 도구 모음의 높이를 *cyHeight* 에 지정 된 값 (픽셀)으로 설정 합니다.

```cpp
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>매개 변수

*cyHeight*<br/>
도구 모음의 높이 (픽셀)입니다.

### <a name="remarks"></a>설명

[Setsizes](#setsizes)를 호출한 후이 멤버 함수를 사용 하 여 표준 도구 모음 높이를 재정의 합니다. 높이가 너무 작으면 단추가 아래쪽에 잘립니다.

이 함수가 호출 되지 않은 경우 프레임 워크는 단추의 크기를 사용 하 여 도구 모음 높이를 결정 합니다.

## <a name="ctoolbarsetsizes"></a><a name="setsizes"></a> CToolBar:: SetSizes

이 멤버 함수를 호출 하 여 도구 모음의 단추를 *Sizebutton* 에 지정 된 크기 (픽셀)로 설정 합니다.

```cpp
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>매개 변수

*sizeButton*<br/>
각 단추의 크기 (픽셀)입니다.

*sizeImage*<br/>
각 이미지의 크기 (픽셀)입니다.

### <a name="remarks"></a>설명

*Sizeimage* 매개 변수는 도구 모음의 비트맵에 있는 이미지의 크기 (픽셀)를 포함 해야 합니다. *Sizebutton* 의 차원은 이미지를 5 픽셀 이상 너비의 너비와 6 픽셀의 높이로 추가 하는 데 충분 해야 합니다. 이 함수는 또한 도구 모음 높이를 단추에 맞게 설정 합니다.

단추 및 이미지 크기에 대 한 소프트웨어 디자인 권장 사항 *에 대 한 Windows 인터페이스 지침* 을 따르지 않는 도구 모음에 대해서만이 멤버 함수를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC Sample DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 클래스](../../mfc/reference/ccontrolbar-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl 클래스](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar 클래스](../../mfc/reference/ccontrolbar-class.md)
