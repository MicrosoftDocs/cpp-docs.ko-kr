---
description: '자세한 정보: CAnimationController 클래스'
title: CAnimationController 클래스
ms.date: 03/27/2019
f1_keywords:
- CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::AddAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::AddKeyframeToGroup
- AFXANIMATIONCONTROLLER/CAnimationController::AnimateGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CleanUpGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CreateKeyframe
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationManagerEvent
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnablePriorityComparisonHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnableStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::GetKeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionLibrary
- AFXANIMATIONCONTROLLER/CAnimationController::IsAnimationInProgress
- AFXANIMATIONCONTROLLER/CAnimationController::IsValid
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnBeforeAnimationStart
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCancel
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCompress
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityConclude
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityTrim
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAllAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationController::ScheduleGroup
- AFXANIMATIONCONTROLLER/CAnimationController::SetRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::UpdateAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::OnAfterSchedule
- AFXANIMATIONCONTROLLER/CAnimationController::gkeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::m_bIsValid
- AFXANIMATIONCONTROLLER/CAnimationController::m_lstAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::m_pRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionLibrary
helpviewer_keywords:
- CAnimationController [MFC], CAnimationController
- CAnimationController [MFC], AddAnimationObject
- CAnimationController [MFC], AddKeyframeToGroup
- CAnimationController [MFC], AnimateGroup
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], CreateKeyframe
- CAnimationController [MFC], EnableAnimationManagerEvent
- CAnimationController [MFC], EnableAnimationTimerEventHandler
- CAnimationController [MFC], EnablePriorityComparisonHandler
- CAnimationController [MFC], EnableStoryboardEventHandler
- CAnimationController [MFC], FindAnimationGroup
- CAnimationController [MFC], FindAnimationObject
- CAnimationController [MFC], GetKeyframeStoryboardStart
- CAnimationController [MFC], GetUIAnimationManager
- CAnimationController [MFC], GetUIAnimationTimer
- CAnimationController [MFC], GetUITransitionFactory
- CAnimationController [MFC], GetUITransitionLibrary
- CAnimationController [MFC], IsAnimationInProgress
- CAnimationController [MFC], IsValid
- CAnimationController [MFC], OnAnimationIntegerValueChanged
- CAnimationController [MFC], OnAnimationManagerStatusChanged
- CAnimationController [MFC], OnAnimationTimerPostUpdate
- CAnimationController [MFC], OnAnimationTimerPreUpdate
- CAnimationController [MFC], OnAnimationTimerRenderingTooSlow
- CAnimationController [MFC], OnAnimationValueChanged
- CAnimationController [MFC], OnBeforeAnimationStart
- CAnimationController [MFC], OnHasPriorityCancel
- CAnimationController [MFC], OnHasPriorityCompress
- CAnimationController [MFC], OnHasPriorityConclude
- CAnimationController [MFC], OnHasPriorityTrim
- CAnimationController [MFC], OnStoryboardStatusChanged
- CAnimationController [MFC], OnStoryboardUpdated
- CAnimationController [MFC], RemoveAllAnimationGroups
- CAnimationController [MFC], RemoveAnimationGroup
- CAnimationController [MFC], RemoveAnimationObject
- CAnimationController [MFC], RemoveTransitions
- CAnimationController [MFC], ScheduleGroup
- CAnimationController [MFC], SetRelatedWnd
- CAnimationController [MFC], UpdateAnimationManager
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], OnAfterSchedule
- CAnimationController [MFC], gkeyframeStoryboardStart
- CAnimationController [MFC], m_bIsValid
- CAnimationController [MFC], m_lstAnimationGroups
- CAnimationController [MFC], m_pAnimationManager
- CAnimationController [MFC], m_pAnimationTimer
- CAnimationController [MFC], m_pRelatedWnd
- CAnimationController [MFC], m_pTransitionFactory
- CAnimationController [MFC], m_pTransitionLibrary
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
ms.openlocfilehash: 30754084ff62a06ef38d16e555ea32a585bb5b52
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254757"
---
# <a name="canimationcontroller-class"></a>CAnimationController 클래스

애니메이션을 만들고 관리하기 위한 중앙 인터페이스를 제공하는 애니메이션 컨트롤러를 구현합니다.

## <a name="syntax"></a>구문

