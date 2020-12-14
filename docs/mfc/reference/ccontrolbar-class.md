---
description: '자세히 알아보기: CControlBar 클래스'
title: CControlBar Class
ms.date: 11/04/2016
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
helpviewer_keywords:
- CControlBar [MFC], CControlBar
- CControlBar [MFC], CalcDynamicLayout
- CControlBar [MFC], CalcFixedLayout
- CControlBar [MFC], CalcInsideRect
- CControlBar [MFC], DoPaint
- CControlBar [MFC], DrawBorders
- CControlBar [MFC], DrawGripper
- CControlBar [MFC], EnableDocking
- CControlBar [MFC], GetBarStyle
- CControlBar [MFC], GetBorders
- CControlBar [MFC], GetCount
- CControlBar [MFC], GetDockingFrame
- CControlBar [MFC], IsFloating
- CControlBar [MFC], OnUpdateCmdUI
- CControlBar [MFC], SetBarStyle
- CControlBar [MFC], SetBorders
- CControlBar [MFC], SetInPlaceOwner
- CControlBar [MFC], m_bAutoDelete
- CControlBar [MFC], m_pInPlaceOwner
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
ms.openlocfilehash: c18e62c20575e5fe8921c9767099e8069fbcb112
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220476"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

컨트롤 막대 클래스의 기본 클래스 [Cstatusbar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md)및 [COleResizeBar](../../mfc/reference/coleresizebar-class.md)입니다.

## <a name="syntax"></a>구문

