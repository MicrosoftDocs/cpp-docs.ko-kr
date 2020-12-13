---
description: '자세한 정보: CAnimationGroup 클래스'
title: CAnimationGroup 클래스
ms.date: 03/27/2019
f1_keywords:
- CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::Animate
- AFXANIMATIONCONTROLLER/CAnimationGroup::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationGroup::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::Schedule
- AFXANIMATIONCONTROLLER/CAnimationGroup::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutoclearTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstKeyFrames
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pStoryboard
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pParentController
helpviewer_keywords:
- CAnimationGroup [MFC], CAnimationGroup
- CAnimationGroup [MFC], Animate
- CAnimationGroup [MFC], ApplyTransitions
- CAnimationGroup [MFC], FindAnimationObject
- CAnimationGroup [MFC], GetGroupID
- CAnimationGroup [MFC], RemoveKeyframes
- CAnimationGroup [MFC], RemoveTransitions
- CAnimationGroup [MFC], Schedule
- CAnimationGroup [MFC], SetAutodestroyTransitions
- CAnimationGroup [MFC], AddKeyframes
- CAnimationGroup [MFC], AddTransitions
- CAnimationGroup [MFC], CreateTransitions
- CAnimationGroup [MFC], m_bAutoclearTransitions
- CAnimationGroup [MFC], m_bAutodestroyAnimationObjects
- CAnimationGroup [MFC], m_bAutodestroyKeyframes
- CAnimationGroup [MFC], m_lstAnimationObjects
- CAnimationGroup [MFC], m_lstKeyFrames
- CAnimationGroup [MFC], m_pStoryboard
- CAnimationGroup [MFC], m_nGroupID
- CAnimationGroup [MFC], m_pParentController
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
ms.openlocfilehash: 45fd49b95f73811f52795b87bf3de2dd004fa5ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336797"
---
# <a name="canimationgroup-class"></a>CAnimationGroup 클래스

애니메이션 스토리 보드, 애니메이션 개체 및 전환을 결합 하 여 애니메이션을 정의 하는 애니메이션 그룹을 구현 합니다.

## <a name="syntax"></a>구문