```
class CAnimationController : public CObject;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAnimationController:: CAnimationController](#canimationcontroller)|애니메이션 컨트롤러를 생성 합니다.|
|[CAnimationController:: ~ CAnimationController](#_dtorcanimationcontroller)|소멸자입니다. 애니메이션 컨트롤러 개체가 제거 될 때 호출 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAnimationController:: Add애니메이션 개체](#addanimationobject)|애니메이션 컨트롤러에 속한 그룹에 애니메이션 개체를 추가 합니다.|
|[CAnimationController:: AddKeyframeToGroup](#addkeyframetogroup)|그룹에 키 프레임을 추가 합니다.|
|[CAnimationController:: AnimateGroup](#animategroup)|애니메이션을 실행할 그룹을 준비 하 고 필요에 따라 일정을 예약 합니다.|
|[CAnimationController:: CleanUpGroup](#cleanupgroup)|오버로드됨. 애니메이션을 예약할 때 그룹을 정리 하기 위해 프레임 워크에서 호출 됩니다.|
|[CAnimationController::CreateKeyframe](#createkeyframe)|오버로드됨. 전환을 사용하는 키 프레임을 만들어 지정된 그룹에 추가합니다.|
|[CAnimationController:: Enable-이벤트 관리자 이벤트](#enableanimationmanagerevent)|애니메이션 관리자의 상태가 변경 될 때 호출할 처리기를 설정 하거나 해제 합니다.|
|[CAnimationController:: Enable를 타이머 처리기](#enableanimationtimereventhandler)|타이밍 이벤트에 대 한 처리기 및 타이밍 업데이트 처리기를 설정 하거나 해제 합니다.|
|[CAnimationController:: EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|예약 된 스토리 보드를 취소, 결론, 트리밍 또는 압축할 수 있는지 여부를 확인 하기 위해 호출할 우선 순위 비교 처리기를 설정 하거나 해제 합니다.|
|[CAnimationController:: EnableStoryboardEventHandler](#enablestoryboardeventhandler)|스토리 보드 상태 및 업데이트 이벤트에 대 한 처리기를 설정 하거나 해제 합니다.|
|[CAnimationController:: Find애니메이션 그룹](#findanimationgroup)|오버로드됨. 해당 storyboard에서 애니메이션 그룹을 찾습니다.|
|[CAnimationController:: Find애니메이션 개체](#findanimationobject)|지정 된 애니메이션 변수를 포함 하는 애니메이션 개체를 찾습니다.|
|[CAnimationController:: GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|스토리 보드의 시작을 식별 하는 키 프레임을 반환 합니다.|
|[CAnimationController:: Getuiwanmanager](#getuianimationmanager)|캡슐화 된 Iui애니메이션 관리자 개체에 대 한 액세스를 제공 합니다.|
|[CAnimationController:: Getui애니메이션 타이머](#getuianimationtimer)|캡슐화 된 Iui애니메이션 타이머 개체에 대 한 액세스를 제공 합니다.|
|[CAnimationController:: GetUITransitionFactory](#getuitransitionfactory)|전환 라이브러리를 만들지 못한 경우 IUIAnimationTransitionFactory interface 또는 NULL에 대 한 포인터입니다.|
|[CAnimationController:: GetUITransitionLibrary](#getuitransitionlibrary)|캡슐화 된 IUIAnimationTransitionLibrary 개체에 대 한 액세스를 제공 합니다.|
|[CAnimationController:: Is를 Inprogress](#isanimationinprogress)|하나 이상의 그룹에서 애니메이션을 재생 하 고 있는지 여부를 나타냅니다.|
|[CAnimationController:: IsValid](#isvalid)|애니메이션 컨트롤러가 유효한 지 여부를 나타냅니다.|
|[CAnimationController:: OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|애니메이션 변수의 정수 값이 변경 될 때 프레임 워크에서 호출 됩니다.|
|[CAnimationController:: OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|애니메이션 관리자의 StatusChanged 이벤트에 대 한 응답으로 프레임 워크에서 호출 됩니다.|
|[CAnimationController:: Onpost타이머 Postupdate](#onanimationtimerpostupdate)|애니메이션 업데이트가 완료 된 후 프레임 워크에서 호출 됩니다.|
|[CAnimationController:: OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|애니메이션 업데이트를 시작 하기 전에 프레임 워크에서 호출 됩니다.|
|[CAnimationController:: OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|애니메이션의 렌더링 프레임 비율이 최소한의 적절 한 프레임 속도로 떨어질 때 프레임 워크에서 호출 됩니다.|
|[CAnimationController:: OnAnimationValueChanged](#onanimationvaluechanged)|애니메이션 변수 값이 변경 될 때 프레임 워크에서 호출 됩니다.|
|[CAnimationController:: OnBeforeAnimationStart](#onbeforeanimationstart)|애니메이션이 예약 되기 직전에 프레임 워크에서 호출 됩니다.|
|[CAnimationController:: OnHasPriorityCancel](#onhasprioritycancel)|일정 충돌을 해결하기 위해 프레임워크에 의해 호출됩니다.|
|[CAnimationController:: OnHasPriorityCompress](#onhasprioritycompress)|일정 충돌을 해결하기 위해 프레임워크에 의해 호출됩니다.|
|[CAnimationController:: OnHasPriorityConclude](#onhaspriorityconclude)|일정 충돌을 해결하기 위해 프레임워크에 의해 호출됩니다.|
|[CAnimationController:: OnHasPriorityTrim](#onhasprioritytrim)|일정 충돌을 해결하기 위해 프레임워크에 의해 호출됩니다.|
|[CAnimationController:: OnStoryboardStatusChanged](#onstoryboardstatuschanged)|스토리 보드 상태가 변경 될 때 프레임 워크에서 호출 됩니다.|
|[CAnimationController:: OnStoryboardUpdated](#onstoryboardupdated)|Storyboard가 업데이트 될 때 프레임 워크에서 호출 됩니다.|
|[CAnimationController:: RemoveAllAnimationGroups](#removeallanimationgroups)|애니메이션 컨트롤러에서 모든 애니메이션 그룹을 제거 합니다.|
|[CAnimationController:: Remove애니메이션 그룹](#removeanimationgroup)|애니메이션 컨트롤러에서 지정 된 ID를 가진 애니메이션 그룹을 제거 합니다.|
|[CAnimationController:: Remove애니메이션 개체](#removeanimationobject)|애니메이션 컨트롤러에서 애니메이션 개체를 제거 합니다.|
|[CAnimationController:: RemoveTransitions](#removetransitions)|지정 된 그룹에 속한 애니메이션 개체에서 전환을 제거 합니다.|
|[CAnimationController:: ScheduleGroup](#schedulegroup)|애니메이션을 예약 합니다.|
|[CAnimationController:: SetRelatedWnd](#setrelatedwnd)|애니메이션 컨트롤러와 창 간의 관계를 설정 합니다.|
|[CAnimationController:: Update' 관리자 '](#updateanimationmanager)|모든 애니메이션 변수의 값을 업데이트 하도록 애니메이션 관리자에 게 지시 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CAnimationController:: CleanUpGroup](#cleanupgroup)|오버로드됨. 그룹을 정리 하는 도우미입니다.|
|[CAnimationController:: OnAfterSchedule](#onafterschedule)|지정 된 그룹에 대 한 애니메이션을 예약할 때 프레임 워크에서 호출 됩니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAnimationController:: gkeyframeStoryboardStart](#g_keyframestoryboardstart)|스토리 보드의 시작을 나타내는 키 프레임입니다.|
|[CAnimationController:: m_bIsValid](#m_bisvalid)|애니메이션 컨트롤러의 유효성 여부를 지정 합니다. 현재 OS가 Windows 애니메이션 API를 지원 하지 않는 경우이 멤버는 FALSE로 설정 됩니다.|
|[CAnimationController:: m_lstAnimationGroups](#m_lstanimationgroups)|이 애니메이션 컨트롤러에 속하는 애니메이션 그룹의 목록입니다.|
|[CAnimationController:: m_pAnimationManager](#m_panimationmanager)|애니메이션 관리자 COM 개체에 대 한 포인터를 저장 합니다.|
|[CAnimationController:: m_pAnimationTimer](#m_panimationtimer)|애니메이션 타이머 COM 개체에 대 한 포인터를 저장 합니다.|
|[CAnimationController:: m_pRelatedWnd](#m_prelatedwnd)|애니메이션 관리자의 상태가 변경 되거나 사후 업데이트 이벤트가 발생 했을 때 자동으로 다시 그려질 수 있는 관련 CWnd 개체에 대 한 포인터입니다. NULL일 수 있습니다.|
|[CAnimationController:: m_pTransitionFactory](#m_ptransitionfactory)|전환 팩터리 COM 개체에 대 한 포인터를 저장 합니다.|
|[CAnimationController:: m_pTransitionLibrary](#m_ptransitionlibrary)|전환 라이브러리 COM 개체에 대 한 포인터를 저장 합니다.|

## <a name="remarks"></a>설명

CAnimationController 클래스는 애니메이션을 관리 하는 키 클래스입니다. 응용 프로그램에서 하나 이상의 애니메이션 컨트롤러 인스턴스를 만들고 필요에 따라 CAnimationController:: SetRelatedWnd를 사용 하 여 애니메이션 컨트롤러 인스턴스를 CWnd 개체에 연결할 수 있습니다. 이 연결은 애니메이션 관리자 상태가 변경 되었거나 애니메이션 타이머가 업데이트 되었을 때 WM_PAINT 메시지를 관련 창에 자동으로 전송 하는 데 필요 합니다. 이 관계를 사용 하지 않는 경우 애니메이션을 수동으로 표시 하는 창을 다시 그려야 합니다. 이러한 목적을 위해 CAnimationController에서 클래스를 파생 하 고 OnAnimationManagerStatusChanged 및/또는 Onanimationmanagerstatuschanged를 재정의 하 고 필요한 경우 하나 이상의 창을 무효화할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>요구 사항

**헤더:** afxanimationcontroller.h

## <a name="canimationcontrollercanimationcontroller"></a><a name="_dtorcanimationcontroller"></a> CAnimationController:: ~ CAnimationController

소멸자입니다. 애니메이션 컨트롤러 개체가 제거 될 때 호출 됩니다.

```
virtual ~CAnimationController(void);
```

## <a name="canimationcontrolleraddanimationobject"></a><a name="addanimationobject"></a> CAnimationController:: Add애니메이션 개체

애니메이션 컨트롤러에 속한 그룹에 애니메이션 개체를 추가 합니다.

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>매개 변수

*pObject*<br/>
애니메이션 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하는 경우 pObject이 추가 된 기존 또는 새 애니메이션 그룹에 대 한 포인터입니다. 다른 애니메이션 컨트롤러에 속한 그룹에 pObject이 이미 추가 된 경우 NULL입니다.

### <a name="remarks"></a>설명

애니메이션 컨트롤러에 애니메이션 개체를 추가 하려면이 메서드를 호출 합니다. 개체의 GroupID에 따라 그룹에 개체가 추가 됩니다 (CAnimationBaseObject:: SetID 참조). 지정 된 GroupID를 사용 하 여 첫 번째 개체를 추가 하는 경우 애니메이션 컨트롤러는 새 그룹을 만듭니다. 애니메이션 개체는 하나의 애니메이션 컨트롤러에만 추가할 수 있습니다. 다른 컨트롤러에 개체를 추가 해야 하는 경우 먼저 RemoveAnimationObject를 호출 합니다. 이미 그룹에 추가 된 개체에 대해 새 GroupID를 사용 하 여 SetID를 호출 하면 개체가 이전 그룹에서 제거 되 고 지정 된 ID를 가진 다른 그룹에 추가 됩니다.

## <a name="canimationcontrolleraddkeyframetogroup"></a><a name="addkeyframetogroup"></a> CAnimationController:: AddKeyframeToGroup

그룹에 키 프레임을 추가 합니다.

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>매개 변수

*nGroupID*<br/>
그룹 ID를 지정 합니다.

*pKeyframe*<br/>
키 프레임에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

일반적으로이 메서드를 호출할 필요가 없습니다. CAnimationController:: CreateKeyframe을 대신 사용 하 여 그룹에 만든 키 프레임을 자동으로 만들어 추가 합니다.

## <a name="canimationcontrolleranimategroup"></a><a name="animategroup"></a> CAnimationController:: AnimateGroup

애니메이션을 실행할 그룹을 준비 하 고 필요에 따라 일정을 예약 합니다.

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>매개 변수

*nGroupID*<br/>
GroupID를 지정 합니다.

*bScheduleNow*<br/>
애니메이션을 즉시 실행할지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

애니메이션이 성공적으로 예약 되 고 실행 되 면 TRUE입니다.

### <a name="remarks"></a>설명

이 메서드는 스토리 보드를 만들고 애니메이션 변수를 추가 하 고 전환을 적용 하 고 키 프레임을 설정 하는 실제 작업을 수행 합니다. BScheduleNow를 FALSE로 설정한 경우 일정을 지연 시킬 수 있습니다. 이 경우 지정 된 그룹은 애니메이션에 대해 설정 된 storyboard를 포함 합니다. 이때 storyboard 및 애니메이션 변수에 대 한 이벤트를 설정할 수 있습니다. 실제로 애니메이션을 실행 해야 하는 경우 CAnimationController:: ScheduleGroup를 호출 합니다.

## <a name="canimationcontrollercanimationcontroller"></a><a name="canimationcontroller"></a> CAnimationController:: CAnimationController

애니메이션 컨트롤러를 생성 합니다.

```
CAnimationController(void);
```

## <a name="canimationcontrollercleanupgroup"></a><a name="cleanupgroup"></a> CAnimationController:: CleanUpGroup

애니메이션을 예약할 때 그룹을 정리 하기 위해 프레임 워크에서 호출 됩니다.

```cpp
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>매개 변수

