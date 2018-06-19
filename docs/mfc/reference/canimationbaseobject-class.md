---
title: CAnimationBaseObject 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db9f7a66b60d70231628ded5dc096bad702bf088
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355606"
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
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|오버로드됨. 애니메이션 개체를 생성 합니다.|  
|[CAnimationBaseObject:: ~ CAnimationBaseObject](#canimationbaseobject__~canimationbaseobject)|소멸자입니다. 애니메이션 개체가 소멸 될 때 호출 됩니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|전환을 캡슐화 된 애니메이션 변수로 스토리 보드에 추가 합니다.|  
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|모든 관련 된 전환을 제거합니다.|  
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|애니메이션 개체에 특정 한 애니메이션 변수가 포함 되어 있는지 여부를 결정 합니다.|  
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|애니메이션 개체와 관련 된 전환을 만듭니다.|  
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|부모 애니메이션 컨트롤러에서 애니메이션 개체를 분리합니다.|  
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|정수 값이 변경 이벤트 처리기를 설정합니다.|  
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|값이 변경 이벤트 처리기를 설정합니다.|  
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|관련 된 전환을 자동으로 소멸 되는지 여부를 알려 줍니다.|  
|[CAnimationBaseObject::GetGroupID](#getgroupid)|현재 그룹 ID를 반환 합니다.|  
|[CAnimationBaseObject::GetObjectID](#getobjectid)|현재 개체 ID를 반환 합니다.|  
|[CAnimationBaseObject::GetUserData](#getuserdata)|사용자 정의 데이터를 반환합니다.|  
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|주문 전환을 자동으로 삭제 하는 플래그를 설정 합니다.|  
|[CAnimationBaseObject::SetID](#setid)|새 Id를 설정합니다.|  
|[CAnimationBaseObject::SetUserData](#setuserdata)|사용자 정의 데이터를 설정 합니다.|  
  
### <a name="protected-methods"></a>Protected 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|포함 된 애니메이션 변수에 대 한 포인터를 수집합니다.|  
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|애니메이션 개체 및 해당 컨테이너에 포함 된 애니메이션 변수 간에 관계가 설정 됩니다.|  
  
### <a name="protected-data-members"></a>보호된 데이터 멤버  
  
|이름|설명|  
|----------|-----------------|  
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|관련 된 전환의 자동으로 제거 되어야 할지 여부를 지정 합니다.|  
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|사용자 정의 데이터를 저장 합니다.|  
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|애니메이션 개체의 그룹 ID를 지정합니다.|  
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|애니메이션 개체의 개체 ID를 지정 합니다.|  
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|부모 애니메이션 컨트롤러에 대 한 포인터입니다.|  
  
## <a name="remarks"></a>설명  
 이 클래스는 모든 애니메이션 개체에 대 한 기본 메서드를 구현합니다. 애니메이션 개체 값, 포인트, 크기, 사각형을 나타내는 하거나 모든 사용자 정의 엔터티를 비롯 하 여 응용 프로그램에 색 수 있습니다. 애니메이션 개체 애니메이션 그룹 (CAnimationGroup 참조)에 저장 됩니다. 각 그룹에는 개별적으로 애니메이션을 적용할 수 있으며 스토리 보드와 유사 하 게 처리할 수 있습니다. 애니메이션 개체 하나 이상의 애니메이션 변수 (CAnimationVariable 참조), 논리적 표현에 따라 캡슐화 합니다. 예를 들어 CAnimationRect 애니메이션 변수 4 개-사각형의 각 측면에 대해 하나의 변수를 포함합니다. 각 애니메이션 개체 클래스에는 전환을 캡슐화 된 애니메이션 변수를 적용 하는 데 사용 될 오버 로드 된 AddTransition 메서드를 노출 합니다. 애니메이션 개체 개체 ID로 (선택 사항) 식별할 수 있습니다 및 그룹 id입니다. 그룹 ID가 올바른 그룹에 애니메이션 개체를 배치 하는 데 필요 하지만 그룹 ID를 지정 하지 않으면 개체 ID가 0으로 기본 그룹에 배치 됩니다. 다른 GroupID로 SetID 호출 하는 경우 애니메이션 개체 (새 그룹이 필요한 경우에 생성은)는 다른 그룹으로 이동 됩니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAnimationBaseObject`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationbaseobject"></a>  CAnimationBaseObject:: ~ CAnimationBaseObject  
 소멸자입니다. 애니메이션 개체가 소멸 될 때 호출 됩니다.  
  
```  
virtual ~CAnimationBaseObject();
```  
  
##  <a name="applytransitions"></a>  CAnimationBaseObject::ApplyTransitions  
 전환을 캡슐화 된 애니메이션 변수로 스토리 보드에 추가 합니다.  
  
```  
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>매개 변수  
 `pStoryboard`  
 스토리 보드에 대 한 포인터입니다.  
  
 `bDependOnKeyframes`  
 FALSE 인이 메서드는 키 프레임에 의존 하지 않는 전환만 추가 합니다.  
  
### <a name="return-value"></a>반환 값  
 전환 성공적으로 추가 된 경우 TRUE입니다.  
  
### <a name="remarks"></a>설명  
 AddTransition (파생된 클래스에서 오버 로드 된 메서드), 스토리 보드에 추가 된 관련된 전환을 추가 합니다.  
  
##  <a name="canimationbaseobject"></a>  CAnimationBaseObject::CAnimationBaseObject  
 애니메이션 개체를 생성 합니다.  
  
```  
CAnimationBaseObject();

 
CAnimationBaseObject(
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>매개 변수  
 `nGroupID`  
 그룹 ID를 지정 합니다.  
  
 `nObjectID`  
 개체 ID를 지정 합니다.  
  
 `dwUserData`  
 사용자 정의 데이터를 애니메이션 개체에 연결 하 고 나중에 런타임에 검색할 수 있습니다.  
  
### <a name="remarks"></a>설명  
 애니메이션 개체를 생성 하 고 기본 개체 ID (0) 및 그룹 ID (0)을 할당 합니다.  
  
##  <a name="cleartransitions"></a>  CAnimationBaseObject::ClearTransitions  
 모든 관련 된 전환을 제거합니다.  
  
```  
virtual void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>매개 변수  
 `bAutodestroy`  
 변환 개체를 자동으로 제거 하거나 관련된 된 목록에서 제거 하기만 것인지 지정 합니다.  
  
### <a name="remarks"></a>설명  
 관련 된 모든 전환을 제거 하 고 bAutodestroy 또는 m_bAutodestroyTransitions 플래그가 TRUE 인 경우 삭제 합니다. 전환의 스택에 할당 되지 않으며 경우에 자동으로 삭제 해야 합니다. 위의 플래그가 FALSE 인 경우 전환만 관련 된 전환의 내부 목록에서 제거 됩니다.  
  
##  <a name="containsvariable"></a>  CAnimationBaseObject::ContainsVariable  
 애니메이션 개체에 특정 한 애니메이션 변수가 포함 되어 있는지 여부를 결정 합니다.  
  
```  
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>매개 변수  
 `pVariable`  
 애니메이션 변수에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 애니메이션 변수 애니메이션 개체;에 포함 되어 있으면 TRUE입니다. 그렇지 않으면 FALSE입니다.  
  
### <a name="remarks"></a>설명  
 PVariable로 지정 된 애니메이션 변수 애니메이션 개체에 포함 되어 있는지 확인 하려면이 메서드를 사용할 수 있습니다. 해당 유형에 따라 애니메이션 개체, 여러 애니메이션 변수를 포함할 수 있습니다. 예를 들어 CAnimationColor (빨강, 녹색 및 파랑)에 각 색의 구성 요소에 대해 하나씩 세 개의 변수를 포함합니다. 애니메이션 변수 값이 변경 될 때 Windows 애니메이션 API 재정의 또는 IntegerValueChanged 이벤트 (설정 된 경우) 및이 이벤트의 매개 변수는 애니메이션 변수의 IUIAnimationVariable 인터페이스에 대 한 포인터를 보냅니다. 이 메서드는 포함 된 COM 개체에 대 한 포인터에서 애니메이션에 대 한 포인터를 가져오는 데 도움이 됩니다.  
  
##  <a name="createtransitions"></a>  CAnimationBaseObject::CreateTransitions  
 애니메이션 개체와 관련 된 전환을 만듭니다.  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>반환 값  
 TRUE 이면 전환; 성공적으로 만들어졌습니다. 그렇지 않으면 FALSE입니다.  
  
### <a name="remarks"></a>설명  
 파생된 된 애니메이션 개체에 캡슐화 된 애니메이션 변수의 목록을 반복 하 고 각 애니메이션 변수와 관련 된 전환을 만듭니다.  
  
##  <a name="detachfromcontroller"></a>  CAnimationBaseObject::DetachFromController  
 부모 애니메이션 컨트롤러에서 애니메이션 개체를 분리합니다.  
  
```  
void DetachFromController();
```  
  
### <a name="remarks"></a>설명  
 이 메서드는 내부적으로 사용 됩니다.  
  
##  <a name="enableintegervaluechangedevent"></a>  CAnimationBaseObject::EnableIntegerValueChangedEvent  
 정수 값이 변경 이벤트 처리기를 설정합니다.  
  
```  
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>매개 변수  
 `pController`  
 부모 컨트롤러에 대 한 포인터입니다.  
  
 `bEnable`  
 를 사용 하도록 설정 하거나 정수 값 변경 이벤트를 사용 하지 않도록 지정 합니다.  
  
### <a name="remarks"></a>설명  
 정수 값이 변경 이벤트 처리기를 사용 하는 경우이 이벤트에 CAnimationController::OnAnimationIntegerValueChanged 메서드는 CAnimationController 파생 클래스에서 재정의 처리할 수 있습니다. 이 메서드는 애니메이션 정수 값이 변경 될 때마다 호출 됩니다.  
  
##  <a name="enablevaluechangedevent"></a>  CAnimationBaseObject::EnableValueChangedEvent  
 값이 변경 이벤트 처리기를 설정합니다.  
  
```  
virtual void EnableValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>매개 변수  
 `pController`  
 부모 컨트롤러에 대 한 포인터입니다.  
  
 `bEnable`  
 를 사용 하도록 설정 하거나 값 변경 이벤트를 사용 하지 않도록 지정 합니다.  
  
### <a name="remarks"></a>설명  
 값이 변경 이벤트 처리기를 사용 하는 경우이 이벤트에 CAnimationController::OnAnimationValueChanged 메서드는 CAnimationController 파생 클래스에서 재정의 처리할 수 있습니다. 이 메서드는 애니메이션 값이 변경 될 때마다 호출 됩니다.  
  
##  <a name="getanimationvariablelist"></a>  CAnimationBaseObject::GetAnimationVariableList  
 포함 된 애니메이션 변수에 대 한 포인터를 수집합니다.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst) = 0;  
```  
  
### <a name="parameters"></a>매개 변수  
 `lst`  
 애니메이션 개체에 포함 된 애니메이션 변수로 채워야 하는 목록입니다.  
  
### <a name="remarks"></a>설명  
 이 파생된 클래스에서 재정의 해야 하는 순수 가상 메서드가 있습니다. 애니메이션 개체의 유형에 따라 하나 이상의 애니메이션 변수를 포함합니다. 예를 들어 CAnimationPoint X 및 Y 좌표는 각각에 대 한 두 개의 변수를 포함 합니다. 애니메이션 변수의 목록에서 역할을 하는 일부 제네릭 메서드를 구현 하는 기본 클래스 CAnimationBaseObject: ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent 합니다. 이러한 GetAnimationVariableList 채워지는 파생된 클래스에서 특정 애니메이션 개체에 포함 된 실제 애니메이션 변수를 다음 목록에 대해 루프를 반복 하 고 필요한 작업을 수행 합니다. 사용자 지정 애니메이션 개체를 만들 경우 해당 개체에 포함 된 모든 애니메이션 변수 lst에 추가 해야 있습니다.  
  
##  <a name="getautodestroytransitions"></a>  CAnimationBaseObject::GetAutodestroyTransitions  
 관련 된 전환을 자동으로 소멸 되는지 여부를 알려 줍니다.  
  
```  
BOOL GetAutodestroyTransitions() const;  
```  
  
### <a name="return-value"></a>반환 값  
 True 인 경우, 관련 된 전환은 자동으로 제거 됩니다. false 인 경우, 응용 프로그램을 호출 하 여 변환 개체 할당을 취소 합니다.  
  
### <a name="remarks"></a>설명  
 기본적으로이 플래그는 TRUE입니다. 할당 된 스택에 전환을 및/또는 전환 호출 응용 프로그램에 의해 할당 취소 되어야 합니다는 경우에이 플래그를 설정 합니다.  
  
##  <a name="getgroupid"></a>  CAnimationBaseObject::GetGroupID  
 현재 그룹 ID를 반환 합니다.  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>반환 값  
 현재 그룹 id입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드를 사용 하 여 그룹 ID를 검색 생성자에서 또는 setid 그룹 ID 명시적으로 설정 되지 않은 경우에 0을의입니다.  
  
##  <a name="getobjectid"></a>  CAnimationBaseObject::GetObjectID  
 현재 개체 ID를 반환 합니다.  
  
```  
UINT32 GetObjectID() const;  
```  
  
### <a name="return-value"></a>반환 값  
 현재 개체의 id입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드를 사용 하 여 개체 ID를 검색 생성자에서 또는 setid 개체 ID 명시적으로 설정 되지 않은 경우에 0을의입니다.  
  
##  <a name="getuserdata"></a>  CAnimationBaseObject::GetUserData  
 사용자 정의 데이터를 반환합니다.  
  
```  
DWORD GetUserData() const;  
```  
  
### <a name="return-value"></a>반환 값  
 사용자 지정 데이터의 값입니다.  
  
### <a name="remarks"></a>설명  
 런타임 시 사용자 지정 데이터를 검색 하려면이 메서드를 호출 합니다. 반환 된 값이 초기화 되지 않은 경우 명시적으로 생성자에 속해 있거나 SetUserData 0이 됩니다.  
  
##  <a name="m_bautodestroytransitions"></a>  CAnimationBaseObject::m_bAutodestroyTransitions  
 관련 된 전환의 자동으로 제거 되어야 할지 여부를 지정 합니다.  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
##  <a name="m_dwuserdata"></a>  CAnimationBaseObject::m_dwUserData  
 사용자 정의 데이터를 저장 합니다.  
  
```  
DWORD m_dwUserData;  
```  
  
##  <a name="m_ngroupid"></a>  CAnimationBaseObject::m_nGroupID  
 애니메이션 개체의 그룹 ID를 지정합니다.  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_nobjectid"></a>  CAnimationBaseObject::m_nObjectID  
 애니메이션 개체의 개체 ID를 지정 합니다.  
  
```  
UINT32 m_nObjectID;  
```  
  
##  <a name="m_pparentcontroller"></a>  CAnimationBaseObject::m_pParentController  
 부모 애니메이션 컨트롤러에 대 한 포인터입니다.  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="setautodestroytransitions"></a>  CAnimationBaseObject::SetAutodestroyTransitions  
 주문 전환을 자동으로 삭제 하는 플래그를 설정 합니다.  
  
```  
void SetAutodestroyTransitions(BOOL bValue);
```  
  
### <a name="parameters"></a>매개 변수  
 `bValue`  
 자동 소멸 플래그를 지정 합니다.  
  
### <a name="remarks"></a>설명  
 New 연산자를 사용 하는 변환 개체를 할당 하는 경우에이 플래그를 설정 합니다. 자동 소멸 스택의 전환 개체가 할당 되는 몇 가지 이유로 플래그는 FALSE 여야 합니다. 기본적으로이 플래그는 TRUE입니다.  
  
##  <a name="setid"></a>  CAnimationBaseObject::SetID  
 새 Id를 설정합니다.  
  
```  
void SetID(
    UINT32 nObjectID,  
    UINT32 nGroupID = 0);
```  
  
### <a name="parameters"></a>매개 변수  
 `nObjectID`  
 새 개체 ID를 지정 합니다.  
  
 `nGroupID`  
 새 그룹 ID를 지정 합니다.  
  
### <a name="remarks"></a>설명  
 그룹 id입니다. 및 개체 ID를 변경할 수 있습니다. 새 그룹 ID는 현재 ID와 다른 경우 애니메이션 개체 (새 그룹 만들어짐, 필요한 경우) 다른 그룹으로 이동 합니다.  
  
##  <a name="setparentanimationobjects"></a>  CAnimationBaseObject::SetParentAnimationObjects  
 애니메이션 개체 및 해당 컨테이너에 포함 된 애니메이션 변수 간에 관계가 설정 됩니다.  
  
```  
virtual void SetParentAnimationObjects();
```  
  
### <a name="remarks"></a>설명  
 애니메이션 개체 및 해당 컨테이너에 포함 된 애니메이션 변수 간에 관계를 설정 하는 데 사용할 수 있는 도우미입니다. 애니메이션 변수를 반복 하 고 각 애니메이션 변수에 부모 애니메이션 개체에 대 한 백 포인터를 설정 합니다. 실제 관계가 성립 CAnimationBaseObject::ApplyTransitions에서 현재 구현에서 따라서 백 포인터 설정 되지 않습니다 CAnimationGroup::Animate를 호출 하기 전에. 관계를 알고 있으면 CAnimationVariable (사용 하 여 CAnimationVariable::GetParentAnimationObject에서)에서 개체 처리 이벤트 및 애니메이션을 부모를 사용 해야 하는 경우에 유용할 수 있습니다.  
  
##  <a name="setuserdata"></a>  CAnimationBaseObject::SetUserData  
 사용자 정의 데이터를 설정 합니다.  
  
```  
void SetUserData (DWORD dwUserData);
```  
  
### <a name="parameters"></a>매개 변수  
 `dwUserData`  
 사용자 지정 데이터를 지정합니다.  
  
### <a name="remarks"></a>설명  
 이 메서드를 사용 하 여 사용자 지정 데이터 애니메이션 개체와 연결 합니다. 이 데이터 GetUserData 하 여 런타임 시 나중에 검색할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [클래스](../../mfc/reference/mfc-classes.md)
