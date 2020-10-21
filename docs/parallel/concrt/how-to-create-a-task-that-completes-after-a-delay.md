---
title: '방법: 지연 후 완료되는 작업 만들기'
description: PPL ConcRT 라이브러리를 사용 하 여 지연 후 완료 되는 작업을 만듭니다.
ms.date: 10/19/2020
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 694b6190a7ec60043a5674e920dc54e6e7bf0eb6
ms.sourcegitcommit: 19016630f9d35f365e9ba249e0f3617515d7ca33
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92274560"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>방법: 지연 후 완료되는 작업 만들기

이 예제에서는,,,, 및 클래스를 사용 하 여 [`concurrency::task`](../../parallel/concrt/reference/task-class.md) [`concurrency::cancellation_token_source`](../../parallel/concrt/reference/cancellation-token-source-class.md) [`concurrency::cancellation_token`](../../parallel/concrt/reference/cancellation-token-class.md) [`concurrency::task_completion_event`](../../parallel/concrt/reference/task-completion-event-class.md) [`concurrency::timer`](../../parallel/concrt/reference/timer-class.md) [`concurrency::call`](../../parallel/concrt/reference/call-class.md) 지연 후 완료 되는 작업을 만드는 방법을 보여 줍니다. 이 메서드를 사용 하 여 때때로 데이터를 폴링하는 루프를 작성할 수 있습니다. 제한 시간을 도입 하 고 미리 정해진 시간에 대 한 사용자 입력의 처리를 지연 시킬 수도 있습니다.

## <a name="example-complete_after-and-cancel_after_timeout-functions"></a>예: complete_after 및 cancel_after_timeout 함수

다음 예제에서는 `complete_after` 및 `cancel_after_timeout` 함수를 보여 줍니다. `complete_after` 함수는 지정된 지연 후에 완료되는 `task` 개체를 만듭니다. 이 함수는 지정된 지연 후에 `timer` 개체와 `call` 개체를 사용하여 `task_completion_event` 개체를 설정합니다. `task_completion_event` 클래스를 사용하여 스레드 후에 또는 값을 사용할 수 있는 다른 작업 신호 후에 완료되는 작업을 정의할 수 있습니다. 이벤트가 설정되면 수신기 작업이 완료되고 작업의 연속 실행이 예약됩니다.

> [!TIP]
> `timer` `call` 비동기 에이전트 라이브러리의 일부인 및 클래스에 대 한 자세한 내용은 [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

함수는 해당 `cancel_after_timeout` `complete_after` 태스크가 지정 된 시간 제한 이전에 완료 되지 않은 경우 작업을 취소 하는 함수를 기반으로 합니다. `cancel_after_timeout` 함수는 두 개의 작업을 만듭니다. 첫 번째 작업은 성공을 나타내며 제공 된 작업이 완료 된 후 완료 됩니다. 두 번째 작업은 실패를 나타내며 지정 된 시간 제한 후에 완료 됩니다. `cancel_after_timeout` 함수는 성공하거나 실패한 작업이 완료되면 실행되는 연속 작업을 생성합니다. 실패한 작업이 먼저 완료되면 연속에서 토큰 소스를 취소하여 전체 작업을 취소합니다.

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example-compute-count-of-prime-numbers"></a>예: 소수 계산 계산

다음 예제에서는 [0, 100000] 범위에서 소수의 수를 여러 번 계산합니다. 지정 된 시간 제한 내에 완료 되지 않으면 작업이 실패 합니다. `count_primes` 함수는 `cancel_after_timeout` 함수를 사용하는 방법을 보여 줍니다. 지정 된 범위에서 prime 수를 계산 하 고, 제공 된 시간 내에 작업이 완료 되지 않으면 실패 합니다. `wmain` 함수는 `count_primes` 함수를 여러 번 호출합니다. 호출할 때마다 제한 시간은 1/2로 줄어듭니다. 프로그램이 현재 시간 제한에서 작업이 완료 되지 않은 후 프로그램이 완료 됩니다.

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

이 방법을 사용 하 여 지연 후 작업을 취소 하는 경우 전체 작업이 취소 된 후에 시작 되지 않은 작업이 시작 되지 않습니다. 그러나 장기 실행 작업은 취소에 신속 하 게 응답 하는 것이 중요 합니다. 작업 취소에 대 한 자세한 내용은 [PPL에서의 취소](cancellation-in-the-ppl.md)를 참조 하세요.

## <a name="complete-code-example"></a>전체 코드 예제

이 예제의 전체 코드는 다음과 같습니다.

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>코드 컴파일

코드를 컴파일하려면 코드를 복사한 다음 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 후 `task-delay.cpp` Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

**cl.exe/EHsc task-delay**

## <a name="see-also"></a>참조

[작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[작업 클래스 (동시성 런타임)](../../parallel/concrt/reference/task-class.md)<br/>
[cancellation_token_source 클래스](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[cancellation_token 클래스](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[task_completion_event 클래스](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[timer 클래스](../../parallel/concrt/reference/timer-class.md)<br/>
[call 클래스](../../parallel/concrt/reference/call-class.md)<br/>
[비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[PPL에서의 취소](cancellation-in-the-ppl.md)
