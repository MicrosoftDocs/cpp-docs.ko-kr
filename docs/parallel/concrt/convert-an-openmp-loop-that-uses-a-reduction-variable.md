---
description: '자세한 정보: 방법: 동시성 런타임를 사용 하기 위해 환산 변수를 사용 하는 OpenMP 루프 변환'
title: '방법: 동시성 런타임을 사용하기 위해 환산 변수를 사용하는 OpenMP 루프 변환'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: 131585caf3e06a11ed45bda4b58efa541272006f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325760"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>방법: 동시성 런타임을 사용하기 위해 환산 변수를 사용하는 OpenMP 루프 변환

이 예에서는 [reduction](../openmp/reference/openmp-clauses.md#reduction) 절을 사용 하 여 동시성 런타임를 사용 하는 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) 루프를 변환 하는 방법을 보여 줍니다.

OpenMP `reduction` 절을 사용 하면 병렬 영역 끝에 감소 작업을 적용 하는 스레드 전용 변수를 하나 이상 지정할 수 있습니다. OpenMP는 축소 연산자 집합을 기본값으로 설정 합니다. 각 감소 변수는 스칼라 여야 합니다 (예: **`int`** , **`long`** 및 **`float`** ). OpenMP는 병렬 지역에서 감소 변수가 사용 되는 방법에 대 한 몇 가지 제한 사항도 정의 합니다.

PPL (병렬 패턴 라이브러리)은 세분화 된 계산을 수행한 다음 해당 계산을 최종 결과로 병합할 수 있는 재사용 가능한 스레드 로컬 저장소를 제공 하는 [concurrency:: 결합할](../../parallel/concrt/reference/combinable-class.md) 수 있는 클래스를 제공 합니다. `combinable`클래스는 스칼라 및 복합 형식 둘 다에서 작동 하는 템플릿입니다. 클래스를 사용 하려면 `combinable` 병렬 구문의 본문에서 하위 계산을 수행한 다음 [concurrency:: combine:: combine](reference/combinable-class.md#combine) 또는 [concurrency::](reference/combinable-class.md#combine_each) 결합할 수:: combine_each 메서드를 호출 하 여 최종 결과를 생성 합니다. `combine`및 메서드는 각 `combine_each` 요소 쌍을 결합 하는 방법을 지정 하는 *combine 함수* 를 사용 합니다. 따라서 클래스는 `combinable` 고정 된 축소 연산자 집합으로 제한 되지 않습니다.

## <a name="example"></a>예제

이 예에서는 OpenMP와 동시성 런타임를 모두 사용 하 여 처음 35 피보나치 수의 합계를 계산 합니다.

[!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
Using OpenMP...
The sum of the first 35 Fibonacci numbers is 14930351.
Using the Concurrency Runtime...
The sum of the first 35 Fibonacci numbers is 14930351.
```

클래스에 대 한 자세한 내용은 `combinable` [병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)를 참조 하세요.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `concrt-omp-fibonacci-reduction.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc/openmp concrt-omp-fibonacci-reduction**

## <a name="see-also"></a>참고 항목

[OpenMP에서 동시성 런타임으로 마이그레이션](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)
