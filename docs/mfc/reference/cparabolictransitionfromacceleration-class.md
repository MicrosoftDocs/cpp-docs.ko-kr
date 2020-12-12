---
description: '자세히 알아보기: CParabolicTransitionFromAcceleration 클래스'
title: CParabolicTransitionFromAcceleration 클래스
ms.date: 11/04/2016
f1_keywords:
- CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::Create
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalVelocity
helpviewer_keywords:
- CParabolicTransitionFromAcceleration [MFC], CParabolicTransitionFromAcceleration
- CParabolicTransitionFromAcceleration [MFC], Create
- CParabolicTransitionFromAcceleration [MFC], m_dblAcceleration
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalValue
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalVelocity
ms.assetid: 1e59b86f-358b-4da0-a4fd-8eaf5e85e00f
ms.openlocfilehash: 037c2ff8391b655c556339547966b14ee094fee0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301492"
---
# <a name="cparabolictransitionfromacceleration-class"></a>CParabolicTransitionFromAcceleration 클래스

포물선 가속 전환을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CParabolicTransitionFromAcceleration : public CBaseTransition;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration:: CParabolicTransitionFromAcceleration](#cparabolictransitionfromacceleration)|포물선 가속 전환을 생성 하 고 지정 된 매개 변수를 사용 하 여 초기화 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration:: Create](#create)|는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다. [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)를 재정의 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration:: m_dblAcceleration](#m_dblacceleration)|전환 하는 동안 애니메이션 변수의 가속입니다.|
|[CParabolicTransitionFromAcceleration:: m_dblFinalValue](#m_dblfinalvalue)|전환의 끝에 있는 애니메이션 변수의 값입니다.|
|[CParabolicTransitionFromAcceleration:: m_dblFinalVelocity](#m_dblfinalvelocity)|전환이 끝날 때 애니메이션 변수의 속도입니다.|

## <a name="remarks"></a>설명

포물선 가속을 전환 하는 동안 애니메이션 변수의 값은 초기 값에서 지정 된 속도에서 끝나는 최종 값으로 변경 됩니다. 가속 속도를 지정 하 여 변수가 최종 값에 도달 하는 속도를 제어할 수 있습니다. 모든 전환은 자동으로 지워지므로 operator new를 사용 하 여 할당 하는 것이 좋습니다. 캡슐화 된 IuiAnimateGroup 전환 COM 개체는 NULL 일 때까지 CAnimationController::에 의해 생성 됩니다. 이 COM 개체를 만든 후 멤버 변수를 변경 해도 아무런 영향을 주지 않습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CParabolicTransitionFromAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="cparabolictransitionfromaccelerationcparabolictransitionfromacceleration"></a><a name="cparabolictransitionfromacceleration"></a> CParabolicTransitionFromAcceleration:: CParabolicTransitionFromAcceleration

포물선 가속 전환을 생성 하 고 지정 된 매개 변수를 사용 하 여 초기화 합니다.

```
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,
    DOUBLE dblFinalVelocity,
    DOUBLE dblAcceleration);
```

### <a name="parameters"></a>매개 변수

*dblFinalValue*<br/>
전환의 끝에 있는 애니메이션 변수의 값입니다.

*dblFinalVelocity*<br/>
전환이 끝날 때 애니메이션 변수의 속도입니다.

*dblAcceleration*<br/>
전환 하는 동안 애니메이션 변수의 가속입니다.

## <a name="cparabolictransitionfromaccelerationcreate"></a><a name="create"></a> CParabolicTransitionFromAcceleration:: Create

는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* /* not used */);
```

### <a name="parameters"></a>매개 변수

*pLibrary*<br/>
표준 전환의 생성을 담당 하는 전환 라이브러리에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

전환이 성공적으로 생성 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cparabolictransitionfromaccelerationm_dblacceleration"></a><a name="m_dblacceleration"></a> CParabolicTransitionFromAcceleration:: m_dblAcceleration

전환 하는 동안 애니메이션 변수의 가속입니다.

```
DOUBLE m_dblAcceleration;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a> CParabolicTransitionFromAcceleration:: m_dblFinalValue

전환의 끝에 있는 애니메이션 변수의 값입니다.

```
DOUBLE m_dblFinalValue;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvelocity"></a><a name="m_dblfinalvelocity"></a> CParabolicTransitionFromAcceleration:: m_dblFinalVelocity

전환이 끝날 때 애니메이션 변수의 속도입니다.

```
DOUBLE m_dblFinalVelocity;
```

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
