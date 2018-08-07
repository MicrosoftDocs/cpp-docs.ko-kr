---
title: 스케줄러 정책 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d9c855260df34290d01f1eeeee89e8bfe8988de
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690409"
---
# <a name="scheduler-policies"></a>Scheduler 정책
이 문서에서는 동시성 런타임에서 스케줄러 정책의 역할을 설명 합니다. A *스케줄러 정책을* 스케줄러가 작업을 관리할 때 사용 하는 전략을 제어 합니다. 예를 들어, 일부 작업은 `THREAD_PRIORITY_NORMAL`에서 실행해야 하고 다른 작업은 `THREAD_PRIORITY_HIGHEST`에서 실행해야 하는 응용 프로그램을 고려해 보겠습니다.  두 가지 스케줄러 인스턴스를 만들 수 있으며, 하나는 `ContextPriority` 정책을 `THREAD_PRIORITY_NORMAL`로 지정하고, 다른 하나는 동일한 정책을 `THREAD_PRIORITY_HIGHEST`로 지정합니다.  
  
 스케줄러 정책을 사용하면 사용 가능한 처리 리소스를 나누고 고정된 리소스 집합을 각 스케줄러에 할당할 수 있습니다. 4 개의 프로세서 개로 확장 병렬 알고리즘을 예로 들 수 있습니다. 동시에 최대 4 개의 프로세서를 사용 하 여 작업을 제한 하는 스케줄러 정책을 만들 수 있습니다.  
  
