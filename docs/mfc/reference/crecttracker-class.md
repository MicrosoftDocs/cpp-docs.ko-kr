---
description: '자세히 알아보기: CRectTracker 클래스'
title: CRectTracker 클래스
ms.date: 11/19/2018
f1_keywords:
- CRectTracker
- AFXEXT/CRectTracker
- AFXEXT/CRectTracker::CRectTracker
- AFXEXT/CRectTracker::AdjustRect
- AFXEXT/CRectTracker::Draw
- AFXEXT/CRectTracker::DrawTrackerRect
- AFXEXT/CRectTracker::GetHandleMask
- AFXEXT/CRectTracker::GetTrueRect
- AFXEXT/CRectTracker::HitTest
- AFXEXT/CRectTracker::NormalizeHit
- AFXEXT/CRectTracker::OnChangedRect
- AFXEXT/CRectTracker::SetCursor
- AFXEXT/CRectTracker::Track
- AFXEXT/CRectTracker::TrackRubberBand
- AFXEXT/CRectTracker::m_nHandleSize
- AFXEXT/CRectTracker::m_nStyle
- AFXEXT/CRectTracker::m_rect
- AFXEXT/CRectTracker::m_sizeMin
helpviewer_keywords:
- CRectTracker [MFC], CRectTracker
- CRectTracker [MFC], AdjustRect
- CRectTracker [MFC], Draw
- CRectTracker [MFC], DrawTrackerRect
- CRectTracker [MFC], GetHandleMask
- CRectTracker [MFC], GetTrueRect
- CRectTracker [MFC], HitTest
- CRectTracker [MFC], NormalizeHit
- CRectTracker [MFC], OnChangedRect
- CRectTracker [MFC], SetCursor
- CRectTracker [MFC], Track
- CRectTracker [MFC], TrackRubberBand
- CRectTracker [MFC], m_nHandleSize
- CRectTracker [MFC], m_nStyle
- CRectTracker [MFC], m_rect
- CRectTracker [MFC], m_sizeMin
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
ms.openlocfilehash: 8406b6b45a99ca2e1816cb650f243fcea2db8ddc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343022"
---
# <a name="crecttracker-class"></a>CRectTracker 클래스

항목을 다른 fashions 표시, 이동 및 크기 조정할 수 있습니다.

## <a name="syntax"></a>구문

```
class CRectTracker
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CRectTracker:: CRectTracker](#crecttracker)|`CRectTracker` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRectTracker:: AdjustRect](#adjustrect)|사각형의 크기를 조정할 때 호출 됩니다.|
|[CRectTracker: 원시:D](#draw)|사각형을 렌더링 합니다.|
|[CRectTracker::D rawTrackerRect](#drawtrackerrect)|개체의 테두리를 그릴 때 호출 `CRectTracker` 됩니다.|
|[CRectTracker:: GetHandleMask](#gethandlemask)|항목의 크기 조정 핸들의 마스크를 가져오기 위해 호출 `CRectTracker` 됩니다.|
|[CRectTracker:: GetTrueRect](#gettruerect)|크기 조정 핸들을 포함 하 여 사각형의 너비와 높이를 반환 합니다.|
|[CRectTracker:: System.windows.media.visualtreehelper.hittest](#hittest)|개체와 관련 된 커서의 현재 위치를 반환 합니다 `CRectTracker` .|
|[CRectTracker:: NormalizeHit](#normalizehit)|적중 테스트 코드를 정규화 합니다.|
|[CRectTracker:: OnChangedRect](#onchangedrect)|사각형의 크기를 조정 하거나 이동 하면 호출 됩니다.|
|[CRectTracker:: SetCursor](#setcursor)|사각형의 위치에 따라 커서를 설정 합니다.|
|[CRectTracker:: Track](#track)|사용자가 사각형을 조작할 수 있도록 합니다.|
|[CRectTracker::](#trackrubberband)|사용자가 선택 항목을 "고무 밴드" 할 수 있습니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CRectTracker:: m_nHandleSize](#m_nhandlesize)|크기 조정 핸들의 크기를 결정 합니다.|
|[CRectTracker:: m_nStyle](#m_nstyle)|추적기의 현재 스타일입니다.|
|[CRectTracker:: m_rect](#m_rect)|사각형의 현재 위치 (픽셀)입니다.|
|[CRectTracker:: m_sizeMin](#m_sizemin)|최소 사각형 너비와 높이를 결정 합니다.|

## <a name="remarks"></a>설명

`CRectTracker` 에 기본 클래스가 없습니다.

클래스는 `CRectTracker` 사용자가 그래픽 인터페이스를 사용 하 여 ole 항목을 조작할 수 있도록 설계 되었지만 ole 사용 응용 프로그램에 대해서는 사용할 수 없습니다. 사용자 인터페이스가 필요한 모든 위치에서 사용할 수 있습니다.

`CRectTracker` 테두리는 실선 또는 점선이 될 수 있습니다. 항목에 서로 다른 상태를 나타내기 위해 해치 테두리를 지정 하거나 해치 패턴으로 중첩 시킬 수 있습니다. 항목의 외부 또는 내부 테두리에 8 개의 크기 조정 핸들을 둘 수 있습니다. 크기 조정 핸들에 대 한 설명은 [GetHandleMask](#gethandlemask)를 참조 하세요. 마지막으로,를 `CRectTracker` 사용 하면 크기를 조정 하는 동안 항목의 방향을 변경할 수 있습니다.

를 사용 하려면 `CRectTracker` 개체를 생성 하 `CRectTracker` 고 초기화 되는 표시 상태를 지정 합니다. 그런 다음이 인터페이스를 사용 하 여 개체와 연결 된 OLE 항목의 현재 상태에 대 한 사용자의 시각적 피드백을 제공할 수 있습니다 `CRectTracker` .

사용에 대 한 자세한 내용은 `CRectTracker` [추적기](../../mfc/trackers.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CRectTracker`

