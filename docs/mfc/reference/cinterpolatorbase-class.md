---
title: CInterpolatorBase 클래스
ms.date: 11/04/2016
f1_keywords:
- CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CreateInstance
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDependencies
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetFinalValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetCustomInterpolator
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetInitialValueAndVelocity
helpviewer_keywords:
- CInterpolatorBase [MFC], CInterpolatorBase
- CInterpolatorBase [MFC], CreateInstance
- CInterpolatorBase [MFC], GetDependencies
- CInterpolatorBase [MFC], GetDuration
- CInterpolatorBase [MFC], GetFinalValue
- CInterpolatorBase [MFC], InterpolateValue
- CInterpolatorBase [MFC], InterpolateVelocity
- CInterpolatorBase [MFC], SetCustomInterpolator
- CInterpolatorBase [MFC], SetDuration
- CInterpolatorBase [MFC], SetInitialValueAndVelocity
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
ms.openlocfilehash: d1fc675b1014ab9a099e8310b52b7458f2bff65f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916208"
---
# <a name="cinterpolatorbase-class"></a>CInterpolatorBase 클래스

애니메이션 API에서 애니메이션 변수의 새 값을 계산해야 할 때 호출하는 콜백을 구현합니다.

## <a name="syntax"></a>구문

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|Description|
|----------|-----------------|
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|개체를 `CInterpolatorBase` 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|Description|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|의 `CInterpolatorBase` 인스턴스를 만들고 이벤트를 처리 하는 사용자 지정 보간 기에 대 한 포인터를 저장 합니다.|
|[CInterpolatorBase::GetDependencies](#getdependencies)|보간 기의 종속성을 가져옵니다. ( `CUIAnimationInterpolatorBase::GetDependencies`을 재정의합니다.)|
|[CInterpolatorBase::GetDuration](#getduration)|보간 기 시간을 가져옵니다. ( `CUIAnimationInterpolatorBase::GetDuration`을 재정의합니다.)|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|보간 기에 사용할 최종 값을 가져옵니다. ( `CUIAnimationInterpolatorBase::GetFinalValue`을 재정의합니다.)|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|지정 된 오프셋 (재정의 `CUIAnimationInterpolatorBase::InterpolateValue`)에서 값을 보간합니다.|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|지정 된 오프셋 (재정의 `CUIAnimationInterpolatorBase::InterpolateVelocity`)의 속도를 보간합니다.|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|이벤트를 처리 하는 사용자 지정 보간 기에 대 한 포인터를 저장 합니다.|
|[CInterpolatorBase::SetDuration](#setduration)|보간 기 (재정의 `CUIAnimationInterpolatorBase::SetDuration`)의 기간을 설정 합니다.|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|보간 기 초기 값과 속도를 설정 합니다. ( `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`을 재정의합니다.)|

## <a name="remarks"></a>설명

이 처리기는에서 `IUIAnimationTransitionFactory::CreateTransition` `CAnimationController::AnimateGroup`시작 되는 애니메이션 초기화 `CCustomTransition` 프로세스의 일부로 개체가 만들어지는 경우에 생성 되어에 전달 됩니다. 일반적으로이 클래스를 직접 사용할 필요는 없으며, 해당 포인터가의 `CCustomInterpolator` `CCustomTransition`생성자에 전달 되는 파생 클래스에 모든 이벤트를 routs 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

##  <a name="cinterpolatorbase"></a>  CInterpolatorBase::CInterpolatorBase

CInterpolatorBase 개체를 생성 합니다.

```
CInterpolatorBase();
```

##  <a name="createinstance"></a>  CInterpolatorBase::CreateInstance

CInterpolatorBase의 인스턴스를 만들고 이벤트를 처리 하는 사용자 지정 보간 기에 대 한 포인터를 저장 합니다.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>매개 변수

*pInterpolator*<br/>
사용자 지정 보간 기에 대 한 포인터입니다.

*ppHandler*<br/>
출력. 함수가 반환 될 때 CInterpolatorBase의 인스턴스에 대 한 포인터를 포함 합니다.

### <a name="return-value"></a>반환 값

##  <a name="getdependencies"></a>  CInterpolatorBase::GetDependencies

보간 기의 종속성을 가져옵니다.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>매개 변수

*initialValueDependencies*<br/>
출력. SetInitialValueAndVelocity 전달 되는 초기 값에 따라 달라 지는 보간 기능입니다.

*initialVelocityDependencies*<br/>
출력. SetInitialValueAndVelocity 전달 되는 초기 속도에 따라 달라 지는 보간 기능입니다.

*durationDependencies*<br/>
출력. SetDuration에 전달 되는 기간에 따라 달라 지는 보간의 측면입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 S_OK를 반환 합니다. CCustomInterpolator이 설정 되지 않은 경우 E_FAIL을 반환 하 고, 사용자 지정 구현은 GetDependencies 메서드에서 FALSE를 반환 합니다.

##  <a name="getduration"></a>  CInterpolatorBase::GetDuration

보간 기 시간을 가져옵니다.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>매개 변수

*duration*<br/>
출력. 전환 기간 (초)입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 S_OK를 반환 합니다. CCustomInterpolator이 설정 되지 않은 경우 E_FAIL을 반환 하 고, 사용자 지정 구현은 GetDuration 메서드에서 FALSE를 반환 합니다.

##  <a name="getfinalvalue"></a>  CInterpolatorBase::GetFinalValue

보간 기에 사용할 최종 값을 가져옵니다.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>매개 변수

*value*<br/>
출력. 전환이 끝날 때 변수의 최종 값입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 S_OK를 반환 합니다. CCustomInterpolator이 설정 되지 않은 경우 E_FAIL을 반환 하 고, 사용자 지정 구현은 GetFinalValue 메서드에서 FALSE를 반환 합니다.

##  <a name="interpolatevalue"></a>  CInterpolatorBase::InterpolateValue

지정 된 오프셋에서 값을 보간합니다.

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>매개 변수

*offset*<br/>
전환 시작 부분에서의 오프셋입니다. 오프셋은 항상 0 보다 크거나 같고 전환 기간 보다 작아야 합니다. 전환 기간이 0 인 경우이 메서드는 호출 되지 않습니다.

*value*<br/>
출력. 보간된 값입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 S_OK를 반환 합니다. CCustomInterpolator이 설정 되지 않은 경우 E_FAIL을 반환 하 고, 사용자 지정 구현은 InterpolateValue 메서드에서 FALSE를 반환 합니다.

##  <a name="interpolatevelocity"></a>  CInterpolatorBase::InterpolateVelocity

지정 된 오프셋의 속도를 보간합니다.

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>매개 변수

*offset*<br/>
전환 시작 부분에서의 오프셋입니다. 오프셋은 항상 0 보다 크거나 같고 전환 기간 보다 작거나 같습니다. 전환 기간이 0 인 경우이 메서드는 호출 되지 않습니다.

*velocity*<br/>
출력. 오프셋에 있는 변수의 속도입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 S_OK를 반환 합니다. CCustomInterpolator이 설정 되지 않은 경우 E_FAIL을 반환 하 고, 사용자 지정 구현은 InterpolateVelocity 메서드에서 FALSE를 반환 합니다.

##  <a name="setcustominterpolator"></a>  CInterpolatorBase::SetCustomInterpolator

이벤트를 처리 하는 사용자 지정 보간 기에 대 한 포인터를 저장 합니다.

```
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>매개 변수

*pInterpolator*<br/>
사용자 지정 보간 기에 대 한 포인터입니다.

##  <a name="setduration"></a>  CInterpolatorBase::SetDuration

보간 기 기간을 설정 합니다.

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>매개 변수

*duration*<br/>
전환 기간입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 S_OK를 반환 합니다. CCustomInterpolator이 설정 되지 않은 경우 E_FAIL을 반환 하 고, 사용자 지정 구현은 SetDuration 메서드에서 FALSE를 반환 합니다.

##  <a name="setinitialvalueandvelocity"></a>  CInterpolatorBase::SetInitialValueAndVelocity

보간 기 초기 값과 속도를 설정 합니다.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>매개 변수

*initialValue*<br/>
전환 시작 시의 변수 값입니다.

*initialVelocity*<br/>
전환 시작 시의 변수 속도입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 S_OK를 반환 합니다. CCustomInterpolator이 설정 되지 않은 경우 E_FAIL을 반환 하 고, SetInitialValueAndVelocity 메서드에서 FALSE를 반환 하는 사용자 지정 구현입니다.

## <a name="see-also"></a>참고자료

[클래스](../../mfc/reference/mfc-classes.md)
