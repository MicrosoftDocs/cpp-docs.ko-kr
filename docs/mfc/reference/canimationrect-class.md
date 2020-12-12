---
description: '자세한 정보: CAnimationRect 클래스'
title: CAnimationRect 클래스
ms.date: 11/04/2016
f1_keywords:
- CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationRect::GetBottom
- AFXANIMATIONCONTROLLER/CAnimationRect::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetLeft
- AFXANIMATIONCONTROLLER/CAnimationRect::GetRight
- AFXANIMATIONCONTROLLER/CAnimationRect::GetTop
- AFXANIMATIONCONTROLLER/CAnimationRect::GetValue
- AFXANIMATIONCONTROLLER/CAnimationRect::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bFixedSize
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bottomValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_leftValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_rightValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_szInitial
- AFXANIMATIONCONTROLLER/CAnimationRect::m_topValue
helpviewer_keywords:
- CAnimationRect [MFC], CAnimationRect
- CAnimationRect [MFC], AddTransition
- CAnimationRect [MFC], GetBottom
- CAnimationRect [MFC], GetDefaultValue
- CAnimationRect [MFC], GetLeft
- CAnimationRect [MFC], GetRight
- CAnimationRect [MFC], GetTop
- CAnimationRect [MFC], GetValue
- CAnimationRect [MFC], SetDefaultValue
- CAnimationRect [MFC], GetAnimationVariableList
- CAnimationRect [MFC], m_bFixedSize
- CAnimationRect [MFC], m_bottomValue
- CAnimationRect [MFC], m_leftValue
- CAnimationRect [MFC], m_rightValue
- CAnimationRect [MFC], m_szInitial
- CAnimationRect [MFC], m_topValue
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
ms.openlocfilehash: 590b1382992a32e0eb3d49e0ea562d10193c1990
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207893"
---
# <a name="canimationrect-class"></a>CAnimationRect 클래스

면에 애니메이션을 적용할 수 있는 사각형 기능을 구현합니다.

## <a name="syntax"></a>구문

```
class CAnimationRect : public CAnimationBaseObject;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAnimationRect:: CAnimationRect](#canimationrect)|오버로드됨. 애니메이션 rect 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAnimationRect:: AddTransition](#addtransition)|왼쪽, 위쪽, 오른쪽 및 아래쪽 좌표에 대 한 전환을 추가 합니다.|
|[CAnimationRect:: GetBottom](#getbottom)|최하위 좌표를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.|
|[CAnimationRect:: GetDefaultValue](#getdefaultvalue)|사각형의 범위에 대 한 기본값을 반환 합니다.|
|[CAnimationRect:: GetLeft](#getleft)|왼쪽 좌표를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.|
|[CAnimationRect:: GetRight](#getright)|오른쪽 좌표를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.|
|[CAnimationRect:: GetTop](#gettop)|위쪽 좌표를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.|
|[CAnimationRect:: GetValue](#getvalue)|현재 값을 반환 합니다.|
|[CAnimationRect:: SetDefaultValue](#setdefaultvalue)|기본값을 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CAnimationRect:: GetAnimationVariableList](#getanimationvariablelist)|캡슐화 된 애니메이션 변수를 목록에 넣습니다. ( [Canimationbaseobject:: GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)를 재정의 합니다.)|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAnimationRect:: operator RECT](#operator_rect)|CAnimationRect를 RECT로 변환 합니다.|
|[CAnimationRect:: operator =](#operator_eq)|Rect를 CAnimationRect에 할당 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAnimationRect:: m_bFixedSize](#m_bfixedsize)|사각형의 크기가 고정 되어 있는지 여부를 지정 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAnimationRect:: m_bottomValue](#m_bottomvalue)|애니메이션 사각형의 아래쪽 경계를 나타내는 캡슐화 된 애니메이션 변수입니다.|
|[CAnimationRect:: m_leftValue](#m_leftvalue)|애니메이션 사각형의 왼쪽 바인딩을 나타내는 캡슐화 된 애니메이션 변수입니다.|
|[CAnimationRect:: m_rightValue](#m_rightvalue)|애니메이션 사각형의 오른쪽 경계를 나타내는 캡슐화 된 애니메이션 변수입니다.|
|[CAnimationRect:: m_szInitial](#m_szinitial)|애니메이션 사각형의 초기 크기를 지정 합니다.|
|[CAnimationRect:: m_topValue](#m_topvalue)|애니메이션 사각형의 상한을 나타내는 캡슐화 된 애니메이션 변수입니다.|

## <a name="remarks"></a>설명

CAnimationRect 클래스는 네 개의 Canimationrect 개체를 캡슐화 하 고 응용 프로그램에 사각형을 나타낼 수 있습니다. 응용 프로그램에서이 클래스를 사용 하려면이 클래스의 개체를 인스턴스화하고 CAnimationController:: Addanimation 개체를 사용 하 여 애니메이션 컨트롤러에 추가 하 고 각 전환이 왼쪽, 오른쪽 위 및 아래쪽 좌표에 적용 될 수 있도록 AddTransition을 호출 하기만 하면 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="canimationrectaddtransition"></a><a name="addtransition"></a> CAnimationRect:: AddTransition

왼쪽, 위쪽, 오른쪽 및 아래쪽 좌표에 대 한 전환을 추가 합니다.

```cpp
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>매개 변수

