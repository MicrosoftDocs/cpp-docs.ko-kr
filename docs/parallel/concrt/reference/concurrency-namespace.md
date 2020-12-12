---
description: '자세히 알아보기: concurrency 네임 스페이스'
title: 동시성 네임스페이스
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue/concurrency
- agents/concurrency
- concurrent_vector/concurrency
- concrt/concurrency
- internal_split_ordered_list/concurrency
- concurrent_queue/concurrency
- pplcancellation_token/concurrency
- pplinterface/concurrency
- ppltasks/concurrency
- ppl/concurrency
- concurrent_unordered_map/concurrency
- concrtrm/concurrency
- concurrent_unordered_set/concurrency
- pplconcrt/concurrency
- internal_concurrent_hash/concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: f1d33ca2-679b-4442-b140-22a9d9df61d1
ms.openlocfilehash: c17e058c6666f944ea9f34b90995e9b9d343b40e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335815"
---
# <a name="concurrency-namespace"></a>동시성 네임스페이스

`Concurrency` 네임스페이스는 C++용 동시 프로그래밍 프레임워크인 동시성 런타임에 액세스하는 데 사용할 수 있는 클래스와 함수를 제공합니다. 자세한 내용은 [Concurrency Runtime](../../../parallel/concrt/concurrency-runtime.md)을 참조하세요.

## <a name="syntax"></a>구문

```cpp
namespace concurrency;
```

## <a name="members"></a>멤버

### <a name="typedefs"></a>Typedefs

|Name|설명|
|----------|-----------------|
|`runtime_object_identity`|각 메시지 인스턴스에는 복제하고 메시지 구성 요소 간에 전달될 때 따라가는 ID가 있습니다. 이 ID는 메시지 개체의 주소가 될 수 없습니다.|
|`task_status`|작업의 종료 상태를 나타내는 형식입니다. 유효한 값은 `completed` 및 `canceled`입니다.|
|`TaskProc`|`void (__cdecl * TaskProc)(void *)`로 정의되는 작업의 기본 추상화입니다. 작업의 본문을 호출하기 위해 `TaskProc`가 호출됩니다.|
|`TaskProc_t`|`void (__cdecl * TaskProc_t)(void *)`로 정의되는 작업의 기본 추상화입니다. 작업의 본문을 호출하기 위해 `TaskProc`가 호출됩니다.|

### <a name="classes"></a>클래스

