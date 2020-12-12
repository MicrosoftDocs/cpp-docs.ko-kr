---
description: '자세히 알아보기: CLinearTransition 클래스'
title: CLinearTransition 클래스
ms.date: 11/04/2016
f1_keywords:
- CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::Create
- AFXANIMATIONCONTROLLER/CLinearTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransition::m_duration
helpviewer_keywords:
- CLinearTransition [MFC], CLinearTransition
- CLinearTransition [MFC], Create
- CLinearTransition [MFC], m_dblFinalValue
- CLinearTransition [MFC], m_duration
ms.assetid: 7fcb2dba-beb8-4933-9f5d-3b7fb1585ef0
ms.openlocfilehash: bff8d580bb07de14583f02c592fceaefa5c3523a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236778"
---
# <a name="clineartransition-class"></a>CLinearTransition 클래스

선형 전환을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CLinearTransition : public CBaseTransition;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CLinearTransition:: CLinearTransition](#clineartransition)|선형 전환 개체를 생성 하 고 duration 및 final 값을 사용 하 여 초기화 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CLinearTransition:: Create](#create)|는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다. [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)를 재정의 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CLinearTransition:: m_dblFinalValue](#m_dblfinalvalue)|전환의 끝에 있는 애니메이션 변수의 값입니다.|
|[CLinearTransition:: m_duration](#m_duration)|전환 기간입니다.|

## <a name="remarks"></a>설명

선형 전환 중 애니메이션 변수의 값은 초기 값에서 지정 된 최종 값으로 선형으로 전환 됩니다. 모든 전환은 자동으로 지워지므로 operator new를 사용 하 여 할당 하는 것이 좋습니다. 캡슐화 된 IuiAnimateGroup 전환 COM 개체는 NULL 일 때까지 CAnimationController::에 의해 생성 됩니다. 이 COM 개체를 만든 후 멤버 변수를 변경 해도 아무런 영향을 주지 않습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransition](../../mfc/reference/clineartransition-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="clineartransitionclineartransition"></a><a name="clineartransition"></a> CLinearTransition:: CLinearTransition

선형 전환 개체를 생성 하 고 duration 및 final 값을 사용 하 여 초기화 합니다.

```
CLinearTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>매개 변수

*duration*<br/>
전환 기간입니다.

*dblFinalValue*<br/>
전환의 끝에 있는 애니메이션 변수의 값입니다.

## <a name="clineartransitioncreate"></a><a name="create"></a> CLinearTransition:: Create

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

## <a name="clineartransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a> CLinearTransition:: m_dblFinalValue

전환의 끝에 있는 애니메이션 변수의 값입니다.

```
DOUBLE m_dblFinalValue;
```

## <a name="clineartransitionm_duration"></a><a name="m_duration"></a> CLinearTransition:: m_duration

전환 기간입니다.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
