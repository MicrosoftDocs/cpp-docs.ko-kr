---
description: '자세히 알아보기: IScheduler Structure'
title: IScheduler 구조체
ms.date: 11/04/2016
f1_keywords:
- IScheduler
- CONCRTRM/concurrency::IScheduler
- CONCRTRM/concurrency::IScheduler::IScheduler::AddVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::GetId
- CONCRTRM/concurrency::IScheduler::IScheduler::GetPolicy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyBusy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyIdle
- CONCRTRM/concurrency::IScheduler::IScheduler::RemoveVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::Statistics
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
ms.openlocfilehash: 3a99ea5041c9d1146bb2247c1dcac54ff2fb7cf1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334462"
---
# <a name="ischeduler-structure"></a>IScheduler 구조체

작업 스케줄러의 추상화에 대한 인터페이스입니다. 동시성 런타임의 리소스 관리자는 이 인터페이스를 사용하여 작업 스케줄러와 통신합니다.

## <a name="syntax"></a>구문

```cpp
struct IScheduler;
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IScheduler:: AddVirtualProcessors](#addvirtualprocessors)|사용할 가상 프로세서 루트 집합을 스케줄러에 제공 합니다. 각 `IVirtualProcessorRoot` 인터페이스는 스케줄러를 대신해 서 작업을 수행할 수 있는 단일 스레드를 실행할 수 있는 권한을 나타냅니다.|
|[IScheduler:: GetId](#getid)|스케줄러에 대 한 고유 식별자를 반환 합니다.|
|[IScheduler:: GetPolicy](#getpolicy)|스케줄러 정책의 복사본을 반환 합니다. 스케줄러 정책에 대 한 자세한 내용은 [SchedulerPolicy](schedulerpolicy-class.md)를 참조 하세요.|
|[IScheduler:: NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|현재 배열의 가상 프로세서 루트 집합으로 표시 된 하드웨어 스레드를 `ppVirtualProcessorRoots` 다른 스케줄러에서 사용 하 고 있음을이 스케줄러에 알립니다.|
|[IScheduler:: NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|배열의 가상 프로세서 루트 집합으로 표시 된 하드웨어 스레드를 `ppVirtualProcessorRoots` 다른 스케줄러에서 사용 하 고 있지 않는다는 것을이 스케줄러에 알립니다.|
|[IScheduler:: RemoveVirtualProcessors](#removevirtualprocessors)|이전에이 스케줄러에 할당 된 가상 프로세서 루트의 제거를 시작 합니다.|
|[IScheduler:: Statistics](#statistics)|작업 도착 및 완료 비율과 관련 된 정보를 제공 하 고 스케줄러에 대 한 큐 길이를 변경 합니다.|

## <a name="remarks"></a>설명

리소스 관리자와 통신 하는 사용자 지정 스케줄러를 구현 하는 경우 인터페이스의 구현을 제공 해야 합니다 `IScheduler` . 이 인터페이스는 스케줄러와 리소스 관리자 간의 양방향 통신 채널의 한쪽 끝입니다. 다른 end는 `IResourceManager` 리소스 관리자에서 구현 하는 및 인터페이스로 표시 됩니다 `ISchedulerProxy` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IScheduler`

## <a name="requirements"></a>요구 사항

**헤더:** concrtrm. h

**네임 스페이스:** 동시성

## <a name="ischeduleraddvirtualprocessors-method"></a><a name="addvirtualprocessors"></a> IScheduler:: AddVirtualProcessors 메서드

사용할 가상 프로세서 루트 집합을 스케줄러에 제공 합니다. 각 `IVirtualProcessorRoot` 인터페이스는 스케줄러를 대신해 서 작업을 수행할 수 있는 단일 스레드를 실행할 수 있는 권한을 나타냅니다.

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>매개 변수

*ppVirtualProcessorRoots*<br/>
`IVirtualProcessorRoot`스케줄러에 추가 되는 가상 프로세서 루트를 나타내는 인터페이스의 배열입니다.

*count*<br/>
`IVirtualProcessorRoot`배열에 있는 인터페이스의 수입니다.

### <a name="remarks"></a>설명

리소스 관리자는 메서드를 호출 `AddVirtualProcessor` 하 여 초기 가상 프로세서 루트 집합을 스케줄러에 부여 합니다. 또한 스케줄러 간에 리소스의 균형을 다시 조정 하는 경우 메서드를 호출 하 여 가상 프로세서 루트를 스케줄러에 추가할 수도 있습니다.

## <a name="ischedulergetid-method"></a><a name="getid"></a> IScheduler:: GetId 메서드

스케줄러에 대 한 고유 식별자를 반환 합니다.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>반환 값

고유한 정수 식별자입니다.

### <a name="remarks"></a>설명