## <a name="requirements"></a>요구 사항

**헤더:** afxext.h

## <a name="crecttrackeradjustrect"></a><a name="adjustrect"></a> CRectTracker:: AdjustRect

크기 조정 핸들을 사용 하 여 추적 사각형의 크기를 조정할 때 프레임 워크에서 호출 됩니다.

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>매개 변수

*nHandle*<br/>
사용 된 핸들의 인덱스입니다.

*lpRect*<br/>
사각형의 현재 크기에 대 한 포인터입니다. 사각형의 크기는 높이와 너비를 기준으로 지정 됩니다.

### <a name="remarks"></a>설명

이 함수의 기본 동작을 사용 하면 `Track` 및 `TrackRubberBand` 가 반전 허용으로 호출 되는 경우에만 사각형의 방향이 변경 됩니다.

끌기 작업 중에 추적 사각형의 조정을 제어 하려면이 함수를 재정의 합니다. 한 가지 방법은를 반환 하기 전에 *lpRect* 에 의해 지정 된 좌표를 조정 하는 것입니다.

이 함수를 재정의 하 여에서 직접 지원 하지 않는 특별 한 기능 ( `CRectTracker` 예: 그리드에 맞추기 또는 유지 비율 유지)을 구현할 수 있습니다.

## <a name="crecttrackercrecttracker"></a><a name="crecttracker"></a> CRectTracker:: CRectTracker

`CRectTracker` 개체를 만들어 초기화합니다.

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>매개 변수

*lpSrcRect*<br/>
사각형 개체의 좌표입니다.

*nStyle*<br/>
개체의 스타일을 지정 합니다 `CRectTracker` . 지원되는 스타일은 다음과 같습니다.

- `CRectTracker::solidLine` 사각형 테두리에 실선을 사용 합니다.

- `CRectTracker::dottedLine` 사각형 테두리에 점선을 사용 합니다.

- `CRectTracker::hatchedBorder` 사각형 테두리에 빗살 무늬 패턴을 사용 합니다.

- `CRectTracker::resizeInside` 사각형 안에 있는 크기 조정 핸들입니다.

- `CRectTracker::resizeOutside` 사각형의 외부에 있는 크기 조정 핸들입니다.

- `CRectTracker::hatchInside` 빗살 무늬 패턴은 전체 사각형을 포함 합니다.

### <a name="remarks"></a>설명

