---
description: '자세한 정보: 방법: parallel_for 루프 작성'
title: '방법: parallel_for 루프 작성'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
ms.openlocfilehash: ccf66c3e457b540721f0a76722b9d17206cf0f7f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205696"
---
# <a name="how-to-write-a-parallel_for-loop"></a>방법: parallel_for 루프 작성

이 예제에서는 [동시성::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 를 사용 하 여 두 매트릭스의 곱을 계산 하는 방법을 보여 줍니다.

## <a name="example-compute-the-product-of-two-matrices"></a>예: 두 매트릭스의 곱 계산

다음 예제에서는 `matrix_multiply` 두 개의 사각형 행렬의 곱을 계산 하는 함수를 보여 줍니다.

[!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]

## <a name="example-compute-a-matrix-multiply-in-parallel"></a>예: 병렬로 행렬 곱하기 계산

다음 예제에서는 알고리즘을 `parallel_matrix_multiply` 사용 하 여 `parallel_for` 외부 루프를 병렬로 수행 하는 함수를 보여 줍니다.

[!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]

이 예제에서는 병렬 처리에 대 한 오버 헤드를 활용 하기 위해 충분 한 작업을 수행 하기 때문에 외부 루프를 데이터가 아니라 합니다. 내부 루프를 병렬화 하는 경우 내부 루프에서 수행 하는 소량의 작업이 병렬 처리에 대 한 오버 헤드를 극복 하지 않으므로 성능이 향상 되지 않습니다. 따라서 외부 루프만 병렬 처리하는 것이 대부분의 시스템에서 동시성의 이점을 극대화하는 가장 좋은 방법입니다.

## <a name="example-finished-parallel_for-loop-code-sample"></a>예: 마침 parallel_for 루프 코드 샘플

다음의 전체 예제에서는 함수와 함수의 성능을 비교 합니다 `matrix_multiply` `parallel_matrix_multiply` .

[!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]

프로세서가 4개인 컴퓨터의 샘플 출력은 다음과 같습니다.

```Output
serial: 3853
parallel: 1311
```

## <a name="compiling-the-code"></a>코드 컴파일

코드를 컴파일하려면 코드를 복사한 다음 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 후 `parallel-matrix-multiply.cpp` Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc parallel-matrix-multiply**

## <a name="see-also"></a>참고 항목

[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for 함수](reference/concurrency-namespace-functions.md#parallel_for)
