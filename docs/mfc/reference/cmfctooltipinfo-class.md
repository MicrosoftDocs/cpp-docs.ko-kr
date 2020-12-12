---
description: '자세히 알아보기: CMFCToolTipInfo 클래스'
title: CMFCToolTipInfo 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBalloonTooltip
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBoldLabel
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bRoundedCorners
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bVislManagerTheme
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrBorder
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFill
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFillGradient
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrText
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nGradientAngle
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nMaxDescrWidth
helpviewer_keywords:
- CMFCToolTipInfo [MFC], m_bBalloonTooltip
- CMFCToolTipInfo [MFC], m_bBoldLabel
- CMFCToolTipInfo [MFC], m_bDrawDescription
- CMFCToolTipInfo [MFC], m_bDrawIcon
- CMFCToolTipInfo [MFC], m_bDrawSeparator
- CMFCToolTipInfo [MFC], m_bRoundedCorners
- CMFCToolTipInfo [MFC], m_bVislManagerTheme
- CMFCToolTipInfo [MFC], m_clrBorder
- CMFCToolTipInfo [MFC], m_clrFill
- CMFCToolTipInfo [MFC], m_clrFillGradient
- CMFCToolTipInfo [MFC], m_clrText
- CMFCToolTipInfo [MFC], m_nGradientAngle
- CMFCToolTipInfo [MFC], m_nMaxDescrWidth
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
ms.openlocfilehash: 06ceca500ad92d5f3a27e2740a298d9c1bbfe1cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143431"
---
# <a name="cmfctooltipinfo-class"></a>CMFCToolTipInfo 클래스

도구 설명의 시각적 모양에 대한 정보를 저장합니다.

## <a name="syntax"></a>구문

```
class CMFCToolTipInfo
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCToolTipInfo::operator=](#operator_eq)||

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CMFCToolTipInfo:: m_bBalloonTooltip](#m_bballoontooltip)|도구 설명이 풍선 모양인지 여부를 나타내는 부울 변수입니다.|
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|도구 설명 레이블이 굵은 글꼴로 표시되는지 여부를 나타내는 부울 변수입니다.|
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|도구 설명이 설명을 포함하는지 여부를 나타내는 부울 변수입니다.|
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|도구 설명이 아이콘을 포함하는지 여부를 나타내는 부울 변수입니다.|
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|도구 설명 레이블과 도구 설명 사이에 구분 기호가 표시되는지 여부를 나타내는 부울 변수입니다.|
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|도구 설명 모서리가 둥근지 여부를 나타내는 부울 변수입니다.|
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|비주얼 관리자가 도구 설명의 모양을 제어 해야 하는지 여부를 나타내는 부울 변수입니다 ( [Cmfcvisualmanager 클래스](../../mfc/reference/cmfcvisualmanager-class.md)참조).|
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|도구 설명 테두리 색입니다.|
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|도구 설명 배경색입니다.|
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|도구 설명의 그라데이션 채우기 색입니다.|
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|도구 설명의 텍스트 색입니다.|
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|도구 설명의 그라데이션 채우기 각도입니다.|
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|도구 설명의 가능한 최대 설명 너비(픽셀)입니다.|

## <a name="remarks"></a>설명

[CMFCToolTipCtrl 클래스](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo` 및 [CTooltipManager 클래스](../../mfc/reference/ctooltipmanager-class.md) 를 함께 사용 하 여 응용 프로그램에 사용자 지정 도구 설명을 구현 합니다. 이러한 도구 설명 클래스를 사용 하는 방법에 대 한 예제는 [CMFCToolTipCtrl 클래스](../../mfc/reference/cmfctooltipctrl-class.md) 항목을 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 `CMFCToolTipInfo` 클래스에서 다양한 멤버 변수의 값을 설정하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxtooltipctrl

## <a name="cmfctooltipinfom_bballoontooltip"></a><a name="m_bballoontooltip"></a> CMFCToolTipInfo:: m_bBalloonTooltip

모든 도구 설명의 표시 스타일을 지정 합니다.

