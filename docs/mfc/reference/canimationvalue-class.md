---
description: '자세한 정보: CAnimationValue 클래스'
title: CAnimationValue 클래스
ms.date: 11/04/2016
f1_keywords:
- CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationValue::GetValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationValue::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationValue::m_value
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
ms.openlocfilehash: d704e83d286b4078af90d09edef35e8445d149d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336748"
---
# <a name="canimationvalue-class"></a>CAnimationValue 클래스

하나의 값을 갖는 애니메이션 개체 기능을 구현합니다.

## <a name="syntax"></a>구문

```
class CAnimationValue : public CAnimationBaseObject;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAnimationValue:: CAnimationValue](#canimationvalue)|오버로드됨. CAnimationValue 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAnimationValue:: AddTransition](#addtransition)|값에 적용 될 전환을 추가 합니다.|
|[CAnimationValue:: GetValue](#getvalue)|오버로드됨. 현재 값을 검색 합니다.|
|[CAnimationValue:: GetVariable](#getvariable)|캡슐화 된 애니메이션 변수에 대 한 액세스를 제공 합니다.|
|[CAnimationValue:: SetDefaultValue](#setdefaultvalue)|기본값을 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CAnimationValue:: GetAnimationVariableList](#getanimationvariablelist)|캡슐화 된 애니메이션 변수를 목록에 넣습니다. ( [Canimationbaseobject:: GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)를 재정의 합니다.)|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAnimationValue:: operator DOUBLE](#operator_double)|CAnimationValue와 DOUBLE 간의 변환을 제공 합니다.|
|[CAnimationValue:: operator INT32](#operator_int32)|CAnimationValue와 INT32 간의 변환을 제공 합니다.|
|[CAnimationValue:: operator =](#operator_eq)|오버로드됨. CAnimationValue에 INT32 값을 할당 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAnimationValue:: m_value](#m_value)|애니메이션 값을 나타내는 캡슐화 된 애니메이션 변수입니다.|

## <a name="remarks"></a>설명

CAnimationValue 클래스는 단일 Canimationvalue 개체를 캡슐화 하 고 응용 프로그램에서 애니메이션 된 단일 값을 나타낼 수 있습니다. 예를 들어 애니메이션 투명도 (페이드 효과), 각도 (개체 회전) 또는 다른 모든 경우에는 애니메이션이 적용 된 단일 값에 따라 애니메이션을 만들어야 하는 경우이 클래스를 사용할 수 있습니다. 응용 프로그램에서이 클래스를 사용 하려면이 클래스의 개체를 인스턴스화한 후 CAnimationController:: Addanimation 개체를 사용 하 여 애니메이션 컨트롤러에 추가 하 고 값에 적용 될 각 전환에 대해 AddTransition을 호출 하면 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="canimationvalueaddtransition"></a><a name="addtransition"></a> CAnimationValue:: AddTransition

값에 적용 될 전환을 추가 합니다.

```cpp
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>매개 변수

*pTransition*<br/>
전환 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

애니메이션 변수에 적용할 전환의 내부 목록에 전환을 추가 하려면이 함수를 호출 합니다. 전환을 추가 하면 즉시 적용 되지 않고 내부 목록에 저장 됩니다. CAnimationController:: AnimateGroup를 호출 하면 전환이 적용 됩니다 (특정 값에 대 한 스토리 보드에 추가 됨).

## <a name="canimationvaluecanimationvalue"></a><a name="canimationvalue"></a> CAnimationValue:: CAnimationValue

CAnimationValue 개체를 생성 합니다.

