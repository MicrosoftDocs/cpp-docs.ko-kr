---
description: '자세한 정보: CAnimationBaseObject 클래스'
title: CAnimationBaseObject 클래스
ms.date: 03/27/2019
f1_keywords:
- CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ContainsVariable
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::DetachFromController
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetParentAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_dwUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_pParentController
helpviewer_keywords:
- CAnimationBaseObject [MFC], CAnimationBaseObject
- CAnimationBaseObject [MFC], ApplyTransitions
- CAnimationBaseObject [MFC], ClearTransitions
- CAnimationBaseObject [MFC], ContainsVariable
- CAnimationBaseObject [MFC], CreateTransitions
- CAnimationBaseObject [MFC], DetachFromController
- CAnimationBaseObject [MFC], EnableIntegerValueChangedEvent
- CAnimationBaseObject [MFC], EnableValueChangedEvent
- CAnimationBaseObject [MFC], GetAutodestroyTransitions
- CAnimationBaseObject [MFC], GetGroupID
- CAnimationBaseObject [MFC], GetObjectID
- CAnimationBaseObject [MFC], GetUserData
- CAnimationBaseObject [MFC], SetAutodestroyTransitions
- CAnimationBaseObject [MFC], SetID
- CAnimationBaseObject [MFC], SetUserData
- CAnimationBaseObject [MFC], GetAnimationVariableList
- CAnimationBaseObject [MFC], SetParentAnimationObjects
- CAnimationBaseObject [MFC], m_bAutodestroyTransitions
- CAnimationBaseObject [MFC], m_dwUserData
- CAnimationBaseObject [MFC], m_nGroupID
- CAnimationBaseObject [MFC], m_nObjectID
- CAnimationBaseObject [MFC], m_pParentController
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
ms.openlocfilehash: bc44d0e55b409f66648007eeb27fefd386640d9f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318665"
---
# <a name="canimationbaseobject-class"></a>CAnimationBaseObject 클래스