```
BOOL m_bBalloonTooltip;
```

### <a name="remarks"></a>설명

TRUE로 설정 하면 도구 설명에 풍선 스타일이 사용 됨을 나타내고, FALSE는 도구 설명에서 사각형 스타일을 사용 함을 나타냅니다.

## <a name="cmfctooltipinfom_bboldlabel"></a><a name="m_bboldlabel"></a> CMFCToolTipInfo:: m_bBoldLabel

도구 설명 텍스트의 글꼴을 굵게 표시할지 여부를 지정 합니다.

```
BOOL m_bBoldLabel;
```

### <a name="remarks"></a>설명

굵게 글꼴이 포함 된 도구 설명 텍스트를 표시 하려면이 멤버를 TRUE로 설정 하 고, 굵게 글꼴이 아닌 글꼴을 사용 하 여 도구 설명 레이블을 표시 하려면 FALSE로 설정

## <a name="cmfctooltipinfom_bdrawdescription"></a><a name="m_bdrawdescription"></a> CMFCToolTipInfo:: m_bDrawDescription

각 도구 설명에 설명 텍스트가 표시 되는지 여부를 지정 합니다.

```
BOOL m_bDrawDescription;
```

### <a name="remarks"></a>설명

설명을 표시 하려면이 멤버를 TRUE로 설정 하 고 설명을 숨기려면 FALSE로 설정 합니다. [CMFCToolTipCtrl:: SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription) 을 호출 하 여 도구 설명에 대 한 설명을 지정할 수 있습니다.

## <a name="cmfctooltipinfom_bdrawicon"></a><a name="m_bdrawicon"></a> CMFCToolTipInfo:: m_bDrawIcon

모든 도구 설명이 아이콘을 표시 하는지 여부를 지정 합니다.

```
BOOL m_bDrawIcon;
```

### <a name="remarks"></a>설명

각 도구 설명에 아이콘을 표시 하려면이 멤버를 TRUE로 설정 하 고, 아이콘이 없는 도구 설명을 표시 하려면 FALSE로 설정 합니다.

## <a name="cmfctooltipinfom_bdrawseparator"></a><a name="m_bdrawseparator"></a> CMFCToolTipInfo:: m_bDrawSeparator

각 도구 설명의 레이블과 해당 설명 사이에 구분 기호가 있는지 여부를 지정 합니다.

```
BOOL m_bDrawSeparator;
```

### <a name="remarks"></a>설명

도구 설명 레이블과 설명 사이에 구분 기호를 표시 하려면이 멤버를 TRUE로 설정 하 고, 구분 기호 없이 도구 설명을 표시 하려면 FALSE로 설정 합니다.

## <a name="cmfctooltipinfom_broundedcorners"></a><a name="m_broundedcorners"></a> CMFCToolTipInfo:: m_bRoundedCorners

모든 도구 설명에 모퉁이가 둥근 지 여부를 지정 합니다.

```
BOOL m_bRoundedCorners;
```

### <a name="remarks"></a>설명

도구 설명에 둥근 모퉁이를 표시 하려면이 멤버를 TRUE로 설정 하 고 도구 설명에 사각형 모퉁이를 표시 하려면 FALSE로 설정 합니다.

## <a name="cmfctooltipinfom_clrborder"></a><a name="m_clrborder"></a> CMFCToolTipInfo:: m_clrBorder

모든 도구 설명의 테두리 색을 지정 합니다.

```
COLORREF m_clrBorder;
```

## <a name="cmfctooltipinfom_clrfill"></a><a name="m_clrfill"></a> CMFCToolTipInfo:: m_clrFill

도구 설명 배경의 색을 지정 합니다.

```
COLORREF m_clrFill;
```

### <a name="remarks"></a>설명

