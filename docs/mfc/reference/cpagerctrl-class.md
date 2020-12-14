---
description: '자세히 알아보기: CPagerCtrl 클래스'
title: CPagerCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CPagerCtrl
- AFXCMN/CPagerCtrl
- AFXCMN/CPagerCtrl::CPagerCtrl
- AFXCMN/CPagerCtrl::Create
- AFXCMN/CPagerCtrl::CreateEx
- AFXCMN/CPagerCtrl::ForwardMouse
- AFXCMN/CPagerCtrl::GetBkColor
- AFXCMN/CPagerCtrl::GetBorder
- AFXCMN/CPagerCtrl::GetButtonSize
- AFXCMN/CPagerCtrl::GetButtonState
- AFXCMN/CPagerCtrl::GetDropTarget
- AFXCMN/CPagerCtrl::GetScrollPos
- AFXCMN/CPagerCtrl::IsButtonDepressed
- AFXCMN/CPagerCtrl::IsButtonGrayed
- AFXCMN/CPagerCtrl::IsButtonHot
- AFXCMN/CPagerCtrl::IsButtonInvisible
- AFXCMN/CPagerCtrl::IsButtonNormal
- AFXCMN/CPagerCtrl::RecalcSize
- AFXCMN/CPagerCtrl::SetBkColor
- AFXCMN/CPagerCtrl::SetBorder
- AFXCMN/CPagerCtrl::SetButtonSize
- AFXCMN/CPagerCtrl::SetChild
- AFXCMN/CPagerCtrl::SetScrollPos
helpviewer_keywords:
- CPagerCtrl [MFC], CPagerCtrl
- CPagerCtrl [MFC], Create
- CPagerCtrl [MFC], CreateEx
- CPagerCtrl [MFC], ForwardMouse
- CPagerCtrl [MFC], GetBkColor
- CPagerCtrl [MFC], GetBorder
- CPagerCtrl [MFC], GetButtonSize
- CPagerCtrl [MFC], GetButtonState
- CPagerCtrl [MFC], GetDropTarget
- CPagerCtrl [MFC], GetScrollPos
- CPagerCtrl [MFC], IsButtonDepressed
- CPagerCtrl [MFC], IsButtonGrayed
- CPagerCtrl [MFC], IsButtonHot
- CPagerCtrl [MFC], IsButtonInvisible
- CPagerCtrl [MFC], IsButtonNormal
- CPagerCtrl [MFC], RecalcSize
- CPagerCtrl [MFC], SetBkColor
- CPagerCtrl [MFC], SetBorder
- CPagerCtrl [MFC], SetButtonSize
- CPagerCtrl [MFC], SetChild
- CPagerCtrl [MFC], SetScrollPos
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
ms.openlocfilehash: ba01d07ebd6d638a1d505d555e44e9562e4bd27b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345227"
---
# <a name="cpagerctrl-class"></a>CPagerCtrl 클래스

`CPagerCtrl` 클래스는 윈도우에 맞지 않는 포함된 창을 보기로 스크롤할 수 있는 Windows 페이저 컨트롤을 래핑합니다.

