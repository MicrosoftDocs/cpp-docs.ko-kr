---
description: '자세히 알아보기: CSinusoidalTransitionFromRange 클래스'
title: CSinusoidalTransitionFromRange 클래스
ms.date: 11/04/2016
f1_keywords:
- CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMaximumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMinimumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_period
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_slope
helpviewer_keywords:
- CSinusoidalTransitionFromRange [MFC], CSinusoidalTransitionFromRange
- CSinusoidalTransitionFromRange [MFC], Create
- CSinusoidalTransitionFromRange [MFC], m_dblMaximumValue
- CSinusoidalTransitionFromRange [MFC], m_dblMinimumValue
- CSinusoidalTransitionFromRange [MFC], m_duration
- CSinusoidalTransitionFromRange [MFC], m_period
- CSinusoidalTransitionFromRange [MFC], m_slope
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
ms.openlocfilehash: 5d00b1cbfb8fe9b76a5a69bd1c9f10316ddf8141
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264572"
---
# <a name="csinusoidaltransitionfromrange-class"></a>CSinusoidalTransitionFromRange 클래스

진동 범위가 지정된 사인 곡선 범위 전환을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CSinusoidalTransitionFromRange : public CBaseTransition;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSinusoidalTransitionFromRange:: CSinusoidalTransitionFromRange](#csinusoidaltransitionfromrange)|전환 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSinusoidalTransitionFromRange:: Create](#create)|는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다. [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)를 재정의 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CSinusoidalTransitionFromRange:: m_dblMaximumValue](#m_dblmaximumvalue)|사인 곡선 wave의 피크에 있는 애니메이션 변수의 값입니다.|
|[CSinusoidalTransitionFromRange:: m_dblMinimumValue](#m_dblminimumvalue)|사인 곡선 wave의 trough에 있는 애니메이션 변수의 값입니다.|
|[CSinusoidalTransitionFromRange:: m_duration](#m_duration)|전환 기간입니다.|
|[CSinusoidalTransitionFromRange:: m_period](#m_period)|사인 곡선 wave의 진동 범위가 기간 (초)입니다.|
|[CSinusoidalTransitionFromRange:: m_slope](#m_slope)|전환 시작의 기울기입니다.|

## <a name="remarks"></a>설명

애니메이션 변수 값은 사인 곡선 범위 전환의 전체 기간 동안 지정 된 최소값과 최대값 사이에서 변동 합니다. 슬로프 매개 변수는 다른 매개 변수로 지정 된 두 개의 가능한 사인 물결 사이를 구분 하는 데 사용 됩니다. 모든 전환은 자동으로 지워지므로 operator new를 사용 하 여 할당 하는 것이 좋습니다. 캡슐화 된 IuiAnimateGroup 전환 COM 개체는 NULL 일 때까지 CAnimationController::에 의해 생성 됩니다. 이 COM 개체를 만든 후 멤버 변수를 변경 해도 아무런 영향을 주지 않습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSinusoidalTransitionFromRange](../../mfc/reference/csinusoidaltransitionfromrange-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="csinusoidaltransitionfromrangecreate"></a><a name="create"></a> CSinusoidalTransitionFromRange:: Create

는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>매개 변수

*pLibrary*<br/>
표준 전환의 생성을 담당 하는 전환 라이브러리에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

전환이 성공적으로 생성 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="csinusoidaltransitionfromrangecsinusoidaltransitionfromrange"></a><a name="csinusoidaltransitionfromrange"></a> CSinusoidalTransitionFromRange:: CSinusoidalTransitionFromRange

전환 개체를 생성 합니다.

```
CSinusoidalTransitionFromRange(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblMinimumValue,
    DOUBLE dblMaximumValue,
    UI_ANIMATION_SECONDS period,
    UI_ANIMATION_SLOPE slope);
```

### <a name="parameters"></a>매개 변수

*duration*<br/>
전환 기간입니다.

*dblMinimumValue*<br/>
사인 곡선 wave의 trough에 있는 애니메이션 변수의 값입니다.

*dblMaximumValue*<br/>
사인 곡선 wave의 피크에 있는 애니메이션 변수의 값입니다.

*간격이*<br/>
사인 곡선 wave의 진동 범위가 기간 (초)입니다.

*slope*<br/>
전환 시작의 기울기입니다.

## <a name="csinusoidaltransitionfromrangem_dblmaximumvalue"></a><a name="m_dblmaximumvalue"></a> CSinusoidalTransitionFromRange:: m_dblMaximumValue

사인 곡선 wave의 피크에 있는 애니메이션 변수의 값입니다.

```
DOUBLE m_dblMaximumValue;
```

## <a name="csinusoidaltransitionfromrangem_dblminimumvalue"></a><a name="m_dblminimumvalue"></a> CSinusoidalTransitionFromRange:: m_dblMinimumValue

사인 곡선 wave의 trough에 있는 애니메이션 변수의 값입니다.

```
DOUBLE m_dblMinimumValue;
```

## <a name="csinusoidaltransitionfromrangem_duration"></a><a name="m_duration"></a> CSinusoidalTransitionFromRange:: m_duration

전환 기간입니다.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="csinusoidaltransitionfromrangem_period"></a><a name="m_period"></a> CSinusoidalTransitionFromRange:: m_period

사인 곡선 wave의 진동 범위가 기간 (초)입니다.

```
UI_ANIMATION_SECONDS m_period;
```

## <a name="csinusoidaltransitionfromrangem_slope"></a><a name="m_slope"></a> CSinusoidalTransitionFromRange:: m_slope

전환 시작의 기울기입니다.

```
UI_ANIMATION_SLOPE m_slope;
```

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
