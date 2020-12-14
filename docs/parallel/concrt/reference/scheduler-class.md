---
description: '자세한 정보: Scheduler 클래스'
title: Scheduler 클래스
ms.date: 11/04/2016
f1_keywords:
- Scheduler
- CONCRT/concurrency::Scheduler
- CONCRT/concurrency::Scheduler::Scheduler
- CONCRT/concurrency::Scheduler::Attach
- CONCRT/concurrency::Scheduler::Create
- CONCRT/concurrency::Scheduler::CreateScheduleGroup
- CONCRT/concurrency::Scheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::Scheduler::GetPolicy
- CONCRT/concurrency::Scheduler::Id
- CONCRT/concurrency::Scheduler::IsAvailableLocation
- CONCRT/concurrency::Scheduler::Reference
- CONCRT/concurrency::Scheduler::RegisterShutdownEvent
- CONCRT/concurrency::Scheduler::Release
- CONCRT/concurrency::Scheduler::ResetDefaultSchedulerPolicy
- CONCRT/concurrency::Scheduler::ScheduleTask
- CONCRT/concurrency::Scheduler::SetDefaultSchedulerPolicy
helpviewer_keywords:
- Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
ms.openlocfilehash: 2a509017c84f7f6c845c153c8c187f5885839035
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188900"
---
# <a name="scheduler-class"></a>Scheduler 클래스

