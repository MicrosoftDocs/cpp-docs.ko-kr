---
description: '자세한 정보: Scheduler 정책'
title: Scheduler 정책
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: 42b5fa951c320fcc3bab8fe5abe3bb4988e6c368
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188016"
---
# <a name="scheduler-policies"></a>Scheduler 정책

이 문서에서는 동시성 런타임의 스케줄러 정책 역할에 대해 설명 합니다. *Scheduler 정책은* 스케줄러에서 작업을 관리 하는 데 사용 하는 전략을 제어 합니다. 예를 들어, 일부 작업은 `THREAD_PRIORITY_NORMAL`에서 실행해야 하고 다른 작업은 `THREAD_PRIORITY_HIGHEST`에서 실행해야 하는 애플리케이션을 고려해 보겠습니다.  두 가지 스케줄러 인스턴스를 만들 수 있으며, 하나는 `ContextPriority` 정책을 `THREAD_PRIORITY_NORMAL`로 지정하고, 다른 하나는 동일한 정책을 `THREAD_PRIORITY_HIGHEST`로 지정합니다.

스케줄러 정책을 사용하면 사용 가능한 처리 리소스를 나누고 고정된 리소스 집합을 각 스케줄러에 할당할 수 있습니다. 예를 들어 4 개의 프로세서 이상으로 확장 되지 않는 병렬 알고리즘을 고려 합니다. 4 개 이하의 프로세서를 동시에 사용 하도록 제한 하는 스케줄러 정책을 만들 수 있습니다.

> [!TIP]
> 동시성 런타임에서는 기본 스케줄러를 제공합니다. 따라서 애플리케이션에서 만들 필요가 없습니다. 작업 스케줄러는 응용 프로그램의 성능을 미세 조정 하는 데 도움이 되므로 동시성 런타임를 처음 접하는 경우 [PPL (병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md) 또는 [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md) 를 사용 하는 것이 좋습니다.

[Concurrency:: CurrentScheduler:: create](reference/currentscheduler-class.md#create), [Concurrency:: Scheduler:: create](reference/scheduler-class.md#create)또는 [concurrency:: scheduler:: SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) 메서드를 사용 하 여 스케줄러 인스턴스를 만드는 경우 scheduler의 동작을 지정 하는 키-값 쌍의 컬렉션을 포함 하는 [concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) 개체를 제공 합니다. 생성자는 다양 `SchedulerPolicy` 한 수의 인수를 사용 합니다. 첫 번째 인수는 지정 하려는 정책 요소의 수입니다. 나머지 인수는 각 정책 요소에 대 한 키-값 쌍입니다. 다음 예제에서는 `SchedulerPolicy` 3 개의 정책 요소를 지정 하는 개체를 만듭니다. 런타임에서는 지정되지 않은 정책 키에 대해 기본값을 사용합니다.

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

[Concurrency::P olicyelementkey](reference/concurrency-namespace-enums.md#policyelementkey) 열거형은 작업 스케줄러와 연결 된 정책 키를 정의 합니다. 다음 표에서는 런타임에서 각각에 대해 사용 하는 정책 키와 기본값에 대해 설명 합니다.

| 정책 키 | 설명 | 기본값 |
|--|--|--|
| `SchedulerKind` | 작업을 예약 하는 데 사용할 스레드 형식을 지정 하는 [concurrency:: SchedulerType](reference/concurrency-namespace-enums.md#schedulertype) 값입니다. | `ThreadScheduler`(일반 스레드 사용) 이 키에 유효한 유일한 값입니다. |
| `MaxConcurrency` | **`unsigned int`** 스케줄러에서 사용 하는 최대 동시성 리소스 수를 지정 하는 값입니다. | [concurrency::MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources) |
| `MinConcurrency` | **`unsigned int`** 스케줄러에서 사용 하는 최소 동시성 리소스 수를 지정 하는 값입니다. | `1` |
| `TargetOversubscriptionFactor` | **`unsigned int`** 각 처리 리소스에 할당할 스레드 수를 지정 하는 값입니다. | `1` |
| `LocalContextCacheSize` | **`unsigned int`** 각 가상 프로세서의 로컬 큐에 캐시할 수 있는 최대 컨텍스트 수를 지정 하는 값입니다. | `8` |
| `ContextStackSize` | **`unsigned int`** 각 컨텍스트에 대해 예약할 스택 크기 (kb)를 지정 하는 값입니다. | `0` (기본 스택 크기 사용) |
| `ContextPriority` | **`int`** 각 컨텍스트의 스레드 우선 순위를 지정 하는 값입니다. [Setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 또는에 전달할 수 있는 모든 값일 수 있습니다 `INHERIT_THREAD_PRIORITY` . | `THREAD_PRIORITY_NORMAL` |
| `SchedulingProtocol` | 사용할 예약 알고리즘을 지정 하는 [concurrency:: SchedulingProtocolType](reference/concurrency-namespace-enums.md#schedulingprotocoltype) 값입니다. | `EnhanceScheduleGroupLocality` |
| `DynamicProgressFeedback` | [동시성:D:](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) 통계 기반 진행률 정보에 따라 리소스의 균형을 ynamicprogressfeedbacktype 여부를 지정 하는 값입니다.<br /><br /> **참고** `ProgressFeedbackDisabled` 런타임에서 사용 하기 위해 예약 되어 있으므로이 정책을로 설정 하지 마세요. | `ProgressFeedbackEnabled` |

각 스케줄러는 작업을 예약할 때 자체 정책을 사용 합니다. 한 스케줄러와 연결된 정책은 다른 스케줄러의 동작에 영향을 주지 않습니다. 또한 개체를 만든 후에는 스케줄러 정책을 변경할 수 없습니다 `Scheduler` .

> [!IMPORTANT]
> 스케줄러 정책만 사용 하 여 런타임에서 만드는 스레드의 특성을 제어 합니다. 정의되지 않은 동작이 발생할 수 있기 때문에 런타임에서 생성된 스레드의 스레드 선호도 또는 우선 순위를 변경하지 마십시오.

명시적으로 만들지 않은 경우 런타임에서 기본 스케줄러를 만듭니다. 응용 프로그램에서 기본 스케줄러를 사용 하려고 하지만 해당 스케줄러에서 사용할 정책을 지정 하려는 경우 병렬 작업을 예약 하기 전에 [concurrency:: scheduler:: SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) 메서드를 호출 합니다. 메서드를 호출 하지 않으면 `Scheduler::SetDefaultSchedulerPolicy` 런타임에서는 테이블의 기본 정책 값을 사용 합니다.

Concurrency: [: CurrentScheduler:: getpolicy](reference/currentscheduler-class.md#getpolicy) 및 [Concurrency:: Scheduler:: getpolicy](reference/scheduler-class.md#getpolicy) 메서드를 사용 하 여 스케줄러 정책의 복사본을 검색 합니다. 이러한 메서드에서 받는 정책 값은 스케줄러를 만들 때 지정 하는 정책 값과 다를 수 있습니다.

## <a name="example"></a>예제

특정 스케줄러 정책을 사용 하 여 scheduler의 동작을 제어 하는 예제를 확인 하려면 [방법: 특정 스케줄러 정책 지정](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) 및 [방법: 특정 스케줄러 정책을 사용 하는 에이전트 만들기](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[작업 Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[방법: 특정 스케줄러 정책 지정](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[방법: 특정 스케줄러 정책을 사용 하는 에이전트 만들기](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