|이름|설명|
|----------|-----------------|
|[affinity_partitioner 클래스](affinity-partitioner-class.md)|`affinity_partitioner` 클래스는 `static_partitioner` 클래스와 비슷하지만 하위 범위를 작업자 스레드로 매핑하는 선택을 통해 캐시 선호도를 향상시킵니다. 동일한 데이터 집합에서 루프를 다시 실행하고 데이터가 캐시에 맞는 경우 성능을 훨씬 향상시킬 수 있습니다. 데이터 집약성을 활용하려면 특정 데이터 집합에 대해 실행되는 병렬 루프의 후속 반복과 함께 동일한 `affinity_partitioner` 개체를 사용해야 합니다.|
|[agent 클래스](agent-class.md)|모든 독립 에이전트에 대한 기본 클래스로 사용되는 클래스입니다. 다른 에이전트로부터 상태를 숨기고 메시지 전달을 사용하여 상호 작용하는 데 사용됩니다.|
|[auto_partitioner 클래스](auto-partitioner-class.md)|`auto_partitioner` 클래스는 `parallel_for`, `parallel_for_each` 및 `parallel_transform`이 반복하는 범위를 분할하는 데 사용하는 기본 방법을 나타냅니다. 이 분할 방법은 부하 분산 및 반복 별 취소에 대해 범위 가로채기를 채택 합니다.|
|[bad_target 클래스](bad-target-class.md)|이 클래스는 수행되는 작업에 잘못된 대상에 대한 포인터가 메시징 블록에 제공되는 경우 발생하는 예외를 설명합니다.|
|[call 클래스](call-class.md)|`call` 메시징 블록은 메시지를 받을 때 지정된 함수를 호출하는 순서가 지정된 다중 소스 `target_block`입니다.|
|[cancellation_token 클래스](cancellation-token-class.md)|`cancellation_token` 클래스는 일부 작업을 취소하도록 요청되었는지 여부를 확인하는 기능을 나타냅니다. 지정된 토큰을 `task_group`, `structured_task_group` 또는 `task`와 연결하여 암시적 취소를 제공할 수 있습니다. 연결된 `cancellation_token_source`가 취소된 경우 취소를 폴링하거나 콜백을 등록할 수도 있습니다.|
|[cancellation_token_registration 클래스](cancellation-token-registration-class.md)|`cancellation_token_registration` 클래스는 `cancellation_token`의 콜백 알림을 나타냅니다. 취소 발생 시 알림을 받는 데 `register`의 `cancellation_token` 메서드를 사용하면 `cancellation_token_registration` 메서드 사용을 통해 더 이상 만들어지지 않는 특정 콜백을 호출자가 요청할 수 있도록 `deregister` 개체가 콜백에 대한 핸들로 반환됩니다.|
|[cancellation_token_source 클래스](cancellation-token-source-class.md)|`cancellation_token_source` 클래스는 일부 취소 가능한 작업을 취소하는 기능을 나타냅니다.|
|[choice 클래스](choice-class.md)|`choice` 메시징 블록은 소스 집합과의 제어 흐름 상호 작용을 나타내는 다중 소스 단일 대상 블록입니다. 선택한 블록은 여러 소스 중 하나가 메시지를 생성할 때까지 대기하고 메시지를 생성한 소스의 인덱스를 전파합니다.|
|[결합 가능한 클래스](combinable-class.md)|`combinable<T>` 개체는 병렬 알고리즘 중에 잠금 없는 스레드 로컬 하위 계산을 수행하기 위해 데이터의 스레드 전용 복사본을 제공합니다. 병렬 작업이 끝나면 스레드 전용 하위 계산을 최종 결과에 병합할 수 있습니다. 이 클래스는 공유 변수 대신 사용될 수 있으며, 그렇지 않을 경우 해당 공유 변수에 대한 경합이 많으면 성능이 향상될 수 있습니다.|
|[concurrent_priority_queue 클래스](concurrent-priority-queue-class.md)|`concurrent_priority_queue` 클래스는 여러 스레드에서 동시에 항목을 푸시 및 팝할 수 있도록 허용하는 컨테이너입니다. 항목은 우선순위에 따라 팝되고, 우선순위는 템플릿 인수로 제공된 함수에 의해 결정됩니다.|
|[concurrent_queue 클래스](concurrent-queue-class.md)|`concurrent_queue` 클래스는 해당 요소에 대해 선입 선출 액세스를 허용하는 시퀀스 컨테이너 클래스입니다. `push` 및 `try_pop`과 같은 동시성으로부터 안전한 작업의 제한된 집합을 사용할 수 있게 합니다.|
|[concurrent_unordered_map 클래스](concurrent-unordered-map-class.md)|`concurrent_unordered_map` 클래스는 `std::pair<const K, _Element_type>` 형식의 다양한 길이 요소 시퀀스를 제어하는 동시성으로부터 안전한 컨테이너입니다. 시퀀스는 동시성으로부터 안전한 추가, 요소 액세스, 반복기 액세스 및 반복기 통과 작업을 사용할 수 있는 방식으로 표시됩니다.|
|[concurrent_unordered_multimap 클래스](concurrent-unordered-multimap-class.md)|`concurrent_unordered_multimap` 클래스는 `std::pair<const K, _Element_type>` 형식의 다양한 길이 요소 시퀀스를 제어하는 동시성으로부터 안전한 컨테이너입니다. 시퀀스는 동시성으로부터 안전한 추가, 요소 액세스, 반복기 액세스 및 반복기 통과 작업을 사용할 수 있는 방식으로 표시됩니다.|
|[concurrent_unordered_multiset 클래스](concurrent-unordered-multiset-class.md)|`concurrent_unordered_multiset`클래스는 K 형식의 다양 한 길이 요소 시퀀스를 제어 하는 동시성이 보장 되는 컨테이너입니다. 시퀀스는 동시성이 보장 되는 추가, 요소 액세스, 반복기 액세스 및 반복기 통과 작업을 가능 하 게 하는 방식으로 표현 됩니다.|
|[concurrent_unordered_set 클래스](concurrent-unordered-set-class.md)|`concurrent_unordered_set`클래스는 K 형식의 다양 한 길이 요소 시퀀스를 제어 하는 동시성이 보장 되는 컨테이너입니다. 시퀀스는 동시성이 보장 되는 추가, 요소 액세스, 반복기 액세스 및 반복기 통과 작업을 가능 하 게 하는 방식으로 표현 됩니다.|
|[concurrent_vector 클래스](concurrent-vector-class.md)|`concurrent_vector` 클래스는 모든 요소에 대해 임의 액세스를 허용하는 시퀀스 컨테이너 클래스입니다. 동시성으로부터 안전한 추가, 요소 액세스, 반복기 액세스 및 반복기 통과 작업을 사용할 수 있게 합니다.|
|[Context 클래스](context-class.md)|실행 컨텍스트에 대한 추상화를 나타냅니다.|
|[context_self_unblock 클래스](context-self-unblock-class.md)|이 클래스는 동일한 컨텍스트에서 `Context` 개체의 `Unblock` 메서드를 호출하는 경우 발생하는 예외를 설명합니다. 자신을 차단 해제하려는 지정된 컨텍스트의 시도를 나타냅니다.|
|[context_unblock_unbalanced 클래스](context-unblock-unbalanced-class.md)|이 클래스는 동일한 컨텍스트에서 `Context` 개체의 `Block` 및 `Unblock` 메서드 호출 쌍이 잘못된 경우 발생하는 예외를 설명합니다.|
|[critical_section 클래스](critical-section-class.md)|동시성 런타임을 명시적으로 인식하는 재진입성이 아닌 뮤텍스입니다.|
|[CurrentScheduler 클래스](currentscheduler-class.md)|호출 컨텍스트와 연결된 현재 스케줄러에 대한 추상화를 나타냅니다.|
|[default_scheduler_exists 클래스](default-scheduler-exists-class.md)|이 클래스는 프로세스 내에 기본 스케줄러가 이미 있을 때 `Scheduler::SetDefaultSchedulerPolicy` 메서드를 호출하는 경우 발생하는 예외를 설명합니다.|
|[이벤트 클래스](event-class.md)|동시성 런타임을 명시적으로 인식하는 수동 다시 설정 이벤트입니다.|
|[improper_lock 클래스](improper-lock-class.md)|이 클래스는 부적절하게 잠금을 얻은 경우 발생하는 예외를 설명합니다.|
|[improper_scheduler_attach 클래스](improper-scheduler-attach-class.md)|이 클래스는 동일한 컨텍스트에 이미 연결된 `Scheduler` 개체에 대해 `Attach` 메서드를 호출하는 경우 발생하는 예외를 설명합니다.|
|[improper_scheduler_detach 클래스](improper-scheduler-detach-class.md)|이 클래스는 `Scheduler` 개체의 `Attach` 메서드를 사용하여 스케줄러에 연결되지 않은 컨텍스트에 대해 `CurrentScheduler::Detach` 메서드를 호출하는 경우 발생하는 예외를 설명합니다.|
|[improper_scheduler_reference 클래스](improper-scheduler-reference-class.md)|이 클래스는 스케줄러에 속하지 않는 컨텍스트에서 종료되는 `Scheduler` 개체에 대해 `Reference` 메서드를 호출하는 경우 발생하는 예외를 설명합니다.|
|[invalid_link_target 클래스](invalid-link-target-class.md)|이 클래스는 메시징 블록의 `link_target` 메서드를 호출하고 메시징 블록이 대상에 연결할 수 없는 경우 발생하는 예외를 설명합니다. 메시징 블록에 허용되는 링크 수를 초과했거나 동일한 소스에 특정 대상을 두 번 연결하려고 시도한 결과일 수 있습니다.|
|[invalid_multiple_scheduling 클래스](invalid-multiple-scheduling-class.md)|이 클래스는 `wait` 또는 `run_and_wait` 메서드에 대한 중간 호출 없이 `task_group` 또는 `structured_task_group` 개체의 `run` 메서드를 사용하여 `task_handle` 개체가 여러 번 예약하는 경우 발생하는 예외를 설명합니다.|
|[invalid_operation 클래스](invalid-operation-class.md)|이 클래스는 잘못된 작업이 수행될 때 throw되는 예외로, 동시성 런타임에서 throw된 다른 예외 형식으로 보다 정확하게 설명되지 않은 예외를 설명합니다.|
|[invalid_oversubscribe_operation 클래스](invalid-oversubscribe-operation-class.md)|이 클래스는 매개 `Context::Oversubscribe` `_BeginOversubscription` 변수를 **`false`** `Context::Oversubscribe` 로 설정 하 여 메서드를 이전에 호출 하지 않고 매개 변수를로 설정 `_BeginOversubscription` **`true`** 하 여 메서드를 호출할 때 throw 되는 예외를 설명 합니다.|
|[invalid_scheduler_policy_key 클래스](invalid-scheduler-policy-key-class.md)|이 클래스는 잘못되었거나 알 수 없는 키가 `SchedulerPolicy` 개체 생성자에 전달된 경우 또는 `SchedulerPolicy` 개체의 `SetPolicyValue` 메서드에 `SetConcurrencyLimits` 메서드와 같은 기타 방법으로 변경해야 하는 키가 전달된 경우 발생하는 예외를 설명합니다.|
|[invalid_scheduler_policy_thread_specification 클래스](invalid-scheduler-policy-thread-specification-class.md)|이 클래스는 `MinConcurrency` 키의 값이 `MaxConcurrency` 키의 값보다 작도록 `SchedulerPolicy` 개체의 동시성 제한을 설정하려고 시도하는 경우 발생하는 예외를 설명합니다.|
|[invalid_scheduler_policy_value 클래스](invalid-scheduler-policy-value-class.md)|이 클래스는 `SchedulerPolicy` 개체의 정책 키가 해당 키에 잘못된 값으로 설정된 경우 발생하는 예외를 설명합니다.|
|[ISource 클래스](isource-class.md)|`ISource` 클래스는 모든 소스 블록에 대한 인터페이스입니다. 소스 블록은 `ITarget` 블록에 메시지를 전파합니다.|
|[ITarget 클래스](itarget-class.md)|`ITarget` 클래스는 모든 대상 블록에 대한 인터페이스입니다. 대상 블록은 `ISource` 블록에서 제공한 메시지를 사용합니다.|
|[join 클래스](join-class.md)|`join` 메시징 블록은 각 소스에서 `T` 형식의 메시지를 결합하는 순서가 지정된 단일 대상 다중 소스 `propagator_block`입니다.|
|[location 클래스](location-class.md)|하드웨어의 실제 위치에 대한 추상화입니다.|
|[message 클래스](message-class.md)|메시징 블록 간에 전달되는 데이터 페이로드를 포함하는 기본 메시지 봉투입니다.|
|[message_not_found 클래스](message-not-found-class.md)|이 클래스는 메시징 블록이 요청된 메시지를 찾을 수 없는 경우 발생하는 예외를 설명합니다.|
|[message_processor 클래스](message-processor-class.md)|`message_processor` 클래스는 `message` 개체 처리를 위한 추상 기본 클래스입니다. 메시지 순서에 대한 보장은 없습니다.|
|[missing_wait 클래스](missing-wait-class.md)|이 클래스는 개체의 소멸자를 실행할 때 `task_group` 또는 `structured_task_group` 개체에 여전히 예약된 작업이 있는 경우 발생하는 예외를 설명합니다. 예외의 결과로 스택 해제 때문에 소멸자에 도달한 경우에는 이 예외가 발생하지 않습니다.|
|[multi_link_registry 클래스](multi-link-registry-class.md)|`multi_link_registry` 개체는 여러 소스 블록 또는 여러 대상 블록을 관리하는 `network_link_registry`입니다.|
|[multitype_join 클래스](multitype-join-class.md)|`multitype_join` 메시징 블록은 각 소스에서 다양한 형식의 메시지를 결합하고 결합된 메시지의 튜플을 대상에 제공하는 다중 소스, 단일 대상 메시징 블록입니다.|
|[nested_scheduler_missing_detach 클래스](nested-scheduler-missing-detach-class.md)|이 클래스는 동시성 런타임에서 `Scheduler` 개체의 `Attach` 메서드를 사용하여 두 번째 스케줄러에 연결된 컨텍스트에 대해 `CurrentScheduler::Detach` 메서드를 호출하지 않은 것을 감지하는 경우 발생하는 예외를 설명합니다.|
|[network_link_registry 클래스](network-link-registry-class.md)|`network_link_registry` 추상 기본 클래스는 소스 및 대상 블록 간의 연결을 관리합니다.|
|[operation_timed_out 클래스](operation-timed-out-class.md)|이 클래스는 작업이 시간 초과된 경우 발생하는 예외를 설명합니다.|
|[ordered_message_processor 클래스](ordered-message-processor-class.md)|`ordered_message_processor`는 메시지 블록이 수신된 순서대로 메시지를 처리할 수 있도록 하는 `message_processor`입니다.|
|[overwrite_buffer 클래스](overwrite-buffer-class.md)|`overwrite_buffer` 메시징 블록은 한 번에 하나의 메시지를 저장할 수 있는, 순서가 지정된 다중 대상 다중 소스 `propagator_block`입니다. 새 메시지가 이전에 보유한 메시지를 덮어씁니다.|
|[progress_reporter 클래스](progress-reporter-class.md)|진행률 보고자 클래스를 사용하면 특정 형식의 진행률 알림을 보고할 수 있습니다. 각 progress_reporter 개체는 특정 비동기 작업이나 연산에 바인딩됩니다.|
|[propagator_block 클래스](propagator-block-class.md)|`propagator_block` 클래스는 소스인 동시에 대상인 메시지 블록에 대한 추상 기본 클래스입니다. `source_block` 및 `target_block` 클래스의 기능을 결합합니다.|
|[reader_writer_lock 클래스](reader-writer-lock-class.md)|로컬 전용 회전을 사용한 작성기 우선 큐 기반 읽기/쓰기 잠금입니다. 잠금은 작성기에 대해 FIFO(선입 선출) 액세스 권한을 부여하며 작성기의 연속 부하 상태에서는 판독기에 제공되지 않습니다.|
|[ScheduleGroup 클래스](schedulegroup-class.md)|일정 그룹에 대한 추상화를 나타냅니다. 일정 그룹은 다른 그룹으로 이동하기 전에 동일한 그룹의 다른 작업을 실행하여 시간적으로 또는 동일한 NUMA 노드 또는 실제 소켓에서 동일한 그룹 내의 여러 항목을 실행하여 공간적으로 서로 가깝게 예약하면 도움이 되는 관련된 작업 집합을 구성합니다.|
|[Scheduler 클래스](scheduler-class.md)|동시성 런타임 스케줄러에 대한 추상화를 나타냅니다.|
|[scheduler_not_attached 클래스](scheduler-not-attached-class.md)|이 클래스는 스케줄러가 현재 컨텍스트에 연결되어야 하는 작업을 수행하는데 연결된 스케줄러가 없는 경우 발생하는 예외를 설명합니다.|
|[scheduler_resource_allocation_error 클래스](scheduler-resource-allocation-error-class.md)|이 클래스는 동시성 런타임에서 중요한 리소스를 얻지 못해 발생하는 예외를 설명합니다.|
|[scheduler_worker_creation_error 클래스](scheduler-worker-creation-error-class.md)|이 클래스는 동시성 런타임에서 작업자 실행 컨텍스트를 만들지 못해 발생하는 예외를 설명합니다.|
|[SchedulerPolicy 클래스](schedulerpolicy-class.md)|`SchedulerPolicy` 클래스에는 정책 요소마다 하나씩, 스케줄러 인스턴스의 동작을 제어하는 키/값 쌍 집합을 포함합니다.|
|[simple_partitioner 클래스](simple-partitioner-class.md)|`simple_partitioner` 클래스는 `parallel_for`에서 반복하는 범위의 정적 분할을 나타냅니다. 파티셔너는 각 청크에 적어도 청크 크기로 지정된 개수의 반복이 있도록 범위를 청크로 나눕니다.|
|[single_assignment 클래스](single-assignment-class.md)|`single_assignment` 메시징 블록은 하나의 한 번 쓰기 `message`를 저장할 수 있는, 순서가 지정된 다중 대상 다중 소스 `propagator_block`입니다.|
|[single_link_registry 클래스](single-link-registry-class.md)|`single_link_registry` 개체는 단일 소스 또는 대상 블록만 관리하는 `network_link_registry`입니다.|
|[source_block 클래스](source-block-class.md)|`source_block` 클래스는 소스 전용 블록에 대한 추상 기본 클래스입니다. 이 클래스는 기본 링크 관리 기능 및 일반적인 오류 검사를 제공합니다.|
|[source_link_manager 클래스](source-link-manager-class.md)|`source_link_manager` 개체는 `ISource` 블록에 대한 메시징 블록 네트워크 연결을 관리합니다.|
|[static_partitioner 클래스](static-partitioner-class.md)|`static_partitioner` 클래스는 `parallel_for`에서 반복하는 범위의 정적 분할을 나타냅니다. 파티 셔 너는 기본 스케줄러에서 사용할 수 있는 작업자의 수 만큼의 청크로 범위를 나눕니다.|
|[structured_task_group 클래스](structured-task-group-class.md)|`structured_task_group` 클래스는 구조화된 병렬 작업 컬렉션을 나타냅니다. `task_handle` 개체를 사용하여 개별 병렬 작업을 `structured_task_group`에 대기시킨 다음 완료되기를 기다리거나 실행이 완료되기 전에 작업 그룹을 취소합니다. 이 경우 실행이 시작되지 않은 작업이 모두 중단됩니다.|
|[target_block 클래스](target-block-class.md)|`target_block` 클래스는 대상 전용 블록에 대해 기본 링크 관리 기능 및 오류 검사를 제공하는 추상 기본 클래스입니다.|
|[작업 클래스 (동시성 런타임)](task-class.md)|PPL(병렬 패턴 라이브러리) `task` 클래스입니다. `task` 개체는 비동기식으로 실행할 수 있으며 동시성 런타임의 병렬 알고리즘을 통해 생성되는 기타 작업 및 병렬 작업과 동시에 실행할 수 있는 작업을 나타냅니다. 이러한 작업이 정상적으로 완료되면 `_ResultType` 형식의 결과가 생성됩니다. `task<void>` 형식의 작업에서는 결과가 생성되지 않습니다. 작업은 다른 작업과 관계없이 대기 및 취소할 수 있으며 연속(`then`), 조인 (`when_all`) 및 선택(`when_any`) 패턴을 사용하여 다른 작업으로 구성될 수도 있습니다.|
|[task_canceled 클래스](task-canceled-class.md)|이 클래스는 현재 작업을 강제 취소하도록 PPL 작업 레이어에서 throw된 예외를 설명합니다. 또한 `get()` 취소 된 작업에 대해 [작업](task-class.md)의 메서드에서 throw 됩니다.|
|[task_completion_event 클래스](task-completion-event-class.md)|`task_completion_event` 클래스를 사용하면 조건이 충족될 때까지 작업 실행을 지연하거나 외부 이벤트에 대한 응답으로 작업을 시작할 수 있습니다.|
|[task_continuation_context 클래스](task-continuation-context-class.md)|`task_continuation_context` 클래스를 사용하면 연속 실행 위치를 지정할 수 있습니다. UWP 앱에서이 클래스를 사용 하는 경우에만 유용 합니다. Windows 런타임 않는 앱의 경우 작업 연속의 실행 컨텍스트는 런타임에 의해 결정 되며 구성할 수 없습니다.|
|[task_group 클래스](task-group-class.md)|`task_group` 클래스는 대기하거나 취소할 수 있는 병렬 작업 컬렉션을 나타냅니다.|
|[task_handle 클래스](task-handle-class.md)|`task_handle` 클래스는 개별 병렬 작업 항목을 나타냅니다. 작업을 실행하는 데 필요한 지침 및 데이터를 캡슐화합니다.|
|[task_options 클래스 (동시성 런타임)](task-options-class-concurrency-runtime.md)|작업을 만드는 데 사용할 수 있는 옵션을 나타냅니다.|
|[timer 클래스](timer-class.md)|`timer` 메시징 블록은 지정된 기간이 경과한 후 또는 특정 간격마다 대상에 메시지를 보낼 수 있는 단일 대상 `source_block`입니다.|
|[변환기 클래스](transformer-class.md)|`transformer` 메시징 블록은 한 형식의 메시지를 수락하고 다른 형식의 메시지를 개수에 제한 없이 저장할 수 있는 순서가 지정된 단일 대상 다중 소스 `propagator_block`입니다.|
|[unbounded_buffer 클래스](unbounded-buffer-class.md)|`unbounded_buffer` 메시징 블록은 메시지를 개수에 제한 없이 저장할 수 있는, 순서가 지정된 다중 대상 다중 소스 `propagator_block`입니다.|
|[unsupported_os 클래스](unsupported-os-class.md)|이 클래스는 지원되지 않는 운영 체제를 사용할 때 throw되는 예외를 설명합니다.|