## <a name="syntax"></a>구문

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CPagerCtrl:: CPagerCtrl](#cpagerctrl)|`CPagerCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPagerCtrl:: Create](#create)|지정 된 스타일을 사용 하 여 페이저 컨트롤을 만들고 현재 개체에 연결 `CPagerCtrl` 합니다.|
|[CPagerCtrl:: CreateEx](#createex)|지정 된 확장 스타일을 사용 하 여 페이저 컨트롤을 만들고 현재 개체에 연결 `CPagerCtrl` 합니다.|
|[CPagerCtrl:: ForwardMouse](#forwardmouse)|현재 페이저 컨트롤에 포함 된 창에 대 한 [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) 메시지 전달을 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CPagerCtrl:: GetBkColor](#getbkcolor)|현재 페이저 컨트롤의 배경색을 검색 합니다.|
|[CPagerCtrl:: GetBorder](#getborder)|현재 페이저 컨트롤의 테두리 크기를 검색 합니다.|
|[CPagerCtrl:: GetButtonSize](#getbuttonsize)|현재 페이저 컨트롤의 단추 크기를 검색 합니다.|
|[CPagerCtrl:: GetButtonState](#getbuttonstate)|현재 페이저 컨트롤에서 지정 된 단추의 상태를 검색 합니다.|
|[CPagerCtrl:: GetDropTarget](#getdroptarget)|현재 pager 컨트롤에 대 한 [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) 인터페이스를 검색 합니다.|
|[CPagerCtrl:: GetScrollPos](#getscrollpos)|현재 pager 컨트롤의 스크롤 위치를 검색 합니다.|
|[CPagerCtrl:: IsButtonDepressed](#isbuttondepressed)|현재 페이저 컨트롤의 지정 된 단추가 상태 인지 여부를 나타냅니다 `pressed` .|
|[CPagerCtrl:: IsButtonGrayed](#isbuttongrayed)|현재 페이저 컨트롤의 지정 된 단추가 상태 인지 여부를 나타냅니다 `grayed` .|
|[CPagerCtrl:: IsButtonHot](#isbuttonhot)|현재 페이저 컨트롤의 지정 된 단추가 상태 인지 여부를 나타냅니다 `hot` .|
|[CPagerCtrl:: IsButtonInvisible 않음](#isbuttoninvisible)|현재 페이저 컨트롤의 지정 된 단추가 상태 인지 여부를 나타냅니다 `invisible` .|
|[CPagerCtrl:: IsButtonNormal](#isbuttonnormal)|현재 페이저 컨트롤의 지정 된 단추가 상태 인지 여부를 나타냅니다 `normal` .|
|[CPagerCtrl:: RecalcSize](#recalcsize)|현재 페이저 컨트롤이 포함 된 창의 크기를 다시 계산 하도록 합니다.|
|[CPagerCtrl:: SetBkColor](#setbkcolor)|현재 페이저 컨트롤의 배경색을 설정 합니다.|
|[CPagerCtrl:: SetBorder](#setborder)|현재 페이저 컨트롤의 테두리 크기를 설정 합니다.|
|[CPagerCtrl:: SetButtonSize](#setbuttonsize)|현재 페이저 컨트롤의 단추 크기를 설정 합니다.|
|[CPagerCtrl:: SetChild](#setchild)|현재 페이저 컨트롤에 대 한 포함 된 창을 설정 합니다.|
|[CPagerCtrl:: SetScrollPos](#setscrollpos)|현재 페이저 컨트롤의 스크롤 위치를 설정 합니다.|

## <a name="remarks"></a>설명

페이저 컨트롤은 포함 하는 창 보다 선형이 고 크기가 큰 다른 창을 포함 하는 창으로, 포함 된 창을 뷰로 스크롤할 수 있습니다. 페이저 컨트롤은 포함 된 창이 가장 먼 범위까지 스크롤될 때 자동으로 사라지는 두 개의 스크롤 단추를 표시 하 고, 다른 경우에는 다시 표시 합니다. 가로 또는 세로 방향으로 스크롤 하는 페이저 컨트롤을 만들 수 있습니다.

예를 들어 응용 프로그램에 모든 항목을 표시 하는 데 충분 하지 않은 도구 모음이 있는 경우 도구 모음을 페이저 컨트롤에 할당할 수 있습니다. 그러면 사용자가 도구 모음을 왼쪽 이나 오른쪽으로 스크롤하여 모든 항목에 액세스할 수 있습니다. Microsoft Internet Explorer 버전 4.0 (commctrl.dll 버전 4.71)에는 페이저 컨트롤이 도입 되었습니다.

`CPagerCtrl`클래스는 [CWnd](../../mfc/reference/cwnd-class.md) 클래스에서 파생 됩니다. 페이저 컨트롤에 대 한 자세한 내용 및 설명은 [Pager Controls](/windows/win32/Controls/pager-controls)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="cpagerctrlcpagerctrl"></a><a name="cpagerctrl"></a> CPagerCtrl:: CPagerCtrl

`CPagerCtrl` 개체를 생성합니다.

```
CPagerCtrl();
```

### <a name="remarks"></a>설명

[CPagerCtrl:: Create](#create) 또는 [CPagerCtrl:: createex](#createex) 메서드를 사용 하 여 페이저 컨트롤을 만들고 개체에 연결 `CPagerCtrl` 합니다.

## <a name="cpagerctrlcreate"></a><a name="create"></a> CPagerCtrl:: Create

지정 된 스타일을 사용 하 여 페이저 컨트롤을 만들고 현재 개체에 연결 `CPagerCtrl` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*\
진행 컨트롤에 적용할 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles) 및 [페이저 컨트롤 스타일](/windows/win32/Controls/pager-control-styles) 의 비트 조합 (또는)입니다.

*직교*\
진행 클라이언트 좌표로 나타낸 컨트롤의 위치와 크기를 포함 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*pParentWnd*\
진행 컨트롤의 부모 창인 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 포인터입니다. 이 매개 변수는 NULL일 수 없습니다.

*nID*\
진행 컨트롤의 ID입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

페이저 컨트롤을 만들려면 변수를 선언한 `CPagerCtrl` 다음 해당 변수에 대해 [CPagerCtrl:: Create](#create) 또는 [CPagerCtrl:: createex](#createex) 메서드를 호출 합니다.

### <a name="example"></a>예제

다음 예제에서는 페이저 컨트롤을 만든 다음 [CPagerCtrl:: SetChild](#setchild) 메서드를 사용 하 여 매우 긴 단추 컨트롤과 페이저 컨트롤을 연결 합니다. 그런 다음 [CPagerCtrl:: SetButtonSize](#setbuttonsize) 메서드를 사용 하 여 페이저 컨트롤의 높이를 20 픽셀로 설정 하 고 [CPagerCtrl:: setborder](#setborder) 메서드를 사용 하 여 테두리 두께를 1 픽셀로 설정 합니다.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlcreateex"></a><a name="createex"></a> CPagerCtrl:: CreateEx

지정 된 확장 스타일을 사용 하 여 페이저 컨트롤을 만들고 현재 개체에 연결 `CPagerCtrl` 합니다.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwExStyle*\
진행 컨트롤에 적용할 확장 스타일의 비트 조합입니다. 자세한 내용은 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 함수의 *dwexstyle* 매개 변수를 참조 하세요.

*dwStyle*\
진행 컨트롤에 적용할 [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles) 및 [페이저 컨트롤 스타일](/windows/win32/Controls/pager-control-styles) 의 비트 조합 (또는)입니다.

*직교*\
진행 클라이언트 좌표로 나타낸 컨트롤의 위치와 크기를 포함 하는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조체에 대 한 참조입니다.

*pParentWnd*\
진행 컨트롤의 부모 창인 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 포인터입니다. 이 매개 변수는 NULL일 수 없습니다.

*nID*\
진행 컨트롤의 ID입니다.

### <a name="return-value"></a>반환 값

이 메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

페이저 컨트롤을 만들려면 변수를 선언한 `CPagerCtrl` 다음 해당 변수에 대해 [CPagerCtrl:: Create](#create) 또는 [CPagerCtrl:: createex](#createex) 메서드를 호출 합니다.

## <a name="cpagerctrlforwardmouse"></a><a name="forwardmouse"></a> CPagerCtrl:: ForwardMouse

현재 페이저 컨트롤에 포함 된 창에 대 한 [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) 메시지 전달을 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>매개 변수

*bForward*\
진행 마우스 메시지를 전달 하거나 마우스 메시지를 전달 하지 않으려면 TRUE로 설정 합니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_FORWARDMOUSE](/windows/win32/Controls/pgm-forwardmouse) 메시지를 보냅니다.

## <a name="cpagerctrlgetborder"></a><a name="getborder"></a> CPagerCtrl:: GetBorder

현재 페이저 컨트롤의 테두리 크기를 검색 합니다.

```
int GetBorder() const;
```

### <a name="return-value"></a>반환 값

현재 테두리 크기 (픽셀)입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_GETBORDER](/windows/win32/Controls/pgm-getborder) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 예제에서는 [CPagerCtrl:: GetBorder](#getborder) 메서드를 사용 하 여 페이저 컨트롤 테두리의 두께를 검색 합니다.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

## <a name="cpagerctrlgetbkcolor"></a><a name="getbkcolor"></a> CPagerCtrl:: GetBkColor

현재 페이저 컨트롤의 배경색을 검색 합니다.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>반환 값

페이저 컨트롤의 현재 배경색을 포함 하는 [Colorref](/windows/win32/gdi/colorref) 값입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_GETBKCOLOR](/windows/win32/Controls/pgm-getbkcolor) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 예제에서는 [CPagerCtrl:: SetBkColor](#setbkcolor) 메서드를 사용 하 여 페이저 컨트롤의 배경색을 red로 설정 하 고 [CPagerCtrl:: GetBkColor](#getbkcolor) 메서드를 사용 하 여 변경 내용이 적용 되었는지 확인 합니다.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlgetbuttonsize"></a><a name="getbuttonsize"></a> CPagerCtrl:: GetButtonSize

현재 페이저 컨트롤의 단추 크기를 검색 합니다.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>반환 값

현재 단추 크기 (픽셀)입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_GETBUTTONSIZE](/windows/win32/Controls/pgm-getbuttonsize) 메시지를 보냅니다.

페이저 컨트롤에 PGS_HORZ 스타일이 있으면 단추 크기에서 페이저 단추의 너비를 결정 하 고, 페이저 컨트롤에 PGS_VERT 스타일이 있는 경우 단추 크기에 따라 페이저 단추의 높이가 결정 됩니다. 자세한 내용은 [Pager 컨트롤 스타일](/windows/win32/Controls/pager-control-styles)을 참조 하세요.

## <a name="cpagerctrlgetbuttonstate"></a><a name="getbuttonstate"></a> CPagerCtrl:: GetButtonState

현재 페이저 컨트롤에서 지정 된 스크롤 단추의 상태를 검색 합니다.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>매개 변수

*iButton*\
진행 상태를 검색할 단추를 나타냅니다. 페이저 컨트롤 스타일이 PGS_HORZ 이면 왼쪽 단추에 PGB_TOPORLEFT를 지정 하 고 오른쪽 단추에 PGB_BOTTOMORRIGHT 합니다. 페이저 컨트롤 스타일이 PGS_VERT 경우 맨 위에 있는 단추에 대해 PGB_TOPORLEFT를 지정 하 고 아래쪽 단추에 PGB_BOTTOMORRIGHT 합니다. 자세한 내용은 [Pager 컨트롤 스타일](/windows/win32/Controls/pager-control-styles)을 참조 하세요.

### <a name="return-value"></a>반환 값

*Ibutton* 매개 변수로 지정 된 단추의 상태입니다. 상태는 PGF_INVISIBLE, PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED 또는 PGF_HOT입니다. 자세한 내용은 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 메시지의 반환 값 섹션을 참조 하십시오.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 메시지를 보냅니다.

## <a name="cpagerctrlgetdroptarget"></a><a name="getdroptarget"></a> CPagerCtrl:: GetDropTarget

현재 pager 컨트롤에 대 한 [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) 인터페이스를 검색 합니다.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>반환 값

`IDropTarget`현재 페이저 컨트롤의 인터페이스에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`IDropTarget` 는 응용 프로그램에서 끌어서 놓기 작업을 지원 하기 위해 구현 하는 인터페이스 중 하나입니다.

이 메서드는 Windows SDK에서 설명 하는 [PGM_GETDROPTARGET](/windows/win32/Controls/pgm-getdroptarget) 메시지를 보냅니다. 이 메서드의 호출자는 `Release` 인터페이스가 더 이상 필요 하지 않을 때 [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) 인터페이스의 멤버를 호출 해야 합니다.

## <a name="cpagerctrlgetscrollpos"></a><a name="getscrollpos"></a> CPagerCtrl:: GetScrollPos

현재 pager 컨트롤의 스크롤 위치를 검색 합니다.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>반환 값

현재 스크롤 위치 (픽셀)입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_GETPOS](/windows/win32/Controls/pgm-getpos) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 예제에서는 [CPagerCtrl:: GetScrollPos](#getscrollpos) 메서드를 사용 하 여 페이저 컨트롤의 현재 스크롤 위치를 검색 합니다. 페이저 컨트롤이 이미 0으로 스크롤 되지 않은 경우,이 예제에서는 [CPagerCtrl:: SetScrollPos](#setscrollpos) 메서드를 사용 하 여 스크롤 위치를 0으로 설정 합니다.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

## <a name="cpagerctrlisbuttondepressed"></a><a name="isbuttondepressed"></a> CPagerCtrl:: IsButtonDepressed

현재 페이저 컨트롤의 지정 된 스크롤 단추가 눌린 상태 인지 여부를 나타냅니다.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>매개 변수

*iButton*\
진행 상태를 검색할 단추를 나타냅니다. 페이저 컨트롤 스타일이 PGS_HORZ 이면 왼쪽 단추에 PGB_TOPORLEFT를 지정 하 고 오른쪽 단추에 PGB_BOTTOMORRIGHT 합니다. 페이저 컨트롤 스타일이 PGS_VERT 경우 맨 위에 있는 단추에 대해 PGB_TOPORLEFT를 지정 하 고 아래쪽 단추에 PGB_BOTTOMORRIGHT 합니다. 자세한 내용은 [Pager 컨트롤 스타일](/windows/win32/Controls/pager-control-styles)을 참조 하세요.

### <a name="return-value"></a>반환 값

지정 된 단추가 눌러진 상태 이면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 메시지를 보냅니다. 그런 다음 반환 된 상태가 PGF_DEPRESSED 되는지 테스트 합니다. 자세한 내용은 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 메시지의 반환 값 섹션을 참조 하십시오.

## <a name="cpagerctrlisbuttongrayed"></a><a name="isbuttongrayed"></a> CPagerCtrl:: IsButtonGrayed

현재 페이저 컨트롤의 지정 된 스크롤 단추가 회색 상태 인지 여부를 나타냅니다.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>매개 변수

*iButton*\
진행 상태를 검색할 단추를 나타냅니다. 페이저 컨트롤 스타일이 PGS_HORZ 이면 왼쪽 단추에 PGB_TOPORLEFT를 지정 하 고 오른쪽 단추에 PGB_BOTTOMORRIGHT 합니다. 페이저 컨트롤 스타일이 PGS_VERT 경우 맨 위에 있는 단추에 대해 PGB_TOPORLEFT를 지정 하 고 아래쪽 단추에 PGB_BOTTOMORRIGHT 합니다. 자세한 내용은 [Pager 컨트롤 스타일](/windows/win32/Controls/pager-control-styles)을 참조 하세요.

### <a name="return-value"></a>반환 값

지정 된 단추가 회색 상태 이면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 메시지를 보냅니다. 그런 다음 반환 된 상태가 PGF_GRAYED 되는지 테스트 합니다. 자세한 내용은 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 메시지의 반환 값 섹션을 참조 하십시오.

## <a name="cpagerctrlisbuttonhot"></a><a name="isbuttonhot"></a> CPagerCtrl:: IsButtonHot

현재 페이저 컨트롤의 지정 된 스크롤 단추가 활성 상태 인지 여부를 나타냅니다.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>매개 변수

*iButton*\
진행 상태를 검색할 단추를 나타냅니다. 페이저 컨트롤 스타일이 PGS_HORZ 이면 왼쪽 단추에 PGB_TOPORLEFT를 지정 하 고 오른쪽 단추에 PGB_BOTTOMORRIGHT 합니다. 페이저 컨트롤 스타일이 PGS_VERT 경우 맨 위에 있는 단추에 대해 PGB_TOPORLEFT를 지정 하 고 아래쪽 단추에 PGB_BOTTOMORRIGHT 합니다. 자세한 내용은 [Pager 컨트롤 스타일](/windows/win32/Controls/pager-control-styles)을 참조 하세요.

### <a name="return-value"></a>반환 값

지정 된 단추가 활성 상태 이면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 메시지를 보냅니다. 그런 다음 반환 된 상태가 PGF_HOT 되는지 테스트 합니다. 자세한 내용은 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 메시지의 반환 값 섹션을 참조 하십시오.

## <a name="cpagerctrlisbuttoninvisible"></a><a name="isbuttoninvisible"></a> CPagerCtrl:: IsButtonInvisible 않음

현재 페이저 컨트롤의 지정 된 스크롤 단추가 보이지 않는 상태 인지 여부를 나타냅니다.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>매개 변수

*iButton*\
진행 상태를 검색할 단추를 나타냅니다. 페이저 컨트롤 스타일이 PGS_HORZ 이면 왼쪽 단추에 PGB_TOPORLEFT를 지정 하 고 오른쪽 단추에 PGB_BOTTOMORRIGHT 합니다. 페이저 컨트롤 스타일이 PGS_VERT 경우 맨 위에 있는 단추에 대해 PGB_TOPORLEFT를 지정 하 고 아래쪽 단추에 PGB_BOTTOMORRIGHT 합니다. 자세한 내용은 [Pager 컨트롤 스타일](/windows/win32/Controls/pager-control-styles)을 참조 하세요.

### <a name="return-value"></a>반환 값

지정 된 단추가 보이지 않는 상태 이면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

단추를 클릭 하면 포함 된 창을 더 이상 표시할 수 없기 때문에 Windows에서 특정 방향으로 스크롤 단추를 특정 방향으로 스크롤할 수 있습니다.

이 메서드는 Windows SDK에서 설명 하는 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 메시지를 보냅니다. 그런 다음 반환 된 상태가 PGF_INVISIBLE 되는지 테스트 합니다. 자세한 내용은 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 메시지의 반환 값 섹션을 참조 하십시오.

### <a name="example"></a>예제

다음 예제에서는 [CPagerCtrl:: IsButtonInvisible](#isbuttoninvisible) 메서드를 사용 하 여 페이저 컨트롤의 왼쪽 및 오른쪽 스크롤 단추를 표시할지 여부를 결정 합니다.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

## <a name="cpagerctrlisbuttonnormal"></a><a name="isbuttonnormal"></a> CPagerCtrl:: IsButtonNormal

현재 페이저 컨트롤의 지정 된 스크롤 단추가 표준 상태 인지 여부를 나타냅니다.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>매개 변수

*iButton*\
진행 상태를 검색할 단추를 나타냅니다. 페이저 컨트롤 스타일이 PGS_HORZ 이면 왼쪽 단추에 PGB_TOPORLEFT를 지정 하 고 오른쪽 단추에 PGB_BOTTOMORRIGHT 합니다. 페이저 컨트롤 스타일이 PGS_VERT 경우 맨 위에 있는 단추에 대해 PGB_TOPORLEFT를 지정 하 고 아래쪽 단추에 PGB_BOTTOMORRIGHT 합니다. 자세한 내용은 [Pager 컨트롤 스타일](/windows/win32/Controls/pager-control-styles)을 참조 하세요.

### <a name="return-value"></a>반환 값

지정 된 단추가 표준 상태 이면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 메시지를 보냅니다. 그런 다음 반환 된 상태가 PGF_NORMAL 되는지 테스트 합니다. 자세한 내용은 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 메시지의 반환 값 섹션을 참조 하십시오.

## <a name="cpagerctrlrecalcsize"></a><a name="recalcsize"></a> CPagerCtrl:: RecalcSize

현재 페이저 컨트롤이 포함 된 창의 크기를 다시 계산 하도록 합니다.

```cpp
void RecalcSize();
```

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_RECALCSIZE](/windows/win32/Controls/pgm-recalcsize) 메시지를 보냅니다. 따라서 페이저 컨트롤은 포함 된 창의 스크롤 가능한 크기를 가져오기 위해 [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) 알림을 보냅니다.

### <a name="example"></a>예제

다음 예제에서는 [CPagerCtrl:: RecalcSize](#recalcsize) 메서드를 사용 하 여 현재 페이저 컨트롤의 크기를 다시 계산 하도록 요청 합니다.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>예제

다음 예제에서는 [메시지 리플렉션을](../../mfc/tn062-message-reflection-for-windows-controls.md) 사용 하 여 컨트롤의 부모 대화 상자에서 계산을 수행 하도록 요구 하는 대신 페이저 컨트롤이 자신의 크기를 다시 계산할 수 있도록 합니다. 이 예제에서는 `MyPagerCtrl` [CPagerCtrl 클래스](../../mfc/reference/cpagerctrl-class.md)에서 클래스를 파생 시킨 다음 메시지 맵을 사용 하 여 알림 처리기와 [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) 알림을 연결 합니다 `OnCalcsize` . 이 예제에서 알림 처리기는 페이저 컨트롤의 너비와 높이를 고정 값으로 설정 합니다.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

## <a name="cpagerctrlsetbkcolor"></a><a name="setbkcolor"></a> CPagerCtrl:: SetBkColor

현재 페이저 컨트롤의 배경색을 설정 합니다.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>매개 변수

*clrBk*\
진행 페이저 컨트롤의 새 배경색을 포함 하는 [Colorref](/windows/win32/gdi/colorref) 값입니다.

### <a name="return-value"></a>반환 값

Pager 컨트롤의 이전 배경색을 포함 하는 [Colorref](/windows/win32/gdi/colorref) 값입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_SETBKCOLOR](/windows/win32/Controls/pgm-setbkcolor) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 예제에서는 [CPagerCtrl:: SetBkColor](#setbkcolor) 메서드를 사용 하 여 페이저 컨트롤의 배경색을 red로 설정 하 고 [CPagerCtrl:: GetBkColor](#getbkcolor) 메서드를 사용 하 여 변경 내용이 적용 되었는지 확인 합니다.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlsetborder"></a><a name="setborder"></a> CPagerCtrl:: SetBorder

현재 페이저 컨트롤의 테두리 크기를 설정 합니다.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>매개 변수

*iBorder*\
진행 새 테두리 크기 (픽셀)입니다. *Iborder* 매개 변수가 음수 이면 테두리 크기가 0으로 설정 됩니다.

### <a name="return-value"></a>반환 값

이전 테두리 크기 (픽셀)입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_SETBORDER](/windows/win32/Controls/pgm-setborder) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 예제에서는 페이저 컨트롤을 만든 다음 [CPagerCtrl:: SetChild](#setchild) 메서드를 사용 하 여 매우 긴 단추 컨트롤과 페이저 컨트롤을 연결 합니다. 그런 다음 [CPagerCtrl:: SetButtonSize](#setbuttonsize) 메서드를 사용 하 여 페이저 컨트롤의 높이를 20 픽셀로 설정 하 고 [CPagerCtrl:: setborder](#setborder) 메서드를 사용 하 여 테두리 두께를 1 픽셀로 설정 합니다.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetbuttonsize"></a><a name="setbuttonsize"></a> CPagerCtrl:: SetButtonSize

현재 페이저 컨트롤의 단추 크기를 설정 합니다.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>매개 변수

*iButtonSize*\
진행 새 단추 크기 (픽셀)입니다.

### <a name="return-value"></a>반환 값

이전 단추 크기 (픽셀)입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_SETBUTTONSIZE](/windows/win32/Controls/pgm-setpos) 메시지를 보냅니다.

페이저 컨트롤에 PGS_HORZ 스타일이 있으면 단추 크기에서 페이저 단추의 너비를 결정 하 고, 페이저 컨트롤에 PGS_VERT 스타일이 있는 경우 단추 크기에 따라 페이저 단추의 높이가 결정 됩니다. 기본 단추 크기는 스크롤 막대 너비의 3 3/4, 최소 단추 크기는 12 픽셀입니다. 자세한 내용은 [Pager 컨트롤 스타일](/windows/win32/Controls/pager-control-styles)을 참조 하세요.

### <a name="example"></a>예제

다음 예제에서는 페이저 컨트롤을 만든 다음 [CPagerCtrl:: SetChild](#setchild) 메서드를 사용 하 여 매우 긴 단추 컨트롤과 페이저 컨트롤을 연결 합니다. 그런 다음 [CPagerCtrl:: SetButtonSize](#setbuttonsize) 메서드를 사용 하 여 페이저 컨트롤의 높이를 20 픽셀로 설정 하 고 [CPagerCtrl:: setborder](#setborder) 메서드를 사용 하 여 테두리 두께를 1 픽셀로 설정 합니다.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetchild"></a><a name="setchild"></a> CPagerCtrl:: SetChild

현재 페이저 컨트롤에 대 한 포함 된 창을 설정 합니다.

```cpp
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>매개 변수

*hwndChild*\
진행 포함할 창에 대 한 핸들입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_SETCHILD](/windows/win32/Controls/pgm-setchild) 메시지를 보냅니다.

이 메서드는 포함 된 창의 부모를 변경 하지 않습니다. 스크롤을 위해 페이저 컨트롤에 창 핸들을 할당 합니다. 대부분의 경우 포함 된 창은 페이저 컨트롤의 자식 창이 됩니다.

### <a name="example"></a>예제

다음 예제에서는 페이저 컨트롤을 만든 다음 [CPagerCtrl:: SetChild](#setchild) 메서드를 사용 하 여 매우 긴 단추 컨트롤과 페이저 컨트롤을 연결 합니다. 그런 다음 [CPagerCtrl:: SetButtonSize](#setbuttonsize) 메서드를 사용 하 여 페이저 컨트롤의 높이를 20 픽셀로 설정 하 고 [CPagerCtrl:: setborder](#setborder) 메서드를 사용 하 여 테두리 두께를 1 픽셀로 설정 합니다.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetscrollpos"></a><a name="setscrollpos"></a> CPagerCtrl:: SetScrollPos

현재 페이저 컨트롤의 스크롤 위치를 설정 합니다.

```cpp
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>매개 변수

*iPos*\
진행 새 스크롤 위치 (픽셀)입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [PGM_SETPOS](/windows/win32/Controls/pgm-setpos) 메시지를 보냅니다.

## <a name="see-also"></a>참고 항목

[CPagerCtrl 클래스](../../mfc/reference/cpagerctrl-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[Pager 컨트롤](/windows/win32/Controls/pager-controls)
