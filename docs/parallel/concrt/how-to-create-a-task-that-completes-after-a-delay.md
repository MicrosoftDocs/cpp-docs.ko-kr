---
title: '방법: 지연 후 완료되는 작업 만들기'
ms.date: 11/04/2016
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 80bfdeb7586f9c32592bc408a9de0c9188b77a29
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413790"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>방법: 지연 후 완료되는 작업 만들기

이 예제에서는 [concurrency:: task](../../parallel/concrt/reference/task-class.md), [concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [concurrency](../../parallel/concrt/reference/cancellation-token-class.md):: cancellation_token, [concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), [concurrency:: timer](../../parallel/concrt/reference/timer-class.md)및 [concurrency:: call](../../parallel/concrt/reference/call-class.md) 클래스를 사용 하 여 지연 후 완료 되는 작업을 만드는 방법을 보여 줍니다. 이 메서드는 때때로 데이터를 폴링하는 루프를 빌드하고, 제한 시간을 적용하고, 미리 지정한 시간 동안 사용자의 입력 처리를 지연하는 데 사용할 수 있습니다.

## <a name="example-complete_after-and-cancel_after_timeout-functions"></a>예: complete_after 및 cancel_after_timeout 함수

다음 예제에서는 `complete_after` 및 `cancel_after_timeout` 함수를 보여 줍니다. `complete_after` 함수는 지정된 지연 후에 완료되는 `task` 개체를 만듭니다. 이 함수는 지정된 지연 후에 `timer` 개체와 `call` 개체를 사용하여 `task_completion_event` 개체를 설정합니다. `task_completion_event` 클래스를 사용하여 스레드 후에 또는 값을 사용할 수 있는 다른 작업 신호 후에 완료되는 작업을 정의할 수 있습니다. 이벤트가 설정되면 수신기 작업이 완료되고 작업의 연속 실행이 예약됩니다.

> [!TIP]
> `timer` `call` 비동기 에이전트 라이브러리의 일부인 및 클래스에 대 한 자세한 내용은 [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

`cancel_after_timeout` 함수는 `complete_after` 함수를 기반으로 하여 주어진 제한 시간 전에 작업이 완료되지 않을 경우 작업을 취소합니다. `cancel_after_timeout` 함수는 두 개의 작업을 만듭니다. 첫 번째 작업은 제공된 작업이 완료된 후 성공했음을 알리고 완료되며, 두 번째 작업은 지정된 제한 시간이 지나면 작업이 실패했음을 알리고 완료됩니다. `cancel_after_timeout` 함수는 성공하거나 실패한 작업이 완료되면 실행되는 연속 작업을 생성합니다. 실패한 작업이 먼저 완료되면 연속에서 토큰 소스를 취소하여 전체 작업을 취소합니다.

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example-compute-count-of-prime-numbers"></a>예: 소수 계산 계산

다음 예제에서는 [0, 100000] 범위에서 소수의 수를 여러 번 계산합니다. 주어진 시간 제한 안에 완료되지 않으면 작업이 실패합니다. `count_primes` 함수는 `cancel_after_timeout` 함수를 사용하는 방법을 보여 줍니다. 지정된 범위에서 소수의 수를 세고 주어진 시간 안에 작업이 완료되지 않으면 실패합니다. `wmain` 함수는 `count_primes` 함수를 여러 번 호출합니다. 호출할 때마다 제한 시간은 1/2로 줄어듭니다. 현재 제한 시간 안에 작업이 완료되지 않으면 프로그램이 종료됩니다.

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

이 방법을 사용하여 지연 후 작업을 취소할 경우 시작되지 않은 작업은 전체 작업이 취소된 후에 시작됩니다. 그러나 장기 실행 작업은 적시에 취소에 응답하는 것이 중요합니다. 작업 취소에 대 한 자세한 내용은 [PPL에서의 취소](cancellation-in-the-ppl.md)를 참조 하세요.

## <a name="complete-code-example"></a>전체 코드 예제

이 예제의 전체 코드는 다음과 같습니다.

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>코드 컴파일

코드를 컴파일하려면 코드를 복사한 다음 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 후 `task-delay.cpp` Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

**cl.exe/EHsc task-delay**

## <a name="see-also"></a>참고 항목

[작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[작업 클래스 (동시성 런타임)](../../parallel/concrt/reference/task-class.md)<br/>
[cancellation_token_source 클래스](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[cancellation_token 클래스](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[task_completion_event 클래스](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[timer 클래스](../../parallel/concrt/reference/timer-class.md)<br/>
[call 클래스](../../parallel/concrt/reference/call-class.md)<br/>
[비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[PPL에서의 취소](cancellation-in-the-ppl.md)
