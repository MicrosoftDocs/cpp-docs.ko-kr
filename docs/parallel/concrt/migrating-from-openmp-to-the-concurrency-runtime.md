---
title: OpenMP에서 동시성 런타임으로 마이그레이션
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
ms.openlocfilehash: 081d0ae8b312d827a0af98dd45c62f7563e81677
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507766"
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>OpenMP에서 동시성 런타임으로 마이그레이션

동시성 런타임은 다양한 프로그래밍 모델을 사용합니다. 이러한 모델은 중복되거나 다른 라이브러리의 모델을 보완할 수 있습니다. 이 단원의 문서에서는 [openmp](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) 와 동시성 런타임를 비교 하 고 동시성 런타임 사용 하도록 기존 OpenMP 코드를 마이그레이션하는 방법에 대 한 예제를 제공 합니다.

OpenMP 프로그래밍 모델은 공개 표준에 의해 정의되며, Fortran 및 C/C++ 프로그래밍 언어에 대한 잘 정의된 바인딩을 가지고 있습니다. Microsoft c + + 컴파일러에서 지원 되는 OpenMP 버전 2.0 및 2.5은 반복적인 병렬 알고리즘에 적합 합니다. 즉, 데이터 배열에 대 한 병렬 반복을 수행 합니다. OpenMP 3.0은 반복적인 작업 뿐만 아니라 반복적인 작업을 지원 합니다.

OpenMP는 병렬 처리 수준이 미리 결정되어 있고 시스템에서 사용 가능한 리소스와 일치할 때 가장 효율적입니다. OpenMP 모델은 매우 큰 계산 문제가 한 컴퓨터의 처리 리소스에서 분산 되는 고성능 컴퓨팅에 특히 적합 합니다. 이 시나리오에서는 하드웨어 환경이 일반적으로 수정 되며 개발자는 알고리즘이 실행 될 때 모든 컴퓨팅 리소스에 단독으로 액세스할 수 있을 것입니다.

그러나 제약이 없는 컴퓨팅 환경은 OpenMP와 일치 하지 않을 수 있습니다. 예를 들어 재귀 문제 (예: 빠른 정렬 알고리즘 또는 데이터 트리 검색)는 OpenMP 2.0 및 2.5을 사용 하 여 구현 하기가 더 어렵습니다. 동시성 런타임는 [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md) 및 PPL ( [병렬 패턴 라이브러리](../../parallel/concrt/parallel-patterns-library-ppl.md) )을 제공 하 여 OpenMP의 기능을 보완 합니다. 비동기 에이전트 라이브러리는 정교 하지 않은 작업 병렬 처리를 지원 합니다. PPL은 보다 세분화 된 병렬 작업을 지원 합니다. 동시성 런타임는 응용 프로그램의 논리에 집중할 수 있도록 작업을 병렬로 수행 하는 데 필요한 인프라를 제공 합니다. 그러나 동시성 런타임에서 다양 한 프로그래밍 모델을 사용할 수 있기 때문에 해당 예약 오버 헤드는 OpenMP와 같은 다른 동시성 라이브러리 보다 클 수 있습니다. 따라서 동시성 런타임 사용 하도록 기존 OpenMP 코드를 변환 하는 경우 성능을 점진적으로 테스트 하는 것이 좋습니다.

## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>OpenMP에서 동시성 런타임로 마이그레이션해야 하는 경우

다음 경우에 동시성 런타임를 사용 하도록 기존 OpenMP 코드를 마이그레이션하는 것이 유용할 수 있습니다.

