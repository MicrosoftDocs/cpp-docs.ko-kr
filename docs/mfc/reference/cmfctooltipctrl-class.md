---
description: '자세히 알아보기: CMFCToolTipCtrl 클래스'
title: CMFCToolTipCtrl 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetIconSize
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetParams
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawBorder
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawLabel
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnFillBackground
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetFixedWidth
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetHotRibbonButton
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetLocation
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetParams
helpviewer_keywords:
- CMFCToolTipCtrl [MFC], GetIconSize
- CMFCToolTipCtrl [MFC], GetParams
- CMFCToolTipCtrl [MFC], OnDrawBorder
- CMFCToolTipCtrl [MFC], OnDrawDescription
- CMFCToolTipCtrl [MFC], OnDrawIcon
- CMFCToolTipCtrl [MFC], OnDrawLabel
- CMFCToolTipCtrl [MFC], OnDrawSeparator
- CMFCToolTipCtrl [MFC], OnFillBackground
- CMFCToolTipCtrl [MFC], SetDescription
- CMFCToolTipCtrl [MFC], SetFixedWidth
- CMFCToolTipCtrl [MFC], SetHotRibbonButton
- CMFCToolTipCtrl [MFC], SetLocation
- CMFCToolTipCtrl [MFC], SetParams
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
ms.openlocfilehash: 918a702a94f2847298d86868d35b2bad65b65b33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331692"
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl 클래스

[CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)를 기반으로 하는 확장된 도구 설명 구현입니다. `CMFCToolTipCtrl` 클래스 기반의 도구 설명은 아이콘, 레이블 및 설명을 표시할 수 있습니다. 그라데이션 채우기, 사용자 지정 텍스트와 테두리 색, 굵은 텍스트, 둥근 모서리 또는 풍선 스타일을 사용하여 시각적인 모양을 사용자 지정할 수 있습니다.

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```cpp
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|기본 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|도구 설명에 아이콘 크기를 반환합니다.|
|[CMFCToolTipCtrl::GetParams](#getparams)|도구 설명의 표시 설정을 반환합니다.|
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|도구 설명의 테두리를 그립니다.|
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|도구 설명에 아이콘을 표시합니다.|
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|도구 설명의 레이블을 그리거나 레이블의 크기를 계산합니다.|
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|도구 설명에서 레이블과 설명 사이에 구분 기호를 그립니다.|
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|도구 설명 배경을 채웁니다.|
|[CMFCToolTipCtrl::SetDescription](#setdescription)|도구 설명에 표시할 설명을 설정합니다.|
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl::SetLocation](#setlocation)||
|[CMFCToolTipCtrl::SetParams](#setparams)|`CMFCToolTipInfo` 개체를 사용하여 도구 설명의 시각적 모양을 지정합니다.|

## <a name="remarks"></a>설명

`CMFCToolTipCtrl`, `CMFCToolTipInfo` 및 [CTooltipManager 클래스](../../mfc/reference/ctooltipmanager-class.md) 개체를 함께 사용 하 여 응용 프로그램에 사용자 지정 도구 설명을 구현 합니다.

예를 들어 풍선 스타일의 도구 설명을 사용하려면 다음 단계를 수행합니다.

1. [CWinAppEx Class](../../mfc/reference/cwinappex-class.md) 메서드를 사용 하 여 응용 프로그램에서 도구 설명 관리자를 초기화 합니다.

2. `CMFCToolTipInfo` 구조체를 만들어 원하는 시각적 스타일을 지정합니다.

    ```cpp
    CMFCToolTipInfo params;
    params.m_bBoldLabel = FALSE;
    params.m_bDrawDescription = FALSE;
    params.m_bDrawIcon = FALSE;
    params.m_bRoundedCorners = TRUE;
    params.m_bDrawSeparator = FALSE;
    if (m_bCustomColors)
    {
        params.m_clrFill = RGB (255, 255, 255);
        params.m_clrFillGradient = RGB (228, 228, 240);
        params.m_clrText = RGB (61, 83, 80);
        params.m_clrBorder = RGB (144, 149, 168);

    }
    ```

3. [CTooltipManager:: SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) 메서드를 사용 하 여 개체에 정의 된 스타일을 사용 하 여 응용 프로그램의 모든 도구 설명에 대 한 비주얼 스타일을 설정 합니다 `CMFCToolTipInfo` .

    ```cpp
    theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
        RUNTIME_CLASS (CMFCToolTipCtrl), &params);
    ```

`CMFCToolTipCtrl`에서 새 클래스를 파생시켜 도구 설명 동작과 렌더링을 제어할 수도 있습니다. 새 도구 설명 컨트롤 클래스를 지정하려면 `CTooltipManager::SetTooltipParams` 메서드를 사용합니다.

```cpp
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```

기본 도구 설명 컨트롤 클래스를 복원하고 도구 설명 모양을 기본 상태로 다시 설정하려면 `SetTooltipParams`의 런타임 클래스 및 도구 설명 정보 매개 변수에 NULL을 지정합니다.

```cpp
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    NULL,
    NULL);
