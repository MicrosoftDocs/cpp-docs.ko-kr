---
description: '자세한 정보: 방법: parallel_invoke를 사용 하 여 병렬 정렬 루틴 작성'
title: '방법: parallel_invoke를 사용하여 병렬 정렬 루틴 작성'
ms.date: 11/04/2016
helpviewer_keywords:
- task_handle class, example
- task_group class, example
- make_task function, example
- structured_task_group class, example
- improving parallel performance with task groups [Concurrency Runtime]
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
ms.openlocfilehash: 4146bed939e265f611d79c465681c10ef28a1ebe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205670"
---
# <a name="how-to-use-parallel_invoke-to-write-a-parallel-sort-routine"></a>방법: parallel_invoke를 사용하여 병렬 정렬 루틴 작성

이 문서에서는 [parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke) 알고리즘을 사용 하 여 바 이토 닉 정렬 알고리즘의 성능을 향상 시키는 방법을 설명 합니다. 바 이토 닉 정렬 알고리즘은 입력 시퀀스를 더 작은 정렬 된 파티션으로 재귀적으로 나눕니다. 각 파티션 작업은 다른 모든 작업과 독립적 이므로, 바 이토 닉 정렬 알고리즘은 병렬로 실행할 수 있습니다.

바 이토 닉 정렬은 모든 입력 시퀀스 조합을 정렬 하는 *정렬 네트워크* 의 한 예 이지만,이 예제에서는 길이가 2의 거듭제곱 인 시퀀스를 정렬 합니다.

> [!NOTE]
> 이 예제에서는 이해를 돕기 위해 병렬 정렬 루틴을 사용합니다. PPL에서 제공 하는 기본 제공 정렬 알고리즘인 [동시성::p arallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [동시성::p arallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)및 [동시성::p arallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort)를 사용할 수도 있습니다. 자세한 내용은 [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요.

## <a name="sections"></a><a name="top"></a> 섹션이

이 문서에서는 다음 작업에 대해 설명 합니다.

- [직렬에서 바 이토 않은 정렬 수행](#serial)

- [Parallel_invoke를 사용 하 여 동시에 바 이토 닉 정렬 수행](#parallel)

## <a name="performing-bitonic-sort-serially"></a><a name="serial"></a> 직렬에서 바 이토 않은 정렬 수행

다음 예에서는 바 이토 닉 정렬 알고리즘의 일련 버전을 보여 줍니다. `bitonic_sort`함수는 시퀀스를 두 개의 파티션으로 나누고, 해당 파티션을 반대 방향으로 정렬 한 다음 결과를 병합 합니다. 이 함수는 자신을 두 번 재귀적으로 호출 하 여 각 파티션을 정렬 합니다.

[!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]

[[맨 위로](#top)이동]

## <a name="using-parallel_invoke-to-perform-bitonic-sort-in-parallel"></a><a name="parallel"></a> Parallel_invoke를 사용 하 여 동시에 바 이토 닉 정렬 수행

이 섹션에서는 알고리즘을 사용 하 여 `parallel_invoke` 바 이토 닉 정렬 알고리즘을 병렬로 수행 하는 방법을 설명 합니다.

### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>바 이토 닉 정렬 알고리즘을 병렬로 수행 하려면

1. `#include`헤더 파일 ppl에 대 한 지시문을 추가 합니다.

[!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]

1. **`using`** 네임 스페이스에 대 한 지시문을 추가 `concurrency` 합니다.

[!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]

1. `parallel_bitonic_mege` `parallel_invoke` 수행할 작업의 양이 충분 한 경우 알고리즘을 사용 하 여 시퀀스를 병렬로 병합 하는 라는 새 함수를 만듭니다. 그렇지 않으면를 호출 `bitonic_merge` 하 여 시퀀스를 직렬로 병합 합니다.

[!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]

1. 이전 단계에 있는 것과 유사한 프로세스를 수행 `bitonic_sort` 합니다.

[!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]

1. `parallel_bitonic_sort`배열을 오름차순으로 정렬 하는 함수의 오버 로드 된 버전을 만듭니다.

[!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]

`parallel_invoke`알고리즘은 호출 컨텍스트에서 마지막 일련의 작업을 수행 하 여 오버 헤드를 줄입니다. 예를 들어 함수에서 `parallel_bitonic_sort` 첫 번째 작업은 별도의 컨텍스트에서 실행 되 고 두 번째 작업은 호출 컨텍스트에서 실행 됩니다.

[!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]

다음 전체 예제에서는 바 이토 닉 정렬 알고리즘의 직렬 및 병렬 버전을 모두 수행 합니다. 또한이 예제에서는 각 계산을 수행 하는 데 필요한 시간을 콘솔에 출력 합니다.

[!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]

프로세서가 4개인 컴퓨터의 샘플 출력은 다음과 같습니다.

```Output
serial time: 4353
parallel time: 1248
```

[[맨 위로](#top)이동]

### <a name="compiling-the-code"></a>코드 컴파일

코드를 컴파일하려면 코드를 복사한 다음 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 후 `parallel-bitonic-sort.cpp` Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc parallel-bitonic-sort**

## <a name="robust-programming"></a>강력한 프로그래밍

이 예제에서는 `parallel_invoke` 각 작업 그룹의 수명이 함수를 벗어나 확장 되지 않으므로 [concurrency:: task_group](reference/task-group-class.md) 클래스 대신 알고리즘을 사용 합니다. `parallel_invoke`개체 보다 실행 오버 헤드가 적기 때문에를 사용 하는 것이 좋습니다 `task group` . 따라서 더 나은 성능을 제공 하는 코드를 작성할 수 있습니다.

일부 알고리즘의 병렬 버전은 수행할 작업이 충분 한 경우에만 더 잘 수행 됩니다. 예를 들어 `parallel_bitonic_merge` 시퀀스에 500 개 이하의 요소가 있으면 함수는 일련 버전를 호출 합니다 `bitonic_merge` . 작업 양에 따라 전체 정렬 전략을 계획할 수도 있습니다. 예를 들어 다음 예제와 같이 배열에 500 개 미만의 항목이 포함 된 경우 빠른 정렬 알고리즘의 일련 버전을 사용 하는 것이 더 효율적일 수 있습니다.

[!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]

모든 병렬 알고리즘과 마찬가지로 코드를 적절 하 게 프로 파일링 하 고 조정 하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목

[작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[parallel_invoke 함수](reference/concurrency-namespace-functions.md#parallel_invoke)
