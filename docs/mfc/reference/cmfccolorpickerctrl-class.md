---
description: '자세한 정보: CMFCColorPickerCtrl 클래스'
title: CMFCColorPickerCtrl 클래스
ms.date: 11/19/2018
f1_keywords:
- CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SelectCellHexagon
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminanceBarWidth
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetOriginalColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetPalette
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetType
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::DrawCursor
helpviewer_keywords:
- CMFCColorPickerCtrl [MFC], CMFCColorPickerCtrl
- CMFCColorPickerCtrl [MFC], GetColor
- CMFCColorPickerCtrl [MFC], GetHLS
- CMFCColorPickerCtrl [MFC], GetHue
- CMFCColorPickerCtrl [MFC], GetLuminance
- CMFCColorPickerCtrl [MFC], GetSaturation
- CMFCColorPickerCtrl [MFC], SelectCellHexagon
- CMFCColorPickerCtrl [MFC], SetColor
- CMFCColorPickerCtrl [MFC], SetHLS
- CMFCColorPickerCtrl [MFC], SetHue
- CMFCColorPickerCtrl [MFC], SetLuminance
- CMFCColorPickerCtrl [MFC], SetLuminanceBarWidth
- CMFCColorPickerCtrl [MFC], SetOriginalColor
- CMFCColorPickerCtrl [MFC], SetPalette
- CMFCColorPickerCtrl [MFC], SetSaturation
- CMFCColorPickerCtrl [MFC], SetType
- CMFCColorPickerCtrl [MFC], DrawCursor
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
ms.openlocfilehash: e4363c08af86dee96df1492e9a029414d9902435
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313075"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFCColorPickerCtrl 클래스

`CMFCColorPickerCtrl`클래스는 색을 선택 하는 데 사용 되는 컨트롤에 대 한 기능을 제공 합니다.