### <a name="structures"></a>구조체

|Name|설명|
|----------|-----------------|
|[DispatchState 구조체](dispatchstate-structure.md)|`DispatchState` 구조체는 `IExecutionContext::Dispatch` 메서드에 상태를 전송하는 데 사용됩니다. `IExecutionContext` 인터페이스에 대해 `Dispatch` 메서드가 호출되는 상황을 설명합니다.|
|[IExecutionContext 구조체](iexecutioncontext-structure.md)|지정된 가상 프로세서에서 실행되고 협조적으로 컨텍스트가 전환될 수 있는 실행 컨텍스트에 대한 인터페이스입니다.|
|[IExecutionResource 구조체](iexecutionresource-structure.md)|하드웨어 스레드에 대한 추상화입니다.|
|[IResourceManager 구조체](iresourcemanager-structure.md)|동시성 런타임의 리소스 관리자에 대한 인터페이스입니다. 스케줄러가 리소스 관리자와 통신하는 데 사용되는 인터페이스입니다.|
|[IScheduler 구조체](ischeduler-structure.md)|작업 스케줄러의 추상화에 대한 인터페이스입니다. 동시성 런타임의 리소스 관리자는 이 인터페이스를 사용하여 작업 스케줄러와 통신합니다.|
|[ISchedulerProxy 구조체](ischedulerproxy-structure.md)|스케줄러가 리소스 할당을 협상하기 위해 동시성 런타임의 리소스 관리자와 통신하는 데 사용되는 인터페이스입니다.|
|[IThreadProxy 구조체](ithreadproxy-structure.md)|실행 스레드에 대한 추상화입니다. 직접 만든 스케줄러의 `SchedulerType` 정책 키에 따라 리소스 관리자는 일반 Win32 스레드 또는 UMS(사용자 모드 예약 가능) 스레드 중 하나에서 지원되는 스레드 프록시를 부여합니다. UMS 스레드는 Windows 7 이상 버전의 64비트 운영 체제에서 지원됩니다.|
|[ITopologyExecutionResource 구조체](itopologyexecutionresource-structure.md)|리소스 관리자에 의해 정의된 실행 리소스에 대한 인터페이스입니다.|
|[ITopologyNode 구조체](itopologynode-structure.md)|리소스 관리자에 의해 정의된 토폴로지 노드에 대한 인터페이스입니다. 노드는 하나 이상의 실행 리소스를 포함합니다.|
|[IUMSCompletionList 구조체](iumscompletionlist-structure.md)|UMS 완성 목록을 나타냅니다. UMS 스레드가 차단되는 경우 원래 스레드가 차단되는 동안 기본 가상 프로세서 루트에 예약할 항목을 결정하기 위해 스케줄러의 지정된 일정 컨텍스트가 디스패치됩니다. 원래 스레드가 차단 해제되면 운영 체제에서 이 인터페이스를 통해 액세스할 수 있는 완성 목록에 대기시킵니다. 스케줄러는 지정된 일정 컨텍스트 또는 작업을 검색하는 다른 위치에 있는 완성 목록을 쿼리할 수 있습니다.|
|[IUMSScheduler 구조체](iumsscheduler-structure.md)|동시성 런타임의 리소스 관리자를 통해 UMS(사용자 모드 예약 가능) 스레드를 전달하려는 작업 스케줄러의 추상화에 대한 인터페이스입니다. 리소스 관리자는 이 인터페이스를 사용하여 UMS 스레드 스케줄러와 통신합니다. `IUMSScheduler` 인터페이스는 `IScheduler` 인터페이스에서 상속됩니다.|
|[IUMSThreadProxy 구조체](iumsthreadproxy-structure.md)|실행 스레드에 대한 추상화입니다. 해당 스케줄러에 UMS(사용자 모드 예약 가능) 스레드를 부여하려는 경우 스케줄러 정책 요소 `SchedulerKind`의 값을 `UmsThreadDefault`로 설정하고 `IUMSScheduler` 인터페이스를 구현합니다. UMS 스레드는 Windows 7 이상 버전의 64비트 운영 체제에서만 지원됩니다.|
|[IUMSUnblockNotification 구조체](iumsunblocknotification-structure.md)|차단되었으며 스케줄러의 지정된 일정 컨텍스트로의 반환을 트리거한 스레드 프록시가 차단 해제되고 예약할 준비가 되었다는 리소스 관리자의 알림을 나타냅니다. `GetContext` 메서드에서 반환된 스레드 프록시의 연결된 실행 컨텍스트가 다시 예약된 후에는 이 인터페이스가 유효하지 않습니다.|
|[IVirtualProcessorRoot 구조체](ivirtualprocessorroot-structure.md)|스레드 프록시가 실행될 수 있는 하드웨어 스레드의 추상화입니다.|
|[scheduler_interface 구조체](scheduler-interface-structure.md)|Scheduler 인터페이스|
|[scheduler_ptr 구조체(동시성 런타임)](scheduler-ptr-structure-concurrency-runtime.md)|스케줄러에 대한 포인터를 나타냅니다. 이 클래스는 shared_ptr를 사용 하거나 원시 포인터를 사용 하 여 일반 참조를 사용 하 여 공유 수명 사양을 허용 하기 위해 존재 합니다.|

