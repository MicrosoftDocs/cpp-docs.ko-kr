---
description: '다음에 대 한 자세한 정보: Scheduler 인스턴스'
title: 스케줄러 인스턴스
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
ms.openlocfilehash: a11c22815c7a73c39033e51ccf47a64ceb47a92d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188055"
---
# <a name="scheduler-instances"></a>스케줄러 인스턴스

이 문서에서는 동시성 런타임의 스케줄러 인스턴스 역할 및 [concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md) 및 [Concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md) 클래스를 사용 하 여 스케줄러 인스턴스를 만들고 관리 하는 방법에 대해 설명 합니다. 스케줄러 인스턴스는 명시적 일정 정책에 특정 유형의 작업을 연결 하려는 경우에 유용 합니다. 예를 들어 높은 스레드 우선 순위로 일부 작업을 실행하기 위한 스케줄러 인스턴스를 하나 만들고, 기본 스케줄러를 사용하여 보통 스레드 우선 순위로 다른 작업을 실행할 수 있습니다.

> [!TIP]
> 동시성 런타임은 기본 스케줄러를 제공하므로 애플리케이션에서 스케줄러를 만들 필요가 없습니다. 작업 스케줄러는 응용 프로그램의 성능을 미세 조정 하는 데 도움이 되므로 동시성 런타임를 처음 접하는 경우 [PPL (병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md) 또는 [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md) 를 사용 하는 것이 좋습니다.

## <a name="sections"></a><a name="top"></a> 섹션이

- [Scheduler 및 CurrentScheduler 클래스](#classes)

- [스케줄러 인스턴스 만들기](#creating)

- [스케줄러 인스턴스의 수명 관리](#managing)

- [메서드 및 기능](#features)

- [예제](#example)

## <a name="the-scheduler-and-currentscheduler-classes"></a><a name="classes"></a> Scheduler 및 CurrentScheduler 클래스

작업 스케줄러를 사용 하면 응용 프로그램에서 하나 이상의 *스케줄러 인스턴스* 를 사용 하 여 작업을 예약할 수 있습니다. [Concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md) 클래스는 스케줄러 인스턴스를 나타내며 작업 예약과 관련 된 기능을 캡슐화 합니다.

스케줄러에 연결 된 스레드를 *실행 컨텍스트나* *컨텍스트* 라고 합니다. 언제 든 지 현재 컨텍스트에서 하나의 스케줄러를 활성화할 수 있습니다. 활성 스케줄러는 *현재 스케줄러* 라고도 합니다. 동시성 런타임 [Concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md) 클래스를 사용 하 여 현재 스케줄러에 대 한 액세스를 제공 합니다. 한 컨텍스트의 현재 스케줄러는 다른 컨텍스트의 현재 스케줄러와 다를 수 있습니다. 런타임에서는 현재 스케줄러의 프로세스 수준 표현을 제공 하지 않습니다.

일반적으로 `CurrentScheduler` 클래스는 현재 스케줄러에 액세스 하는 데 사용 됩니다. `Scheduler`클래스는 현재가 아닌 스케줄러를 관리 해야 하는 경우에 유용 합니다.

다음 섹션에서는 스케줄러 인스턴스를 만들고 관리 하는 방법을 설명 합니다. 이러한 작업을 설명 하는 전체 예제는 [방법: 스케줄러 인스턴스 관리](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="creating-a-scheduler-instance"></a><a name="creating"></a> 스케줄러 인스턴스 만들기

다음 세 가지 방법으로 개체를 만들 수 있습니다 `Scheduler` .

- 스케줄러가 없으면 런타임에 병렬 알고리즘과 같은 런타임 기능을 사용 하 여 작업을 수행할 때 기본 스케줄러를 만듭니다. 기본 스케줄러는 병렬 작업을 시작 하는 컨텍스트에 대 한 현재 스케줄러가 됩니다.

- [Concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create) 메서드는 `Scheduler` 특정 정책을 사용 하는 개체를 만들고 해당 스케줄러를 현재 컨텍스트와 연결 합니다.

- [Concurrency:: Scheduler:: Create](reference/scheduler-class.md#create) 메서드는 `Scheduler` 특정 정책을 사용 하는 개체를 만들지만 현재 컨텍스트와 연결 하지 않습니다.

런타임이 기본 스케줄러를 만들도록 허용 하면 모든 동시 태스크가 동일한 스케줄러를 공유할 수 있습니다. 일반적으로 PPL ( [병렬 패턴 라이브러리](../../parallel/concrt/parallel-patterns-library-ppl.md) ) 또는 [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md) 에서 제공 하는 기능은 병렬 작업을 수행 하는 데 사용 됩니다. 따라서 해당 정책 또는 수명을 제어 하기 위해 스케줄러와 직접 작업 하지 않아도 됩니다. PPL 또는 에이전트 라이브러리를 사용 하는 경우 런타임에서 기본 스케줄러를 만들어 각 컨텍스트에 대 한 현재 스케줄러로 만듭니다. 스케줄러를 만들어 현재 스케줄러로 설정 하면 런타임에서는 해당 스케줄러를 사용 하 여 작업을 예약 합니다. 특정 일정 예약 정책을 필요로 하는 경우에만 추가 스케줄러 인스턴스를 만듭니다. 스케줄러와 연결 된 정책에 대 한 자세한 내용은 [Scheduler 정책](../../parallel/concrt/scheduler-policies.md)을 참조 하십시오.

[[맨 위로](#top)이동]

## <a name="managing-the-lifetime-of-a-scheduler-instance"></a><a name="managing"></a> 스케줄러 인스턴스의 수명 관리

런타임은 참조 횟수 메커니즘을 사용 하 여 개체의 수명을 제어 `Scheduler` 합니다.

메서드나 메서드를 사용 하 여 `CurrentScheduler::Create` `Scheduler::Create` 개체를 만드는 경우 `Scheduler` 런타임은 해당 스케줄러의 초기 참조 횟수를 1로 설정 합니다. [Concurrency:: Scheduler:: Attach](reference/scheduler-class.md#attach) 메서드를 호출 하면 런타임에서 참조 횟수를 증가 시킵니다. `Scheduler::Attach`메서드는 개체를 `Scheduler` 현재 컨텍스트와 함께 연결 합니다. 이렇게 하면 현재 스케줄러로 설정 됩니다. 메서드를 호출 하면 `CurrentScheduler::Create` 런타임에서 개체를 만들어 `Scheduler` 현재 컨텍스트에 연결 하 고 참조 횟수를 1로 설정 합니다. [Concurrency:: Scheduler:: reference](reference/scheduler-class.md#reference) 메서드를 사용 하 여 개체의 참조 횟수를 증가 시킬 수도 있습니다 `Scheduler` .

[Concurrency:: CurrentScheduler::D etach](reference/currentscheduler-class.md#detach) 메서드를 호출 하 여 현재 스케줄러를 분리 하거나 [Concurrency:: Scheduler:: Release](reference/scheduler-class.md#release) 메서드를 호출 하면 런타임에서 참조 횟수를 감소 시킵니다. 참조 횟수가 0에 도달 하면 런타임은 `Scheduler` 모든 예약 된 작업이 완료 된 후에 개체를 소멸 시킵니다. 실행 중인 태스크가 현재 스케줄러의 참조 횟수를 증가 시킬 수 있습니다. 따라서 참조 횟수가 0에 도달 하 고 작업이 참조 횟수를 증가 시키는 경우 `Scheduler` 참조 횟수가 다시 0에 도달 하 고 모든 작업이 완료 될 때까지 런타임에서 개체가 삭제 되지 않습니다.

런타임은 `Scheduler` 각 컨텍스트에 대 한 개체의 내부 스택을 유지 합니다. 또는 메서드를 호출 `Scheduler::Attach` 하면 `CurrentScheduler::Create` 런타임에서 `Scheduler` 현재 컨텍스트의 스택에 해당 개체를 푸시합니다. 이렇게 하면 현재 스케줄러로 설정 됩니다. 를 호출 하면 `CurrentScheduler::Detach` 런타임에서 현재 컨텍스트의 현재 스케줄러를 팝 하 고 이전 스케줄러를 현재 스케줄러로 설정 합니다.

런타임은 스케줄러 인스턴스의 수명을 관리 하는 여러 가지 방법을 제공 합니다. 다음 표에서는 스케줄러를 만들거나 현재 컨텍스트에 연결 하는 각 메서드에 대 한 현재 컨텍스트에서 스케줄러를 해제 하거나 분리 하는 적절 한 메서드를 보여 줍니다.

|만들기 또는 연결 방법|Release 또는 detach 메서드|
|-----------------------------|------------------------------|
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|
|`Scheduler::Create`|`Scheduler::Release`|
|`Scheduler::Attach`|`CurrentScheduler::Detach`|
|`Scheduler::Reference`|`Scheduler::Release`|

부적절 한 릴리스 또는 분리 메서드를 호출 하면 런타임에서 지정 되지 않은 동작이 생성 됩니다.

PPL과 같은 기능을 사용 하 여 런타임에서 기본 스케줄러를 만들도록 하면이 스케줄러를 해제 하거나 분리 하지 마십시오. 런타임은 만들어진 모든 스케줄러의 수명을 관리 합니다.

런타임은 `Scheduler` 모든 작업이 완료 되기 전에 개체를 소멸 시 키 지 않으므로 [concurrency:: Scheduler:: RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) 메서드 또는 [Concurrency:: Currentscheduler:: RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) 메서드를 사용 하 여 개체가 소멸 될 때 알림을 받을 수 있습니다 `Scheduler` . 이는 개체에 예약 된 모든 작업이 완료 될 때까지 기다려야 하는 경우에 유용 `Scheduler` 합니다.

[[맨 위로](#top)이동]

## <a name="methods-and-features"></a><a name="features"></a> 메서드 및 기능

이 섹션에서는 및 클래스의 중요 한 메서드를 요약 합니다 `CurrentScheduler` `Scheduler` .

`CurrentScheduler`클래스는 현재 컨텍스트에서 사용할 스케줄러를 만들기 위한 도우미로 생각 하면 됩니다. `Scheduler`클래스를 사용 하면 다른 컨텍스트에 속한 스케줄러를 제어할 수 있습니다.

다음 표에서는 클래스에 의해 정의 되는 중요 한 메서드를 보여 줍니다 `CurrentScheduler` .

|메서드|Description|
|------------|-----------------|
|[만들기](reference/currentscheduler-class.md#create)|지정 된 `Scheduler` 정책을 사용 하는 개체를 만들고 현재 컨텍스트와 연결 합니다.|
|[가져오기](reference/currentscheduler-class.md#get)|현재 컨텍스트와 연결 된 개체에 대 한 포인터를 검색 `Scheduler` 합니다. 이 메서드는 개체의 참조 횟수를 증가 시 지 않습니다 `Scheduler` .|
|[분리](reference/currentscheduler-class.md#detach)|현재 컨텍스트에서 현재 스케줄러를 분리 하 고 이전 스케줄러를 현재 스케줄러로 설정 합니다.|
|[RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)|현재 스케줄러가 제거 될 때 런타임에서 설정 하는 이벤트를 등록 합니다.|
|[CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)|현재 스케줄러에 [concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) 개체를 만듭니다.|
|[ScheduleTask](reference/currentscheduler-class.md#scheduletask)|현재 스케줄러의 일정 큐에 간단한 작업을 추가 합니다.|
|[GetPolicy](reference/currentscheduler-class.md#getpolicy)|현재 스케줄러에 연결 된 정책의 복사본을 검색 합니다.|

다음 표에서는 클래스에 의해 정의 되는 중요 한 메서드를 보여 줍니다 `Scheduler` .

|메서드|Description|
|------------|-----------------|
|[만들기](reference/scheduler-class.md#create)|지정 된 `Scheduler` 정책을 사용 하는 개체를 만듭니다.|
|[연결](reference/scheduler-class.md#attach)|개체를 `Scheduler` 현재 컨텍스트와 함께 연결 합니다.|
|[참조](reference/scheduler-class.md#reference)|개체의 참조 카운터를 증가 시킵니다 `Scheduler` .|
|[릴리스](reference/scheduler-class.md#release)|개체의 참조 카운터를 감소 시킵니다 `Scheduler` .|
|[RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)|개체가 소멸 될 때 런타임에서 설정 하는 이벤트를 등록 `Scheduler` 합니다.|
|[CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)|개체에 [concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) 개체를 만듭니다 `Scheduler` .|
|[ScheduleTask](reference/scheduler-class.md#scheduletask)|개체에서 간단한 작업을 예약 `Scheduler` 합니다.|
|[GetPolicy](reference/scheduler-class.md#getpolicy)|개체와 연결 된 정책의 복사본을 검색 합니다 `Scheduler` .|
|[SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)|런타임에 기본 스케줄러를 만들 때 사용할 정책을 설정 합니다.|
|[ResetDefaultSchedulerPolicy](reference/scheduler-class.md#resetdefaultschedulerpolicy)|에 대 한 호출 이전에 활성화 된 정책을 기본 정책으로 복원 `SetDefaultSchedulerPolicy` 합니다. 이 호출 후 기본 스케줄러를 만든 경우 런타임은 기본 정책 설정을 사용 하 여 스케줄러를 만듭니다.|

[[맨 위로](#top)이동]

## <a name="example"></a><a name="example"></a> 예

스케줄러 인스턴스를 만들고 관리 하는 방법에 대 한 기본 예제 [는 방법: 스케줄러 인스턴스 관리](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[작업 Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[방법: 스케줄러 인스턴스 관리](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[스케줄러 정책](../../parallel/concrt/scheduler-policies.md)<br/>
[일정 그룹](../../parallel/concrt/schedule-groups.md)
