---
description: '자세히 알아보기: CDiscreteTransition 클래스'
title: CDiscreteTransition 클래스
ms.date: 11/04/2016
f1_keywords:
- CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::Create
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_delay
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_hold
helpviewer_keywords:
- CDiscreteTransition [MFC], CDiscreteTransition
- CDiscreteTransition [MFC], Create
- CDiscreteTransition [MFC], m_dblFinalValue
- CDiscreteTransition [MFC], m_delay
- CDiscreteTransition [MFC], m_hold
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
ms.openlocfilehash: 5ab2e2aa8a56236ac0354be088bc72afe5042a76
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185182"
---
# <a name="cdiscretetransition-class"></a>CDiscreteTransition 클래스

불연속 전환을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CDiscreteTransition : public CBaseTransition;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDiscreteTransition:: CDiscreteTransition](#cdiscretetransition)|불연속 전환 개체를 생성 하 고 해당 매개 변수를 초기화 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDiscreteTransition:: Create](#create)|는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다. [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)를 재정의 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDiscreteTransition:: m_dblFinalValue](#m_dblfinalvalue)|전환의 끝에 있는 애니메이션 변수의 값입니다.|
|[CDiscreteTransition:: m_delay](#m_delay)|즉시 전환을 최종 값으로 지연 하는 시간입니다.|
|[CDiscreteTransition:: m_hold](#m_hold)|최종 값에서 변수를 보유 하는 데 소요 되는 시간입니다.|

## <a name="remarks"></a>설명

불연속 전환을 수행 하는 동안 애니메이션 변수는 지정 된 지연 시간에 대 한 초기 값을 유지 하 고, 즉시 지정 된 최종 값으로 전환 되 고 지정 된 보류 시간에 대해 해당 값을 유지 합니다. 모든 전환은 자동으로 지워지므로 operator new를 사용 하 여 할당 하는 것이 좋습니다. 캡슐화 된 IuiAnimateGroup 전환 COM 개체는 NULL 일 때까지 CAnimationController::에 의해 생성 됩니다. 이 COM 개체를 만든 후 멤버 변수를 변경 해도 아무런 영향을 주지 않습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="cdiscretetransitioncdiscretetransition"></a><a name="cdiscretetransition"></a> CDiscreteTransition:: CDiscreteTransition

불연속 전환 개체를 생성 하 고 해당 매개 변수를 초기화 합니다.

```
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,
    DOUBLE dblFinalValue,
    UI_ANIMATION_SECONDS hold);
```

### <a name="parameters"></a>매개 변수

*연기할*<br/>
즉시 전환을 최종 값으로 지연 하는 시간입니다.

*dblFinalValue*<br/>
전환의 끝에 있는 애니메이션 변수의 값입니다.

*놓고*<br/>
최종 값에서 변수를 보유 하는 데 소요 되는 시간입니다.

## <a name="cdiscretetransitioncreate"></a><a name="create"></a> CDiscreteTransition:: Create

는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

*pLibrary*<br/>
표준 전환 라이브러리를 정의 하는 [IUIAnimationTransitionLibrary 인터페이스](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

전환이 성공적으로 생성 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cdiscretetransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a> CDiscreteTransition:: m_dblFinalValue

전환의 끝에 있는 애니메이션 변수의 값입니다.

```
DOUBLE m_dblFinalValue;
```

## <a name="cdiscretetransitionm_delay"></a><a name="m_delay"></a> CDiscreteTransition:: m_delay

즉시 전환을 최종 값으로 지연 하는 시간입니다.

```
UI_ANIMATION_SECONDS m_delay;
```

## <a name="cdiscretetransitionm_hold"></a><a name="m_hold"></a> CDiscreteTransition:: m_hold

최종 값에서 변수를 보유 하는 데 소요 되는 시간입니다.

```
UI_ANIMATION_SECONDS m_hold;
```

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