기본 생성자는 `CRectTracker` *lpSrcRect* 의 값을 사용 하 여 개체를 초기화 하 고 다른 크기를 시스템 기본값으로 초기화 합니다. 매개 변수 없이 개체를 만드는 경우 `m_rect` 및 `m_nStyle` 데이터 멤버가 초기화 되지 않습니다.

## <a name="crecttrackerdraw"></a><a name="draw"></a> CRectTracker: 원시:D

사각형의 외부 선 및 내부 영역을 그리려면이 함수를 호출 합니다.

```cpp
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
그릴 장치 컨텍스트에 대 한 포인터입니다.

### <a name="remarks"></a>설명

추적기 스타일에 따라 그리기를 수행 하는 방법이 결정 됩니다. `CRectTracker`사용 가능한 스타일에 대 한 자세한 내용은 생성자를 참조 하십시오.

## <a name="crecttrackerdrawtrackerrect"></a><a name="drawtrackerrect"></a> CRectTracker::D rawTrackerRect

또는 멤버 함수 내에서 추적기 위치가 변경 될 때마다 프레임 워크에서 호출 `Track` `TrackRubberBand` 됩니다.

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*lpRect*<br/>
`RECT`그릴 사각형을 포함 하는에 대 한 포인터입니다.

*pWndClipTo*<br/>
사각형을 클리핑 하는 데 사용할 창에 대 한 포인터입니다.

*컨트롤러가*<br/>
그릴 장치 컨텍스트에 대 한 포인터입니다.

*pWnd*<br/>
그리기가 발생 되는 창에 대 한 포인터입니다.

### <a name="remarks"></a>설명

기본 구현에서는를 호출 하 여 `CDC::DrawFocusRect` 점선 사각형을 그립니다.

추적 작업을 수행 하는 동안 다른 피드백을 제공 하려면이 함수를 재정의 합니다.

## <a name="crecttrackergethandlemask"></a><a name="gethandlemask"></a> CRectTracker:: GetHandleMask

프레임 워크는이 멤버 함수를 호출 하 여 사각형의 크기 조정 핸들에 대 한 마스크를 검색 합니다.

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>반환 값

`CRectTracker`항목 크기 조정 핸들의 마스크입니다.

### <a name="remarks"></a>설명

크기 조정 핸들은 사각형의 면과 모퉁이에 표시 되며 사용자가 사각형의 모양과 크기를 제어할 수 있습니다.

사각형의 크기를 조정 하는 8 개의 크기 조정 핸들이 0-7입니다. 각 크기 조정 핸들은 마스크에서 비트로 표시 됩니다. 해당 비트의 값은 2 ^ *n* 입니다. 여기서 *n* 은 크기 조정 핸들 번호입니다. 비트 0-3는 왼쪽 위에서 시계 방향으로 시작 하 여 모퉁이 크기 조정 핸들에 해당 합니다. 비트 4-7는 위쪽으로 이동 하는 위쪽에서 시작 하는 측면 크기 조정 핸들에 해당 합니다. 다음 그림에서는 사각형의 크기 조정 핸들 및 해당 크기 조정 핸들 번호와 값을 보여 줍니다.

![크기 조정 핸들 번호](../../mfc/reference/media/vc35dp1.gif "크기 조정 핸들 번호")

의 기본 구현은 `GetHandleMask` 크기 조정 핸들이 나타나도록 비트 마스크를 반환 합니다. 단일 비트가 설정 되어 있으면 해당 크기 조정 핸들이 그려집니다.

표시 된 크기 조정 핸들을 숨기 거 나 표시 하려면이 멤버 함수를 재정의 합니다.

## <a name="crecttrackergettruerect"></a><a name="gettruerect"></a> CRectTracker:: GetTrueRect

사각형의 좌표를 검색 하려면이 함수를 호출 합니다.

```cpp
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>매개 변수

*lpTrueRect*<br/>
`RECT`개체의 장치 좌표를 포함 하는 구조에 대 한 포인터 `CRectTracker` 입니다.

### <a name="remarks"></a>설명

사각형의 크기는 바깥쪽 테두리에 있는 크기 조정 핸들의 높이와 너비를 포함 합니다. 반환 시 *lpTrueRect* 는 항상 장치 좌표의 정규화 된 사각형입니다.