*pLeftTransition*<br/>
좌 변의 전환을 지정 합니다.

*pTopTransition*<br/>
위쪽 변의 전환을 지정 합니다.

*pRightTransition*<br/>
오른쪽의 전환을 지정 합니다.

*pBottomTransition*<br/>
아래쪽의 전환을 지정 합니다.

### <a name="remarks"></a>설명

지정 된 전환을 각 사각형 변의 애니메이션 변수에 적용 되는 내부 전환 목록에 추가 하려면이 함수를 호출 합니다. 전환을 추가 하면 즉시 적용 되지 않고 내부 목록에 저장 됩니다. CAnimationController:: AnimateGroup를 호출 하면 전환이 적용 됩니다 (특정 값에 대 한 스토리 보드에 추가 됨). 사각형 측면 중 하나에 전환을 적용할 필요가 없으면 NULL을 전달할 수 있습니다.

## <a name="canimationrectcanimationrect"></a><a name="canimationrect"></a> CAnimationRect:: CAnimationRect

CAnimationRect 개체를 생성 합니다.

```
CAnimationRect();

CAnimationRect(
    const CRect& rect,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    const CPoint& pt,
    const CSize& sz,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    int nLeft,
    int nTop,
    int nRight,
    int nBottom,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
기본 사각형을 지정 합니다.

*nGroupID*<br/>
그룹 ID를 지정 합니다.

*nObjectID*<br/>
개체 ID를 지정 합니다.

*dwUserData*<br/>
사용자 정의 데이터를 지정 합니다.

*pt*<br/>
왼쪽 위 모퉁이의 좌표입니다.

*sz*<br/>
사각형의 크기입니다.

*nLeft*<br/>
왼쪽 범위의 좌표를 지정 합니다.

*nTop*<br/>
상한의 좌표를 지정 합니다.

*nRight*<br/>
오른쪽 경계의 좌표를 지정 합니다.

*n 하단*<br/>
상한의 좌표를 지정 합니다.

### <a name="remarks"></a>설명

개체는 왼쪽, 위쪽, 오른쪽 및 아래쪽, 개체 ID 및 그룹 ID (0으로 설정 됨)에 대 한 기본값을 사용 하 여 생성 됩니다. SetDefaultValue 및 SetID를 사용 하 여 나중에 런타임에 변경할 수 있습니다.

## <a name="canimationrectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a> CAnimationRect:: GetAnimationVariableList

캡슐화 된 애니메이션 변수를 목록에 넣습니다.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>매개 변수

*.lst*<br/>
함수는를 반환 하는 경우 사각형의 좌표를 나타내는 네 개의 CAnimationVariable 개체에 대 한 포인터를 포함 합니다.

## <a name="canimationrectgetbottom"></a><a name="getbottom"></a> CAnimationRect:: GetBottom

최하위 좌표를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>반환 값

아래쪽 좌표를 나타내는 캡슐화 된 CAnimationVariable에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 아래쪽 좌표를 나타내는 기본 CAnimationVariable에 직접 액세스할 수 있습니다.

## <a name="canimationrectgetdefaultvalue"></a><a name="getdefaultvalue"></a> CAnimationRect:: GetDefaultValue

사각형의 범위에 대 한 기본값을 반환 합니다.

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>반환 값

왼쪽, 오른쪽, 위쪽 및 아래쪽의 기본값을 포함 하는 CRect 값입니다.

### <a name="remarks"></a>설명

이전에 생성자 또는 SetDefaultValue에 의해 설정 된 기본값을 검색 하려면이 함수를 호출 합니다.

## <a name="canimationrectgetleft"></a><a name="getleft"></a> CAnimationRect:: GetLeft

왼쪽 좌표를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>반환 값

왼쪽 좌표를 나타내는 캡슐화 된 CAnimationVariable에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 왼쪽 좌표를 나타내는 기본 CAnimationVariable에 직접 액세스할 수 있습니다.

## <a name="canimationrectgetright"></a><a name="getright"></a> CAnimationRect:: GetRight

오른쪽 좌표를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>반환 값

오른쪽 좌표를 나타내는 캡슐화 된 CAnimationVariable에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 오른쪽 좌표를 나타내는 기본 CAnimationVariable에 직접 액세스할 수 있습니다.

## <a name="canimationrectgettop"></a><a name="gettop"></a> CAnimationRect:: GetTop

위쪽 좌표를 나타내는 CAnimationVariable에 대 한 액세스를 제공 합니다.

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>반환 값

위쪽 좌표를 나타내는 캡슐화 된 CAnimationVariable에 대 한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 최상위 좌표를 나타내는 기본 CAnimationVariable에 직접 액세스할 수 있습니다.

## <a name="canimationrectgetvalue"></a><a name="getvalue"></a> CAnimationRect:: GetValue

현재 값을 반환 합니다.

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
출력 이 메서드가 반환 하는 현재 값을 포함 합니다.

### <a name="return-value"></a>반환 값

현재 값이 성공적으로 검색 되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

애니메이션 사각형의 현재 값을 검색 하려면이 함수를 호출 합니다. 이 메서드가 실패 하거나 왼쪽, 위쪽, 오른쪽 및 아래쪽의 기본 COM 개체가 초기화 되지 않은 경우에는 이전에 생성자 또는 SetDefaultValue로 설정 된 기본값을 rect에 포함 합니다.

## <a name="canimationrectm_bfixedsize"></a><a name="m_bfixedsize"></a> CAnimationRect:: m_bFixedSize

사각형의 크기가 고정 되어 있는지 여부를 지정 합니다.

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>설명

이 멤버가 true 이면 사각형 크기가 고정 되 고 왼쪽 위 모퉁이가 고정 크기에 따라 이동 될 때마다 오른쪽 및 아래쪽 값이 다시 계산 됩니다. 사각형을 화면 주위로 쉽게 이동 하려면이 값을 TRUE로 설정 합니다. 이 경우 오른쪽 및 아래쪽 좌표에 적용 되는 전환은 무시 됩니다. 크기는 개체를 생성 하거나 SetDefaultValue를 호출할 때 내부적으로 저장 됩니다. 기본적으로이 멤버는 FALSE로 설정 됩니다.

## <a name="canimationrectm_bottomvalue"></a><a name="m_bottomvalue"></a> CAnimationRect:: m_bottomValue

애니메이션 사각형의 아래쪽 경계를 나타내는 캡슐화 된 애니메이션 변수입니다.

```
CAnimationVariable m_bottomValue;
```

## <a name="canimationrectm_leftvalue"></a><a name="m_leftvalue"></a> CAnimationRect:: m_leftValue

애니메이션 사각형의 왼쪽 바인딩을 나타내는 캡슐화 된 애니메이션 변수입니다.

```
CAnimationVariable m_leftValue;
```

## <a name="canimationrectm_rightvalue"></a><a name="m_rightvalue"></a> CAnimationRect:: m_rightValue

애니메이션 사각형의 오른쪽 경계를 나타내는 캡슐화 된 애니메이션 변수입니다.

```
CAnimationVariable m_rightValue;
```

## <a name="canimationrectm_szinitial"></a><a name="m_szinitial"></a> CAnimationRect:: m_szInitial

애니메이션 사각형의 초기 크기를 지정 합니다.

```
CSize m_szInitial;
```

## <a name="canimationrectm_topvalue"></a><a name="m_topvalue"></a> CAnimationRect:: m_topValue

애니메이션 사각형의 상한을 나타내는 캡슐화 된 애니메이션 변수입니다.

```
CAnimationVariable m_topValue;
```

## <a name="canimationrectoperator-rect"></a><a name="operator_rect"></a> CAnimationRect:: operator RECT

CAnimationRect를 RECT로 변환 합니다.

```
operator RECT();
```

### <a name="return-value"></a>반환 값

애니메이션 사각형의 현재 값 (RECT)입니다.

### <a name="remarks"></a>설명

이 함수는 내부적으로 GetValue를 호출 합니다. 특정 이유에 대해 GetValue가 실패 한 경우 반환 된 RECT는 모든 사각형 좌표의 기본값을 포함 합니다.

## <a name="canimationrectoperator"></a><a name="operator_eq"></a> CAnimationRect:: operator =

Rect를 CAnimationRect에 할당 합니다.

```cpp
void operator=(const RECT& rect);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
애니메이션 사각형의 새 값입니다.

### <a name="remarks"></a>설명

이 연산자는 색 구성 요소가 생성 된 경우 기본 COM 개체를 다시 생성 하는 SetDefaultValue를 호출 하기 때문에 애니메이션을 시작 하기 전에이 작업을 수행 하는 것이 좋습니다. 이 애니메이션 개체를 이벤트 (ValueChanged 또는 IntegerValueChanged)에 구독 한 경우 이러한 이벤트를 다시 사용 하도록 설정 해야 합니다.

## <a name="canimationrectsetdefaultvalue"></a><a name="setdefaultvalue"></a> CAnimationRect:: SetDefaultValue

기본값을 설정 합니다.

```cpp
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>매개 변수

*rect*<br/>
왼쪽, 위쪽, 오른쪽 및 아래쪽의 새 기본값을 지정 합니다.

### <a name="remarks"></a>설명

애니메이션 개체에 기본값을 설정 하려면이 함수를 사용 합니다. 이 메서드는 사각형의 범위에 기본값을 할당 합니다. 또한 생성 된 기본 COM 개체를 다시 만듭니다. 이 애니메이션 개체를 이벤트 (ValueChanged 또는 IntegerValueChanged)에 구독 한 경우 이러한 이벤트를 다시 사용 하도록 설정 해야 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
