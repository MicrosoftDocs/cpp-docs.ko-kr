---
description: CBaseTransition 클래스에 대해 자세히 알아보세요.
title: CBaseTransition 클래스
ms.date: 03/27/2019
f1_keywords:
- CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboardAtKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::Clear
- AFXANIMATIONCONTROLLER/CBaseTransition::Create
- AFXANIMATIONCONTROLLER/CBaseTransition::GetEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::GetStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::GetType
- AFXANIMATIONCONTROLLER/CBaseTransition::IsAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::SetKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::SetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_transition
- AFXANIMATIONCONTROLLER/CBaseTransition::m_type
helpviewer_keywords:
- CBaseTransition [MFC], CBaseTransition
- CBaseTransition [MFC], AddToStoryboard
- CBaseTransition [MFC], AddToStoryboardAtKeyframes
- CBaseTransition [MFC], Clear
- CBaseTransition [MFC], Create
- CBaseTransition [MFC], GetEndKeyframe
- CBaseTransition [MFC], GetRelatedVariable
- CBaseTransition [MFC], GetStartKeyframe
- CBaseTransition [MFC], GetTransition
- CBaseTransition [MFC], GetType
- CBaseTransition [MFC], IsAdded
- CBaseTransition [MFC], SetKeyframes
- CBaseTransition [MFC], SetRelatedVariable
- CBaseTransition [MFC], m_bAdded
- CBaseTransition [MFC], m_pEndKeyframe
- CBaseTransition [MFC], m_pRelatedVariable
- CBaseTransition [MFC], m_pStartKeyframe
- CBaseTransition [MFC], m_transition
- CBaseTransition [MFC], m_type
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
ms.openlocfilehash: 16a7b5e7f88e292fd2b771c627f7169c70fec2c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122826"
---
# <a name="cbasetransition-class"></a>CBaseTransition 클래스

기본 전환을 나타냅니다.

## <a name="syntax"></a>구문

```
class CBaseTransition : public CObject;
```

## <a name="members"></a>멤버

### <a name="public-enumerations"></a>public 열거형