```
class CAnimationGroup;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAnimationGroup:: CAnimationGroup](#canimationgroup)|애니메이션 그룹을 생성 합니다.|
|[CAnimationGroup:: ~ CAnimationGroup](#_dtorcanimationgroup)|소멸자입니다. 애니메이션 그룹이 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAnimationGroup:: 애니메이션](#animate)|그룹에 애니메이션 효과를 적용 합니다.|
|[CAnimationGroup:: ApplyTransitions](#applytransitions)|애니메이션 개체에 전환을 적용 합니다.|
|[CAnimationGroup:: Find애니메이션 개체](#findanimationobject)|지정 된 애니메이션 변수를 포함 하는 애니메이션 개체를 찾습니다.|
|[CAnimationGroup:: GetGroupID](#getgroupid)|GroupID를 반환 합니다.|
|[CAnimationGroup:: RemoveKeyframes](#removekeyframes)|애니메이션 그룹에 속하는 모든 키 프레임을 제거 하 고 필요에 따라 소멸 시킵니다.|
|[CAnimationGroup:: RemoveTransitions](#removetransitions)|애니메이션 그룹에 속한 애니메이션 개체에서 전환을 제거 합니다.|
|[CAnimationGroup:: Schedule](#schedule)|지정 된 시간에 애니메이션을 예약 합니다.|
|[CAnimationGroup:: SetAutodestroyTransitions](#setautodestroytransitions)|그룹에 속한 모든 애니메이션 개체의 전환을 자동으로 제거 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CAnimationGroup:: AddKeyframes](#addkeyframes)|Storyboard에 키 프레임을 추가 하는 도우미입니다.|
|[CAnimationGroup:: AddTransitions](#addtransitions)|스토리 보드에 전환을 추가 하는 도우미입니다.|
|[CAnimationGroup:: CreateTransitions](#createtransitions)|COM 전환 개체를 만드는 도우미입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAnimationGroup:: m_bAutoclearTransitions](#m_bautocleartransitions)|그룹에 속한 애니메이션 개체에서 전환을 지우는 방법을 지정 합니다. 이 멤버가 TRUE 이면 애니메이션이 예약 될 때 전환이 자동으로 제거 됩니다. 그렇지 않으면 전환을 수동으로 제거 해야 합니다.|
|[CAnimationGroup:: m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|애니메이션 개체를 삭제 하는 방법을 지정 합니다. 이 매개 변수가 TRUE 이면 그룹이 제거 될 때 애니메이션 개체가 자동으로 제거 됩니다. 그렇지 않으면 애니메이션 개체를 수동으로 제거 해야 합니다. 기본값은 FALSE입니다. 그룹에 속한 모든 애니메이션 개체가 operator new를 사용 하 여 동적으로 할당 되는 경우에만이 값을 TRUE로 설정 합니다.|
|[CAnimationGroup:: m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|키 프레임을 제거 하는 방법을 지정 합니다. 이 값이 TRUE 이면 모든 키프레임이 제거 되 고 제거 됩니다. 그렇지 않으면 목록 에서만 제거 됩니다. 기본값은 TRUE입니다.|
|[CAnimationGroup:: m_lstAnimationObjects](#m_lstanimationobjects)|애니메이션 개체의 목록을 포함 합니다.|
|[CAnimationGroup:: m_lstKeyFrames](#m_lstkeyframes)|키 프레임 목록을 포함 합니다.|
|[CAnimationGroup:: m_pStoryboard](#m_pstoryboard)|애니메이션 스토리 보드를 가리킵니다. 이 포인터는 애니메이션에 대 한 호출 후에만 유효 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAnimationGroup:: m_nGroupID](#m_ngroupid)|애니메이션 그룹의 고유 식별자입니다.|
|[CAnimationGroup:: m_pParentController](#m_pparentcontroller)|이 그룹이 속한 애니메이션 컨트롤러에 대 한 포인터입니다.|

## <a name="remarks"></a>설명

애니메이션 그룹은 CAnimationController:: Addanimation 개체를 사용 하 여 애니메이션 개체를 추가할 때 애니메이션 컨트롤러 (CAnimationController)에 의해 자동으로 생성 됩니다. 애니메이션 그룹은 일반적으로 애니메이션 그룹을 조작 하기 위해 매개 변수로 사용 되는 GroupID로 식별 됩니다. GroupID는 새 애니메이션 그룹에 추가 되는 첫 번째 애니메이션 개체에서 가져옵니다. 캡슐화 된 애니메이션 스토리 보드는 CAnimationController:: AnimateGroup를 호출한 후에 만들어지며 public 멤버 m_pStoryboard를 통해 액세스할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CAnimationGroup`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="canimationgroupcanimationgroup"></a><a name="_dtorcanimationgroup"></a> CAnimationGroup:: ~ CAnimationGroup

소멸자입니다. 애니메이션 그룹이 제거 될 때 호출 됩니다.

```
~CAnimationGroup();
```

## <a name="canimationgroupaddkeyframes"></a><a name="addkeyframes"></a> CAnimationGroup:: AddKeyframes

Storyboard에 키 프레임을 추가 하는 도우미입니다.

```cpp
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>매개 변수

*pStoryboard*<br/>
스토리 보드 COM 개체에 대 한 포인터입니다.

*bAddDeep*<br/>
이 메서드가 다른 키프레임에 종속 되는 스토리 보드 키프레임에 추가 되어야 하는지 여부를 지정 합니다.

## <a name="canimationgroupaddtransitions"></a><a name="addtransitions"></a> CAnimationGroup:: AddTransitions

스토리 보드에 전환을 추가 하는 도우미입니다.

```cpp
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>매개 변수

*pStoryboard*<br/>
스토리 보드 COM 개체에 대 한 포인터입니다.

*bDependOnKeyframes*

