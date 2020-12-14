---
description: '자세한 정보: 일정 그룹'
title: 일정 그룹
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
ms.openlocfilehash: bee4f20ae58f94ddad93770232028df7b82dd39e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188068"
---
# <a name="schedule-groups"></a>일정 그룹

이 문서에서는 동시성 런타임에서 일정 그룹의 역할을 설명 합니다. *일정 그룹* 은 관련 된 작업을 선호도 하거나 그룹화 합니다. 모든 스케줄러에는 하나 이상의 일정 그룹이 있습니다. 작업 간에 높은 수준의 국부성이 필요한 경우, 예를 들어 동일한 프로세서 노드에서 관련 작업 그룹을 실행하면 이점이 있는 경우 일정 그룹을 사용합니다. 반대로, 작업 집합에 할당 되는 처리 리소스의 양을 제한 하려는 경우와 같이 응용 프로그램에 특정 품질 요구 사항이 있는 경우 스케줄러 인스턴스를 사용 합니다. Scheduler 인스턴스에 대 한 자세한 내용은 [Scheduler instances](../../parallel/concrt/scheduler-instances.md)을 참조 하세요.

> [!TIP]
> 동시성 런타임은 기본 스케줄러를 제공하므로 애플리케이션에서 스케줄러를 만들 필요가 없습니다. 작업 스케줄러는 응용 프로그램의 성능을 미세 조정 하는 데 도움이 되므로 동시성 런타임를 처음 접하는 경우 [PPL (병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md) 또는 [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md) 를 사용 하는 것이 좋습니다.

모든 `Scheduler` 개체에는 일정 노드에 대 한 기본 일정 그룹이 있습니다. *일정 노드* 는 기본 시스템 토폴로지에 매핑됩니다. 런타임은 모든 프로세서 패키지 또는 NUMA (Non-uniform Memory Architecture) 노드에 대해 하나의 일정 노드를 만듭니다 .이 노드 수는 더 큽니다. 작업을 일정 그룹에 명시적으로 연결 하지 않으면 스케줄러에서 작업을 추가할 그룹을 선택 합니다.

`SchedulingProtocol`Scheduler 정책은 스케줄러가 각 일정 그룹의 작업을 실행 하는 순서에 영향을 미칩니다. `SchedulingProtocol`가 (기본값)로 설정 된 경우 `EnhanceScheduleGroupLocality` 작업 스케줄러는 현재 태스크가 완료 되거나 협조적으로 생성 될 때 작업 중인 일정 그룹에서 다음 작업을 선택 합니다. 작업 스케줄러는 현재 일정 그룹에서 사용 가능한 다음 그룹으로 이동 하기 전에 작업을 검색 합니다. 반대로 `SchedulingProtocol` 가로 설정 된 경우 `EnhanceForwardProgress` 스케줄러는 각 태스크가 완료 되거나 생성 된 후 다음 일정 그룹으로 이동 합니다. 이러한 정책을 비교 하는 예제는 [방법: 일정 그룹을 사용 하 여 실행 순서에 영향](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)을 참조 하세요.

런타임은 [concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) 클래스를 사용 하 여 일정 그룹을 나타냅니다. 개체를 만들려면 `ScheduleGroup` [concurrency:: currentscheduler:: CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) 또는 [concurrency:: Scheduler:: CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup) 메서드를 호출 합니다. 런타임은 참조 횟수 메커니즘을 사용 하 여 개체 `ScheduleGroup` 와 마찬가지로 개체의 수명을 제어 `Scheduler` 합니다. 개체를 만들 때 `ScheduleGroup` 런타임은 참조 카운터를 하나로 설정 합니다. [Concurrency:: ScheduleGroup:: reference](reference/schedulegroup-class.md#reference) 메서드는 참조 카운터를 1 씩 증가 시킵니다. [Concurrency:: ScheduleGroup:: Release](reference/schedulegroup-class.md#release) 메서드는 참조 카운터를 1 씩 감소 시킵니다.

동시성 런타임에서 많은 형식을 사용 하면 개체와 일정 그룹을 함께 연결할 수 있습니다. 예를 들어 concurrency:: [agent](../../parallel/concrt/reference/agent-class.md) 클래스 및 메시지 블록 클래스 (예: [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md), [concurrency:: join](../../parallel/concrt/reference/join-class.md)및 concurrency::[timer](reference/timer-class.md))는 개체를 사용 하는 생성자의 오버 로드 된 버전을 제공 `ScheduleGroup` 합니다. 런타임은 `Scheduler` 이 개체와 연결 된 개체를 사용 하 여 `ScheduleGroup` 작업을 예약 합니다.

또한 [concurrency:: ScheduleGroup:: ScheduleTask](reference/schedulegroup-class.md#scheduletask) 메서드를 사용 하 여 간단한 작업을 예약할 수 있습니다. 경량 태스크에 대 한 자세한 내용은 [경량 작업](../../parallel/concrt/lightweight-tasks.md)을 참조 하세요.

## <a name="example"></a>예제

일정 그룹을 사용 하 여 작업 실행 순서를 제어 하는 예제는 [방법: 일정 그룹을 사용 하 여 실행 순서에 영향](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[작업 Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Scheduler 인스턴스](../../parallel/concrt/scheduler-instances.md)<br/>
[방법: 일정 그룹을 사용 하 여 실행 순서에 영향을 줍니다.](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)