```
class CControlBar : public CWnd
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CControlBar:: CControlBar](#ccontrolbar)|`CControlBar` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CControlBar:: CalcDynamicLayout](#calcdynamiclayout)|동적 컨트롤 막대의 크기를 [Csize](../../atl-mfc-shared/reference/csize-class.md) 개체로 반환 합니다.|
|[CControlBar:: CalcFixedLayout](#calcfixedlayout)|컨트롤 막대의 크기를 [Csize](../../atl-mfc-shared/reference/csize-class.md) 개체로 반환 합니다.|
|[CControlBar:: CalcInsideRect](#calcinsiderect)|컨트롤 막대 영역의 현재 크기를 반환 합니다. 테두리를 포함 합니다.|
|[CControlBar::D oPaint](#dopaint)|컨트롤 막대의 테두리와 그리퍼를 렌더링 합니다.|
|[CControlBar::D rawBorders](#drawborders)|컨트롤 막대의 테두리를 렌더링 합니다.|
|[CControlBar::D rawGripper](#drawgripper)|컨트롤 막대의 위치 조정 막대를 렌더링 합니다.|
|[CControlBar:: EnableDocking](#enabledocking)|컨트롤 막대를 도킹 하거나 부동으로 표시할 수 있습니다.|
|[CControlBar:: GetBarStyle](#getbarstyle)|컨트롤 막대 스타일 설정을 검색 합니다.|
|[CControlBar:: GetBorders](#getborders)|컨트롤 막대의 테두리 값을 검색 합니다.|
|[CControlBar:: GetCount](#getcount)|컨트롤 막대의 비-HWND 요소 수를 반환 합니다.|
|[CControlBar:: GetDockingFrame](#getdockingframe)|컨트롤 막대가 도킹 되는 프레임에 대 한 포인터를 반환 합니다.|
|[CControlBar:: IsFloating](#isfloating)|문제가 있는 컨트롤 막대가 부동 컨트롤 막대 이면 0이 아닌 값을 반환 합니다.|
|[CControlBar:: OnUpdateCmdUI](#onupdatecmdui)|명령 UI 처리기를 호출 합니다.|
|[CControlBar:: SetBarStyle](#setbarstyle)|컨트롤 막대 스타일 설정을 수정 합니다.|
|[CControlBar:: SetBorders](#setborders)|컨트롤 막대의 테두리 값을 설정 합니다.|
|[CControlBar:: SetInPlaceOwner](#setinplaceowner)|컨트롤 막대의 현재 위치의 소유자를 변경 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CControlBar:: m_bAutoDelete](#m_bautodelete)|0이 아니면 `CControlBar` Windows 컨트롤 막대가 소멸 될 때 개체가 삭제 됩니다.|
|[CControlBar:: m_pInPlaceOwner](#m_pinplaceowner)|컨트롤 막대의 현재 위치의 소유자입니다.|

## <a name="remarks"></a>설명

컨트롤 막대는 일반적으로 프레임 창의 왼쪽 또는 오른쪽에 정렬 되는 창입니다. Windows 메시지를 생성 하 고 응답 하는 windows 인 HWND 기반 컨트롤과 응용 프로그램 코드 또는 프레임 워크 코드에 의해 관리 되는 비 HWND 기반 항목을 포함할 수 있습니다. 목록 상자와 편집 컨트롤은 HWND 기반 컨트롤의 예입니다. 상태 표시줄 창과 비트맵 단추는 비 HWND 기반 컨트롤의 예입니다.

컨트롤 막대 창은 일반적으로 부모 프레임 창의 자식 창이 며 일반적으로 프레임 창의 클라이언트 뷰 또는 MDI 클라이언트에 대 한 형제입니다. `CControlBar`개체는 부모 창의 클라이언트 사각형에 대 한 정보를 사용 하 여 자신을 배치 합니다. 그런 다음 부모 창에 부모 창 클라이언트 영역에서 할당 되지 않은 공간 크기를 알려 줍니다.

에 대 한 자세한 내용은 `CControlBar` 다음을 참조 하세요.

- [컨트롤 막대](../../mfc/control-bars.md)

- [기술 참고 31: 컨트롤 막대](../../mfc/tn031-control-bars.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>요구 사항

**헤더:** afxext.h

## <a name="ccontrolbarcalcdynamiclayout"></a><a name="calcdynamiclayout"></a> CControlBar:: CalcDynamicLayout

프레임 워크는이 멤버 함수를 호출 하 여 동적 도구 모음의 차원을 계산 합니다.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>매개 변수

*nLength*<br/>
*Dwmode* 에 따라 가로 또는 세로 컨트롤 표시줄의 요청 된 차원입니다.

*nMode*<br/>
다음 미리 정의 된 플래그는 동적 컨트롤 막대의 높이와 너비를 결정 하는 데 사용 됩니다. 비트 or (&#124;) 연산자를 사용 하 여 플래그를 결합할 수 있습니다.

|레이아웃 모드 플래그|의미|
|-----------------------|-------------------|
|LM_STRETCH|컨트롤 막대를 프레임 크기로 늘일 지 여부를 나타냅니다. 막대가 도킹 막대가 아닌 경우를 설정 합니다 (도킹에 사용할 수 없음). 막대가 도킹 되거나 부동 (도킹에 사용 가능) 인 경우에는 설정 되지 않습니다. 설정 하는 경우 LM_STRETCH *Nlength* 를 무시 하 고 LM_HORZ 상태를 기준으로 차원을 반환 합니다. LM_STRETCH는 [CalcFixedLayout](#calcfixedlayout)에서 사용 되는 *bstretch* 매개 변수와 유사 하 게 작동 합니다. 스트레치와 방향 간의 관계에 대 한 자세한 내용은 해당 멤버 함수를 참조 하세요.|
|LM_HORZ|가로 또는 세로 방향으로 막대를 나타냅니다. 가로 막대의 가로 방향으로 설정 하 고 세로 방향인 경우에는 설정 되지 않습니다. LM_HORZ는 [CalcFixedLayout](#calcfixedlayout)에서 사용 되는 *bhorz* 매개 변수와 유사 하 게 작동 합니다. 스트레치와 방향 간의 관계에 대 한 자세한 내용은 해당 멤버 함수를 참조 하세요.|
|LM_MRUWIDTH|가장 최근에 사용한 동적 너비입니다. *Nlength* 매개 변수를 무시 하 고 가장 최근에 사용 된 저장 된 너비를 사용 합니다.|
|LM_HORZDOCK|가로로 도킹 된 차원입니다. *Nlength* 매개 변수를 무시 하 고 너비가 가장 큰 동적 크기를 반환 합니다.|
|LM_VERTDOCK|세로로 도킹 된 차원입니다. *Nlength* 매개 변수를 무시 하 고 높이가 가장 큰 동적 크기를 반환 합니다.|
|LM_LENGTHY|*Nlength* 가 너비 대신 높이 (Y 방향)를 나타내는 경우에 설정 합니다.|
|LM_COMMIT|LM_MRUWIDTH를 부동 컨트롤 막대의 현재 너비로 다시 설정 합니다.|

### <a name="return-value"></a>반환 값

[Csize](../../atl-mfc-shared/reference/csize-class.md) 개체의 컨트롤 막대 크기 (픽셀)입니다.

### <a name="remarks"></a>설명

파생 하는 클래스에서 고유한 동적 레이아웃을 제공 하려면이 멤버 함수를 재정의 `CControlBar` 합니다. CToolbar와 같이에서 파생 된 MFC 클래스는 `CControlBar` 이 멤버 함수를 재정의 하 고 자체 구현을 제공 합니다. [](../../mfc/reference/ctoolbar-class.md)

## <a name="ccontrolbarcalcfixedlayout"></a><a name="calcfixedlayout"></a> CControlBar:: CalcFixedLayout

이 멤버 함수를 호출 하 여 컨트롤 막대의 가로 크기를 계산 합니다.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>매개 변수

*bStretch*<br/>
프레임 크기까지 막대를 늘일 지 여부를 나타냅니다. 막대가 도킹 막대가 아닌 경우 (도킹에 사용할 수 없음) *Bstretch* 매개 변수는 0이 아니며 도킹 되거나 부동 (도킹에 사용 가능) 인 경우 0입니다.

*bHorz*<br/>
가로 또는 세로 방향으로 막대를 나타냅니다. 막대가 가로 방향인 경우 *Bhorz* 매개 변수는 0이 아니고 세로 방향인 경우 0입니다.

### <a name="return-value"></a>반환 값

개체의 컨트롤 막대 크기 (픽셀) `CSize` 입니다.

### <a name="remarks"></a>설명

도구 모음과 같은 컨트롤 막대는 가로 또는 세로로 확장 되어 컨트롤 막대에 포함 된 단추를 수용할 수 있습니다.

*Bstretch* 가 TRUE 이면 *bstretch* 에서 제공 하는 방향에 따라 차원을 늘립니다. 즉, *Bhorz* 이 FALSE 인 경우 컨트롤 막대는 세로로 늘어납니다. *Bstretch* 가 FALSE 이면 스트레치가 발생 하지 않습니다. 다음 표에서는 *Bstretch* 및 *bstretch* 의 가능한 순열 및 결과 컨트롤 막대 스타일을 보여 줍니다.

|bStretch|bHorz|확장|방향|도킹/도킹 안 함|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|수평 확장|가로 방향|도킹 안 함|
|TRUE|FALSE|수직 확장|세로 방향|도킹 안 함|
|FALSE|TRUE|스트레치 사용 안 함|가로 방향|도킹|
|FALSE|FALSE|스트레치 사용 안 함|세로 방향|도킹|

## <a name="ccontrolbarcalcinsiderect"></a><a name="calcinsiderect"></a> CControlBar:: CalcInsideRect

프레임 워크는이 함수를 호출 하 여 컨트롤 막대의 클라이언트 영역을 계산 합니다.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
컨트롤 막대의 현재 크기를 포함 합니다. 테두리를 포함 합니다.

*bHorz*<br/>
가로 또는 세로 방향으로 막대를 나타냅니다. 막대가 가로 방향인 경우 *Bhorz* 매개 변수는 0이 아니고 세로 방향인 경우 0입니다.

### <a name="remarks"></a>설명

이 함수는 컨트롤 막대를 그리기 전에 호출 됩니다.

이 함수를 재정의 하 여 컨트롤 막대의 테두리와 그리퍼 막대의 렌더링을 사용자 지정 합니다.

## <a name="ccontrolbarccontrolbar"></a><a name="ccontrolbar"></a> CControlBar:: CControlBar

`CControlBar` 개체를 생성합니다.

```
CControlBar();
```

## <a name="ccontrolbardopaint"></a><a name="dopaint"></a> CControlBar::D oPaint

컨트롤 막대의 테두리와 그리퍼 막대를 렌더링 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
컨트롤 막대의 테두리와 그리퍼를 렌더링 하는 데 사용할 장치 컨텍스트를 가리킵니다.

### <a name="remarks"></a>설명

이 함수를 재정의 하 여 컨트롤 막대의 그리기 동작을 사용자 지정 합니다.

또 다른 사용자 지정 방법은 및 함수를 재정의 하 `DrawBorders` `DrawGripper` 고 테두리 및 위치 조정 막대에 대 한 사용자 지정 그리기 코드를 추가 하는 것입니다. 이러한 메서드는 기본 메서드에 의해 호출 되므로 `DoPaint` 재정의는 `DoPaint` 필요 하지 않습니다.

## <a name="ccontrolbardrawborders"></a><a name="drawborders"></a> CControlBar::D rawBorders

컨트롤 막대의 테두리를 렌더링 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
컨트롤 막대의 테두리를 렌더링 하는 데 사용할 장치 컨텍스트를 가리킵니다.

*rect*<br/>
`CRect`컨트롤 막대의 크기를 포함 하는 개체입니다.

### <a name="remarks"></a>설명

이 함수를 재정의 하 여 컨트롤 막대 테두리의 모양을 사용자 지정 합니다.

## <a name="ccontrolbardrawgripper"></a><a name="drawgripper"></a> CControlBar::D rawGripper

컨트롤 막대의 위치 조정 막대를 렌더링 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
컨트롤 막대 그리퍼를 렌더링 하는 데 사용할 장치 컨텍스트를 가리킵니다.

*rect*<br/>
`CRect`컨트롤 막대 위치 조정 막대의 크기를 포함 하는 개체입니다.

### <a name="remarks"></a>설명

이 함수를 재정의 하 여 컨트롤 막대 그리퍼의 모양을 사용자 지정 합니다.

## <a name="ccontrolbarenabledocking"></a><a name="enabledocking"></a> CControlBar:: EnableDocking

컨트롤 막대를 도킹할 수 있도록 하려면이 함수를 호출 합니다.

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>매개 변수

*dwDockStyle*<br/>
지원 되는 경우 컨트롤 막대를 도킹할 수 있는 컨트롤 막대를 도킹할 수 있는지 여부를 지정 합니다. 다음 중 하나 이상이 될 수 있습니다.

- CBRS_ALIGN_TOP 클라이언트 영역의 맨 위에 도킹을 허용 합니다.

- 클라이언트 영역의 아래쪽에 도킹을 허용 CBRS_ALIGN_BOTTOM.

- CBRS_ALIGN_LEFT 클라이언트 영역의 왼쪽에 도킹할 수 있습니다.

- CBRS_ALIGN_RIGHT 클라이언트 영역의 오른쪽에 도킹할 수 있습니다.

- CBRS_ALIGN_ANY은 클라이언트 영역의 어느 쪽에 나 도킹할 수 있습니다.

- CBRS_FLOAT_MULTI를 사용 하면 단일 미니 프레임 창에서 여러 컨트롤 막대를 부동으로 표시할 수 있습니다.

0 (즉, 플래그가 없음을 나타냄) 인 경우에는 컨트롤 막대가 도킹 되지 않습니다.

### <a name="remarks"></a>설명

지정 된 면은 대상 프레임 창에서 도킹에 사용할 수 있는 면 중 하 나와 일치 해야 합니다. 그렇지 않으면 해당 프레임 창에 컨트롤 막대를 도킹할 수 없습니다.

## <a name="ccontrolbargetbarstyle"></a><a name="getbarstyle"></a> CControlBar:: GetBarStyle

이 함수를 호출 하 여 현재 컨트롤 막대에 대해 설정 된 **CBRS_** (컨트롤 막대 스타일) 설정을 확인 합니다.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>반환 값

컨트롤 막대에 대 한 현재 **CBRS_** (컨트롤 막대 스타일) 설정입니다. 사용 가능한 스타일의 전체 목록은 [Ccontrolbar:: Setbar style](#setbarstyle) 을 참조 하세요.

### <a name="remarks"></a>설명

**WS_** (창 스타일) 스타일을 처리 하지 않습니다.

## <a name="ccontrolbargetborders"></a><a name="getborders"></a> CControlBar:: GetBorders

컨트롤 막대에 대 한 현재 테두리 값을 반환 합니다.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>반환 값

`CRect`컨트롤 막대 개체의 각 면에 대 한 현재 너비 (픽셀 단위)를 포함 하는 개체입니다. 예를 들어, [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체의 *왼쪽* 멤버 값은 왼쪽 테두리의 너비입니다.

## <a name="ccontrolbargetcount"></a><a name="getcount"></a> CControlBar:: GetCount

개체의 비 HWND 항목 수를 반환 합니다 `CControlBar` .

```
int GetCount() const;
```

### <a name="return-value"></a>반환 값

개체의 비 HWND 항목 수입니다 `CControlBar` . 이 함수는 [CDialogBar](../../mfc/reference/cdialogbar-class.md) 개체에 대해 0을 반환 합니다.

### <a name="remarks"></a>설명

항목의 형식은 파생 개체 ( [Cstatusbar](../../mfc/reference/cstatusbar-class.md) 개체의 경우) 및 [CToolBar](../../mfc/reference/ctoolbar-class.md) 개체의 단추와 구분 기호에 따라 달라 집니다.

## <a name="ccontrolbargetdockingframe"></a><a name="getdockingframe"></a> CControlBar:: GetDockingFrame

이 멤버 함수를 호출 하 여 컨트롤 막대가 도킹 된 현재 프레임 창에 대 한 포인터를 가져옵니다.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>반환 값

성공 하면 프레임 창에 대 한 포인터입니다. 그렇지 않으면 NULL입니다.

컨트롤 막대가 프레임 창에 도킹 되지 않은 경우 (즉, 컨트롤 막대가 부동 인 경우)이 함수는 부모 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)에 대 한 포인터를 반환 합니다.

### <a name="remarks"></a>설명

도킹 가능한 컨트롤 막대에 대 한 자세한 내용은 [Ccontrolbar:: EnableDocking](#enabledocking) and [CFrameWnd::D ockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar)를 참조 하세요.

## <a name="ccontrolbarisfloating"></a><a name="isfloating"></a> CControlBar:: IsFloating

이 멤버 함수를 호출 하 여 컨트롤 막대의 부동 또는 도킹 여부를 확인 합니다.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>반환 값

컨트롤 막대가 부동 인 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

컨트롤 막대의 상태를 도킹에서 부동으로 변경 하려면 [CFrameWnd:: FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar)를 호출 합니다.

## <a name="ccontrolbarm_bautodelete"></a><a name="m_bautodelete"></a> CControlBar:: m_bAutoDelete

0이 아니면 `CControlBar` Windows 컨트롤 막대가 소멸 될 때 개체가 삭제 됩니다.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>설명

*m_bAutoDelete* 은 BOOL 형식의 공용 변수입니다.

컨트롤 막대 개체는 일반적으로 프레임 창 개체에 포함 되어 있습니다. 이 경우 프레임 창이 제거 될 때 포함 된 컨트롤 막대 개체가 제거 되므로 *m_bAutoDelete* 은 0입니다.

힙에 개체를 할당 하 고를 호출할 계획이 없는 경우이 변수를 0이 아닌 값으로 설정 `CControlBar` **`delete`** 합니다.

## <a name="ccontrolbarm_pinplaceowner"></a><a name="m_pinplaceowner"></a> CControlBar:: m_pInPlaceOwner

컨트롤 막대의 현재 위치의 소유자입니다.

```
CWnd* m_pInPlaceOwner;
```

## <a name="ccontrolbaronupdatecmdui"></a><a name="onupdatecmdui"></a> CControlBar:: OnUpdateCmdUI

이 멤버 함수는 도구 모음 또는 상태 표시줄의 상태를 업데이트 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>매개 변수

*pTarget*<br/>
응용 프로그램의 주 프레임 창을 가리킵니다. 이 포인터는 업데이트 메시지를 라우팅하는 데 사용 됩니다.

*bDisableIfNoHndler*<br/>
업데이트 처리기가 없는 컨트롤을 자동으로 비활성으로 표시할지 여부를 나타내는 플래그입니다.

### <a name="remarks"></a>설명

개별 단추나 창을 업데이트 하려면 메시지 맵의 ON_UPDATE_COMMAND_UI 매크로를 사용 하 여 업데이트 처리기를 적절 하 게 설정 합니다. 이 매크로 사용에 대 한 자세한 내용은 [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) 를 참조 하십시오.

`OnUpdateCmdUI` 응용 프로그램이 유휴 상태일 때 프레임 워크에서 호출 됩니다. 업데이트할 프레임 창은 표시 되는 프레임 창의 자식 창 (최소한 간접적) 이어야 합니다. `OnUpdateCmdUI` 은 (는) 고급 재정의 가능입니다.

## <a name="ccontrolbarsetbarstyle"></a><a name="setbarstyle"></a> CControlBar:: SetBarStyle

컨트롤 막대의 원하는 **CBRS_** 스타일을 설정 하려면이 함수를 호출 합니다.

```cpp
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
컨트롤 막대의 원하는 스타일입니다. 다음 중 하나 이상이 될 수 있습니다.