> [!TIP]
>  동시성 런타임에서는 기본 스케줄러를 제공합니다. 따라서 응용 프로그램에서 만들 필요가 없습니다. 작업 스케줄러를 사용 하면 응용 프로그램의 성능을 미세 조정할 수 있습니다, 때문에로 시작 하는 것이 좋습니다는 [라이브러리 PPL (병렬 패턴)](../../parallel/concrt/parallel-patterns-library-ppl.md) 또는 [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md) 하려는 경우 동시성 런타임으로 새입니다.  
  
 사용 하는 경우는 [concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create), [concurrency::Scheduler::Create](reference/scheduler-class.md#create), 또는 [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) 메서드를 제공 하는 스케줄러 인스턴스를 만듭니다는 [concurrency:: schedulerpolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) 스케줄러의 동작을 지정 하는 키-값 쌍의 컬렉션을 포함 하는 개체입니다. `SchedulerPolicy` 생성자의 인수 수를 사용 합니다. 첫 번째 인수가 지정 하려고 하는 정책 요소 수를 보여 줍니다. 나머지 인수는 각 정책 요소에 대 한 키-값 쌍입니다. 다음 예제에서는 한 `SchedulerPolicy` 세 가지 정책 요소를 지정 하는 개체입니다. 런타임에서는 지정되지 않은 정책 키에 대해 기본값을 사용합니다.  

  
 [!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]  
  

 [concurrency:: policyelementkey](reference/concurrency-namespace-enums.md#policyelementkey) 열거형은 작업 스케줄러와 연결 된 정책 키를 정의 합니다. 다음 표에서 각 끝점에 런타임이 사용 하는 기본값 및 정책 키를 설명 합니다.  
  
|정책 키|설명|기본값|  
|----------------|-----------------|-------------------|  
|`SchedulerKind`|A [concurrency:: schedulertype](reference/concurrency-namespace-enums.md#schedulertype) 작업 일정을 사용 하는 스레드 형식을 지정 하는 값입니다.|`ThreadScheduler`(일반 스레드 사용) 이 키에 유효한 유일한 값입니다.|  
|`MaxConcurrency`|`unsigned int` 스케줄러를 사용 하는 동시성 리소스의 최대 수를 지정 하는 값입니다.|[concurrency::MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources)|  
|`MinConcurrency`|`unsigned int` 스케줄러를 사용 하는 동시성 리소스의 최소 수를 지정 하는 값입니다.|`1`|  
|`TargetOversubscriptionFactor`|`unsigned int` 각 처리 리소스를 할당할 스레드의 수를 지정 하는 값입니다.|`1`|  
|`LocalContextCacheSize`|`unsigned int` 각 가상 프로세서의 로컬 큐에 캐시 될 수 있는 컨텍스트의 최대 수를 지정 하는 값입니다.|`8`|  
|`ContextStackSize`|`unsigned int` (킬로바이트) 각 컨텍스트에 대 한 예약 하는 스택 크기를 지정 하는 값입니다.|`0` (기본 스택 크기를 사용 하 여)|  
|`ContextPriority`|`int` 컨텍스트마다의 스레드 우선 순위를 지정 하는 값입니다. 이에 전달할 수 있는 모든 값이 될 수 있습니다 [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) 또는 `INHERIT_THREAD_PRIORITY`합니다.|`THREAD_PRIORITY_NORMAL`|  

|`SchedulingProtocol`| A [concurrency:: schedulingprotocoltype](reference/concurrency-namespace-enums.md#schedulingprotocoltype) 사용할 예약 알고리즘을 지정 하는 값입니다. |`EnhanceScheduleGroupLocality`|  
|`DynamicProgressFeedback`| A [concurrency:: dynamicprogressfeedbacktype](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) 통계에 기반한 진행 정보에 따라 리소스를 다시 분산 여부를 지정 하는 값입니다.<br /><br /> **참고** 이 정책을 설정 하지 않으면 `ProgressFeedbackDisabled` 런타임에서 사용 하기 위해 예약 되어 있으므로. |`ProgressFeedbackEnabled`|  

  
 각 스케줄러 작업을 예약할 때 자체 정책을 사용 합니다. 한 스케줄러와 연결된 정책은 다른 스케줄러의 동작에 영향을 주지 않습니다. 만든 후 스케줄러 정책을 변경할 수 없습니다 또한는 `Scheduler` 개체입니다.  
  
> [!IMPORTANT]
>  스케줄러 정책에 대 한를 사용 하 여 런타임에서 만든 스레드에 대 한 특성을 제어 합니다. 정의되지 않은 동작이 발생할 수 있기 때문에 런타임에서 생성된 스레드의 스레드 선호도 또는 우선 순위를 변경하지 마십시오.  
  
 런타임에서는 명시적으로 만들지 않으면 하나 하는 경우 기본 스케줄러를 만듭니다. 응용 프로그램에서 기본 스케줄러를 사용 하려고 하지만 호출를 사용 하도록 해당 스케줄러에 대 한 정책을 지정 하려는 경우는 [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) 병렬 작업을 예약 하기 전에 메서드. 호출 하지 않으면는 `Scheduler::SetDefaultSchedulerPolicy` 메서드, 기본 정책 값 테이블에서 사용 하 여 런타임입니다.  
  
 사용 하 여는 [concurrency::CurrentScheduler::GetPolicy](reference/currentscheduler-class.md#getpolicy) 및 [concurrency::Scheduler::GetPolicy](reference/scheduler-class.md#getpolicy) 스케줄러 정책의 복사본을 검색 하는 메서드. 이러한 방법 중에서 수신 하는 정책 값은 스케줄러를 만들 때 지정 하는 정책 값은 다를 수 있습니다.  
  
## <a name="example"></a>예제  
 스케줄러의 동작을 제어 하려면 특정 스케줄러 정책을 사용 하는 예제를 검사 하려면 참조 [하는 방법: 특정 스케줄러 정책 지정](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) 및 [하는 방법: 에이전트를 사용 하 여 특정 스케줄러 정책만들기](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).  
  
## <a name="see-also"></a>참고 항목  
 [작업 스케줄러](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [방법: 특정 스케줄러 정책 지정](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)   
 [방법: 특정 스케줄러 정책을 사용하는 에이전트 만들기](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