*nGroupID*<br/>
GroupID를 지정 합니다.

*pGroup*<br/>
정리할 애니메이션 그룹에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 애니메이션이 예약 된 후 관련 되지 않으므로 지정 된 그룹에서 모든 전환 및 키 프레임을 제거 합니다.

## <a name="canimationcontrollercreatekeyframe"></a><a name="createkeyframe"></a> CAnimationController:: CreateKeyframe

전환을 사용하는 키 프레임을 만들어 지정된 그룹에 추가합니다.

```
CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseTransition* pTransition);

CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>매개 변수

*nGroupID*<br/>
키 프레임을 만들 그룹 ID를 지정합니다.

*pTransition*<br/>
전환에 대한 포인터입니다. 이 전환 후 스토리보드에 키 프레임이 삽입됩니다.

*pKeyframe*<br/>
이 키 프레임의 기본 키 프레임에 대한 포인터입니다.

*offset*<br/>
pKeyframe에 지정된 기본 키 프레임에서의 오프셋(초)입니다.

### <a name="return-value"></a>반환 값

함수가 성공할 경우 새로 생성되는 키 프레임에 대한 포인터입니다.

### <a name="remarks"></a>설명

반환된 포인터를 저장하고 새로 만든 키 프레임을 다른 키 프레임의 기반으로 사용할 수 있습니다(두 번째 오버로드 참조). 키 프레임에서 전환을 시작할 수 있습니다(CBaseTransition::SetKeyframes 참조). 이런 방법으로 만든 키 프레임은 애니메이션 그룹에 의해 자동으로 삭제되기 때문에 삭제할 필요가 없습니다. 다른 키 프레임 및 전환을 기반으로 하여 키 프레임을 만들 때는 순환 참조가 발생하지 않도록 주의하세요.

## <a name="canimationcontrollerenableanimationmanagerevent"></a><a name="enableanimationmanagerevent"></a> CAnimationController:: Enable-이벤트 관리자 이벤트

애니메이션 관리자의 상태가 변경 될 때 호출할 처리기를 설정 하거나 해제 합니다.

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
처리기를 설정 하거나 해제할 것인지 지정 합니다.

### <a name="return-value"></a>반환 값

처리기가 성공적으로 설정 또는 해제 되었으면 TRUE입니다.

### <a name="remarks"></a>설명

처리기를 설정 (활성화) 하면 애니메이션 관리자의 상태가 변경 될 때 Windows 애니메이션에서 OnAnimationManagerStatusChanged를 호출 합니다.

## <a name="canimationcontrollerenableanimationtimereventhandler"></a><a name="enableanimationtimereventhandler"></a> CAnimationController:: Enable를 타이머 처리기

타이밍 이벤트에 대 한 처리기 및 타이밍 업데이트 처리기를 설정 하거나 해제 합니다.

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
처리기를 설정 하거나 해제 하는지 여부를 지정 합니다.

*idleBehavior*<br/>
타이머 업데이트 처리기에 대 한 유휴 동작을 지정 합니다.

### <a name="return-value"></a>반환 값

처리기가 성공적으로 설정 또는 해제 되었으면 TRUE이 고, 그렇지 않으면입니다. 처리기를 먼저 해제 하지 않고이 메서드가 두 번 호출 되 면 FALSE이 고, 다른 오류가 발생 하면 FALSE입니다.

### <a name="remarks"></a>설명

처리기가 설정 (활성화) 되 면 Windows 애니메이션 API는 OnOnRenderingTooSlow를 호출 합니다. Windows 애니메이션 API 업데이트 storyboard를 허용 하려면 애니메이션 타이머를 사용 하도록 설정 해야 합니다. 그렇지 않으면 모든 애니메이션 변수의 값을 업데이트 하도록 애니메이션 관리자에 게 지시 하기 위해 CAnimationController:: Updateanimation Manager를 호출 해야 합니다.

## <a name="canimationcontrollerenableprioritycomparisonhandler"></a><a name="enableprioritycomparisonhandler"></a> CAnimationController:: EnablePriorityComparisonHandler

예약 된 스토리 보드를 취소, 결론, 트리밍 또는 압축할 수 있는지 여부를 확인 하기 위해 호출할 우선 순위 비교 처리기를 설정 하거나 해제 합니다.

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>매개 변수

*dwHandlerType*<br/>
설정 하거나 해제할 처리기를 지정 하는 UI_ANIMATION_PHT_ 플래그의 조합입니다 (설명 참조).

### <a name="return-value"></a>반환 값

처리기가 성공적으로 설정 또는 해제 되었으면 TRUE입니다.

### <a name="remarks"></a>설명

처리기가 설정 (사용) 되 면 Windows 애니메이션은 dwHandlerType: OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress에 따라 다음과 같은 가상 메서드를 호출 합니다. dwHandler는 다음과 같은 플래그를 조합 하 여 사용할 수 있습니다. UI_ANIMATION_PHT_NONE 모든 처리기 UI_ANIMATION_PHT_CANCEL 설정 취소 비교 처리기 UI_ANIMATION_PHT_CONCLUDE 집합 압축 비교 처리기 UI_ANIMATION_PHT_TRIM-설정 트리밍 비교 처리기 UI_ANIMATION_PHT_CANCEL_REMOVE-제거 비교 처리기 UI_ANIMATION_PHT_CONCLUDE_REMOVE 제거-UI_ANIMATION_PHT_COMPRESS 비교 처리기 UI_ANIMATION_PHT_COMPRESS_REMOVE 제거-압축 비교 처리기 UI_ANIMATION_PHT_TRIM_REMOVE 제거 트리밍 비교 처리기 제거

## <a name="canimationcontrollerenablestoryboardeventhandler"></a><a name="enablestoryboardeventhandler"></a> CAnimationController:: EnableStoryboardEventHandler

스토리 보드 상태 및 업데이트 이벤트에 대 한 처리기를 설정 하거나 해제 합니다.

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>매개 변수

*nGroupID*<br/>
그룹 ID를 지정 합니다.

*bEnable*<br/>
처리기를 설정 하거나 해제할 것인지 지정 합니다.

### <a name="return-value"></a>반환 값

처리기가 성공적으로 설정 또는 해제 되었으면 TRUE이 고, 그렇지 않으면입니다. 지정 된 애니메이션 그룹을 찾을 수 없거나 지정 된 그룹에 대 한 애니메이션이 시작 되지 않고 내부 storyboard가 NULL 이면 FALSE입니다.

### <a name="remarks"></a>설명

처리기가 설정 (활성화) 되 면 Windows 애니메이션 API가 OnStoryboardStatusChanges 및 OnStoryboardUpdated 가상 메서드를 호출 합니다. 캡슐화 된 Iuianimation Storyboard 개체를 만들기 때문에 지정 된 애니메이션 그룹에 대해 CAnimationController:: Animate를 호출한 후 처리기를 설정 해야 합니다.

## <a name="canimationcontrollerfindanimationgroup"></a><a name="findanimationgroup"></a> CAnimationController:: Find애니메이션 그룹

그룹 ID를 기준으로 애니메이션 그룹을 찾습니다.

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>매개 변수

*nGroupID*<br/>
GroupID를 지정 합니다.

*pStoryboard*<br/>
스토리 보드에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

애니메이션 그룹에 대 한 포인터 이거나, 지정 된 ID를 가진 그룹을 찾을 수 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 런타임 시 애니메이션 그룹을 찾을 수 있습니다. 특정 GroupID를 가진 첫 번째 애니메이션 개체가 애니메이션 컨트롤러에 추가 되는 경우 그룹을 만들어 애니메이션 그룹의 내부 목록에 추가 합니다.

## <a name="canimationcontrollerfindanimationobject"></a><a name="findanimationobject"></a> CAnimationController:: Find애니메이션 개체

지정 된 애니메이션 변수를 포함 하는 애니메이션 개체를 찾습니다.

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>매개 변수

*pVariable*<br/>
애니메이션 변수에 대 한 포인터입니다.

*ppObject*<br/>
출력 애니메이션 개체 또는 NULL에 대 한 포인터를 포함 합니다.

*ppGroup*<br/>
출력 애니메이션 개체를 보유 하는 애니메이션 그룹 또는 NULL에 대 한 포인터를 포함 합니다.

### <a name="return-value"></a>반환 값

개체가 있으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

들어오는 애니메이션 변수에서 애니메이션 개체를 찾아야 하는 경우 이벤트 처리기에서 호출 됩니다.

## <a name="canimationcontrollergkeyframestoryboardstart"></a><a name="g_keyframestoryboardstart"></a> CAnimationController:: gkeyframeStoryboardStart

스토리 보드의 시작을 나타내는 키 프레임입니다.

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

## <a name="canimationcontrollergetkeyframestoryboardstart"></a><a name="getkeyframestoryboardstart"></a> CAnimationController:: GetKeyframeStoryboardStart

스토리 보드의 시작을 식별 하는 키 프레임을 반환 합니다.

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>반환 값

Storyboard의 시작을 식별 하는 기본 키 프레임에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 키 프레임을 가져와 storyboard를 시작 하는 시점에 다른 모든 키 프레임 또는 전환을 기반으로 합니다.

## <a name="canimationcontrollergetuianimationmanager"></a><a name="getuianimationmanager"></a> CAnimationController:: Getuiwanmanager

캡슐화 된 Iui애니메이션 관리자 개체에 대 한 액세스를 제공 합니다.

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>반환 값

애니메이션 관리자를 만들지 못한 경우 Iuianimation Manager 인터페이스 또는 NULL에 대 한 포인터입니다.

### <a name="remarks"></a>설명

현재 OS가 Windows 애니메이션 API를 지원 하지 않는 경우이 메서드는 NULL을 반환 하 고 CAnimationController:: IsValid의 모든 후속 호출이 FALSE를 반환 합니다. 애니메이션 컨트롤러에서 래핑되지 않은 인터페이스 메서드를 호출 하려면 Iui연결 관리자에 액세스 해야 할 수 있습니다.

## <a name="canimationcontrollergetuianimationtimer"></a><a name="getuianimationtimer"></a> CAnimationController:: Getui애니메이션 타이머

캡슐화 된 Iui애니메이션 타이머 개체에 대 한 액세스를 제공 합니다.

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>반환 값

애니메이션 타이머를 만들지 못한 경우 Iuianimation Timer 인터페이스 또는 NULL에 대 한 포인터입니다.

### <a name="remarks"></a>설명

현재 OS가 Windows 애니메이션 API를 지원 하지 않는 경우이 메서드는 NULL을 반환 하 고 CAnimationController:: IsValid의 모든 후속 호출이 FALSE를 반환 합니다.

## <a name="canimationcontrollergetuitransitionfactory"></a><a name="getuitransitionfactory"></a> CAnimationController:: GetUITransitionFactory

전환 라이브러리를 만들지 못한 경우 IUIAnimationTransitionFactory interface 또는 NULL에 대 한 포인터입니다.

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>반환 값

전환 팩터리 생성에 실패 한 경우 IUIAnimationTransitionFactory 또는 NULL에 대 한 포인터입니다.

### <a name="remarks"></a>설명

현재 OS가 Windows 애니메이션 API를 지원 하지 않는 경우이 메서드는 NULL을 반환 하 고 CAnimationController:: IsValid의 모든 후속 호출이 FALSE를 반환 합니다.

## <a name="canimationcontrollergetuitransitionlibrary"></a><a name="getuitransitionlibrary"></a> CAnimationController:: GetUITransitionLibrary

캡슐화 된 IUIAnimationTransitionLibrary 개체에 대 한 액세스를 제공 합니다.

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>반환 값

전환 라이브러리를 만들지 못한 경우 IUIAnimationTransitionLibrary interface 또는 NULL에 대 한 포인터입니다.

### <a name="remarks"></a>설명

현재 OS가 Windows 애니메이션 API를 지원 하지 않는 경우이 메서드는 NULL을 반환 하 고 CAnimationController:: IsValid의 모든 후속 호출이 FALSE를 반환 합니다.

## <a name="canimationcontrollerisanimationinprogress"></a><a name="isanimationinprogress"></a> CAnimationController:: Is를 Inprogress

하나 이상의 그룹에서 애니메이션을 재생 하 고 있는지 여부를 나타냅니다.

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>반환 값

이 애니메이션 컨트롤러에 대 한 애니메이션이 진행 중인 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

애니메이션 관리자의 상태를 확인 하 고 상태를 UI_ANIMATION_MANAGER_BUSY 경우 TRUE를 반환 합니다.

## <a name="canimationcontrollerisvalid"></a><a name="isvalid"></a> CAnimationController:: IsValid

애니메이션 컨트롤러가 유효한 지 여부를 나타냅니다.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>반환 값

애니메이션 컨트롤러를 사용할 수 있으면 TRUE이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 현재 OS에서 Windows 애니메이션 API가 지원 되지 않는 경우에만 FALSE를 반환 하 고, 등록 되지 않았기 때문에 애니메이션 관리자를 만들지 못했습니다. 이 플래그를 설정 하려면 COM 라이브러리를 초기화 한 후에 한 번 이상 Getui% 1을 (를) 호출 해야 합니다.

## <a name="canimationcontrollerm_bisvalid"></a><a name="m_bisvalid"></a> CAnimationController:: m_bIsValid

애니메이션 컨트롤러의 유효성 여부를 지정 합니다. 현재 OS가 Windows 애니메이션 API를 지원 하지 않는 경우이 멤버는 FALSE로 설정 됩니다.

```
BOOL m_bIsValid;
```

## <a name="canimationcontrollerm_lstanimationgroups"></a><a name="m_lstanimationgroups"></a> CAnimationController:: m_lstAnimationGroups

이 애니메이션 컨트롤러에 속하는 애니메이션 그룹의 목록입니다.

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

## <a name="canimationcontrollerm_panimationmanager"></a><a name="m_panimationmanager"></a> CAnimationController:: m_pAnimationManager

애니메이션 관리자 COM 개체에 대 한 포인터를 저장 합니다.

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

## <a name="canimationcontrollerm_panimationtimer"></a><a name="m_panimationtimer"></a> CAnimationController:: m_pAnimationTimer

애니메이션 타이머 COM 개체에 대 한 포인터를 저장 합니다.

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

## <a name="canimationcontrollerm_prelatedwnd"></a><a name="m_prelatedwnd"></a> CAnimationController:: m_pRelatedWnd

애니메이션 관리자의 상태가 변경 되거나 사후 업데이트 이벤트가 발생 했을 때 자동으로 다시 그려질 수 있는 관련 CWnd 개체에 대 한 포인터입니다. NULL일 수 있습니다.

```
CWnd* m_pRelatedWnd;
```

## <a name="canimationcontrollerm_ptransitionfactory"></a><a name="m_ptransitionfactory"></a> CAnimationController:: m_pTransitionFactory

전환 팩터리 COM 개체에 대 한 포인터를 저장 합니다.

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

## <a name="canimationcontrollerm_ptransitionlibrary"></a><a name="m_ptransitionlibrary"></a> CAnimationController:: m_pTransitionLibrary

전환 라이브러리 COM 개체에 대 한 포인터를 저장 합니다.

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

## <a name="canimationcontrolleronafterschedule"></a><a name="onafterschedule"></a> CAnimationController:: OnAfterSchedule

지정 된 그룹에 대 한 애니메이션을 예약할 때 프레임 워크에서 호출 됩니다.

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>매개 변수

*pGroup*<br/>
예약 된 애니메이션 그룹에 대 한 포인터입니다.

### <a name="remarks"></a>설명

기본 구현에서는 지정 된 그룹에서 키 프레임을 제거 하 고 지정 된 그룹에 속하는 애니메이션 변수에서 키를 전환 합니다. 파생 클래스에서 재정의 하 여 애니메이션 일정에 따라 추가 작업을 수행할 수 있습니다.

## <a name="canimationcontrolleronanimationintegervaluechanged"></a><a name="onanimationintegervaluechanged"></a> CAnimationController:: OnAnimationIntegerValueChanged

애니메이션 변수의 정수 값이 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>매개 변수

*pGroup*<br/>
값이 변경 된 애니메이션 개체를 보유 하는 애니메이션 그룹에 대 한 포인터입니다.

*pObject*<br/>
값이 변경 된 애니메이션 변수를 포함 하는 애니메이션 개체에 대 한 포인터입니다.

*variable*<br/>
애니메이션 변수에 대 한 포인터입니다.

*newValue*<br/>
새 값을 지정 합니다.

*prevValue*<br/>
이전 값을 지정 합니다.

### <a name="remarks"></a>설명

이 메서드는 특정 애니메이션 변수 또는 애니메이션 개체에 대해 EnableIntegerValueChangedEvent가 호출 된 애니메이션 변수 이벤트를 사용 하도록 설정 하는 경우 호출 됩니다. 애플리케이션별 작업을 수행하기 위해 파생된 클래스에서 재정의될 수 있습니다.

## <a name="canimationcontrolleronanimationmanagerstatuschanged"></a><a name="onanimationmanagerstatuschanged"></a> CAnimationController:: OnAnimationManagerStatusChanged

애니메이션 관리자의 StatusChanged 이벤트에 대 한 응답으로 프레임 워크에서 호출 됩니다.

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>매개 변수

*newStatus*<br/>
새 애니메이션 관리자 상태입니다.

*previousStatus*<br/>
이전 애니메이션 관리자 상태입니다.

### <a name="remarks"></a>설명

이 메서드는 Enableanimation Managerevent로 animation manager 이벤트를 사용 하도록 설정 하는 경우 호출 됩니다. 애플리케이션별 작업을 수행하기 위해 파생된 클래스에서 재정의될 수 있습니다. SetRelatedWnd로 설정 된 경우에는 기본 구현에서 관련 창이 업데이트 됩니다.

## <a name="canimationcontrolleronanimationtimerpostupdate"></a><a name="onanimationtimerpostupdate"></a> CAnimationController:: Onpost타이머 Postupdate

애니메이션 업데이트가 완료 된 후 프레임 워크에서 호출 됩니다.

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>설명

이 메서드는 Enableeventhandler를 사용 하 여 타이머 이벤트 처리기를 사용 하도록 설정 하는 경우 호출 됩니다. 애플리케이션별 작업을 수행하기 위해 파생된 클래스에서 재정의될 수 있습니다.

## <a name="canimationcontrolleronanimationtimerpreupdate"></a><a name="onanimationtimerpreupdate"></a> CAnimationController:: OnAnimationTimerPreUpdate

애니메이션 업데이트를 시작 하기 전에 프레임 워크에서 호출 됩니다.

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>설명

이 메서드는 Enableeventhandler를 사용 하 여 타이머 이벤트 처리기를 사용 하도록 설정 하는 경우 호출 됩니다. 애플리케이션별 작업을 수행하기 위해 파생된 클래스에서 재정의될 수 있습니다.

## <a name="canimationcontrolleronanimationtimerrenderingtooslow"></a><a name="onanimationtimerrenderingtooslow"></a> CAnimationController:: OnAnimationTimerRenderingTooSlow

애니메이션의 렌더링 프레임 비율이 최소한의 적절 한 프레임 속도로 떨어질 때 프레임 워크에서 호출 됩니다.

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>매개 변수

*24*<br/>
초당 프레임의 현재 프레임 속도로,

### <a name="remarks"></a>설명

이 메서드는 Enableeventhandler를 사용 하 여 타이머 이벤트 처리기를 사용 하도록 설정 하는 경우 호출 됩니다. 애플리케이션별 작업을 수행하기 위해 파생된 클래스에서 재정의될 수 있습니다. 적절 한 최소 프레임 비율은 IuiSetFrameRateThreshold Timer::를 호출 하 여 지정 합니다.

## <a name="canimationcontrolleronanimationvaluechanged"></a><a name="onanimationvaluechanged"></a> CAnimationController:: OnAnimationValueChanged

애니메이션 변수 값이 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>매개 변수

*pGroup*<br/>
값이 변경 된 애니메이션 개체를 보유 하는 애니메이션 그룹에 대 한 포인터입니다.

*pObject*<br/>
값이 변경 된 애니메이션 변수를 포함 하는 애니메이션 개체에 대 한 포인터입니다.

*variable*<br/>
애니메이션 변수에 대 한 포인터입니다.

*newValue*<br/>
새 값을 지정 합니다.

*prevValue*<br/>
이전 값을 지정 합니다.

### <a name="remarks"></a>설명

이 메서드는 특정 애니메이션 변수 또는 애니메이션 개체에 대해 EnableValueChangedEvent가 호출 된 애니메이션 변수 이벤트를 사용 하도록 설정 하는 경우 호출 됩니다. 애플리케이션별 작업을 수행하기 위해 파생된 클래스에서 재정의될 수 있습니다.

## <a name="canimationcontrolleronbeforeanimationstart"></a><a name="onbeforeanimationstart"></a> CAnimationController:: OnBeforeAnimationStart

애니메이션이 예약 되기 직전에 프레임 워크에서 호출 됩니다.

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>매개 변수

*pGroup*<br/>
애니메이션이 시작 될 애니메이션 그룹에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 호출은 관련 CWnd로 라우팅됩니다. 지정 된 그룹에 대해 애니메이션이 시작 되기 전에 파생 클래스에서 재정의 하 여 추가 작업을 수행할 수 있습니다.

## <a name="canimationcontrolleronhasprioritycancel"></a><a name="onhasprioritycancel"></a> CAnimationController:: OnHasPriorityCancel

일정 충돌을 해결하기 위해 프레임워크에 의해 호출됩니다.

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>매개 변수

*pGroupScheduled*<br/>
현재 예약된 스토리보드를 소유하고 있는 그룹입니다.

*pGroupNew*<br/>
pGroupScheduled에서 소유한 예약된 스토리보드와 충돌을 예약하고 있는 새 스토리보드를 소유하는 그룹입니다.

*priorityEffect*<br/>
pGroupScheduled에 높은 우선 순위가 있는 경우 pGroupNew에서 발생할 수 있는 효과입니다.

### <a name="return-value"></a>반환 값

pGroupNew에서 소유한 스토리보드가 우선인 경우 TRUE를 반환해야 합니다. pGroupScheduled에서 소유한 스토리보드가 우선인 경우 FALSE를 반환해야 합니다.

### <a name="remarks"></a>설명

이 메서드는 CAnimationController::EnablePriorityComparisonHandler를 사용하여 우선 순위 비교 이벤트를 활성화하고 UI_ANIMATION_PHT_CANCEL을 지정하는 경우 호출됩니다. 애플리케이션별 작업을 수행하기 위해 파생된 클래스에서 재정의될 수 있습니다. [충돌 관리](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)에 대 한 자세한 내용은 WINDOWS 애니메이션 API 설명서를 참조 하세요.

## <a name="canimationcontrolleronhasprioritycompress"></a><a name="onhasprioritycompress"></a> CAnimationController:: OnHasPriorityCompress

일정 충돌을 해결하기 위해 프레임워크에 의해 호출됩니다.

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>매개 변수

*pGroupScheduled*<br/>
현재 예약된 스토리보드를 소유하고 있는 그룹입니다.

*pGroupNew*<br/>
pGroupScheduled에서 소유한 예약된 스토리보드와 충돌을 예약하고 있는 새 스토리보드를 소유하는 그룹입니다.

*priorityEffect*<br/>
pGroupScheduled에 높은 우선 순위가 있는 경우 pGroupNew에서 발생할 수 있는 효과입니다.

### <a name="return-value"></a>반환 값

pGroupNew에서 소유한 스토리보드가 우선인 경우 TRUE를 반환해야 합니다. pGroupScheduled에서 소유한 스토리보드가 우선인 경우 FALSE를 반환해야 합니다.

### <a name="remarks"></a>설명

이 메서드는 CAnimationController::EnablePriorityComparisonHandler를 사용하여 우선 순위 비교 이벤트를 활성화하고 UI_ANIMATION_PHT_COMPRESS를 지정하는 경우 호출됩니다. 애플리케이션별 작업을 수행하기 위해 파생된 클래스에서 재정의될 수 있습니다. [충돌 관리](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)에 대 한 자세한 내용은 WINDOWS 애니메이션 API 설명서를 참조 하세요.

## <a name="canimationcontrolleronhaspriorityconclude"></a><a name="onhaspriorityconclude"></a> CAnimationController:: OnHasPriorityConclude

일정 충돌을 해결하기 위해 프레임워크에 의해 호출됩니다.

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>매개 변수

*pGroupScheduled*<br/>
현재 예약된 스토리보드를 소유하고 있는 그룹입니다.

*pGroupNew*<br/>
pGroupScheduled에서 소유한 예약된 스토리보드와 충돌을 예약하고 있는 새 스토리보드를 소유하는 그룹입니다.

*priorityEffect*<br/>
pGroupScheduled에 높은 우선 순위가 있는 경우 pGroupNew에서 발생할 수 있는 효과입니다.

### <a name="return-value"></a>반환 값

pGroupNew에서 소유한 스토리보드가 우선인 경우 TRUE를 반환해야 합니다. pGroupScheduled에서 소유한 스토리보드가 우선인 경우 FALSE를 반환해야 합니다.

### <a name="remarks"></a>설명

이 메서드는 CAnimationController::EnablePriorityComparisonHandler를 사용하여 우선 순위 비교 이벤트를 활성화하고 UI_ANIMATION_PHT_TRIM을 지정하는 경우 호출됩니다. 애플리케이션별 작업을 수행하기 위해 파생된 클래스에서 재정의될 수 있습니다. [충돌 관리](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)에 대 한 자세한 내용은 WINDOWS 애니메이션 API 설명서를 참조 하세요.

## <a name="canimationcontrolleronhasprioritytrim"></a><a name="onhasprioritytrim"></a> CAnimationController:: OnHasPriorityTrim

일정 충돌을 해결하기 위해 프레임워크에 의해 호출됩니다.

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>매개 변수

*pGroupScheduled*<br/>
현재 예약된 스토리보드를 소유하고 있는 그룹입니다.

*pGroupNew*<br/>
pGroupScheduled에서 소유한 예약된 스토리보드와 충돌을 예약하고 있는 새 스토리보드를 소유하는 그룹입니다.

*priorityEffect*<br/>
pGroupScheduled에 높은 우선 순위가 있는 경우 pGroupNew에서 발생할 수 있는 효과입니다.

### <a name="return-value"></a>반환 값

pGroupNew에서 소유한 스토리보드가 우선인 경우 TRUE를 반환해야 합니다. pGroupScheduled에서 소유한 스토리보드가 우선인 경우 FALSE를 반환해야 합니다.

### <a name="remarks"></a>설명

이 메서드는 CAnimationController::EnablePriorityComparisonHandler를 사용하여 우선 순위 비교 이벤트를 활성화하고 UI_ANIMATION_PHT_TRIM을 지정하는 경우 호출됩니다. 애플리케이션별 작업을 수행하기 위해 파생된 클래스에서 재정의될 수 있습니다. [충돌 관리](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)에 대 한 자세한 내용은 WINDOWS 애니메이션 API 설명서를 참조 하세요.

## <a name="canimationcontrolleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a> CAnimationController:: OnStoryboardStatusChanged

스토리 보드 상태가 변경 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>매개 변수

*pGroup*<br/>
상태가 변경 된 storyboard를 소유 하는 애니메이션 그룹에 대 한 포인터입니다.

*newStatus*<br/>
새 상태를 지정 합니다.

*previousStatus*<br/>
이전 상태를 지정 합니다.

### <a name="remarks"></a>설명

이 메서드는 CAnimationController:: EnableStoryboardEventHandler를 사용 하 여 storyboard 이벤트를 사용 하도록 설정 하는 경우 호출 됩니다. 애플리케이션별 작업을 수행하기 위해 파생된 클래스에서 재정의될 수 있습니다.

## <a name="canimationcontrolleronstoryboardupdated"></a><a name="onstoryboardupdated"></a> CAnimationController:: OnStoryboardUpdated

Storyboard가 업데이트 될 때 프레임 워크에서 호출 됩니다.

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>매개 변수

*pGroup*<br/>
스토리 보드를 소유 하는 그룹에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 CAnimationController:: EnableStoryboardEventHandler를 사용 하 여 storyboard 이벤트를 사용 하도록 설정 하는 경우 호출 됩니다. 애플리케이션별 작업을 수행하기 위해 파생된 클래스에서 재정의될 수 있습니다.

## <a name="canimationcontrollerremoveallanimationgroups"></a><a name="removeallanimationgroups"></a> CAnimationController:: RemoveAllAnimationGroups

애니메이션 컨트롤러에서 모든 애니메이션 그룹을 제거 합니다.

```cpp
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>설명

