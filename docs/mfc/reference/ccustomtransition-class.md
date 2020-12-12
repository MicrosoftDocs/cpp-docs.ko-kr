---
description: '자세히 알아보기: CCustomTransition 클래스'
title: CCustomTransition 클래스
ms.date: 11/04/2016
f1_keywords:
- CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::Create
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialValueSpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialVelocitySpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_pInterpolator
helpviewer_keywords:
- CCustomTransition [MFC], CCustomTransition
- CCustomTransition [MFC], Create
- CCustomTransition [MFC], SetInitialValue
- CCustomTransition [MFC], SetInitialVelocity
- CCustomTransition [MFC], m_bInitialValueSpecified
- CCustomTransition [MFC], m_bInitialVelocitySpecified
- CCustomTransition [MFC], m_initialValue
- CCustomTransition [MFC], m_initialVelocity
- CCustomTransition [MFC], m_pInterpolator
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
ms.openlocfilehash: 22c08cdcedc3a7cbdbe824ac1d98d62cfe810772
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227665"
---
# <a name="ccustomtransition-class"></a>CCustomTransition 클래스

사용자 지정 전환을 구현합니다.

## <a name="syntax"></a>구문

```
class CCustomTransition : public CBaseTransition;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CCustomTransition:: CCustomTransition](#ccustomtransition)|사용자 지정 전환 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CCustomTransition:: Create](#create)|는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다. [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)를 재정의 합니다.|
|[CCustomTransition:: SetInitialValue](#setinitialvalue)|이 전환과 연결 된 애니메이션 변수에 적용 되는 초기 값을 설정 합니다.|
|[CCustomTransition:: SetInitialVelocity](#setinitialvelocity)|이 전환과 연결 된 애니메이션 변수에 적용 되는 초기 속도를 설정 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CCustomTransition:: m_bInitialValueSpecified](#m_binitialvaluespecified)|초기 값이 SetInitialValue를 사용 하 여 지정 되었는지 여부를 지정 합니다.|
|[CCustomTransition:: m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|초기 속도를 SetInitialVelocity 지정 했는지 여부를 지정 합니다.|
|[CCustomTransition:: m_initialValue](#m_initialvalue)|초기 값을 저장 합니다.|
|[CCustomTransition:: m_initialVelocity](#m_initialvelocity)|초기 속도를 저장 합니다.|
|[CCustomTransition:: m_pInterpolator](#m_pinterpolator)|사용자 지정 보간 기에 대 한 포인터를 저장 합니다.|

## <a name="remarks"></a>설명

CCustomTransitions 클래스를 사용 하면 개발자가 사용자 지정 전환을 구현할 수 있습니다. 이 클래스는 표준 전환으로 생성 되 고 사용 되지만, 해당 생성자는 사용자 지정 보간 기에 대 한 포인터를 매개 변수로 받아들입니다. 사용자 지정 전환을 사용 하려면 다음 단계를 수행 합니다. 1. CCustomInterpolator에서 클래스를 파생 시키고 최소한 InterpolateValue 메서드를 구현 합니다. 2. 사용자 지정 보간 개체의 수명이 사용 되는 애니메이션의 기간 보다 길어야 합니다. 3. CCustomTransition 개체를 인스턴스화하고 (operator new 사용) 생성자의 사용자 지정 보간에 포인터를 전달 합니다. 4. 사용자 지정 보간에 이러한 매개 변수가 필요한 경우 CCustomTransition:: SetInitialValue 및 CCustomTransition:: Setinitialvalue를 호출 합니다. 5. 사용자 지정 알고리즘을 사용 하 여 해당 값에 애니메이션을 적용 해야 하는 애니메이션 개체의 AddTransition 메서드에 사용자 지정 전환에 대 한 포인터를 전달 합니다. 6. 애니메이션 개체의 값이 Windows 애니메이션을 변경 해야 하는 경우 API는 CCustomInterpolator에서 InterpolateValue (및 기타 관련 메서드)를 호출 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="ccustomtransitionccustomtransition"></a><a name="ccustomtransition"></a> CCustomTransition:: CCustomTransition

사용자 지정 전환 개체를 생성 합니다.

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>매개 변수

*pInterpolator*<br/>
사용자 지정 보간 기에 대 한 포인터입니다.

## <a name="ccustomtransitioncreate"></a><a name="create"></a> CCustomTransition:: Create

는 전환 라이브러리를 호출 하 여 캡슐화 된 전환 COM 개체를 만듭니다.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>매개 변수

*pFactory*<br/>
사용자 지정 전환의 생성을 담당 하는 전환 팩터리에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

또한이 메서드는이 전환과 관련 된 애니메이션 변수에 적용 되는 초기 값 및 초기 속도를 설정할 수 있습니다. 이러한 목적을 위해 프레임 워크에서 캡슐화 된 전환 COM 개체 (CAnimationController:: AnimateGroup를 호출할 때 발생)를 만들기 전에 SetInitialValue 및 Setinitialvalue를 호출 해야 합니다.

## <a name="ccustomtransitionm_binitialvaluespecified"></a><a name="m_binitialvaluespecified"></a> CCustomTransition:: m_bInitialValueSpecified

초기 값이 SetInitialValue를 사용 하 여 지정 되었는지 여부를 지정 합니다.

```
BOOL m_bInitialValueSpecified;
```

## <a name="ccustomtransitionm_binitialvelocityspecified"></a><a name="m_binitialvelocityspecified"></a> CCustomTransition:: m_bInitialVelocitySpecified

초기 속도를 SetInitialVelocity 지정 했는지 여부를 지정 합니다.

```
BOOL m_bInitialVelocitySpecified;
```

## <a name="ccustomtransitionm_initialvalue"></a><a name="m_initialvalue"></a> CCustomTransition:: m_initialValue

초기 값을 저장 합니다.

```
DOUBLE m_initialValue;
```

## <a name="ccustomtransitionm_initialvelocity"></a><a name="m_initialvelocity"></a> CCustomTransition:: m_initialVelocity

초기 속도를 저장 합니다.

```
DOUBLE m_initialVelocity;
```

## <a name="ccustomtransitionm_pinterpolator"></a><a name="m_pinterpolator"></a> CCustomTransition:: m_pInterpolator

사용자 지정 보간 기에 대 한 포인터를 저장 합니다.

```
CCustomInterpolator* m_pInterpolator;
```

## <a name="ccustomtransitionsetinitialvalue"></a><a name="setinitialvalue"></a> CCustomTransition:: SetInitialValue

이 전환과 연결 된 애니메이션 변수에 적용 되는 초기 값을 설정 합니다.

```cpp
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>매개 변수

*initialValue*

## <a name="ccustomtransitionsetinitialvelocity"></a><a name="setinitialvelocity"></a> CCustomTransition:: SetInitialVelocity

이 전환과 연결 된 애니메이션 변수에 적용 되는 초기 속도를 설정 합니다.

```cpp
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>매개 변수

*initialVelocity 속도*

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