모든 애니메이션 개체의 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class CAnimationBaseObject : public CObject;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAnimationBaseObject:: CAnimationBaseObject](#canimationbaseobject)|오버로드됨. 애니메이션 개체를 생성 합니다.|
|[CAnimationBaseObject:: ~ CAnimationBaseObject](#_dtorcanimationbaseobject)|소멸자입니다. 애니메이션 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAnimationBaseObject:: ApplyTransitions](#applytransitions)|캡슐화 된 애니메이션 변수가 있는 storyboard에 전환을 추가 합니다.|
|[CAnimationBaseObject:: ClearTransitions](#cleartransitions)|모든 관련 전환을 제거 합니다.|
|[CAnimationBaseObject:: ContainsVariable](#containsvariable)|애니메이션 개체에 특정 애니메이션 변수가 포함 되어 있는지 여부를 확인 합니다.|
|[CAnimationBaseObject:: CreateTransitions](#createtransitions)|애니메이션 개체와 연결 된 전환을 만듭니다.|
|[CAnimationBaseObject::D etachFromController](#detachfromcontroller)|부모 애니메이션 컨트롤러에서 애니메이션 개체를 분리 합니다.|
|[CAnimationBaseObject:: EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|정수 값 변경 이벤트 처리기를 설정 합니다.|
|[CAnimationBaseObject:: EnableValueChangedEvent](#enablevaluechangedevent)|값 변경 이벤트 처리기를 설정 합니다.|
|[CAnimationBaseObject:: GetAutodestroyTransitions](#getautodestroytransitions)|관련 전환이 자동으로 제거 되는지 여부를 나타냅니다.|
|[CAnimationBaseObject:: GetGroupID](#getgroupid)|현재 그룹 ID를 반환 합니다.|
|[CAnimationBaseObject:: GetObjectID](#getobjectid)|현재 개체 ID를 반환 합니다.|
|[CAnimationBaseObject:: GetUserData](#getuserdata)|사용자 정의 데이터를 반환 합니다.|
|[CAnimationBaseObject:: SetAutodestroyTransitions](#setautodestroytransitions)|전환을 자동으로 삭제 하는 플래그를 설정 합니다.|
|[CAnimationBaseObject:: SetID](#setid)|새 Id를 설정 합니다.|
|[CAnimationBaseObject:: SetUserData](#setuserdata)|사용자 정의 데이터를 설정 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CAnimationBaseObject:: GetAnimationVariableList](#getanimationvariablelist)|포함 된 애니메이션 변수에 대 한 포인터를 수집 합니다.|
|[CAnimationBaseObject:: Setparent애니메이션 개체](#setparentanimationobjects)|애니메이션 개체에 포함 된 애니메이션 변수와 해당 컨테이너 간의 관계를 설정 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAnimationBaseObject:: m_bAutodestroyTransitions](#m_bautodestroytransitions)|관련 전환을 자동으로 제거할지 여부를 지정 합니다.|
|[CAnimationBaseObject:: m_dwUserData](#m_dwuserdata)|사용자 정의 데이터를 저장 합니다.|
|[CAnimationBaseObject:: m_nGroupID](#m_ngroupid)|애니메이션 개체의 그룹 ID를 지정 합니다.|
|[CAnimationBaseObject:: m_nObjectID](#m_nobjectid)|애니메이션 개체의 개체 ID를 지정 합니다.|
|[CAnimationBaseObject:: m_pParentController](#m_pparentcontroller)|부모 애니메이션 컨트롤러에 대 한 포인터입니다.|

## <a name="remarks"></a>설명

이 클래스는 모든 애니메이션 개체에 대 한 기본 메서드를 구현 합니다. 애니메이션 개체는 응용 프로그램의 값, 점, 크기, 사각형 또는 색 뿐만 아니라 사용자 지정 엔터티를 나타낼 수 있습니다. 애니메이션 개체는 애니메이션 그룹에 저장 됩니다 (CAnimationGroup 참조). 각 그룹은 개별적으로 애니메이션을 적용할 수 있으며, storyboard의 아날로그로 처리 될 수 있습니다. 애니메이션 개체는 논리적 표현에 따라 하나 이상의 애니메이션 변수 (CAnimationVariable 참조)를 캡슐화 합니다. 예를 들어 CAnimationRect는 사각형의 양쪽에 대해 하나의 변수를 포함 하는 4 개의 애니메이션 변수를 포함 합니다. 각 애니메이션 개체 클래스는 캡슐화 된 애니메이션 변수에 전환을 적용 하는 데 사용 해야 하는 오버 로드 된 AddTransition 메서드를 노출 합니다. 애니메이션 개체는 개체 ID (선택 사항) 및 그룹 ID로 식별할 수 있습니다. 애니메이션 개체를 올바른 그룹에 배치 하려면 그룹 ID가 필요 하지만 그룹 ID를 지정 하지 않으면 개체는 ID가 0 인 기본 그룹에 배치 됩니다. 다른 GroupID를 사용 하 여 SetID를 호출 하는 경우 애니메이션 개체는 다른 그룹으로 이동 됩니다 (필요한 경우 새 그룹이 만들어짐).

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="_dtorcanimationbaseobject"></a> CAnimationBaseObject:: ~ CAnimationBaseObject

소멸자입니다. 애니메이션 개체가 제거 될 때 호출 됩니다.

```
virtual ~CAnimationBaseObject();
```

## <a name="canimationbaseobjectapplytransitions"></a><a name="applytransitions"></a> CAnimationBaseObject:: ApplyTransitions

캡슐화 된 애니메이션 변수가 있는 storyboard에 전환을 추가 합니다.

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>매개 변수

*pStoryboard*<br/>
스토리 보드에 대 한 포인터입니다.

*bDependOnKeyframes*<br/>
FALSE 인 경우이 메서드는 키 프레임에 종속 되지 않은 전환만 추가 합니다.

### <a name="return-value"></a>반환 값

전환이 성공적으로 추가 되었으면 TRUE입니다.

### <a name="remarks"></a>설명

AddTransition (파생 클래스의 오버 로드 된 메서드)를 사용 하 여 추가 된 관련 전환을 storyboard에 추가 합니다.

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="canimationbaseobject"></a> CAnimationBaseObject:: CAnimationBaseObject

애니메이션 개체를 생성 합니다.

```
CAnimationBaseObject();

CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>매개 변수

*nGroupID*<br/>
그룹 ID를 지정 합니다.

*nObjectID*<br/>
개체 ID를 지정 합니다.

*dwUserData*<br/>
애니메이션 개체와 연결 하 여 나중에 런타임에 검색할 수 있는 사용자 정의 데이터입니다.

### <a name="remarks"></a>설명

애니메이션 개체를 생성 하 고 기본 개체 ID (0) 및 그룹 ID (0)를 할당 합니다.

## <a name="canimationbaseobjectcleartransitions"></a><a name="cleartransitions"></a> CAnimationBaseObject:: ClearTransitions

모든 관련 전환을 제거 합니다.

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>매개 변수

*bAutodestroy*<br/>
전환 개체를 자동으로 제거할지 또는 관련 목록에서 제거할지를 지정 합니다.

### <a name="remarks"></a>설명

모든 관련 전환을 제거 하 고 bAutodestroy 또는 m_bAutodestroyTransitions 플래그가 TRUE 이면 제거 합니다. 변환은 스택에 할당 되지 않은 경우에만 자동으로 삭제 됩니다. 위의 플래그가 FALSE 이면 전환은 관련 전환의 내부 목록에서 제거 됩니다.

## <a name="canimationbaseobjectcontainsvariable"></a><a name="containsvariable"></a> CAnimationBaseObject:: ContainsVariable

애니메이션 개체에 특정 애니메이션 변수가 포함 되어 있는지 여부를 확인 합니다.

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>매개 변수

*pVariable*<br/>
애니메이션 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

애니메이션 변수가 애니메이션 개체에 포함 되어 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 pVariable로 지정 된 애니메이션 변수가 애니메이션 개체에 포함 되어 있는지 여부를 확인 하는 데 사용할 수 있습니다. 애니메이션 개체에는 형식에 따라 여러 애니메이션 변수가 포함 될 수 있습니다. 예를 들어 CAnimationColor에는 각 색 구성 요소 (빨강, 녹색 및 파랑) 마다 하나씩 세 개의 변수가 포함 되어 있습니다. 애니메이션 변수 값이 변경 되 면 Windows 애니메이션 API가 ValueChanged 또는 IntegerValueChanged 이벤트 (사용 하도록 설정 된 경우)를 보내고이 이벤트의 매개 변수는 애니메이션 변수의 Iuianimation 변수 인터페이스에 대 한 포인터입니다. 이 메서드는 포함 된 COM 개체에 대 한 포인터에서 애니메이션에 대 한 포인터를 가져오는 데 도움이 됩니다.

## <a name="canimationbaseobjectcreatetransitions"></a><a name="createtransitions"></a> CAnimationBaseObject:: CreateTransitions

애니메이션 개체와 연결 된 전환을 만듭니다.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>반환 값

전환이 성공적으로 생성 되었으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

파생 애니메이션 개체에 캡슐화 된 애니메이션 변수 목록에 대해 루프를 실행 하 고 각 애니메이션 변수와 연결 된 전환을 만듭니다.

## <a name="canimationbaseobjectdetachfromcontroller"></a><a name="detachfromcontroller"></a> CAnimationBaseObject::D etachFromController

부모 애니메이션 컨트롤러에서 애니메이션 개체를 분리 합니다.

```cpp
void DetachFromController();
```

### <a name="remarks"></a>설명

이 메서드는 내부적으로 사용 됩니다.

## <a name="canimationbaseobjectenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a> CAnimationBaseObject:: EnableIntegerValueChangedEvent

정수 값 변경 이벤트 처리기를 설정 합니다.

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>매개 변수

*pController*<br/>
부모 컨트롤러에 대 한 포인터입니다.

*bEnable*<br/>
정수 값 변경 이벤트를 사용 하거나 사용 하지 않도록 설정할지 여부를 지정 합니다.

### <a name="remarks"></a>설명

정수 값 변경 이벤트 처리기를 사용 하도록 설정한 경우 canimationcontroller:: OnAnimationIntegerValueChanged 메서드에서이 이벤트를 처리할 수 있습니다 .이 이벤트는 CAnimationController 파생 클래스에서 재정의 해야 합니다. 이 메서드는 애니메이션 정수 값이 변경 될 때마다 호출 됩니다.

## <a name="canimationbaseobjectenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a> CAnimationBaseObject:: EnableValueChangedEvent

값 변경 이벤트 처리기를 설정 합니다.

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>매개 변수

*pController*<br/>
부모 컨트롤러에 대 한 포인터입니다.

*bEnable*<br/>
값 변경 이벤트를 사용 하거나 사용 하지 않도록 설정할지 여부를 지정 합니다.

### <a name="remarks"></a>설명

값 변경 이벤트 처리기를 사용 하도록 설정한 경우 canimationcontroller:: OnAnimationValueChanged 메서드에서이 이벤트를 처리할 수 있습니다 .이 이벤트는 CAnimationController 파생 클래스에서 재정의 해야 합니다. 이 메서드는 애니메이션 값이 변경 될 때마다 호출 됩니다.

## <a name="canimationbaseobjectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a> CAnimationBaseObject:: GetAnimationVariableList

포함 된 애니메이션 변수에 대 한 포인터를 수집 합니다.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& list) = 0;
```

### <a name="parameters"></a>매개 변수

*list*<br/>
애니메이션 개체에 포함 된 애니메이션 변수로 채워야 하는 목록입니다.

### <a name="remarks"></a>설명

이 순수 가상 메서드는 파생 클래스에서 재정의 해야 합니다. 애니메이션 개체의 형식에 따라 애니메이션 변수가 하나 이상 포함 되어 있습니다. 예를 들어 CAnimationPoint는 각각 X 및 Y 좌표의 두 변수를 포함 합니다. CAnimationBaseObject 기본 클래스는 애니메이션 변수 목록 (ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent)에 대해 작동 하는 몇 가지 제네릭 메서드를 구현 합니다. 이러한 메서드는 파생 클래스에서 특정 애니메이션 개체에 포함 된 실제 애니메이션 변수로 채운 GetAnimationVariableList를 호출 하 고, 목록에 대해 루프를 실행 하 고 필요한 작업을 수행 합니다. 사용자 지정 애니메이션 개체를 만드는 경우를 추가 하 여 해당 개체에 포함 된 모든 애니메이션 변수를 *나열* 해야 합니다.

## <a name="canimationbaseobjectgetautodestroytransitions"></a><a name="getautodestroytransitions"></a> CAnimationBaseObject:: GetAutodestroyTransitions

관련 전환이 자동으로 제거 되는지 여부를 나타냅니다.

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>반환 값

TRUE 이면 관련 전환이 자동으로 제거 됩니다. FALSE 이면 응용 프로그램을 호출 하 여 전환 개체의 할당을 취소 해야 합니다.

### <a name="remarks"></a>설명

기본적으로이 플래그는 TRUE입니다. 스택에 전환을 할당 하 고 호출 응용 프로그램에서 전환을 할당 취소 해야 하는 경우에만이 플래그를 설정 합니다.

## <a name="canimationbaseobjectgetgroupid"></a><a name="getgroupid"></a> CAnimationBaseObject:: GetGroupID

현재 그룹 ID를 반환 합니다.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>반환 값

현재 그룹 ID입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 그룹 ID를 검색 합니다. 그룹 ID가 생성자 또는 SetID로 명시적으로 설정 되지 않은 경우 0입니다.

## <a name="canimationbaseobjectgetobjectid"></a><a name="getobjectid"></a> CAnimationBaseObject:: GetObjectID

현재 개체 ID를 반환 합니다.

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>반환 값

현재 개체 ID입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 개체 ID를 검색 합니다. 생성자 또는 SetID를 사용 하 여 개체 ID를 명시적으로 설정 하지 않은 경우 0입니다.

## <a name="canimationbaseobjectgetuserdata"></a><a name="getuserdata"></a> CAnimationBaseObject:: GetUserData

사용자 정의 데이터를 반환 합니다.

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>반환 값

사용자 지정 데이터의 값입니다.

### <a name="remarks"></a>설명

런타임에 사용자 지정 데이터를 검색 하려면이 메서드를 호출 합니다. 생성자 또는 SetUserData를 사용 하 여 명시적으로 초기화 되지 않은 경우 반환 되는 값은 0이 됩니다.

## <a name="canimationbaseobjectm_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a> CAnimationBaseObject:: m_bAutodestroyTransitions

관련 전환을 자동으로 제거할지 여부를 지정 합니다.

```
BOOL m_bAutodestroyTransitions;
```

## <a name="canimationbaseobjectm_dwuserdata"></a><a name="m_dwuserdata"></a> CAnimationBaseObject:: m_dwUserData

사용자 정의 데이터를 저장 합니다.

```
DWORD m_dwUserData;
```

## <a name="canimationbaseobjectm_ngroupid"></a><a name="m_ngroupid"></a> CAnimationBaseObject:: m_nGroupID

애니메이션 개체의 그룹 ID를 지정 합니다.

```
UINT32 m_nGroupID;
```

## <a name="canimationbaseobjectm_nobjectid"></a><a name="m_nobjectid"></a> CAnimationBaseObject:: m_nObjectID

애니메이션 개체의 개체 ID를 지정 합니다.

```
UINT32 m_nObjectID;
```

## <a name="canimationbaseobjectm_pparentcontroller"></a><a name="m_pparentcontroller"></a> CAnimationBaseObject:: m_pParentController

부모 애니메이션 컨트롤러에 대 한 포인터입니다.

```
CAnimationController* m_pParentController;
```

## <a name="canimationbaseobjectsetautodestroytransitions"></a><a name="setautodestroytransitions"></a> CAnimationBaseObject:: SetAutodestroyTransitions

전환을 자동으로 삭제 하는 플래그를 설정 합니다.

```cpp
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>매개 변수

*되며 bvalue*<br/>
자동 소멸 플래그를 지정 합니다.

### <a name="remarks"></a>설명

Operator new를 사용 하 여 전환 개체를 할당 한 경우에만이 플래그를 설정 합니다. 일부 이유로 인해 전환 개체가 스택에 할당 되는 경우 자동 소멸 플래그는 FALSE가 됩니다. 기본적으로이 플래그는 TRUE입니다.

## <a name="canimationbaseobjectsetid"></a><a name="setid"></a> CAnimationBaseObject:: SetID

새 Id를 설정 합니다.

```cpp
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>매개 변수

*nObjectID*<br/>
새 개체 ID를 지정 합니다.

*nGroupID*<br/>
새 그룹 ID를 지정 합니다.

### <a name="remarks"></a>설명

개체 ID 및 그룹 ID를 변경할 수 있습니다. 새 그룹 ID가 현재 ID와 다른 경우 애니메이션 개체는 다른 그룹으로 이동 됩니다. 필요한 경우 새 그룹이 생성 됩니다.

## <a name="canimationbaseobjectsetparentanimationobjects"></a><a name="setparentanimationobjects"></a> CAnimationBaseObject:: Setparent애니메이션 개체

애니메이션 개체에 포함 된 애니메이션 변수와 해당 컨테이너 간의 관계를 설정 합니다.

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>설명

이 도우미는 애니메이션 개체에 포함 된 애니메이션 변수와 해당 컨테이너 간의 관계를 설정 하는 데 사용할 수 있습니다. 애니메이션 변수를 반복 하 고 부모 애니메이션 개체에 대 한 백 포인터를 각 애니메이션 변수로 설정 합니다. 현재 구현에서 실제 관계는 CAnimationBaseObject:: ApplyTransitions 통해 설정 되므로 CAnimationGroup:: Animate를 호출할 때까지 후방 포인터가 설정 되지 않습니다. 관계를 알면 이벤트를 처리 하 고 CAnimationVariable에서 부모 애니메이션 개체를 가져와야 하는 경우에 유용할 수 있습니다. CAnimationVariable:: GetParentAnimationObject를 사용 합니다.

## <a name="canimationbaseobjectsetuserdata"></a><a name="setuserdata"></a> CAnimationBaseObject:: SetUserData

사용자 정의 데이터를 설정 합니다.

```cpp
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>매개 변수

*dwUserData*<br/>
사용자 지정 데이터를 지정 합니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 사용자 지정 데이터를 애니메이션 개체와 연결 합니다. 이 데이터는 나중에 GetUserData에서 검색할 수 있습니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