모든 그룹이 삭제 되 고 응용 프로그램 수준에 저장 된 경우 해당 포인터는 무효화 되어야 합니다. 삭제할 그룹에 대 한 CAnimationGroup:: m_bAutodestroyAnimationObjects이 TRUE 이면 해당 그룹에 속한 모든 애니메이션 개체가 삭제 됩니다. 그렇지 않으면 부모 애니메이션 컨트롤러에 대 한 참조가 NULL로 설정 되 고 다른 컨트롤러에 추가 될 수 있습니다.

## <a name="canimationcontrollerremoveanimationgroup"></a><a name="removeanimationgroup"></a> CAnimationController:: Remove애니메이션 그룹

애니메이션 컨트롤러에서 지정 된 ID를 가진 애니메이션 그룹을 제거 합니다.

```cpp
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>매개 변수

*nGroupID*<br/>
애니메이션 그룹 ID를 지정 합니다.

### <a name="remarks"></a>설명

이 메서드는 그룹의 내부 목록에서 애니메이션 그룹을 제거 하 고 삭제 합니다. 따라서 해당 애니메이션 그룹에 대 한 포인터를 저장 한 경우 무효화 되어야 합니다. CAnimationGroup:: m_bAutodestroyAnimationObjects TRUE 이면 해당 그룹에 속한 모든 애니메이션 개체가 삭제 됩니다. 그렇지 않으면 부모 애니메이션 컨트롤러에 대 한 참조가 NULL로 설정 되 고 다른 컨트롤러에 추가 될 수 있습니다.

## <a name="canimationcontrollerremoveanimationobject"></a><a name="removeanimationobject"></a> CAnimationController:: Remove애니메이션 개체

애니메이션 컨트롤러에서 애니메이션 개체를 제거 합니다.

```cpp
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>매개 변수