### <a name="enumerations"></a>열거형

|Name|설명|
|----------|-----------------|
|[agent_status](concurrency-namespace-enums.md#agent_status)|`agent`에 유효한 상태입니다.|
|[Agents_EventType](concurrency-namespace-enums.md#agents_eventtype)|에이전트 라이브러리에서 제공하는 추적 기능을 사용하여 추적할 수 있는 이벤트 형식입니다.|
|[ConcRT_EventType](concurrency-namespace-enums.md#concrt_eventtype)|동시성 런타임에서 제공하는 추적 기능을 사용하여 추적할 수 있는 이벤트 형식입니다.|
|[Concrt_TraceFlags](concurrency-namespace-enums.md#concrt_traceflags)|이벤트 형식에 대한 추적 플래그입니다.|
|[CriticalRegionType](concurrency-namespace-enums.md#criticalregiontype)|컨텍스트가 있는 위험 영역의 형식입니다.|
|[DynamicProgressFeedbackType](concurrency-namespace-enums.md#dynamicprogressfeedbacktype)|`DynamicProgressFeedback` 정책에서 스케줄러에 대한 리소스를 스케줄러에서 수집한 통계 정보에 따라 균형을 조정할지, 아니면 `IVirtualProcessorRoot` 인터페이스의 `Activate` 및 `Deactivate` 메서드 호출을 통해 유휴 상태로 들어오고 나가는 가상 프로세서를 기준으로만 균형을 조정할지를 설명하는 데 사용됩니다. 사용 가능한 스케줄러 정책에 대 한 자세한 내용은 [Policyelementkey](concurrency-namespace-enums.md#policyelementkey)를 참조 하세요.|
|[join_type](concurrency-namespace-enums.md#join_type)|`join` 메시징 블록의 형식입니다.|
|[message_status](concurrency-namespace-enums.md#message_status)|블록에 대한 `message` 개체 제공에 유효한 응답입니다.|
|[PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)|스케줄러 동작의 측면을 설명하는 정책 키입니다. 각 정책 요소는 키-값 쌍으로 설명됩니다. 스케줄러 정책 및 스케줄러에 대 한 영향에 대 한 자세한 내용은 [작업 스케줄러](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)를 참조 하세요.|
|[SchedulerType](concurrency-namespace-enums.md#schedulertype)|`SchedulerKind` 정책에서 스케줄러가 기본 실행 컨텍스트에 활용해야 하는 스레드 형식을 설명하는 데 사용됩니다. 사용 가능한 스케줄러 정책에 대 한 자세한 내용은 [Policyelementkey](concurrency-namespace-enums.md#policyelementkey)를 참조 하세요.|
|[SchedulingProtocolType](concurrency-namespace-enums.md#schedulingprotocoltype)|`SchedulingProtocol` 정책에서 스케줄러에 활용되는 일정 알고리즘을 설명하는 데 사용됩니다. 사용 가능한 스케줄러 정책에 대 한 자세한 내용은 [Policyelementkey](concurrency-namespace-enums.md#policyelementkey)를 참조 하세요.|
|[SwitchingProxyState](concurrency-namespace-enums.md#switchingproxystate)|다른 스레드 프록시로의 협조적 컨텍스트 전환을 실행하는 경우 스레드 프록시의 현재 상태를 나타내는 데 사용됩니다.|
|[task_group_status](concurrency-namespace-enums.md#task_group_status)|`task_group` 또는 `structured_task_group` 개체의 실행 상태를 설명합니다. 이 형식의 값은 작업 그룹에 예약된 작업이 완료되기를 기다리는 수많은 메서드에 의해 반환됩니다.|
|[WinRTInitializationType](concurrency-namespace-enums.md#winrtinitializationtype)|`WinRTInitialization` 정책에서 Windows 8 또는 그 이상 버전의 운영 체제에서 실행되는 애플리케이션에 대한 스케줄러 스레드에서 Windows 런타임이 초기화될지 여부와 초기화되는 방법을 설명하는데 사용됩니다. 사용 가능한 스케줄러 정책에 대 한 자세한 내용은 [Policyelementkey](concurrency-namespace-enums.md#policyelementkey)를 참조 하세요.|

### <a name="functions"></a>함수

|Name|설명|
|----------|-----------------|
|[Alloc 함수](concurrency-namespace-functions.md#alloc)|동시성 런타임 캐싱 하위 할당기에서 지정된 크기의 메모리 블록을 할당합니다.|
|[asend 함수](concurrency-namespace-functions.md#asend)|오버로드됨. 대상 블록에 데이터를 전파하는 작업을 예약하는 비동기 전송 작업입니다.|
|[cancel_current_task 함수](concurrency-namespace-functions.md#cancel_current_task)|현재 실행 중인 작업을 취소합니다. 이 함수는 작업 실행을 중단하도록 작업 본문 내에서 호출될 수 있으며 `canceled` 상태로 들어가도록 할 수 있습니다.<br /><br /> `task`의 본문에 없는 경우에 이 함수를 호출하는 것은 지원되는 시나리오가 아닙니다. 이렇게 하면 응용 프로그램에서 충돌 또는 응답 하지 않는 등의 정의 되지 않은 동작이 발생 합니다.|
|[create_async 함수](concurrency-namespace-functions.md#create_async)|사용자가 제공한 람다 또는 함수 개체를 기준으로 Windows 런타임 비동기 구문을 만듭니다. `create_async`의 반환 형식은 메서드에 전달된 람다의 시그니처에 따라 `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^` 또는 `IAsyncOperationWithProgress<TResult, TProgress>^` 중 하나입니다.|
|[create_task 함수](concurrency-namespace-functions.md#create_task)|오버로드됨. PPL [작업](task-class.md) 개체를 만듭니다. 작업 생성자를 사용하는 곳이면 어디에나 `create_task`를 사용할 수 있습니다. 작업을 만드는 동안 키워드를 사용할 수 있기 때문에 주로 편의를 위해 제공 됩니다 **`auto`** .|
|[CreateResourceManager 함수](concurrency-namespace-functions.md#createresourcemanager)|동시성 런타임 리소스 관리자의 singleton 인스턴스를 나타내는 인터페이스를 반환합니다. 리소스 관리자는 서로 협력하려는 스케줄러에 리소스를 할당해야 합니다.|
|[DisableTracing 함수](concurrency-namespace-functions.md#disabletracing)|동시성 런타임에서 추적을 사용하지 않도록 설정합니다. ETW 추적이 기본적으로 등록되지 않으므로 이 함수는 사용되지 않습니다.|
|[EnableTracing 함수](concurrency-namespace-functions.md#enabletracing)|동시성 런타임에서 추적을 사용하도록 설정합니다. 이제 ETW 추적이 기본적으로 설정되므로 이 함수는 사용되지 않습니다.|
|[Free 함수](concurrency-namespace-functions.md#free)|`Alloc` 메서드에 의해 동시성 런타임 캐싱 하위 할당자에 이전에 할당된 메모리 블록을 해제합니다.|
|[get_ambient_scheduler 함수(동시성 런타임)](concurrency-namespace-functions.md#get_ambient_scheduler)||
|[GetExecutionContextId 함수](concurrency-namespace-functions.md#getexecutioncontextid)|`IExecutionContext` 인터페이스를 구현하는 실행 컨텍스트에 할당할 수 있는 고유 식별자를 반환합니다.|
|[GetOSVersion 함수](concurrency-namespace-functions.md#getosversion)|운영 체제 버전을 반환합니다.|
|[GetProcessorCount 함수](concurrency-namespace-functions.md#getprocessorcount)|기본 시스템의 하드웨어 스레드 수를 반환합니다.|
|[GetProcessorNodeCount 함수](concurrency-namespace-functions.md#getprocessornodecount)|기본 시스템의 NUMA 노드 또는 프로세서 패키지 수를 반환합니다.|
|[GetSchedulerId 함수](concurrency-namespace-functions.md#getschedulerid)|`IScheduler` 인터페이스를 구현하는 스케줄러에 할당할 수 있는 고유 식별자를 반환합니다.|
|[interruption_point 함수](concurrency-namespace-functions.md#interruption_point)|취소를 위한 중단 지점을 만듭니다. 이 함수가 호출된 컨텍스트에서 취소가 진행 중이면 현재 실행 중인 병렬 작업의 실행을 중단하는 내부 예외가 발생합니다. 취소가 진행되고 있지 않으면 함수에서 아무 작업도 하지 않습니다.|
|[is_current_task_group_canceling 함수](concurrency-namespace-functions.md#is_current_task_group_canceling)|현재 컨텍스트에서 현재 인라인으로 실행 중인 작업 그룹이 활성 취소 중이거나 곧 취소되는지 여부를 나타내는 표시를 반환합니다. 현재 컨텍스트에서 현재 인라인으로 실행 중인 작업 그룹이 없으면이 **`false`** 반환 됩니다.|
|[make_choice 함수](concurrency-namespace-functions.md#make_choice)|오버로드됨. 선택적 `choice` 또는 `Scheduler`과 두 개 이상의 입력 소스로 `ScheduleGroup` 메시징 블록을 생성합니다.|
|[make_greedy_join 함수](concurrency-namespace-functions.md#make_greedy_join)|오버로드됨. 선택적 `greedy multitype_join` 또는 `Scheduler`과 두 개 이상의 입력 소스로 `ScheduleGroup` 메시징 블록을 생성합니다.|
|[make_join 함수](concurrency-namespace-functions.md#make_join)|오버로드됨. 선택적 `non_greedy multitype_join` 또는 `Scheduler`과 두 개 이상의 입력 소스로 `ScheduleGroup` 메시징 블록을 생성합니다.|
|[make_task 함수](concurrency-namespace-functions.md#make_task)|`task_handle` 개체를 만들기 위한 팩터리 메서드입니다.|
|[parallel_buffered_sort 함수](concurrency-namespace-functions.md#parallel_buffered_sort)|오버로드됨. 지정 된 범위의 요소를 내림차순으로 정렬 하거나 이진 조건자로 지정한 정렬 기준에 따라 병렬로 정렬 합니다. 이 함수는 `O(n)` 추가 공간이 필요하고 정렬되는 요소에 대한 기본 초기화를 요구한다는 점을 제외하고, 비교 기반의 불안정한 내부 정렬이라는 점에서 `std::sort`와 의미 체계가 비슷합니다.|
|[parallel_for 함수](concurrency-namespace-functions.md#parallel_for)|오버로드됨. `parallel_for`는 일정 범위의 인덱스를 반복하고 각 반복 시 사용자가 제공한 함수를 병렬로 실행합니다.|
|[parallel_for_each 함수](concurrency-namespace-functions.md#parallel_for_each)|오버로드됨. `parallel_for_each`는 범위 내의 각 요소에 지정된 함수를 병렬로 적용합니다. 요소에 대한 반복이 병렬로 수행되고 반복 순서가 지정되지 않는다는 점을 제외하고 `std` 네임스페이스의 `for_each` 함수와 의미 체계가 같습니다. `_Func` 인수는 `operator()(T)` 형식의 함수 호출 연산자를 지원해야 합니다. 여기서 `T` 매개 변수는 반복되는 컨테이너의 항목 형식입니다.|
|[parallel_invoke 함수](concurrency-namespace-functions.md#parallel_invoke)|오버로드됨. 매개 변수로 제공된 함수 개체를 병렬로 실행하고 실행이 완료될 때까지 차단됩니다. 각 함수 개체는 람다 식, 함수에 대한 포인터 또는 `void operator()()` 서명을 사용하여 함수 호출 연산자를 지원하는 모든 개체일 수 있습니다.|
|[parallel_radixsort 함수](concurrency-namespace-functions.md#parallel_radixsort)|오버로드됨. 기수 정렬 알고리즘을 사용하여 지정된 범위의 요소를 비내림차순으로 정렬합니다. 부호 없는 정수와 유사한 키로 정렬할 요소를 프로젝션할 수 있는 프로젝션 함수를 요구하는 안정적인 정렬 함수입니다. 정렬되는 요소에 기본 초기화가 필요합니다.|
|[parallel_reduce 함수](concurrency-namespace-functions.md#parallel_reduce)|오버로드됨. 연속적 부분 합계를 계산하여 지정된 범위 내 모든 요소의 합계를 계산하거나, 합계 대신 지정된 이항 연산을 사용하여 유사하게 구한 연속적 부분 결과의 결과를 병렬로 계산합니다. `parallel_reduce`는 이항 연산이 결합형이어야 하고 초기 값 대신 ID 값을 요구한다는 점을 제외하고 `std::accumulate`와 의미 체계가 비슷합니다.|
|[parallel_sort 함수](concurrency-namespace-functions.md#parallel_sort)|오버로드됨. 지정 된 범위의 요소를 내림차순으로 정렬 하거나 이진 조건자로 지정한 정렬 기준에 따라 병렬로 정렬 합니다. 이 함수는 비교 기반의 불안정한 내부 정렬이라는 점에서 `std::sort`와 의미 체계가 비슷합니다.|
|[parallel_transform 함수](concurrency-namespace-functions.md#parallel_transform)|오버로드됨. 두 소스 범위에서 요소 쌍에 또는 소스 범위에 있는 각 요소에 지정된 함수 개체를 적용하고 대상 범위에 함수 개체의 반환 값을 병렬로 복사합니다. 이 함수는 `std::transform`과 의미 체계가 같습니다.|
|[receive 함수](concurrency-namespace-functions.md#receive)|오버로드됨. 컨텍스트에서 정확히 한 소스의 데이터를 대기하고 허용되는 값을 필터링할 수 있게 하는 일반 receive 구현입니다.|
|[run_with_cancellation_token 함수](concurrency-namespace-functions.md#run_with_cancellation_token)|지정된 취소 토큰의 컨텍스트에서 동기적으로 즉시 함수 개체를 실행합니다.|
|[send 함수](concurrency-namespace-functions.md#send)|오버로드됨. 대상이 메시지를 수락 또는 거절할 때까지 기다리는 동기 전송 작업입니다.|
|[set_ambient_scheduler 함수(동시성 런타임)](concurrency-namespace-functions.md#set_ambient_scheduler)||
|[set_task_execution_resources 함수](concurrency-namespace-functions.md#set_task_execution_resources)|오버로드됨. 동시성 런타임 내부 작업자 스레드가 사용하는 실행 리소스를 지정된 선호도 집합으로 제한합니다.<br /><br /> 리소스 관리자가 생성되기 전이나 두 리소스 관리자 수명 사이에만 이 메서드를 호출할 수 있습니다. 리소스 관리자가 호출 시 존재하지 않는 한 여러 번 호출할 수 있습니다. 선호도 제한이 설정된 후에는 다음 유효한 `set_task_execution_resources` 메서드 호출까지 적용된 상태로 유지됩니다.<br /><br /> 제공된 선호도 마스크는 프로세스 선호도 마스크의 하위 집합이 아니어야 합니다. 필요한 경우 프로세스 선호도가 업데이트됩니다.|
|[swap 함수](concurrency-namespace-functions.md#swap)|두 `concurrent_vector` 개체의 요소를 교환합니다.|
|[task_from_exception 함수(동시성 런타임)](concurrency-namespace-functions.md#task_from_exception)||
|[task_from_result 함수(동시성 런타임)](concurrency-namespace-functions.md#task_from_result)||
|[Trace_agents_register_name 함수](concurrency-namespace-functions.md#trace_agents_register_name)|ETW 추적에서 메시지 블록 또는 에이전트에 지정된 이름을 연결합니다.|
|[try_receive 함수](concurrency-namespace-functions.md#try_receive)|오버로드됨. 컨텍스트에서 정확히 한 소스의 데이터를 찾고 허용되는 값을 필터링할 수 있게 하는 일반 try-receive 구현입니다. 데이터가 준비되지 않은 경우 메서드가 false를 반환합니다.|
|[wait 함수](concurrency-namespace-functions.md#wait)|지정된 시간 동안 현재 컨텍스트를 일시 중지합니다.|
|[when_all 함수](concurrency-namespace-functions.md#when_all)|인수로 제공된 모든 작업이 성공적으로 완료될 경우 완료되는 작업을 만듭니다.|
|[when_any 함수](concurrency-namespace-functions.md#when_any)|오버로드됨. 인수로 제공된 모든 작업이 성공적으로 완료될 경우 완료되는 작업을 만듭니다.|

### <a name="operators"></a>연산자

|Name|설명|
|----------|-----------------|
|[연산자! =](concurrency-namespace-operators.md#operator_neq)|연산자의 좌변에 있는 `concurrent_vector` 개체가 우변에 있는 `concurrent_vector` 개체와 같지 않은지 테스트합니다.|
|[연산자&&](concurrency-namespace-operators.md#operator_amp_amp)|오버로드됨. 인수로 제공 된 두 작업이 모두 성공적으로 완료 되 면 완료 되는 작업을 만듭니다.|
|[operator&#124;&#124;](concurrency-namespace-operators.md#operator_lor)|오버로드됨. 인수로 제공된 작업 중 하나가 성공적으로 완료될 경우 완료되는 작업을 만듭니다.|
|[연산자<](concurrency-namespace-operators.md#operator_lt)|연산자의 좌변에 있는 `concurrent_vector` 개체가 우변에 있는 `concurrent_vector` 개체보다 작은지 테스트합니다.|
|[연산자<=](concurrency-namespace-operators.md#operator_lt_eq)|연산자의 좌변에 있는 `concurrent_vector` 개체가 우변에 있는 `concurrent_vector` 개체보다 작거나 같은지 테스트합니다.|
|[연산자 = =](concurrency-namespace-operators.md#operator_eq_eq)|연산자의 좌변에 있는 `concurrent_vector` 개체가 우변에 있는 `concurrent_vector` 개체와 같은지 테스트합니다.|
|[연산자>](concurrency-namespace-operators.md#operator_gt)|연산자의 좌변에 있는 `concurrent_vector` 개체가 우변에 있는 `concurrent_vector` 개체보다 큰지 테스트합니다.|
|[연산자>=](concurrency-namespace-operators.md#operator_lt_eq)|연산자의 좌변에 있는 `concurrent_vector` 개체가 우변에 있는 `concurrent_vector` 개체보다 크거나 같은지 테스트합니다.|

### <a name="constants"></a>상수

|Name|설명|
|----------|-----------------|
|[AgentEventGuid](concurrency-namespace-constants1.md#agenteventguid)|동시성 런타임의 에이전트 라이브러리에서 발생하는 ETW 이벤트를 설명하는 범주 GUID({B9B5B78C-0713-4898-A21A-C67949DCED07})입니다.|
|[ChoreEventGuid](concurrency-namespace-constants1.md#choreeventguid)|작업 또는 태스크와 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.|
|[ConcRT_ProviderGuid](concurrency-namespace-constants1.md#concrt_providerguid)|동시성 런타임에 대한 ETW 공급자 GUID입니다.|
|[CONCRT_RM_VERSION_1](concurrency-namespace-constants1.md#concrt_rm_version_1)|Visual Studio 2010에서 정의된 리소스 관리자 인터페이스의 지원을 나타냅니다.|
|[ConcRTEventGuid](concurrency-namespace-constants1.md#concrteventguid)|다른 범주에서 보다 구체적으로 설명되지 않은, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.|
|[ContextEventGuid](concurrency-namespace-constants1.md#contexteventguid)|컨텍스트와 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.|
|[COOPERATIVE_TIMEOUT_INFINITE](concurrency-namespace-constants1.md#cooperative_timeout_infinite)|대기 시간이 초과되지 않아야 함을 나타내는 값입니다.|
|[COOPERATIVE_WAIT_TIMEOUT](concurrency-namespace-constants1.md#cooperative_wait_timeout)|대기 시간이 초과되었음을 나타내는 값입니다.|
|[INHERIT_THREAD_PRIORITY](concurrency-namespace-constants1.md#inherit_thread_priority)|스케줄러의 모든 컨텍스트에 대한 스레드 우선순위가 스케줄러를 만든 스레드의 우선순위와 같아야 함을 나타내는 정책 키 `ContextPriority`에 대한 특수 값입니다.|
|[LockEventGuid](concurrency-namespace-constants1.md#lockeventguid)|잠금과 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.|
|[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)|정책 키 `MinConcurrency` 및 `MaxConcurrency`에 대한 특수 값입니다. 기본값은 다른 제약 조건이 없는 경우 컴퓨터의 하드웨어 스레드 수입니다.|
|[PPLParallelForeachEventGuid](concurrency-namespace-constants1.md#pplparallelforeacheventguid)|`parallel_for_each` 함수 사용과 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.|
|[PPLParallelForEventGuid](concurrency-namespace-constants1.md#pplparallelforeventguid)|`parallel_for` 함수 사용과 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.|
|[PPLParallelInvokeEventGuid](concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|`parallel_invoke` 함수 사용과 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.|
|[ResourceManagerEventGuid](concurrency-namespace-constants1.md#resourcemanagereventguid)|리소스 관리자와 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.|
|[ScheduleGroupEventGuid](concurrency-namespace-constants1.md#schedulegroupeventguid)|일정 그룹과 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.|
|[SchedulerEventGuid](concurrency-namespace-constants1.md#schedulereventguid)|스케줄러 작업과 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.|
|[VirtualProcessorEventGuid](concurrency-namespace-constants1.md#virtualprocessoreventguid)|가상 프로세서와 직접 관련된, 동시성 런타임에서 발생하는 ETW 이벤트를 설명하는 범주 GUID입니다.|

## <a name="requirements"></a>요구 사항

**헤더:** pplconcrt.h, concrt. h, concrtrm.h, concurrent_priority_queue .h, concurrent_queue, concurrent_unordered_map .h, concurrent_unordered_set, concurrent_vector, internal_concurrent_hash, internal_split_ordered_list, ppl, pplcancellation_token, pplinterface.h, ppltasks.h,. h,. h,,

## <a name="see-also"></a>참고 항목

[참조](reference-concurrency-runtime.md)
