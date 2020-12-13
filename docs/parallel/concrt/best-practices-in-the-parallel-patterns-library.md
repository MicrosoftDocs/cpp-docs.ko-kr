---
description: '자세한 정보: 병렬 패턴 라이브러리의 모범 사례'
title: 병렬 패턴 라이브러리의 유용한 정보
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library, practices to avoid
- practices to avoid, Parallel Patterns Library
- best practices, Parallel Patterns Library
- Parallel Patterns Library, best practices
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
ms.openlocfilehash: 72b0ff36532decbc55ae792ee407b3b711bd54a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334691"
---
# <a name="best-practices-in-the-parallel-patterns-library"></a>병렬 패턴 라이브러리의 유용한 정보

이 문서에서는 PPL(병렬 패턴 라이브러리)을 효율적으로 사용하는 방법을 설명합니다. PPL은 세부적인 병렬 처리를 수행하기 위한 범용 컨테이너, 개체 및 알고리즘을 제공합니다.

PPL에 대 한 자세한 내용은 [ppl (병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md)을 참조 하세요.

## <a name="sections"></a><a name="top"></a> 섹션이

이 문서는 다음 섹션으로 구성됩니다.

- [작은 루프 본문을 평행화하지 않음](#small-loops)

- [가장 높은 수준의 빠른 병렬 처리](#highest)

- [parallel_invoke를 사용하여 Divide-and-Conquer 문제 해결](#divide-and-conquer)

- [취소 또는 예외 처리를 사용하여 병렬 루프 중단](#breaking-loops)

- [취소 및 예외 처리가 개체 소멸에 미치는 영향 이해](#object-destruction)

- [병렬 루프에서 반복적으로 차단되지 않음](#repeated-blocking)

- [병렬 작업을 취소하는 경우 차단 작업을 수행하지 않음](#blocking)

- [병렬 루프에서 공유 데이터에 쓰지 않음](#shared-writes)

- [가능한 경우 거짓 공유 방지](#false-sharing)

- [작업의 전체 수명 동안 변수가 유효한지 확인](#lifetime)

## <a name="do-not-parallelize-small-loop-bodies"></a><a name="small-loops"></a> 작은 루프 본문을 병렬화 하지 않음

비교적 작은 루프 본문을 평행화하면 관련된 예약 오버헤드가 병렬 처리의 이점보다 더 커질 수 있습니다. 두 배열에 각 요소 쌍을 추가하는 다음 예제를 고려해 보세요.

[!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_1.cpp)]

각 병렬 루프 반복에 대한 작업이 너무 작아서 병렬 처리 오버헤드의 이점이 없습니다. 루프 본문에서 더 많은 작업을 수행하거나 루프를 직렬로 수행하여 이 루프의 성능을 향상시킬 수 있습니다.

[[맨 위로](#top)이동]

## <a name="express-parallelism-at-the-highest-possible-level"></a><a name="highest"></a> 가능한 가장 높은 수준에서 병렬 처리

낮은 수준에서만 코드를 병렬 처리하는 경우 프로세서 수가 증가할 때 크기가 조정되지 않는 분기-조인 구문이 도입될 수 있습니다. *포크 조인* 구문은 한 태스크에서 작업을 더 작은 병렬 하위 작업으로 나누고 해당 하위 작업이 완료 될 때까지 대기 하는 구문입니다. 각 하위 작업은 재귀적으로 추가 하위 작업으로 나뉠 수 있습니다.

분기-조인 모델은 다양한 문제를 해결하는 데 유용할 수 있지만 동기화 오버헤드로 인해 확장성이 감소하는 경우도 있습니다. 예를 들어 이미지 데이터를 처리하는 다음 직렬 코드를 고려해 보세요.

[!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_2.cpp)]

각 루프 반복은 서로 독립적이기 때문에 다음 예제와 같이 대부분의 작업을 병렬 처리할 수 있습니다. 이 예제에서는 [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 알고리즘을 사용 하 여 외부 루프를 병렬화 합니다.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_3.cpp)]

다음 예제에서는 루프에서 `ProcessImage` 함수를 호출하여 분기-조인 구문을 보여 줍니다. 각 하위 작업이 완료될 때까지 각 `ProcessImage` 호출이 반환되지 않습니다.

[!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_4.cpp)]

병렬 루프의 각 반복이 거의 작업을 수행하지 않거나 병렬 루프에서 수행하는 작업의 균형이 맞지 않는 경우(즉, 일부 루프 반복이 다른 반복보다 오래 걸리는 경우) 자주 작업을 분기 및 조인하는 데 필요한 예약 오버헤드가 병렬 실행의 이점보다 클 수 있습니다. 프로세서 수가 증가하면 이 오버헤드도 증가합니다.

이 예제에서 예약 오버헤드를 줄이기 위해 내부 루프를 병렬 처리하기 전에 외부 루프를 병렬 처리하거나 파이프라인과 같은 다른 병렬 구문을 사용할 수 있습니다. 다음 예에서는 `ProcessImages` [동시성::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 알고리즘을 사용 하 여 외부 루프를 병렬화 하는 함수를 수정 합니다.

[!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_5.cpp)]

파이프라인을 사용 하 여 동시에 이미지 처리를 수행 하는 비슷한 예제는 [연습: Image-Processing 네트워크 만들기](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="use-parallel_invoke-to-solve-divide-and-conquer-problems"></a><a name="divide-and-conquer"></a> Parallel_invoke를 사용 하 여 나누기 및 정복 문제 해결

*나누기 및* 해결 문제는 재귀를 사용 하 여 작업을 하위 작업으로 나누는 포크 조인 구문의 형태입니다. Concurrency: [: task_group](reference/task-group-class.md) 및 [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) 클래스 외에도 [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) 알고리즘을 사용 하 여 분할 및 문제를 해결할 수 있습니다. `parallel_invoke` 알고리즘은 작업 그룹 개체보다 구문이 더 간결하며 고정된 개수의 병렬 작업이 있는 경우에 유용합니다.

다음 예제에서는 `parallel_invoke` 알고리즘을 사용하여 바이토닉 정렬 알고리즘을 구현하는 방법을 보여 줍니다.

[!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_6.cpp)]

오버헤드를 줄이기 위해 `parallel_invoke` 알고리즘은 호출 컨텍스트에서 일련의 작업 중 마지막 작업을 수행합니다.

이 예제의 전체 버전을 보려면 [방법: parallel_invoke를 사용 하 여 병렬 정렬 루틴 작성](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)을 참조 하세요. 알고리즘에 대 한 자세한 내용은 `parallel_invoke` [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="use-cancellation-or-exception-handling-to-break-from-a-parallel-loop"></a><a name="breaking-loops"></a> 취소 또는 예외 처리를 사용 하 여 병렬 루프 중단

PPL은 작업 그룹 또는 병렬 알고리즘에서 수행하는 병렬 작업을 취소하는 두 가지 방법을 제공합니다. 한 가지 방법은 [concurrency:: task_group](reference/task-group-class.md) 및 [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) 클래스에서 제공 하는 취소 메커니즘을 사용 하는 것입니다. 다른 방법은 작업 함수의 본문에서 예외를 발생시키는 것입니다. 병렬 작업 트리를 취소하는 경우 취소 메커니즘이 예외 처리보다 더 효율적입니다. *병렬 작업 트리* 는 일부 작업 그룹이 다른 작업 그룹을 포함 하는 관련 작업 그룹의 그룹입니다. 취소 메커니즘은 하향식으로 작업 그룹 및 자식 작업 그룹을 취소합니다. 반대로 예외 처리는 상향식으로 작동하고 예외가 위쪽으로 전파될 때 각 자식 작업 그룹을 개별적으로 취소해야 합니다.

작업 그룹 개체로 직접 작업 하는 경우 [concurrency:: task_group:: cancel](reference/task-group-class.md#cancel) 또는 [concurrency:: structured_task_group:: cancel](reference/structured-task-group-class.md#cancel) 메서드를 사용 하 여 해당 작업 그룹에 속한 작업을 취소 합니다. 병렬 알고리즘(예: `parallel_for`)을 취소하려면 부모 작업 그룹을 만들고 해당 작업 그룹을 취소합니다. 예를 들어 병렬로 배열에서 값을 검색하는 `parallel_find_any` 함수를 고려해 보세요.

[!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_7.cpp)]

병렬 알고리즘에서 작업 그룹을 사용하므로 병렬 반복 중 하나가 부모 작업 그룹을 취소하는 경우 전체 작업이 취소됩니다. 이 예제의 전체 버전을 보려면 [방법: 취소를 사용 하 여 병렬 루프 중단](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)을 참조 하세요.

병렬 작업을 취소하는 경우 예외 처리가 취소 메커니즘보다 덜 효율적인 방법이지만 예외 처리가 적합한 경우도 있습니다. 예를 들어 `for_all` 메서드는 `tree` 구조의 각 노드에서 작업 함수를 재귀적으로 수행합니다. 이 예제에서 `_children` 데이터 멤버는 개체를 포함 하는 [std:: list](../../standard-library/list-class.md) 입니다 `tree` .

[!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_8.cpp)]

`tree::for_all` 메서드의 호출자는 트리의 각 요소에 대해 작업 함수를 호출할 필요가 없는 경우 예외를 발생시킬 수 있습니다. 다음 예제에서는 제공된 `tree` 개체에서 값을 검색하는 `search_for_value` 함수를 보여 줍니다. `search_for_value` 함수는 트리의 현재 요소가 제공된 값과 일치하는 경우 예외를 발생시키는 작업 함수를 사용합니다. `search_for_value` 함수는 `try-catch` 블록을 사용하여 예외를 캡처하고 결과를 콘솔에 출력합니다.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_9.cpp)]

이 예제의 전체 버전을 보려면 [방법: 예외 처리를 사용 하 여 병렬 루프 중단을](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)참조 하세요.

PPL에서 제공 하는 취소 및 예외 처리 메커니즘에 대 한 일반적인 정보는 [ppl의 취소](cancellation-in-the-ppl.md) 및 [예외 처리](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="understand-how-cancellation-and-exception-handling-affect-object-destruction"></a><a name="object-destruction"></a> 취소 및 예외 처리가 개체 소멸에 미치는 영향 이해

병렬 작업 트리에서 취소된 작업은 자식 작업이 실행되지 않도록 합니다. 따라서 자식 작업 중 하나가 리소스 해제와 같이 애플리케이션에 중요한 작업을 수행하는 경우 문제가 발생할 수 있습니다. 또한 작업 취소로 인해 예외가 개체 소멸자를 통해 전파되고 애플리케이션에서 정의되지 않은 동작이 발생할 수 있습니다.

다음 예제에서 `Resource` 클래스는 리소스를 설명하고 `Container` 클래스는 리소스를 보유하는 컨테이너를 설명합니다. 해당 소멸자에서 `Container` 클래스는 `Resource` 멤버 중 두 개에서 `cleanup` 메서드를 병렬로 호출한 다음 세 번째 `Resource` 멤버에서 `cleanup` 메서드를 호출합니다.

[!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_10.h)]

이 패턴 자체에는 문제가 없지만 두 작업을 병렬로 실행하는 다음 코드를 고려해 보세요. 첫 번째 작업은 `Container` 개체를 만들고 두 번째 작업은 전체 작업을 취소합니다. 예시를 위해이 예제에서는 두 개의 [concurrency:: event](../../parallel/concrt/reference/event-class.md) 개체를 사용 하 여 개체가 생성 된 후 취소가 발생 하 `Container` 고 `Container` 취소 작업이 발생 한 후 개체가 소멸 되는지 확인 합니다.

[!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_11.cpp)]

이 예제는 다음과 같은 출력을 생성합니다.

```Output
Container 1: Freeing resources...Exiting program...
```

이 코드 예제에는 예상과 다르게 동작하게 만들 수 있는 다음과 같은 문제가 포함되어 있습니다.

- 부모 작업을 취소 하면 자식 작업 인 [동시성::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)에 대 한 호출도 취소 됩니다. 따라서 이러한 두 리소스가 해제되지 않습니다.

- 부모 작업을 취소하면 자식 작업에서 내부 예외가 발생합니다. `Container` 소멸자는 이 예외를 처리하지 않으므로 예외가 상향 전파되고 세 번째 리소스가 해제되지 않습니다.

- 자식 작업에서 발생하는 예외는 `Container` 소멸자를 통해 전파됩니다. 소멸자에서 발생하면 애플리케이션이 정의되지 않은 상태가 됩니다.

이러한 작업이 취소되지 않도록 보장할 수 없는 경우 리소스 해제와 같은 중요한 작업을 수행하지 않는 것이 좋습니다. 또한 형식의 소멸자에서 발생할 수 있는 런타임 기능을 사용하지 않는 것이 좋습니다.

[[맨 위로](#top)이동]

## <a name="do-not-block-repeatedly-in-a-parallel-loop"></a><a name="repeated-blocking"></a> 병렬 루프에서 반복적으로 차단 하지 않습니다.

블로킹 작업으로 인해 발생 하는 [동시성::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 또는 [동시성::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 와 같은 병렬 루프는 런타임에서 짧은 시간 동안 많은 스레드를 만들 수 있습니다.

작업이 완료되거나 협조적으로 차단 또는 양보하는 경우 동시성 런타임에서 추가 작업을 수행합니다. 하나의 병렬 루트 반복이 차단되는 경우 런타임에서 다른 반복을 시작할 수 있습니다. 사용 가능한 유휴 스레드가 없는 경우 런타임에서 새 스레드를 만듭니다.

병렬 루프의 본문이 가끔 차단되는 경우 이 메커니즘은 전반적인 작업 처리량을 최대화하는 데 도움이 됩니다. 그러나 많은 반복이 차단되는 경우 런타임에서 추가 작업을 실행할 많은 스레드를 만들 수 있습니다. 이 경우 메모리 부족 상태 또는 하드웨어 리소스의 사용률 저하가 발생할 수 있습니다.

루프의 각 반복에서 [concurrency:: send](reference/concurrency-namespace-functions.md#send) 함수를 호출 하는 다음 예제를 살펴보십시오 `parallel_for` . `send`는 협조적으로 차단되기 때문에 런타임에서 `send`가 호출될 때마다 추가 작업을 실행할 새 스레드를 만듭니다.

[!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_12.cpp)]

이 패턴을 방지하려면 코드를 리팩터링하는 것이 좋습니다. 이 예제에서는 직렬 루프에서를 호출 하 여 추가 스레드를 만들지 않도록 방지할 수 있습니다 `send` **`for`** .

[[맨 위로](#top)이동]

## <a name="do-not-perform-blocking-operations-when-you-cancel-parallel-work"></a><a name="blocking"></a> 병렬 작업을 취소할 때 차단 작업 수행 안 함

가능 하면 [concurrency:: task_group:: cancel](reference/task-group-class.md#cancel) 또는 [concurrency:: structured_task_group:: cancel](reference/structured-task-group-class.md#cancel) 메서드를 호출 하 여 병렬 작업을 취소 하기 전에 차단 작업을 수행 하지 마십시오.

작업(task)이 협조적 차단 작업(operation)을 수행하면 첫 번째 작업(task)이 데이터를 기다리는 동안 런타임에서 다른 작업(work)을 수행할 수 있습니다. 대기 중인 작업이 차단 해제되면 런타임에서 다시 예약합니다. 일반적으로 런타임은 이전에 차단 해제된 작업을 다시 예약하기 전에 최근에 차단 해제된 작업을 다시 예약합니다. 따라서 런타임이 차단 작업 중에 불필요한 작업을 예약하여 성능 저하가 발생할 수 있습니다. 병렬 작업을 취소하기 전에 차단 작업을 수행하는 경우 차단 작업으로 인해 `cancel` 호출이 지연될 수 있습니다. 이 경우 다른 작업이 불필요한 작업을 수행합니다.

제공된 조건자 함수를 충족하는 제공된 배열의 요소를 검색하는 `parallel_find_answer` 함수를 정의하는 다음 예제를 고려해 보세요. 조건자 함수가 반환 될 때 **`true`** parallel work 함수는 개체를 만들고 `Answer` 전체 작업을 취소 합니다.

[!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_13.cpp)]

`new` 연산자는 차단될 수 있는 힙 할당을 수행합니다. 런타임은 [concurrency:: critical_section:: lock](reference/critical-section-class.md#lock)호출과 같이 협조적 차단 호출을 수행 하는 경우에만 다른 작업을 수행 합니다.

다음 예제에서는 불필요한 작업을 방지하여 성능을 향상시키는 방법을 보여 줍니다. 이 예제는 `Answer` 개체에 대한 스토리지를 할당하기 전에 작업 그룹을 취소합니다.

[!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_14.cpp)]

[[맨 위로](#top)이동]

## <a name="do-not-write-to-shared-data-in-a-parallel-loop"></a><a name="shared-writes"></a> 병렬 루프에서 공유 데이터에 쓰지 않음

동시성 런타임는 공유 데이터에 대 한 동시 액세스를 동기화 하는 여러 데이터 구조 (예: [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md))를 제공 합니다. 이러한 데이터 구조는 여러 작업이 가끔 리소스에 대한 공유 액세스를 요구하는 경우 등 여러 경우에서 유용합니다.

[동시성::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 알고리즘과 개체를 사용 하 여 `critical_section` [std:: array](../../standard-library/array-class-stl.md) 개체의 소수 수를 계산 하는 다음 예제를 살펴보십시오. 이 예제는 각 스레드가 공유 변수 `prime_sum`에 액세스하기 위해 대기해야 하므로 크기가 조정되지 않습니다.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_15.cpp)]

이 예제에서는 잦은 잠금 작업이 사실상 루프를 직렬화하기 때문에 성능이 저하될 수도 있습니다. 또한 동시성 런타임 개체가 차단 작업을 수행하는 경우 첫 번째 스레드가 데이터를 기다리는 동안 스케줄러에서 다른 작업을 수행할 추가 스레드를 만들 수 있습니다. 많은 작업이 공유 데이터를 대기 중이어서 런타임에서 많은 스레드를 만드는 경우 애플리케이션 성능이 저하되거나 리소스 부족 상태가 될 수 있습니다.

PPL은 [concurrency:: 결합할](../../parallel/concrt/reference/combinable-class.md) 수 있는 클래스를 정의 하며,이를 통해 잠금 없는 방식으로 공유 리소스에 대 한 액세스를 제공 하 여 공유 상태를 제거할 수 있습니다. `combinable` 클래스는 세분화된 계산을 수행한 다음 이러한 계산을 최종 결과로 병합할 수 있게 해주는 스레드 로컬 스토리지를 제공합니다. `combinable` 개체는 환산(reduction) 변수로 간주될 수 있습니다.

다음 예제에서는 `critical_section` 개체 대신 `combinable` 개체로 합계를 계산하여 앞의 예제를 수정합니다. 이 예제는 각 스레드가 합계의 자체 로컬 복사본을 유지하기 때문에 크기가 조정됩니다. 이 예제에서는 [concurrency:: 결합할 수:: combine](reference/combinable-class.md#combine) 메서드를 사용 하 여 로컬 계산을 최종 결과로 병합 합니다.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_16.cpp)]

이 예제의 전체 버전을 보려면 [방법: 결합 된 항목을 사용 하 여 성능 향상](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)을 참조 하세요. 클래스에 대 한 자세한 내용은 `combinable` [병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="when-possible-avoid-false-sharing"></a><a name="false-sharing"></a> 가능 하면 거짓 공유 방지

*False 공유* 는 별도의 프로세서에서 실행 되는 여러 동시 태스크가 동일한 캐시 줄에 있는 변수에 쓰는 경우에 발생 합니다. 한 작업이 변수 중 하나에 쓰는 경우 두 변수에 대한 캐시 라인이 모두 무효화됩니다. 캐시 라인이 무효화될 때마다 각 프로세서가 캐시 라인을 다시 로드해야 합니다. 따라서 거짓 공유로 인해 애플리케이션 성능이 저하될 수 있습니다.

다음 기본 예제에서는 각각 공유 카운터 변수를 증가시키는 두 개의 동시 작업을 보여 줍니다.

[!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_17.cpp)]

두 작업 간에 데이터 공유를 제거하기 위해 두 개의 카운터 변수를 사용하도록 예제를 수정할 수 있습니다. 이 예제에서는 작업이 완료된 후 최종 카운터 값을 계산합니다. 그러나 이 예제에서는 `count1` 및 `count2` 변수가 동일한 캐시 라인에 있을 가능성이 크기 때문에 거짓 공유를 보여 줍니다.

[!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_18.cpp)]

거짓 공유를 제거하는 한 가지 방법은 카운터 변수가 개별 캐시 라인에 있도록 하는 것입니다. 다음 예제에서는 `count1` 및 `count2` 변수를 64바이트 경계에 맞춥니다.

[!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_19.cpp)]

이 예제에서는 메모리 캐시의 크기가 64바이트 이하라고 가정합니다.

작업 간에 데이터를 공유 해야 하는 경우 [concurrency:: 결합할](../../parallel/concrt/reference/combinable-class.md) 수 있는 클래스를 사용 하는 것이 좋습니다. `combinable` 클래스는 거짓 공유의 가능성이 더 낮도록 스레드 지역 변수를 만듭니다. 클래스에 대 한 자세한 내용은 `combinable` [병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="make-sure-that-variables-are-valid-throughout-the-lifetime-of-a-task"></a><a name="lifetime"></a> 변수가 작업의 수명 내내 유효 하는지 확인 합니다.

작업 그룹 또는 병렬 알고리즘에 람다 식을 제공하는 경우 캡처 절은 람다 식의 본문이 값이나 참조로 바깥쪽 범위의 변수에 액세스하는지를 지정합니다. 변수를 참조로 람다 식에 전달하는 경우 작업이 완료될 때까지 해당 변수의 수명이 유지되도록 보장해야 합니다.

`object` 클래스 및 `perform_action` 함수를 정의하는 다음 예제를 고려해 보세요. `perform_action` 함수는 `object` 변수를 만들고 해당 변수에 대해 비동기적으로 일부 작업을 수행합니다. `perform_action` 함수가 반환되기 전에 작업이 완료되도록 보장되지 않으므로 작업을 실행 중일 때 `object` 변수가 제거되면 프로그램 작동이 중단되거나 지정되지 않은 동작이 나타납니다.

[!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_20.cpp)]

애플리케이션의 요구 사항에 따라 다음 기술 중 하나를 사용하여 변수가 각 작업의 전체 수명 동안 유효하도록 보장할 수 있습니다.

다음 예제에서는 값으로 `object` 변수를 작업에 전달합니다. 따라서 작업이 변수의 자체 복사본에서 작동합니다.

[!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_21.cpp)]

`object` 변수가 값으로 전달되기 때문에 이 변수에 발생하는 상태 변경 내용은 원래 복사본에 나타나지 않습니다.

다음 예제에서는 [concurrency:: task_group:: wait](reference/task-group-class.md#wait) 메서드를 사용 하 여 함수가 반환 되기 전에 태스크가 완료 되는지 확인 합니다 `perform_action` .

[!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_22.cpp)]

이제 함수가 반환되기 전에 작업이 완료되기 때문에 `perform_action` 함수가 더 이상 비동기적으로 동작하지 않습니다.

다음 예제에서는 `object` 변수에 대한 참조를 사용하도록 `perform_action` 함수를 수정합니다. 호출자는 작업이 완료될 때까지 `object` 변수의 수명이 유효하도록 보장해야 합니다.

[!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_23.cpp)]

포인터를 사용하여 작업 그룹 또는 병렬 알고리즘에 전달하는 개체의 수명을 제어할 수도 있습니다.

람다 식에 대 한 자세한 내용은 [람다 식](../../cpp/lambda-expressions-in-cpp.md)을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="see-also"></a>참고 항목

[동시성 런타임 모범 사례](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[PPL(병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL에서의 취소](cancellation-in-the-ppl.md)<br/>
[예외 처리](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[연습: Image-Processing 네트워크 만들기](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[방법: parallel_invoke를 사용 하 여 병렬 정렬 루틴 작성](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br/>
[방법: 취소를 사용 하 여 병렬 루프 중단](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br/>
[방법: 결합을 사용 하 여 성능 향상](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
[비동기 에이전트 라이브러리의 모범 사례](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br/>
[동시성 런타임의 일반적인 모범 사례](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
