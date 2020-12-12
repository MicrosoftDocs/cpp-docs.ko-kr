---
description: '자세한 정보: PPL (병렬 패턴 라이브러리)'
title: PPL(병렬 패턴 라이브러리)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library (PPL)
ms.assetid: 40fd86b2-69fa-45e5-93d8-98a75636c242
ms.openlocfilehash: ea5719e8ebaacf8f181678ef7af8aae9c900fbe6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172351"
---
# <a name="parallel-patterns-library-ppl"></a>PPL(병렬 패턴 라이브러리)

PPL(병렬 패턴 라이브러리)은 여러 애플리케이션을 동시에 개발할 수 있도록 편의성과 확장성을 높이는 명령적 프로그래밍 모델을 제공합니다. PPL은 동시성 런타임의 예약 및 리소스 관리 구성 요소를 기반으로 빌드됩니다. 또한 데이터에 대해 병렬로 작동하는 형식이 안전한 일반 알고리즘과 컨테이너를 제공함으로써 애플리케이션 코드와 기본 스레딩 메커니즘 간의 추상화 수준을 높입니다. 또한 PPL을 사용하면 공유 상태 대신 사용할 수 있는 옵션을 제공하여 확장 가능한 애플리케이션을 개발할 수 있습니다.

PPL은 다음과 같은 기능을 제공합니다.

- *작업 병렬 처리*: 여러 작업 항목 (작업)을 병렬로 실행 하기 위해 Windows ThreadPool 위에서 작동 하는 메커니즘입니다.

- *병렬 알고리즘*: 데이터 컬렉션에 대해 병렬로 작동 하는 동시성 런타임을 기반으로 하는 일반 알고리즘

- *병렬 컨테이너 및 개체*: 해당 요소에 대 한 안전한 동시 액세스를 제공 하는 제네릭 컨테이너 형식

## <a name="example"></a>예제

PPL은 c + + 표준 라이브러리와 유사한 프로그래밍 모델을 제공 합니다. 다음 예제에서는 PPL의 여러 기능을 보여 줍니다. 이 예제에서는 여러 피보나치 수를 직렬 및 병렬로 계산합니다. 두 계산은 모두 [std:: array](../../standard-library/array-class-stl.md) 개체에서 작동 합니다. 또한 이 예제에서는 두 계산을 모두 수행하는 데 필요한 시간을 콘솔에 출력합니다.

직렬 버전은 c + + 표준 라이브러리 [std:: for_each](../../standard-library/algorithm-functions.md#for_each) 알고리즘을 사용 하 여 배열을 트래버스 하 고 결과를 [std:: vector](../../standard-library/vector-class.md) 개체에 저장 합니다. 병렬 버전은 동일한 작업을 수행 하지만 PPL [동시성::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 알고리즘을 사용 하 여 결과를 [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 개체에 저장 합니다. `concurrent_vector` 클래스를 사용하면 컨테이너에 대한 쓰기 권한을 동기화하지 않아도 각 루프 반복이 요소를 동시에 추가할 수 있습니다.

`parallel_for_each`는 동시에 동작하므로 이 예제의 병렬 버전은 직렬 버전과 같은 결과를 생성하기 위해 `concurrent_vector` 개체를 정렬해야 합니다.

예제에서는 간단한 메서드를 사용하여 피보나치 수를 계산합니다. 그러나 이 방법은 동시성 런타임을 통해 긴 컴퓨팅의 성능을 개선하는 방법을 보여 줍니다.

[!code-cpp[concrt-parallel-fibonacci#1](../../parallel/concrt/codesnippet/cpp/parallel-patterns-library-ppl_1.cpp)]

프로세서가 4개인 컴퓨터의 샘플 출력은 다음과 같습니다.

```Output
serial time: 9250 ms
parallel time: 5726 ms

fib(24): 46368
fib(26): 121393
fib(41): 165580141
fib(42): 267914296
```

루프의 각 반복을 완료하는 데 필요한 시간은 서로 다릅니다. `parallel_for_each`의 성능은 마지막으로 완료되는 작업에 의해 제한됩니다. 따라서 이 예제의 직렬 버전과 병렬 버전에서 성능이 일정하게 개선된다고 기대해서는 안 됩니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|PPL의 작업 및 작업 그룹 역할에 대해 설명합니다.|
|[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)|`parallel_for` 및 `parallel_for_each`와 같은 병렬 알고리즘을 사용하는 방법에 대해 설명합니다.|
|[병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)|PPL에서 제공하는 여러 병렬 컨테이너 및 개체에 대해 설명합니다.|
|[PPL에서의 취소](cancellation-in-the-ppl.md)|병렬 알고리즘에서 수행 중인 작업을 취소하는 방법을 설명합니다.|
|[동시성 런타임](../../parallel/concrt/concurrency-runtime.md)|병렬 프로그래밍을 간소화하는 동시성 런타임에 대해 설명하고 관련 항목의 링크를 제공합니다.|
