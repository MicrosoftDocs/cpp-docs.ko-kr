---
description: '자세히 알아보기: CSliderCtrl 클래스'
title: CSliderCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
helpviewer_keywords:
- CSliderCtrl [MFC], CSliderCtrl
- CSliderCtrl [MFC], ClearSel
- CSliderCtrl [MFC], ClearTics
- CSliderCtrl [MFC], Create
- CSliderCtrl [MFC], CreateEx
- CSliderCtrl [MFC], GetBuddy
- CSliderCtrl [MFC], GetChannelRect
- CSliderCtrl [MFC], GetLineSize
- CSliderCtrl [MFC], GetNumTics
- CSliderCtrl [MFC], GetPageSize
- CSliderCtrl [MFC], GetPos
- CSliderCtrl [MFC], GetRange
- CSliderCtrl [MFC], GetRangeMax
- CSliderCtrl [MFC], GetRangeMin
- CSliderCtrl [MFC], GetSelection
- CSliderCtrl [MFC], GetThumbLength
- CSliderCtrl [MFC], GetThumbRect
- CSliderCtrl [MFC], GetTic
- CSliderCtrl [MFC], GetTicArray
- CSliderCtrl [MFC], GetTicPos
- CSliderCtrl [MFC], GetToolTips
- CSliderCtrl [MFC], SetBuddy
- CSliderCtrl [MFC], SetLineSize
- CSliderCtrl [MFC], SetPageSize
- CSliderCtrl [MFC], SetPos
- CSliderCtrl [MFC], SetRange
- CSliderCtrl [MFC], SetRangeMax
- CSliderCtrl [MFC], SetRangeMin
- CSliderCtrl [MFC], SetSelection
- CSliderCtrl [MFC], SetThumbLength
- CSliderCtrl [MFC], SetTic
- CSliderCtrl [MFC], SetTicFreq
- CSliderCtrl [MFC], SetTipSide
- CSliderCtrl [MFC], SetToolTips
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
ms.openlocfilehash: 556366f429b39344f4ae2f20acd3c20fd9760552
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264546"
---
# <a name="csliderctrl-class"></a>CSliderCtrl 클래스