## <a name="crecttrackerhittest"></a><a name="hittest"></a> CRectTracker:: System.windows.media.visualtreehelper.hittest

사용자가 크기 조정 핸들을 grabbed 여부를 확인 하려면이 함수를 호출 합니다.

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>매개 변수

*까지*<br/>
테스트할 지점 (장치 좌표)입니다.

### <a name="return-value"></a>반환 값

반환 되는 값은 열거 형식을 기반으로 `CRectTracker::TrackerHit` 하며 다음 값 중 하나를 사용할 수 있습니다.

- `CRectTracker::hitNothing` -1

- `CRectTracker::hitTopLeft` 0

- `CRectTracker::hitTopRight` 1(sp1)

- `CRectTracker::hitBottomRight` sr-2

- `CRectTracker::hitBottomLeft` 3

- `CRectTracker::hitTop` 4

- `CRectTracker::hitRight` 5

- `CRectTracker::hitBottom` 6@@

- `CRectTracker::hitLeft` 일

- `CRectTracker::hitMiddle` 20cm(8

## <a name="crecttrackerm_nhandlesize"></a><a name="m_nhandlesize"></a> CRectTracker:: m_nHandleSize

크기 조정 핸들의 크기 (픽셀)입니다 `CRectTracker` .

```
int m_nHandleSize;
```

### <a name="remarks"></a>설명

기본 시스템 값으로 초기화 됩니다.

## <a name="crecttrackerm_rect"></a><a name="m_rect"></a> CRectTracker:: m_rect

클라이언트 좌표에서 사각형의 현재 위치 (픽셀)입니다.

```
CRect m_rect;
```

## <a name="crecttrackerm_sizemin"></a><a name="m_sizemin"></a> CRectTracker:: m_sizeMin

사각형의 최소 크기입니다.

```
CSize m_sizeMin;
```

### <a name="remarks"></a>설명

기본값와는 모두 `cx` `cy` 테두리 너비에 대 한 기본 시스템 값에서 계산 됩니다. 이 데이터 멤버는 멤버 함수 에서만 사용 됩니다 `AdjustRect` .

## <a name="crecttrackerm_nstyle"></a><a name="m_nstyle"></a> CRectTracker:: m_nStyle

사각형의 현재 스타일입니다.

```
UINT m_nStyle;
```

### <a name="remarks"></a>설명

가능한 스타일 목록은 [CRectTracker:: CRectTracker](#crecttracker) 를 참조 하세요.

## <a name="crecttrackernormalizehit"></a><a name="normalizehit"></a> CRectTracker:: NormalizeHit

잠재적으로 반전 된 핸들을 변환 하려면이 함수를 호출 합니다.

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>매개 변수

*nHandle*<br/>
사용자가 선택한 핸들입니다.

### <a name="return-value"></a>반환 값

정규화 된 핸들의 인덱스입니다.

### <a name="remarks"></a>설명

을 `CRectTracker::Track` `CRectTracker::TrackRubberBand` 사용 하 여 또는가 호출 되 면 사각형은 x 축, y 축 또는 둘 다에서 반전 될 수 있습니다. 이 경우 `HitTest` 는 사각형을 기준으로도 반전 된 핸들을 반환 합니다. 피드백은 수정할 사각형 데이터 구조의 일부가 아니라 사각형의 화면 위치에 따라 달라 지므로 커서 피드백 그리기에는 적합 하지 않습니다.

## <a name="crecttrackeronchangedrect"></a><a name="onchangedrect"></a> CRectTracker:: OnChangedRect

을 호출 하는 동안 추적기 사각형이 변경 될 때마다 프레임 워크에서 호출 `Track` 됩니다.

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>매개 변수

*rectOld*<br/>
개체의 이전 장치 좌표를 포함 합니다 `CRectTracker` .

### <a name="remarks"></a>설명

이 함수가 호출 될 때로 그려진 모든 피드백이 `DrawTrackerRect` 제거 되었습니다. 이 함수의 기본 구현은 아무 작업도 수행하지 않습니다.

사각형의 크기가 조정 된 후 작업을 수행 하려면이 함수를 재정의 합니다.

## <a name="crecttrackersetcursor"></a><a name="setcursor"></a> CRectTracker:: SetCursor

이 함수를 호출 하 여 개체의 영역 위에 있는 동안 cursor 셰이프를 변경 `CRectTracker` 합니다.

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
현재 커서를 포함 하는 창을 가리킵니다.

*nHitTest*<br/>
WM_SETCURSOR 메시지의 이전 적중 횟수 테스트 결과입니다.

### <a name="return-value"></a>반환 값

이전 적중이 tracker 사각형 위에 있는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

WM_SETCURSOR 메시지를 처리 하는 창의 함수 내에서이 함수를 호출 합니다 (일반적으로 `OnSetCursor` ).

## <a name="crecttrackertrack"></a><a name="track"></a> CRectTracker:: Track

사각형의 크기를 조정 하는 사용자 인터페이스를 표시 하려면이 함수를 호출 합니다.

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
사각형을 포함 하는 window 개체입니다.

*까지*<br/>
클라이언트 영역을 기준으로 하는 현재 마우스 위치의 장치 좌표입니다.

*bAllowInvert*<br/>
TRUE 이면 사각형이 x 축 또는 y 축을 따라 반전 될 수 있습니다. 그렇지 않으면 FALSE입니다.

*pWndClipTo*<br/>
그리기 작업을 클리핑할 창입니다. NULL 인 경우 *pWnd* 는 클리핑 사각형으로 사용 됩니다.

### <a name="return-value"></a>반환 값

ESC 키를 누르면 추적 프로세스가 중단 되 고 추적기에 저장 된 사각형은 변경 되지 않으며 0이 반환 됩니다. 변경을 커밋한 경우 마우스를 이동 하 고 왼쪽 마우스 단추를 놓으면 새 위치 및/또는 크기가 추적기의 사각형에 기록 되 고 0이 아닌 값이 반환 됩니다.

### <a name="remarks"></a>설명

일반적으로이는 메시지를 처리 하는 응용 프로그램의 함수 내에서 호출 됩니다 `WM_LBUTTONDOWN` (일반적으로 `OnLButtonDown` ).

이 함수는 사용자가 마우스 왼쪽 단추를 놓을 때까지 마우스를 캡처하거나 ESC 키를 누르거나 마우스 오른쪽 단추를 누릅니다. 사용자가 마우스 커서를 움직이면 및를 호출 하 여 피드백을 업데이트 `DrawTrackerRect` 합니다 `OnChangedRect` .

*Ballowinvert* 이 TRUE 이면 x 축 또는 y 축에서 추적 사각형을 반전 시킬 수 있습니다.

## <a name="crecttrackertrackrubberband"></a><a name="trackrubberband"></a> CRectTracker::

고무 밴드 선택을 수행 하려면이 함수를 호출 합니다.

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
사각형을 포함 하는 window 개체입니다.

*까지*<br/>
클라이언트 영역을 기준으로 하는 현재 마우스 위치의 장치 좌표입니다.

*bAllowInvert*<br/>
TRUE 이면 사각형이 x 축 또는 y 축을 따라 반전 될 수 있습니다. 그렇지 않으면 FALSE입니다.

### <a name="return-value"></a>반환 값

마우스가 이동 하 고 사각형이 비어 있지 않으면 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

일반적으로 WM_LBUTTONDOWN 메시지를 처리 하는 응용 프로그램의 함수 내에서 호출 됩니다 (일반적으로 `OnLButtonDown` ).

이 함수는 사용자가 마우스 왼쪽 단추를 놓을 때까지 마우스를 캡처하거나 ESC 키를 누르거나 마우스 오른쪽 단추를 누릅니다. 사용자가 마우스 커서를 움직이면 및를 호출 하 여 피드백을 업데이트 `DrawTrackerRect` 합니다 `OnChangedRect` .

오른쪽 아래 핸들에서 고무 밴드 유형 선택을 사용 하 여 추적을 수행 합니다. 반전이 허용 되는 경우 위쪽 및 왼쪽 또는 오른쪽으로 끌어 사각형의 크기를 조정할 수 있습니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 추적기](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleResizeBar 클래스](../../mfc/reference/coleresizebar-class.md)<br/>
[CRect 클래스](../../atl-mfc-shared/reference/crect-class.md)