```

## <a name="example"></a>예제

다음 예제에서는 `CMFCToolTipCtrl` 개체를 생성하고, 도구 설명에 표시되는 설명을 설정하고, 도구 설명 컨트롤의 너비를 설정하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxtooltipctrl

## <a name="cmfctooltipctrlcmfctooltipctrl"></a><a name="cmfctooltipctrl"></a> CMFCToolTipCtrl:: CMFCToolTipCtrl

```cpp
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>매개 변수

진행 *Pparams*<br/>

### <a name="remarks"></a>설명

## <a name="cmfctooltipctrlgeticonsize"></a><a name="geticonsize"></a> CMFCToolTipCtrl:: GetIconSize

도구 설명에 아이콘 크기를 반환합니다.

```cpp
virtual CSize GetIconSize();
```

### <a name="return-value"></a>반환 값

아이콘의 크기 (픽셀)입니다.

## <a name="cmfctooltipctrlgetparams"></a><a name="getparams"></a> CMFCToolTipCtrl:: GetParams

도구 설명의 표시 설정을 반환합니다.

```cpp
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>반환 값

[CMFCToolTipInfo 클래스](../../mfc/reference/cmfctooltipinfo-class.md) 개체에 저장 된 현재 도구 설명 표시 설정입니다.

## <a name="cmfctooltipctrlondrawborder"></a><a name="ondrawborder"></a> CMFCToolTipCtrl:: OnDrawBorder

도구 설명의 테두리를 그립니다.

```cpp
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 도구 설명의 경계 사각형입니다.

*clrLine*<br/>
진행 테두리 색입니다.

### <a name="remarks"></a>설명

파생 클래스에서이 메서드를 재정의 하 여 도구 설명 테두리의 모양을 사용자 지정 합니다.

## <a name="cmfctooltipctrlondrawdescription"></a><a name="ondrawdescription"></a> CMFCToolTipCtrl:: OnDrawDescription

```cpp
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>매개 변수

진행 *pDC*<br/>
[in] *rect*<br/>
진행 *Bcalit*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfctooltipctrlondrawicon"></a><a name="ondrawicon"></a> CMFCToolTipCtrl:: OnDrawIcon

도구 설명에 아이콘을 표시합니다.

```cpp
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rectImage*<br/>
진행 아이콘의 좌표입니다.

### <a name="return-value"></a>반환 값

아이콘을 그린 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

