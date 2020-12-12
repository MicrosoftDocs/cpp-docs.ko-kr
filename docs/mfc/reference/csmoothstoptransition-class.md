---
description: '자세히 알아보기: CSmoothStopTransition 클래스'
title: CSmoothStopTransition 클래스
ms.date: 11/04/2016
f1_keywords:
- CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::Create
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_maximumDuration
helpviewer_keywords:
- CSmoothStopTransition [MFC], CSmoothStopTransition
- CSmoothStopTransition [MFC], Create
- CSmoothStopTransition [MFC], m_dblFinalValue
- CSmoothStopTransition [MFC], m_maximumDuration
ms.assetid: e1a4b476-6f96-43dd-90db-870a64406b85
ms.openlocfilehash: 14ea7475c886201d6b9b72eefc62f41679e73008
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264533"
---
# <a name="csmoothstoptransition-class"></a>CSmoothStopTransition 클래스

부드러운 중지 전환을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CSmoothStopTransition : public CBaseTransition;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSmoothStopTransition:: CSmoothStopTransition](#csmoothstoptransition)|부드러운 중지 전환을 생성 하 고 최대 기간과 최종 값을 초기화 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSmoothStopTransition:: Create](#create)|는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다. [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)를 재정의 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CSmoothStopTransition:: m_dblFinalValue](#m_dblfinalvalue)|전환의 끝에 있는 애니메이션 변수의 값입니다.|
|[CSmoothStopTransition:: m_maximumDuration](#m_maximumduration)|전환의 최대 지속 시간입니다.|

## <a name="remarks"></a>설명

부드러운 중지 전환은 지정 된 최종 값에 접근 하는 속도가 느려지고 속도가 0 인 경우에도이에 도달 합니다. 전환 기간은 초기 속도, 초기 값과 최종 값의 차이 및 지정 된 최대 기간에 따라 결정 됩니다. 단일 포물선 호로 구성 된 솔루션이 없는 경우이 메서드는 입방 전환을 만듭니다. 모든 전환은 자동으로 지워지므로 operator new를 사용 하 여 할당 하는 것이 좋습니다. 캡슐화 된 IuiAnimateGroup 전환 COM 개체는 NULL 일 때까지 CAnimationController::에 의해 생성 됩니다. 이 COM 개체를 만든 후 멤버 변수를 변경 해도 아무런 영향을 주지 않습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSmoothStopTransition](../../mfc/reference/csmoothstoptransition-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="csmoothstoptransitioncreate"></a><a name="create"></a> CSmoothStopTransition:: Create

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

## <a name="csmoothstoptransitioncsmoothstoptransition"></a><a name="csmoothstoptransition"></a> CSmoothStopTransition:: CSmoothStopTransition

부드러운 중지 전환을 생성 하 고 최대 기간과 최종 값을 초기화 합니다.

```
CSmoothStopTransition(
    UI_ANIMATION_SECONDS maximumDuration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>매개 변수

*maximumDuration*<br/>
전환의 최대 지속 시간입니다.

*dblFinalValue*<br/>
전환의 끝에 있는 애니메이션 변수의 값입니다.

## <a name="csmoothstoptransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a> CSmoothStopTransition:: m_dblFinalValue

전환의 끝에 있는 애니메이션 변수의 값입니다.

```
DOUBLE m_dblFinalValue;
```

## <a name="csmoothstoptransitionm_maximumduration"></a><a name="m_maximumduration"></a> CSmoothStopTransition:: m_maximumDuration

전환의 최대 지속 시간입니다.

```
UI_ANIMATION_SECONDS m_maximumDuration;
```

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