|Name|설명|
|----------|-----------------|
|[CBaseTransition:: TRANSITION_TYPE 열거형](#transition_type_enumeration)|Windows 애니메이션 API의 MFC 구현에서 현재 지원 되는 전환 유형을 정의 합니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CBaseTransition:: CBaseTransition](#cbasetransition)|기본 전환 개체를 생성 합니다.|
|[CBaseTransition:: ~ CBaseTransition](#_dtorcbasetransition)|소멸자입니다. 전환 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CBaseTransition::가 중 Storyboard](#addtostoryboard)|스토리 보드에 전환을 추가 합니다.|
|[CBaseTransition:: AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|스토리 보드에 전환을 추가 합니다.|
|[CBaseTransition:: Clear](#clear)|캡슐화 된 Iui개체 전환 COM 개체를 해제 합니다.|
|[CBaseTransition:: Create](#create)|COM 전환을 만듭니다.|
|[CBaseTransition:: GetEndKeyframe](#getendkeyframe)|시작 키 프레임을 반환 합니다.|
|[CBaseTransition:: GetRelatedVariable](#getrelatedvariable)|관련 변수에 대 한 포인터를 반환 합니다.|
|[CBaseTransition:: GetStartKeyframe](#getstartkeyframe)|시작 키 프레임을 반환 합니다.|
|[CBaseTransition:: GetTransition](#gettransition)|오버로드됨. 내부 COM 전환 개체에 대 한 포인터를 반환 합니다.|
|[CBaseTransition:: GetType](#gettype)|전환 유형을 반환 합니다.|
|[CBaseTransition:: IsAdded 됨](#isadded)|전환이 스토리 보드에 추가 되었는지 여부를 나타냅니다.|
|[CBaseTransition:: SetKeyframes](#setkeyframes)|전환에 대 한 키 프레임을 설정 합니다.|
|[CBaseTransition:: SetRelatedVariable](#setrelatedvariable)|애니메이션 변수와 전환 간의 관계를 설정 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CBaseTransition:: m_bAdded](#m_badded)|전환을 storyboard에 추가할지 여부를 지정 합니다.|
|[CBaseTransition:: m_pEndKeyframe](#m_pendkeyframe)|전환의 끝을 지정 하는 키 프레임에 대 한 포인터를 저장 합니다.|
|[CBaseTransition:: m_pRelatedVariable](#m_prelatedvariable)|M_transition에 저장 된 전환과 함께 애니메이션 되는 애니메이션 변수에 대 한 포인터입니다.|
|[CBaseTransition:: m_pStartKeyframe](#m_pstartkeyframe)|전환의 시작을 지정 하는 키 프레임에 대 한 포인터를 저장 합니다.|
|[CBaseTransition:: m_transition](#m_transition)|Iui애니메이션 전환에 대 한 포인터를 저장 합니다. COM 전환 개체가 생성 되지 않은 경우 NULL입니다.|
|[CBaseTransition:: m_type](#m_type)|전환 유형을 저장 합니다.|

## <a name="remarks"></a>설명

이 클래스는 Iui인터페이스 전환 인터페이스를 캡슐화 하 고 모든 전환에 대 한 기본 클래스로 사용 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="cbasetransitioncbasetransition"></a><a name="_dtorcbasetransition"></a> CBaseTransition:: ~ CBaseTransition

소멸자입니다. 전환 개체가 제거 될 때 호출 됩니다.

```
virtual ~CBaseTransition();
```

## <a name="cbasetransitionaddtostoryboard"></a><a name="addtostoryboard"></a> CBaseTransition::가 중 Storyboard

스토리 보드에 전환을 추가 합니다.

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>매개 변수

*pStoryboard*<br/>
관련 변수에 애니메이션 효과를 주는 storyboard에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

전환을 storyboard에 성공적으로 추가한 경우 TRUE입니다.

### <a name="remarks"></a>설명

스토리 보드의 관련 변수에 전환을 적용 합니다. 이 스토리 보드에서이 변수에 적용 되는 첫 번째 전환 인 경우 전환은 storyboard의 시작 부분에서 시작 됩니다. 그렇지 않으면 최근 변수에 추가 된 전환에 전환이 추가 됩니다.

## <a name="cbasetransitionaddtostoryboardatkeyframes"></a><a name="addtostoryboardatkeyframes"></a> CBaseTransition:: AddToStoryboardAtKeyframes

스토리 보드에 전환을 추가 합니다.

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>매개 변수

*pStoryboard*<br/>
관련 변수에 애니메이션 효과를 주는 storyboard에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

전환을 storyboard에 성공적으로 추가한 경우 TRUE입니다.

### <a name="remarks"></a>설명

스토리 보드의 관련 변수에 전환을 적용 합니다. 시작 키프레임이 지정 된 경우 전환은 해당 키 프레임에서 시작 됩니다. End 키프레임이 지정 된 경우 전환은 시작 키 프레임에서 시작 하 고 종료 키 프레임에서 중지 됩니다. Duration 매개 변수를 지정 하 여 전환을 만든 경우 시작 및 종료 키 프레임 사이의 시간 동안 해당 기간을 덮어씁니다. 키 프레임을 지정 하지 않으면 가장 최근에 변수에 추가 된 전환에 전환이 추가 됩니다.

## <a name="cbasetransitioncbasetransition"></a><a name="cbasetransition"></a> CBaseTransition:: CBaseTransition

기본 전환 개체를 생성 합니다.

```
CBaseTransition();
```

## <a name="cbasetransitionclear"></a><a name="clear"></a> CBaseTransition:: Clear

캡슐화 된 Iui개체 전환 COM 개체를 해제 합니다.

```cpp
void Clear();
```

### <a name="remarks"></a>설명

IUITransition 인터페이스 누수가 발생 하지 않도록 하려면 파생 클래스의 Create 메서드에서이 메서드를 호출 해야 합니다.

## <a name="cbasetransitioncreate"></a><a name="create"></a> CBaseTransition:: Create

COM 전환을 만듭니다.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>매개 변수

*pLibrary*<br/>
표준 전환을 만드는 전환 라이브러리에 대 한 포인터입니다. 사용자 지정 전환의 경우 NULL 일 수 있습니다.

*pFactory*<br/>
사용자 지정 전환을 만드는 전환 팩터리에 대 한 포인터입니다. 표준 전환의 경우 NULL 일 수 있습니다.

### <a name="return-value"></a>반환 값

전환 COM 개체가 성공적으로 생성 되었으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

파생 클래스에서 재정의 되어야 하는 순수 가상 함수입니다. 기본 COM 전환 개체를 인스턴스화하기 위해 프레임 워크에서 호출 됩니다.

## <a name="cbasetransitiongetendkeyframe"></a><a name="getendkeyframe"></a> CBaseTransition:: GetEndKeyframe

시작 키 프레임을 반환 합니다.

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>반환 값

키 프레임에 대 한 유효한 포인터 이거나, 키 프레임 사이에 전환을 삽입 하지 않아야 하는 경우 NULL입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 이전에 SetKeyframes에 의해 설정 된 keyframe 개체에 액세스할 수 있습니다. 전환이 스토리 보드에 추가 될 때 최상위 코드에 의해 호출 됩니다.

## <a name="cbasetransitiongetrelatedvariable"></a><a name="getrelatedvariable"></a> CBaseTransition:: GetRelatedVariable

관련 변수에 대 한 포인터를 반환 합니다.

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>반환 값

애니메이션 변수에 대 한 유효한 포인터 이거나, 애니메이션 변수가 SetRelatedVariable에 의해 설정 되지 않은 경우 NULL입니다.

### <a name="remarks"></a>설명

관련 애니메이션 변수에 대 한 접근자입니다.

## <a name="cbasetransitiongetstartkeyframe"></a><a name="getstartkeyframe"></a> CBaseTransition:: GetStartKeyframe

시작 키 프레임을 반환 합니다.

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>반환 값

키 프레임에 대 한 유효한 포인터 이거나, 키 프레임 후에 전환을 시작 하지 않아야 하는 경우 NULL입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 이전에 SetKeyframes에 의해 설정 된 keyframe 개체에 액세스할 수 있습니다. 전환이 스토리 보드에 추가 될 때 최상위 코드에 의해 호출 됩니다.

## <a name="cbasetransitiongettransition"></a><a name="gettransition"></a> CBaseTransition:: GetTransition

내부 COM 전환 개체에 대 한 포인터를 반환 합니다.

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>매개 변수

*pLibrary*<br/>
표준 전환을 만드는 전환 라이브러리에 대 한 포인터입니다. 사용자 지정 전환의 경우 NULL 일 수 있습니다.

*pFactory*<br/>
사용자 지정 전환을 만드는 전환 팩터리에 대 한 포인터입니다. 표준 전환의 경우 NULL 일 수 있습니다.

### <a name="return-value"></a>반환 값

Iui대 여 전환에 대 한 유효한 포인터 이거나, 기본 전환을 만들 수 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

이 메서드는 기본 COM 전환 개체에 대 한 포인터를 반환 하 고 필요한 경우이를 만듭니다.

## <a name="cbasetransitiongettype"></a><a name="gettype"></a> CBaseTransition:: GetType

전환 유형을 반환 합니다.

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>반환 값

TRANSITION_TYPE 열거형 값 중 하나입니다.

### <a name="remarks"></a>설명

이 메서드는 해당 형식으로 전환 개체를 식별 하는 데 사용할 수 있습니다. 형식은 파생 클래스의 생성자에 설정 됩니다.

## <a name="cbasetransitionisadded"></a><a name="isadded"></a> CBaseTransition:: IsAdded 됨

전환이 스토리 보드에 추가 되었는지 여부를 나타냅니다.

```
BOOL IsAdded();
```

### <a name="return-value"></a>반환 값

전환이 스토리 보드에 추가 되 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 플래그는 최상위 코드에서 storyboard에 전환을 추가할 때 내부적으로 설정 됩니다.

## <a name="cbasetransitionm_badded"></a><a name="m_badded"></a> CBaseTransition:: m_bAdded

전환을 storyboard에 추가할지 여부를 지정 합니다.

```
BOOL m_bAdded;
```

## <a name="cbasetransitionm_pendkeyframe"></a><a name="m_pendkeyframe"></a> CBaseTransition:: m_pEndKeyframe

전환의 끝을 지정 하는 키 프레임에 대 한 포인터를 저장 합니다.

```
CBaseKeyFrame* m_pEndKeyframe;
```

## <a name="cbasetransitionm_prelatedvariable"></a><a name="m_prelatedvariable"></a> CBaseTransition:: m_pRelatedVariable

M_transition에 저장 된 전환과 함께 애니메이션 되는 애니메이션 변수에 대 한 포인터입니다.

```
CAnimationVariable* m_pRelatedVariable;
```

## <a name="cbasetransitionm_pstartkeyframe"></a><a name="m_pstartkeyframe"></a> CBaseTransition:: m_pStartKeyframe

전환의 시작을 지정 하는 키 프레임에 대 한 포인터를 저장 합니다.

```
CBaseKeyFrame* m_pStartKeyframe;
```

## <a name="cbasetransitionm_transition"></a><a name="m_transition"></a> CBaseTransition:: m_transition

Iui애니메이션 전환에 대 한 포인터를 저장 합니다. COM 전환 개체가 생성 되지 않은 경우 NULL입니다.

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

## <a name="cbasetransitionm_type"></a><a name="m_type"></a> CBaseTransition:: m_type

전환 유형을 저장 합니다.

```
TRANSITION_TYPE m_type;
```

## <a name="cbasetransitionsetkeyframes"></a><a name="setkeyframes"></a> CBaseTransition:: SetKeyframes

전환에 대 한 키 프레임을 설정 합니다.

```cpp
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>매개 변수

*pStart*<br/>
전환의 시작을 지정 하는 키 프레임입니다.

*보류*<br/>
전환의 끝을 지정 하는 키 프레임입니다.

### <a name="remarks"></a>설명

이 메서드는 지정 된 키 프레임 후 전환을 시작 하도록 지시 하 고, 필요에 따라 보류가 NULL이 아닌 경우 지정 된 키 프레임 앞에서 종료 되도록 합니다. Duration 매개 변수를 지정 하 여 전환을 만든 경우 시작 및 종료 키 프레임 사이의 시간 동안 해당 기간을 덮어씁니다.

## <a name="cbasetransitionsetrelatedvariable"></a><a name="setrelatedvariable"></a> CBaseTransition:: SetRelatedVariable

애니메이션 변수와 전환 간의 관계를 설정 합니다.

```cpp
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>매개 변수

*pVariable*<br/>
관련 애니메이션 변수에 대 한 포인터입니다.

### <a name="remarks"></a>설명

애니메이션 변수와 전환 간의 관계를 설정 합니다. 전환은 하나의 변수에만 적용할 수 있습니다.

## <a name="cbasetransitiontransition_type-enumeration"></a><a name="transition_type_enumeration"></a> CBaseTransition:: TRANSITION_TYPE 열거형

Windows 애니메이션 API의 MFC 구현에서 현재 지원 되는 전환 유형을 정의 합니다.

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>설명

전환 형식은 특정 전환의 생성자에 설정 됩니다. 예를 들어 CSinusoidalTransitionFromRange는 해당 형식을 SINUSOIDAL_FROM_RANGE로 설정 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
