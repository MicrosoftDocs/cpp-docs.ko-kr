---
description: '방법: 방법: 매핑 수행 및 병렬 작업 줄이기'
title: '방법: 매핑 수행 및 병렬 작업 줄이기'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
ms.openlocfilehash: f35c9bf4df5a79cf9568bc286ff628e2f9fd45c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209843"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>방법: 매핑 수행 및 병렬 작업 줄이기

이 예제에서는 [동시성::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) 및 [동시성::p arallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) 알고리즘과 [concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) 클래스를 사용 하 여 파일에서 단어의 발생 횟수를 계산 하는 방법을 보여 줍니다.

*Map* 연산은 시퀀스의 각 값에 함수를 적용 합니다. *감소* 연산은 시퀀스의 요소를 하나의 값으로 결합 합니다. C + + 표준 라이브러리 [std:: transform](../../standard-library/algorithm-functions.md#transform) 및 [std:: 누적](../../standard-library/numeric-functions.md#accumulate) 함수를 사용 하 여 맵 및 감소 작업을 수행할 수 있습니다. 그러나 많은 문제에 대해 성능을 향상시키기 위해 `parallel_transform` 알고리즘을 사용하여 매핑 작업을 병렬로 수행하고, `parallel_reduce` 알고리즘을 사용하여 줄이기 작업을 병렬로 수행할 수 있습니다. 경우에 따라 `concurrent_unordered_map`을 사용하여 매핑과 줄이기를 하나의 작업으로 수행할 수도 있습니다.

## <a name="example"></a>예제

다음 예제에서는 파일에서 단어가 나타나는 횟수를 계산합니다. [Std:: vector](../../standard-library/vector-class.md) 를 사용 하 여 두 파일의 내용을 나타냅니다. 매핑 작업은 각 벡터에서 각 단어가 나타나는 횟수를 계산합니다. 줄이기 작업은 두 벡터의 단어 개수를 누적합니다.

[!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]

## <a name="compiling-the-code"></a>코드 컴파일

코드를 컴파일하려면 코드를 복사한 다음 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 후 `parallel-map-reduce.cpp` Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc parallel-map-reduce**

## <a name="robust-programming"></a>강력한 프로그래밍

이 예제에서는 concurrent_unordered_map.h에서 정의된 `concurrent_unordered_map` 클래스를 사용하여 매핑과 줄이기를 하나의 작업으로 수행할 수 있습니다.

[!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]

일반적으로 외부 또는 내부 루프만 평행화합니다. 비교적 적은 파일이 있고 각 파일이 많은 단어를 포함하는 경우 내부 루프를 평행화합니다. 비교적 많은 파일이 있고 각 파일이 적은 단어를 포함하는 경우 외부 루프를 평행화합니다.

## <a name="see-also"></a>참고 항목

[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_transform 함수](reference/concurrency-namespace-functions.md#parallel_transform)<br/>
[parallel_reduce 함수](reference/concurrency-namespace-functions.md#parallel_reduce)<br/>
[concurrent_unordered_map 클래스](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
