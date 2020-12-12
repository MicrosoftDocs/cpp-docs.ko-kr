---
description: '자세히 알아보기: CAccelerateDecelerateTransition 클래스'
title: CAccelerateDecelerateTransition 클래스
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 5981c6f57acaf2507410acbb6c792f77b96f75c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322761"
---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition 클래스

가속-감속 전환을 구현합니다.

## <a name="syntax"></a>구문

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|전환 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAccelerateDecelerateTransition:: Create](#create)|는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다. [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)를 재정의 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAccelerateDecelerateTransition:: m_accelerationRatio](#m_accelerationratio)|기간을 단축 하는 데 걸린 시간의 비율입니다.|
|[CAccelerateDecelerateTransition:: m_decelerationRatio](#m_decelerationratio)|기간에 감속 하는 데 소요 된 시간의 비율입니다.|
|[CAccelerateDecelerateTransition:: m_duration](#m_duration)|전환 기간입니다.|
|[CAccelerateDecelerateTransition:: m_finalValue](#m_finalvalue)|전환의 끝에 있는 애니메이션 변수의 값입니다.|

## <a name="remarks"></a>설명

가속 감속 전환을 수행 하는 동안 애니메이션 변수는 지정 된 값에서 종료 되 고 전환 기간 동안 속도가 빨라집니다. 서로 다른 가속 및 감속 비율을 지정 하 여 변수를 독립적으로 가속 하 고 감속 하는 속도를 제어할 수 있습니다. 초기 속도가 0 인 경우 가속 비율은 변수에 소요 되는 기간에 대 한 비율입니다. 감속 비율을 사용 하는 경우에도 마찬가지입니다. 초기 속도가 0이 아닌 경우 속도는 0에 도달 하 고 전환의 끝에 도달 하는 시간의 비율입니다. 가속 비율과 감속/가속 비율은 최대 1.0입니다. 모든 전환은 자동으로 지워지므로 operator new를 사용 하 여 할당 하는 것이 좋습니다. 캡슐화 된 IuiAnimateGroup 전환 COM 개체는 NULL 일 때까지 CAnimationController::에 의해 생성 됩니다. 이 COM 개체를 만든 후 멤버 변수를 변경 해도 아무런 영향을 주지 않습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="cacceleratedeceleratetransitioncacceleratedeceleratetransition"></a><a name="cacceleratedeceleratetransition"></a> CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

전환 개체를 생성 합니다.

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>매개 변수

*duration*<br/>
전환 기간입니다.

*가이 값*<br/>
전환의 끝에 있는 애니메이션 변수의 값입니다.

*accelerationRatio*<br/>
기간을 단축 하는 데 걸린 시간의 비율입니다.

*Decelerationratio가*<br/>
기간에 감속 하는 데 소요 된 시간의 비율입니다.

## <a name="cacceleratedeceleratetransitioncreate"></a><a name="create"></a> CAccelerateDecelerateTransition:: Create

는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>매개 변수

*pLibrary*<br/>
표준 전환 라이브러리를 정의 하는 [IUIAnimationTransitionLibrary 인터페이스](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

전환이 성공적으로 생성 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cacceleratedeceleratetransitionm_accelerationratio"></a><a name="m_accelerationratio"></a> CAccelerateDecelerateTransition:: m_accelerationRatio

기간을 단축 하는 데 걸린 시간의 비율입니다.

```
DOUBLE m_accelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_decelerationratio"></a><a name="m_decelerationratio"></a> CAccelerateDecelerateTransition:: m_decelerationRatio

기간에 감속 하는 데 소요 된 시간의 비율입니다.

```
DOUBLE m_decelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_duration"></a><a name="m_duration"></a> CAccelerateDecelerateTransition:: m_duration

전환 기간입니다.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="cacceleratedeceleratetransitionm_finalvalue"></a><a name="m_finalvalue"></a> CAccelerateDecelerateTransition:: m_finalValue

전환의 끝에 있는 애니메이션 변수의 값입니다.

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
