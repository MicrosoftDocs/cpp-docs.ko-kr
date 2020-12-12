---
description: '자세한 정보: CAnimationColor 클래스'
title: CAnimationColor 클래스
ms.date: 11/04/2016
f1_keywords:
- CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationColor::GetB
- AFXANIMATIONCONTROLLER/CAnimationColor::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetG
- AFXANIMATIONCONTROLLER/CAnimationColor::GetR
- AFXANIMATIONCONTROLLER/CAnimationColor::GetValue
- AFXANIMATIONCONTROLLER/CAnimationColor::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationColor::m_bValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_gValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_rValue
helpviewer_keywords:
- CAnimationColor [MFC], CAnimationColor
- CAnimationColor [MFC], AddTransition
- CAnimationColor [MFC], GetB
- CAnimationColor [MFC], GetDefaultValue
- CAnimationColor [MFC], GetG
- CAnimationColor [MFC], GetR
- CAnimationColor [MFC], GetValue
- CAnimationColor [MFC], SetDefaultValue
- CAnimationColor [MFC], GetAnimationVariableList
- CAnimationColor [MFC], m_bValue
- CAnimationColor [MFC], m_gValue
- CAnimationColor [MFC], m_rValue
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
ms.openlocfilehash: 430f017bc9d60eed5e2d42b71f0303546deecaca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318639"
---
# <a name="canimationcolor-class"></a>CAnimationColor 클래스

빨강, 녹색 및 파랑 구성 요소에 애니메이션을 적용할 수 있는 색 기능을 구현합니다.

## <a name="syntax"></a>구문

```
class CAnimationColor : public CAnimationBaseObject;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAnimationColor:: CAnimationColor](#canimationcolor)|오버로드됨. 애니메이션 색 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAnimationColor:: AddTransition](#addtransition)|빨강, 녹색 및 파랑 구성 요소에 대 한 전환을 추가 합니다.|
|[CAnimationColor:: GetB](#getb)|Blue 구성 요소를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.|
|[CAnimationColor:: GetDefaultValue](#getdefaultvalue)|색 구성 요소의 기본값을 반환 합니다.|
|[CAnimationColor:: GetG](#getg)|녹색 구성 요소를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.|
|[CAnimationColor:: GetR](#getr)|Red 구성 요소를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.|
|[CAnimationColor:: GetValue](#getvalue)|현재 값을 반환 합니다.|
|[CAnimationColor:: SetDefaultValue](#setdefaultvalue)|기본값을 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CAnimationColor:: GetAnimationVariableList](#getanimationvariablelist)|캡슐화 된 애니메이션 변수를 목록에 넣습니다. ( [Canimationbaseobject:: GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)를 재정의 합니다.)|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAnimationColor:: operator COLORREF](#operator_colorref)||
|[CAnimationColor:: operator =](#operator_eq)|CAnimationColor에 색을 할당 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAnimationColor:: m_bValue](#m_bvalue)|애니메이션 색의 파랑 구성 요소를 나타내는 캡슐화 된 애니메이션 변수입니다.|
|[CAnimationColor:: m_gValue](#m_gvalue)|애니메이션 색의 녹색 구성 요소를 나타내는 캡슐화 된 애니메이션 변수입니다.|
|[CAnimationColor:: m_rValue](#m_rvalue)|애니메이션 색의 빨강 구성 요소를 나타내는 캡슐화 된 애니메이션 변수입니다.|

## <a name="remarks"></a>설명

CAnimationColor 클래스는 세 개의 Canimationcolor 개체를 캡슐화 하 고 응용 프로그램에 색을 나타낼 수 있습니다. 예를 들어이 클래스를 사용 하 여 텍스트 색, 배경색 등 화면에 있는 모든 개체의 색에 애니메이션 효과를 적용할 수 있습니다. 응용 프로그램에서이 클래스를 사용 하려면이 클래스의 개체를 인스턴스화한 후 CAnimationController:: Addanimation 개체를 사용 하 여 애니메이션 컨트롤러에 추가 하 고 빨강, 녹색 및 파랑 구성 요소에 적용 될 각 전환에 대해 AddTransition을 호출 하면 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="canimationcoloraddtransition"></a><a name="addtransition"></a> CAnimationColor:: AddTransition

빨강, 녹색 및 파랑 구성 요소에 대 한 전환을 추가 합니다.

```cpp
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>매개 변수

*pRTransition*<br/>
Red 구성 요소를 전환 합니다.

*pGTransition*<br/>
녹색 구성 요소를 전환 합니다.

*Ptransition*<br/>
Blue 구성 요소를 전환 합니다.

### <a name="remarks"></a>설명

지정 된 전환을 색 구성 요소를 나타내는 애니메이션 변수에 적용할 내부 전환 목록에 추가 하려면이 함수를 호출 합니다. 전환을 추가 하면 즉시 적용 되지 않고 내부 목록에 저장 됩니다. CAnimationController:: AnimateGroup를 호출 하면 전환이 적용 됩니다 (특정 값에 대 한 스토리 보드에 추가 됨). 색 구성 요소 중 하나에 전환을 적용할 필요가 없으면 NULL을 전달할 수 있습니다.

## <a name="canimationcolorcanimationcolor"></a><a name="canimationcolor"></a> CAnimationColor:: CAnimationColor

CAnimationColor 개체를 생성 합니다.

