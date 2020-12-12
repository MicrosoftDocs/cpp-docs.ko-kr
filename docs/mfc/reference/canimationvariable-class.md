---
description: '자세한 정보: CAnimationVariable 클래스'
title: CAnimationVariable 클래스
ms.date: 03/27/2019
f1_keywords:
- CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationVariable::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::Create
- AFXANIMATIONCONTROLLER/CAnimationVariable::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_dblDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_lstTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_pParentObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_variable
helpviewer_keywords:
- CAnimationVariable [MFC], CAnimationVariable
- CAnimationVariable [MFC], AddTransition
- CAnimationVariable [MFC], ApplyTransitions
- CAnimationVariable [MFC], ClearTransitions
- CAnimationVariable [MFC], Create
- CAnimationVariable [MFC], CreateTransitions
- CAnimationVariable [MFC], EnableIntegerValueChangedEvent
- CAnimationVariable [MFC], EnableValueChangedEvent
- CAnimationVariable [MFC], GetDefaultValue
- CAnimationVariable [MFC], GetParentAnimationObject
- CAnimationVariable [MFC], GetValue
- CAnimationVariable [MFC], GetVariable
- CAnimationVariable [MFC], SetDefaultValue
- CAnimationVariable [MFC], SetParentAnimationObject
- CAnimationVariable [MFC], m_bAutodestroyTransitions
- CAnimationVariable [MFC], m_dblDefaultValue
- CAnimationVariable [MFC], m_lstTransitions
- CAnimationVariable [MFC], m_pParentObject
- CAnimationVariable [MFC], m_variable
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
ms.openlocfilehash: 66f0aacc0338acd4096b4c65cec45489a625910c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207919"
---
# <a name="canimationvariable-class"></a>CAnimationVariable 클래스

애니메이션 변수를 나타냅니다.

## <a name="syntax"></a>구문

```
class CAnimationVariable;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAnimationVariable:: CAnimationVariable](#canimationvariable)|애니메이션 변수 개체를 생성 합니다.|
|[CAnimationVariable:: ~ CAnimationVariable](#_dtorcanimationvariable)|소멸자입니다. CAnimationVariable 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAnimationVariable:: AddTransition](#addtransition)|전환을 추가 합니다.|
|[CAnimationVariable:: ApplyTransitions](#applytransitions)|내부 목록의 전환을 storyboard에 추가 합니다.|
|[CAnimationVariable:: ClearTransitions](#cleartransitions)|전환을 지웁니다.|
|[CAnimationVariable:: Create](#create)|기본 애니메이션 변수 COM 개체를 만듭니다.|
|[CAnimationVariable:: CreateTransitions](#createtransitions)|이 애니메이션 변수에 적용할 모든 전환을 만듭니다.|
|[CAnimationVariable:: EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|IntegerValueChanged 이벤트를 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CAnimationVariable:: EnableValueChangedEvent](#enablevaluechangedevent)|ValueChanged 이벤트를 사용 하거나 사용 하지 않도록 설정 합니다.|
|[CAnimationVariable:: GetDefaultValue](#getdefaultvalue)|기본값을 반환 합니다.|
|[CAnimationVariable:: GetParentAnimationObject](#getparentanimationobject)|부모 애니메이션 개체를 반환 합니다.|
|[CAnimationVariable:: GetValue](#getvalue)|오버로드됨. 애니메이션 변수의 현재 값을 반환 합니다.|
|[CAnimationVariable:: GetVariable](#getvariable)|Iui애니메이션 COM 개체에 대 한 포인터를 반환 합니다.|
|[CAnimationVariable:: SetDefaultValue](#setdefaultvalue)|기본값을 설정 하 고 Iui애니메이션 COM 개체를 해제 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CAnimationVariable:: Setparent애니메이션 개체](#setparentanimationobject)|애니메이션 변수와 애니메이션 개체 간의 관계를 설정 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAnimationVariable:: m_bAutodestroyTransitions](#m_bautodestroytransitions)|관련 전환 개체를 삭제할지 여부를 지정 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAnimationVariable:: m_dblDefaultValue](#m_dbldefaultvalue)|Iui애니메이션으로 전파 되는 기본값을 지정 합니다.|
|[CAnimationVariable:: m_lstTransitions](#m_lsttransitions)|이 애니메이션 변수에 애니메이션 효과를 주는 전환 목록을 포함 합니다.|
|[CAnimationVariable:: m_pParentObject](#m_pparentobject)|이 애니메이션 변수를 캡슐화 하는 애니메이션 개체에 대 한 포인터입니다.|
|[CAnimationVariable:: m_variable](#m_variable)|Iui애니메이션 COM 개체에 대 한 포인터를 저장 합니다. COM 개체를 아직 만들지 않은 경우 NULL이 고, 만들지 못한 경우에는 NULL입니다.|

## <a name="remarks"></a>설명

CAnimationVariable 클래스는 Iui애니메이션 COM 개체를 캡슐화 합니다. 스토리 보드의 애니메이션 변수에 적용 되는 전환의 목록도 포함 됩니다. CAnimationVariable 개체는 애니메이션 개체에 포함 되어 있습니다 .이 개체는 애니메이션 된 값, 점, 크기, 색 및 사각형을 응용 프로그램에 나타낼 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CAnimationVariable`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="canimationvariablecanimationvariable"></a><a name="_dtorcanimationvariable"></a> CAnimationVariable:: ~ CAnimationVariable