|사례|동시성 런타임의 이점|
|-----------|-------------------------------------------|
|확장 가능한 동시 프로그래밍 프레임 워크가 필요 합니다.|동시성 런타임의 기능 중 다수는 확장 가능합니다. 기존 기능을 결합하여 새 기능을 구성할 수도 있습니다. OpenMP는 컴파일러 지시문에 의존 하므로 쉽게 확장할 수 없습니다.|
|응용 프로그램은 협조적 차단의 이점을 누릴 수 있습니다.|작업에서 아직 사용할 수 없는 리소스가 필요 하기 때문에 작업을 차단 하는 경우에는 첫 번째 태스크가 리소스를 기다리는 동안 다른 작업을 수행할 수 동시성 런타임.|
|응용 프로그램에서 동적 부하 분산을 활용 하는 것이 좋습니다.|동시성 런타임는 작업 변경에 따라 컴퓨팅 리소스의 할당을 조정 하는 일정 알고리즘을 사용 합니다. OpenMP에서 스케줄러가 병렬 지역에 컴퓨팅 리소스를 할당 하는 경우 이러한 리소스 할당은 계산 전체에서 고정 됩니다.|
|예외 처리를 지원 해야 합니다.|PPL을 사용 하면 병렬 영역 또는 루프의 내부 및 외부 모두에서 예외를 catch 할 수 있습니다. OpenMP에서는 병렬 영역 또는 루프 내에서 예외를 처리 해야 합니다.|
|취소 메커니즘이 필요 합니다.|PPL을 사용 하면 응용 프로그램에서 개별 작업과 작업의 병렬 트리를 모두 취소할 수 있습니다. OpenMP에서는 응용 프로그램이 자체 취소 메커니즘을 구현 해야 합니다.|
|병렬 코드가 시작 되는 다른 컨텍스트에서 완료 되어야 합니다.|동시성 런타임를 사용 하면 한 컨텍스트에서 작업을 시작한 다음 다른 컨텍스트에서 작업을 기다리거나 취소할 수 있습니다. OpenMP에서 모든 병렬 작업은 시작 되는 컨텍스트에서 완료 되어야 합니다.|
|향상 된 디버깅 지원이 필요 합니다.|Visual Studio는 다중 스레드 응용 프로그램을 더 쉽게 디버그할 수 있도록 **병렬 스택** 및 **병렬 작업** 창을 제공 합니다.<br /><br /> 동시성 런타임에 대 한 디버깅 지원에 대 한 자세한 내용은 [작업 창 사용](/visualstudio/debugger/using-the-tasks-window), [병렬 스택 창 사용](/visualstudio/debugger/using-the-parallel-stacks-window)및 [연습: 병렬 응용 프로그램 디버깅](/visualstudio/debugger/walkthrough-debugging-a-parallel-application)을 참조 하세요.|

## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>OpenMP에서 동시성 런타임로 마이그레이션하지 않는 경우

다음 경우 동시성 런타임를 사용 하도록 기존 OpenMP 코드를 마이그레이션하는 것이 적절 하지 않을 수 있는 경우를 설명 합니다.

|사례|설명|
|-----------|-----------------|
|응용 프로그램이 이미 요구 사항을 충족 합니다.|응용 프로그램 성능 및 현재 디버깅 지원에 만족 하는 경우 마이그레이션이 적절 하지 않을 수 있습니다.|
|병렬 루프 본문은 약간의 작업을 수행 합니다.|동시성 런타임 작업 scheduler의 오버 헤드로 인해 루프 본문을 병렬로 실행 하는 이점을 극복 하지 못할 수 있습니다. 특히 루프 본문이 비교적 작은 경우입니다.|
|응용 프로그램은 C로 작성 됩니다.|동시성 런타임는 많은 c + + 기능을 사용 하기 때문에 C 응용 프로그램에서이 기능을 완전히 사용할 수 있도록 하는 코드를 작성할 수 없는 경우에는 적합 하지 않을 수 있습니다.|

## <a name="related-topics"></a>관련 항목

[방법: 동시성 런타임 사용 하기 위해 OpenMP parallel for 루프 변환](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)

OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) 및 [for](../openmp/reference/openmp-directives.md#for-openmp) 지시문을 사용 하는 기본 루프를 고려 하 여 동시성 런타임 [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 알고리즘을 사용 하도록 변환 하는 방법을 보여 줍니다.

[방법: 취소를 사용 하 여 동시성 런타임 사용 하는 OpenMP 루프 변환](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)<br/>
모든 반복을 실행할 필요가 없는 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) 루프를 지정 하면 동시성 런타임 취소 메커니즘을 사용 하도록 변환 하는 방법을 보여 줍니다.

[방법: 예외 처리를 사용 하 여 동시성 런타임 사용 하는 OpenMP 루프 변환](../../parallel/concrt/convert-an-openmp-loop-that-uses-exception-handling.md)<br/>
예외 처리를 수행 하는 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) 루프를 지정 하는 경우 동시성 런타임 예외 처리 메커니즘을 사용 하도록 변환 하는 방법을 보여 줍니다.

[방법: 동시성 런타임를 사용 하기 위해 환산 변수를 사용 하는 OpenMP 루프 변환](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)<br/>
[Reduction](../openmp/reference/openmp-clauses.md#reduction) 절을 사용 하는 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) 루프를 지정 하는 경우 동시성 런타임 사용 하도록 변환 하는 방법을 보여 줍니다.

## <a name="see-also"></a>참고 항목

[동시성 런타임](../../parallel/concrt/concurrency-runtime.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)<br/>
[PPL(병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)
