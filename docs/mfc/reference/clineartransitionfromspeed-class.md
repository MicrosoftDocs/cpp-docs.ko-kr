---
description: '자세히 알아보기: CLinearTransitionFromSpeed 클래스'
title: CLinearTransitionFromSpeed 클래스
ms.date: 11/04/2016
f1_keywords:
- CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::Create
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblSpeed
helpviewer_keywords:
- CLinearTransitionFromSpeed [MFC], CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed [MFC], Create
- CLinearTransitionFromSpeed [MFC], m_dblFinalValue
- CLinearTransitionFromSpeed [MFC], m_dblSpeed
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
ms.openlocfilehash: ce919787508f4f6326f9d07c0c6003a63633b279
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236739"
---
# <a name="clineartransitionfromspeed-class"></a>CLinearTransitionFromSpeed 클래스

선형 속도 전환을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CLinearTransitionFromSpeed : public CBaseTransition;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CLinearTransitionFromSpeed:: CLinearTransitionFromSpeed](#clineartransitionfromspeed)|선형 속도 전환 개체를 생성 하 고 속도 및 최종 값을 사용 하 여 초기화 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CLinearTransitionFromSpeed:: Create](#create)|는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다. [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)를 재정의 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CLinearTransitionFromSpeed:: m_dblFinalValue](#m_dblfinalvalue)|전환의 끝에 있는 애니메이션 변수의 값입니다.|
|[CLinearTransitionFromSpeed:: m_dblSpeed](#m_dblspeed)|변수 속도의 절대값입니다.|

## <a name="remarks"></a>설명

선형 속도 전환 중 애니메이션 변수의 값은 지정 된 속도에서 변경 됩니다. 전환 기간은 초기 값과 지정 된 최종 값의 차이에 따라 결정 됩니다. 모든 전환은 자동으로 지워지므로 operator new를 사용 하 여 할당 하는 것이 좋습니다. 캡슐화 된 IuiAnimateGroup 전환 COM 개체는 NULL 일 때까지 CAnimationController::에 의해 생성 됩니다. 이 COM 개체를 만든 후 멤버 변수를 변경 해도 아무런 영향을 주지 않습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="clineartransitionfromspeedclineartransitionfromspeed"></a><a name="clineartransitionfromspeed"></a> CLinearTransitionFromSpeed:: CLinearTransitionFromSpeed

선형 속도 전환 개체를 생성 하 고 속도 및 최종 값을 사용 하 여 초기화 합니다.

```
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>매개 변수

*dblSpeed*<br/>
변수 속도의 절대값입니다.

*dblFinalValue*<br/>
전환의 끝에 있는 애니메이션 변수의 값입니다.

## <a name="clineartransitionfromspeedcreate"></a><a name="create"></a> CLinearTransitionFromSpeed:: Create

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

## <a name="clineartransitionfromspeedm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a> CLinearTransitionFromSpeed:: m_dblFinalValue

전환의 끝에 있는 애니메이션 변수의 값입니다.

```
DOUBLE m_dblFinalValue;
```

## <a name="clineartransitionfromspeedm_dblspeed"></a><a name="m_dblspeed"></a> CLinearTransitionFromSpeed:: m_dblSpeed

변수 속도의 절대값입니다.

```
DOUBLE m_dblSpeed;
```

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