## <a name="canimationgroupanimate"></a><a name="animate"></a> CAnimationGroup:: 애니메이션

그룹에 애니메이션 효과를 적용 합니다.

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>매개 변수

*pManager*<br/>
*Ptimer* 
 *bScheduleNow*

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 내부 스토리 보드를 만들고, 전환을 만들고 적용 하 고, bScheduleNow가 TRUE 인 경우 애니메이션을 예약 합니다. BScheduleNow가 FALSE 이면 지정 된 시간에 애니메이션을 시작 하려면 Schedule을 호출 해야 합니다.

## <a name="canimationgroupapplytransitions"></a><a name="applytransitions"></a> CAnimationGroup:: ApplyTransitions

애니메이션 개체에 전환을 적용 합니다.

```cpp
void ApplyTransitions();
```

### <a name="remarks"></a>설명

이 메서드는 storyboard를 만들지 않은 경우 디버그 모드에서 어설션 합니다. 먼저 모든 전환을 만든 다음 "정적" 키 프레임 (오프셋에 종속 된 키 프레임)을 추가 하 고, 전환 및 기타 키프레임에 따라 키 프레임을 추가 하 고, 마지막으로 키 프레임에 종속 되는 전환을 추가 합니다.

## <a name="canimationgroupcanimationgroup"></a><a name="canimationgroup"></a> CAnimationGroup:: CAnimationGroup

애니메이션 그룹을 생성 합니다.

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>매개 변수

*pParentController*<br/>
그룹을 만드는 애니메이션 컨트롤러에 대 한 포인터입니다.

*nGroupID*<br/>
GroupID를 지정 합니다.

## <a name="canimationgroupcreatetransitions"></a><a name="createtransitions"></a> CAnimationGroup:: CreateTransitions

COM 전환 개체를 만드는 도우미입니다.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="canimationgroupfindanimationobject"></a><a name="findanimationobject"></a> CAnimationGroup:: Find애니메이션 개체

지정 된 애니메이션 변수를 포함 하는 애니메이션 개체를 찾습니다.

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>매개 변수

*pVariable*<br/>
애니메이션 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

애니메이션 개체에 대 한 포인터 이거나, 애니메이션 개체를 찾을 수 없는 경우 NULL입니다.

## <a name="canimationgroupgetgroupid"></a><a name="getgroupid"></a> CAnimationGroup:: GetGroupID

GroupID를 반환 합니다.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>반환 값

그룹 식별자입니다.

## <a name="canimationgroupm_bautocleartransitions"></a><a name="m_bautocleartransitions"></a> CAnimationGroup:: m_bAutoclearTransitions

그룹에 속한 애니메이션 개체에서 전환을 지우는 방법을 지정 합니다. 이 멤버가 TRUE 이면 애니메이션이 예약 될 때 전환이 자동으로 제거 됩니다. 그렇지 않으면 전환을 수동으로 제거 해야 합니다.

```
BOOL m_bAutoclearTransitions;
```

## <a name="canimationgroupm_bautodestroyanimationobjects"></a><a name="m_bautodestroyanimationobjects"></a> CAnimationGroup:: m_bAutodestroyAnimationObjects

애니메이션 개체를 삭제 하는 방법을 지정 합니다. 이 매개 변수가 TRUE 이면 그룹이 제거 될 때 애니메이션 개체가 자동으로 제거 됩니다. 그렇지 않으면 애니메이션 개체를 수동으로 제거 해야 합니다. 기본값은 FALSE입니다. 그룹에 속한 모든 애니메이션 개체가 operator new를 사용 하 여 동적으로 할당 되는 경우에만이 값을 TRUE로 설정 합니다.

```
BOOL m_bAutodestroyAnimationObjects;
```

## <a name="canimationgroupm_bautodestroykeyframes"></a><a name="m_bautodestroykeyframes"></a> CAnimationGroup:: m_bAutodestroyKeyframes

키 프레임을 제거 하는 방법을 지정 합니다. 이 값이 TRUE 이면 모든 키프레임이 제거 되 고 제거 됩니다. 그렇지 않으면 목록 에서만 제거 됩니다. 기본값은 TRUE입니다.

