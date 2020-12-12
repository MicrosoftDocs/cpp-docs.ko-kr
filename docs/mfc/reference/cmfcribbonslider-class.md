---
description: '자세한 정보: Cmfc리본 슬라이더 클래스'
title: Cmfc리본 슬라이더 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
ms.openlocfilehash: d125afdf961d97c0501742acdc75d7802c7e104d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321736"
---
# <a name="cmfcribbonslider-class"></a>Cmfc리본 슬라이더 클래스

`CMFCRibbonSlider`클래스는 리본 표시줄 또는 리본 상태 표시줄에 추가할 수 있는 슬라이더 컨트롤을 구현 합니다. 리본 슬라이더 컨트롤은 Office 2007 애플리케이션의 확대/축소 슬라이더와 유사합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonSlider : public CMFCRibbonBaseElement
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Cmfc리본 슬라이더:: Cmfc리본 슬라이더](#cmfcribbonslider)|리본 슬라이더 컨트롤을 생성 하 고 초기화 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Cmfc리본 슬라이더:: GetPos](#getpos)|슬라이더 컨트롤의 현재 위치를 반환 합니다.|
|[Cmfc리본 슬라이더:: GetRangeMax](#getrangemax)|슬라이더의 최대값을 반환 합니다.|
|[Cmfc리본 슬라이더:: GetRangeMin](#getrangemin)|슬라이더의 최 솟 값을 반환 합니다.|
|[Cmfc리본 슬라이더:: GetRegularSize](#getregularsize)|리본 요소의 보통 크기를 반환합니다. [Cmfc리본 Baseelement:: GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)를 재정의 합니다.|
|[Cmfc리본 슬라이더:: GetZoomIncrement](#getzoomincrement)|슬라이더 컨트롤에 대 한 확대/축소 증가값의 크기를 반환 합니다.|
|[Cmfc리본 슬라이더:: Has확대 단추](#haszoombuttons)|슬라이더에 확대/축소 단추가 있는지 여부를 지정 합니다.|
|[Cmfc리본 슬라이더:: OnDraw](#ondraw)|리본 요소를 그리기 위해 프레임워크에서 호출됩니다. [Cmfc리본 Baseelement:: OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw)를 재정의 합니다.|
|[Cmfc리본 슬라이더:: SetPos](#setpos)|슬라이더 컨트롤의 현재 위치를 설정 합니다.|
|[Cmfc리본 슬라이더:: SetRange](#setrange)|최소값과 최대값을 설정 하 여 슬라이더 컨트롤의 범위를 지정 합니다.|
|[Cmfc리본 슬라이더:: Set확대 단추](#setzoombuttons)|확대/축소 단추를 표시 하거나 숨깁니다.|
|[Cmfc리본 슬라이더:: SetZoomIncrement](#setzoomincrement)|슬라이더 컨트롤에 대 한 확대/축소 증가값의 크기를 설정 합니다.|

## <a name="remarks"></a>설명

메서드를 사용 하 여 `SetRange` 슬라이더에 대 한 확대/축소 범위를 구성할 수 있습니다. 메서드를 사용 하 여 슬라이더의 현재 위치를 설정할 수 있습니다 `SetPos` .

메서드를 사용 하 여 슬라이더 컨트롤의 왼쪽과 오른쪽에 원형 확대/축소 단추를 표시할 수 있습니다 `SetZoomButtons` . 기본적으로 슬라이더는 가로 방향으로, 왼쪽 확대/축소 단추에는 빼기 기호가 표시 되 고 오른쪽 확대/축소 단추에는 더하기 기호가 표시 됩니다.

`SetZoomIncrement`메서드는 사용자가 확대/축소 단추를 클릭할 때 현재 위치에서 더하거나 뺄 증가값을 정의 합니다.

## <a name="example"></a>예제

다음 예제에서는 클래스에서 다양 한 메서드를 사용 하 여 슬라이더의 속성을 설정 하는 방법을 보여 줍니다 `CMFCRibbonSlider` . 예제에서는 개체를 생성 하 고 `CMFCRibbonSlider` , 확대/축소 단추를 표시 하 고, 슬라이더 컨트롤의 현재 위치를 설정 하 고, 슬라이더 컨트롤에 대 한 값 범위를 설정 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxribbonslider

## <a name="cmfcribbonslidercmfcribbonslider"></a><a name="cmfcribbonslider"></a> Cmfc리본 슬라이더:: Cmfc리본 슬라이더

리본 슬라이더를 구성 합니다.

```
CMFCRibbonSlider(
    UINT nID,
    int nWidth=100);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
진행 슬라이더 ID입니다.

[in]. *Nwidth* 슬라이더 너비 (픽셀)입니다.

### <a name="remarks"></a>설명

슬라이더가 추가 된 패널 범주에서 *너비가* 픽셀 너비 인 리본 슬라이더를 생성 합니다. 기본적으로 슬라이더는 가로 방향입니다.

## <a name="cmfcribbonslidergetpos"></a><a name="getpos"></a> Cmfc리본 슬라이더:: GetPos

슬라이더 컨트롤의 현재 위치를 반환 합니다.

```
int GetPos() const;
```

### <a name="return-value"></a>반환 값

슬라이더의 시작 부분을 기준으로 하는 슬라이더 컨트롤의 현재 위치입니다.

## <a name="cmfcribbonslidergetrangemax"></a><a name="getrangemax"></a> Cmfc리본 슬라이더:: GetRangeMax

슬라이더가 슬라이더 컨트롤에서 이동할 수 있는 슬라이더의 최대 증가값을 가져옵니다.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>반환 값

슬라이더가 슬라이더 컨트롤에서 이동할 수 있는 슬라이더의 최대 증가값입니다.

## <a name="cmfcribbonslidergetrangemin"></a><a name="getrangemin"></a> Cmfc리본 슬라이더:: GetRangeMin

슬라이더가 슬라이더 컨트롤에서 이동할 수 있는 최소 증가값을 반환 합니다.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>반환 값

슬라이더가 슬라이더 컨트롤에서 이동할 수 있는 최소 증가값입니다.

## <a name="cmfcribbonslidergetregularsize"></a><a name="getregularsize"></a> Cmfc리본 슬라이더:: GetRegularSize

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonslidergetzoomincrement"></a><a name="getzoomincrement"></a> Cmfc리본 슬라이더:: GetZoomIncrement

슬라이더 컨트롤에 대 한 확대/축소 증가값을 가져옵니다.

```
int GetZoomIncrement() const;
```

### <a name="return-value"></a>반환 값

슬라이더 컨트롤의 확대/축소 증가값입니다.

## <a name="cmfcribbonsliderhaszoombuttons"></a><a name="haszoombuttons"></a> Cmfc리본 슬라이더:: Has확대 단추

슬라이더에 확대/축소 단추가 있는지 여부를 지정 합니다.

```
BOOL HasZoomButtons() const;
```

### <a name="return-value"></a>반환 값

슬라이더에 확대/축소 단추가 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cmfcribbonsliderondraw"></a><a name="ondraw"></a> Cmfc리본 슬라이더:: OnDraw

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcribbonslidersetpos"></a><a name="setpos"></a> Cmfc리본 슬라이더:: SetPos

슬라이더 컨트롤의 현재 위치를 설정 합니다.

```cpp
void SetPos(
    int nPos,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
진행 슬라이더에 대해 설정할 위치를 지정 합니다. 위치는 슬라이더의 시작 부분을 기준으로 합니다.

*bRedraw*<br/>
진행 TRUE 이면 슬라이더가 다시 그려집니다.

## <a name="cmfcribbonslidersetrange"></a><a name="setrange"></a> Cmfc리본 슬라이더:: SetRange

슬라이더 컨트롤에 대 한 값의 범위를 설정 합니다.

```cpp
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>매개 변수

*nMin*<br/>
진행 슬라이더 컨트롤의 최 솟 값을 지정 합니다.

*nMax*<br/>
진행 슬라이더 컨트롤의 최대값을 지정 합니다.

### <a name="remarks"></a>설명

최소값과 최대값을 설정 하 여 슬라이더 컨트롤에 대 한 값의 범위를 지정 합니다.

## <a name="cmfcribbonslidersetzoombuttons"></a><a name="setzoombuttons"></a> Cmfc리본 슬라이더:: Set확대 단추

확대/축소 단추를 표시 하거나 숨깁니다.

```cpp
void SetZoomButtons(BOOL bSet=TRUE);
```

### <a name="parameters"></a>매개 변수

[in]. *bSet* 확대/축소 단추를 표시 하려면 TRUE로 설정 합니다. 숨기려면 FALSE로 설정 합니다.

## <a name="cmfcribbonslidersetzoomincrement"></a><a name="setzoomincrement"></a> Cmfc리본 슬라이더:: SetZoomIncrement

슬라이더 컨트롤에 대 한 확대/축소 증가값을 설정 합니다.

```cpp
void SetZoomIncrement(int nZoomIncrement);
```

### <a name="parameters"></a>매개 변수

*nZoomIncrement*<br/>
진행 슬라이더 컨트롤의 확대/축소 증가값을 지정 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 Baseelement 클래스](../../mfc/reference/cmfcribbonbaseelement-class.md)
