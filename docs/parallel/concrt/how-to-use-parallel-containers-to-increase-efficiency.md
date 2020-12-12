---
description: '자세한 정보: 방법: 병렬 컨테이너를 사용 하 여 효율성 향상'
title: '방법: 병렬 컨테이너를 사용하여 효율성 향상'
ms.date: 11/04/2016
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
ms.openlocfilehash: 6e416da7b1cdcbe1a9b3073569cf4dda6434ceea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341557"
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>방법: 병렬 컨테이너를 사용하여 효율성 향상

이 항목에서는 병렬 컨테이너를 사용 하 여 데이터를 효율적으로 효율적으로 저장 하 고 액세스 하는 방법을 보여 줍니다.

예제 코드는 소수 및 Carmichael 숫자 집합을 병렬로 계산 합니다. 그런 다음, 각 Carmichael 수에 대해 코드는 해당 숫자의 소수 부분을 계산 합니다.

## <a name="example-determine-if-an-input-value-is-a-prime-number"></a>예: 입력 값이 소수 인지 확인

다음 예에서는 `is_prime` 입력 값이 소수 인지 여부를 확인 하는 함수 및 `is_carmichael` 입력 값이 Carmichael number 인지 여부를 결정 하는 함수를 보여 줍니다.

[!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]

## <a name="example-compute-prime-and-carmichael-numbers"></a>예: Compute 소수 및 Carmichael 번호

다음 예에서는 및 함수를 사용 하 여 `is_prime` `is_carmichael` 소수 및 Carmichael 숫자 집합을 계산 합니다. 이 예제에서는 [동시성::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) 및 [동시성::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 알고리즘을 사용 하 여 각 집합을 병렬로 계산 합니다. 병렬 알고리즘에 대 한 자세한 내용은 [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요.

이 예제에서는 [concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) 개체를 사용 하 여 Carmichael 번호 집합을 저장 합니다 .이는 나중에 해당 개체를 작업 큐로 사용 하기 때문입니다. 이는 나중에이 집합을 반복 하 여 프라임 요인을 찾기 때문에 [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 개체를 사용 하 여 소수 집합을 저장 합니다.

[!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]

## <a name="example-find-all-prime-factors-of-a-given-value"></a>예: 지정 된 값의 모든 소수 요소 찾기

다음 예에서는 `prime_factors_of` 체험 나누기를 사용 하 여 지정 된 값의 모든 소수 요소를 찾는 함수를 보여 줍니다.

이 함수는 [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 알고리즘을 사용 하 여 소수 컬렉션을 반복 합니다. `concurrent_vector`개체를 사용 하면 병렬 루프에서 결과에 소수 요소를 동시에 추가할 수 있습니다.

[!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]

## <a name="example-processes-each-element-in-the-queue-of-carmichael-numbers"></a>예: Carmichael 번호의 큐에 있는 각 요소를 처리 합니다.

이 예제에서는 함수를 호출 하 여 Carmichael 수의 큐에 있는 각 요소를 처리 `prime_factors_of` 하 여 해당 소수 요소를 계산 합니다. 작업 그룹을 사용 하 여이 작업을 병렬로 수행 합니다. 작업 그룹에 대 한 자세한 내용은 [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)를 참조 하세요.

이 예에서는 각 Carmichael number의 소수 요소가 4 개를 초과 하는 경우 각 숫자의 소수 요소를 인쇄 합니다.

[!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]

## <a name="example-finished-parallel-container-code-sample"></a>예: 완료 된 병렬 컨테이너 코드 샘플

다음 코드에서는 병렬 컨테이너를 사용 하 여 Carmichael 숫자의 소수 부분을 계산 하는 전체 예제를 보여 줍니다.

[!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]

이 예제에서는 다음 샘플 출력을 생성 합니다.

```Output
Prime factors of 9890881 are: 7 11 13 41 241.
Prime factors of 825265 are: 5 7 17 19 73.
Prime factors of 1050985 are: 5 13 19 23 37.
```

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `carmichael-primes.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc carmichael-primes**

## <a name="see-also"></a>참고 항목

[병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[concurrent_vector 클래스](../../parallel/concrt/reference/concurrent-vector-class.md)<br/>
[concurrent_queue 클래스](../../parallel/concrt/reference/concurrent-queue-class.md)<br/>
[parallel_invoke 함수](reference/concurrency-namespace-functions.md#parallel_invoke)<br/>
[parallel_for 함수](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[task_group 클래스](reference/task-group-class.md)