소멸자입니다. CAnimationVariable 개체가 제거 될 때 호출 됩니다.

```
virtual ~CAnimationVariable();
```

## <a name="canimationvariableaddtransition"></a><a name="addtransition"></a> CAnimationVariable:: AddTransition

전환을 추가 합니다.

```cpp
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>매개 변수

*pTransition*<br/>
추가할 전환에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 애니메이션 변수에 적용 될 내부 전환 목록에 전환을 추가 하기 위해 호출 됩니다. 애니메이션을 예약할 때이 목록을 지워야 합니다.

## <a name="canimationvariableapplytransitions"></a><a name="applytransitions"></a> CAnimationVariable:: ApplyTransitions

내부 목록의 전환을 storyboard에 추가 합니다.

```cpp
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>매개 변수

*pController*<br/>
부모 애니메이션 컨트롤러에 대 한 포인터입니다.

*pStoryboard*<br/>
Storyboard에 대 한 포인터입니다.

*bDependOnKeyframes*<br/>
이 메서드가 키 프레임에 종속 된 전환을 추가 해야 하는 경우 TRUE입니다.

### <a name="remarks"></a>설명

이 메서드는 내부 목록에서 storyboard로 전환을 추가 합니다. 키 프레임을 여러 번 호출 하 여 키프레임에 종속 되지 않는 전환을 추가 하 고 키프레임에 종속 된 전환을 추가 합니다. 기본 애니메이션 변수 COM 개체를 만들지 않은 경우이 메서드는이 단계에서 만듭니다.

## <a name="canimationvariablecanimationvariable"></a><a name="canimationvariable"></a> CAnimationVariable:: CAnimationVariable

애니메이션 변수 개체를 생성 합니다.

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>매개 변수

*dblDefaultValue*<br/>
기본값을 지정 합니다.

### <a name="remarks"></a>설명

애니메이션 변수 개체를 생성 하 고 기본값을 설정 합니다. 기본값은 변수가 애니메이션이 적용 되지 않거나 애니메이션을 적용할 수 없을 때 사용 됩니다.

## <a name="canimationvariablecleartransitions"></a><a name="cleartransitions"></a> CAnimationVariable:: ClearTransitions

전환을 지웁니다.

