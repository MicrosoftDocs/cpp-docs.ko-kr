---
description: '자세한 정보: CurrentScheduler 클래스'
title: CurrentScheduler 클래스
ms.date: 11/04/2016
f1_keywords:
- CurrentScheduler
- CONCRT/concurrency::CurrentScheduler
- CONCRT/concurrency::CurrentScheduler::Create
- CONCRT/concurrency::CurrentScheduler::CreateScheduleGroup
- CONCRT/concurrency::CurrentScheduler::Detach
- CONCRT/concurrency::CurrentScheduler::Get
- CONCRT/concurrency::CurrentScheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::CurrentScheduler::GetPolicy
- CONCRT/concurrency::CurrentScheduler::Id
- CONCRT/concurrency::CurrentScheduler::IsAvailableLocation
- CONCRT/concurrency::CurrentScheduler::RegisterShutdownEvent
- CONCRT/concurrency::CurrentScheduler::ScheduleTask
helpviewer_keywords:
- CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
ms.openlocfilehash: d2456513dba05f8e38035eb96709e540cb781629
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115237"
---
# <a name="currentscheduler-class"></a>CurrentScheduler 클래스

호출 컨텍스트와 연결된 현재 스케줄러에 대한 추상화를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class CurrentScheduler;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|Description|
|----------|-----------------|
|[만들기](#create)|매개 변수에서 동작을 설명 하는 새 스케줄러를 만들어 `_Policy` 호출 컨텍스트에 연결 합니다. 새로 만든 스케줄러는 호출 하는 컨텍스트에 대 한 현재 스케줄러가 됩니다.|
|[CreateScheduleGroup](#createschedulegroup)|오버로드됨. 호출 컨텍스트와 연결 된 스케줄러 내에 새 일정 그룹을 만듭니다. 매개 변수를 사용 하는 버전은 `_Placement` 새로 만든 일정 그룹 내의 태스크가 해당 매개 변수로 지정 된 위치에서 실행 될 때 편향 되도록 합니다.|
|[분리](#detach)|호출 컨텍스트에서 현재 스케줄러를 분리 하 고 이전에 연결 된 스케줄러를 현재 스케줄러로 복원 합니다 (있는 경우). 이 메서드가 반환 된 후에는 또는 메서드를 사용 하 여 컨텍스트에 이전에 연결 된 스케줄러에서 호출 컨텍스트를 관리 `CurrentScheduler::Create` 합니다 `Scheduler::Attach` .|
|[가져오기](#get)|호출 컨텍스트와 연결 된 스케줄러에 대 한 포인터를 반환 합니다. 현재 스케줄러 라고도 합니다.|
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|호출 컨텍스트와 연결 된 스케줄러의 현재 가상 프로세서 수를 반환 합니다.|
|[GetPolicy](#getpolicy)|현재 스케줄러를 만든 정책의 복사본을 반환 합니다.|
|[ID](#id)|현재 스케줄러에 대 한 고유 식별자를 반환 합니다.|
|[IsAvailableLocation](#isavailablelocation)|현재 스케줄러에서 지정된 위치를 사용할 수 있는지를 확인합니다.|
|[RegisterShutdownEvent](#registershutdownevent)|`_ShutdownEvent`현재 컨텍스트와 연결 된 스케줄러를 종료 하 고 자체를 소멸 시킬 때 매개 변수에 전달 된 Windows 이벤트 핸들이 신호를 받도록 합니다. 이벤트가 신호를 받을 때 스케줄러에 예약 된 모든 작업이 완료 됩니다. 이 메서드를 통해 여러 종료 이벤트를 등록할 수 있습니다.|
|[ScheduleTask](#scheduletask)|오버로드됨. 호출 컨텍스트와 연결 된 스케줄러 내에서 경량 작업을 예약 합니다. 간단한 작업은 런타임에 의해 결정되는 일정 그룹에 배치됩니다. `_Placement` 매개 변수를 사용하는 버전은 작업이 지정된 위치에서 실행되도록 합니다.|

## <a name="remarks"></a>설명

호출 컨텍스트와 연결 된 스케줄러 ( [scheduler](scheduler-class.md)참조)가 없는 경우 클래스 내의 많은 메서드가 `CurrentScheduler` 프로세스의 기본 스케줄러를 첨부 합니다. 이는 이러한 호출 중에 프로세스의 기본 스케줄러가 생성 됨을 의미할 수도 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CurrentScheduler`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="create"></a><a name="create"></a> 만들기

매개 변수에서 동작을 설명 하는 새 스케줄러를 만들어 `_Policy` 호출 컨텍스트에 연결 합니다. 새로 만든 스케줄러는 호출 하는 컨텍스트에 대 한 현재 스케줄러가 됩니다.

```cpp
static void __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>매개 변수

*_Policy*<br/>
새로 만든 스케줄러의 동작을 설명 하는 스케줄러 정책입니다.

### <a name="remarks"></a>설명

스케줄러를 호출 컨텍스트에 첨부 하면 암시적으로 스케줄러에 참조 횟수가 추가 됩니다.

메서드를 사용 하 여 스케줄러를 만든 후에는 `Create` 나중에 [etach](#detach) 메서드를:D 호출 하 여 스케줄러가 종료 될 수 있도록 해야 합니다.

이 메서드가 다른 스케줄러에 이미 연결 되어 있는 컨텍스트에서 호출 되는 경우 기존 스케줄러는 이전 스케줄러로 기억 되 고 새로 만든 스케줄러는 현재 스케줄러가 됩니다. `CurrentScheduler::Detach`이후 시점에서 메서드를 호출 하면 이전 스케줄러가 현재 스케줄러로 복원 됩니다.

이 메서드는 [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) 및 [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)를 포함 하 여 다양 한 예외를 throw 할 수 있습니다.

## <a name="createschedulegroup"></a><a name="createschedulegroup"></a> CreateScheduleGroup

호출 컨텍스트와 연결 된 스케줄러 내에 새 일정 그룹을 만듭니다. 매개 변수를 사용 하는 버전은 `_Placement` 새로 만든 일정 그룹 내의 태스크가 해당 매개 변수로 지정 된 위치에서 실행 될 때 편향 되도록 합니다.

```cpp
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```

### <a name="parameters"></a>매개 변수

*_Placement*<br/>
일정 그룹 내의 태스크가에서 실행 될 때 편향 되는 위치에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

새로 만든 일정 그룹에 대 한 포인터입니다. 이 `ScheduleGroup` 개체에는 초기 참조 수가 배치 되어 있습니다.

### <a name="remarks"></a>설명

이 메서드를 사용하면 현재 호출 컨텍스트와 연결된 스케줄러가 없는 경우 프로세스의 기본 스케줄러가 생성되고 호출 컨텍스트에 연결됩니다.

작업 예약을 완료 한 후에는 일정 그룹에서 [Release](schedulegroup-class.md#release) 메서드를 호출 해야 합니다. 스케줄러는 대기 중인 모든 작업이 완료 되 면 일정 그룹을 삭제 합니다.

이 스케줄러를 명시적으로 만든 경우에는 현재 컨텍스트를 분리 하 여 스케줄러에서 참조를 해제 하기 전에 해당 스케줄러 내에서 일정 그룹에 대 한 모든 참조를 해제 해야 합니다.

## <a name="detach"></a><a name="detach"></a> 분리

호출 컨텍스트에서 현재 스케줄러를 분리 하 고 이전에 연결 된 스케줄러를 현재 스케줄러로 복원 합니다 (있는 경우). 이 메서드가 반환 된 후에는 또는 메서드를 사용 하 여 컨텍스트에 이전에 연결 된 스케줄러에서 호출 컨텍스트를 관리 `CurrentScheduler::Create` 합니다 `Scheduler::Attach` .

```cpp
static void __cdecl Detach();
```

### <a name="remarks"></a>설명

`Detach`메서드는 스케줄러에서 참조 횟수를 암시적으로 제거 합니다.

호출 컨텍스트에 연결 된 스케줄러가 없는 경우이 메서드를 호출 하면 [scheduler_not_attached](scheduler-not-attached-class.md) 예외가 발생 합니다.

스케줄러에서 내부 및 관리 되는 컨텍스트에서이 메서드를 호출 하거나 [scheduler:: Attach](scheduler-class.md#attach) 또는 [Currentscheduler:: Create](#create) 메서드 이외의 메서드를 사용 하 여 연결 된 컨텍스트를 호출 하면 [improper_scheduler_detach](improper-scheduler-detach-class.md) 예외가 throw 됩니다.

## <a name="get"></a><a name="get"></a> 가져오기

호출 컨텍스트와 연결 된 스케줄러에 대 한 포인터를 반환 합니다. 현재 스케줄러 라고도 합니다.

```cpp
static Scheduler* __cdecl Get();
```

### <a name="return-value"></a>반환 값

호출 컨텍스트 (현재 스케줄러)와 연결 된 스케줄러에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드를 사용하면 현재 호출 컨텍스트와 연결된 스케줄러가 없는 경우 프로세스의 기본 스케줄러가 생성되고 호출 컨텍스트에 연결됩니다. 이 메서드에서 반환 하는 개체에 추가 참조가 배치 되지 않습니다 `Scheduler` .

## <a name="getnumberofvirtualprocessors"></a><a name="getnumberofvirtualprocessors"></a> GetNumberOfVirtualProcessors

호출 컨텍스트와 연결 된 스케줄러의 현재 가상 프로세서 수를 반환 합니다.

```cpp
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```

### <a name="return-value"></a>반환 값

스케줄러가 호출 컨텍스트와 연결 된 경우 해당 스케줄러에 대 한 현재 가상 프로세서 수입니다. 그렇지 않으면 값 `-1` 입니다.

### <a name="remarks"></a>설명

호출 컨텍스트가 스케줄러에 아직 연결 되지 않은 경우이 메서드는 스케줄러 첨부 파일을 생성 하지 않습니다.

이 메서드의 반환 값은 호출 컨텍스트와 연결 된 스케줄러의 가상 프로세서 수에 대 한 즉각적인 샘플링입니다. 이 값은 반환되는 순간 부실 값이 될 수 있습니다.

## <a name="getpolicy"></a><a name="getpolicy"></a> GetPolicy

현재 스케줄러를 만든 정책의 복사본을 반환 합니다.

```cpp
static SchedulerPolicy __cdecl GetPolicy();
```

### <a name="return-value"></a>반환 값

현재 스케줄러를 만든 정책의 복사본입니다.

### <a name="remarks"></a>설명

이 메서드를 사용하면 현재 호출 컨텍스트와 연결된 스케줄러가 없는 경우 프로세스의 기본 스케줄러가 생성되고 호출 컨텍스트에 연결됩니다.

## <a name="id"></a><a name="id"></a> A-id

현재 스케줄러에 대 한 고유 식별자를 반환 합니다.

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>반환 값

스케줄러가 호출 컨텍스트와 연결 된 경우 해당 스케줄러에 대 한 고유 식별자입니다. 그렇지 않으면 값 `-1` 입니다.

### <a name="remarks"></a>설명

호출 컨텍스트가 스케줄러에 아직 연결 되지 않은 경우이 메서드는 스케줄러 첨부 파일을 생성 하지 않습니다.

## <a name="isavailablelocation"></a><a name="isavailablelocation"></a> IsAvailableLocation

현재 스케줄러에서 지정된 위치를 사용할 수 있는지를 확인합니다.

```cpp
static bool __cdecl IsAvailableLocation(const location& _Placement);
```

### <a name="parameters"></a>매개 변수

*_Placement*<br/>
현재 스케줄러를 쿼리하는 위치에 대한 참조입니다.

### <a name="return-value"></a>반환 값

`_Placement` 인수로 지정된 위치를 현재 스케줄러에서 사용할 수 있는지 여부를 나타냅니다.

### <a name="remarks"></a>설명

호출 컨텍스트가 스케줄러에 아직 연결 되지 않은 경우이 메서드는 스케줄러 첨부 파일을 생성 하지 않습니다.

반환 값은 지정된 위치를 사용할 수 있는지 여부의 순간 샘플링입니다. 여러 스케줄러가 있으면 동적 자원 관리에서 어느 시점에 스케줄러의 리소스를 추가하거나 제거할 수 있습니다. 이 경우 지정된 위치의 가용성이 변경될 수 있습니다.

## <a name="registershutdownevent"></a><a name="registershutdownevent"></a> RegisterShutdownEvent

`_ShutdownEvent`현재 컨텍스트와 연결 된 스케줄러를 종료 하 고 자체를 소멸 시킬 때 매개 변수에 전달 된 Windows 이벤트 핸들이 신호를 받도록 합니다. 이벤트가 신호를 받을 때 스케줄러에 예약 된 모든 작업이 완료 됩니다. 이 메서드를 통해 여러 종료 이벤트를 등록할 수 있습니다.

```cpp
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```

### <a name="parameters"></a>매개 변수

*_ShutdownEvent*<br/>
현재 컨텍스트와 연결 된 스케줄러를 종료 하 고 자체를 소멸 시킬 때 런타임에 의해 신호를 받는 Windows 이벤트 개체에 대 한 핸들입니다.

### <a name="remarks"></a>설명

호출 컨텍스트에 연결 된 스케줄러가 없는 경우이 메서드를 호출 하면 [scheduler_not_attached](scheduler-not-attached-class.md) 예외가 발생 합니다.

## <a name="scheduletask"></a><a name="scheduletask"></a> ScheduleTask

호출 컨텍스트와 연결 된 스케줄러 내에서 경량 작업을 예약 합니다. 간단한 작업은 런타임에 의해 결정되는 일정 그룹에 배치됩니다. `_Placement` 매개 변수를 사용하는 버전은 작업이 지정된 위치에서 실행되도록 합니다.

```cpp
static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data);

static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement);
```

### <a name="parameters"></a>매개 변수

*_Proc*<br/>
경량 작업 본문을 수행 하기 위해 실행 하는 함수에 대 한 포인터입니다.

*_Data*<br/>
작업 본문에 매개 변수로 전달 될 데이터에 대 한 void 포인터입니다.

*_Placement*<br/>
간단한 작업이 실행될 수 있는 위치에 대한 참조입니다.

### <a name="remarks"></a>설명

이 메서드를 사용하면 현재 호출 컨텍스트와 연결된 스케줄러가 없는 경우 프로세스의 기본 스케줄러가 생성되고 호출 컨텍스트에 연결됩니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[Scheduler 클래스](scheduler-class.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[작업 Scheduler](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
