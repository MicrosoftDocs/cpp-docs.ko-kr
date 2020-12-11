---
description: '자세한 정보: 방법: parallel_for_each 루프 작성'
title: '방법: parallel_for_each 루프 작성'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
ms.openlocfilehash: cb80173d3d4c78fe4d46f017d60af2c3c6659096
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112234"
---
# <a name="how-to-write-a-parallel_for_each-loop"></a>방법: parallel_for_each 루프 작성

이 예제에서는 [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 알고리즘을 사용 하 여 [std:: array](../../standard-library/array-class-stl.md) 개체의 소수 수를 병렬로 계산 하는 방법을 보여 줍니다.

## <a name="example"></a>예제

다음 예제에서는 배열에서 두 번의 소수 수를 계산 합니다. 이 예에서는 먼저 [std:: for_each](../../standard-library/algorithm-functions.md#for_each) 알고리즘을 사용 하 여 카운트를 순차적으로 계산 합니다. 그런 다음이 예제에서는 알고리즘을 사용 하 여 `parallel_for_each` 동일한 작업을 병렬로 수행 합니다. 또한 이 예제에서는 두 계산을 모두 수행하는 데 필요한 시간을 콘솔에 출력합니다.

[!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]

프로세서가 4개인 컴퓨터의 샘플 출력은 다음과 같습니다.

```Output
serial version:
found 17984 prime numbers
took 6115 ms

parallel version:
found 17984 prime numbers
took 1653 ms
```

## <a name="compiling-the-code"></a>코드 컴파일

코드를 컴파일하려면 코드를 복사한 다음 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 후 `parallel-count-primes.cpp` Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc parallel-count-primes**

## <a name="robust-programming"></a>강력한 프로그래밍

예제가 알고리즘에 전달 하는 람다 식은 `parallel_for_each` 함수를 사용 하 여 `InterlockedIncrement` 루프의 병렬 반복을 통해 카운터를 동시에 증가 시킵니다. 와 같은 함수를 사용 하 여 `InterlockedIncrement` 공유 리소스에 대 한 액세스를 동기화 하는 경우 코드에 성능 병목 현상을 제공할 수 있습니다. 공유 리소스에 대 한 동시 액세스를 제거 하는 데 필요한 잠금 없는 동기화 메커니즘 (예: [concurrency:: 결합할](../../parallel/concrt/reference/combinable-class.md) 수 있는 클래스)을 사용할 수 있습니다. 이러한 방식으로 클래스를 사용 하는 예제는 `combinable` [방법: 조합 사용을 사용 하 여 성능 향상](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for_each 함수](reference/concurrency-namespace-functions.md#parallel_for_each)
