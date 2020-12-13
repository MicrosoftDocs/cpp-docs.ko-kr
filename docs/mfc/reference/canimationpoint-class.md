---
description: '자세한 정보: CAnimationPoint 클래스'
title: CAnimationPoint 클래스
ms.date: 11/04/2016
f1_keywords:
- CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetX
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetY
- AFXANIMATIONCONTROLLER/CAnimationPoint::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_xValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_yValue
helpviewer_keywords:
- CAnimationPoint [MFC], CAnimationPoint
- CAnimationPoint [MFC], AddTransition
- CAnimationPoint [MFC], GetDefaultValue
- CAnimationPoint [MFC], GetValue
- CAnimationPoint [MFC], GetX
- CAnimationPoint [MFC], GetY
- CAnimationPoint [MFC], SetDefaultValue
- CAnimationPoint [MFC], GetAnimationVariableList
- CAnimationPoint [MFC], m_xValue
- CAnimationPoint [MFC], m_yValue
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
ms.openlocfilehash: ddefb93950f0ff1109478f3574413faf9f60a22a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336790"
---
# <a name="canimationpoint-class"></a>CAnimationPoint 클래스

좌표에 애니메이션을 적용할 수 있는 점 기능을 구현합니다.

## <a name="syntax"></a>구문

```
class CAnimationPoint : public CAnimationBaseObject;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAnimationPoint:: CAnimationPoint](#canimationpoint)|오버로드됨. CAnimationPoint 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAnimationPoint:: AddTransition](#addtransition)|X 및 Y 좌표에 대 한 전환을 추가 합니다.|
|[CAnimationPoint:: GetDefaultValue](#getdefaultvalue)|X 및 Y 좌표의 기본값을 반환 합니다.|
|[CAnimationPoint:: GetValue](#getvalue)|현재 값을 반환 합니다.|
|[CAnimationPoint:: GetX](#getx)|X 좌표에 대해 CAnimationVariable에 대 한 액세스를 제공 합니다.|
|[CAnimationPoint:: GetY](#gety)|Y 좌표의 CAnimationVariable에 대 한 액세스를 제공 합니다.|
|[CAnimationPoint:: SetDefaultValue](#setdefaultvalue)|기본값을 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CAnimationPoint:: GetAnimationVariableList](#getanimationvariablelist)|캡슐화 된 애니메이션 변수를 목록에 넣습니다. ( [Canimationbaseobject:: GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)를 재정의 합니다.)|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAnimationPoint:: operator CPoint](#operator_cpoint)|CAnimationPoint를 CPoint로 변환 합니다.|
|[CAnimationPoint:: operator =](#operator_eq)|PtSrc를 CAnimationPoint에 할당 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAnimationPoint:: m_xValue](#m_xvalue)|애니메이션 지점의 X 좌표를 나타내는 캡슐화 된 애니메이션 변수입니다.|
|[CAnimationPoint:: m_yValue](#m_yvalue)|애니메이션 지점의 Y 좌표를 나타내는 캡슐화 된 애니메이션 변수입니다.|

## <a name="remarks"></a>설명

CAnimationPoint 클래스는 두 개의 Canimationpoint 개체를 캡슐화 하 고 응용 프로그램에 점을 나타낼 수 있습니다. 예를 들어이 클래스를 사용 하 여 화면에서 개체의 위치에 애니메이션 효과를 적용할 수 있습니다 (예: 텍스트 문자열, 원, 점 등). 응용 프로그램에서이 클래스를 사용 하려면이 클래스의 개체를 인스턴스화한 후 CAnimationController:: Addanimation 개체를 사용 하 여 애니메이션 컨트롤러에 추가 하 고 X 및/또는 Y 좌표에 적용 될 각 전환에 대해 AddTransition을 호출 하면 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="canimationpointaddtransition"></a><a name="addtransition"></a> CAnimationPoint:: AddTransition

X 및 Y 좌표에 대 한 전환을 추가 합니다.

```cpp
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>매개 변수

*pXTransition*<br/>
X 좌표에 대 한 전환에 대 한 포인터입니다.

*pYTransition*<br/>
Y 좌표에 대 한 전환 포인터입니다.

### <a name="remarks"></a>설명

이 함수를 호출 하 여 지정 된 전환을 X 및 Y 좌표의 애니메이션 변수에 적용할 내부 전환 목록에 추가 합니다. 전환을 추가 하면 즉시 적용 되지 않고 내부 목록에 저장 됩니다. CAnimationController:: AnimateGroup를 호출 하면 전환이 적용 됩니다 (특정 값에 대 한 스토리 보드에 추가 됨). 좌표 중 하나에 전환을 적용할 필요가 없으면 NULL을 전달할 수 있습니다.

## <a name="canimationpointcanimationpoint"></a><a name="canimationpoint"></a> CAnimationPoint:: CAnimationPoint

CAnimationPoint 개체를 생성 합니다.