사용자 지정 아이콘을 표시 하려면 파생 클래스에서이 메서드를 재정의 합니다. 또한 [CMFCToolTipCtrl:: GetIconSize](#geticonsize) 를 재정의 하 여 도구 설명에서 텍스트 및 설명의 레이아웃을 올바르게 계산 하도록 해야 합니다.

## <a name="cmfctooltipctrlondrawlabel"></a><a name="ondrawlabel"></a> CMFCToolTipCtrl:: OnDrawLabel

도구 설명의 레이블을 그리거나 레이블의 크기를 계산합니다.

```cpp
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 레이블 영역의 경계 사각형입니다.

*bCalcOnly*<br/>
진행 TRUE 이면 레이블이 그려지지 않습니다.

### <a name="return-value"></a>반환 값

레이블의 크기 (픽셀)입니다.

### <a name="remarks"></a>설명

도구 설명 레이블의 모양을 사용자 지정 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="cmfctooltipctrlondrawseparator"></a><a name="ondrawseparator"></a> CMFCToolTipCtrl:: OnDrawSeparator

도구 설명에서 레이블과 설명 사이에 구분 기호를 그립니다.

```cpp
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*x*<br/>
진행 구분 기호의 왼쪽 끝에 대 한 가로 좌표입니다.

*x2*<br/>
진행 구분 기호 오른쪽 끝의 가로 좌표입니다.

*예*<br/>
진행 구분 기호의 세로 좌표입니다.

### <a name="remarks"></a>설명

기본 구현에서는 점 (x1, y)에서 지점 (x2, y)으로 줄을 그립니다.

구분 기호 모양을 사용자 지정 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="cmfctooltipctrlonfillbackground"></a><a name="onfillbackground"></a> CMFCToolTipCtrl:: OnFillBackground

도구 설명 배경을 채웁니다.

```cpp
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rect*<br/>
진행 채울 영역의 경계 사각형을 지정 합니다.

*clrText*<br/>
진행 도구 설명 전경색입니다.

*clrLine*<br/>
진행 레이블과 설명 사이에 있는 테두리와 구분 기호 선의 색입니다.

### <a name="remarks"></a>설명

기본 구현은 *rect* 로 지정 된 사각형을 [CMFCToolTipCtrl:: setparams](#setparams)에 대 한 가장 최근의 호출로 지정 된 색 또는 패턴으로 채웁니다.

도구 설명의 모양을 사용자 지정 하려면 파생 클래스에서이 메서드를 재정의 합니다.

## <a name="cmfctooltipctrlsetdescription"></a><a name="setdescription"></a> CMFCToolTipCtrl:: SetDescription

도구 설명에 표시할 설명을 설정합니다.

```cpp
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>매개 변수

*strDesrciption*<br/>
진행 설명 텍스트입니다.

### <a name="remarks"></a>설명

설명 텍스트가 도구 설명의 구분 기호 아래에 표시 됩니다.

## <a name="cmfctooltipctrlsetfixedwidth"></a><a name="setfixedwidth"></a> CMFCToolTipCtrl:: SetFixedWidth

```cpp
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>매개 변수

진행 *Nwidthregular*<br/>
진행 *nWidthLargeImage*<br/>

### <a name="remarks"></a>설명

## <a name="cmfctooltipctrlsethotribbonbutton"></a><a name="sethotribbonbutton"></a> CMFCToolTipCtrl:: SetHotRibbonButton

```cpp
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>매개 변수

진행 방법 *Bbonbutton*<br/>

### <a name="remarks"></a>설명

## <a name="cmfctooltipctrlsetlocation"></a><a name="setlocation"></a> CMFCToolTipCtrl:: SetLocation

```cpp
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>매개 변수

진행 *pt*<br/>

### <a name="remarks"></a>설명

## <a name="cmfctooltipctrlsetparams"></a><a name="setparams"></a> CMFCToolTipCtrl:: SetParams

[CMFCToolTipInfo 클래스](../../mfc/reference/cmfctooltipinfo-class.md) 개체를 사용 하 여 도구 설명의 시각적 모양을 지정 합니다.

```cpp
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>매개 변수

*pParams*<br/>
진행 표시 매개 변수를 포함 하는 [CMFCToolTipInfo 클래스](../../mfc/reference/cmfctooltipinfo-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

도구 설명이 표시 될 때마다 *Pparams* 가 지정 하는 색 및 비주얼 스타일을 사용 하 여 그려집니다. *Pparams* 의 값은 protected 멤버에 저장 됩니다 .이 멤버는 `m_Params` [CMFCToolTipCtrl:: ondrawborder](#ondrawborder), [CMFCToolTipCtrl:: ondrawborder](#ondrawicon), [CMFCToolTipCtrl:: Ondrawborder](#ondrawlabel), [CMFCToolTipCtrl:: ondrawborder](#ondrawseparator)또는 [CMFCToolTipCtrl:: ondrawborder](#onfillbackground) 를 재정의 하는 파생 클래스에서 액세스 하 여 지정 된 모양을 유지할 수 있습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CToolTipCtrl 클래스](../../mfc/reference/ctooltipctrl-class.md)<br/>
[CTooltipManager 클래스](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipInfo 클래스](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)
