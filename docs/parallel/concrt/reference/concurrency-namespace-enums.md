---
description: '자세한 정보: concurrency 네임 스페이스 열거형'
title: concurrency 네임스페이스 열거형
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::Agents_EventType
- CONCRT/concurrency::Concrt_TraceFlags
- CONCRT/concurrency::CriticalRegionType
- CONCRT/concurrency::PolicyElementKey
- CONCRT/concurrency::SchedulerType
- CONCRT/concurrency::SwitchingProxyState
- CONCRT/concurrency::WinRTInitializationType
- CONCRT/concurrency::join_type
- CONCRT/concurrency::message_status Enumeration
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
ms.openlocfilehash: 9d4f5e2fcdb2beb19d65f96687b53e52ba03ed8c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331299"
---
# <a name="concurrency-namespace-enums"></a>concurrency 네임스페이스 열거형

:::row:::
   :::column span="":::
      [`agent_status`](#agent_status)\
      [`Agents_EventType`](#agents_eventtype)\
      [`ConcRT_EventType`](#concrt_eventtype)\
      [`Concrt_TraceFlags`](#concrt_traceflags)\
      [`CriticalRegionType`](#criticalregiontype)
   :::column-end:::
   :::column span="":::
      [`DynamicProgressFeedbackType`](#dynamicprogressfeedbacktype)\
      [`join_type`](#join_type)\
      [`message_status`](#message_status)\
      [`PolicyElementKey`](#policyelementkey)\
      [`SchedulerType`](#schedulertype)
   :::column-end:::
   :::column span="":::
      [`SchedulingProtocolType`](#schedulingprotocoltype)\
      [`SwitchingProxyState`](#switchingproxystate)\
      [`task_group_status`](#task_group_status)\
      [`WinRTInitializationType`](#winrtinitializationtype)
   :::column-end:::
:::row-end:::

## <a name="agent_status-enumeration"></a><a name="agent_status"></a> agent_status 열거형

`agent`에 유효한 상태입니다.

```cpp
enum agent_status;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`agent_canceled`|`agent`을 취소했습니다.|
|`agent_created`|`agent`이 만들어졌지만 시작 되지 않았습니다.|
|`agent_done`|가 `agent` 취소 되지 않은 상태에서 완료 되었습니다.|
|`agent_runnable`|`agent`가 시작 되었지만 해당 메서드에 입력 되지 않은 경우 `run`|
|`agent_started`|`agent`가 시작 되었습니다.|

### <a name="remarks"></a>설명

자세한 내용은 [비동기 에이전트](../../../parallel/concrt/asynchronous-agents.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** concrt .h

## <a name="agents_eventtype-enumeration"></a><a name="agents_eventtype"></a> Agents_EventType 열거형

에이전트 라이브러리에서 제공하는 추적 기능을 사용하여 추적할 수 있는 이벤트 형식입니다.

```cpp
enum Agents_EventType;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|개체의 생성을 나타내는 이벤트 형식입니다.|
|`AGENTS_EVENT_DESTROY`|개체의 제거를 나타내는 이벤트 형식입니다.|
|`AGENTS_EVENT_END`|일부 처리의 종료를 나타내는 이벤트 형식입니다.|
|`AGENTS_EVENT_LINK`|메시지 블록의 연결을 나타내는 이벤트 형식입니다.|
|`AGENTS_EVENT_NAME`|개체의 이름을 나타내는 이벤트 형식입니다.|
|`AGENTS_EVENT_SCHEDULE`|프로세스의 일정을 나타내는 이벤트 형식입니다.|
|`AGENTS_EVENT_START`|일부 처리의 시작을 나타내는 이벤트 형식입니다.|
|`AGENTS_EVENT_UNLINK`|메시지 블록의 연결 해제를 나타내는 이벤트 형식입니다.|

### <a name="requirements"></a>요구 사항

**헤더:** concrt .h

## <a name="concrt_eventtype-enumeration"></a><a name="concrt_eventtype"></a> ConcRT_EventType 열거형

동시성 런타임에서 제공하는 추적 기능을 사용하여 추적할 수 있는 이벤트 형식입니다.

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|스케줄러에 연결 하는 동작을 나타내는 이벤트 형식입니다.|
|`CONCRT_EVENT_BLOCK`|컨텍스트 차단의 동작을 나타내는 이벤트 형식입니다.|
|`CONCRT_EVENT_DETACH`|스케줄러에서 분리 하는 동작을 나타내는 이벤트 형식입니다.|
|`CONCRT_EVENT_END`|시작/종료 이벤트 쌍의 시작을 표시 하는 이벤트 유형입니다.|
|`CONCRT_EVENT_GENERIC`|기타 이벤트에 사용 되는 이벤트 유형입니다.|
|`CONCRT_EVENT_IDLE`|유휴 상태가 되는 컨텍스트의 동작을 나타내는 이벤트 형식입니다.|
|`CONCRT_EVENT_START`|시작/종료 이벤트 쌍의 시작을 표시 하는 이벤트 유형입니다.|
|`CONCRT_EVENT_UNBLOCK`|컨텍스트 차단을 해제 하는 동작을 나타내는 이벤트 형식입니다.|
|`CONCRT_EVENT_YIELD`|컨텍스트 생성의 동작을 나타내는 이벤트 형식입니다.|

### <a name="requirements"></a>요구 사항

**헤더:** concrt .H **네임 스페이스:** 동시성

## <a name="concrt_traceflags-enumeration"></a><a name="concrt_traceflags"></a> Concrt_TraceFlags 열거형

이벤트 형식에 대한 추적 플래그입니다.

```cpp
enum Concrt_TraceFlags;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`AgentEventFlag`||
|`AllEventsFlag`||
|`ContextEventFlag`||
|`PPLEventFlag`||
|`ResourceManagerEventFlag`||
|`SchedulerEventFlag`||
|`VirtualProcessorEventFlag`||

### <a name="requirements"></a>요구 사항

**헤더:** concrt .h

## <a name="criticalregiontype-enumeration"></a><a name="criticalregiontype"></a> CriticalRegionType 열거형

컨텍스트가 있는 위험 영역의 형식입니다.

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`InsideCriticalRegion`|컨텍스트가 위험 영역 내에 있음을 나타냅니다. 중요 한 지역 내에 있는 경우 비동기 일시 중단 스케줄러에서 숨겨집니다. 이러한 일시 중단이 발생 하면 리소스 관리자 스레드가 실행 될 때까지 기다렸다가 스케줄러를 다시 호출 하는 대신 다시 시작 합니다. 이러한 지역 내에서 수행 되는 모든 잠금은 매우 신중 하 게 수행 해야 합니다.|
|`InsideHyperCriticalRegion`|컨텍스트가 매우 중요 한 영역 내에 있음을 나타냅니다. 중요 한 영역 내에 있는 경우 동기 및 비동기 일시 중단 모두 스케줄러에서 숨겨집니다. 이러한 일시 중단 또는 차단이 발생 해야 하는 경우 resource manager는 스레드가 실행 될 때까지 기다린 후 스케줄러를 다시 호출 하는 대신 다시 시작 하면 됩니다. 이러한 지역 내에서 수행 되는 잠금은 이러한 지역 외부에서 실행 되는 코드와 공유 되어서는 안 됩니다. 이렇게 하면 예기치 않은 교착 상태가 발생 합니다.|
|`OutsideCriticalRegion`|컨텍스트가 중요 한 영역 외부에 있음을 나타냅니다.|

### <a name="requirements"></a>요구 사항

**헤더:** concrtrm. h

## <a name="dynamicprogressfeedbacktype-enumeration"></a><a name="dynamicprogressfeedbacktype"></a> DynamicProgressFeedbackType 열거형

`DynamicProgressFeedback` 정책에서 스케줄러에 대한 리소스를 스케줄러에서 수집한 통계 정보에 따라 균형을 조정할지, 아니면 `IVirtualProcessorRoot` 인터페이스의 `Activate` 및 `Deactivate` 메서드 호출을 통해 유휴 상태로 들어오고 나가는 가상 프로세서를 기준으로만 균형을 조정할지를 설명하는 데 사용됩니다. 사용 가능한 스케줄러 정책에 대 한 자세한 내용은 [Policyelementkey](concurrency-namespace-enums.md)를 참조 하세요.

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`ProgressFeedbackDisabled`|스케줄러는 진행률 정보를 수집 하지 않습니다. 균형 재조정은 기본 하드웨어 스레드의 구독 수준에 따라서만 수행 됩니다. 구독 수준에 대 한 자세한 내용은 [Iexecutionresource:: CurrentSubscriptionLevel](IExecutionResource-structure.md)을 참조 하세요.<br /><br /> 이 값은 런타임에 사용 하도록 예약 되어 있습니다.|
|`ProgressFeedbackEnabled`|Scheduler는 진행률 정보를 수집 하 여 resource manager에 전달 합니다. 리소스 관리자는이 통계 정보를 활용 하 여 기본 하드웨어 스레드의 구독 수준 외에도 스케줄러를 대신 하 여 리소스의 균형을 조정 합니다. 구독 수준에 대 한 자세한 내용은 [Iexecutionresource:: CurrentSubscriptionLevel](IExecutionResource-structure.md)을 참조 하세요.|

## <a name="join_type-enumeration"></a><a name="join_type"></a> join_type 열거형

`join` 메시징 블록의 형식입니다.

```cpp
enum join_type;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`greedy`|Greedy `join` 메시징 블록은 전파 시 즉시 메시지를 수락 합니다. 이는 보다 효율적 이지만 네트워크 구성에 따라 라이브 잠금이 발생할 수 있습니다.|
|`non_greedy`|Non-greedy `join` 메시징 블록은 메시지를 연기 하 고 모두 도착 한 후에 시도 하 여 사용 합니다. 이러한 작업은 작동 하지만 속도가 느립니다.|

### <a name="requirements"></a>요구 사항

**헤더:** agents.h

## <a name="message_status-enumeration"></a><a name="message_status"></a> message_status 열거형

블록에 대한 `message` 개체 제공에 유효한 응답입니다.

```cpp
enum message_status;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`accepted`|대상에서 메시지를 수락 했습니다.|
|`declined`|대상이 메시지를 수락 하지 않았습니다.|
|`missed`|대상에서 메시지를 수락 하려고 했지만 더 이상 사용할 수 없습니다.|
|`postponed`|대상이 메시지를 연기 했습니다.|

### <a name="requirements"></a>요구 사항

**헤더:** agents.h

## <a name="policyelementkey-enumeration"></a><a name="policyelementkey"></a> PolicyElementKey 열거형

스케줄러 동작의 측면을 설명하는 정책 키입니다. 각 정책 요소는 키-값 쌍으로 설명됩니다. 스케줄러 정책 및 스케줄러에 대 한 영향에 대 한 자세한 내용은 [작업 스케줄러](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)를 참조 하세요.

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`ContextPriority`|스케줄러에서 각 컨텍스트의 운영 체제 스레드 우선 순위입니다. 이 키가 값으로 설정 되 면 `INHERIT_THREAD_PRIORITY` 스케줄러의 컨텍스트가 스케줄러를 만든 스레드의 우선 순위를 상속 하 게 됩니다.<br /><br /> 유효한 값: Windows `SetThreadPriority` 함수와 특수 값에 대 한 유효한 값 `INHERIT_THREAD_PRIORITY`<br /><br /> 기본값: `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|스케줄러에서 각 컨텍스트의 예약 된 스택 크기 (kb)입니다.<br /><br /> 유효한 값: 양의 정수<br /><br /> 기본값 `0` 은 스택 크기에 대 한 프로세스의 기본값을 사용 함을 나타냅니다.|
|`DynamicProgressFeedback`|스케줄러에 대 한 리소스를 스케줄러에서 수집 된 통계 정보에 따라 균형 아니면 기본 하드웨어 스레드의 구독 수준에 따라서만 할지를 결정 합니다. 자세한 내용은 [DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)를 참조 하세요.<br /><br /> 유효한 값: 열거형의 멤버 중 `DynamicProgressFeedbackType` 하나입니다. `ProgressFeedbackEnabled``ProgressFeedbackDisabled`<br /><br /> 기본값: `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|`SchedulingProtocol`정책 키가 값으로 설정 된 경우이 값은 `EnhanceScheduleGroupLocality` 가상 프로세서 로컬 큐에 캐시할 수 있는 최대 실행 가능 컨텍스트 수를 지정 합니다. 이러한 컨텍스트는 일반적으로 가상 프로세서에서 실행 가능 하도록 하는 LIFO (LIFO) 순서로 실행 됩니다. `SchedulingProtocol`키가 값으로 설정 된 경우에는이 정책 키가 의미가 없습니다 `EnhanceForwardProgress` .<br /><br /> 유효한 값: 음수가 아닌 정수<br /><br /> 기본값: `8`|
|`MaxConcurrency`|스케줄러에서 원하는 최대 동시성 수준입니다. 리소스 관리자는이 많은 가상 프로세서를 초기에 할당 하려고 합니다. 특수 값 [Maxexecutionresources](concurrency-namespace-constants1.md#maxexecutionresources) 는 원하는 동시성 수준이 컴퓨터의 하드웨어 스레드 수와 동일 함을 나타냅니다. 에 지정 된 값이 `MinConcurrency` 컴퓨터의 하드웨어 스레드 수보다 크고로 지정 된 경우에 대 한 `MaxConcurrency` 값은 `MaxExecutionResources` `MaxConcurrency` 에 대해 설정 된 값과 일치 하도록 발생 합니다 `MinConcurrency` .<br /><br /> 유효한 값: 양의 정수 및 특수 값 `MaxExecutionResources`<br /><br /> 기본값: `MaxExecutionResources`|
|`MaxPolicyElementKey`|최대 정책 요소 키입니다. 잘못 된 요소 키입니다.|
|`MinConcurrency`|리소스 관리자가 스케줄러에 제공 해야 하는 최소 동시성 수준입니다. 스케줄러에 할당 된 가상 프로세서의 수는 최소한 이상으로 표시 되지 않습니다. 특수 값 [Maxexecutionresources](concurrency-namespace-constants1.md#maxexecutionresources) 는 최소 동시성 수준이 컴퓨터의 하드웨어 스레드 수와 동일 함을 나타냅니다. 에 지정 된 값 `MaxConcurrency` 이 컴퓨터의 하드웨어 스레드 수보다 작고로 지정 된 경우의 `MinConcurrency` 값이 `MaxExecutionResources` `MinConcurrency` 설정 된 값과 일치 하도록 줄어듭니다 `MaxConcurrency` .<br /><br /> 유효한 값: 음수가 아닌 정수 및 특수 값 `MaxExecutionResources` 입니다. 동시성 런타임이 스케줄러의 생성에 사용되는 스케줄러 정책의 경우에는 값 `0`이 유효하지 않습니다.<br /><br /> 기본값: `1`|
|`SchedulerKind`|스케줄러가 기본 실행 컨텍스트에 사용할 스레드의 형식입니다. 자세한 내용은 [SchedulerType](#schedulertype)를 참조 하세요.<br /><br /> 유효한 값: `SchedulerType` 열거형의 멤버. 예: `ThreadScheduler`<br /><br /> 기본값은 `ThreadScheduler` 입니다. 이는 모든 운영 체제에서 Win32 스레드로 변환 됩니다.|
|`SchedulingProtocol`|스케줄러에서 사용할 일정 알고리즘을 설명 합니다. 자세한 내용은 [SchedulingProtocolType](#schedulingprotocoltype)를 참조 하세요.<br /><br /> 유효한 값: 열거형의 멤버 중 `SchedulingProtocolType` 하나입니다. `EnhanceScheduleGroupLocality``EnhanceForwardProgress`<br /><br /> 기본값: `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|하드웨어 스레드별 가상 프로세서의 미정 수입니다. 필요할 경우 시스템의 하드웨어 스레드로 `MaxConcurrency`를 만족시키기 위해 리소스 관리자에서 대상 초과 구독 비율을 증가시킬 수 있습니다.<br /><br /> 유효한 값: 양의 정수<br /><br /> 기본값: `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>요구 사항

**헤더:** concrt .h

## <a name="schedulertype-enumeration"></a><a name="schedulertype"></a> SchedulerType 열거형

`SchedulerKind` 정책에서 스케줄러가 기본 실행 컨텍스트에 활용해야 하는 스레드 형식을 설명하는 데 사용됩니다. 사용 가능한 스케줄러 정책에 대 한 자세한 내용은 [Policyelementkey](concurrency-namespace-enums.md)를 참조 하세요.

```cpp
enum SchedulerType;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`ThreadScheduler`|일반 Win32 스레드의 명시적 요청을 나타냅니다.|
|`UmsThreadDefault`|UMS (사용자 모드 예약 가능) 스레드는 Visual Studio 2013 동시성 런타임에서 지원 되지 않습니다. `UmsThreadDefault`를 `SchedulerType` 정책의 값으로 사용하면 오류가 발생하지 않습니다. 그러나 해당 정책을 사용하여 만들어진 스케줄러는 기본적으로 Win32 스레드를 사용합니다.|

### <a name="requirements"></a>요구 사항

**헤더:** concrt .h

## <a name="schedulingprotocoltype-enumeration"></a><a name="schedulingprotocoltype"></a> SchedulingProtocolType 열거형

`SchedulingProtocol` 정책에서 스케줄러에 활용되는 일정 알고리즘을 설명하는 데 사용됩니다. 사용 가능한 스케줄러 정책에 대 한 자세한 내용은 [Policyelementkey](concurrency-namespace-enums.md)를 참조 하세요.

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`EnhanceForwardProgress`|스케줄러는 각 작업을 실행 한 후 일정 그룹을 통해 라운드 로빈을 선호 합니다. 차단을 해제 한 컨텍스트는 일반적으로 FIFO (선입 선출) 방식으로 예약 됩니다. 가상 프로세서는 차단 해제 컨텍스트를 캐시 하지 않습니다.|
|`EnhanceScheduleGroupLocality`|스케줄러는 다른 일정 그룹으로 이동 하기 전에 현재 일정 그룹 내의 작업에 대 한 작업을 계속 하는 것을 선호 합니다. 차단 해제 된 컨텍스트는 가상 프로세서당 캐시 되며 일반적으로이를 차단 해제 하는 가상 프로세서에 의해 LIFO (선입 authentication) 방식으로 예약 됩니다.|

### <a name="requirements"></a>요구 사항

**헤더:** concrt .h

## <a name="switchingproxystate-enumeration"></a><a name="switchingproxystate"></a> SwitchingProxyState 열거형

다른 스레드 프록시로의 협조적 컨텍스트 전환을 실행하는 경우 스레드 프록시의 현재 상태를 나타내는 데 사용됩니다.

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`Blocking`|호출 스레드가 협조적으로 차단 되며 이후에 다시 실행 되 고 다른 작업을 수행할 때까지 호출자가 독점적으로 소유 해야 함을 나타냅니다.|
|`Idle`|는 호출 스레드가 스케줄러에서 더 이상 필요 하지 않으며 리소스 관리자 반환 되 고 있음을 나타냅니다. 디스패치할 컨텍스트는 더 이상 리소스 관리자에서 활용할 수 없습니다.|
|`Nesting`|호출 스레드가 자식 스케줄러를 중첩 하 고 다른 스케줄러에 연결 하기 위해 호출자에 게 필요 함을 나타냅니다.|

### <a name="remarks"></a>설명

호출 하는 `SwitchingProxyState` `IThreadProxy::SwitchTo` 스레드 프록시를 처리 하는 방법을 리소스 관리자에 지시 하기 위해 형식의 매개 변수가 메서드에 전달 됩니다.

이 형식을 사용 하는 방법에 대 한 자세한 내용은 [Ithreadproxy:: SwitchTo](ithreadproxy-structure.md#switchto)를 참조 하세요.

## <a name="task_group_status-enumeration"></a><a name="task_group_status"></a> task_group_status 열거형

`task_group` 또는 `structured_task_group` 개체의 실행 상태를 설명합니다. 이 형식의 값은 작업 그룹에 예약된 작업이 완료되기를 기다리는 수많은 메서드에 의해 반환됩니다.

```cpp
enum task_group_status;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`canceled`|`task_group` 또는 `structured_task_group` 개체가 취소되었습니다. 하나 이상의 작업이 실행되지 않았을 수 있습니다.|
|`completed`|`task_group` 또는 `structured_task_group` 개체의 큐에 대기 중인 작업이 성공적으로 완료되었습니다.|
|`not_complete`|`task_group` 개체의 큐에 대기 중인 작업이 완료되지 않았습니다. 이 값은 현재 동시성 런타임에서 반환되지 않습니다.|

### <a name="requirements"></a>요구 사항

**헤더:** pplinterface.h

## <a name="winrtinitializationtype-enumeration"></a><a name="winrtinitializationtype"></a> WinRTInitializationType 열거형

`WinRTInitialization` 정책에서 Windows 8 또는 그 이상 버전의 운영 체제에서 실행되는 애플리케이션에 대한 스케줄러 스레드에서 Windows 런타임이 초기화될지 여부와 초기화되는 방법을 설명하는데 사용됩니다. 사용 가능한 스케줄러 정책에 대 한 자세한 내용은 [Policyelementkey](concurrency-namespace-enums.md)를 참조 하세요.

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`DoNotInitializeWinRT`|애플리케이션이 Windows 8 또는 그 이상 버전의 운영 체제에서 실행될 경우 스케줄러 내의 스레드는 Windows 런타임을 초기화하지 않습니다.|
|`InitializeWinRTAsMTA`|애플리케이션이 Windows 8 또는 그 이상 버전의 운영 체제에서 실행할 경우 스케줄러 내의 각 스레드는 Windows 런타임을 초기화하고 이것을 멀티스레드의 일부로 선언합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)