동시성 런타임 스케줄러에 대한 추상화를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class Scheduler;
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[Scheduler](#ctor)|클래스의 개체는 `Scheduler` 팩터리 메서드를 사용 하거나 암시적 으로만 만들 수 있습니다.|
|[~ Scheduler 소멸자](#dtor)|클래스의 개체는 `Scheduler` 모든 외부 참조가 존재 하지 않는 경우 암시적으로 제거 됩니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[연결](#attach)|스케줄러를 호출 컨텍스트에 연결 합니다. 이 메서드가 반환 된 후에는 호출 컨텍스트가 스케줄러에 의해 관리 되 고 스케줄러는 현재 스케줄러가 됩니다.|
|[만들기](#create)|매개 변수에서 동작을 설명 하는 새 스케줄러를 만들고 `_Policy` , 스케줄러에 초기 참조를 배치 하 고,이에 대 한 포인터를 반환 합니다.|
|[CreateScheduleGroup](#createschedulegroup)|오버로드됨. 스케줄러 내에 새 일정 그룹을 만듭니다. 매개 변수를 사용 하는 버전은 `_Placement` 새로 만든 일정 그룹 내의 태스크가 해당 매개 변수로 지정 된 위치에서 실행 될 때 편향 되도록 합니다.|
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|스케줄러에 대 한 현재 가상 프로세서 수를 반환 합니다.|
|[GetPolicy](#getpolicy)|스케줄러를 만든 정책의 복사본을 반환 합니다.|
|[ID](#id)|스케줄러에 대 한 고유 식별자를 반환 합니다.|
|[IsAvailableLocation](#isavailablelocation)|지정 된 위치를 스케줄러에서 사용할 수 있는지 여부를 확인 합니다.|
|[참조](#reference)|스케줄러 참조 횟수를 증가 시킵니다.|
|[RegisterShutdownEvent](#registershutdownevent)|`_Event`스케줄러를 종료 하 고 자체를 소멸 시킬 때 매개 변수에 전달 된 Windows 이벤트 핸들이 신호를 받도록 합니다. 이벤트가 신호를 받을 때 스케줄러에 예약 된 모든 작업이 완료 됩니다. 이 메서드를 통해 여러 종료 이벤트를 등록할 수 있습니다.|
|[릴리스](#release)|스케줄러 참조 횟수를 감소시킵니다.|
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|기본 스케줄러 정책을 런타임 기본값으로 다시 설정 합니다. 다음에 기본 스케줄러를 만들 때 런타임 기본 정책 설정이 사용 됩니다.|
|[ScheduleTask](#scheduletask)|오버로드됨. 스케줄러 내에서 경량 작업을 예약 합니다. 간단한 작업은 런타임에 의해 결정되는 일정 그룹에 배치됩니다. `_Placement` 매개 변수를 사용하는 버전은 작업이 지정된 위치에서 실행되도록 합니다.|
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|사용자 정의 정책을 사용 하 여 기본 스케줄러를 만들 수 있습니다. 이 메서드는 프로세스 내에 기본 스케줄러가 없는 경우에만 호출할 수 있습니다. 기본 정책을 설정한 후에는 `SetDefaultSchedulerPolicy` 또는 [ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy) 메서드에 대 한 다음 유효한 호출까지 적용 됩니다.|

## <a name="remarks"></a>설명

동시성 런타임 scheduler는 응용 프로그램에서 큐에 대기 중인 작업을 실행 하기 위해 스레드와 같은 운영 체제 실행 컨텍스트에 매핑되는 실행 컨텍스트를 사용 합니다. 언제 든 지 스케줄러의 동시성 수준은 리소스 관리자에 의해 부여 된 가상 프로세서의 수와 동일 합니다. 가상 프로세서는 처리 리소스에 대 한 추상화 이며 기본 시스템의 하드웨어 스레드에 매핑됩니다. 단일 스케줄러 컨텍스트는 지정 된 시간에 가상 프로세서에서 실행할 수 있습니다.

동시성 런타임는 프로세스 당 기본 스케줄러를 만들어 병렬 작업을 실행 합니다. 또한 사용자 고유의 스케줄러 인스턴스를 만들고이 클래스를 사용 하 여 조작할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Scheduler`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="attach"></a><a name="attach"></a> 첨부

스케줄러를 호출 컨텍스트에 연결 합니다. 이 메서드가 반환 된 후에는 호출 컨텍스트가 스케줄러에 의해 관리 되 고 스케줄러는 현재 스케줄러가 됩니다.

```cpp
virtual void Attach() = 0;
```

### <a name="remarks"></a>설명

스케줄러를 연결 하면 암시적으로 스케줄러에 참조가 배치 됩니다.

나중에 스케줄러를 종료할 수 있도록 [currentscheduler::D etach](currentscheduler-class.md#detach) 메서드를 호출 해야 합니다.

이 메서드가 다른 스케줄러에 이미 연결 되어 있는 컨텍스트에서 호출 되는 경우 기존 스케줄러는 이전 스케줄러로 기억 되 고 새로 만든 스케줄러는 현재 스케줄러가 됩니다. `CurrentScheduler::Detach`이후 시점에서 메서드를 호출 하면 이전 스케줄러가 현재 스케줄러로 복원 됩니다.

이 스케줄러가 호출 컨텍스트의 현재 scheduler 인 경우이 메서드는 [improper_scheduler_attach](improper-scheduler-attach-class.md) 예외를 throw 합니다.

## <a name="create"></a><a name="create"></a> 만들기

매개 변수에서 동작을 설명 하는 새 스케줄러를 만들고 `_Policy` , 스케줄러에 초기 참조를 배치 하 고,이에 대 한 포인터를 반환 합니다.

```cpp
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>매개 변수

*_Policy*<br/>
새로 만든 스케줄러의 동작을 설명 하는 스케줄러 정책입니다.

### <a name="return-value"></a>반환 값

새로 만든 스케줄러에 대 한 포인터입니다. 이 `Scheduler` 개체에는 초기 참조 수가 배치 되어 있습니다.

### <a name="remarks"></a>설명

메서드를 사용 하 여 스케줄러를 만든 후에는 `Create` `Release` 앞의 특정 시점에서 메서드를 호출 하 여 초기 참조 횟수를 제거 하 고 스케줄러를 종료할 수 있도록 해야 합니다.

이 메서드를 사용 하 여 만든 스케줄러는 호출 컨텍스트에 연결 되지 않습니다. [Attach](#attach) 메서드를 사용 하 여 컨텍스트에 연결할 수 있습니다.

이 메서드는 [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) 및 [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)를 포함 하 여 다양 한 예외를 throw 할 수 있습니다.

## <a name="createschedulegroup"></a><a name="createschedulegroup"></a> CreateScheduleGroup

스케줄러 내에 새 일정 그룹을 만듭니다. 매개 변수를 사용 하는 버전은 `_Placement` 새로 만든 일정 그룹 내의 태스크가 해당 매개 변수로 지정 된 위치에서 실행 될 때 편향 되도록 합니다.

```cpp
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```

### <a name="parameters"></a>매개 변수

*_Placement*<br/>
일정 그룹 내의 태스크가에서 실행 되는 것에 해당 하는 위치에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

새로 만든 일정 그룹에 대 한 포인터입니다. 이 `ScheduleGroup` 개체에는 초기 참조 수가 배치 되어 있습니다.

### <a name="remarks"></a>설명

작업 예약을 완료 한 후에는 일정 그룹에서 [Release](schedulegroup-class.md#release) 메서드를 호출 해야 합니다. 스케줄러는 대기 중인 모든 작업이 완료 되 면 일정 그룹을 삭제 합니다.

이 스케줄러를 명시적으로 만든 경우 스케줄러에서 참조를 해제 하기 전에 해당 스케줄러 내의 일정 그룹에 대 한 모든 참조를 해제 해야 합니다.

## <a name="getnumberofvirtualprocessors"></a><a name="getnumberofvirtualprocessors"></a> GetNumberOfVirtualProcessors

스케줄러에 대 한 현재 가상 프로세서 수를 반환 합니다.

```cpp
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```

### <a name="return-value"></a>반환 값

스케줄러에 대 한 현재 가상 프로세서 수입니다.

## <a name="getpolicy"></a><a name="getpolicy"></a> GetPolicy

스케줄러를 만든 정책의 복사본을 반환 합니다.

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>반환 값

스케줄러를 만든 정책의 복사본입니다.

## <a name="id"></a><a name="id"></a> A-id

스케줄러에 대 한 고유 식별자를 반환 합니다.

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>반환 값

스케줄러에 대 한 고유 식별자입니다.

## <a name="isavailablelocation"></a><a name="isavailablelocation"></a> IsAvailableLocation

지정 된 위치를 스케줄러에서 사용할 수 있는지 여부를 확인 합니다.

```cpp
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```

### <a name="parameters"></a>매개 변수

*_Placement*<br/>
스케줄러를 쿼리 하는 위치에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

인수로 지정 된 위치를 `_Placement` 스케줄러에서 사용할 수 있는지 여부를 나타냅니다.

### <a name="remarks"></a>설명

반환 값은 지정된 위치를 사용할 수 있는지 여부의 순간 샘플링입니다. 여러 스케줄러가 있으면 동적 자원 관리에서 어느 시점에 스케줄러의 리소스를 추가하거나 제거할 수 있습니다. 이 경우 지정된 위치의 가용성이 변경될 수 있습니다.

## <a name="reference"></a><a name="reference"></a> 참조일

스케줄러 참조 횟수를 증가 시킵니다.

```cpp
virtual unsigned int Reference() = 0 ;
```

### <a name="return-value"></a>반환 값

새로 증가 된 참조 수입니다.

### <a name="remarks"></a>설명

이는 일반적으로 컴퍼지션에 대 한 스케줄러의 수명을 관리 하는 데 사용 됩니다. 스케줄러의 참조 횟수가 0이 되면 스케줄러가 종료되고 스케줄러의 모든 작업이 완료된 후 자체적으로 소멸합니다.

메서드는 메서드를 호출 [](improper-scheduler-reference-class.md) 하기 전의 참조 횟수가 `Reference` 0이 고 스케줄러가 소유 하지 않은 컨텍스트에서 호출 되는 경우 improper_scheduler_reference 예외를 throw 합니다.

## <a name="registershutdownevent"></a><a name="registershutdownevent"></a> RegisterShutdownEvent

`_Event`스케줄러를 종료 하 고 자체를 소멸 시킬 때 매개 변수에 전달 된 Windows 이벤트 핸들이 신호를 받도록 합니다. 이벤트가 신호를 받을 때 스케줄러에 예약 된 모든 작업이 완료 됩니다. 이 메서드를 통해 여러 종료 이벤트를 등록할 수 있습니다.

```cpp
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```

### <a name="parameters"></a>매개 변수

*_Event*<br/>
스케줄러가 종료 되 고 자체적으로 소멸 될 때 런타임에서 신호를 받는 Windows 이벤트 개체에 대 한 핸들입니다.

## <a name="release"></a><a name="release"></a> 릴리스

스케줄러 참조 횟수를 감소시킵니다.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>반환 값

새로 감소 한 참조 수입니다.

### <a name="remarks"></a>설명

이는 일반적으로 컴퍼지션에 대 한 스케줄러의 수명을 관리 하는 데 사용 됩니다. 스케줄러의 참조 횟수가 0이 되면 스케줄러가 종료되고 스케줄러의 모든 작업이 완료된 후 자체적으로 소멸합니다.

## <a name="resetdefaultschedulerpolicy"></a><a name="resetdefaultschedulerpolicy"></a> ResetDefaultSchedulerPolicy

기본 스케줄러 정책을 런타임 기본값으로 다시 설정 합니다. 다음에 기본 스케줄러를 만들 때 런타임 기본 정책 설정이 사용 됩니다.

```cpp
static void __cdecl ResetDefaultSchedulerPolicy();
```

### <a name="remarks"></a>설명

이 메서드는 프로세스 내에 기본 스케줄러가 있는 동안 호출 될 수 있습니다. 기존 기본 스케줄러의 정책에는 영향을 주지 않습니다. 그러나 기본 스케줄러를 종료 하 고 나중에 새 기본값을 만들어야 하는 경우 새 스케줄러는 런타임 기본 정책 설정을 사용 합니다.

## <a name="scheduler"></a><a name="ctor"></a> 일정표

클래스의 개체는 `Scheduler` 팩터리 메서드를 사용 하거나 암시적 으로만 만들 수 있습니다.

```cpp
Scheduler();
```

### <a name="remarks"></a>설명

스케줄러를 호출 컨텍스트에 연결 해야 하는 다양 한 런타임 함수를 활용할 때 프로세스의 기본 스케줄러가 암시적으로 생성 됩니다. 클래스 내의 메서드와 `CurrentScheduler` PPL 및 에이전트 계층의 기능은 일반적으로 암시적 첨부 파일을 수행 합니다.

메서드나 메서드를 통해 명시적으로 스케줄러를 만들 수도 있습니다 `CurrentScheduler::Create` `Scheduler::Create` .

## <a name="scheduler"></a><a name="dtor"></a> ~ 스케줄러

클래스의 개체는 `Scheduler` 모든 외부 참조가 존재 하지 않는 경우 암시적으로 제거 됩니다.

```cpp
virtual ~Scheduler();
```

## <a name="scheduletask"></a><a name="scheduletask"></a> ScheduleTask

스케줄러 내에서 경량 작업을 예약 합니다. 간단한 작업은 런타임에 의해 결정되는 일정 그룹에 배치됩니다. `_Placement` 매개 변수를 사용하는 버전은 작업이 지정된 위치에서 실행되도록 합니다.

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;

virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement) = 0;
```

### <a name="parameters"></a>매개 변수

*_Proc*<br/>
경량 작업 본문을 수행 하기 위해 실행 하는 함수에 대 한 포인터입니다.

*_Data*<br/>
작업 본문에 매개 변수로 전달 될 데이터에 대 한 void 포인터입니다.

*_Placement*<br/>
간단한 작업이 실행될 수 있는 위치에 대한 참조입니다.

## <a name="setdefaultschedulerpolicy"></a><a name="setdefaultschedulerpolicy"></a> SetDefaultSchedulerPolicy

사용자 정의 정책을 사용 하 여 기본 스케줄러를 만들 수 있습니다. 이 메서드는 프로세스 내에 기본 스케줄러가 없는 경우에만 호출할 수 있습니다. 기본 정책을 설정한 후에는 `SetDefaultSchedulerPolicy` 또는 [ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy) 메서드에 대 한 다음 유효한 호출까지 적용 됩니다.

```cpp
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>매개 변수

*_Policy*<br/>
기본 스케줄러 정책으로 설정할 정책입니다.

### <a name="remarks"></a>설명

`SetDefaultSchedulerPolicy`프로세스 내에 기본 스케줄러가 이미 있을 때 메서드를 호출 하면 런타임에서 [default_scheduler_exists](default-scheduler-exists-class.md) 예외가 throw 됩니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[Scheduler 클래스](scheduler-class.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[작업 Scheduler](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
