---
description: '자세히 알아보기: CInstantaneousTransition 클래스'
title: CInstantaneousTransition 클래스
ms.date: 11/04/2016
f1_keywords:
- CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::Create
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::m_dblFinalValue
helpviewer_keywords:
- CInstantaneousTransition [MFC], CInstantaneousTransition
- CInstantaneousTransition [MFC], Create
- CInstantaneousTransition [MFC], m_dblFinalValue
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
ms.openlocfilehash: 1152d7ed6317b5f1d0c30929cc908266594deb1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143574"
---
# <a name="cinstantaneoustransition-class"></a>CInstantaneousTransition 클래스

순간 전환을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CInstantaneousTransition : public CBaseTransition;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CInstantaneousTransition::CInstantaneousTransition](#cinstantaneoustransition)|전환 개체를 생성 하 고 최종 값을 초기화 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CInstantaneousTransition:: Create](#create)|는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다. [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)를 재정의 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CInstantaneousTransition:: m_dblFinalValue](#m_dblfinalvalue)|전환의 끝에 있는 애니메이션 변수의 값입니다.|

## <a name="remarks"></a>설명

즉시 전환 하는 동안 애니메이션 변수의 값은 현재 값에서 지정 된 최종 값으로 즉시 변경 됩니다. 이 전환 기간은 항상 0입니다. 모든 전환은 자동으로 지워지므로 operator new를 사용 하 여 할당 하는 것이 좋습니다. 캡슐화 된 IuiAnimateGroup 전환 COM 개체는 NULL 일 때까지 CAnimationController::에 의해 생성 됩니다. 이 COM 개체를 만든 후 멤버 변수를 변경 해도 아무런 영향을 주지 않습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CInstantaneousTransition](../../mfc/reference/cinstantaneoustransition-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="cinstantaneoustransitioncinstantaneoustransition"></a><a name="cinstantaneoustransition"></a> CInstantaneousTransition::CInstantaneousTransition

전환 개체를 생성 하 고 최종 값을 초기화 합니다.

```
CInstantaneousTransition(DOUBLE dblFinalValue);
```

### <a name="parameters"></a>매개 변수

*dblFinalValue*<br/>
전환의 끝에 있는 애니메이션 변수의 값입니다.

## <a name="cinstantaneoustransitioncreate"></a><a name="create"></a> CInstantaneousTransition:: Create

는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>매개 변수

*pLibrary*<br/>
표준 전환 라이브러리를 정의 하는 [IUIAnimationTransitionLibrary 인터페이스](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

전환이 성공적으로 생성 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="cinstantaneoustransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a> CInstantaneousTransition:: m_dblFinalValue

전환의 끝에 있는 애니메이션 변수의 값입니다.

```
DOUBLE m_dblFinalValue;
```

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
