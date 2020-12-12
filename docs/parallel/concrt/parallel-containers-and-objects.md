---
description: '자세한 정보: 병렬 컨테이너 및 개체'
title: 병렬 컨테이너 및 개체
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: 2d0b6b491fbe41ea74ad0e6c138cb270558f6e73
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172442"
---
# <a name="parallel-containers-and-objects"></a>병렬 컨테이너 및 개체

PPL (병렬 패턴 라이브러리)에는 해당 요소에 스레드로부터 안전한 액세스를 제공 하는 여러 컨테이너와 개체가 포함 되어 있습니다.

*동시 컨테이너* 는 가장 중요 한 작업에 대 한 동시성이 보장 된 액세스를 제공 합니다. 여기서는 동시성이 안전 함을 의미 하는 포인터가 나 반복기는 항상 유효 합니다. 요소 초기화 나 특정 트래버스 주문의 보장은 아닙니다. 이러한 컨테이너의 기능은 c + + 표준 라이브러리에서 제공 하는 것과 유사 합니다. 예를 들어 [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 클래스는 [std:: vector](../../standard-library/vector-class.md) 클래스와 유사 합니다. 단, `concurrent_vector` 클래스를 통해 요소를 병렬로 추가할 수 있습니다. 동일한 컨테이너에 대 한 읽기 및 쓰기 권한이 모두 필요한 병렬 코드를 사용 하는 경우 동시 컨테이너를 사용 합니다.

*동시 개체* 는 구성 요소 간에 동시에 공유 됩니다. 동시 개체의 상태를 병렬로 계산 하는 프로세스는 동일한 상태를 직렬로 계산 하는 다른 프로세스와 동일한 결과를 생성 합니다. [Concurrency:: 결합할](../../parallel/concrt/reference/combinable-class.md) 수 있는 클래스는 동시 개체 형식의 한 예입니다. `combinable`클래스를 사용 하 여 병렬로 계산을 수행한 다음 이러한 계산을 최종 결과로 결합할 수 있습니다. 뮤텍스와 같은 동기화 메커니즘을 사용 하 여 공유 변수 또는 리소스에 대 한 액세스를 동기화 하는 경우 동시 개체를 사용 합니다.

## <a name="sections"></a><a name="top"></a> 섹션이

이 항목에서는 다음과 같은 병렬 컨테이너 및 개체에 대해 자세히 설명 합니다.

동시 컨테이너:

- [concurrent_vector 클래스](#vector)

  - [Concurrent_vector와 vector의 차이점](#vector-differences)

  - [동시성이 안전 하 게 작동 하는 작업](#vector-safety)

  - [예외 안전성](#vector-exceptions)

- [concurrent_queue 클래스](#queue)

  - [Concurrent_queue와 큐의 차이점](#queue-differences)

  - [동시성이 안전 하 게 작동 하는 작업](#queue-safety)

  - [반복기 지원](#queue-iterators)

- [concurrent_unordered_map 클래스](#unordered_map)

  - [Concurrent_unordered_map와 unordered_map의 차이점](#map-differences)

  - [동시성이 안전 하 게 작동 하는 작업](#map-safety)

- [concurrent_unordered_multimap 클래스](#unordered_multimap)

- [concurrent_unordered_set 클래스](#unordered_set)

- [concurrent_unordered_multiset 클래스](#unordered_multiset)

동시 개체:

- [결합 가능한 클래스](#combinable)

  - [메서드 및 기능](#combinable-features)

  - [예제](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a> concurrent_vector 클래스

[Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 클래스는 [std:: vector](../../standard-library/vector-class.md) 클래스와 마찬가지로 요소에 임의로 액세스할 수 있도록 하는 시퀀스 컨테이너 클래스입니다. 클래스는 동시성이 보장 되는 `concurrent_vector` 추가 및 요소 액세스 작업을 가능 하 게 합니다. 추가 작업은 기존 포인터 또는 반복기를 무효화 하지 않습니다. 반복기 액세스 및 트래버스 작업도 동시성이 안전 합니다. 여기서는 동시성이 안전 함을 의미 하는 포인터가 나 반복기는 항상 유효 합니다. 요소 초기화 나 특정 트래버스 주문의 보장은 아닙니다.

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a> Concurrent_vector와 vector의 차이점

`concurrent_vector`클래스는 클래스와 유사 합니다 `vector` . 개체에 대 한 추가, 요소 액세스 및 반복기 액세스 작업의 복잡성은 `concurrent_vector` 개체의 경우와 동일 합니다 `vector` . 다음은가와 어떻게 다른 지를 보여 주는 점입니다 `concurrent_vector` `vector` .

- 개체에 대 한 추가, 요소 액세스, 반복기 액세스 및 반복기 순회 연산은 `concurrent_vector` 동시성이 보장 됩니다.

- 개체의 끝에만 요소를 추가할 수 있습니다 `concurrent_vector` . `concurrent_vector`클래스는 메서드를 제공 하지 않습니다 `insert` .

- 개체는 추가 하는 `concurrent_vector` 경우 [이동 의미 체계](../../cpp/rvalue-reference-declarator-amp-amp.md) 를 사용 하지 않습니다.

- `concurrent_vector`클래스는 또는 메서드를 제공 하지 않습니다 `erase` `pop_back` . 와 마찬가지로 `vector` [clear](reference/concurrent-vector-class.md#clear) 메서드를 사용 하 여 개체에서 모든 요소를 제거 `concurrent_vector` 합니다.

- `concurrent_vector`클래스는 요소를 메모리에 연속적으로 저장 하지 않습니다. 따라서 `concurrent_vector` 배열을 사용할 수 있는 방법으로는 클래스를 사용할 수 없습니다. 예를 들어 형식 이라는 변수의 경우 `v` `concurrent_vector` 식에서 `&v[0]+2` 정의 되지 않은 동작을 생성 합니다.

- `concurrent_vector`클래스는 [grow_by](reference/concurrent-vector-class.md#grow_by) 및 [grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least) 메서드를 정의 합니다. 이러한 메서드는 동시성이 안전 하다는 점을 제외 하 고 [resize](reference/concurrent-vector-class.md#resize) 메서드와 유사 합니다.

- `concurrent_vector`개체를 추가 하거나 크기를 조정 하는 경우 개체는 해당 요소의 위치를 다시 조정 하지 않습니다. 이렇게 하면 동시 작업 동안 기존 포인터 및 반복기가 유효한 상태로 유지 됩니다.

- 런타임은 형식에 대해의 특수화 된 버전을 정의 하지 않습니다 `concurrent_vector` **`bool`** .

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a> Concurrency-Safe 작업

개체의 크기를 추가 하거나 늘리거나 개체의 요소에 액세스 하는 모든 메서드는 `concurrent_vector` `concurrent_vector` 동시성이 안전 합니다. 여기서는 동시성이 안전 함을 의미 하는 포인터가 나 반복기는 항상 유효 합니다. 요소 초기화 나 특정 트래버스 주문의 보장은 아닙니다. 이 규칙의 예외는 `resize` 메서드입니다.

다음 표에서는 동시성이 보장 되는 일반적인 `concurrent_vector` 메서드 및 연산자를 보여 줍니다.

:::row:::
   :::column span="":::
      [`at`](reference/concurrent-vector-class.md#at)\
      [`back`](reference/concurrent-vector-class.md#back)\
      [`begin`](reference/concurrent-vector-class.md#begin)\
      [`capacity`](reference/concurrent-vector-class.md#capacity)
   :::column-end:::
   :::column span="":::
      [`empty`](reference/concurrent-vector-class.md#empty)\
      [`end`](reference/concurrent-vector-class.md#end)\
      [`front`](reference/concurrent-vector-class.md#front)\
      [`grow_by`](reference/concurrent-vector-class.md#grow_by)
   :::column-end:::
   :::column span="":::
      [`grow_to_at_least`](reference/concurrent-vector-class.md#grow_to_at_least)\
      [`max_size`](reference/concurrent-vector-class.md#max_size)\
      [`operator[]`](reference/concurrent-vector-class.md#operator_at)\
      [`push_back`](reference/concurrent-vector-class.md#push_back)
   :::column-end:::
   :::column span="":::
      [`rbegin`](reference/concurrent-vector-class.md#rbegin)\
      [`rend`](reference/concurrent-vector-class.md#rend)\
      [`size`](reference/concurrent-vector-class.md#size)
   :::column-end:::
:::row-end:::

런타임에서 c + + 표준 라이브러리와의 호환성을 위해 제공 하는 작업 (예:) `reserve` 은 동시성이 안전 하지 않습니다. 다음 표에서는 동시성이 보장 되지 않는 일반적인 메서드 및 연산자를 보여 줍니다.

:::row:::
   :::column span="":::
      [`assign`](reference/concurrent-vector-class.md#assign)\
      [`clear`](reference/concurrent-vector-class.md#clear)
   :::column-end:::
   :::column span="":::
      [`operator=`](reference/concurrent-vector-class.md#operator_eq)\
      [`reserve`](reference/concurrent-vector-class.md#reserve)
   :::column-end:::
   :::column span="":::
      [`resize`](reference/concurrent-vector-class.md#resize)
   :::column-end:::
   :::column span="":::
      [`shrink_to_fit`](reference/concurrent-vector-class.md#shrink_to_fit)
   :::column-end:::
:::row-end:::

기존 요소의 값을 수정 하는 연산은 동시성이 안전 하지 않습니다. [Reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 개체와 같은 동기화 개체를 사용 하 여 동일한 데이터 요소에 대 한 동시 읽기 및 쓰기 작업을 동기화 합니다. 동기화 개체에 대 한 자세한 내용은 [동기화 데이터 구조](../../parallel/concrt/synchronization-data-structures.md)를 참조 하세요.

에서 사용 하는 기존 코드를 변환 하는 경우 `vector` `concurrent_vector` 동시 작업으로 인해 응용 프로그램의 동작이 변경 될 수 있습니다. 예를 들어, 개체에서 두 개의 작업을 동시에 수행 하는 다음 프로그램이 있다고 가정 합니다 `concurrent_vector` . 첫 번째 작업은 개체에 추가 요소를 추가 합니다 `concurrent_vector` . 두 번째 태스크는 동일한 개체에 있는 모든 요소의 합계를 계산 합니다.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

메서드는 `end` 동시성이 안전 하지만 [push_back](reference/concurrent-vector-class.md#push_back) 메서드에 대 한 동시 호출로 인해에서 반환 하는 값이 `end` 변경 됩니다. 반복기가 트래버스하는 요소 수는 결정 되지 않습니다. 따라서이 프로그램은 실행 될 때마다 다른 결과를 생성할 수 있습니다. 요소 형식이 trivial이 아닌 경우 및 호출 사이에 경합 상태가 있을 수 `push_back` `end` 있습니다. `end`메서드는 할당 되었지만 완전히 초기화 되지 않은 요소를 반환할 수 있습니다.

### <a name="exception-safety"></a><a name="vector-exceptions"></a> 예외 안전성

증가 또는 할당 작업에서 예외를 throw 하는 경우 개체의 상태가 `concurrent_vector` 유효 하지 않게 됩니다. 달리 지정 되지 `concurrent_vector` 않은 경우 잘못 된 상태의 개체 동작은 정의 되지 않습니다. 그러나 개체의 상태가 잘못 된 경우에도 소멸자는 항상 개체가 할당 하는 메모리를 해제 합니다.

벡터 요소의 데이터 형식인는 `T` 다음 요구 사항을 충족 해야 합니다. 그렇지 않으면 클래스의 동작이 `concurrent_vector` 정의 되지 않습니다.

- 소멸자는를 throw 해서는 안 됩니다.

- 기본 생성자 또는 복사 생성자가를 throw 하는 경우 소멸자는 키워드를 사용 하 여 선언 되지 않아야 하며, 초기화 되지 않은 메모리를 사용 하 여 **`virtual`** 제대로 작동 해야 합니다.

[[맨 위로](#top)이동]

## <a name="concurrent_queue-class"></a><a name="queue"></a> concurrent_queue 클래스

[Std:: queue](../../standard-library/queue-class.md) 클래스와 마찬가지로 [concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) 클래스를 사용 하 여 front 및 back 요소에 액세스할 수 있습니다. 클래스는 동시성이 보장 되는 큐에 넣기 `concurrent_queue` 및 큐에서 제거 작업을 가능 하 게 합니다. 여기서는 동시성이 안전 함을 의미 하는 포인터가 나 반복기는 항상 유효 합니다. 요소 초기화 나 특정 트래버스 주문의 보장은 아닙니다. `concurrent_queue`또한 클래스는 동시성이 안전 하지 않은 반복기 지원도 제공 합니다.

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a> Concurrent_queue와 큐의 차이점

`concurrent_queue`클래스는 클래스와 유사 합니다 `queue` . 다음은가와 어떻게 다른 지를 보여 주는 점입니다 `concurrent_queue` `queue` .

- 개체에 대 한 큐에 넣기 및 큐에서 제거 작업 `concurrent_queue` 은 동시성이 보장 됩니다.

- `concurrent_queue`클래스는 동시성이 안전 하지 않은 반복기 지원을 제공 합니다.

- `concurrent_queue`클래스는 또는 메서드를 제공 하지 않습니다 `front` `pop` . `concurrent_queue`클래스는 [try_pop](reference/concurrent-queue-class.md#try_pop) 메서드를 정의 하 여 이러한 메서드를 대체 합니다.

- `concurrent_queue`클래스는 메서드를 제공 하지 않습니다 `back` . 따라서 큐의 끝을 참조할 수 없습니다.

- `concurrent_queue`클래스는 메서드 대신 [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) 메서드를 제공 합니다 `size` . `unsafe_size`메서드는 동시성이 보장 되지 않습니다.

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a> Concurrency-Safe 작업

개체에서 큐에 넣기 또는 큐에서 제거 하는 모든 메서드 `concurrent_queue` 는 동시성이 보장 됩니다. 여기서는 동시성이 안전 함을 의미 하는 포인터가 나 반복기는 항상 유효 합니다. 요소 초기화 나 특정 트래버스 주문의 보장은 아닙니다.

다음 표에서는 동시성이 보장 되는 일반적인 `concurrent_queue` 메서드 및 연산자를 보여 줍니다.

:::row:::
   :::column span="":::
      [`empty`](reference/concurrent-queue-class.md#empty)
   :::column-end:::
   :::column span="":::
      [`get_allocator`](reference/concurrent-queue-class.md#get_allocator)
   :::column-end:::
   :::column span="":::
      [`push`](reference/concurrent-queue-class.md#push)
   :::column-end:::
   :::column span="":::
      [`try_pop`](reference/concurrent-queue-class.md#try_pop)
   :::column-end:::
:::row-end:::

메서드는 `empty` 동시성이 안전 하지만, 동시 작업을 수행 하면 메서드가 반환 되기 전에 큐가 늘어나거나 줄어들 수 있습니다 `empty` .

다음 표에서는 동시성이 보장 되지 않는 일반적인 메서드 및 연산자를 보여 줍니다.

:::row:::
   :::column span="":::
      [`clear`](reference/concurrent-queue-class.md#clear)
   :::column-end:::
   :::column span="":::
      [`unsafe_begin`](reference/concurrent-queue-class.md#unsafe_begin)
   :::column-end:::
   :::column span="":::
      [`unsafe_end`](reference/concurrent-queue-class.md#unsafe_end)
   :::column-end:::
   :::column span="":::
      [`unsafe_size`](reference/concurrent-queue-class.md#unsafe_size)
   :::column-end:::
:::row-end:::

### <a name="iterator-support"></a><a name="queue-iterators"></a> 반복기 지원

는 `concurrent_queue` 동시성이 안전 하지 않은 반복기를 제공 합니다. 디버깅에만 이러한 반복기를 사용 하는 것이 좋습니다.

`concurrent_queue`반복기는 정방향 방향 으로만 요소를 트래버스 합니다. 다음 표에서는 각 반복기가 지 원하는 연산자를 보여 줍니다.

|연산자|설명|
|--------------|-----------------|
|`operator++`|큐에서 다음 항목으로 이동 합니다. 이 연산자는 오버 로드 된 후 위 의미 체계를 모두 제공 하도록 오버 로드 됩니다.|
|`operator*`|현재 항목에 대 한 참조를 검색 합니다.|
|`operator->`|현재 항목에 대 한 포인터를 검색 합니다.|

\[[위쪽](#top)]

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a> concurrent_unordered_map 클래스

[Concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) 클래스는 [std:: unordered_map](../../standard-library/unordered-map-class.md) 클래스와 마찬가지로 [std::p air \<const Key, Ty> ](../../standard-library/pair-structure.md)형식의 요소에 대 한 다양 한 길이의 요소 시퀀스를 제어 하는 결합형 컨테이너 클래스입니다. 순서가 지정 되지 않은 지도는 키와 값 쌍을 추가 하거나 키로 값을 조회할 수 있는 사전으로 생각 하면 됩니다. 이 클래스는 공유 컨테이너에 동시에 액세스 하거나,이를 삽입 하거나, 업데이트 해야 하는 여러 스레드나 태스크가 있는 경우에 유용 합니다.

다음 예에서는를 사용 하기 위한 기본 구조를 보여 줍니다 `concurrent_unordered_map` . 이 예에서는 [' a ', ' i '] 범위의 문자 키를 삽입 합니다. 작업 순서는 결정 되지 않으므로 각 키의 최종 값도 결정 되지 않습니다. 그러나 동시에 삽입을 수행 하는 것이 안전 합니다.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

를 사용 하 여 `concurrent_unordered_map` 맵을 수행 하 고 작업을 병렬로 줄이기 위해를 사용 하는 예제는 [방법: 매핑 수행 및 병렬 작업 줄이기](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)를 참조 하세요.

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a> Concurrent_unordered_map와 unordered_map의 차이점

`concurrent_unordered_map`클래스는 클래스와 유사 합니다 `unordered_map` . 다음은가와 어떻게 다른 지를 보여 주는 점입니다 `concurrent_unordered_map` `unordered_map` .

- ,, 및 `erase` `bucket` `bucket_count` `bucket_size` 메서드의 이름은 `unsafe_erase` 각각,, `unsafe_bucket` `unsafe_bucket_count` 및 `unsafe_bucket_size` 입니다. `unsafe_`명명 규칙은 이러한 메서드가 동시성이 안전 하지 않음을 나타냅니다. 동시성 안전성에 대 한 자세한 내용은 [동시성 안전 작업](#map-safety)을 참조 하세요.

- 삽입 작업은 기존 포인터 또는 반복기를 무효화 하지 않으며 맵에 이미 존재 하는 항목의 순서를 변경 하지도 않습니다. 삽입 및 트래버스 작업은 동시에 발생할 수 있습니다.

- `concurrent_unordered_map` 는 전방 반복만 지원 합니다.

- 삽입은에서 반환 하는 반복기를 무효화 하거나 업데이트 하지 않습니다 `equal_range` . 삽입은 범위의 끝에 같지 않은 항목을 추가할 수 있습니다. Begin iterator는 동일한 항목을 가리킵니다.

교착 상태를 방지 하기 위해의 메서드는 `concurrent_unordered_map` 메모리 할당자, 해시 함수 또는 기타 사용자 정의 코드를 호출할 때 잠금을 보유 하지 않습니다. 또한 해시 함수는 항상 동일한 키를 동일한 값으로 평가 하는지 확인 해야 합니다. 최상의 해시 함수는 해시 코드 공간에서 키를 균일 하 게 분산 합니다.

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a> Concurrency-Safe 작업

클래스는 동시성이 보장 되는 `concurrent_unordered_map` 삽입 및 요소 액세스 작업을 가능 하 게 합니다. 삽입 작업은 기존 포인터 또는 반복기를 무효화 하지 않습니다. 반복기 액세스 및 트래버스 작업도 동시성이 안전 합니다. 여기서는 동시성이 안전 함을 의미 하는 포인터가 나 반복기는 항상 유효 합니다. 요소 초기화 나 특정 트래버스 주문의 보장은 아닙니다. 다음 표에서는 동시성이 보장 되는 일반적으로 사용 되는 `concurrent_unordered_map` 메서드 및 연산자를 보여 줍니다.

:::row:::
   :::column span="":::
      [`at`](reference/concurrent-unordered-map-class.md#at)\
      [`begin`](reference/concurrent-unordered-map-class.md#begin)\
      [`cbegin`](reference/concurrent-unordered-map-class.md#cbegin)\
      [`cend`](reference/concurrent-unordered-map-class.md#cend)
   :::column-end:::
   :::column span="":::
      [`count`](reference/concurrent-unordered-map-class.md#count)\
      [`empty`](reference/concurrent-unordered-map-class.md#empty)\
      [`end`](reference/concurrent-unordered-map-class.md#cend)\
      [`equal_range`](reference/concurrent-unordered-map-class.md#equal_range)
   :::column-end:::
   :::column span="":::
      [`find`](reference/concurrent-unordered-map-class.md#find)\
      [`get_allocator`](reference/concurrent-unordered-map-class.md#get_allocator)\
      [`hash_function`](reference/concurrent-unordered-map-class.md#hash_function)\
      [`insert`](reference/concurrent-unordered-map-class.md#insert)
   :::column-end:::
   :::column span="":::
      [`key_eq`](reference/concurrent-unordered-map-class.md#key_eq)\
      [`max_size`](reference/concurrent-unordered-map-class.md#max_size)\
      [`operator[]`](./reference/concurrent-unordered-map-class.md#operator_at)\
      [`size`](reference/concurrent-unordered-map-class.md#size)
   :::column-end:::
:::row-end:::

동시에 `count` 실행 되는 스레드에서 메서드를 안전 하 게 호출할 수 있지만 새 값이 컨테이너에 동시에 삽입 되는 경우 다른 스레드가 다른 결과를 받을 수 있습니다.

다음 표에서는 동시성이 보장 되지 않는 일반적으로 사용 되는 메서드 및 연산자를 보여 줍니다.

:::row:::
   :::column span="":::
      [`clear`](reference/concurrent-unordered-map-class.md#clear)\
      [`load_factor`](reference/concurrent-unordered-map-class.md#load_factor)
   :::column-end:::
   :::column span="":::
      [`max_load_factor`](reference/concurrent-unordered-map-class.md#max_load_factor)
   :::column-end:::
   :::column span="":::
      [`operator=`](reference/concurrent-unordered-map-class.md#operator_eq)
   :::column-end:::
   :::column span="":::
      [`rehash`](reference/concurrent-unordered-map-class.md#rehash)
   :::column-end:::
:::row-end:::

이러한 메서드 외에도로 시작 하는 모든 메서드 `unsafe_` 는 동시성이 안전 하지 않습니다.

[[맨 위로](#top)이동]

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a> concurrent_unordered_multimap 클래스

[Concurrency:: concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) 클래스는 `concurrent_unordered_map` 여러 값이 동일한 키에 매핑되도록 허용 한다는 점을 제외 하 고 클래스와 매우 비슷합니다. 또한 다음과 같은 점에서와 다릅니다 `concurrent_unordered_map` .

- [Concurrent_unordered_multimap:: insert](reference/concurrent-unordered-multimap-class.md#insert) 메서드는 대신 반복기를 반환 합니다 `std::pair<iterator, bool>` .

- `concurrent_unordered_multimap`클래스는 `operator[]` 및 메서드를 제공 하지 않습니다 `at` .

다음 예에서는를 사용 하기 위한 기본 구조를 보여 줍니다 `concurrent_unordered_multimap` . 이 예에서는 [' a ', ' i '] 범위의 문자 키를 삽입 합니다. `concurrent_unordered_multimap` 키에 여러 값을 사용할 수 있습니다.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[맨 위로](#top)이동]

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a> concurrent_unordered_set 클래스

[Concurrency:: concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) 클래스는 `concurrent_unordered_map` 키 및 값 쌍 대신 값을 관리 한다는 점을 제외 하 고 클래스와 매우 비슷합니다. `concurrent_unordered_set`클래스는 `operator[]` 및 메서드를 제공 하지 않습니다 `at` .

다음 예에서는를 사용 하기 위한 기본 구조를 보여 줍니다 `concurrent_unordered_set` . 이 예에서는 [' a ', ' i '] 범위의 문자 값을 삽입 합니다. 삽입을 병렬로 수행 하는 것이 안전 합니다.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[맨 위로](#top)이동]

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a> concurrent_unordered_multiset 클래스

[Concurrency:: concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) 클래스는 `concurrent_unordered_set` 중복 값을 허용 한다는 점을 제외 하 고 클래스와 유사 합니다. 또한 다음과 같은 점에서와 다릅니다 `concurrent_unordered_set` .

- [Concurrent_unordered_multiset:: insert](reference/concurrent-unordered-multiset-class.md#insert) 메서드는 대신 반복기를 반환 합니다 `std::pair<iterator, bool>` .

- `concurrent_unordered_multiset`클래스는 `operator[]` 및 메서드를 제공 하지 않습니다 `at` .

다음 예에서는를 사용 하기 위한 기본 구조를 보여 줍니다 `concurrent_unordered_multiset` . 이 예에서는 [' a ', ' i '] 범위의 문자 값을 삽입 합니다. `concurrent_unordered_multiset` 값을 여러 번 사용할 수 있도록 합니다.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[맨 위로](#top)이동]

## <a name="combinable-class"></a><a name="combinable"></a> 결합 가능한 클래스

[Concurrency:: 결합할](../../parallel/concrt/reference/combinable-class.md) 수 있는 클래스는 세분화 된 계산을 수행한 다음 이러한 계산을 최종 결과로 병합할 수 있는 재사용 가능한 스레드 로컬 저장소를 제공 합니다. `combinable` 개체는 환산(reduction) 변수로 간주될 수 있습니다.

`combinable`클래스는 여러 스레드나 작업 간에 공유 되는 리소스가 있는 경우에 유용 합니다. `combinable`클래스를 사용 하면 잠금 없는 방식으로 공유 리소스에 대 한 액세스를 제공 하 여 공유 상태를 제거할 수 있습니다. 따라서이 클래스는 뮤텍스와 같은 동기화 메커니즘을 사용 하 여 여러 스레드의 공유 데이터에 대 한 액세스를 동기화 하는 대신 사용할 수 있는 방법을 제공 합니다.

### <a name="methods-and-features"></a><a name="combinable-features"></a> 메서드 및 기능

다음 표에서는 클래스의 몇 가지 중요 한 메서드를 보여 줍니다 `combinable` . 모든 클래스 메서드에 대 한 자세한 내용은 `combinable` [결합 가능한 클래스](../../parallel/concrt/reference/combinable-class.md)를 참조 하세요.

|메서드|설명|
|------------|-----------------|
|[로컬](reference/combinable-class.md#local)|현재 스레드 컨텍스트와 연결 된 지역 변수에 대 한 참조를 검색 합니다.|
|[clear](reference/combinable-class.md#clear)|개체에서 모든 스레드 지역 변수를 제거 합니다 `combinable` .|
|[결합](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|제공 된 combine 함수를 사용 하 여 모든 스레드 로컬 계산 집합에서 최종 값을 생성 합니다.|

`combinable`클래스는 병합 된 최종 결과에 매개 변수화 된 템플릿 클래스입니다. 기본 생성자를 호출 하는 경우 `T` 템플릿 매개 변수 형식에는 기본 생성자와 복사 생성자가 있어야 합니다. `T`템플릿 매개 변수 형식에 기본 생성자가 없는 경우 초기화 함수를 매개 변수로 사용 하는 생성자의 오버 로드 된 버전을 호출 합니다.

`combinable` [Combine](reference/combinable-class.md#combine) 또는 [combine_each](reference/combinable-class.md#combine_each) 메서드를 호출한 후에는 개체에 추가 데이터를 저장할 수 있습니다. `combine`및 메서드를 여러 번 호출할 수도 있습니다 `combine_each` . 개체에 로컬 값이 변경 되지 않은 경우 `combinable` `combine` 및 `combine_each` 메서드는 호출 될 때마다 동일한 결과를 생성 합니다.

### <a name="examples"></a><a name="combinable-examples"></a> 예

클래스를 사용 하는 방법에 대 한 예제는 `combinable` 다음 항목을 참조 하세요.

- [방법: 결합을 사용 하 여 성능 향상](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [방법: 조합 하 여 집합 결합](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[맨 위로](#top)이동]

## <a name="related-topics"></a>관련 항목

[방법: 병렬 컨테이너를 사용 하 여 효율성 향상](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
병렬 컨테이너를 사용 하 여 효율적으로 데이터를 효율적으로 저장 하 고 액세스 하는 방법을 보여 줍니다.

[방법: 결합을 사용 하 여 성능 향상](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
클래스를 사용 하 여 `combinable` 공유 상태를 제거 하 여 성능을 향상 시키는 방법을 보여 줍니다.

[방법: 조합 하 여 집합 결합](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
함수를 사용 하 여 `combine` 스레드 로컬 데이터 집합을 병합 하는 방법을 보여 줍니다.

[PPL(병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
동시 응용 프로그램을 개발 하기 위한 확장성과 사용 편의성을 향상 시키는 명령형 프로그래밍 모델을 제공 하는 PPL에 대해 설명 합니다.

## <a name="reference"></a>참조

[concurrent_vector 클래스](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue 클래스](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map 클래스](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap 클래스](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set 클래스](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset 클래스](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[결합 가능한 클래스](../../parallel/concrt/reference/combinable-class.md)