```
CAnimationColor();

CAnimationColor(
    COLORREF color,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
기본 색을 지정 합니다.

*nGroupID*<br/>
그룹 ID를 지정 합니다.

*nObjectID*<br/>
개체 ID를 지정 합니다.

*dwUserData*<br/>
사용자 정의 데이터를 지정 합니다.

### <a name="remarks"></a>설명

개체는 빨강, 녹색, 파랑, 개체 ID 및 그룹 ID에 대 한 기본값을 사용 하 여 생성 됩니다 .이 값은 0으로 설정 됩니다. SetDefaultValue 및 SetID를 사용 하 여 나중에 런타임에 변경할 수 있습니다.

## <a name="canimationcolorgetanimationvariablelist"></a><a name="getanimationvariablelist"></a> CAnimationColor:: GetAnimationVariableList

캡슐화 된 애니메이션 변수를 목록에 넣습니다.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>매개 변수

*.lst*<br/>
함수는를 반환 하는 경우 빨간색, 녹색 및 파랑 구성 요소를 나타내는 세 개의 CAnimationVariable 개체에 대 한 포인터를 포함 합니다.

## <a name="canimationcolorgetb"></a><a name="getb"></a> CAnimationColor:: GetB

Blue 구성 요소를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>반환 값

파랑 구성 요소를 나타내는 캡슐화 된 CAnimationVariable에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 Blue 구성 요소를 나타내는 기본 CAnimationVariable에 직접 액세스할 수 있습니다.

## <a name="canimationcolorgetdefaultvalue"></a><a name="getdefaultvalue"></a> CAnimationColor:: GetDefaultValue

색 구성 요소의 기본값을 반환 합니다.

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>반환 값

RGB 구성 요소의 기본값을 포함 하는 COLORREF 값입니다.

### <a name="remarks"></a>설명

이전에 생성자 또는 SetDefaultValue에 의해 설정 된 기본값을 검색 하려면이 함수를 호출 합니다.

## <a name="canimationcolorgetg"></a><a name="getg"></a> CAnimationColor:: GetG

녹색 구성 요소를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>반환 값

녹색 구성 요소를 나타내는 캡슐화 된 CAnimationVariable에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 녹색 구성 요소를 나타내는 기본 CAnimationVariable에 직접 액세스할 수 있습니다.

## <a name="canimationcolorgetr"></a><a name="getr"></a> CAnimationColor:: GetR

Red 구성 요소를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>반환 값

빨강 구성 요소를 나타내는 캡슐화 된 CAnimationVariable에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 빨강 구성 요소를 나타내는 기본 CAnimationVariable에 직접 액세스할 수 있습니다.

## <a name="canimationcolorgetvalue"></a><a name="getvalue"></a> CAnimationColor:: GetValue

현재 값을 반환 합니다.

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
출력 이 메서드가 반환 하는 현재 값을 포함 합니다.

### <a name="return-value"></a>반환 값

현재 값이 성공적으로 검색 되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

애니메이션 색의 현재 값을 검색 하려면이 함수를 호출 합니다. 이 메서드가 실패 하거나 색 구성 요소에 대 한 기본 COM 개체가 초기화 되지 않은 경우 색에는 이전에 생성자 또는 SetDefaultValue에서 설정한 기본값이 포함 됩니다.

## <a name="canimationcolorm_bvalue"></a><a name="m_bvalue"></a> CAnimationColor:: m_bValue

애니메이션 색의 파랑 구성 요소를 나타내는 캡슐화 된 애니메이션 변수입니다.

```
CAnimationVariable m_bValue;
```

## <a name="canimationcolorm_gvalue"></a><a name="m_gvalue"></a> CAnimationColor:: m_gValue

애니메이션 색의 녹색 구성 요소를 나타내는 캡슐화 된 애니메이션 변수입니다.

```
CAnimationVariable m_gValue;
```

## <a name="canimationcolorm_rvalue"></a><a name="m_rvalue"></a> CAnimationColor:: m_rValue

애니메이션 색의 빨강 구성 요소를 나타내는 캡슐화 된 애니메이션 변수입니다.

```
CAnimationVariable m_rValue;
```

## <a name="canimationcoloroperator-colorref"></a><a name="operator_colorref"></a> CAnimationColor:: operator COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>반환 값

## <a name="canimationcoloroperator"></a><a name="operator_eq"></a> CAnimationColor:: operator =

CAnimationColor에 색을 할당 합니다.

```cpp
void operator=(COLORREF color);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
새 값 애니메이션 색을 지정 합니다.

### <a name="remarks"></a>설명

이 연산자는 색 구성 요소가 생성 된 경우 기본 COM 개체를 다시 생성 하는 SetDefaultValue를 호출 하기 때문에 애니메이션을 시작 하기 전에이 작업을 수행 하는 것이 좋습니다. 이 애니메이션 개체를 이벤트 (ValueChanged 또는 IntegerValueChanged)에 구독 한 경우 이러한 이벤트를 다시 사용 하도록 설정 해야 합니다.

## <a name="canimationcolorsetdefaultvalue"></a><a name="setdefaultvalue"></a> CAnimationColor:: SetDefaultValue

기본값을 설정 합니다.

```cpp
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
빨강, 녹색 및 파랑 구성 요소의 새 기본값을 지정 합니다.

### <a name="remarks"></a>설명

애니메이션 개체에 기본값을 설정 하려면이 함수를 사용 합니다. 이 메서드는 애니메이션 색의 색 구성 요소에 기본값을 할당 합니다. 또한 생성 된 기본 COM 개체를 다시 만듭니다. 이 애니메이션 개체를 이벤트 (ValueChanged 또는 IntegerValueChanged)에 구독 한 경우 이러한 이벤트를 다시 사용 하도록 설정 해야 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
