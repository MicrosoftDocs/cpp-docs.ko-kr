---
description: '자세한 정보: CAnimationSize 클래스'
title: CAnimationSize 클래스
ms.date: 11/04/2016
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
helpviewer_keywords:
- CAnimationSize [MFC], CAnimationSize
- CAnimationSize [MFC], AddTransition
- CAnimationSize [MFC], GetCX
- CAnimationSize [MFC], GetCY
- CAnimationSize [MFC], GetDefaultValue
- CAnimationSize [MFC], GetValue
- CAnimationSize [MFC], SetDefaultValue
- CAnimationSize [MFC], GetAnimationVariableList
- CAnimationSize [MFC], m_cxValue
- CAnimationSize [MFC], m_cyValue
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
ms.openlocfilehash: 894675c485077291c3fca35acfb9bfa9a3d10286
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336777"
---
# <a name="canimationsize-class"></a>CAnimationSize 클래스

차원에 애니메이션을 적용할 수 있는 크기 개체 기능을 구현합니다.

## <a name="syntax"></a>구문

```
class CAnimationSize : public CAnimationBaseObject;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAnimationSize:: CAnimationSize](#canimationsize)|오버로드됨. 애니메이션 크기 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAnimationSize:: AddTransition](#addtransition)|너비 및 높이에 대 한 전환을 추가 합니다.|
|[CAnimationSize:: GetCX](#getcx)|너비를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.|
|[CAnimationSize:: GetCY](#getcy)|높이를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.|
|[CAnimationSize:: GetDefaultValue](#getdefaultvalue)|너비와 높이의 기본값을 반환 합니다.|
|[CAnimationSize:: GetValue](#getvalue)|현재 값을 반환 합니다.|
|[CAnimationSize:: SetDefaultValue](#setdefaultvalue)|기본값을 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CAnimationSize:: GetAnimationVariableList](#getanimationvariablelist)|캡슐화 된 애니메이션 변수를 목록에 넣습니다. ( [Canimationbaseobject:: GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)를 재정의 합니다.)|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAnimationSize:: operator CSize](#operator_csize)|CAnimationSize를 CSize로 변환 합니다.|
|[CAnimationSize:: operator =](#operator_eq)|SzSrc를 CAnimationSize에 할당 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAnimationSize:: m_cxValue](#m_cxvalue)|애니메이션 크기의 너비를 나타내는 캡슐화 된 애니메이션 변수입니다.|
|[CAnimationSize:: m_cyValue](#m_cyvalue)|애니메이션 크기의 높이를 나타내는 캡슐화 된 애니메이션 변수입니다.|

## <a name="remarks"></a>설명

CAnimationSize 클래스는 두 개의 Canimationsize 개체를 캡슐화 하며 응용 프로그램 크기를 나타낼 수 있습니다. 예를 들어이 클래스를 사용 하 여 화면에서 2 차원 개체의 크기에 애니메이션 효과를 적용할 수 있습니다 (예: 사각형, 컨트롤 등). 응용 프로그램에서이 클래스를 사용 하려면이 클래스의 개체를 인스턴스화하고 CAnimationController:: Addanimation 개체를 사용 하 여 애니메이션 컨트롤러에 추가 하 고 각 전환에 대해 Width 및/또는 Height에 적용 하는 AddTransition을 호출 하기만 하면 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="canimationsizeaddtransition"></a><a name="addtransition"></a> CAnimationSize:: AddTransition

너비 및 높이에 대 한 전환을 추가 합니다.

```cpp
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>매개 변수

*pCXTransition*<br/>
너비 전환에 대 한 포인터입니다.

*pCYTransition*<br/>
높이 전환에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 함수를 호출 하 여 지정 된 전환을 너비 및 높이에 대 한 애니메이션 변수에 적용할 내부 전환 목록에 추가 합니다. 전환을 추가 하면 즉시 적용 되지 않고 내부 목록에 저장 됩니다. CAnimationController:: AnimateGroup를 호출 하면 전환이 적용 됩니다 (특정 값에 대 한 스토리 보드에 추가 됨). 차원 중 하나에 전환을 적용할 필요가 없으면 NULL을 전달할 수 있습니다.

## <a name="canimationsizecanimationsize"></a><a name="canimationsize"></a> CAnimationSize:: CAnimationSize

애니메이션 크기 개체를 생성 합니다.