```cpp
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>매개 변수

*bAutodestroy*<br/>
이 메서드가 전환 개체를 삭제 해야 하는지 여부를 지정 합니다.

### <a name="remarks"></a>설명

이 메서드는 내부 전환 목록에서 모든 전환을 제거 합니다. BAutodestroy TRUE 이거나 m_bAutodestroyTransitions TRUE 이면 전환이 삭제 됩니다. 그렇지 않으면 호출자가 전환 개체의 할당을 취소 해야 합니다.

## <a name="canimationvariablecreate"></a><a name="create"></a> CAnimationVariable:: Create

기본 애니메이션 변수 COM 개체를 만듭니다.

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>매개 변수

*pManager*<br/>
애니메이션 관리자에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

애니메이션 변수가 성공적으로 만들어졌으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 기본 애니메이션 변수 COM 개체를 만들고 기본값을 설정 합니다.

## <a name="canimationvariablecreatetransitions"></a><a name="createtransitions"></a> CAnimationVariable:: CreateTransitions

이 애니메이션 변수에 적용할 모든 전환을 만듭니다.

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>매개 변수

*pLibrary*<br/>
표준 전환 라이브러리를 정의 하는 [IUIAnimationTransitionLibrary 인터페이스](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

전환이 성공적으로 생성 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 변수의 내부 전환 목록에 추가 된 전환을 만들어야 할 때 프레임 워크에서 호출 됩니다.

## <a name="canimationvariableenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a> CAnimationVariable:: EnableIntegerValueChangedEvent

IntegerValueChanged 이벤트를 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>매개 변수

*pController*<br/>
부모 컨트롤러에 대 한 포인터입니다.

*bEnable*<br/>
TRUE-이벤트 사용, FALSE-이벤트 사용 안 함

### <a name="remarks"></a>설명

ValueChanged 이벤트를 사용 하는 경우 프레임 워크는 가상 메서드인 CAnimationController:: OnAnimationIntegerValueChanged를 호출 합니다. 이 이벤트를 처리 하기 위해 CAnimationController에서 파생 된 클래스에서 재정의 해야 합니다. 이 메서드는 애니메이션 변수의 정수 값이 변경 될 때마다 호출 됩니다.

## <a name="canimationvariableenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a> CAnimationVariable:: EnableValueChangedEvent

ValueChanged 이벤트를 사용 하거나 사용 하지 않도록 설정 합니다.

```cpp
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>매개 변수

*pController*<br/>
부모 컨트롤러에 대 한 포인터입니다.

*bEnable*<br/>
TRUE-이벤트 사용, FALSE-이벤트 사용 안 함

### <a name="remarks"></a>설명

ValueChanged 이벤트를 사용 하는 경우 프레임 워크는 가상 메서드인 CAnimationController:: OnAnimationValueChanged를 호출 합니다. 이 이벤트를 처리 하기 위해 CAnimationController에서 파생 된 클래스에서 재정의 해야 합니다. 이 메서드는 애니메이션 변수 값이 변경 될 때마다 호출 됩니다.

## <a name="canimationvariablegetdefaultvalue"></a><a name="getdefaultvalue"></a> CAnimationVariable:: GetDefaultValue

기본값을 반환 합니다.

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>반환 값

기본값입니다.

### <a name="remarks"></a>설명

애니메이션 변수의 기본값을 가져오려면이 함수를 사용 합니다. 생성자 또는 SetDefaultValue 메서드에서 기본값을 설정할 수 있습니다.

## <a name="canimationvariablegetparentanimationobject"></a><a name="getparentanimationobject"></a> CAnimationVariable:: GetParentAnimationObject

부모 애니메이션 개체를 반환 합니다.

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>반환 값

관계가 설정 된 경우 부모 애니메이션 개체에 대 한 포인터이 고, 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 부모 애니메이션 개체 (컨테이너)에 대 한 포인터를 검색할 수 있습니다.

## <a name="canimationvariablegetvalue"></a><a name="getvalue"></a> CAnimationVariable:: GetValue

애니메이션 변수의 현재 값을 반환 합니다.

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>매개 변수

*dblValue*<br/>
애니메이션 변수의 현재 값입니다.

*N 값*<br/>
애니메이션 변수의 현재 값입니다.

### <a name="return-value"></a>반환 값