Windows의 공용 슬라이더 컨트롤의 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSliderCtrl:: CSliderCtrl](#csliderctrl)|`CSliderCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSliderCtrl:: ClearSel](#clearsel)|슬라이더 컨트롤에서 현재 선택 영역을 지웁니다.|
|[CSliderCtrl:: ClearTics](#cleartics)|슬라이더 컨트롤에서 현재 눈금 표시를 제거 합니다.|
|[CSliderCtrl:: Create](#create)|슬라이더 컨트롤을 만들어 개체에 연결 `CSliderCtrl` 합니다.|
|[CSliderCtrl:: CreateEx](#createex)|지정 된 Windows 확장 스타일을 사용 하 여 슬라이더 컨트롤을 만들고 개체에 연결 `CSliderCtrl` 합니다.|
|[CSliderCtrl:: GetBuddy](#getbuddy)|지정 된 위치에 있는 슬라이더 컨트롤 버디 창의 핸들을 검색 합니다.|
|[CSliderCtrl:: GetChannelRect](#getchannelrect)|슬라이더 컨트롤의 채널 크기를 검색 합니다.|
|[CSliderCtrl:: GetLineSize](#getlinesize)|슬라이더 컨트롤의 줄 크기를 검색 합니다.|
|[CSliderCtrl:: GetNumTics](#getnumtics)|슬라이더 컨트롤의 눈금 표시 수를 검색 합니다.|
|[CSliderCtrl:: GetPageSize](#getpagesize)|슬라이더 컨트롤의 페이지 크기를 검색 합니다.|
|[CSliderCtrl:: GetPos](#getpos)|슬라이더의 현재 위치를 검색 합니다.|
|[CSliderCtrl:: GetRange](#getrange)|슬라이더의 최소 및 최대 위치를 검색 합니다.|
|[CSliderCtrl:: GetRangeMax](#getrangemax)|슬라이더의 최대 위치를 검색 합니다.|
|[CSliderCtrl:: GetRangeMin](#getrangemin)|슬라이더의 최소 위치를 검색 합니다.|
|[CSliderCtrl:: GetSelection](#getselection)|현재 선택 영역의 범위를 검색 합니다.|
|[CSliderCtrl:: GetThumbLength](#getthumblength)|현재 trackbar 컨트롤의 슬라이더 길이를 검색 합니다.|
|[CSliderCtrl:: GetThumbRect](#getthumbrect)|슬라이더 컨트롤의 엄지 단추 크기를 검색 합니다.|
|[CSliderCtrl:: GetTic](#gettic)|지정 된 눈금 표시의 위치를 검색 합니다.|
|[CSliderCtrl:: GetTicArray](#getticarray)|슬라이더 컨트롤에 대 한 눈금 표시 위치의 배열을 검색 합니다.|
|[CSliderCtrl:: GetTicPos](#getticpos)|클라이언트 좌표로 지정 된 눈금 표시의 위치를 검색 합니다.|
|[CSliderCtrl:: GetToolTips](#gettooltips)|슬라이더 컨트롤에 할당 된 도구 설명 컨트롤에 대 한 핸들을 검색 합니다 (있는 경우).|
|[CSliderCtrl:: SetBuddy](#setbuddy)|창을 슬라이더 컨트롤에 대 한 버디 창으로 할당 합니다.|
|[CSliderCtrl:: SetLineSize](#setlinesize)|슬라이더 컨트롤의 줄 크기를 설정 합니다.|
|[CSliderCtrl:: SetPageSize](#setpagesize)|슬라이더 컨트롤의 페이지 크기를 설정 합니다.|
|[CSliderCtrl:: SetPos](#setpos)|슬라이더의 현재 위치를 설정 합니다.|
|[CSliderCtrl:: SetRange](#setrange)|슬라이더의 최소 및 최대 위치를 설정 합니다.|
|[CSliderCtrl:: SetRangeMax](#setrangemax)|슬라이더의 최대 위치를 설정 합니다.|
|[CSliderCtrl:: SetRangeMin](#setrangemin)|슬라이더의 최소 위치를 설정 합니다.|
|[CSliderCtrl:: SetSelection](#setselection)|현재 선택 영역의 범위를 설정 합니다.|
|[CSliderCtrl:: setthumblg](#setthumblength)|현재 trackbar 컨트롤의 슬라이더 길이를 설정 합니다.|
|[CSliderCtrl:: SetTic](#settic)|지정 된 눈금 표시의 위치를 설정 합니다.|
|[CSliderCtrl:: SetTicFreq](#setticfreq)|슬라이더 컨트롤 증가값 당 눈금 표시의 빈도를 설정 합니다.|
|[CSliderCtrl:: SetTipSide](#settipside)|Trackbar 컨트롤에서 사용 하는 도구 설명 컨트롤을 배치 합니다.|
|[CSliderCtrl:: SetToolTips](#settooltips)|도구 설명 컨트롤을 슬라이더 컨트롤에 할당 합니다.|

## <a name="remarks"></a>설명

"슬라이더 컨트롤" (trackbar 라고도 함)은 슬라이더와 선택적 눈금 표시를 포함 하는 창입니다. 사용자가 마우스나 방향 키 중 하나를 사용 하 여 슬라이더를 움직이면 컨트롤이 변경 내용을 나타내는 알림 메시지를 보냅니다.

슬라이더 컨트롤은 사용자가 범위에서 불연속 값 또는 연속 값 집합을 선택 하려는 경우에 유용 합니다. 예를 들어 슬라이더 컨트롤을 사용 하 여 사용자가 슬라이더를 지정 된 눈금으로 이동 하 여 키보드의 반복 주기를 설정할 수 있습니다.

이 컨트롤 (및 `CSliderCtrl` 클래스)은 windows 95/98 및 WINDOWS NT 버전 3.51 이상에서 실행 되는 프로그램에만 사용할 수 있습니다.

슬라이더는 만들 때 사용자가 지정 하는 증분 단위로 이동 합니다. 예를 들어 슬라이더의 범위를 5로 지정 하는 경우 슬라이더는 슬라이더 컨트롤의 왼쪽에 있는 위치와 범위의 각 증가값에 대 한 위치 하나를 6 개 까지만 차지할 수 있습니다. 일반적으로 이러한 각 위치는 눈금 표시로 식별 됩니다.

의 멤버 함수 및 생성자를 사용 하 여 슬라이더를 만듭니다 `Create` `CSliderCtrl` . 슬라이더 컨트롤을 만든 후에는의 멤버 함수를 사용 하 여 `CSliderCtrl` 많은 속성을 변경할 수 있습니다. 슬라이더에 대한 최소 및 최대 위치 설정, 눈금 표시 그리기, 선택 범위 설정 및 슬라이더 위치 조정을 변경할 수 있습니다.

사용에 대 한 자세한 내용은 `CSliderCtrl` [컨트롤](../../mfc/controls-mfc.md) 및 [CSliderCtrl 사용](../../mfc/using-csliderctrl.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>요구 사항

**헤더:** afxcmn.h

## <a name="csliderctrlclearsel"></a><a name="clearsel"></a> CSliderCtrl:: ClearSel

슬라이더 컨트롤에서 현재 선택 영역을 지웁니다.

```cpp
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>매개 변수

*bRedraw*<br/>
다시 그리기 플래그입니다. 이 매개 변수가 TRUE 이면 선택 영역이 지워진 후 슬라이더가 다시 그려집니다. 그렇지 않으면 슬라이더가 다시 그려지지 않습니다.

## <a name="csliderctrlcleartics"></a><a name="cleartics"></a> CSliderCtrl:: ClearTics

슬라이더 컨트롤에서 현재 눈금 표시를 제거 합니다.

```cpp
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>매개 변수

*bRedraw*<br/>
다시 그리기 플래그입니다. 이 매개 변수가 TRUE 이면 눈금 표시가 지워진 후 슬라이더가 다시 그려집니다. 그렇지 않으면 슬라이더가 다시 그려지지 않습니다.

## <a name="csliderctrlcreate"></a><a name="create"></a> CSliderCtrl:: Create

슬라이더 컨트롤을 만들어 개체에 연결 `CSliderCtrl` 합니다.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>매개 변수

*dwStyle*<br/>
슬라이더 컨트롤의 스타일을 지정 합니다. Windows SDK에 설명 된 [슬라이더 컨트롤 스타일](/windows/win32/Controls/trackbar-control-styles)의 조합을 컨트롤에 적용 합니다.

*rect*<br/>
슬라이더 컨트롤의 크기와 위치를 지정 합니다. 이는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 구조 일 수 있습니다.

*pParentWnd*<br/>
슬라이더 컨트롤의 부모 창 (일반적으로)을 지정 합니다 `CDialog` . NULL이 아니어야 합니다.

*nID*<br/>
슬라이더 컨트롤의 ID를 지정 합니다.

### <a name="return-value"></a>반환 값

초기화에 성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CSliderCtrl`두 단계로을 생성 합니다. 먼저 생성자를 호출한 다음을 호출 합니다 `Create` .이 메서드는 슬라이더 컨트롤을 만들고이를 개체에 연결 `CSliderCtrl` 합니다.

*Dwstyle* 에 대해 설정 된 값에 따라 슬라이더 컨트롤은 세로 방향 또는 가로 방향 중 하나를 사용할 수 있습니다. 둘 중 어느 쪽에 나 양쪽에 눈금 표시를 포함할 수 있습니다. 연속 값의 범위를 지정 하는 데에도 사용할 수 있습니다.

슬라이더 컨트롤에 확장 창 스타일을 적용 하려면 대신 [Createex](#createex) 를 호출 `Create` 합니다.

## <a name="csliderctrlcreateex"></a><a name="createex"></a> CSliderCtrl:: CreateEx

컨트롤 (자식 창)을 만들고이를 개체에 연결 `CSliderCtrl` 합니다.

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
슬라이더 컨트롤의 스타일을 지정 합니다. Windows SDK에 설명 된 [슬라이더 컨트롤 스타일](/windows/win32/Controls/trackbar-control-styles)의 조합을 컨트롤에 적용 합니다.

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

## <a name="csliderctrlcsliderctrl"></a><a name="csliderctrl"></a> CSliderCtrl:: CSliderCtrl

`CSliderCtrl` 개체를 생성합니다.

```
CSliderCtrl();
```

## <a name="csliderctrlgetbuddy"></a><a name="getbuddy"></a> CSliderCtrl:: GetBuddy

지정 된 위치에 있는 슬라이더 컨트롤 버디 창의 핸들을 검색 합니다.

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>매개 변수

*fLocation*<br/>
검색할 두 개의 버디 창 핸들을 나타내는 부울 값입니다. 다음 값 중 하나일 수 있습니다.

- TRUE는 슬라이더 왼쪽에 있는 버디에 대 한 핸들을 검색 합니다. 슬라이더 컨트롤에서 TBS_VERT 스타일을 사용 하는 경우이 메시지는 슬라이더 위의 버디를 검색 합니다.

- FALSE는 슬라이더의 오른쪽에 있는 버디에 대 한 핸들을 검색 합니다. 슬라이더 컨트롤에서 TBS_VERT 스타일을 사용 하는 경우이 메시지는 슬라이더 아래에 있는 버디를 검색 합니다.

### <a name="return-value"></a>반환 값

*Flocation* 에 지정 된 위치에 있는 버디 창인 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 포인터 이거나, 해당 위치에 버디 창이 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy)의 동작을 구현 합니다. Slider 컨트롤 스타일에 대 한 설명은 Windows SDK의 [Trackbar 컨트롤 스타일](/windows/win32/Controls/trackbar-control-styles) 을 참조 하세요.

## <a name="csliderctrlgetchannelrect"></a><a name="getchannelrect"></a> CSliderCtrl:: GetChannelRect

슬라이더 컨트롤 채널에 대 한 경계 사각형의 크기와 위치를 검색 합니다.

```cpp
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>매개 변수

*lprc*<br/>
함수가 반환 될 때 채널 경계 사각형의 크기와 위치를 포함 하는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

채널은 슬라이더가 이동 하는 영역이 며 범위를 선택할 때 강조 표시를 포함 합니다.

## <a name="csliderctrlgetlinesize"></a><a name="getlinesize"></a> CSliderCtrl:: GetLineSize

슬라이더 컨트롤의 줄 크기를 검색 합니다.

```
int GetLineSize() const;
```

### <a name="return-value"></a>반환 값

슬라이더 컨트롤의 줄 크기입니다.

### <a name="remarks"></a>설명

줄 크기는 TB_LINEUP 및 TB_LINEDOWN 알림에 대해 슬라이더가 이동 하는 정도에 영향을 줍니다. 줄 크기의 기본 설정은 1입니다.

## <a name="csliderctrlgetnumtics"></a><a name="getnumtics"></a> CSliderCtrl:: GetNumTics

슬라이더 컨트롤의 눈금 표시 수를 검색 합니다.

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>반환 값

슬라이더 컨트롤의 눈금 표시 수입니다.

## <a name="csliderctrlgetpagesize"></a><a name="getpagesize"></a> CSliderCtrl:: GetPageSize

슬라이더 컨트롤의 페이지 크기를 검색 합니다.

```
int GetPageSize() const;
```

### <a name="return-value"></a>반환 값

슬라이더 컨트롤의 페이지 크기입니다.

### <a name="remarks"></a>설명

페이지 크기는 TB_PAGEUP 및 TB_PAGEDOWN 알림에 대해 슬라이더가 이동 하는 정도에 영향을 줍니다.

## <a name="csliderctrlgetpos"></a><a name="getpos"></a> CSliderCtrl:: GetPos

슬라이더 컨트롤에서 슬라이더의 현재 위치를 검색 합니다.

```
int GetPos() const;
```

### <a name="return-value"></a>반환 값

현재 위치입니다.

## <a name="csliderctrlgetrange"></a><a name="getrange"></a> CSliderCtrl:: GetRange

슬라이더 컨트롤에서 슬라이더의 최대 및 최소 위치를 검색 합니다.

```cpp
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>매개 변수

*nMin*<br/>
최소 위치를 수신 하는 정수에 대 한 참조입니다.

*nMax*<br/>
최대 위치를 수신 하는 정수에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 함수는 *Nmin* 및 *n 일별 최대* 에서 참조 하는 정수에 값을 복사 합니다.

## <a name="csliderctrlgetrangemax"></a><a name="getrangemax"></a> CSliderCtrl:: GetRangeMax

슬라이더 컨트롤에서 슬라이더의 최대 위치를 검색 합니다.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>반환 값

컨트롤의 최대 위치입니다.

## <a name="csliderctrlgetrangemin"></a><a name="getrangemin"></a> CSliderCtrl:: GetRangeMin

슬라이더 컨트롤에서 슬라이더의 최소 위치를 검색 합니다.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>반환 값

컨트롤의 최소 위치입니다.

## <a name="csliderctrlgetselection"></a><a name="getselection"></a> CSliderCtrl:: GetSelection

슬라이더 컨트롤에서 현재 선택 영역의 시작 및 끝 위치를 검색 합니다.

```cpp
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>매개 변수

*nMin*<br/>
현재 선택 영역의 시작 위치를 수신 하는 정수에 대 한 참조입니다.

*nMax*<br/>
현재 선택 영역의 끝 위치를 받는 정수에 대 한 참조입니다.

## <a name="csliderctrlgetthumblength"></a><a name="getthumblength"></a> CSliderCtrl:: GetThumbLength

현재 trackbar 컨트롤의 슬라이더 길이를 검색 합니다.

```
int GetThumbLength() const;
```

### <a name="return-value"></a>반환 값

슬라이더의 길이 (픽셀)입니다.

### <a name="remarks"></a>설명

이 메서드는 Windows SDK에서 설명 하는 [TBM_GETTHUMBLENGTH](/windows/win32/Controls/tbm-getthumblength) 메시지를 보냅니다.

## <a name="csliderctrlgetthumbrect"></a><a name="getthumbrect"></a> CSliderCtrl:: GetThumbRect

슬라이더 컨트롤에서 슬라이더 (엄지 단추)에 대 한 경계 사각형의 크기와 위치를 검색 합니다.

```cpp
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>매개 변수

*lprc*<br/>
`CRect`함수가 반환 될 때 슬라이더의 경계 사각형을 포함 하는 개체에 대 한 포인터입니다.

## <a name="csliderctrlgettic"></a><a name="gettic"></a> CSliderCtrl:: GetTic

슬라이더 컨트롤에서 눈금 표시의 위치를 검색 합니다.

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>매개 변수

*nTic*<br/>
눈금 표시를 식별 하는 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

지정 된 눈금 표시의 위치 이거나, *Ntic* 가 유효한 인덱스를 지정 하지 않는 경우-1입니다.

## <a name="csliderctrlgetticarray"></a><a name="getticarray"></a> CSliderCtrl:: GetTicArray

슬라이더 컨트롤의 눈금 표시 위치를 포함 하는 배열의 주소를 검색 합니다.

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>반환 값

슬라이더 컨트롤의 눈금 표시 위치를 포함 하는 배열의 주소입니다.

## <a name="csliderctrlgetticpos"></a><a name="getticpos"></a> CSliderCtrl:: GetTicPos

슬라이더 컨트롤에서 눈금 표시의 현재 실제 위치를 검색 합니다.

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>매개 변수

*nTic*<br/>
눈금 표시를 식별 하는 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

지정 된 눈금 표시의 실제 위치 (클라이언트 좌표) 이거나, *Ntic* 가 유효한 인덱스를 지정 하지 않은 경우-1입니다.

## <a name="csliderctrlgettooltips"></a><a name="gettooltips"></a> CSliderCtrl:: GetToolTips

슬라이더 컨트롤에 할당 된 도구 설명 컨트롤에 대 한 핸들을 검색 합니다 (있는 경우).

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>반환 값

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) 개체에 대 한 포인터 또는 도구 설명이 사용 되지 않는 경우 NULL입니다. 슬라이더 컨트롤에서 TBS_TOOLTIPS 스타일을 사용 하지 않는 경우 반환 값은 NULL입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips)의 동작을 구현 합니다. 이 멤버 함수는 `CToolTipCtrl` 컨트롤에 대 한 핸들 대신 개체를 반환 합니다.

Slider 컨트롤 스타일에 대 한 설명은 Windows SDK의 [Trackbar 컨트롤 스타일](/windows/win32/Controls/trackbar-control-styles) 을 참조 하세요.

## <a name="csliderctrlsetbuddy"></a><a name="setbuddy"></a> CSliderCtrl:: SetBuddy

창을 슬라이더 컨트롤에 대 한 버디 창으로 할당 합니다.

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>매개 변수

*pWndBuddy*<br/>
`CWnd`슬라이더 컨트롤의 버디로 설정 되는 개체에 대 한 포인터입니다.

*fLocation*<br/>
버디 창을 표시할 위치를 지정 하는 값입니다. 이 값은 다음 중 하나일 수 있습니다.

- TRUE 이면 trackbar 컨트롤에서 TBS_HORZ 스타일을 사용 하는 경우 버디가 트랙 표시줄의 왼쪽에 표시 됩니다. Trackbar에서 TBS_VERT 스타일을 사용 하는 경우 buddy는 trackbar 컨트롤 위에 표시 됩니다.

- FALSE trackbar 컨트롤에서 TBS_HORZ 스타일을 사용 하는 경우 버디가 트랙 표시줄의 오른쪽에 표시 됩니다. Trackbar에서 TBS_VERT 스타일을 사용 하는 경우 buddy는 trackbar 컨트롤 아래에 나타납니다.

### <a name="return-value"></a>반환 값

해당 위치에서 슬라이더 컨트롤에 이전에 할당 된 [CWnd](../../mfc/reference/cwnd-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy)의 동작을 구현 합니다. 이 멤버 함수는 개체에 대 한 포인터를 사용 하 여 `CWnd` 반환 값과 매개 변수 모두에 대 한 창 핸들을 사용 하지 않습니다.

Slider 컨트롤 스타일에 대 한 설명은 Windows SDK의 [Trackbar 컨트롤 스타일](/windows/win32/Controls/trackbar-control-styles) 을 참조 하세요.

## <a name="csliderctrlsetlinesize"></a><a name="setlinesize"></a> CSliderCtrl:: SetLineSize

슬라이더 컨트롤의 줄 크기를 설정 합니다.

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>매개 변수

*nSize*<br/>
슬라이더 컨트롤의 줄 바꿈 크기입니다.

### <a name="return-value"></a>반환 값

이전 줄 크기입니다.

### <a name="remarks"></a>설명

줄 크기는 TB_LINEUP 및 TB_LINEDOWN 알림에 대해 슬라이더가 이동 하는 정도에 영향을 줍니다.

## <a name="csliderctrlsetpagesize"></a><a name="setpagesize"></a> CSliderCtrl:: SetPageSize

슬라이더 컨트롤의 페이지 크기를 설정 합니다.

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>매개 변수

*nSize*<br/>
슬라이더 컨트롤의 새 페이지 크기입니다.

### <a name="return-value"></a>반환 값

이전 페이지 크기입니다.

### <a name="remarks"></a>설명

페이지 크기는 TB_PAGEUP 및 TB_PAGEDOWN 알림에 대해 슬라이더가 이동 하는 정도에 영향을 줍니다.

## <a name="csliderctrlsetpos"></a><a name="setpos"></a> CSliderCtrl:: SetPos

슬라이더 컨트롤에서 슬라이더의 현재 위치를 설정 합니다.

```cpp
void SetPos(int nPos);
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
새 슬라이더 위치를 지정 합니다.

## <a name="csliderctrlsetrange"></a><a name="setrange"></a> CSliderCtrl:: SetRange

슬라이더 컨트롤에서 슬라이더의 범위 (최소 및 최대 위치)를 설정 합니다.

```cpp
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>매개 변수

*nMin*<br/>
슬라이더의 최소 위치입니다.

*nMax*<br/>
슬라이더의 최대 위치입니다.

*bRedraw*<br/>
다시 그리기 플래그입니다. 이 매개 변수가 TRUE 이면 범위가 설정 된 후 슬라이더가 다시 그려집니다. 그렇지 않으면 슬라이더가 다시 그려지지 않습니다.

## <a name="csliderctrlsetrangemax"></a><a name="setrangemax"></a> CSliderCtrl:: SetRangeMax

슬라이더 컨트롤에서 슬라이더의 최대 범위를 설정 합니다.

```cpp
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>매개 변수

*nMax*<br/>
슬라이더의 최대 위치입니다.

*bRedraw*<br/>
다시 그리기 플래그입니다. 이 매개 변수가 TRUE 이면 범위가 설정 된 후 슬라이더가 다시 그려집니다. 그렇지 않으면 슬라이더가 다시 그려지지 않습니다.

## <a name="csliderctrlsetrangemin"></a><a name="setrangemin"></a> CSliderCtrl:: SetRangeMin

슬라이더 컨트롤에서 슬라이더의 최소 범위를 설정 합니다.

```cpp
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>매개 변수

*nMin*<br/>
슬라이더의 최소 위치입니다.

*bRedraw*<br/>
다시 그리기 플래그입니다. 이 매개 변수가 TRUE 이면 범위가 설정 된 후 슬라이더가 다시 그려집니다. 그렇지 않으면 슬라이더가 다시 그려지지 않습니다.

## <a name="csliderctrlsetselection"></a><a name="setselection"></a> CSliderCtrl:: SetSelection

슬라이더 컨트롤에서 현재 선택 영역에 대 한 시작 및 끝 위치를 설정 합니다.

```cpp
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>매개 변수

*nMin*<br/>
슬라이더의 시작 위치입니다.

*nMax*<br/>
슬라이더의 끝 위치입니다.

## <a name="csliderctrlsetthumblength"></a><a name="setthumblength"></a> CSliderCtrl:: setthumblg

현재 trackbar 컨트롤의 슬라이더 길이를 설정 합니다.

```cpp
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>매개 변수

*nLength*\
진행 슬라이더의 길이 (픽셀)입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하려면 trackbar 컨트롤이 [TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles) 스타일로 설정 되어야 합니다.

이 메서드는 Windows SDK에서 설명 하는 [TBM_SETTHUMBLENGTH](/windows/win32/Controls/tbm-setthumblength) 메시지를 보냅니다.

### <a name="example"></a>예제

다음 코드 예제에서는 `m_sliderCtrl` 현재 trackbar 컨트롤에 액세스 하는 데 사용 되는 변수를 정의 합니다. 또한이 예제에서는 `thumbLength` trackbar 컨트롤의 thumb 구성 요소 기본 길이를 저장 하는 데 사용 되는 변수를 정의 합니다. 이러한 변수는 다음 예제에서 사용 됩니다.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>예제

다음 코드 예제에서는 trackbar 컨트롤의 thumb 구성 요소를 기본 길이의 두 배로 설정 합니다.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

## <a name="csliderctrlsettic"></a><a name="settic"></a> CSliderCtrl:: SetTic

슬라이더 컨트롤에서 눈금 표시의 위치를 설정 합니다.

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>매개 변수

*nTic*<br/>
눈금 표시의 위치입니다. 이 매개 변수는 양수 값을 지정 해야 합니다.

### <a name="return-value"></a>반환 값

눈금 표시가 설정 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="csliderctrlsetticfreq"></a><a name="setticfreq"></a> CSliderCtrl:: SetTicFreq

슬라이더에 눈금 표시가 표시 되는 빈도를 설정 합니다.

```cpp
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>매개 변수

*nFreq*<br/>
눈금 표시의 빈도입니다.

### <a name="remarks"></a>설명

예를 들어 frequency를 2로 설정 하면 슬라이더 범위의 다른 모든 증가값에 대해 눈금 표시가 표시 됩니다. 빈도의 기본 설정은 1입니다. 즉, 범위의 모든 증분이 눈금 표시와 연결 됩니다.

이 함수를 사용 하려면 TBS_AUTOTICKS 스타일을 사용 하 여 컨트롤을 만들어야 합니다. 자세한 내용은 [CSliderCtrl:: Create](#create)를 참조 하세요.

## <a name="csliderctrlsettipside"></a><a name="settipside"></a> CSliderCtrl:: SetTipSide

Trackbar 컨트롤에서 사용 하는 도구 설명 컨트롤을 배치 합니다.

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>매개 변수

*N 위치*<br/>
도구 설명 컨트롤이 표시 되는 위치를 나타내는 값입니다. 가능한 값 목록은 Windows SDK에 설명 된 대로 Win32 메시지 [TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside)를 참조 하세요.

### <a name="return-value"></a>반환 값

Tooltip 컨트롤의 이전 위치를 나타내는 값입니다. 반환 값은 *Nlocation* 에 사용할 수 있는 값 중 하 나와 같습니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 TBM_SETTIPSIDE의 동작을 구현 합니다. TBS_TOOLTIPS 스타일을 사용 하는 슬라이더 컨트롤 도구 설명을 표시 합니다. Slider 컨트롤 스타일에 대 한 설명은 Windows SDK의 [Trackbar 컨트롤 스타일](/windows/win32/Controls/trackbar-control-styles) 을 참조 하세요.

## <a name="csliderctrlsettooltips"></a><a name="settooltips"></a> CSliderCtrl:: SetToolTips

도구 설명 컨트롤을 슬라이더 컨트롤에 할당 합니다.

```cpp
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>매개 변수

*pWndTip*<br/>
슬라이더 컨트롤과 함께 사용할 도구 설명을 포함 하는 [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK에 설명 된 대로 Win32 메시지 [TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips)의 동작을 구현 합니다. TBS_TOOLTIPS 스타일을 사용 하 여 슬라이더 컨트롤을 만들면 슬라이더의 현재 위치를 표시 하는 슬라이더 옆에 표시 되는 기본 도구 설명 컨트롤을 만듭니다. Slider 컨트롤 스타일에 대 한 설명은 Windows SDK의 [Trackbar 컨트롤 스타일](/windows/win32/Controls/trackbar-control-styles) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 샘플 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 클래스](../../mfc/reference/cwnd-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl 클래스](../../mfc/reference/cprogressctrl-class.md)
