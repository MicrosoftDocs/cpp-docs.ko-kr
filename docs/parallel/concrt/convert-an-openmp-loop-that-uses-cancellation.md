---
title: '방법: 동시성 런타임을 사용하기 위해 취소를 사용하는 OpenMP 루프 변환'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
ms.openlocfilehash: adde6decc086b883c50e52d12e388197e185fb39
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505947"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>방법: 동시성 런타임을 사용하기 위해 취소를 사용하는 OpenMP 루프 변환

일부 병렬 루프에서는 모든 반복을 실행할 필요가 없습니다. 예를 들어 값을 검색 하는 알고리즘은 값을 찾은 후 종료 될 수 있습니다. OpenMP는 병렬 루프를 중단 하는 메커니즘을 제공 하지 않습니다. 그러나 부울 값 또는 플래그를 사용 하 여 루프 반복을 사용 하도록 설정 하 여 솔루션이 발견 되었음을 나타낼 수 있습니다. 동시성 런타임은 한 작업에서 아직 시작 되지 않은 다른 작업을 취소할 수 있도록 하는 기능을 제공 합니다.

이 예에서는 동시성 런타임 취소 메커니즘을 사용 하기 위해 모든 반복을 실행할 필요가 없는 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) 루프를 변환 하는 방법을 보여 줍니다.

## <a name="example"></a>예제

이 예제에서는 OpenMP와 동시성 런타임를 모두 사용 하 여 [std:: any_of](../../standard-library/algorithm-functions.md#any_of) 알고리즘의 병렬 버전을 구현 합니다. 이 예제의 OpenMP 버전에서는 플래그를 사용 하 여 조건이 충족 된 모든 병렬 루프 반복 간에 조정 합니다. 동시성 런타임를 사용 하는 버전은 [Concurrency:: structured_task_group:: cancel](reference/structured-task-group-class.md#cancel) 메서드를 사용 하 여 조건이 충족 될 때 전체 작업을 중지 합니다.

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

OpenMP를 사용 하는 버전에서 플래그가 설정 된 경우에도 루프의 모든 반복이 실행 됩니다. 또한 태스크가 자식 작업을 포함 하는 경우 해당 자식 작업에서 취소를 전달 하는 데에도 플래그를 사용할 수 있어야 합니다. 동시성 런타임에서 작업 그룹이 취소 되 면 런타임에서 자식 작업을 비롯 한 전체 작업 트리를 취소 합니다. [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 알고리즘은 작업을 사용 하 여 작업을 수행 합니다. 따라서 루프의 반복 하나가 루트 작업을 취소 하면 계산의 전체 트리도 취소 됩니다. 작업 트리를 취소 하면 런타임에서 새 작업을 시작 하지 않습니다. 그러나 런타임에서는 이미 완료 된 작업을 허용 합니다. 따라서 알고리즘의 경우 `parallel_for_each` 활성 루프 반복은 해당 리소스를 정리할 수 있습니다.

이 예제의 두 버전에서 배열에 검색할 값의 복사본이 두 개 이상 포함 된 경우 여러 루프 반복에서 결과를 동시에 설정 하 고 전체 작업을 취소할 수 있습니다. 중요 한 섹션과 같은 동기화 기본 형식을 사용할 수 있습니다. 문제가 발생 하면 조건이 충족 될 때 하나의 작업만 작업을 수행 해야 하는 경우입니다.

또한 예외 처리를 사용 하 여 PPL을 사용 하는 작업을 취소할 수 있습니다. 취소에 대 한 자세한 내용은 [PPL에서의 취소](cancellation-in-the-ppl.md)를 참조 하세요.

및 기타 병렬 알고리즘에 대 한 자세한 내용은 `parallel_for_each` [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `concrt-omp-parallel-any-of.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc/openmp concrt-omp-parallel-any-of**

## <a name="see-also"></a>참고 항목

[OpenMP에서 동시성 런타임으로 마이그레이션](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[PPL에서의 취소](cancellation-in-the-ppl.md)<br/>
[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)
