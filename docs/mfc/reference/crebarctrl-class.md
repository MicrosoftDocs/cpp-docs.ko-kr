---
description: '자세한 정보: Cre바 Ctrl 클래스'
title: Cre바 Ctrl 클래스
ms.date: 11/19/2018
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
helpviewer_keywords:
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
ms.openlocfilehash: 75caee2fb0b6bb883ecb421325d41b25c38252b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301232"
---
# <a name="crebarctrl-class"></a>Cre바 Ctrl 클래스

자식 창의 컨테이너인 rebar 컨트롤의 기능을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Cre바 Ctrl:: Cre Ctrl](#crebarctrl)|`CReBarCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Cre바 Ctrl:: BeginDrag](#begindrag)|Rebar 컨트롤을 끌어서 놓기 모드로 전환 합니다.|
|[Cre바 Ctrl:: Create](#create)|Rebar 컨트롤을 만들고이를 개체에 연결 `CReBarCtrl` 합니다.|
|[Cre바 Ctrl:: CreateEx](#createex)|지정 된 Windows 확장 스타일을 사용 하 여 rebar 컨트롤을 만들고이를 `CReBarCtrl` 개체에 연결 합니다.|
|[Cre바 Ctrl::D eleteBand](#deleteband)|Rebar 컨트롤에서 밴드를 삭제 합니다.|
|[Cre바 Ctrl::D ragMove](#dragmove)|를 호출한 후 rebar 컨트롤의 끌기 위치를 업데이트 `BeginDrag` 합니다.|
|[Cre바 Ctrl:: EndDrag](#enddrag)|Rebar 컨트롤의 끌어서 놓기 작업을 종료 합니다.|
|[Cre바 Ctrl:: Get밴드 테두리](#getbandborders)|밴드의 테두리를 검색 합니다.|
|[Cre바 Ctrl:: Get대역 수](#getbandcount)|현재 rebar 컨트롤의 밴드 수를 검색 합니다.|
|[Cre바 Ctrl:: Get대역 정보](#getbandinfo)|Rebar 컨트롤에서 지정 된 밴드에 대 한 정보를 검색 합니다.|
|[Cre바 Ctrl:: Get대역 여백](#getbandmargins)|밴드의 여백을 검색 합니다.|
|[Cre바 Ctrl:: GetBarHeight](#getbarheight)|Rebar 컨트롤의 높이를 검색 합니다.|
|[Cre바 Ctrl:: Get 정보](#getbarinfo)|Rebar 컨트롤과이 컨트롤에서 사용 하는 이미지 목록에 대 한 정보를 검색 합니다.|
|[Cre바 Ctrl:: GetBkColor](#getbkcolor)|Rebar 컨트롤의 기본 배경색을 검색 합니다.|
|[Cre바 Ctrl:: GetColorScheme](#getcolorscheme)|Rebar 컨트롤과 연결 된 [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) 구조체를 검색 합니다.|
|[Cre바 Ctrl:: GetDropTarget](#getdroptarget)|Rebar 컨트롤의 `IDropTarget` 인터페이스 포인터를 검색 합니다.|
|[Cre바 Ctrl:: GetExtendedStyle](#getextendedstyle)|현재 rebar 컨트롤의 확장 스타일을 가져옵니다.|
|[Cre바 Ctrl:: GetImageList](#getimagelist)|Rebar 컨트롤과 연결 된 이미지 목록을 검색 합니다.|
|[Cre바 Ctrl:: GetPalette](#getpalette)|Rebar 컨트롤의 현재 색상표를 검색 합니다.|
|[Cre바 Ctrl:: GetRect](#getrect)|Rebar 컨트롤에서 지정 된 밴드에 대 한 경계 사각형을 검색 합니다.|
|[Cre바 Ctrl:: GetRowCount](#getrowcount)|Rebar 컨트롤의 밴드 행 수를 검색 합니다.|
|[Cre바 Ctrl:: GetRowHeight](#getrowheight)|Rebar 컨트롤에서 지정 된 행의 높이를 검색 합니다.|
|[Cre바 Ctrl:: GetTextColor](#gettextcolor)|Rebar 컨트롤의 기본 텍스트 색을 검색 합니다.|
|[Cre바 Ctrl:: GetToolTips](#gettooltips)|Rebar 컨트롤과 연결 된 모든 도구 설명 컨트롤에 대 한 핸들을 검색 합니다.|
|[Cre바 Ctrl:: System.windows.media.visualtreehelper.hittest](#hittest)|해당 지점에 rebar 밴드가 있는 경우 화면에서 지정 된 지점에 있는 rebar 밴드의 부분을 결정 합니다.|
|[CReBarCtrl:: IDToIndex](#idtoindex)|밴드 식별자 (ID)를 rebar 컨트롤의 밴드 인덱스로 변환 합니다.|
|[Cre바 Ctrl:: InsertBand](#insertband)|Rebar 컨트롤에 새 밴드를 삽입 합니다.|
|[Cre바 Ctrl:: MaximizeBand](#maximizeband)|Rebar 컨트롤의 밴드 크기를 가장 큰 크기로 조정 합니다.|
|[Cre바 Ctrl:: MinimizeBand](#minimizeband)|Rebar 컨트롤의 밴드 크기를 가장 작은 크기로 조정 합니다.|
|[Cre바 Ctrl:: MoveBand](#moveband)|한 인덱스에서 다른 인덱스로 밴드를 이동 합니다.|
|[Cre바 Ctrl::P ushChevron](#pushchevron)|프로그래밍 방식으로 펼침 단추를 푸시합니다.|
|[Cre바 Ctrl:: RestoreBand](#restoreband)|Rebar 컨트롤의 밴드 크기를 이상적인 크기로 조정 합니다.|
|[Cre바 Ctrl:: Set대역 정보](#setbandinfo)|Rebar 컨트롤에서 기존 밴드의 특징을 설정 합니다.|
|[Cre바 Ctrl:: SetBandWidth](#setbandwidth)|현재 rebar 컨트롤에서 지정 된 도킹 된 밴드의 너비를 설정 합니다.|
|[Cre바 Ctrl:: Set 정보](#setbarinfo)|Rebar 컨트롤의 특징을 설정 합니다.|
|[Cre바 Ctrl:: SetBkColor](#setbkcolor)|Rebar 컨트롤의 기본 배경색을 설정 합니다.|
|[Cre바 Ctrl:: SetColorScheme](#setcolorscheme)|Rebar 컨트롤의 단추 색 구성표를 설정 합니다.|
|[Cre바 Ctrl:: SetExtendedStyle](#setextendedstyle)|현재 rebar 컨트롤에 대 한 확장 스타일을 설정 합니다.|
|[Cre바 Ctrl:: Seon Agelist](#setimagelist)|Rebar 컨트롤의 이미지 목록을 설정 합니다.|
|[Cre바 Ctrl:: SetOwner](#setowner)|Rebar 컨트롤의 소유자 창을 설정 합니다.|
|[Cre바 Ctrl:: SetPalette](#setpalette)|Rebar 컨트롤의 현재 색상표를 설정 합니다.|
|[Cre바 Ctrl:: SetTextColor](#settextcolor)|Rebar 컨트롤의 기본 텍스트 색을 설정 합니다.|
|[Cre바 Ctrl:: SetToolTips](#settooltips)|도구 설명 컨트롤을 rebar 컨트롤과 연결 합니다.|
|[Cre바 Ctrl:: SetWindowTheme](#setwindowtheme)|Rebar 컨트롤의 비주얼 스타일을 설정 합니다.|
|[Cre바 Ctrl:: ShowBand](#showband)|Rebar 컨트롤에서 지정 된 밴드를 표시 하거나 숨깁니다.|
|[Cre바 Ctrl:: SizeToRect](#sizetorect)|지정 된 사각형에 rebar 컨트롤을 맞춥니다.|

## <a name="remarks"></a>설명

Rebar 컨트롤이 있는 응용 프로그램은 rebar 컨트롤에 포함 된 자식 창을 rebar 밴드에 할당 합니다. 자식 창은 일반적으로 다른 공용 컨트롤입니다.

Rebar 컨트롤은 하나 이상의 밴드를 포함 합니다. 각 밴드에는 그리퍼 막대, 비트맵, 텍스트 레이블 및 자식 창의 조합을 포함할 수 있습니다. 밴드는 이러한 항목 중 하나만 포함할 수 있습니다.

Rebar 컨트롤은 지정 된 배경 비트맵 위에 자식 창을 표시할 수 있습니다. RBBS_FIXEDSIZE 스타일을 사용 하는 경우를 제외 하 고 모든 rebar 컨트롤 밴드의 크기를 조정할 수 있습니다. Rebar 컨트롤 밴드의 위치를 변경 하거나 크기를 조정할 때 rebar 컨트롤은 해당 밴드에 할당 된 자식 창의 크기와 위치를 관리 합니다. 컨트롤 내에서 밴드의 크기를 조정 하거나 순서를 변경 하려면 밴드의 그리퍼 막대를 클릭 하 고 끕니다.

다음 그림에서는 세 개의 밴드가 있는 rebar 컨트롤을 보여 줍니다.

- 대역 0에는 플랫 투명 도구 모음 컨트롤이 포함 되어 있습니다.

- 밴드 1에는 투명 표준 및 투명 드롭다운 단추가 모두 포함 됩니다.

- 밴드 2는 콤보 상자와 4 개의 표준 단추를 포함 합니다.

   ![Rebar 메뉴의 예](../../mfc/reference/media/vc4scc1.gif "Rebar 메뉴의 예")

## <a name="rebar-control"></a>Rebar 컨트롤

Rebar 컨트롤 지원:

- 이미지 목록.

- 메시지 처리.

- 사용자 지정 그리기 기능.

- 표준 창 스타일 외에도 다양 한 컨트롤 스타일입니다. 이러한 스타일의 목록은 Windows SDK의 [Rebar 컨트롤 스타일](/windows/win32/Controls/rebar-control-styles) 을 참조 하세요.

자세한 내용은 [CReBarCtrl 사용](../../mfc/using-crebarctrl.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="crebarctrlbegindrag"></a><a name="begindrag"></a> Cre바 Ctrl:: BeginDrag

Windows SDK에 설명 된 대로 Win32 메시지 [RB_BEGINDRAG](/windows/win32/Controls/rb-begindrag)의 동작을 구현 합니다.

```cpp
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>매개 변수

*uBand*<br/>
끌어서 놓기 작업에 영향을 줄 수 있는 대역의 인덱스 (0부터 시작)입니다.

*dwPos*<br/>
시작 마우스 좌표를 포함 하는 DWORD 값입니다. 가로 좌표는 LOWORD에 포함 되 고 세로 좌표는 고가 단어에 포함 됩니다. (DWORD)-1을 전달 하는 경우 rebar 컨트롤은 컨트롤의 스레드가 마지막으로 또는를 호출한 시간에 마우스 위치를 사용 `GetMessage` 합니다 `PeekMessage` .

## <a name="crebarctrlcreate"></a><a name="create"></a> Cre바 Ctrl:: Create

Rebar 컨트롤을 만들고이를 개체에 연결 `CReBarCtrl` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
컨트롤에 적용 되는 rebar 컨트롤 스타일의 조합을 지정 합니다. 지원 되는 스타일 목록은 Windows SDK의 [Rebar 컨트롤 스타일](/windows/win32/Controls/rebar-control-styles) 을 참조 하세요.

*rect*<br/>
Rebar 컨트롤의 위치와 크기에 해당 하는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*pParentWnd*<br/>
Rebar 컨트롤의 부모 창인 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 포인터입니다. NULL이 아니어야 합니다.

*nID*<br/>
Rebar 컨트롤의 컨트롤 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

개체가 성공적으로 만들어진 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

다음 두 단계로 rebar 컨트롤을 만듭니다.

1. [Cre바 ctrl](#crebarctrl) 을 호출 하 여 `CReBarCtrl` 개체를 생성 합니다.

1. 이 멤버 함수를 호출 합니다 .이 함수는 Windows rebar 컨트롤을 만들고이를 개체에 연결 `CReBarCtrl` 합니다.

를 호출 하면 `Create` 공용 컨트롤이 초기화 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

## <a name="crebarctrlcreateex"></a><a name="createex"></a> Cre바 Ctrl:: CreateEx

컨트롤 (자식 창)을 만들고이를 개체에 연결 `CReBarCtrl` 합니다.

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
컨트롤에 적용 되는 rebar 컨트롤 스타일의 조합을 지정 합니다. 지원 되는 스타일 목록은 Windows SDK의 [Rebar 컨트롤 스타일](/windows/win32/Controls/rebar-control-styles) 을 참조 하세요.

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

## <a name="crebarctrlcrebarctrl"></a><a name="crebarctrl"></a> Cre바 Ctrl:: Cre Ctrl

`CReBarCtrl` 개체를 만듭니다.

```
CReBarCtrl();
```

### <a name="example"></a>예제

  [Crebarctrl:: Create](#create)의 예제를 참조 하세요.

## <a name="crebarctrldeleteband"></a><a name="deleteband"></a> Cre바 Ctrl::D eleteBand

Windows SDK에 설명 된 대로 Win32 메시지 [RB_DELETEBAND](/windows/win32/Controls/rb-deleteband)의 동작을 구현 합니다.

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>매개 변수

*uBand*<br/>
삭제할 밴드의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

밴드가 삭제 되 면 0이 아닌 값으로 설정 됩니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

## <a name="crebarctrldragmove"></a><a name="dragmove"></a> Cre바 Ctrl::D ragMove

Windows SDK에 설명 된 대로 Win32 메시지 [RB_DRAGMOVE](/windows/win32/Controls/rb-dragmove)의 동작을 구현 합니다.

```cpp
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>매개 변수

*dwPos*<br/>
새 마우스 좌표를 포함 하는 DWORD 값입니다. 가로 좌표는 LOWORD에 포함 되 고 세로 좌표는 고가 단어에 포함 됩니다. (DWORD)-1을 전달 하는 경우 rebar 컨트롤은 컨트롤의 스레드가 마지막으로 또는를 호출한 시간에 마우스 위치를 사용 `GetMessage` 합니다 `PeekMessage` .

## <a name="crebarctrlenddrag"></a><a name="enddrag"></a> Cre바 Ctrl:: EndDrag

Windows SDK에 설명 된 대로 Win32 메시지 [RB_ENDDRAG](/windows/win32/Controls/rb-enddrag)의 동작을 구현 합니다.

```cpp
void EndDrag();
```

## <a name="crebarctrlgetbandborders"></a><a name="getbandborders"></a> Cre바 Ctrl:: Get밴드 테두리

Windows SDK에 설명 된 대로 Win32 메시지 [RB_GETBANDBORDERS](/windows/win32/Controls/rb-getbandborders)의 동작을 구현 합니다.

```cpp
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>매개 변수

*uBand*<br/>
테두리를 검색할 대역의 인덱스 (0부터 시작)입니다.

*prc*<br/>
밴드 테두리를 수신 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 포인터입니다. Rebar 컨트롤에 RBS_BANDBORDERS 스타일이 있는 경우이 구조체의 각 멤버는 경계를 구성 하는 밴드의 해당 측면에서 픽셀 수를 받습니다. Rebar 컨트롤에 RBS_BANDBORDERS 스타일이 없으면이 구조체의 왼쪽 멤버만 유효한 정보를 받습니다. Rebar 컨트롤 스타일에 대 한 설명은 Windows SDK의 [Rebar 컨트롤 스타일](/windows/win32/Controls/rebar-control-styles) 을 참조 하세요.

## <a name="crebarctrlgetbandcount"></a><a name="getbandcount"></a> Cre바 Ctrl:: Get대역 수

Windows SDK에 설명 된 대로 Win32 메시지 [RB_GETBANDCOUNT](/windows/win32/Controls/rb-getbandcount)의 동작을 구현 합니다.

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>반환 값

컨트롤에 할당 된 밴드 수입니다.

## <a name="crebarctrlgetbandinfo"></a><a name="getbandinfo"></a> Cre바 Ctrl:: Get대역 정보

Windows SDK에 설명 된 대로 Win32 메시지 [RB_GETBANDINFO](/windows/win32/Controls/rb-getbandinfo) 의 동작을 구현 합니다.

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>매개 변수

*uBand*<br/>
정보를 검색할 대역의 인덱스 (0부터 시작)입니다.

*prbbi*<br/>
대역 정보를 수신 하는 [Re바 밴드 정보](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) 구조에 대 한 포인터입니다. 이 `cbSize` 구조체의 멤버를로 설정 하 `sizeof(REBARBANDINFO)` 고 `fMask` 이 메시지를 보내기 전에 검색 하려는 항목으로 멤버를 설정 해야 합니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

## <a name="crebarctrlgetbandmargins"></a><a name="getbandmargins"></a> Cre바 Ctrl:: Get대역 여백

밴드의 여백을 검색 합니다.

```cpp
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>매개 변수

*pMargins*<br/>
정보를 수신 하는 [여백](/windows/win32/api/uxtheme/ns-uxtheme-margins)구조에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 [RB_GETBANDMARGINS](/windows/win32/Controls/rb-getbandmargins) 메시지의 기능을 에뮬레이트합니다.

## <a name="crebarctrlgetbarheight"></a><a name="getbarheight"></a> Cre바 Ctrl:: GetBarHeight

Rebar 막대의 높이를 검색 합니다.

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>반환 값

컨트롤의 높이를 픽셀 단위로 나타내는 값입니다.

## <a name="crebarctrlgetbarinfo"></a><a name="getbarinfo"></a> Cre바 Ctrl:: Get 정보

Windows SDK에 설명 된 대로 Win32 메시지 [RB_GETBARINFO](/windows/win32/Controls/rb-getbarinfo)의 동작을 구현 합니다.

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>매개 변수

*prbi*<br/>
Rebar 컨트롤 정보를 받는 [Rebarinfo](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) 구조에 대 한 포인터입니다. 이 메시지를 보내기 전에이 구조체의 *Cbsize* 멤버를로 설정 해야 합니다 `sizeof(REBARINFO)` .

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

## <a name="crebarctrlgetbkcolor"></a><a name="getbkcolor"></a> Cre바 Ctrl:: GetBkColor

Windows SDK에 설명 된 대로 Win32 메시지 [RB_GETBKCOLOR](/windows/win32/Controls/rb-getbkcolor)의 동작을 구현 합니다.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>반환 값

현재 기본 배경색을 나타내는 COLORREF 값입니다.

## <a name="crebarctrlgetcolorscheme"></a><a name="getcolorscheme"></a> Cre바 Ctrl:: GetColorScheme

Rebar 컨트롤에 대 한 [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) 구조체를 검색 합니다.

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>매개 변수

*lpcs*<br/>
Windows SDK 설명 된 대로 [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

구조체에는 `COLORSCHEME` 단추 강조 색과 단추 그림자 색이 포함 됩니다.

## <a name="crebarctrlgetdroptarget"></a><a name="getdroptarget"></a> Cre바 Ctrl:: GetDropTarget

Windows SDK에 설명 된 대로 Win32 메시지 [RB_GETDROPTARGET](/windows/win32/Controls/rb-getdroptarget)의 동작을 구현 합니다.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>반환 값

[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) 인터페이스에 대 한 포인터입니다.

## <a name="crebarctrlgetextendedstyle"></a><a name="getextendedstyle"></a> Cre바 Ctrl:: GetExtendedStyle

현재 rebar 컨트롤의 확장 스타일을 가져옵니다.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>반환 값

확장 스타일을 나타내는 플래그의 비트 조합 (OR)입니다. 가능한 플래그는 RBS_EX_SPLITTER 및 RBS_EX_TRANSPARENT입니다. 자세한 내용은 [Cre바 ctrl:: SetExtendedStyle](#setextendedstyle) 메서드의 *dwmask* 매개 변수를 참조 하세요.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [RB_GETEXTENDEDSTYLE](/windows/win32/Controls/rb-dragmove) 메시지를 보냅니다.

## <a name="crebarctrlgetimagelist"></a><a name="getimagelist"></a> Cre바 Ctrl:: GetImageList

`CImageList`Rebar 컨트롤과 연결 된 개체를 가져옵니다.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>반환 값

[CImageList](../../mfc/reference/cimagelist-class.md) 개체에 대 한 포인터입니다. 컨트롤에 대해 설정 된 이미지 목록이 없으면 NULL을 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK 설명 된 대로 [Re바 정보](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) 구조에 저장 된 크기 및 마스크 정보를 사용 합니다.

## <a name="crebarctrlgetpalette"></a><a name="getpalette"></a> Cre바 Ctrl:: GetPalette

Rebar 컨트롤의 현재 색상표를 검색 합니다.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>반환 값

Rebar 컨트롤의 현재 색상표를 지정 하는 [Cpalette](../../mfc/reference/cpalette-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 `CPalette` HPALETTE 대신 개체를 반환 값으로 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

## <a name="crebarctrlgetrect"></a><a name="getrect"></a> Cre바 Ctrl:: GetRect

Windows SDK에 설명 된 대로 Win32 메시지 [RB_GETRECT](/windows/win32/Controls/rb-getrect)의 동작을 구현 합니다.

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>매개 변수

*uBand*<br/>
Rebar 컨트롤에서 밴드의 인덱스 (0부터 시작)입니다.

*prc*<br/>
Rebar 밴드의 경계를 수신 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

## <a name="crebarctrlgetrowcount"></a><a name="getrowcount"></a> Cre바 Ctrl:: GetRowCount

Windows SDK에 설명 된 대로 Win32 메시지 [RB_GETROWCOUNT](/windows/win32/Controls/rb-getrowcount)의 동작을 구현 합니다.

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>반환 값

컨트롤의 밴드 행 수를 나타내는 UINT 값입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

## <a name="crebarctrlgetrowheight"></a><a name="getrowheight"></a> Cre바 Ctrl:: GetRowHeight

Windows SDK에 설명 된 대로 Win32 메시지 [RB_GETROWHEIGHT](/windows/win32/Controls/rb-getrowheight)의 동작을 구현 합니다.

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>매개 변수

*uRow*<br/>
높이가 검색 되는 대역의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

행 높이 (픽셀)를 나타내는 UINT 값입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

## <a name="crebarctrlgettextcolor"></a><a name="gettextcolor"></a> Cre바 Ctrl:: GetTextColor

Windows SDK에 설명 된 대로 Win32 메시지 [RB_GETTEXTCOLOR](/windows/win32/Controls/rb-gettextcolor)의 동작을 구현 합니다.

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>반환 값

현재 기본 텍스트 색을 나타내는 COLORREF 값입니다.

## <a name="crebarctrlgettooltips"></a><a name="gettooltips"></a> Cre바 Ctrl:: GetToolTips

Windows SDK에 설명 된 대로 Win32 메시지 [RB_GETTOOLTIPS](/windows/win32/Controls/rb-gettooltips)의 동작을 구현 합니다.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>반환 값

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

의 MFC 구현은 `GetToolTips` HWND가 아니라에 대 한 포인터를 반환 합니다 `CToolTipCtrl` .

## <a name="crebarctrlhittest"></a><a name="hittest"></a> Cre바 Ctrl:: System.windows.media.visualtreehelper.hittest

Windows SDK에 설명 된 대로 Win32 메시지 [RB_HITTEST](/windows/win32/Controls/rb-hittest)의 동작을 구현 합니다.

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>매개 변수

*prbht*<br/>
[RBHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-rbhittestinfo) 구조체에 대 한 포인터입니다. 메시지를 보내기 전에 `pt` 이 구조체의 멤버를 테스트 하는 지점 (클라이언트 좌표)으로 초기화 해야 합니다.

### <a name="return-value"></a>반환 값

지정 된 지점에 있는 대역의 인덱스 (0부터 시작)이 고, 지점에 있는 크기 조정 밴드가 없으면-1입니다.

## <a name="crebarctrlidtoindex"></a><a name="idtoindex"></a> CReBarCtrl:: IDToIndex

Windows SDK에 설명 된 대로 Win32 메시지 [RB_IDTOINDEX](/windows/win32/controls/rb-idtoindex)의 동작을 구현 합니다.

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>매개 변수

*uBandID*<br/>
`wID`밴드가 삽입 될 때 [Re바 밴드 정보](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) 구조의 구성원에 전달 되는, 지정 된 대역의 응용 프로그램 정의 식별자입니다.

### <a name="return-value"></a>반환 값

성공 하면 0부터 시작 하는 밴드 인덱스이 고, 그렇지 않으면-1입니다. 중복 된 밴드 인덱스가 있으면 첫 번째 인덱스가 반환 됩니다.

## <a name="crebarctrlinsertband"></a><a name="insertband"></a> Cre바 Ctrl:: InsertBand

Windows SDK에 설명 된 대로 Win32 메시지 [RB_INSERTBAND](/windows/win32/Controls/rb-insertband)의 동작을 구현 합니다.

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>매개 변수

*uIndex*<br/>
밴드가 삽입 되는 위치의 인덱스 (0부터 시작)입니다. 이 매개 변수를-1로 설정 하면 컨트롤이 마지막 위치에 새 밴드를 추가 합니다.

*prbbi*<br/>
삽입할 대역을 정의 하는 [Re바 밴드 정보](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) 구조에 대 한 포인터입니다. 이 함수를 호출 하기 전에이 구조체의 *Cbsize* 멤버를로 설정 해야 합니다 `sizeof(REBARBANDINFO)` .

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

## <a name="crebarctrlmaximizeband"></a><a name="maximizeband"></a> Cre바 Ctrl:: MaximizeBand

Rebar 컨트롤의 밴드 크기를 가장 큰 크기로 조정 합니다.

```cpp
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>매개 변수

*uBand*<br/>
최대화할 밴드의 인덱스 (0부터 시작)입니다.

### <a name="remarks"></a>설명

Windows SDK에 설명 된 대로가 0으로 설정 된 [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) Win32 메시지의 동작을 구현 합니다 `fIdeal` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

## <a name="crebarctrlminimizeband"></a><a name="minimizeband"></a> Cre바 Ctrl:: MinimizeBand

Rebar 컨트롤의 밴드 크기를 가장 작은 크기로 조정 합니다.

```cpp
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>매개 변수

*uBand*<br/>
최소화할 대역의 인덱스 (0부터 시작)입니다.

### <a name="remarks"></a>설명

Windows SDK에 설명 된 대로 Win32 메시지 [RB_MINIMIZEBAND](/windows/win32/Controls/rb-minimizeband)의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

## <a name="crebarctrlmoveband"></a><a name="moveband"></a> Cre바 Ctrl:: MoveBand

Windows SDK에 설명 된 대로 Win32 메시지 [RB_MOVEBAND](/windows/win32/Controls/rb-moveband)의 동작을 구현 합니다.

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>매개 변수

*uFrom*<br/>
이동할 밴드의 인덱스 (0부터 시작)입니다.

*U)*<br/>
새 대역 위치의 인덱스 (0부터 시작)입니다. 이 매개 변수 값은 대역에서 1을 뺀 값 보다 클 수 없습니다. 밴드 수를 가져오려면 [get밴드로 count](#getbandcount)를 호출 합니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

## <a name="crebarctrlpushchevron"></a><a name="pushchevron"></a> Cre바 Ctrl::P ushChevron

Windows SDK에 설명 된 대로 Win32 메시지 [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)의 동작을 구현 합니다.

```cpp
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>매개 변수

*uBand*<br/>
갈매기형 펼침 단추를 푸시할 대역의 인덱스 (0부터 시작)입니다.

*lAppValue*<br/>
32 비트 값이 정의 된 응용 프로그램입니다. Windows SDK에서 [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron) *lappvalue* 를 참조 하세요.

## <a name="crebarctrlrestoreband"></a><a name="restoreband"></a> Cre바 Ctrl:: RestoreBand

Rebar 컨트롤의 밴드 크기를 이상적인 크기로 조정 합니다.

```cpp
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>매개 변수

*uBand*<br/>
최대화할 밴드의 인덱스 (0부터 시작)입니다.

### <a name="remarks"></a>설명

[](/windows/win32/Controls/rb-maximizeband) `fIdeal` Windows SDK에 설명 된 대로를 1로 설정 하 여 RB_MAXIMIZEBAND Win32 메시지의 동작을 구현 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

## <a name="crebarctrlsetbandinfo"></a><a name="setbandinfo"></a> Cre바 Ctrl:: Set대역 정보

Windows SDK에 설명 된 대로 Win32 메시지 [RB_SETBANDINFO](/windows/win32/Controls/rb-setbandinfo)의 동작을 구현 합니다.

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>매개 변수

*uBand*<br/>
새 설정을 받을 대역의 인덱스 (0부터 시작)입니다.

*prbbi*<br/>
삽입할 대역을 정의 하는 [Re바 밴드 정보](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) 구조에 대 한 포인터입니다. 이 `cbSize` 메시지를 보내기 전에이 구조체의 멤버를로 설정 해야 합니다 `sizeof(REBARBANDINFO)` .

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

## <a name="crebarctrlsetbandwidth"></a><a name="setbandwidth"></a> Cre바 Ctrl:: SetBandWidth

현재 rebar 컨트롤에서 지정 된 도킹 된 밴드의 너비를 설정 합니다.

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>매개 변수

*uBand*\
진행 Rebar 밴드의 인덱스 (0부터 시작)입니다.

*cxWidth*\
진행 Rebar 밴드의 새 너비 (픽셀)입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [RB_SETBANDWIDTH](/windows/win32/Controls/rb-setbandwidth) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 `m_rebar` 현재 rebar 컨트롤에 액세스 하는 데 사용 되는 변수를 정의 합니다. 이 변수는 다음 예제에서 사용됩니다.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 각 rebar 밴드를 같은 너비로 설정 합니다.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

## <a name="crebarctrlsetbarinfo"></a><a name="setbarinfo"></a> Cre바 Ctrl:: Set 정보

Windows SDK에 설명 된 대로 Win32 메시지 [RB_SETBARINFO](/windows/win32/Controls/rb-setbarinfo)의 동작을 구현 합니다.

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>매개 변수

*prbi*<br/>
설정할 정보를 포함 하는 [Rebarinfo](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) 구조에 대 한 포인터입니다. 이 `cbSize` `sizeof(REBARINFO)` 메시지를 보내기 전에이 구조체의 멤버를로 설정 해야 합니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

## <a name="crebarctrlsetbkcolor"></a><a name="setbkcolor"></a> Cre바 Ctrl:: SetBkColor

Windows SDK에 설명 된 대로 Win32 메시지 [RB_SETBKCOLOR](/windows/win32/Controls/rb-setbkcolor)의 동작을 구현 합니다.

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>매개 변수

*clr*<br/>
새 기본 배경색을 나타내는 COLORREF 값입니다.

### <a name="return-value"></a>반환 값

이전 기본 배경색을 나타내는 [Colorref](/windows/win32/gdi/colorref) 값입니다.

### <a name="remarks"></a>설명

배경색을 설정 하는 시기와 기본값을 설정 하는 방법에 대 한 자세한 내용은이 항목을 참조 하세요.

## <a name="crebarctrlsetcolorscheme"></a><a name="setcolorscheme"></a> Cre바 Ctrl:: SetColorScheme

Rebar 컨트롤의 단추 색 구성표를 설정 합니다.

```cpp
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>매개 변수

*lpcs*<br/>
Windows SDK 설명 된 대로 [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) 구조체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

구조체에는 `COLORSCHEME` 단추 강조 표시 색과 단추 그림자 색이 모두 포함 되어 있습니다.

## <a name="crebarctrlsetextendedstyle"></a><a name="setextendedstyle"></a> Cre바 Ctrl:: SetExtendedStyle

현재 rebar 컨트롤에 대 한 확장 스타일을 설정 합니다.

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>매개 변수

*dwMask*\
진행 *DwStyleEx* 매개 변수에서 적용 되는 플래그를 지정 하는 플래그의 비트 조합 (or)입니다. 다음 값 중 하나 이상을 사용 합니다.

- `RBS_EX_SPLITTER`: 기본적으로 가로 모드의 아래쪽에 분할자를 표시 하 고 세로 모드에서 오른쪽으로 분할자를 표시 합니다.
- `RBS_EX_TRANSPARENT`: [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) 메시지를 부모 창으로 전달 합니다.

*dwStyleEx*\
진행 적용할 스타일을 지정 하는 플래그의 비트 조합 (OR)입니다. 스타일을 설정 하려면 *Dwmask* 매개 변수에 사용 되는 것과 동일한 플래그를 지정 합니다. 스타일을 다시 설정 하려면 이진 0을 지정 합니다.

### <a name="return-value"></a>반환 값

이전 확장 스타일입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [RB_SETEXTENDEDSTYLE](/windows/win32/Controls/rb-setextendedstyle) 메시지를 보냅니다.

## <a name="crebarctrlsetimagelist"></a><a name="setimagelist"></a> Cre바 Ctrl:: Seon Agelist

Rebar 컨트롤에 이미지 목록을 할당 합니다.

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>매개 변수

*pImageList*<br/>
Rebar 컨트롤에 할당할 이미지 목록을 포함 하는 [CImageList](../../mfc/reference/cimagelist-class.md) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

## <a name="crebarctrlsetowner"></a><a name="setowner"></a> Cre바 Ctrl:: SetOwner

Windows SDK에 설명 된 대로 Win32 메시지 [RB_SETPARENT](/windows/win32/Controls/rb-setparent)의 동작을 구현 합니다.

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
`CWnd`Rebar 컨트롤의 소유자로 설정할 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

Rebar 컨트롤의 현재 소유자 인 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 창에 대 한 `CWnd` 핸들이 아니라 rebar 컨트롤의 현재 소유자와 선택 된 소유자 모두에 대해 개체에 대 한 포인터를 사용 합니다.

> [!NOTE]
> 이 멤버 함수는 컨트롤을 만들 때 설정 된 실제 부모를 변경 하지 않습니다. 대신 지정 하는 창에 알림 메시지를 보냅니다.

## <a name="crebarctrlsetpalette"></a><a name="setpalette"></a> Cre바 Ctrl:: SetPalette

Windows SDK에 설명 된 대로 Win32 메시지 [RB_SETPALETTE](/windows/win32/Controls/rb-setpalette)의 동작을 구현 합니다.

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>매개 변수

*hPal*<br/>
Rebar 컨트롤이 사용할 새 색상표를 지정 하는 HPALETTE입니다.

### <a name="return-value"></a>반환 값

Rebar 컨트롤의 이전 색상표를 지정 하는 [cpalette](../../mfc/reference/cpalette-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 `CPalette` HPALETTE 대신 개체를 반환 값으로 사용 합니다.

## <a name="crebarctrlsettextcolor"></a><a name="settextcolor"></a> Cre바 Ctrl:: SetTextColor

Windows SDK에 설명 된 대로 Win32 메시지 [RB_SETTEXTCOLOR](/windows/win32/Controls/rb-settextcolor)의 동작을 구현 합니다.

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>매개 변수

*clr*<br/>
개체의 새 텍스트 색을 나타내는 COLORREF 값입니다 `CReBarCtrl` .

### <a name="return-value"></a>반환 값

개체와 연결 된 이전 텍스트 색을 나타내는 [Colorref](/windows/win32/gdi/colorref) 값 `CReBarCtrl` 입니다.

### <a name="remarks"></a>설명

Rebar 컨트롤에서 텍스트 색 유연성을 지원 하기 위해 제공 됩니다.

## <a name="crebarctrlsettooltips"></a><a name="settooltips"></a> Cre바 Ctrl:: SetToolTips

도구 설명 컨트롤을 rebar 컨트롤과 연결 합니다.

```cpp
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>매개 변수

*pToolTip*<br/>
[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`CToolTipCtrl`작업이 완료 되 면 개체를 삭제 해야 합니다.

## <a name="crebarctrlsetwindowtheme"></a><a name="setwindowtheme"></a> Cre바 Ctrl:: SetWindowTheme

Rebar 컨트롤의 비주얼 스타일을 설정 합니다.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>매개 변수

*pszSubAppName*<br/>
설정할 rebar 비주얼 스타일을 포함 하는 유니코드 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

반환 값은 사용 되지 않습니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 [RB_SETWINDOWTHEME](/windows/win32/Controls/rb-setwindowtheme) 메시지의 기능을 에뮬레이트합니다.

## <a name="crebarctrlshowband"></a><a name="showband"></a> Cre바 Ctrl:: ShowBand

Windows SDK에 설명 된 대로 Win32 메시지 [RB_SHOWBAND](/windows/win32/Controls/rb-showband)의 동작을 구현 합니다.

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>매개 변수

*uBand*<br/>
Rebar 컨트롤에서 밴드의 인덱스 (0부터 시작)입니다.

*fShow*<br/>
밴드를 표시 하거나 숨길지 여부를 나타냅니다. 이 값이 TRUE 이면 밴드가 표시 됩니다. 그렇지 않으면 대역이 숨겨집니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

## <a name="crebarctrlsizetorect"></a><a name="sizetorect"></a> Cre바 Ctrl:: SizeToRect

Windows SDK에 설명 된 대로 Win32 메시지 [RB_SIZETORECT](/windows/win32/Controls/rb-sizetorect)의 동작을 구현 합니다.

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
Rebar 컨트롤의 크기를 조정 해야 하는 사각형을 지정 하는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공하는 경우 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 `CRect` 구조체 대신 개체를 매개 변수로 사용 합니다 `RECT` .

## <a name="see-also"></a>참고 항목

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