```
CAnimationValue();

CAnimationValue(
    DOUBLE dblDefaultValue,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>매개 변수

*dblDefaultValue*<br/>
기본값을 지정 합니다.

*nGroupID*<br/>
그룹 ID를 지정 합니다.

*nObjectID*<br/>
개체 ID를 지정 합니다.

*dwUserData*<br/>
사용자 정의 데이터를 지정 합니다.

### <a name="remarks"></a>설명

기본 속성을 사용 하 여 CAnimationValue 개체 생성: 기본값, 그룹 ID 및 개체 ID가 0으로 설정 되어 있습니다.

## <a name="canimationvaluegetanimationvariablelist"></a><a name="getanimationvariablelist"></a> CAnimationValue:: GetAnimationVariableList

캡슐화 된 애니메이션 변수를 목록에 넣습니다.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>매개 변수

*.lst*<br/>
함수는 반환 될 때 애니메이션 된 값을 나타내는 CAnimationVariable에 대 한 포인터를 포함 합니다.

## <a name="canimationvaluegetvalue"></a><a name="getvalue"></a> CAnimationValue:: GetValue

현재 값을 검색 합니다.

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>매개 변수

*dblValue*<br/>
출력 함수는 반환 될 때 애니메이션 변수의 현재 값을 포함 합니다.

*N 값*<br/>
출력 함수는 반환 될 때 애니메이션 변수의 현재 값을 포함 합니다.

### <a name="return-value"></a>반환 값

현재 값이 성공적으로 검색 되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

현재 값을 검색 하려면이 함수를 호출 합니다. 이 구현은 캡슐화 된 COM 개체를 호출 하 고, 호출이 실패 하면이 메서드는 이전에 생성자 또는 SetDefaultValue로 설정 된 기본값을 반환 합니다.

## <a name="canimationvaluegetvariable"></a><a name="getvariable"></a> CAnimationValue:: GetVariable

캡슐화 된 애니메이션 변수에 대 한 액세스를 제공 합니다.

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>반환 값

캡슐화 된 애니메이션 변수에 대 한 참조입니다.

### <a name="remarks"></a>설명

캡슐화 된 애니메이션 변수에 액세스 하려면이 메서드를 사용 합니다. CAnimationVariable에서 애니메이션 변수를 만들지 않은 경우 포인터가 NULL 일 수 있는 기본 IUIAnimationVariable 개체에 액세스할 수 있습니다.

## <a name="canimationvaluem_value"></a><a name="m_value"></a> CAnimationValue:: m_value

애니메이션 값을 나타내는 캡슐화 된 애니메이션 변수입니다.

```
CAnimationVariable m_value;
```

## <a name="canimationvalueoperator-double"></a><a name="operator_double"></a> CAnimationValue:: operator DOUBLE

CAnimationValue와 DOUBLE 간의 변환을 제공 합니다.

```
operator DOUBLE();
```

### <a name="return-value"></a>반환 값

애니메이션 값의 현재 값입니다.

### <a name="remarks"></a>설명

CAnimationValue와 DOUBLE 간의 변환을 제공 합니다. 이 메서드는 내부적으로 GetValue를 호출 하 고 오류를 확인 하지 않습니다. GetValue가 실패 하는 경우 반환 된 값에는 이전에 생성자 또는 SetDefaultValue로 설정 된 기본값이 포함 됩니다.

## <a name="canimationvalueoperator-int32"></a><a name="operator_int32"></a> CAnimationValue:: operator INT32

CAnimationValue와 INT32 간의 변환을 제공 합니다.

```
operator INT32();
```

### <a name="return-value"></a>반환 값

애니메이션 값의 현재 값 (정수)입니다.

### <a name="remarks"></a>설명

CAnimationValue와 INT32 간의 변환을 제공 합니다. 이 메서드는 내부적으로 GetValue를 호출 하 고 오류를 확인 하지 않습니다. GetValue가 실패 하는 경우 반환 된 값에는 이전에 생성자 또는 SetDefaultValue로 설정 된 기본값이 포함 됩니다.

## <a name="canimationvalueoperator"></a><a name="operator_eq"></a> CAnimationValue:: operator =

CAnimationValue에 DOUBLE 값을 할당 합니다.

```cpp
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>매개 변수

*dblVal*<br/>
애니메이션 값에 할당할 값을 지정 합니다.

*nVal*<br/>
애니메이션 값에 할당할 값을 지정 합니다.

### <a name="remarks"></a>설명

CAnimationValue에 DOUBLE 값을 할당 합니다. 이 값은 캡슐화 된 애니메이션 변수에 대 한 기본값으로 설정 됩니다. 이 애니메이션 개체를 이벤트 (ValueChanged 또는 IntegerValueChanged)에 구독 한 경우 이러한 이벤트를 다시 사용 하도록 설정 해야 합니다.

## <a name="canimationvaluesetdefaultvalue"></a><a name="setdefaultvalue"></a> CAnimationValue:: SetDefaultValue

기본값을 설정 합니다.

```cpp
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>매개 변수

*dblDefaultValue*<br/>
기본값을 지정 합니다.

### <a name="remarks"></a>설명

기본값을 설정 하려면이 메서드를 사용 합니다. 애니메이션이 시작 되지 않았거나 내부 COM 개체가 만들어지지 않은 경우 기본값이 응용 프로그램으로 반환 됩니다. CAnimationVarible에 캡슐화 된 기본 COM 개체가 이미 만들어진 경우이 메서드는이를 다시 만듭니다. 따라서/EnableIntegerValueChanged 메서드를 다시 호출 해야 할 수도 있습니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