- CBRS_ALIGN_TOP를 사용 하면 컨트롤 막대를 프레임 창의 클라이언트 영역 맨 위에 도킹할 수 있습니다.

- CBRS_ALIGN_BOTTOM를 사용 하면 컨트롤 막대를 프레임 창의 클라이언트 영역 아래쪽에 도킹할 수 있습니다.

- CBRS_ALIGN_LEFT를 사용 하면 컨트롤 막대를 프레임 창의 클라이언트 영역 왼쪽에 도킹할 수 있습니다.

- CBRS_ALIGN_RIGHT를 사용 하면 컨트롤 막대를 프레임 창의 클라이언트 영역 오른쪽에 도킹할 수 있습니다.

- CBRS_ALIGN_ANY를 사용 하면 컨트롤 막대를 프레임 창의 클라이언트 영역에 도킹할 수 있습니다.

- CBRS_BORDER_TOP 표시 될 때 컨트롤 막대의 위쪽 가장자리에 테두리를 그립니다.

- CBRS_BORDER_BOTTOM 표시 될 때 컨트롤 막대의 아래쪽 가장자리에 테두리를 그립니다.

- CBRS_BORDER_LEFT 표시 될 때 컨트롤 막대의 왼쪽 가장자리에 테두리를 그립니다.