값을 성공적으로 얻 었는 지, 아니면 기본 애니메이션 변수가 만들어지지 S_OK 합니다. 그렇지 않으면 HRESULT 오류 코드입니다.

### <a name="remarks"></a>설명

애니메이션 변수의 현재 값을 검색 하기 위해이 메서드를 호출할 수 있습니다. 기본 COM 개체를 만들지 않은 경우 dblValue는 함수가 반환 될 때 기본값을 포함 합니다.

## <a name="canimationvariablegetvariable"></a><a name="getvariable"></a> CAnimationVariable:: GetVariable

Iui애니메이션 COM 개체에 대 한 포인터를 반환 합니다.

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>반환 값

Iuianimation Variable COM 개체에 대 한 유효한 포인터 이거나, 애니메이션 변수를 만들지 않았거나 만들 수 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여 기본 Iui애니메이션 COM 개체에 액세스 하 고 필요한 경우 해당 메서드를 직접 호출 합니다.

## <a name="canimationvariablem_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a> CAnimationVariable:: m_bAutodestroyTransitions

관련 전환 개체를 삭제할지 여부를 지정 합니다.

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>설명

전환 개체를 전환의 내부 목록에서 제거할 때 강제로 삭제 하려면이 값을 TRUE로 설정 합니다. 이 값이 FALSE 이면 응용 프로그램을 호출 하 여 전환을 삭제 해야 합니다. 애니메이션을 예약한 후에는 항상 전환 목록이 지워집니다. 기본값은 FALSE입니다.

## <a name="canimationvariablem_dbldefaultvalue"></a><a name="m_dbldefaultvalue"></a> CAnimationVariable:: m_dblDefaultValue

Iui애니메이션으로 전파 되는 기본값을 지정 합니다.

```
DOUBLE m_dblDefaultValue;
```

## <a name="canimationvariablem_lsttransitions"></a><a name="m_lsttransitions"></a> CAnimationVariable:: m_lstTransitions

이 애니메이션 변수에 애니메이션 효과를 주는 전환 목록을 포함 합니다.

```
CObList m_lstTransitions;
```

## <a name="canimationvariablem_pparentobject"></a><a name="m_pparentobject"></a> CAnimationVariable:: m_pParentObject

이 애니메이션 변수를 캡슐화 하는 애니메이션 개체에 대 한 포인터입니다.

```
CAnimationBaseObject* m_pParentObject;
```

## <a name="canimationvariablem_variable"></a><a name="m_variable"></a> CAnimationVariable:: m_variable

Iui애니메이션 COM 개체에 대 한 포인터를 저장 합니다. COM 개체를 아직 만들지 않은 경우 NULL이 고, 만들지 못한 경우에는 NULL입니다.

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

## <a name="canimationvariablesetdefaultvalue"></a><a name="setdefaultvalue"></a> CAnimationVariable:: SetDefaultValue

기본값을 설정 하 고 Iui애니메이션 COM 개체를 해제 합니다.

```cpp
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>매개 변수

*dblDefaultValue*<br/>
새 기본값을 지정 합니다.

### <a name="remarks"></a>설명

기본값을 다시 설정 하려면이 메서드를 사용 합니다. 이 메서드는 내부 Iui애니메이션 COM 개체를 해제 하므로 애니메이션 변수를 다시 만들 때 기본 COM 개체가 새 기본값을 가져옵니다. 애니메이션 변수를 나타내는 COM 개체가 생성 되지 않은 경우 또는 변수에 애니메이션이 적용 되지 않은 경우에는 GetValue에서 기본값을 반환 합니다.

## <a name="canimationvariablesetparentanimationobject"></a><a name="setparentanimationobject"></a> CAnimationVariable:: Setparent애니메이션 개체

애니메이션 변수와 애니메이션 개체 간의 관계를 설정 합니다.

```cpp
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>매개 변수

*pParentObject*<br/>
이 변수를 포함 하는 애니메이션 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 애니메이션 변수와이를 캡슐화 하는 애니메이션 개체 사이에 일 대 일 관계를 설정 하기 위해 내부적으로 호출 됩니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
