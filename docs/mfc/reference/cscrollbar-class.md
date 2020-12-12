---
description: '자세히 알아보기: CScrollBar 클래스'
title: CScrollBar 클래스
ms.date: 11/04/2016
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
helpviewer_keywords:
- CScrollBar [MFC], CScrollBar
- CScrollBar [MFC], Create
- CScrollBar [MFC], EnableScrollBar
- CScrollBar [MFC], GetScrollBarInfo
- CScrollBar [MFC], GetScrollInfo
- CScrollBar [MFC], GetScrollLimit
- CScrollBar [MFC], GetScrollPos
- CScrollBar [MFC], GetScrollRange
- CScrollBar [MFC], SetScrollInfo
- CScrollBar [MFC], SetScrollPos
- CScrollBar [MFC], SetScrollRange
- CScrollBar [MFC], ShowScrollBar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
ms.openlocfilehash: a557fe490b2cdce81d5639f9ce15fd6462442029
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264741"
---
# <a name="cscrollbar-class"></a>CScrollBar 클래스

Windows 스크롤 막대 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CScrollBar : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CScrollBar:: CScrollBar](#cscrollbar)|`CScrollBar` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CScrollBar:: Create](#create)|Windows 스크롤 막대를 만들어 개체에 연결 `CScrollBar` 합니다.|
|[CScrollBar:: EnableScrollBar](#enablescrollbar)|스크롤 막대의 화살표 하나 또는 둘 다를 사용하거나 사용하지 않도록 설정합니다.|
|[CScrollBar:: GetScrollBarInfo](#getscrollbarinfo)|구조를 사용 하 여 스크롤 막대에 대 한 정보를 검색 `SCROLLBARINFO` 합니다.|
|[CScrollBar:: GetScrollInfo](#getscrollinfo)|스크롤 막대에 대 한 정보를 검색 합니다.|
|[CScrollBar:: GetScrollLimit](#getscrolllimit)|스크롤 막대의 한도를 검색 합니다.|
|[CScrollBar:: GetScrollPos](#getscrollpos)|스크롤 상자의 현재 위치를 검색합니다.|
|[CScrollBar:: GetScrollRange](#getscrollrange)|지정 된 스크롤 막대에 대 한 현재 최소 및 최대 스크롤 막대 위치를 검색 합니다.|
|[CScrollBar:: SetScrollInfo](#setscrollinfo)|스크롤 막대에 대한 정보를 설정합니다.|
|[CScrollBar:: SetScrollPos](#setscrollpos)|스크롤 상자의 현재 위치를 설정 합니다.|
|[CScrollBar:: SetScrollRange](#setscrollrange)|지정된 스크롤 막대에 대한 최소 및 최대 위치 값을 설정합니다.|
|[CScrollBar:: ShowScrollBar](#showscrollbar)|스크롤 막대를 표시 하거나 숨깁니다.|

## <a name="remarks"></a>설명

스크롤 막대 컨트롤은 두 단계로 만듭니다. 먼저 생성자를 호출 `CScrollBar` 하 여 개체를 생성 `CScrollBar` 한 다음 [create](#create) member 함수를 호출 하 여 Windows 스크롤 막대 컨트롤을 만들고이를 개체에 연결 `CScrollBar` 합니다.

대화 상자에서 대화 상자를 사용 하 여 개체를 만드는 경우 `CScrollBar` `CScrollBar` 사용자가 대화 상자를 닫으면가 자동으로 삭제 됩니다.

`CScrollBar`창 내에서 개체를 만드는 경우 해당 개체를 삭제 해야 할 수도 있습니다.

스택에서 개체를 만들면 `CScrollBar` 자동으로 제거 됩니다. `CScrollBar`함수를 사용 하 여 힙에서 개체를 만드는 경우 **`new`** **`delete`** 사용자가 Windows 스크롤 막대를 종료할 때 개체에 대해를 호출 하 여 개체를 제거 해야 합니다.

개체에 메모리를 할당 하는 경우 `CScrollBar` 소멸자를 재정의 `CScrollBar` 하 여 할당을 삭제 합니다.

사용에 대 한 관련 정보는 `CScrollBar` [컨트롤](../../mfc/controls-mfc.md)을 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cscrollbarcreate"></a><a name="create"></a> CScrollBar:: Create

Windows 스크롤 막대를 만들어 개체에 연결 `CScrollBar` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
스크롤 막대의 스타일을 지정 합니다. 스크롤 막대 [스타일](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) 의 조합을 스크롤 막대에 적용 합니다.

*rect*<br/>
스크롤 막대의 크기와 위치를 지정 합니다. `RECT`구조 또는 개체 중 하나일 수 있습니다 `CRect` .

*pParentWnd*<br/>
스크롤 막대의 부모 창 (일반적으로 개체)을 지정 합니다 `CDialog` . NULL이 아니어야 합니다.

*nID*<br/>
스크롤 막대의 컨트롤 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CScrollBar`두 단계로 개체를 구성 합니다. 먼저 개체를 생성 하는 생성자를 호출 하 고 `CScrollBar` ,를 호출 하 여 `Create` 연결 된 Windows 스크롤 막대를 만들고 초기화 한 다음 개체에 연결 합니다 `CScrollBar` .

스크롤 막대에 다음 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles) 을 적용 합니다.

- 항상 WS_CHILD

- WS_VISIBLE 일반적으로

- WS_DISABLED 거의 없음

- 컨트롤을 그룹화 WS_GROUP

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

## <a name="cscrollbarcscrollbar"></a><a name="cscrollbar"></a> CScrollBar:: CScrollBar

`CScrollBar` 개체를 생성합니다.

```
CScrollBar();
```

### <a name="remarks"></a>설명

개체를 생성 한 후에는 `Create` 멤버 함수를 호출 하 여 Windows 스크롤 막대를 만들고 초기화 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

## <a name="cscrollbarenablescrollbar"></a><a name="enablescrollbar"></a> CScrollBar:: EnableScrollBar

스크롤 막대의 화살표 하나 또는 둘 다를 사용하거나 사용하지 않도록 설정합니다.

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>매개 변수

*nArrowFlags*<br/>
스크롤 화살표를 사용 하거나 사용 하지 않도록 설정 하 고 사용 하거나 사용 하지 않도록 설정 된 화살표를 지정 합니다. 이 매개 변수는 다음 값 중 하나일 수 있습니다.

- ESB_ENABLE_BOTH 스크롤 막대의 두 화살표를 모두 사용 하도록 설정 합니다.

- ESB_DISABLE_LTUP 가로 스크롤 막대의 왼쪽 화살표나 세로 스크롤 막대의 위쪽 화살표를 사용 하지 않도록 설정 합니다.

- ESB_DISABLE_RTDN 가로 스크롤 막대의 오른쪽 화살표 또는 세로 스크롤 막대의 아래쪽 화살표를 사용 하지 않도록 설정 합니다.

- ESB_DISABLE_BOTH 스크롤 막대의 두 화살표를 모두 사용 하지 않도록 설정 합니다.

### <a name="return-value"></a>반환 값

지정 된 대로 화살표를 사용 하거나 사용 하지 않도록 설정 하는 경우 0이 아닙니다. 그렇지 않으면 0이 고 화살표가 이미 요청 된 상태에 있거나 오류가 발생 했음을 나타냅니다.

### <a name="example"></a>예제

  [Cscrollbar:: SetScrollRange](#setscrollrange)에 대 한 예제를 참조 하세요.

## <a name="cscrollbargetscrollbarinfo"></a><a name="getscrollbarinfo"></a> CScrollBar:: GetScrollBarInfo

`SCROLLBARINFO` 구조체에서 스크롤 막대에 대해 유지 관리하는 정보를 검색합니다.

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>매개 변수

*pScrollInfo*<br/>
[SCROLLBARINFO](/windows/win32/api/winuser/ns-winuser-scrollbarinfo) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 [SBM_SCROLLBARINFO](/windows/win32/Controls/sbm-getscrollbarinfo) 메시지의 기능을 에뮬레이트합니다.

## <a name="cscrollbargetscrollinfo"></a><a name="getscrollinfo"></a> CScrollBar:: GetScrollInfo

`SCROLLINFO` 구조체에서 스크롤 막대에 대해 유지 관리하는 정보를 검색합니다.

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>매개 변수

*lpScrollInfo*<br/>
[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) 구조체에 대 한 포인터입니다. 이 구조에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

*nMask*<br/>
검색할 스크롤 막대 매개 변수를 지정 합니다. 일반적인 사용법 SIF_ALL는 SIF_PAGE, SIF_POS, SIF_TRACKPOS 및 SIF_RANGE의 조합을 지정 합니다. `SCROLLINFO`NMask 값에 대 한 자세한 내용은을 참조 하십시오.

### <a name="return-value"></a>반환 값

메시지에서 값을 검색 한 경우 반환 값은 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

`GetScrollInfo` 응용 프로그램에서 32 비트 스크롤 위치를 사용할 수 있도록 합니다.

[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) 구조체에는 최소 및 최대 스크롤 위치, 페이지 크기 및 스크롤 상자 (엄지 단추)의 위치를 포함 하는 스크롤 막대에 대 한 정보가 포함 되어 있습니다. `SCROLLINFO`구조 기본값을 변경 하는 방법에 대 한 자세한 내용은 Windows SDK 구조 항목을 참조 하세요.

스크롤 막대 위치 [CWnd:: OnHScroll 및 [CWnd:: Onhscroll](../../mfc/reference/cwnd-class.md#onvscroll)을 나타내는 MFC Windows 메시지 처리기는 16 비트의 위치 데이터만 제공 합니다. `GetScrollInfo` 및 `SetScrollInfo` 는 스크롤 막대 위치 데이터의 32 비트를 제공 합니다. 따라서 응용 프로그램은 `GetScrollInfo` 또는를 처리 하는 동안를 호출 하 여 `CWnd::OnHScroll` `CWnd::OnVScroll` 32 비트 스크롤 막대 위치 데이터를 가져올 수 있습니다.

### <a name="example"></a>예제

  [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)의 예제를 참조 하세요.

## <a name="cscrollbargetscrolllimit"></a><a name="getscrolllimit"></a> CScrollBar:: GetScrollLimit

스크롤 막대의 최대 스크롤 위치를 검색 합니다.

```
int GetScrollLimit();
```

### <a name="return-value"></a>반환 값

성공 하는 경우 스크롤 막대의 최대 위치를 지정 합니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

  [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)의 예제를 참조 하세요.

## <a name="cscrollbargetscrollpos"></a><a name="getscrollpos"></a> CScrollBar:: GetScrollPos

스크롤 상자의 현재 위치를 검색합니다.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>반환 값

성공 하는 경우 스크롤 상자의 현재 위치를 지정 합니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

현재 위치는 현재 스크롤 범위에 따라 달라 지는 상대 값입니다. 예를 들어 스크롤 범위가 100에서 200이 고 스크롤 상자가 가로 막대의 가운데에 있는 경우 현재 위치는 150입니다.

### <a name="example"></a>예제

  [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)의 예제를 참조 하세요.

## <a name="cscrollbargetscrollrange"></a><a name="getscrollrange"></a> CScrollBar:: GetScrollRange

지정 된 스크롤 막대의 현재 최소 및 최대 스크롤 막대 위치를 *Lpminpos* 및 *lpminpos* 로 지정 된 위치에 복사 합니다.

```cpp
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>매개 변수

*lpMinPos*<br/>
최소 위치를 받을 정수 변수를 가리킵니다.

*lpMaxPos*<br/>
최대 위치를 받을 정수 변수를 가리킵니다.

### <a name="remarks"></a>설명

스크롤 막대 컨트롤의 기본 범위는 비어 있습니다 (두 값 모두 0).

### <a name="example"></a>예제

  [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)의 예제를 참조 하세요.

## <a name="cscrollbarsetscrollinfo"></a><a name="setscrollinfo"></a> CScrollBar:: SetScrollInfo

`SCROLLINFO`구조에서 스크롤 막대에 대해 유지 관리 하는 정보를 설정 합니다.

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>매개 변수

*lpScrollInfo*<br/>
[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) 구조체에 대 한 포인터입니다.

*bRedraw*<br/>
새 정보를 반영 하기 위해 스크롤 막대를 다시 그릴지 여부를 지정 합니다. *BRedraw* 가 TRUE 이면 스크롤 막대가 다시 그려집니다. FALSE 이면 다시 그려지지 않습니다. 기본적으로 스크롤 막대가 다시 그려집니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE가 반환 됩니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

`SCROLLINFO`플래그 값을 포함 하 여 구조 매개 변수에 필요한 값을 제공 해야 합니다.

구조에는 `SCROLLINFO` 최소 및 최대 스크롤 위치, 페이지 크기 및 스크롤 상자 (엄지 단추)의 위치를 포함 하는 스크롤 막대에 대 한 정보가 포함 되어 있습니다. 구조 기본값을 변경 하는 방법에 대 한 자세한 내용은 Windows SDK의 [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) structure 항목을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

## <a name="cscrollbarsetscrollpos"></a><a name="setscrollpos"></a> CScrollBar:: SetScrollPos

스크롤 상자의 현재 위치를 *Npos* 에 지정 된 위치에 설정 하 고, 지정 된 경우 새 위치를 반영 하도록 스크롤 막대를 다시 그립니다.

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
스크롤 상자의 새 위치를 지정 합니다. 스크롤 범위 내에 있어야 합니다.

*bRedraw*<br/>
새 위치를 반영 하기 위해 스크롤 막대를 다시 그릴지 여부를 지정 합니다. *BRedraw* 가 TRUE 이면 스크롤 막대가 다시 그려집니다. FALSE 이면 다시 그려지지 않습니다. 기본적으로 스크롤 막대가 다시 그려집니다.

### <a name="return-value"></a>반환 값

성공 하는 경우 스크롤 상자의 이전 위치를 지정 합니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

다른 함수에 대 한 후속 호출에서 스크롤 막대를 다시 그릴 때마다 *bRedraw* 을 FALSE로 설정 하 여 스크롤 막대가 짧은 간격 내에 두 번 다시 그려지지 않도록 합니다.

### <a name="example"></a>예제

  [Cscrollbar:: SetScrollRange](#setscrollrange)에 대 한 예제를 참조 하세요.

## <a name="cscrollbarsetscrollrange"></a><a name="setscrollrange"></a> CScrollBar:: SetScrollRange

지정된 스크롤 막대에 대한 최소 및 최대 위치 값을 설정합니다.

```cpp
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>매개 변수

*nMinPos*<br/>
최소 스크롤 위치를 지정 합니다.

*nMaxPos*<br/>
최대 스크롤 위치를 지정 합니다.

*bRedraw*<br/>
변경 내용을 반영 하기 위해 스크롤 막대를 다시 그릴지 여부를 지정 합니다. *BRedraw* 가 TRUE 이면 스크롤 막대가 다시 그려집니다. FALSE 이면 다시 그려지지 않습니다. 기본적으로 다시 그려집니다.

### <a name="remarks"></a>설명

표준 스크롤 막대를 숨기려면 *Nminpos* 및 *nminpos* 를 0으로 설정 합니다.

스크롤 막대 알림 메시지를 처리 하는 동안 스크롤 막대를 숨기려면이 함수를 호출 하지 마세요.

에 대 한 호출이 `SetScrollRange` 멤버 함수를 호출 하는 즉시 수행 되는 경우 `SetScrollPos` 에는 *bRedraw* 를 `SetScrollPos` 0으로 설정 하 여 스크롤 막대가 두 번 다시 그려지지 않도록 합니다.

*Nminpos* 및 *nminpos* 에 지정 된 값의 차이는 32767 보다 크지 않아야 합니다. 스크롤 막대 컨트롤의 기본 범위는 비어 있습니다 ( *Nminpos* 및 *nminpos* 는 모두 0).

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

## <a name="cscrollbarshowscrollbar"></a><a name="showscrollbar"></a> CScrollBar:: ShowScrollBar

스크롤 막대를 표시 하거나 숨깁니다.

```cpp
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>매개 변수

*bShow*<br/>
스크롤 막대를 표시할지 여부를 지정 합니다. 이 매개 변수가 TRUE 이면 스크롤 막대가 표시 됩니다. 그렇지 않으면 숨깁니다.

### <a name="remarks"></a>설명

스크롤 막대 알림 메시지를 처리 하는 동안 스크롤 막대를 숨기려면 응용 프로그램에서이 함수를 호출 하면 안 됩니다.

### <a name="example"></a>예제

  [Cscrollbar:: Create](#create)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[CButton 클래스](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 클래스](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit 클래스](../../mfc/reference/cedit-class.md)<br/>
[CListBox 클래스](../../mfc/reference/clistbox-class.md)<br/>
[CStatic 클래스](../../mfc/reference/cstatic-class.md)<br/>
[CDialog 클래스](../../mfc/reference/cdialog-class.md)
