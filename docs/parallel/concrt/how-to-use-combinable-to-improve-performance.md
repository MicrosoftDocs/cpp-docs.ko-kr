---
description: '자세히 알아보기: 방법: 조합 하 여 성능 향상'
title: '방법: combinable을 사용하여 성능 개선'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
ms.openlocfilehash: b9ab906f00f32fee59e2dd9a1131fe87fcbc53a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283305"
---
# <a name="how-to-use-combinable-to-improve-performance"></a>방법: combinable을 사용하여 성능 개선

이 예제에서는 [concurrency:: 결합할](../../parallel/concrt/reference/combinable-class.md) 수 있는 클래스를 사용 하 여 [std:: array](../../standard-library/array-class-stl.md) 개체에서 소수 부분에 있는 숫자의 합계를 계산 하는 방법을 보여 줍니다. `combinable`클래스는 공유 상태를 제거 하 여 성능을 향상 시킵니다.

> [!TIP]
> 경우에 따라 병렬 맵 ([동시성::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)) 및 감소 ([concurrency:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce))를 통해 성능을 향상 시킬 수 있습니다 `combinable` . Map 및 줄임 연산을 사용 하 여이 예제와 동일한 결과를 생성 하는 예제는 [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요.

## <a name="example---accumulate"></a>예제-누적

다음 예제에서는 [std:: 누적](../../standard-library/numeric-functions.md#accumulate) 함수를 사용 하 여 배열의 요소에 대 한 합계를 계산 합니다. 이 예제에서 `a` 는 개체이 `array` 고 함수는 `is_prime` 해당 입력 값이 소수 인지 여부를 확인 합니다.

[!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]

## <a name="example---parallel_for_each"></a>예제-parallel_for_each

다음 예제에서는 이전 예제를 병렬화 하는 naive 방법을 보여 줍니다. 이 예제에서는 [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 알고리즘을 사용 하 여 배열을 병렬로 처리 하 고 [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) 개체를 사용 하 여 변수에 대 한 액세스를 동기화 `prime_sum` 합니다. 각 스레드가 공유 리소스를 사용할 수 있을 때까지 기다려야 하므로이 예제는 크기가 조정 되지 않습니다.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]

## <a name="example---combinable"></a>예제-결합 가능한

다음 예제에서는 개체를 사용 하 여 `combinable` 이전 예제의 성능을 향상 시킵니다. 이 예제에서는 동기화 개체의 필요성을 제거 합니다. `combinable` 개체를 사용 하면 각 스레드가 태스크를 독립적으로 수행할 수 있으므로 크기가 조정 됩니다.

`combinable`개체는 일반적으로 두 단계에서 사용 됩니다. 먼저 작업을 병렬로 수행 하 여 세분화 된 일련의 계산을 생성 합니다. 그런 다음 계산을 최종 결과로 결합 (또는 감소) 합니다. 이 예제에서는 [concurrency:: 결합할 수:: local](reference/combinable-class.md#local) 메서드를 사용 하 여 로컬 합계에 대 한 참조를 가져옵니다. 그런 다음 [concurrency:: lu:: combine](reference/combinable-class.md#combine) 메서드 및 [std::p](../../standard-library/plus-struct.md) 개체를 사용 하 여 로컬 계산을 최종 결과로 결합 합니다.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]

## <a name="example---serial-and-parallel"></a>예-직렬 및 병렬

다음 전체 예제에서는 프라임 숫자의 합계를 직렬 및 병렬 모두 계산 합니다. 이 예제에서는 두 계산을 모두 수행 하는 데 필요한 시간을 콘솔에 출력 합니다.

[!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]

프로세서가 4개인 컴퓨터의 샘플 출력은 다음과 같습니다.

```Output
1709600813
serial time: 6178 ms

1709600813
parallel time: 1638 ms
```

## <a name="compiling-the-code"></a>코드 컴파일

코드를 컴파일하려면 코드를 복사한 다음 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 후 `parallel-sum-of-primes.cpp` Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc parallel-sum-of-primes**

## <a name="robust-programming"></a>강력한 프로그래밍

Map 및 줄임 연산을 사용 하 여 동일한 결과를 생성 하는 예제는 [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[결합 가능한 클래스](../../parallel/concrt/reference/combinable-class.md)<br/>
[critical_section 클래스](../../parallel/concrt/reference/critical-section-class.md)
