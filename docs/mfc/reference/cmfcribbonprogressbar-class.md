---
description: '자세한 정보: Cmfc리본 Progressbar 클래스'
title: Cmfc리본 Progressbar 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
ms.openlocfilehash: b4e91a604386a57aa7cac59294c569635583304c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321763"
---
# <a name="cmfcribbonprogressbar-class"></a>Cmfc리본 Progressbar 클래스

긴 작업의 진행률을 시각적으로 나타내는 컨트롤을 구현합니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Cmfc리본 Progressbar:: Cmfc리본 Progressbar](#cmfcribbonprogressbar)|`CMFCRibbonProgressBar` 개체를 생성하고 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[Cmfc리본 Progressbar:: GetPos](#getpos)|현재 진행 상태를 반환 합니다.|
|[Cmfc리본 Progressbar:: GetRangeMax](#getrangemax)|현재 범위의 최 댓 값을 반환 합니다.|
|[Cmfc리본 Progressbar:: GetRangeMin](#getrangemin)|현재 범위의 최 솟 값을 반환 합니다.|
|[Cmfc리본 Progressbar:: GetRegularSize](#getregularsize)|리본 요소의 보통 크기를 반환합니다. [Cmfc리본 Baseelement:: GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)를 재정의 합니다.|
|[Cmfc리본 Progressbar:: IsInfiniteMode](#isinfinitemode)|진행률 표시줄이 무한 모드에서 작동 하는지 여부를 지정 합니다.|
|[Cmfc리본 Progressbar:: OnDraw](#ondraw)|리본 요소를 그리기 위해 프레임워크에서 호출됩니다. [Cmfc리본 Baseelement:: OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw)를 재정의 합니다.|
|[Cmfc리본 Progressbar:: SetInfiniteMode](#setinfinitemode)|진행률 표시줄이 무한 모드에서 작동 하도록 설정 합니다.|
|[Cmfc리본 Progressbar:: SetPos](#setpos)|현재 진행 상태를 설정 합니다.|
|[Cmfc리본 Progressbar:: SetRange](#setrange)|최소값과 최대값을 설정 합니다.|

## <a name="remarks"></a>설명

는 `CMFCRibbonProgressBar` 일반 및 무한 모드의 두 가지 모드로 작동할 수 있습니다. 일반 모드에서 진행률 표시줄은 왼쪽에서 오른쪽으로 채워지고 최 댓 값에 도달 하면 중지 됩니다. 무한 모드에서 진행률 표시줄은 최소값에서 최 댓 값으로 반복적으로 채워집니다. 무한 모드를 사용 하 여 작업이 진행 중이지만 완료 시간을 알 수 없음을 나타낼 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 `CMFCRibbonProgressBar` 클래스에서 다양한 메서드를 사용하는 방법을 보여 줍니다. 이 예제에서는 진행률 표시줄을 무한 모드에서 작동 하도록 설정 하는 방법 (작업 완료 시간을 알 수 없음)을 설정 하 고 진행률 표시줄의 최소값과 최대값을 설정 하 고 진행률 표시줄의 현재 위치를 설정 하는 방법을 보여 줍니다. 이 코드 조각은 [MS Office 2007 Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxRibbonProgressBar

## <a name="cmfcribbonprogressbarcmfcribbonprogressbar"></a><a name="cmfcribbonprogressbar"></a> Cmfc리본 Progressbar:: Cmfc리본 Progressbar

[Cmfc리본 progressbar](../../mfc/reference/cmfcribbonprogressbar-class.md) 개체를 생성 하 고 초기화 합니다.

```
CMFCRibbonProgressBar();

CMFCRibbonProgressBar(
    UINT nID,
    int nWidth = 90,
    int nHeight = 22);
```

### <a name="parameters"></a>매개 변수

*nID*<br/>
진행 리본 진행률 표시줄의 명령 ID를 지정 합니다.

*nWidth*<br/>
진행 리본 진행률 표시줄의 너비를 픽셀 단위로 지정 합니다.

*nHeight*<br/>
진행 리본 진행률 표시줄의 높이 (픽셀 단위)를 지정 합니다.

## <a name="cmfcribbonprogressbargetpos"></a><a name="getpos"></a> Cmfc리본 Progressbar:: GetPos

진행률 표시줄의 현재 위치를 반환 합니다.

```
int GetPos () const;
```

### <a name="return-value"></a>반환 값

진행률 표시줄의 현재 위치를 나타내는 값입니다.

### <a name="remarks"></a>설명

설정 되는 범위는 [Cmfc리본 progressbar:: SetRange](#setrange) 메서드에 지정 된 범위 내에 있어야 합니다.

## <a name="cmfcribbonprogressbargetrangemax"></a><a name="getrangemax"></a> Cmfc리본 Progressbar:: GetRangeMax

진행률 표시줄의 현재 최대값을 반환 합니다.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>반환 값

현재 범위의 최대값입니다.

### <a name="remarks"></a>설명

## <a name="cmfcribbonprogressbargetrangemin"></a><a name="getrangemin"></a> Cmfc리본 Progressbar:: GetRangeMin

진행률 표시줄의 현재 최소 범위 값을 반환 합니다.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>반환 값

현재 범위의 최소값입니다.

## <a name="cmfcribbonprogressbargetregularsize"></a><a name="getregularsize"></a> Cmfc리본 Progressbar:: GetRegularSize

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcribbonprogressbarisinfinitemode"></a><a name="isinfinitemode"></a> Cmfc리본 Progressbar:: IsInfiniteMode

진행률 표시줄이 무한 모드에서 작동 하는지 여부를 지정 합니다.

```
BOOL IsInfiniteMode() const;
```

### <a name="return-value"></a>반환 값

진행률 표시줄이 무한 모드 이면 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

무한 모드에서 진행률 표시줄은 최소값에서 최 댓 값으로 반복적으로 채워집니다. 무한 모드를 사용 하 여 작업이 진행 중이지만 완료 시간을 알 수 없음을 나타낼 수 있습니다.

## <a name="cmfcribbonprogressbarondraw"></a><a name="ondraw"></a> Cmfc리본 Progressbar:: OnDraw

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>

### <a name="remarks"></a>설명

## <a name="cmfcribbonprogressbarsetinfinitemode"></a><a name="setinfinitemode"></a> Cmfc리본 Progressbar:: SetInfiniteMode

진행률 표시줄이 무한 모드에서 작동 하도록 설정 합니다.

```cpp
void SetInfiniteMode(BOOL bSet = TRUE);
```

### <a name="parameters"></a>매개 변수

*bSet*<br/>
진행 진행률 표시줄이 무한 모드 임을 지정 하려면 TRUE로 설정 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

일반적으로 진행률 표시줄이 무한 모드 이면 작업이 진행 중이지만 완료 시간을 알 수 없음을 사용자에 게 알려 주는 것입니다. 따라서 진행률 표시줄은 최소값에서 최 댓 값으로 반복적으로 채워집니다.

## <a name="cmfcribbonprogressbarsetpos"></a><a name="setpos"></a> Cmfc리본 Progressbar:: SetPos

진행률 표시줄의 현재 위치를 설정 합니다.

```cpp
void SetPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>매개 변수

*nPos*<br/>
진행 진행률 표시줄이 설정 되는 위치를 지정 합니다.

*bRedraw*<br/>
진행 진행률 표시줄을 다시 그려야 할지 여부를 지정 합니다.

### <a name="remarks"></a>설명

설정 되는 범위는 [Cmfc리본 progressbar:: SetRange](#setrange) 메서드에 지정 된 범위 내에 있어야 합니다.

## <a name="cmfcribbonprogressbarsetrange"></a><a name="setrange"></a> Cmfc리본 Progressbar:: SetRange

진행률 표시줄의 최소값과 최대값을 설정 합니다.

```cpp
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>매개 변수

*nMin*<br/>
진행 범위의 최 솟 값을 지정 합니다.

*nMax*<br/>
진행 범위의 최대값을 지정 합니다.

### <a name="remarks"></a>설명

최소 및 최대 값을 설정 하 여 진행률 표시줄의 범위를 정의 하려면이 메서드를 사용 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 Baseelement 클래스](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[Cmfc리본 표시줄 클래스](../../mfc/reference/cmfcribbonbar-class.md)