[GetSchedulerId](concurrency-namespace-functions.md) 함수를 사용 하 여 인터페이스를 구현 하는 개체의 고유 식별자를 가져온 `IScheduler` 후에는 인터페이스를 리소스 관리자 제공 된 메서드에 대 한 매개 변수로 사용 해야 합니다. 함수가 호출 될 때 동일한 식별자를 반환할 것으로 예상 됩니다 `GetId` .

다른 소스에서 가져온 식별자로 인해 정의 되지 않은 동작이 발생할 수 있습니다.

## <a name="ischedulergetpolicy-method"></a><a name="getpolicy"></a> IScheduler:: GetPolicy 메서드

스케줄러 정책의 복사본을 반환 합니다. 스케줄러 정책에 대 한 자세한 내용은 [SchedulerPolicy](schedulerpolicy-class.md)를 참조 하세요.

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>반환 값

스케줄러 정책의 복사본입니다.

## <a name="ischedulernotifyresourcesexternallybusy-method"></a><a name="notifyresourcesexternallybusy"></a> IScheduler:: NotifyResourcesExternallyBusy 메서드

현재 배열의 가상 프로세서 루트 집합으로 표시 된 하드웨어 스레드를 `ppVirtualProcessorRoots` 다른 스케줄러에서 사용 하 고 있음을이 스케줄러에 알립니다.

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>매개 변수

*ppVirtualProcessorRoots*<br/>
`IVirtualProcessorRoot`다른 스케줄러가 사용 중인 하드웨어 스레드와 연결 된 인터페이스의 배열입니다.

*count*<br/>
`IVirtualProcessorRoot`배열에 있는 인터페이스의 수입니다.

### <a name="remarks"></a>설명

한 번에 특정 하드웨어 스레드를 여러 스케줄러에 할당할 수 있습니다. 한 가지 이유는 리소스를 공유 하지 않고 모든 스케줄러에 대 한 최소 동시성을 충족 하기 위해 시스템에 하드웨어 스레드가 부족 하기 때문일 수 있습니다. 다른 경우에는 소유 하는 스케줄러가 사용 하지 않는 경우 해당 하드웨어 스레드의 모든 가상 프로세서 루트를 비활성화 하 여 리소스를 다른 스케줄러에 일시적으로 할당할 수 있습니다.

하드웨어 스레드의 구독 수준은 해당 하드웨어 스레드와 연결 된 구독 된 스레드 수 및 활성화 된 가상 프로세서 루트로 표시 됩니다. 특정 스케줄러 관점에서 볼 때 하드웨어 스레드의 외부 구독 수준은 다른 스케줄러의 영향을 주는 구독의 일부입니다. 리소스를 외부에서 사용 하는 알림은 하드웨어 스레드의 외부 구독 수준이 0에서 양의 영토로 이동 하는 경우 스케줄러로 보내집니다.

이 메서드를 통한 알림은 정책 `MinConcurrency` 키 값이 정책 키에 대 한 값과 같은 정책이 있는 스케줄러에만 전송 됩니다 `MaxConcurrency` . 스케줄러 정책에 대 한 자세한 내용은 [SchedulerPolicy](schedulerpolicy-class.md)를 참조 하세요.

알림을 정규화 하는 스케줄러는 생성 될 때 초기 알림 집합을 가져오고 방금 할당 된 리소스가 외부에서 사용 중인지 또는 유휴 상태 인지를 알려 줍니다.

## <a name="ischedulernotifyresourcesexternallyidle-method"></a><a name="notifyresourcesexternallyidle"></a> IScheduler:: NotifyResourcesExternallyIdle 메서드

배열의 가상 프로세서 루트 집합으로 표시 된 하드웨어 스레드를 `ppVirtualProcessorRoots` 다른 스케줄러에서 사용 하 고 있지 않는다는 것을이 스케줄러에 알립니다.

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>매개 변수

*ppVirtualProcessorRoots*<br/>
`IVirtualProcessorRoot`다른 스케줄러가 유휴 상태가 된 하드웨어 스레드와 연결 된 인터페이스의 배열입니다.

*count*<br/>
`IVirtualProcessorRoot`배열에 있는 인터페이스의 수입니다.

### <a name="remarks"></a>설명

한 번에 특정 하드웨어 스레드를 여러 스케줄러에 할당할 수 있습니다. 한 가지 이유는 리소스를 공유 하지 않고 모든 스케줄러에 대 한 최소 동시성을 충족 하기 위해 시스템에 하드웨어 스레드가 부족 하기 때문일 수 있습니다. 다른 경우에는 소유 하는 스케줄러가 사용 하지 않는 경우 해당 하드웨어 스레드의 모든 가상 프로세서 루트를 비활성화 하 여 리소스를 다른 스케줄러에 일시적으로 할당할 수 있습니다.

하드웨어 스레드의 구독 수준은 해당 하드웨어 스레드와 연결 된 구독 된 스레드 수 및 활성화 된 가상 프로세서 루트로 표시 됩니다. 특정 스케줄러 관점에서 볼 때 하드웨어 스레드의 외부 구독 수준은 다른 스케줄러의 영향을 주는 구독의 일부입니다. 리소스를 외부에서 사용 하는 알림은 하드웨어 스레드의 외부 구독 수준이 이전 양수 값에서 0이 될 때 스케줄러로 보내집니다.

