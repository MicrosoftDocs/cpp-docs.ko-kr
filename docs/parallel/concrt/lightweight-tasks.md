---
description: '자세한 정보: 간단한 작업'
title: 간단한 작업
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
ms.openlocfilehash: 328d556eacb2e33bdf3077b722defa81669a525c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205566"
---
# <a name="lightweight-tasks"></a>간단한 작업

이 문서에서는 동시성 런타임의 간단한 작업 역할에 대해 설명 합니다. *간단한 작업* 은 또는 개체에서 직접 예약 하는 작업입니다 `concurrency::Scheduler` `concurrency::ScheduleGroup` . 간단한 작업은 Windows API [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) 함수에 제공 하는 함수와 유사 합니다. 따라서 동시성 런타임의 예약 기능을 사용 하도록 기존 코드를 조정 하는 경우 간단한 작업이 유용 합니다. 동시성 런타임 자체는 간단한 작업을 사용 하 여 비동기 에이전트를 예약 하 고 비동기 메시지 블록 간에 메시지를 보냅니다.

> [!TIP]
> 동시성 런타임은 기본 스케줄러를 제공하므로 애플리케이션에서 스케줄러를 만들 필요가 없습니다. 작업 스케줄러는 응용 프로그램의 성능을 미세 조정 하는 데 도움이 되므로 동시성 런타임를 처음 접하는 경우 [PPL (병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md) 또는 [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md) 를 사용 하는 것이 좋습니다.

간단한 작업은 비동기 에이전트 및 작업 그룹 보다 오버 헤드가 적습니다. 예를 들어, 런타임에서는 간단한 작업이 완료 될 때 사용자에 게 알리지 않습니다. 또한 런타임은 간단한 작업에서 throw 된 예외를 catch 하거나 처리 하지 않습니다. 예외 처리 및 간단한 작업에 대 한 자세한 내용은 [예외 처리](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)를 참조 하세요.

작업 그룹 및 병렬 알고리즘과 같은 보다 강력한 기능을 사용 하면 복잡 한 작업을 보다 쉽게 사용할 수 있으므로 작업 그룹 및 병렬 알고리즘과 같은 보다 강력한 기능을 사용 하는 것이 좋습니다. 작업 그룹에 대 한 자세한 내용은 [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)를 참조 하세요. 병렬 알고리즘에 대 한 자세한 내용은 [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요.

간단한 작업을 만들려면 [concurrency:: ScheduleGroup:: ScheduleTask](reference/schedulegroup-class.md#scheduletask), [Concurrency:: Currentscheduler:: ScheduleTask](reference/currentscheduler-class.md#scheduletask)또는 [concurrency:: Scheduler:: ScheduleTask](reference/scheduler-class.md#scheduletask) 메서드를 호출 합니다. 간단한 작업이 완료 될 때까지 기다리려면 부모 스케줄러가 종료 될 때까지 기다리거나 [concurrency:: event](../../parallel/concrt/reference/event-class.md) 개체와 같은 동기화 메커니즘을 사용 합니다.

## <a name="example"></a>예제

간단한 작업을 사용 하기 위해 기존 코드를 조정 하는 방법을 보여 주는 예제는 [연습: 간단한 작업을 사용 하기 위해 기존 코드](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)조정을 참조 하세요.

## <a name="see-also"></a>참고 항목

[작업 Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[연습: 간단한 작업을 사용 하기 위해 기존 코드 조정](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)