```
CAnimationSize();

CAnimationSize(
    const CSize& szDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>매개 변수

*szDefault*<br/>
기본 크기를 지정 합니다.

*nGroupID*<br/>
그룹 ID를 지정 합니다.

*nObjectID*<br/>
개체 ID를 지정 합니다.

*dwUserData*<br/>
사용자 정의 데이터를 지정 합니다.

### <a name="remarks"></a>설명

개체는 너비, 높이, 개체 ID 및 그룹 ID에 대 한 기본값을 사용 하 여 생성 됩니다 .이 값은 0으로 설정 됩니다. SetDefaultValue 및 SetID를 사용 하 여 나중에 런타임에 변경할 수 있습니다.

## <a name="canimationsizegetanimationvariablelist"></a><a name="getanimationvariablelist"></a> CAnimationSize:: GetAnimationVariableList

캡슐화 된 애니메이션 변수를 목록에 넣습니다.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>매개 변수

*.lst*<br/>
함수는 반환 될 때 너비와 높이를 나타내는 두 개의 CAnimationVariable 개체에 대 한 포인터를 포함 합니다.

## <a name="canimationsizegetcx"></a><a name="getcx"></a> CAnimationSize:: GetCX

너비를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>반환 값

너비를 나타내는 캡슐화 된 CAnimationVariable에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 너비를 나타내는 기본 CAnimationVariable에 직접 액세스할 수 있습니다.

## <a name="canimationsizegetcy"></a><a name="getcy"></a> CAnimationSize:: GetCY

높이를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>반환 값

높이를 나타내는 캡슐화 된 CAnimationVariable에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 높이를 나타내는 기본 CAnimationVariable에 직접 액세스할 수 있습니다.

## <a name="canimationsizegetdefaultvalue"></a><a name="getdefaultvalue"></a> CAnimationSize:: GetDefaultValue

너비와 높이의 기본값을 반환 합니다.

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>반환 값

기본값을 포함 하는 CSize 개체입니다.

### <a name="remarks"></a>설명

이전에 생성자 또는 SetDefaultValue에 의해 설정 된 기본값을 검색 하려면이 함수를 호출 합니다.

## <a name="canimationsizegetvalue"></a><a name="getvalue"></a> CAnimationSize:: GetValue

현재 값을 반환 합니다.

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>매개 변수

*szValue*<br/>
출력 이 메서드가 반환 하는 현재 값을 포함 합니다.

### <a name="return-value"></a>반환 값

현재 값이 성공적으로 검색 되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

애니메이션 크기의 현재 값을 검색 하려면이 함수를 호출 합니다. 이 메서드가 실패 하거나 너비와 크기에 대 한 기본 COM 개체가 초기화 되지 않은 경우, szValue는 이전에 생성자 또는 SetDefaultValue에서 설정 된 기본값을 포함 합니다.

## <a name="canimationsizem_cxvalue"></a><a name="m_cxvalue"></a> CAnimationSize:: m_cxValue

애니메이션 크기의 너비를 나타내는 캡슐화 된 애니메이션 변수입니다.

```
CAnimationVariable m_cxValue;
```

## <a name="canimationsizem_cyvalue"></a><a name="m_cyvalue"></a> CAnimationSize:: m_cyValue

애니메이션 크기의 높이를 나타내는 캡슐화 된 애니메이션 변수입니다.

```
CAnimationVariable m_cyValue;
```

## <a name="canimationsizeoperator-csize"></a><a name="operator_csize"></a> CAnimationSize:: operator CSize

CAnimationSize를 CSize로 변환 합니다.

```
operator CSize();
```

### <a name="return-value"></a>반환 값

애니메이션 크기의 현재 값 (CSize)입니다.

### <a name="remarks"></a>설명

이 함수는 내부적으로 GetValue를 호출 합니다. 특정 이유에 대해 GetValue가 실패 한 경우 반환 되는 크기는 너비 및 높이에 대 한 기본값을 포함 합니다.

## <a name="canimationsizeoperator"></a><a name="operator_eq"></a> CAnimationSize:: operator =

SzSrc를 CAnimationSize에 할당 합니다.

```cpp
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>매개 변수

*szSrc*<br/>
는 CSize 또는 SIZE를 나타냅니다.

### <a name="remarks"></a>설명

SzSrc를 CAnimationSize에 할당 합니다. 애니메이션을 시작 하기 전에이 연산자를 사용 하는 것이 좋습니다 .이 연산자는 생성 된 경우 너비 및 높이에 대 한 기본 COM 개체를 다시 생성 하는 SetDefaultValue를 호출 합니다. 이 애니메이션 개체를 이벤트 (ValueChanged 또는 IntegerValueChanged)에 구독 한 경우 이러한 이벤트를 다시 사용 하도록 설정 해야 합니다.

## <a name="canimationsizesetdefaultvalue"></a><a name="setdefaultvalue"></a> CAnimationSize:: SetDefaultValue

기본값을 설정 합니다.

```cpp
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>매개 변수

*szDefault*<br/>
새 기본 크기를 지정 합니다.

### <a name="remarks"></a>설명

애니메이션 개체에 기본값을 설정 하려면이 함수를 사용 합니다. 이 메서드는 애니메이션 크기의 너비와 높이에 기본값을 할당 합니다. 또한 생성 된 기본 COM 개체를 다시 만듭니다. 이 애니메이션 개체를 이벤트 (ValueChanged 또는 IntegerValueChanged)에 구독 한 경우 이러한 이벤트를 다시 사용 하도록 설정 해야 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