이 메서드를 통한 알림은 정책 `MinConcurrency` 키 값이 정책 키에 대 한 값과 같은 정책이 있는 스케줄러에만 전송 됩니다 `MaxConcurrency` . 스케줄러 정책에 대 한 자세한 내용은 [SchedulerPolicy](schedulerpolicy-class.md)를 참조 하세요.

알림을 정규화 하는 스케줄러는 생성 될 때 초기 알림 집합을 가져오고 방금 할당 된 리소스가 외부에서 사용 중인지 또는 유휴 상태 인지를 알려 줍니다.

## <a name="ischedulerremovevirtualprocessors-method"></a><a name="removevirtualprocessors"></a> IScheduler:: RemoveVirtualProcessors 메서드

이전에이 스케줄러에 할당 된 가상 프로세서 루트의 제거를 시작 합니다.

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>매개 변수

*ppVirtualProcessorRoots*<br/>
`IVirtualProcessorRoot`제거할 가상 프로세서 루트를 나타내는 인터페이스의 배열입니다.

*count*<br/>
`IVirtualProcessorRoot`배열에 있는 인터페이스의 수입니다.

### <a name="remarks"></a>설명

리소스 관리자는 메서드를 호출 `RemoveVirtualProcessors` 하 여 스케줄러에서 가상 프로세서 루트 집합을 다시 가져옵니다. 스케줄러는 가상 프로세서 루트를 사용 하 여 완료 될 때 각 인터페이스에서 [Remove](iexecutionresource-structure.md#remove) 메서드를 호출 해야 합니다. `IVirtualProcessorRoot`메서드를 호출한 후에는 인터페이스를 사용 하지 마십시오 `Remove` .

매개 변수는 `ppVirtualProcessorRoots` 인터페이스의 배열을 가리킵니다. 제거할 가상 프로세서 루트 집합 중에서 메서드를 사용 하 여 루트를 활성화 된 적이 없습니다 `Remove` . 활성화 되었으며 작업을 실행 중이 고 작업이 도착할 때까지 대기 중인 루트는 비동기식으로 반환 되어야 합니다. 스케줄러는 가상 프로세서 루트를 최대한 신속 하 게 제거 하려고 합니다. 가상 프로세서 루트의 제거를 지연 하면 스케줄러 내에서 의도 하지 않은 초과 구독을 발생 시킬 수 있습니다.

## <a name="ischedulerstatistics-method"></a><a name="statistics"></a> IScheduler:: Statistics 메서드

작업 도착 및 완료 비율과 관련 된 정보를 제공 하 고 스케줄러에 대 한 큐 길이를 변경 합니다.

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>매개 변수

*Ptask성공률*<br/>
이 메서드에 대 한 마지막 호출 이후 스케줄러에서 완료 된 작업의 수입니다.

*pTaskArrivalRate*<br/>
이 메서드에 대 한 마지막 호출 이후 스케줄러에 도착 한 작업 수입니다.

*Pnumberoftask대기 큐*<br/>
모든 스케줄러 큐의 총 태스크 수입니다.

### <a name="remarks"></a>설명

이 메서드는 스케줄러에 대 한 통계를 수집 하기 위해 리소스 관리자에 의해 호출 됩니다. 여기에 수집 된 통계는 동적 피드백 알고리즘을 구동 하 여 스케줄러에 더 많은 리소스를 할당 하 고 리소스를 사용 하는 시기를 결정 하는 데 사용 됩니다. 스케줄러에서 제공 하는 값은 낙관적이 될 수 있으며 현재 개수를 정확 하 게 반영 해야 하는 것은 아닙니다.

리소스 관리자에서 작업 도착 등에 대한 피드백을 사용하여 사용자의 스케줄러와 리소스 관리자에 등록된 다른 스케줄러 간에 리소스 균형을 조정하는 방법을 결정하려면 이 메서드를 구현해야 합니다. 통계를 수집 하지 않도록 선택 하는 경우 스케줄러 정책의 값으로 정책 키를 설정할 수 `DynamicProgressFeedback` `DynamicProgressFeedbackDisabled` 있으며, 리소스 관리자 스케줄러에서이 메서드를 호출 하지 않습니다.

통계 정보가 없을 경우 리소스 관리자는 하드웨어 스레드 구독 수준을 사용 하 여 리소스 할당과 마이그레이션 결정을 내립니다. 구독 수준에 대 한 자세한 내용은 [Iexecutionresource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy 클래스](schedulerpolicy-class.md)<br/>
[IExecutionContext 구조체](iexecutioncontext-structure.md)<br/>
[IThreadProxy 구조체](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot 구조체](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager 구조체](iresourcemanager-structure.md)
