---
title: '방법: 동시성 런타임을 사용하기 위해 OpenMP parallel for 루프 변환'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
ms.openlocfilehash: 4f523f9f6de7f1ffb4c3b578b60de587239dffb6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507877"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>방법: 동시성 런타임을 사용하기 위해 OpenMP parallel for 루프 변환

이 예에서는 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) 을 사용 하는 기본 루프를 변환 하는 방법과 동시성 런타임 [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 알고리즘을 사용 하 [는 지시문을](../openmp/reference/openmp-directives.md#for-openmp) 변환 하는 방법을 보여 줍니다.

## <a name="example---prime-count"></a>예제-소수 개수

이 예제에서는 OpenMP와 동시성 런타임를 모두 사용 하 여 난수 배열의 소수 수를 계산 합니다.

[!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
Using OpenMP...
found 107254 prime numbers.
Using the Concurrency Runtime...
found 107254 prime numbers.
```

`parallel_for`알고리즘 및 OpenMP 3.0는 인덱스 형식이 부호 있는 정수 계열 형식 또는 부호 없는 정수 형식이 될 수 있도록 허용 합니다. `parallel_for`또한 알고리즘은 지정 된 범위에서 부호 있는 형식을 오버플로 하지 않도록 합니다. OpenMP 버전 2.0 및 2.5는 부호 있는 정수 계열 인덱스 형식만 허용 합니다. 또한 OpenMP는 인덱스 범위의 유효성을 검사 하지 않습니다.

동시성 런타임를 사용 하는이 예제의 버전은 [원자성](../openmp/reference/openmp-directives.md#atomic) 지시문 대신 [Concurrency:: 결합할](../../parallel/concrt/reference/combinable-class.md) 수 있는 개체를 사용 하 여 동기화를 요구 하지 않고 카운터 값을 증가 시킵니다.

및 기타 병렬 알고리즘에 대 한 자세한 내용은 `parallel_for` [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요. 클래스에 대 한 자세한 내용은 `combinable` [병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)를 참조 하세요.

## <a name="example---use-stdarray"></a>예제-std:: array 사용

이 예제에서는 네이티브 배열이 아니라 [std:: array](../../standard-library/array-class-stl.md) 개체에 대해 작동 하도록 이전 항목을 수정 합니다. OpenMP 버전 2.0 및 2.5에서는 구문에서 부호 있는 정수 계열 인덱스 형식만 허용 하므로 `parallel_for` 반복기를 사용 하 여 c + + 표준 라이브러리 컨테이너의 요소에 병렬로 액세스할 수는 없습니다. PPL (병렬 패턴 라이브러리)은 c + + 표준 라이브러리에서 제공 하는 것과 같은 반복적인 컨테이너에서 작업을 병렬로 수행 하는 [동시성::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 알고리즘을 제공 합니다. 알고리즘에서 사용 하는 것과 동일한 분할 논리를 사용 `parallel_for` 합니다. 알고리즘은 `parallel_for_each` 작업을 동시에 실행 한다는 점을 제외 하 고 c + + 표준 라이브러리 [std:: for_each](../../standard-library/algorithm-functions.md#for_each) 알고리즘과 유사 `parallel_for_each` 합니다.

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `concrt-omp-count-primes.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc/openmp concrt-omp-count-primes**

## <a name="see-also"></a>참고 항목

[OpenMP에서 동시성 런타임으로 마이그레이션](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)<br/>
[병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)