## <a name="syntax"></a>구문

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Cmfccolor을 Kerctrl:: CMFCColorPickerCtrl](#cmfccolorpickerctrl)|`CMFCColorPickerCtrl` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCColorPickerCtrl:: GetColor](#getcolor)|사용자가 선택 하는 색을 검색 합니다.|
|[CMFCColorPickerCtrl:: GetHLS](#gethls)|사용자가 선택 하는 색의 색조, 광도 및 채도 값을 검색 합니다.|
|[CMFCColorPickerCtrl:: GetHue](#gethue)|사용자가 선택 하는 색의 색상 구성 요소를 검색 합니다.|
|[CMFCColorPickerCtrl:: GetLuminance](#getluminance)|사용자가 선택 하는 색의 광도 구성 요소를 검색 합니다.|
|[CMFCColorPickerCtrl:: GetSaturation](#getsaturation)|사용자가 선택 하는 색의 채도 구성 요소를 검색 합니다.|
|[CMFCColorPickerCtrl:: SelectCellHexagon](#selectcellhexagon)|현재 색을 지정 된 RGB 색 구성 요소나 지정 된 셀 육각형으로 정의 된 색으로 설정 합니다.|
|[CMFCColorPickerCtrl:: SetColor](#setcolor)|현재 색을 지정 된 RGB 색 값으로 설정 합니다.|
|[CMFCColorPickerCtrl:: SetHLS](#sethls)|현재 색을 지정 된 HLS 색 값으로 설정 합니다.|
|[CMFCColorPickerCtrl:: SetHue](#sethue)|현재 선택 된 색의 색상 구성 요소를 변경 합니다.|
|[CMFCColorPickerCtrl:: SetLuminance](#setluminance)|현재 선택 된 색의 광도 구성 요소를 변경 합니다.|
|[CMFCColorPickerCtrl:: SetLuminanceBarWidth](#setluminancebarwidth)|색 선택 컨트롤에서 광도 막대의 너비를 설정 합니다.|
|[CMFCColorPickerCtrl:: SetOriginalColor](#setoriginalcolor)|초기 선택 된 색을 설정 합니다.|
|[CMFCColorPickerCtrl:: SetPalette](#setpalette)|현재 색상표를 설정 합니다.|
|[CMFCColorPickerCtrl:: SetSaturation](#setsaturation)|현재 선택 된 색의 채도 구성 요소를 변경 합니다.|
|[CMFCColorPickerCtrl:: SetType](#settype)|표시할 색 선택 컨트롤의 형식을 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[Cmfccolorrawcursor Ctrl::D](#drawcursor)|선택한 색을 가리키는 커서가 표시 되기 전에 프레임 워크에서 호출 됩니다.|

## <a name="remarks"></a>설명

표준 색은 육각형 색상표에서 선택 되 고 사용자 지정 색은 빨강/녹색/파랑 표기법 또는 색상/satuaration/광도 표기법을 사용 하 여 색이 지정 된 광도 표시줄에서 선택 됩니다.

다음 그림에서는 여러 개체를 보여 줍니다 `CMFCColorPickerCtrl` .

![CMFCColorPickerCtrl 대화 상자](../../mfc/reference/media/colorpicker.png "CMFCColorPickerCtrl 대화 상자")

에서는 `CMFCColorPickerCtrl` 두 가지 형식의 스타일을 지원 합니다. HEX 및 HEX_GREYSCALE 스타일은 표준 색 선택에 적합 합니다. 선택 및 광도 스타일은 사용자 지정 색 선택에 적합 합니다.

다음 단계를 수행 하 여 `CMFCColorPickerCtrl` 컨트롤을 대화 상자에 통합 합니다.

1. 클래스 **마법사** 를 사용 하는 경우 클래스는 클래스에서 상속 되기 때문에 대화 상자 템플릿에 새 단추 컨트롤을 삽입 `CMFCColorPickerCtrl` `CButton` 합니다.

1. 새 단추 컨트롤과 연결 된 멤버 변수를 대화 상자 클래스에 삽입 합니다. 그런 다음 변수 유형을에서로 변경 합니다 `CButton` `CMFCColorPickerCtrl` .

1. `WM_INITDIALOG`대화 상자 클래스에 대 한 메시지 처리기를 삽입 합니다. 처리기에서 컨트롤의 형식, 색상표 및 초기 선택 된 색을 설정 `CMFCColorPickerCtrl` 합니다.

## <a name="example"></a>예제

다음 예제에서는 `CMFCColorPickerCtrl` 클래스에서 다양 한 메서드를 사용 하 여 개체를 구성 하는 방법을 보여 줍니다 `CMFCColorPickerCtrl` . 이 예제에서는 선택 컨트롤의 형식과 색, 색상, 광도 및 채도를 설정 하는 방법을 보여 줍니다. 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxcolorpickerctrl

## <a name="cmfccolorpickerctrlcmfccolorpickerctrl"></a><a name="cmfccolorpickerctrl"></a> Cmfccolor을 Kerctrl:: CMFCColorPickerCtrl

`CMFCColorPickerCtrl` 개체를 생성합니다.

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfccolorpickerctrldrawcursor"></a><a name="drawcursor"></a> Cmfccolorrawcursor Ctrl::D

선택한 색을 가리키는 커서가 표시 되기 전에 프레임 워크에서 호출 됩니다.

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 선택한 색 둘레의 사각형 영역을 지정 합니다.

### <a name="remarks"></a>설명

선택한 색을 가리키는 커서의 셰이프를 변경 해야 하는 경우이 메서드를 재정의 합니다.

## <a name="cmfccolorpickerctrlgetcolor"></a><a name="getcolor"></a> CMFCColorPickerCtrl:: GetColor

사용자가 선택 하는 색을 검색 합니다.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>반환 값

선택한 색의 RGB 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorpickerctrlgethls"></a><a name="gethls"></a> CMFCColorPickerCtrl:: GetHLS

사용자가 선택 하는 색의 색조, 광도 및 채도 값을 검색 합니다.

```cpp
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>매개 변수

*]*<br/>
제한이 색상 정보를 받는 double 형식의 변수에 대 한 포인터입니다.

*광도가*<br/>
제한이 광도 정보를 받는 double 형식의 변수에 대 한 포인터입니다.

*초과할*<br/>
제한이 채도 정보를 받는 double 형식의 변수에 대 한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorpickerctrlgethue"></a><a name="gethue"></a> CMFCColorPickerCtrl:: GetHue

사용자가 선택 하는 색의 색상 구성 요소를 검색 합니다.

```
double GetHue() const;
```

### <a name="return-value"></a>반환 값

선택한 색의 색상 구성 요소입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorpickerctrlgetluminance"></a><a name="getluminance"></a> CMFCColorPickerCtrl:: GetLuminance

사용자가 선택 하는 색의 광도 구성 요소를 검색 합니다.

```
double GetLuminance() const;
```

### <a name="return-value"></a>반환 값

선택한 색의 광도 구성 요소입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorpickerctrlgetsaturation"></a><a name="getsaturation"></a> CMFCColorPickerCtrl:: GetSaturation

사용자가 선택 하는 색의 채도 값을 검색 합니다.

```
double GetSaturation() const;
```

### <a name="return-value"></a>반환 값

선택한 색의 채도 구성 요소입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorpickerctrlselectcellhexagon"></a><a name="selectcellhexagon"></a> CMFCColorPickerCtrl:: SelectCellHexagon

현재 색을 지정 된 RGB 색 구성 요소나 지정 된 셀 육각형으로 정의 된 색으로 설정 합니다.

```cpp
void SelectCellHexagon(
    BYTE R,
    BYTE G,
    BYTE B);

BOOL SelectCellHexagon(
    int x,
    int y);
```

### <a name="parameters"></a>매개 변수

*R*<br/>
진행 빨간색 색 구성 요소입니다.

*Express-g*<br/>
진행 녹색 색 구성 요소입니다.

*B*<br/>
진행 파랑 색 구성 요소입니다.

*x*<br/>
진행 셀 육각형을 가리키는 커서의 x 좌표입니다.

*y*<br/>
진행 셀 육각형을 가리키는 커서의 y 좌표입니다.

### <a name="return-value"></a>반환 값

이 메서드의 두 번째 오버 로드는 항상 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드의 첫 번째 오버 로드는 현재 색을 색 선택 컨트롤의 지정 된 빨강, 녹색 및 파랑 색 구성 요소에 해당 하는 색으로 설정 합니다.

이 메서드의 두 번째 오버 로드는 현재 색을 지정 된 커서 위치가 가리키는 셀 육각형의 색으로 설정 합니다.

## <a name="cmfccolorpickerctrlsetcolor"></a><a name="setcolor"></a> CMFCColorPickerCtrl:: SetColor

현재 색을 지정 된 RGB 색 값으로 설정 합니다.

```cpp
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>매개 변수

*색상*<br/>
진행 RGB 색 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorpickerctrlsethls"></a><a name="sethls"></a> CMFCColorPickerCtrl:: SetHLS

현재 색을 지정 된 HLS 색 값으로 설정 합니다.

```cpp
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>매개 변수

*]*<br/>
진행 색상 값입니다.

*광도가*<br/>
진행 광도 값입니다.

*초과할*<br/>
진행 채도 값입니다.

*bInvalidate*<br/>
진행 창이 새 색으로 즉시 업데이트 되도록 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorpickerctrlsethue"></a><a name="sethue"></a> CMFCColorPickerCtrl:: SetHue

현재 선택 된 색의 색상을 변경 합니다.

```cpp
void SetHue(double Hue);
```

### <a name="parameters"></a>매개 변수

*Hue*<br/>
진행 색상 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorpickerctrlsetluminance"></a><a name="setluminance"></a> CMFCColorPickerCtrl:: SetLuminance

현재 선택 된 색의 광도를 변경 합니다.

```cpp
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>매개 변수

*광도*<br/>
진행 광도 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorpickerctrlsetluminancebarwidth"></a><a name="setluminancebarwidth"></a> CMFCColorPickerCtrl:: SetLuminanceBarWidth

색 선택 컨트롤에서 광도 막대의 너비를 설정 합니다.

```cpp
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>매개 변수

*w*<br/>
진행 측정 된 광도 막대의 너비 (픽셀)입니다.

### <a name="remarks"></a>설명

색 선택 컨트롤의 **사용자 지정** 탭에 있는 광도 표시줄의 크기를 조정 하려면이 메서드를 사용 합니다. *W* 매개 변수는 광도 막대의 새 너비를 지정 합니다. 너비 값은 클라이언트 영역 너비의 3/4 3 개를 초과 하면 무시 됩니다.

## <a name="cmfccolorpickerctrlsetoriginalcolor"></a><a name="setoriginalcolor"></a> CMFCColorPickerCtrl:: SetOriginalColor

초기 선택 된 색을 설정 합니다.

```cpp
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>매개 변수

*ref*<br/>
진행 RGB 색 값입니다.

### <a name="remarks"></a>설명

색 선택 컨트롤이 초기화 되 면이 메서드를 호출 합니다.

## <a name="cmfccolorpickerctrlsetpalette"></a><a name="setpalette"></a> CMFCColorPickerCtrl:: SetPalette

현재 색상표를 설정 합니다.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>매개 변수

*pPalette*<br/>
진행 색상표에 대 한 포인터입니다.

### <a name="remarks"></a>설명

색상표는 색 선택 컨트롤에 표시 되는 색 배열을 정의 합니다.

## <a name="cmfccolorpickerctrlsetsaturation"></a><a name="setsaturation"></a> CMFCColorPickerCtrl:: SetSaturation

현재 선택 된 색의 채도를 변경 합니다.

```cpp
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>매개 변수

*채도*<br/>
진행 채도 값입니다.

### <a name="remarks"></a>설명

## <a name="cmfccolorpickerctrlsettype"></a><a name="settype"></a> CMFCColorPickerCtrl:: SetType

표시할 색 선택 컨트롤의 형식을 설정 합니다.

```cpp
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>매개 변수

*colorType*<br/>
진행 색 선택 컨트롤 형식입니다.

형식은 열거형에 의해 정의 됩니다 `CMFCColorPickerCtrl::COLORTYPE` . 가능한 형식은 광도, 선택, HEX 및 HEX_GREYSCALE입니다. 기본 유형은 선택기입니다.

### <a name="remarks"></a>설명

색 선택 컨트롤 형식을 지정 하려면 Windows 컨트롤을 만들기 전에이 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog 클래스](../../mfc/reference/cmfccolordialog-class.md)
