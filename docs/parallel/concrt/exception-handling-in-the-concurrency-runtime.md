---
description: '자세히 알아보기: 동시성 런타임에서 예외 처리'
title: 동시성 런타임에서 예외 처리
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks, exception handling [Concurrency Runtime]
- exception handling [Concurrency Runtime]
- structured task groups, exception handling [Concurrency Runtime]
- agents, exception handling [Concurrency Runtime]
- task groups, exception handling [Concurrency Runtime]
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
ms.openlocfilehash: 4613c2b11102c3468bfb3fa5976f8aeeeeb73be3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234308"
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>동시성 런타임에서 예외 처리

동시성 런타임는 c + + 예외 처리를 사용 하 여 여러 종류의 오류를 전달 합니다. 이러한 오류에는 잘못 된 런타임 사용, 리소스 획득 실패와 같은 런타임 오류 및 작업 및 작업 그룹에 제공 하는 작업 함수에서 발생 하는 오류가 포함 됩니다. 작업 또는 작업 그룹이 예외를 throw 하는 경우 런타임은 해당 예외를 보유 하 고 태스크 또는 작업 그룹이 완료 되기를 기다리는 컨텍스트로 마샬링합니다. 경량 작업 및 에이전트와 같은 구성 요소의 경우 런타임은 예외를 관리 하지 않습니다. 이러한 경우 사용자 고유의 예외 처리 메커니즘을 구현 해야 합니다. 이 항목에서는 런타임에서 작업, 작업 그룹, 경량 작업 및 비동기 에이전트에 의해 throw 되는 예외를 처리 하는 방법과 응용 프로그램에서 예외에 응답 하는 방법에 대해 설명 합니다.

## <a name="key-points"></a>요점

- 작업 또는 작업 그룹이 예외를 throw 하는 경우 런타임은 해당 예외를 보유 하 고 태스크 또는 작업 그룹이 완료 되기를 기다리는 컨텍스트로 마샬링합니다.

