---
description: '자세히 알아보기: 방법: 일정 그룹을 사용 하 여 실행 순서에 영향을 줍니다.'
title: '방법: 실행 순서에 영향을 주는 일정 그룹 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
ms.openlocfilehash: 28bf3e1c302e2aafe05f6670571c1f07c2f0136d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205682"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>방법: 실행 순서에 영향을 주는 일정 그룹 사용

동시성 런타임에서 작업이 예약 되는 순서는 비결 정적입니다. 그러나 예약 정책을 사용 하 여 태스크가 실행 되는 순서에 영향을 줄 수 있습니다. 이 항목에서는 [concurrency:: SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey) scheduler 정책과 함께 schedule 그룹을 사용 하 여 작업이 실행 되는 순서에 영향을 주는 방법을 보여 줍니다.

이 예에서는 작업 집합을 두 번 실행 합니다. 각 작업은 서로 다른 일정 정책을 사용 합니다. 두 정책 모두 처리 리소스의 최대 수를 2 개로 제한 합니다. 첫 번째 실행에서는 `EnhanceScheduleGroupLocality` 기본 인 정책을 사용 하며, 두 번째 실행은 정책을 사용 합니다 `EnhanceForwardProgress` . `EnhanceScheduleGroupLocality`이 정책에서 스케줄러는 각 태스크가 완료 되거나 생성 될 때까지 한 일정 그룹의 모든 작업을 실행 합니다. `EnhanceForwardProgress`이 정책에서는 한 작업이 완료 되거나 생성 된 후에 라운드 로빈 방식으로 스케줄러에서 다음 일정 그룹으로 이동 합니다.

각 일정 그룹이 관련 태스크를 포함 하는 경우 `EnhanceScheduleGroupLocality` 정책에서는 일반적으로 작업 간에 캐시 집약성이 유지 되기 때문에 성능이 향상 됩니다. `EnhanceForwardProgress`이 정책은 작업을 진행 하는 데 사용할 수 있으며 일정 그룹에서 일정을 공평 하 게 해야 하는 경우에 유용 합니다.

## <a name="example"></a>예제

이 예제에서는 `work_yield_agent` [concurrency:: agent](../../parallel/concrt/reference/agent-class.md)에서 파생 되는 클래스를 정의 합니다. `work_yield_agent`클래스는 작업 단위를 수행 하 고 현재 컨텍스트를 생성 한 다음 다른 작업 단위를 수행 합니다. 에이전트는 [concurrency:: wait](reference/concurrency-namespace-functions.md#wait) 함수를 사용 하 여 다른 컨텍스트가 실행 될 수 있도록 현재 컨텍스트를 협조적으로 양보 합니다.

이 예에서는 네 개의 `work_yield_agent` 개체를 만듭니다. 에이전트를 실행 하는 순서에 영향을 주는 스케줄러 정책을 설정 하는 방법을 설명 하기 위해이 예에서는 첫 번째 두 에이전트를 하나의 일정 그룹과 연결 하 고 다른 두 에이전트를 다른 일정 그룹에 연결 합니다. 이 예제에서는 [concurrency:: CurrentScheduler:: CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) 메서드를 사용 하 여 [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) 개체를 만듭니다. 이 예에서는 각각 다른 예약 정책을 사용 하 여 4 개의 에이전트를 두 번 실행 합니다.

[!code-cpp[concrt-scheduling-protocol#1](../../parallel/concrt/codesnippet/cpp/how-to-use-schedule-groups-to-influence-order-of-execution_1.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
Using EnhanceScheduleGroupLocality...
group 0,
    task 0: first loop...
group 0,
    task 1: first loop...
group 0,
    task 0: waiting...
group 1,
    task 0: first loop...
group 0,
    task 1: waiting...
group 1,
    task 1: first loop...
group 1,
    task 0: waiting...
group 0,
    task 0: second loop...
group 1,
    task 1: waiting...
group 0,
    task 1: second loop...
group 0,
    task 0: finished...
group 1,
    task 0: second loop...
group 0,
    task 1: finished...
group 1,
    task 1: second loop...
group 1,
    task 0: finished...
group 1,
    task 1: finished...

Using EnhanceForwardProgress...
group 0,
    task 0: first loop...
group 1,
    task 0: first loop...
group 0,
    task 0: waiting...
group 0,
    task 1: first loop...
group 1,
    task 0: waiting...
group 1,
    task 1: first loop...
group 0,
    task 1: waiting...
group 0,
    task 0: second loop...
group 1,
    task 1: waiting...
group 1,
    task 0: second loop...
group 0,
    task 0: finished...
group 0,
    task 1: second loop...
group 1,
    task 0: finished...
group 1,
    task 1: second loop...
group 0,
    task 1: finished...
group 1,
    task 1: finished...
```

두 정책 모두 동일한 이벤트 시퀀스를 생성 합니다. 그러나를 사용 하는 정책은 `EnhanceScheduleGroupLocality` 두 번째 그룹의 일부인 에이전트를 시작 하기 전에 첫 번째 일정 그룹의 일부인 두 에이전트를 모두 시작 합니다. 에서 사용 하는 정책은 `EnhanceForwardProgress` 첫 번째 그룹에서 하나의 에이전트를 시작한 다음 두 번째 그룹에서 첫 번째 에이전트를 시작 합니다.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `scheduling-protocol.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc scheduling-protocol**

## <a name="see-also"></a>참고 항목

[일정 그룹](../../parallel/concrt/schedule-groups.md)<br/>
[비동기 에이전트](../../parallel/concrt/asynchronous-agents.md)