[CMFCToolTipInfo:: m_clrFillGradient](#m_clrfillgradient) 가-1 인 경우 도구 설명 배경색은 `m_clrFill` 입니다. 그렇지 않은 경우에는 `m_clrFill` 그라데이션의 시작 색을 지정 하 고 `m_clrFillGradient` 그라데이션 끝 색을 지정 합니다. [CMFCToolTipInfo:: m_nGradientAngle](#m_ngradientangle) 는 그라데이션의 방향을 결정 합니다.

## <a name="cmfctooltipinfom_clrfillgradient"></a><a name="m_clrfillgradient"></a> CMFCToolTipInfo:: m_clrFillGradient

도구 설명에 대 한 그라데이션 배경의 끝 색을 지정 합니다.

```
COLORREF m_clrFillGradient;
```

### <a name="remarks"></a>설명

`m_clrFillGradient`가-1 이면 그라데이션이 없는 것입니다. 그렇지 않으면 그라데이션 초기 색은 [CMFCToolTipInfo:: m_clrFill](#m_clrfill) 에 의해 지정 되 고 그라데이션 끝 색은에 의해 지정 됩니다 `m_clrFillGradient` . [CMFCToolTipInfo:: m_nGradientAngle](#m_ngradientangle) 는 그라데이션의 방향을 결정 합니다.

## <a name="cmfctooltipinfom_clrtext"></a><a name="m_clrtext"></a> CMFCToolTipInfo:: m_clrText

모든 도구 설명의 텍스트 색을 지정 합니다.

```
COLORREF m_clrText;
```

## <a name="cmfctooltipinfom_ngradientangle"></a><a name="m_ngradientangle"></a> CMFCToolTipInfo:: m_nGradientAngle

도구 설명의 배경에 그라데이션이 그려지는 각도를 지정 합니다.

```
int m_nGradientAngle;
```

### <a name="remarks"></a>설명

`m_nGradientAngle` 도구 설명 배경의 그라데이션이 가로에서 오프셋 되는 각도 (도)를 지정 합니다. `m_nGradientAngle`가 0 이면 왼쪽에서 오른쪽으로 그라데이션이 그려집니다. `m_nGradientAngle`가 1에서 360 사이인 경우 그라데이션은 각도 만큼 시계 방향으로 회전 합니다. `m_nGradientAngle`가 기본값인-1 이면 위쪽에서 아래쪽으로 그라데이션이 그려집니다. 이는를 90로 설정 하는 것과 같습니다 `m_nGradientAngle` .

[CMFCToolTipInfo:: m_clrFill](#m_clrfill) `clrFill` 그라데이션의 시작 색을 지정 하 고 [CMFCToolTipInfo:: m_clrFillGradient](#m_clrfillgradient) 는 `clrFillGradient` 그라데이션의 끝 색을 지정 합니다. `m_clrFillGradient`가-1 이면 그라데이션이 없는 것입니다.

## <a name="cmfctooltipinfom_nmaxdescrwidth"></a><a name="m_nmaxdescrwidth"></a> CMFCToolTipInfo:: m_nMaxDescrWidth

각 도구 설명에 표시 되는 설명의 최대 너비를 지정 합니다. 설명 너비가 지정 된 값을 초과 하면 텍스트가 래핑됩니다.

```
int m_nMaxDescrWidth;
```

## <a name="cmfctooltipinfom_bvislmanagertheme"></a><a name="m_bvislmanagertheme"></a> CMFCToolTipInfo:: m_bVislManagerTheme

응용 프로그램의 visual 관리자가 모든 도구 설명의 모양을 제어 하는지 여부를 지정 합니다.

```
BOOL m_bVislManagerTheme;
```

### <a name="remarks"></a>설명

`m_bVislManagerTheme`이 TRUE 이면 모든 도구 설명이 화면에 표시 되기 전에 응용 프로그램의 visual manager에서 새 [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) 를 요청 하 고 해당 개체의 값을 사용 하 여 모양을 결정 합니다. [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) 의 다른 멤버는 무시 됩니다.

## <a name="cmfctooltipinfooperator"></a><a name="operator_eq"></a> CMFCToolTipInfo:: operator =

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```

### <a name="parameters"></a>매개 변수

진행 *src*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CTooltipManager 클래스](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipCtrl 클래스](../../mfc/reference/cmfctooltipctrl-class.md)