- 가능 하면 [concurrency:: task:: get](reference/task-class.md#get) 및 [concurrency:: task:: wait로 wait](reference/task-class.md#wait) 를 호출 **`try`** / **`catch`** 하 여 복구할 수 있는 오류를 처리 합니다. 작업에서 예외를 throw 하 고 태스크, 연속 중 하나 또는 주 응용 프로그램에서 예외를 catch 하지 않을 경우 런타임이 응용 프로그램을 종료 합니다.

- 작업 기반 연속은 항상 실행 됩니다. 선행 작업이 성공적으로 완료 되었는지, 예외를 throw 되었는지 또는 취소 되었는지 여부는 중요 하지 않습니다. 선행 작업이 throw 하거나 취소 하는 경우에는 값 기반 연속이 실행 되지 않습니다.

- 작업 기반 연속은 항상 실행 되므로 연속 체인의 끝에 작업 기반 연속을 추가할지 여부를 고려 합니다. 이렇게 하면 코드가 모든 예외를 관찰 하는 데 도움이 됩니다.

- [Concurrency:: task:: get](reference/task-class.md#get) 을 호출 하 고 해당 작업이 취소 되 면 런타임에서 [concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) 을 throw 합니다.

- 런타임에서는 경량 작업 및 에이전트에 대 한 예외를 관리 하지 않습니다.

## <a name="in-this-document"></a><a name="top"></a> 이 문서의

- [작업 및 연속 작업](#tasks)

- [작업 그룹 및 병렬 알고리즘](#task_groups)

- [런타임에 의해 Throw 되는 예외](#runtime)

- [여러 예외](#multiple)

- [취소](#cancellation)

- [간단한 작업](#lwts)

- [비동기 에이전트](#agents)

## <a name="tasks-and-continuations"></a><a name="tasks"></a> 작업 및 연속

이 섹션에서는 런타임이 [concurrency:: task](../../parallel/concrt/reference/task-class.md) 개체 및 해당 연속에서 throw 되는 예외를 처리 하는 방법을 설명 합니다. 태스크 및 연속 모델에 대 한 자세한 내용은 [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)를 참조 하세요.

개체에 전달 하는 작업 함수의 본문에서 예외를 throw 하는 경우 `task` 런타임은 해당 예외를 저장 하 고 [concurrency:: task:: get](reference/task-class.md#get) 또는 [concurrency:: task:: wait](reference/task-class.md#wait)를 호출 하는 컨텍스트로 마샬링합니다. 문서 [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md) 는 작업 기반 및 값 기반 연속을 설명 하지만 요약 하면 값 기반 연속은 형식의 매개 변수를 사용 `T` 하 고 작업 기반 연속은 형식의 매개 변수를 사용 합니다 `task<T>` . 에서 throw 하는 태스크에 하나 이상의 값 기반 연속이 있으면 해당 연속 작업이 실행 되도록 예약 되지 않습니다. 다음은 이 동작에 대한 예입니다.

[!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]

작업 기반 연속을 사용 하면 선행 작업에서 throw 되는 모든 예외를 처리할 수 있습니다. 작업 기반 연속은 항상 실행 됩니다. 작업을 성공적으로 완료 했거나, 예외를 throw 했거나, 취소 되었는지 여부는 중요 하지 않습니다. 작업에서 예외가 throw 되 면 작업 기반 연속 작업이 실행 되도록 예약 됩니다. 다음 예제에서는 항상을 throw 하는 작업을 보여 줍니다. 작업에는 두 개의 연속이 있습니다. 하나는 값을 기반으로 하며 다른 하나는 작업을 기반으로 합니다. 작업 기반 예외는 항상 실행 되므로 선행 작업에서 throw 되는 예외를 catch 할 수 있습니다. 이 예제에서 두 연속이 완료 될 때까지 대기 하는 경우 `task::get` 또는가 호출 될 때 작업 예외가 항상 throw 되기 때문에 예외가 다시 throw 됩니다 `task::wait` .

[!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]

작업 기반 연속을 사용 하 여 처리할 수 있는 예외를 catch 하는 것이 좋습니다. 작업 기반 연속은 항상 실행 되므로 연속 체인의 끝에 작업 기반 연속을 추가할지 여부를 고려 합니다. 이렇게 하면 코드가 모든 예외를 관찰 하는 데 도움이 됩니다. 다음 예에서는 기본 값 기반 연속 체인을 보여 줍니다. 체인의 세 번째 태스크가 throw 되므로 그 다음에 나오는 값 기반 연속은 실행 되지 않습니다. 그러나 최종 연속 작업은 작업 기반 이므로 항상 실행 됩니다. 이 마지막 연속 작업은 세 번째 작업에서 throw 되는 예외를 처리 합니다.

가능한 가장 구체적인 예외를 catch 하는 것이 좋습니다. 특정 예외를 catch 할 수 없는 경우이 최종 작업 기반 연속을 생략할 수 있습니다. 모든 예외는 처리 되지 않은 상태로 유지 되며 응용 프로그램을 종료할 수 있습니다.

[!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]

> [!TIP]
> [Concurrency:: task_completion_event:: set_exception](../../parallel/concrt/reference/task-completion-event-class.md) 메서드를 사용 하 여 예외를 작업 완료 이벤트와 연결할 수 있습니다. 문서 [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md) 는 [concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) 클래스에 대해 보다 자세히 설명 합니다.

[concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) 는와 관련 된 중요 한 런타임 예외 형식입니다 `task` . 을 호출 하 `task_canceled` `task::get` 고 해당 작업이 취소 되 면 런타임이 throw 됩니다. 반대로는 `task::wait` [task_status:: canceled](reference/concurrency-namespace-enums.md#task_group_status) 를 반환 하 고을 throw 하지 않습니다.) 작업 기반 연속에서 또는를 호출할 때이 예외를 catch 하 고 처리할 수 있습니다 `task::get` . 작업 취소에 대 한 자세한 내용은 [PPL에서의 취소](cancellation-in-the-ppl.md)를 참조 하세요.

> [!CAUTION]
> 코드에서 `task_canceled`를 throw하지 마세요. 대신 [concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) 를 호출 합니다.

작업에서 예외를 throw 하 고 태스크, 연속 중 하나 또는 주 응용 프로그램에서 예외를 catch 하지 않을 경우 런타임이 응용 프로그램을 종료 합니다. 응용 프로그램이 충돌 하는 경우 c + + 예외가 throw 될 때 중단 하도록 Visual Studio를 구성할 수 있습니다. 처리 되지 않은 예외의 위치를 진단 했으면 작업 기반 연속을 사용 하 여 처리 합니다.

이 문서에서 [런타임에 throw 된 예외](#runtime) 섹션에서는 런타임 예외를 보다 자세히 처리 하는 방법을 설명 합니다.

[[맨 위로](#top)이동]

## <a name="task-groups-and-parallel-algorithms"></a><a name="task_groups"></a> 작업 그룹 및 병렬 알고리즘

이 섹션에서는 런타임에서 작업 그룹에 의해 throw 되는 예외를 처리 하는 방법을 설명 합니다. 이 섹션은 [동시성::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)와 같은 병렬 알고리즘에도 적용 됩니다. 이러한 알고리즘은 작업 그룹에서 빌드됩니다.

> [!CAUTION]
> 예외가 종속 작업에 미치는 영향을 이해 해야 합니다. 작업 또는 병렬 알고리즘에서 예외 처리를 사용 하는 방법에 대 한 권장 방법은 병렬 패턴 라이브러리의 모범 사례 항목에서 [취소 및 예외 처리가 개체 소멸에 미치는 영향 이해](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) 섹션을 참조 하세요.

작업 그룹에 대 한 자세한 내용은 [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)를 참조 하세요. 병렬 알고리즘에 대 한 자세한 내용은 [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요.

[Concurrency:: task_group](reference/task-group-class.md) 또는 [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) 개체에 전달 하는 작업 함수의 본문에서 예외를 throw 하는 경우 런타임은 해당 예외를 저장 하 고 [concurrency:: task_group:: wait](reference/task-group-class.md#wait), [concurrency:: structured_task_group:: wait](reference/structured-task-group-class.md#wait), [concurrency:: task_group:: run_and_wait](reference/task-group-class.md#run_and_wait)또는 [concurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait)를 호출 하는 컨텍스트로 마샬링합니다. 또한 런타임에서는 작업 그룹에 있는 모든 활성 작업 (자식 작업 그룹의 작업 포함)을 중지 하 고 아직 시작 되지 않은 모든 작업을 삭제 합니다.

다음 예제에서는 예외를 throw 하는 작업 함수의 기본 구조를 보여 줍니다. 이 예제에서는 개체를 사용 하 여 `task_group` 두 개체의 값을 `point` 병렬로 인쇄 합니다. `print_point`작업 함수는 개체의 값을 `point` 콘솔에 출력 합니다. 입력 값이 인 경우 work 함수는 예외를 throw 합니다 `NULL` . 런타임은이 예외를 저장 하 고를 호출 하는 컨텍스트로 마샬링합니다 `task_group::wait` .

[!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
X = 15, Y = 30Caught exception: point is NULL.
```

작업 그룹에서 예외 처리를 사용 하는 전체 예제는 [방법: 예외 처리를 사용 하 여 병렬 루프 중단](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="exceptions-thrown-by-the-runtime"></a><a name="runtime"></a> 런타임에 의해 Throw 되는 예외

런타임에 대 한 호출에서 예외가 발생할 수 있습니다. [Concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) 및 [concurrency:: operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md)를 제외 하 고 대부분의 예외 형식은 프로그래밍 오류를 표시 합니다. 일반적으로 이러한 오류는 복구할 수 없으므로 응용 프로그램 코드에서 catch 하거나 처리 해서는 안 됩니다. 프로그래밍 오류를 진단 해야 하는 경우 응용 프로그램 코드에서 복구할 수 없는 오류를 catch 하거나 처리 하는 것이 좋습니다. 그러나 런타임에 정의 된 예외 형식을 이해 하면 프로그래밍 오류를 진단 하는 데 도움이 될 수 있습니다.

예외 처리 메커니즘은 작업 함수에서 throw 된 예외로 런타임에서 throw 되는 예외에 대해 동일 합니다. 예를 들어 [concurrency:: receive](reference/concurrency-namespace-functions.md#receive) 함수는 `operation_timed_out` 지정 된 기간 내에 메시지를 수신 하지 않을 때 throw 됩니다. 가 `receive` 작업 그룹에 전달 하는 작업 함수에서 예외를 throw 하는 경우 런타임은 해당 예외를 저장 하 고,, 또는를 호출 하는 컨텍스트로 마샬링합니다 `task_group::wait` `structured_task_group::wait` `task_group::run_and_wait` `structured_task_group::run_and_wait` .

다음 예에서는 [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) 알고리즘을 사용 하 여 두 작업을 병렬로 실행 합니다. 첫 번째 작업은 5 초 동안 대기한 후 메시지 버퍼에 메시지를 보냅니다. 두 번째 태스크는 함수를 사용 하 여 `receive` 세 초 동안 같은 메시지 버퍼에서 메시지를 수신 합니다. `receive`이 함수는 해당 `operation_timed_out` 기간에 메시지를 수신 하지 않는 경우 throw 됩니다.

[!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
The operation timed out.
```

응용 프로그램이 비정상적으로 종료 되는 것을 방지 하려면 런타임에를 호출할 때 코드에서 예외를 처리 하는지 확인 합니다. 또한 동시성 런타임를 사용 하는 외부 코드를 호출 하는 경우 (예: 타사 라이브러리) 예외를 처리 합니다.

[[맨 위로](#top)이동]

## <a name="multiple-exceptions"></a><a name="multiple"></a> 여러 예외

작업 또는 병렬 알고리즘이 여러 예외를 수신 하는 경우 런타임은 이러한 예외 중 하나만 호출 컨텍스트로 마샬링합니다. 런타임에서는 마샬링할 예외를 보장 하지 않습니다.

다음 예에서는 알고리즘을 사용 하 여 `parallel_for` 콘솔에 숫자를 인쇄 합니다. 입력 값이 일부 최소값 보다 작거나 최대값 보다 큰 경우 예외를 throw 합니다. 이 예제에서는 여러 작업 함수에서 예외를 throw 할 수 있습니다.

[!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]

다음은이 예제에 대 한 샘플 출력을 보여 줍니다.

```Output
8293104567Caught exception: -5: the value is less than the minimum.
```

[[맨 위로](#top)이동]

## <a name="cancellation"></a><a name="cancellation"></a> 취소

모든 예외가 오류를 나타내는 것은 아닙니다. 예를 들어 검색 알고리즘은 예외 처리를 사용 하 여 결과를 찾을 때 연결 된 작업을 중지할 수 있습니다. 코드에서 취소 메커니즘을 사용 하는 방법에 대 한 자세한 내용은 [PPL에서의 취소](../../parallel/concrt/cancellation-in-the-ppl.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="lightweight-tasks"></a><a name="lwts"></a> 간단한 작업

간단한 작업은 [concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) 개체에서 직접 예약 하는 작업입니다. 경량 작업은 일반 작업 보다 오버 헤드가 적습니다. 그러나 런타임에서는 간단한 작업에서 throw 되는 예외를 catch 하지 않습니다. 대신 처리 되지 않은 예외 처리기에서 예외를 catch 하며,이는 기본적으로 프로세스를 종료 합니다. 따라서 응용 프로그램에서 적절 한 오류 처리 메커니즘을 사용 합니다. 간단한 작업에 대 한 자세한 내용은 [작업 스케줄러](../../parallel/concrt/task-scheduler-concurrency-runtime.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="asynchronous-agents"></a><a name="agents"></a> 비동기 에이전트

간단한 작업 처럼 런타임은 비동기 에이전트에서 throw 되는 예외를 관리 하지 않습니다.

다음 예제에서는 [concurrency:: agent](../../parallel/concrt/reference/agent-class.md)에서 파생 되는 클래스의 예외를 처리 하는 한 가지 방법을 보여 줍니다. 이 예제에서는 클래스를 정의 `points_agent` 합니다. `points_agent::run`메서드는 `point` 메시지 버퍼에서 개체를 읽고 콘솔에 출력 합니다. `run`메서드는 포인터를 수신 하는 경우 예외를 throw 합니다 `NULL` .

`run`메서드는 블록의 모든 작업을 둘러쌉니다 **`try`** - **`catch`** . **`catch`** 블록은 예외를 메시지 버퍼에 저장 합니다. 응용 프로그램은 에이전트가 완료 된 후이 버퍼에서 읽어서 오류가 발생 했는지 여부를 확인 합니다.

[!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
X: 10 Y: 20
X: 20 Y: 30
error occurred in agent: point must not be NULL
the status of the agent is: done
```

블록은 루프 외부에 존재 하기 때문에 **`try`** - **`catch`** **`while`** 첫 번째 오류가 발생할 때 에이전트가 처리를 종료 합니다. **`try`** - **`catch`** 블록이 루프 내에 있으면 **`while`** 오류가 발생 한 후에도 에이전트가 계속 됩니다.

이 예에서는 다른 구성 요소에서 에이전트가 실행 될 때 오류를 모니터링할 수 있도록 예외를 메시지 버퍼에 저장 합니다. 이 예제에서는 [concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) 개체를 사용 하 여 오류를 저장 합니다. 에이전트가 여러 예외를 처리 하는 경우 `single_assignment` 클래스는 전달 된 첫 번째 메시지만 저장 합니다. 마지막 예외도 저장 하려면 [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 클래스를 사용 합니다. 모든 예외를 저장 하려면 [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) 클래스를 사용 합니다. 이러한 메시지 블록에 대 한 자세한 내용은 [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

비동기 에이전트에 대 한 자세한 내용은 [비동기 에이전트](../../parallel/concrt/asynchronous-agents.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="summary"></a><a name="summary"></a> 요약

[[맨 위로](#top)이동]

## <a name="see-also"></a>참고 항목

[동시성 런타임](../../parallel/concrt/concurrency-runtime.md)<br/>
[작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL에서의 취소](cancellation-in-the-ppl.md)<br/>
[작업 Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[비동기 에이전트](../../parallel/concrt/asynchronous-agents.md)