- CBRS_BORDER_RIGHT 표시 될 때 컨트롤 막대의 오른쪽 가장자리에 테두리를 그립니다.

- CBRS_FLOAT_MULTI를 사용 하면 단일 미니 프레임 창에서 여러 컨트롤 막대를 부동으로 표시할 수 있습니다.

- CBRS_TOOLTIPS 컨트롤 막대에 대 한 도구 설명이 표시 됩니다.

- CBRS_FLYBY 하면 메시지 텍스트가 도구 설명과 동시에 업데이트 됩니다.

- CBRS_GRIPPER를 사용 하면 개체의 밴드에서 사용 되는 것과 비슷한 그리퍼가 `CReBar` 파생 클래스에 대해 그려집니다 `CControlBar` .

### <a name="remarks"></a>설명

**WS_** (창 스타일) 설정에 영향을 주지 않습니다.

## <a name="ccontrolbarsetborders"></a><a name="setborders"></a> CControlBar:: SetBorders

컨트롤 막대 테두리의 크기를 설정 하려면이 함수를 호출 합니다.

```cpp
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>매개 변수

*cxLeft*<br/>
컨트롤 막대의 왼쪽 테두리 너비 (픽셀)입니다.

*cyTop*<br/>
컨트롤 막대의 위쪽 테두리의 높이 (픽셀)입니다.

*cxRight*<br/>
컨트롤 막대의 오른쪽 테두리 너비 (픽셀)입니다.

*cyBottom*<br/>
컨트롤 막대 아래쪽 테두리의 높이 (픽셀)입니다.

*lpRect*<br/>
컨트롤 막대 개체에 대 한 각 테두리의 현재 너비 (픽셀 단위)를 포함 하는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체에 대 한 포인터입니다.

### <a name="example"></a>예제

다음 코드 예제에서는 컨트롤 막대의 위쪽 및 아래쪽 테두리를 5 픽셀, 왼쪽 및 오른쪽 테두리를 2 픽셀로 설정 합니다.

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

## <a name="ccontrolbarsetinplaceowner"></a><a name="setinplaceowner"></a> CControlBar:: SetInPlaceOwner

컨트롤 막대의 현재 위치의 소유자를 변경 합니다.

```cpp
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
`CWnd` 개체에 대한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[MFC 샘플 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 클래스](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar 클래스](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar 클래스](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar 클래스](../../mfc/reference/crebar-class.md)