```
BOOL m_bAutodestroyKeyframes;
```

## <a name="canimationgroupm_lstanimationobjects"></a><a name="m_lstanimationobjects"></a> CAnimationGroup:: m_lstAnimationObjects

애니메이션 개체의 목록을 포함 합니다.

```
CObList m_lstAnimationObjects;
```

## <a name="canimationgroupm_lstkeyframes"></a><a name="m_lstkeyframes"></a> CAnimationGroup:: m_lstKeyFrames

키 프레임 목록을 포함 합니다.

```
CObList m_lstKeyFrames;
```

## <a name="canimationgroupm_ngroupid"></a><a name="m_ngroupid"></a> CAnimationGroup:: m_nGroupID

애니메이션 그룹의 고유 식별자입니다.

```
UINT32 m_nGroupID;
```

## <a name="canimationgroupm_pparentcontroller"></a><a name="m_pparentcontroller"></a> CAnimationGroup:: m_pParentController

이 그룹이 속한 애니메이션 컨트롤러에 대 한 포인터입니다.

```
CAnimationController* m_pParentController;
```

## <a name="canimationgroupm_pstoryboard"></a><a name="m_pstoryboard"></a> CAnimationGroup:: m_pStoryboard

애니메이션 스토리 보드를 가리킵니다. 이 포인터는 애니메이션에 대 한 호출 후에만 유효 합니다.

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

## <a name="canimationgroupremovekeyframes"></a><a name="removekeyframes"></a> CAnimationGroup:: RemoveKeyframes

애니메이션 그룹에 속하는 모든 키 프레임을 제거 하 고 필요에 따라 소멸 시킵니다.

```cpp
void RemoveKeyframes();
```

### <a name="remarks"></a>설명

M_bAutodestroyKeyframes 멤버가 TRUE 이면 키프레임이 제거 되 고 제거 되 고, 그렇지 않으면 키프레임이 내부 키 목록에서 제거 됩니다.

## <a name="canimationgroupremovetransitions"></a><a name="removetransitions"></a> CAnimationGroup:: RemoveTransitions

애니메이션 그룹에 속한 애니메이션 개체에서 전환을 제거 합니다.

```cpp
void RemoveTransitions();
```

### <a name="remarks"></a>설명

M_bAutoclearTransitions 플래그가 TRUE로 설정 된 경우이 메서드는 그룹에 속하는 모든 애니메이션 개체를 반복 하 고 CAnimationObject:: ClearTransitions 호출 합니다 (FALSE).

## <a name="canimationgroupschedule"></a><a name="schedule"></a> CAnimationGroup:: Schedule

지정 된 시간에 애니메이션을 예약 합니다.

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>매개 변수

*pTimer*<br/>
애니메이션 타이머에 대 한 포인터입니다.

*time*<br/>
애니메이션을 예약 하는 시간을 지정 합니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 메서드가 실패 하거나 bScheduleNow가 FALSE로 설정 된 상태에서 애니메이션을 호출 하지 않은 경우 FALSE입니다.

### <a name="remarks"></a>설명

지정 된 시간에 애니메이션을 예약 하려면이 함수를 호출 합니다. BScheduleNow를 FALSE로 설정 하 여 애니메이션 효과를 먼저 호출 해야 합니다.

## <a name="canimationgroupsetautodestroytransitions"></a><a name="setautodestroytransitions"></a> CAnimationGroup:: SetAutodestroyTransitions

그룹에 속한 모든 애니메이션 개체의 전환을 자동으로 제거 합니다.

```cpp
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>매개 변수

*bAutoDestroy*<br/>
전환을 제거 하는 방법을 지정 합니다.

### <a name="remarks"></a>설명

스택에서 전환을 할당 하는 경우에만이 값을 FALSE로 설정 합니다. 기본값은 TRUE 이므로 operator new를 사용 하 여 전환 개체를 할당 하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