```
CAnimationPoint();

CAnimationPoint(
    const CPoint& ptDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>매개 변수

*ptDefault*<br/>
기본 점 좌표를 지정 합니다.

*nGroupID*<br/>
그룹 ID를 지정 합니다.

*nObjectID*<br/>
개체 ID를 지정 합니다.

*dwUserData*<br/>
사용자 정의 데이터를 지정 합니다.

### <a name="remarks"></a>설명

기본 속성을 사용 하 여 CAnimationPoint 개체를 생성 합니다. 기본 점 좌표, 그룹 ID 및 개체 ID는 0으로 설정 됩니다.

## <a name="canimationpointgetanimationvariablelist"></a><a name="getanimationvariablelist"></a> CAnimationPoint:: GetAnimationVariableList

캡슐화 된 애니메이션 변수를 목록에 넣습니다.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>매개 변수

*.lst*<br/>
함수는 반환 될 때 X 및 Y 좌표를 나타내는 두 개의 CAnimationVariable 개체에 대 한 포인터를 포함 합니다.

## <a name="canimationpointgetdefaultvalue"></a><a name="getdefaultvalue"></a> CAnimationPoint:: GetDefaultValue

X 및 Y 좌표의 기본값을 반환 합니다.

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>반환 값

기본값을 포함 하는 지점입니다.

### <a name="remarks"></a>설명

이전에 생성자 또는 SetDefaultValue에 의해 설정 된 기본값을 검색 하려면이 함수를 호출 합니다.

## <a name="canimationpointgetvalue"></a><a name="getvalue"></a> CAnimationPoint:: GetValue

현재 값을 반환 합니다.

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>매개 변수

*ptValue*<br/>
출력 이 메서드가 반환 하는 현재 값을 포함 합니다.

### <a name="return-value"></a>반환 값

현재 값이 성공적으로 검색 되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

애니메이션 지점의 현재 값을 검색 하려면이 함수를 호출 합니다. 이 메서드가 실패 하거나 X 및 Y 좌표의 기본 COM 개체가 초기화 되지 않은 경우 ptValue는 이전에 생성자 또는 SetDefaultValue에서 설정 된 기본값을 포함 합니다.

## <a name="canimationpointgetx"></a><a name="getx"></a> CAnimationPoint:: GetX

X 좌표에 대해 CAnimationVariable에 대 한 액세스를 제공 합니다.

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>반환 값

X 좌표를 나타내는 캡슐화 된 CAnimationVariable에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 X 좌표를 나타내는 기본 CAnimationVariable에 직접 액세스할 수 있습니다.

## <a name="canimationpointgety"></a><a name="gety"></a> CAnimationPoint:: GetY

Y 좌표의 CAnimationVariable에 대 한 액세스를 제공 합니다.

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>반환 값

Y 좌표를 나타내는 캡슐화 된 CAnimationVariable에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 Y 좌표를 나타내는 기본 CAnimationVariable에 직접 액세스할 수 있습니다.

## <a name="canimationpointm_xvalue"></a><a name="m_xvalue"></a> CAnimationPoint:: m_xValue

애니메이션 지점의 X 좌표를 나타내는 캡슐화 된 애니메이션 변수입니다.

```
CAnimationVariable m_xValue;
```

## <a name="canimationpointm_yvalue"></a><a name="m_yvalue"></a> CAnimationPoint:: m_yValue

애니메이션 지점의 Y 좌표를 나타내는 캡슐화 된 애니메이션 변수입니다.

```
CAnimationVariable m_yValue;
```

## <a name="canimationpointoperator-cpoint"></a><a name="operator_cpoint"></a> CAnimationPoint:: operator CPoint

CAnimationPoint를 CPoint로 변환 합니다.

```
operator CPoint();
```

### <a name="return-value"></a>반환 값

CPoint 인 CAnimationPoint의 현재 값입니다.

### <a name="remarks"></a>설명

이 함수는 내부적으로 GetValue를 호출 합니다. 특정 이유에 대해 GetValue가 실패 한 경우 반환 되는 점은 X 및 Y 좌표의 기본값을 포함 합니다.

## <a name="canimationpointoperator"></a><a name="operator_eq"></a> CAnimationPoint:: operator =

PtSrc를 CAnimationPoint에 할당 합니다.

```cpp
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>매개 변수

*ptSrc*<br/>
는 CPoint 또는 POINT를 참조 합니다.

### <a name="remarks"></a>설명

PtSrc를 CAnimationPoint에 할당 합니다. 이 연산자는 생성 된 X 및 Y 좌표에 대 한 기본 COM 개체를 다시 생성 하는 SetDefaultValue를 호출 하기 때문에 애니메이션을 시작 하기 전에이 작업을 수행 하는 것이 좋습니다. 이 애니메이션 개체를 이벤트 (ValueChanged 또는 IntegerValueChanged)에 구독 한 경우 이러한 이벤트를 다시 사용 하도록 설정 해야 합니다.

## <a name="canimationpointsetdefaultvalue"></a><a name="setdefaultvalue"></a> CAnimationPoint:: SetDefaultValue

기본값을 설정 합니다.

```cpp
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>매개 변수

*ptDefault*<br/>
기본 점 값을 지정 합니다.

### <a name="remarks"></a>설명

애니메이션 개체에 기본값을 설정 하려면이 함수를 사용 합니다. 이 메서드는 애니메이션 지점의 X 및 Y 좌표에 기본값을 할당 합니다. 또한 생성 된 기본 COM 개체를 다시 만듭니다. 이 애니메이션 개체를 이벤트 (ValueChanged 또는 IntegerValueChanged)에 구독 한 경우 이러한 이벤트를 다시 사용 하도록 설정 해야 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
