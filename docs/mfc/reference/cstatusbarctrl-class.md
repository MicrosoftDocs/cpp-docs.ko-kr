---
description: '자세히 알아보기: CStatusBarCtrl 클래스'
title: CStatusBarCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
ms.openlocfilehash: 424edbd2d78fc82c7c78315dea1d430c6ea9459d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342636"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl 클래스

Windows의 공용 상태 표시줄 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CStatusBarCtrl:: CStatusBarCtrl](#cstatusbarctrl)|`CStatusBarCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CStatusBarCtrl:: Create](#create)|상태 표시줄 컨트롤을 만들고이를 개체에 연결 `CStatusBarCtrl` 합니다.|
|[CStatusBarCtrl:: CreateEx](#createex)|지정 된 Windows 확장 스타일을 사용 하 여 상태 표시줄 컨트롤을 만들고이를 `CStatusBarCtrl` 개체에 연결 합니다.|
|[CStatusBarCtrl::D rawItem](#drawitem)|소유자 그리기 상태 표시줄 컨트롤의 시각적 측면이 변경 될 때 호출 됩니다.|
|[CStatusBarCtrl:: GetBorders](#getborders)|상태 표시줄 컨트롤의 가로 및 세로 테두리의 현재 너비를 검색 합니다.|
|[CStatusBarCtrl:: GetIcon](#geticon)|현재 상태 표시줄 컨트롤에서 파트 (창이 라고도 함)의 아이콘을 검색 합니다.|
|[CStatusBarCtrl:: GetParts](#getparts)|상태 표시줄 컨트롤에서 파트의 수를 검색 합니다.|
|[CStatusBarCtrl:: GetRect](#getrect)|상태 표시줄 컨트롤에서 파트의 경계 사각형을 검색 합니다.|
|[CStatusBarCtrl:: GetText](#gettext)|상태 표시줄 컨트롤의 지정 된 부분에서 텍스트를 검색 합니다.|
|[CStatusBarCtrl:: GetTextLength](#gettextlength)|상태 표시줄 컨트롤의 지정 된 부분에서 텍스트의 길이 (문자)를 검색 합니다.|
|[CStatusBarCtrl:: GetTipText](#gettiptext)|상태 표시줄에 있는 창에 대 한 도구 설명 텍스트를 검색 합니다.|
|[CStatusBarCtrl:: IsSimple](#issimple)|상태 창 컨트롤이 단순 모드 인지 확인 합니다.|
|[CStatusBarCtrl:: SetBkColor](#setbkcolor)|상태 표시줄의 배경색을 설정 합니다.|
|[CStatusBarCtrl:: SetIcon](#seticon)|상태 표시줄의 창에 대 한 아이콘을 설정 합니다.|
|[CStatusBarCtrl:: SetMinHeight](#setminheight)|상태 표시줄 컨트롤의 그리기 영역에 대 한 최소 높이를 설정 합니다.|
|[CStatusBarCtrl:: SetParts](#setparts)|상태 표시줄 컨트롤의 파트 수와 각 파트의 오른쪽 가장자리 좌표를 설정 합니다.|
|[CStatusBarCtrl:: SetSimple](#setsimple)|상태 표시줄 컨트롤이 단순 텍스트를 표시 하거나에 대 한 이전 호출로 설정 된 모든 컨트롤 파트를 표시할지 여부를 지정 합니다 `SetParts` .|
|[CStatusBarCtrl:: SetText](#settext)|상태 표시줄 컨트롤의 특정 부분에서 텍스트를 설정합니다.|
|[CStatusBarCtrl:: SetTipText](#settiptext)|상태 표시줄에 창에 대 한 도구 설명 텍스트를 설정 합니다.|

## <a name="remarks"></a>설명

"상태 표시줄 컨트롤"은 일반적으로 부모 창 맨 아래에 표시 되는 가로 창으로, 응용 프로그램에서 다양 한 종류의 상태 정보를 표시할 수 있습니다. 상태 표시줄 컨트롤을 여러 부분으로 나누어 여러 유형의 정보를 표시할 수 있습니다.

이 컨트롤 (및 `CStatusBarCtrl` 클래스)은 windows 95/98 및 WINDOWS NT 버전 3.51 이상에서 실행 되는 프로그램에만 사용할 수 있습니다.

사용에 대 한 자세한 내용은 `CStatusBarCtrl` [컨트롤](../../mfc/controls-mfc.md) 및 [CStatusBarCtrl 사용](../../mfc/using-cstatusbarctrl.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="cstatusbarctrlcreate"></a><a name="create"></a> CStatusBarCtrl:: Create

상태 표시줄 컨트롤을 만들고이를 개체에 연결 `CStatusBarCtrl` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
상태 표시줄 컨트롤의 스타일을 지정 합니다. Windows SDK의 [공용 컨트롤 스타일](/windows/win32/Controls/common-control-styles) 에 나열 된 상태 표시줄 컨트롤 스타일의 조합을 적용 합니다. 이 매개 변수는 WS_CHILD 스타일을 포함 해야 합니다. 또한 WS_VISIBLE 스타일을 포함 해야 합니다.

*rect*<br/>
상태 표시줄 컨트롤의 크기와 위치를 지정 합니다. 이는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 일 수 있습니다.

*pParentWnd*<br/>
상태 표시줄 컨트롤의 부모 창 (일반적으로)을 지정 합니다 `CDialog` . NULL이 아니어야 합니다.

*nID*<br/>
상태 표시줄 컨트롤의 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CStatusBarCtrl`두 단계로을 생성 합니다. 먼저 생성자를 호출한 다음 `Create` 상태 표시줄 컨트롤을 만들고 개체에 연결 하는를 호출 합니다 `CStatusBarCtrl` .

상태 창의 기본 위치는 부모 창의 아래쪽에 있지만 부모 창의 클라이언트 영역 맨 위에 표시 되도록 CCS_TOP 스타일을 지정할 수 있습니다. 상태 창의 오른쪽 끝에 크기 조정 그립을 포함 하도록 SBARS_SIZEGRIP 스타일을 지정할 수 있습니다. 시스템이 상태 창에 그려지는 경우에도 결과 크기 조정 그립은 작동 하지 않으므로 CCS_TOP 및 SBARS_SIZEGRIP 스타일을 결합 하지 않는 것이 좋습니다.

확장 창 스타일을 사용 하 여 상태 표시줄을 만들려면 대신 [CStatusBarCtrl:: CreateEx](#createex) 를 호출 `Create` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

## <a name="cstatusbarctrlcreateex"></a><a name="createex"></a> CStatusBarCtrl:: CreateEx

컨트롤 (자식 창)을 만들고이를 개체에 연결 `CStatusBarCtrl` 합니다.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwExStyle*<br/>
만들려는 컨트롤의 확장 스타일을 지정 합니다. 확장 된 Windows 스타일의 목록에 대해서는 Windows SDK의 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 에 대 한 *dwexstyle* 매개 변수를 참조 하세요.

*dwStyle*<br/>
상태 표시줄 컨트롤의 스타일을 지정 합니다. Windows SDK의 [공용 컨트롤 스타일](/windows/win32/Controls/common-control-styles) 에 나열 된 상태 표시줄 컨트롤 스타일의 조합을 적용 합니다. 이 매개 변수는 WS_CHILD 스타일을 포함 해야 합니다. 또한 WS_VISIBLE 스타일을 포함 해야 합니다.

*rect*<br/>
*PParentWnd* 의 클라이언트 좌표에서 만들 창의 크기와 위치를 설명 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*pParentWnd*<br/>
컨트롤의 부모 창에 대 한 포인터입니다.

*nID*<br/>
컨트롤의 자식 창 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CreateEx` [Create](#create) 대신를 사용 하 여 **WS_EX_** windows 확장 스타일로 지정 된 확장 된 windows 스타일을 적용 합니다.

## <a name="cstatusbarctrlcstatusbarctrl"></a><a name="cstatusbarctrl"></a> CStatusBarCtrl:: CStatusBarCtrl

`CStatusBarCtrl` 개체를 생성합니다.

```
CStatusBarCtrl();
```

## <a name="cstatusbarctrldrawitem"></a><a name="drawitem"></a> CStatusBarCtrl::D rawItem

소유자 그리기 상태 표시줄 컨트롤의 시각적 측면이 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>매개 변수

*lpDrawItemStruct*<br/>
필요한 그리기 형식에 대 한 정보를 포함 하는 [Drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) 구조체에 대 한 긴 포인터입니다.

### <a name="remarks"></a>설명

`itemAction`구조체의 멤버는 `DRAWITEMSTRUCT` 수행할 그리기 작업을 정의 합니다.

기본적으로이 멤버 함수는 아무 작업도 수행 하지 않습니다. 소유자 그리기 개체에 대 한 그리기를 구현 하려면이 멤버 함수를 재정의 `CStatusBarCtrl` 합니다.

응용 프로그램은이 멤버 함수가 종료 되기 전에 *Lpdrawitemstruct* 에 제공 된 표시 컨텍스트에 대해 선택한 모든 GDI (그래픽 장치 인터페이스) 개체를 복원 해야 합니다.

## <a name="cstatusbarctrlgetborders"></a><a name="getborders"></a> CStatusBarCtrl:: GetBorders

상태 표시줄 컨트롤의 현재 너비와 가로 및 세로 테두리를 검색 하 고 사각형 사이의 공간을 검색 합니다.

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>매개 변수

*pBorders*<br/>
세 개의 요소가 있는 정수 배열의 주소입니다. 첫 번째 요소는 가로 테두리의 너비를 받고, 두 번째 요소는 세로 테두리의 너비를 받으며, 세 번째 요소는 사각형 사이의 테두리 너비를 수신 합니다.

*nHorz*<br/>
가로 테두리의 너비를 받는 정수에 대 한 참조입니다.

*디스크로 변환 (*<br/>
세로 테두리의 너비를 받는 정수에 대 한 참조입니다.

*n 간격*<br/>
사각형 사이의 테두리 너비를 받는 정수에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이러한 테두리는 컨트롤의 바깥쪽 가장자리와 텍스트를 포함 하는 컨트롤 내의 사각형 사이의 간격을 결정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

## <a name="cstatusbarctrlgeticon"></a><a name="geticon"></a> CStatusBarCtrl:: GetIcon

현재 상태 표시줄 컨트롤에서 파트 (창이 라고도 함)의 아이콘을 검색 합니다.

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>매개 변수

*iPart*\
진행 검색할 아이콘이 포함 된 파트의 인덱스 (0부터 시작)입니다. 이 매개 변수가-1 인 경우 상태 표시줄은 단순 모드 상태 표시줄 이라고 가정 합니다.

### <a name="return-value"></a>반환 값

메서드가 성공한 경우 아이콘에 대 한 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [SB_GETICON](/windows/win32/Controls/sb-geticon) 메시지를 보냅니다.

상태 표시줄 컨트롤은 파트 라고도 하는 텍스트 출력 창의 행으로 구성 됩니다. 상태 표시줄에 대 한 자세한 내용은 [MFC의 상태 표시줄 구현](../../mfc/status-bar-implementation-in-mfc.md) 및 [CStatusBarCtrl 개체의 모드 설정](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)을 참조 하세요.

### <a name="example"></a>예제

다음 코드 예제에서는 `m_statusBar` 현재 상태 표시줄 컨트롤에 액세스 하는 데 사용 되는 변수를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 현재 상태 표시줄 컨트롤의 두 창에 아이콘을 복사 합니다. 코드 예제의 이전 섹션에서는 세 개의 창이 있는 상태 표시줄 컨트롤을 만든 다음 첫 번째 창에 아이콘을 추가 했습니다. 이 예제에서는 첫 번째 창에서 아이콘을 검색 한 다음 두 번째 및 세 번째 창에 추가 합니다.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

## <a name="cstatusbarctrlgetparts"></a><a name="getparts"></a> CStatusBarCtrl:: GetParts

상태 표시줄 컨트롤에서 파트의 수를 검색 합니다.

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>매개 변수

*n 부분*<br/>
좌표를 검색할 파트의 수입니다. 이 매개 변수가 컨트롤의 파트 수보다 크면 메시지는 기존 파트의 좌표를 검색 합니다.

*pParts*<br/>
*Nparts* 에서 지정한 파트 수와 동일한 수의 요소를 포함 하는 정수 배열의 주소입니다. 배열의 각 요소는 해당 파트의 오른쪽 가장자리에 대 한 클라이언트 좌표를 수신 합니다. 요소가-1로 설정 된 경우 해당 파트에 대 한 오른쪽 가장자리의 위치는 상태 표시줄의 오른쪽 가장자리로 확장 됩니다.

### <a name="return-value"></a>반환 값

성공 하면 컨트롤의 부분 수이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 또한 지정 된 파트 수의 오른쪽 가장자리 좌표를 검색 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

## <a name="cstatusbarctrlgetrect"></a><a name="getrect"></a> CStatusBarCtrl:: GetRect

상태 표시줄 컨트롤에서 파트의 경계 사각형을 검색 합니다.

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>매개 변수

*nPane*<br/>
경계 사각형을 검색할 파트의 인덱스 (0부터 시작)입니다.

*lpRect*<br/>
경계 사각형을 받는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체의 주소입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

## <a name="cstatusbarctrlgettext"></a><a name="gettext"></a> CStatusBarCtrl:: GetText

상태 표시줄 컨트롤의 지정 된 부분에서 텍스트를 검색 합니다.

```
CString GetText(
    int nPane,
    int* pType = NULL) const;

int GetText(
    LPCTSTR lpszText,
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
텍스트를 받는 버퍼의 주소입니다. 이 매개 변수는 null로 끝나는 문자열입니다.

*nPane*<br/>
텍스트를 검색할 파트의 인덱스 (0부터 시작)입니다.

*pType*<br/>
형식 정보를 수신 하는 정수에 대 한 포인터입니다. 형식은 다음 값 중 하나일 수 있습니다.

- **0** 상태 표시줄의 평면 보다 작게 표시 되는 테두리가 있는 텍스트가 그려집니다.

- 텍스트를 테두리 없이 그릴 SBT_NOBORDERS 합니다.

- 상태 표시줄의 평면 보다 위쪽에 표시 되는 테두리를 사용 하 여 텍스트를 그린 SBT_POPOUT 합니다.

- SBT_OWNERDRAW 텍스트가 SBT_OWNERDRAW 그리기 형식이 면 *Ptype* 은이 메시지를 받고 길이 및 작업 형식 대신 텍스트와 연결 된 32 비트 값을 반환 합니다.

### <a name="return-value"></a>반환 값

텍스트 또는 현재 텍스트를 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 의 길이 (문자)입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

## <a name="cstatusbarctrlgettextlength"></a><a name="gettextlength"></a> CStatusBarCtrl:: GetTextLength

상태 표시줄 컨트롤의 지정 된 부분에서 텍스트의 길이 (문자)를 검색 합니다.

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>매개 변수

*nPane*<br/>
텍스트를 검색할 파트의 인덱스 (0부터 시작)입니다.

*pType*<br/>
형식 정보를 수신 하는 정수에 대 한 포인터입니다. 형식은 다음 값 중 하나일 수 있습니다.

- **0** 상태 표시줄의 평면 보다 작게 표시 되는 테두리가 있는 텍스트가 그려집니다.

- 텍스트를 테두리 없이 그릴 SBT_NOBORDERS 합니다.

- 부모 창에서 텍스트를 그릴 SBT_OWNERDRAW입니다.

- 상태 표시줄의 평면 보다 위쪽에 표시 되는 테두리를 사용 하 여 텍스트를 그린 SBT_POPOUT 합니다.

### <a name="return-value"></a>반환 값

텍스트의 길이 (문자)입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

## <a name="cstatusbarctrlgettiptext"></a><a name="gettiptext"></a> CStatusBarCtrl:: GetTipText

상태 표시줄에 있는 창에 대 한 도구 설명 텍스트를 검색 합니다.

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>매개 변수

*nPane*<br/>
도구 설명 텍스트를 받을 상태 표시줄 창의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

도구 설명에 사용할 텍스트를 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext)의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

## <a name="cstatusbarctrlissimple"></a><a name="issimple"></a> CStatusBarCtrl:: IsSimple

상태 창 컨트롤이 단순 모드 인지 확인 합니다.

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>반환 값

상태 창 컨트롤이 단순 모드 이면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [SB_ISSIMPLE](/windows/win32/Controls/sb-issimple)의 동작을 구현 합니다.

## <a name="cstatusbarctrlsetbkcolor"></a><a name="setbkcolor"></a> CStatusBarCtrl:: SetBkColor

상태 표시줄의 배경색을 설정 합니다.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>매개 변수

*cr*<br/>
새 배경색을 지정 하는 COLORREF 값입니다. 상태 표시줄의 기본 배경색을 사용 하 여 CLR_DEFAULT 값을 지정 합니다.

### <a name="return-value"></a>반환 값

이전 기본 배경색을 나타내는 [Colorref](/windows/win32/gdi/colorref) 값입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor)의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

## <a name="cstatusbarctrlseticon"></a><a name="seticon"></a> CStatusBarCtrl:: SetIcon

상태 표시줄의 창에 대 한 아이콘을 설정 합니다.

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>매개 변수

*nPane*<br/>
아이콘을 받을 창의 인덱스 (0부터 시작)입니다. 이 매개 변수가-1 인 경우 상태 표시줄은 간단한 상태 표시줄 이라고 가정 합니다.

*hIcon*<br/>
설정할 아이콘에 대 한 핸들입니다. 이 값이 NULL 이면 파트에서 아이콘이 제거 됩니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [SB_SETICON](/windows/win32/Controls/sb-seticon)의 동작을 구현 합니다.

### <a name="example"></a>예제

  [CStatusBarCtrl:: SetBkColor](#setbkcolor)의 예제를 참조 하세요.

## <a name="cstatusbarctrlsetminheight"></a><a name="setminheight"></a> CStatusBarCtrl:: SetMinHeight

상태 표시줄 컨트롤의 그리기 영역에 대 한 최소 높이를 설정 합니다.

```cpp
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>매개 변수

*nMin*<br/>
컨트롤의 최소 높이 (픽셀)입니다.

### <a name="remarks"></a>설명

최소 높이는 상태 표시줄 컨트롤의 세로 테두리 너비 (픽셀)와 *n 분* 의 합입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

## <a name="cstatusbarctrlsetparts"></a><a name="setparts"></a> CStatusBarCtrl:: SetParts

상태 표시줄 컨트롤의 파트 수와 각 파트의 오른쪽 가장자리 좌표를 설정 합니다.

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>매개 변수

*n 부분*<br/>
설정할 파트의 수입니다. 파트 수는 255 보다 클 수 없습니다.

*pWidths*<br/>
*Nparts* 에서 지정한 부분과 동일한 수의 요소를 포함 하는 정수 배열의 주소입니다. 배열의 각 요소는 해당 파트의 오른쪽 가장자리의 위치 (클라이언트 좌표)를 지정 합니다. 요소가-1 인 경우 해당 파트에 대 한 오른쪽 가장자리의 위치는 컨트롤의 오른쪽 가장자리로 확장 됩니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

## <a name="cstatusbarctrlsetsimple"></a><a name="setsimple"></a> CStatusBarCtrl:: SetSimple

상태 표시줄 컨트롤에서 간단한 텍스트를 표시 하거나 [setparts](#setparts)에 대 한 이전 호출로 설정 된 모든 제어 파트를 표시할지 여부를 지정 합니다.

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>매개 변수

*bSimple*<br/>
진행 표시 유형 플래그입니다. 이 매개 변수가 TRUE 이면 컨트롤은 단순 텍스트를 표시 합니다. FALSE 인 경우 여러 부분을 표시 합니다.

### <a name="return-value"></a>반환 값

항상 0을 반환합니다.

### <a name="remarks"></a>설명

응용 프로그램에서 상태 표시줄 컨트롤을 단순 하지 않음에서 단순으로 또는 그 반대로 변경 하는 경우 시스템은 즉시 컨트롤을 다시 그립니다.

## <a name="cstatusbarctrlsettext"></a><a name="settext"></a> CStatusBarCtrl:: SetText

상태 표시줄 컨트롤의 특정 부분에서 텍스트를 설정합니다.

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
설정할 텍스트를 지정하는 null 종료 문자열의 주소입니다. *NType* 가 SBT_OWNERDRAW 이면 *lpszText* 는 32 비트 데이터를 나타냅니다.

*nPane*<br/>
설정할 부분의 0부터 시작하는 인덱스입니다. 이 값이 255인 경우에는 상태 표시줄 컨트롤이 하나의 부분만 있는 단일 컨트롤인 것으로 간주됩니다.

*nType*<br/>
그리기 작업의 형식입니다. 가능한 값 목록은 [SB_SETTEXT 메시지](/windows/win32/Controls/sb-settext) 를 참조 하세요.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메시지는 컨트롤이 다음에 WM_PAINT 메시지를 받을 때 새 텍스트를 표시 하도록 변경 된 컨트롤 부분을 무효화 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

## <a name="cstatusbarctrlsettiptext"></a><a name="settiptext"></a> CStatusBarCtrl:: SetTipText

상태 표시줄에 창에 대 한 도구 설명 텍스트를 설정 합니다.

```cpp
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>매개 변수

*nPane*<br/>
도구 설명 텍스트를 받을 상태 표시줄 창의 인덱스 (0부터 시작)입니다.

*pszTipText*<br/>
도구 설명 텍스트를 포함 하는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [SB_SETTIPTEXT](/windows/win32/Controls/sb-settiptext)의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>참고 항목

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl 클래스](../../mfc/reference/ctoolbarctrl-class.md)