*pObject*<br/>
애니메이션 개체에 대 한 포인터입니다.

*bNoDelete*<br/>
이 매개 변수가 TRUE 이면 제거 시 개체가 삭제 되지 않습니다.

### <a name="remarks"></a>설명

애니메이션 컨트롤러와 애니메이션 그룹에서 애니메이션 개체를 제거 합니다. 특정 개체에 더 이상 애니메이션을 적용 하지 않아야 하거나 개체를 다른 애니메이션 컨트롤러로 이동 해야 하는 경우이 함수를 호출 합니다. 마지막 사례에서 bNoDelete는 TRUE 여야 합니다.

## <a name="canimationcontrollerremovetransitions"></a><a name="removetransitions"></a> CAnimationController:: RemoveTransitions

지정 된 그룹에 속한 애니메이션 개체에서 전환을 제거 합니다.

```cpp
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>매개 변수

*nGroupID*<br/>
그룹 ID를 지정 합니다.

### <a name="remarks"></a>설명

그룹은 애니메이션 개체를 반복 하 고 각 애니메이션 개체에 대해 ClearTransitions (FALSE)을 호출 합니다. 이 메서드는 애니메이션이 예약 된 후 프레임 워크에서 호출 됩니다.

## <a name="canimationcontrollerschedulegroup"></a><a name="schedulegroup"></a> CAnimationController:: ScheduleGroup

애니메이션을 예약 합니다.

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>매개 변수

*nGroupID*<br/>
예약할 애니메이션 그룹 ID를 지정 합니다.

*time*<br/>
예약할 시간을 지정 합니다.

### <a name="return-value"></a>반환 값

애니메이션이 성공적으로 예약 되었으면 TRUE입니다. Storyboard가 만들어지지 않았거나 다른 오류가 발생 하면 FALSE입니다.

### <a name="remarks"></a>설명

BScheduleNow 매개 변수를 ScheduleGroup로 설정 하 여 AnimateGroup를 호출 해야 합니다. IuiGetTime Timer::에서 가져온 원하는 애니메이션 시간을 지정할 수 있습니다. Time 매개 변수가 0.0 이면 현재 시간에 대해 애니메이션이 예약 됩니다.

## <a name="canimationcontrollersetrelatedwnd"></a><a name="setrelatedwnd"></a> CAnimationController:: SetRelatedWnd

애니메이션 컨트롤러와 창 간의 관계를 설정 합니다.

```cpp
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>매개 변수

*pWnd*<br/>
설정할 창 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

관련 CWnd 개체가 설정 된 경우 애니메이션 컨트롤러는 애니메이션 관리자의 상태가 변경 되거나 타이머 사후 업데이트 이벤트가 발생 했을 때 자동으로 업데이트 (WM_PAINT 메시지 보내기) 할 수 있습니다.

## <a name="canimationcontrollerupdateanimationmanager"></a><a name="updateanimationmanager"></a> CAnimationController:: Update' 관리자 '

모든 애니메이션 변수의 값을 업데이트 하도록 애니메이션 관리자에 게 지시 합니다.

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>설명

이 메서드를 호출 하면 애니메이션 관리자가 현재 시간으로 이동 하 고, 필요에 따라 storyboard 상태를 변경 하 고, 애니메이션 변수를 적절 한 보간된 값으로 업데이트 합니다. 내부적으로이 메서드는 IuiGetTime Timer:: (timeNow) 및 Iui Manager:: Update (timeNow)를 호출 합니다. 파생 클래스에서이 메서드를 재정의 하 여이 동작을 사용자 지정 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)
