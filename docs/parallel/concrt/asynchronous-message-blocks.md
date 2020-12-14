---
description: '자세한 정보: 비동기 메시지 블록'
title: 비동기 메시지 블록
ms.date: 11/04/2016
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
ms.openlocfilehash: 7447d30932693eebe22d0a6f7f0aad0fba2abf16
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189147"
---
# <a name="asynchronous-message-blocks"></a>비동기 메시지 블록

에이전트 라이브러리는 여러 메시지 블록 형식을 제공 하 여 스레드로부터 안전한 방식으로 응용 프로그램 구성 요소 간에 메시지를 전파할 수 있습니다. 이러한 메시지 블록 형식은 [동시성:: send](reference/concurrency-namespace-functions.md#send), [concurrency:: asend](reference/concurrency-namespace-functions.md#asend), [concurrency:: receive](reference/concurrency-namespace-functions.md#receive)및 [concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive)와 같은 다양 한 메시지 전달 루틴에서 주로 사용 됩니다. 에이전트 라이브러리에 의해 정의 되는 메시지 전달 루틴에 대 한 자세한 내용은 [메시지 전달 함수](../../parallel/concrt/message-passing-functions.md)를 참조 하세요.

## <a name="sections"></a><a name="top"></a> 섹션이

이 항목에는 다음과 같은 단원이 포함되어 있습니다.

- [소스 및 대상](#sources_and_targets)

- [메시지 전파](#propagation)

- [메시지 블록 형식 개요](#overview)

- [unbounded_buffer 클래스](#unbounded_buffer)

- [overwrite_buffer 클래스](#overwrite_buffer)

- [single_assignment 클래스](#single_assignment)

- [call 클래스](#call)

- [변환기 클래스](#transformer)

- [choice 클래스](#choice)

- [조인 및 multitype_join 클래스](#join)

- [timer 클래스](#timer)

- [메시지 필터링](#filtering)

- [메시지 예약](#reservation)

## <a name="sources-and-targets"></a><a name="sources_and_targets"></a> 원본 및 대상

원본 및 대상은 메시지 전달 시 중요 한 두 참가자입니다. *소스* 는 메시지를 보내는 통신의 끝점을 참조 합니다. *대상은* 메시지를 수신 하는 통신의 끝점을 참조 합니다. 소스를에서 읽은 끝점으로 간주 하 고 대상을에 작성 하는 끝점으로 간주할 수 있습니다. 응용 프로그램은 원본 및 대상을 함께 연결 하 여 *메시징 네트워크* 를 형성 합니다.

에이전트 라이브러리는 두 개의 추상 클래스를 사용 하 여 소스 및 대상을 나타냅니다. [concurrency:: ISource](../../parallel/concrt/reference/isource-class.md) 및 [Concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md). 소스로 작동 하는 메시지 블록 형식은에서 파생 되며 `ISource` 대상으로 작동 하는 메시지 블록 형식은에서 파생 `ITarget` 됩니다. 소스 및 대상 역할을 하는 메시지 블록 형식은와 모두에서 파생 `ISource` `ITarget` 됩니다.

[[맨 위로](#top)이동]

## <a name="message-propagation"></a><a name="propagation"></a> 메시지 전파

*메시지 전파* 는 한 구성 요소에서 다른 구성 요소로 메시지를 전송 하는 동작입니다. 메시지 블록에 메시지가 제공 되 면 해당 메시지를 수락, 거부 또는 연기할 수 있습니다. 모든 메시지 블록 형식은 다양 한 방법으로 메시지를 저장 하 고 전송 합니다. 예를 들어, `unbounded_buffer` 클래스는 무제한의 메시지를 저장 하 고, 클래스는 한 `overwrite_buffer` 번에 하나의 메시지를 저장 하며, 변환기 클래스는 각 메시지의 변경 된 버전을 저장 합니다. 이러한 메시지 블록 형식은이 문서의 뒷부분에서 자세히 설명 합니다.

메시지 블록이 메시지를 수락 하는 경우 선택적으로 작업을 수행 하 고, 메시지 블록이 원본인 경우 결과 메시지를 네트워크의 다른 구성원에 게 전달 합니다. 메시지 블록은 필터 함수를 사용 하 여 수신 하지 않으려는 메시지를 거부할 수 있습니다. 필터는이 항목의 뒷부분에 있는 [메시지 필터링](#filtering)섹션에서 자세히 설명 합니다. 메시지를 연기 하는 메시지 블록은 메시지를 예약 하 고 나중에 사용할 수 있습니다. 메시지 예약은이 항목의 뒷부분에 있는 [메시지 예약](#reservation)섹션에서 자세히 설명 합니다.

에이전트 라이브러리를 사용 하면 메시지 블록에서 메시지를 비동기적으로 또는 동기적으로 전달할 수 있습니다. 예를 들어 함수를 사용 하 여 메시지 블록에 메시지를 동기적으로 전달 하는 경우 `send` 런타임에서는 대상 블록이 메시지를 수락 하거나 거부할 때까지 현재 컨텍스트를 차단 합니다. 예를 들어 함수를 사용 하 여 메시지 블록에 메시지를 비동기적으로 전달 하는 경우 `asend` 런타임에서는 대상에 메시지를 제공 하 고 대상이 메시지를 수락 하는 경우 런타임은 메시지를 받는 사람에 게 전파 하는 비동기 작업을 예약 합니다. 런타임은 간단한 작업을 사용 하 여 협조적 방식으로 메시지를 전파 합니다. 간단한 작업에 대 한 자세한 내용은 [작업 스케줄러](../../parallel/concrt/task-scheduler-concurrency-runtime.md)를 참조 하세요.

응용 프로그램은 원본 및 대상을 함께 연결 하 여 메시징 네트워크를 형성 합니다. 일반적으로 네트워크를 연결 하 고 `send` 또는 `asend` 를 호출 하 여 네트워크에 데이터를 전달 합니다. 소스 메시지 블록을 대상에 연결 하려면 [concurrency:: ISource:: link_target](reference/isource-class.md#link_target) 메서드를 호출 합니다. 대상에서 소스 블록의 연결을 끊으려면 [concurrency:: ISource:: unlink_target](reference/isource-class.md#unlink_target) 메서드를 호출 합니다. 모든 대상에서 소스 블록의 연결을 끊으려면 [concurrency:: ISource:: unlink_targets](reference/isource-class.md#unlink_targets) 메서드를 호출 합니다. 미리 정의 된 메시지 블록 형식 중 하나가 범위를 벗어나거나 소멸 되 면 모든 대상 블록에서 자동으로 연결을 끊습니다. 일부 메시지 블록 형식은 쓸 수 있는 대상의 최대 수를 제한 합니다. 다음 섹션에서는 미리 정의 된 메시지 블록 형식에 적용 되는 제한 사항에 대해 설명 합니다.

[[맨 위로](#top)이동]

## <a name="overview-of-message-block-types"></a><a name="overview"></a> 메시지 블록 형식 개요

다음 표에서는 중요 한 메시지 블록 형식의 역할에 대해 간략하게 설명 합니다.

[unbounded_buffer](#unbounded_buffer)<br/>
메시지 큐를 저장 합니다.

[overwrite_buffer](#overwrite_buffer)<br/>
여러 번 읽고 쓸 수 있는 메시지 하나를 저장 합니다.

[single_assignment](#single_assignment)<br/>
한 번에 쓸 수 있고 여러 번 읽을 수 있는 메시지 하나를 저장 합니다.

[call](#call)<br/>
메시지를 받을 때 작업을 수행 합니다.

[가](#transformer)<br/>
는 데이터를 받을 때 작업을 수행 하 고 해당 작업의 결과를 다른 대상 블록으로 보냅니다. `transformer`클래스는 다양 한 입력 및 출력 형식에 대해 작동할 수 있습니다.

[choice](#choice)<br/>
원본 집합에서 사용 가능한 첫 번째 메시지를 선택 합니다.

[join 및 다중 형식 join](#join)<br/>
원본 집합에서 모든 메시지가 수신 될 때까지 기다린 다음 메시지를 다른 메시지 블록에 대 한 하나의 메시지로 결합 합니다.

[시간이](#timer)<br/>
는 일정 한 간격으로 대상 블록에 메시지를 보냅니다.

이러한 메시지 블록 형식은 다양 한 상황에서 유용 하 게 사용할 수 있는 다양 한 특성을 가집니다. 이러한 특성은 다음과 같습니다.

- *전파 유형*: 메시지 블록이 데이터 원본, 데이터의 수신자 또는 둘 다의 역할을 하는지 여부입니다.

- *메시지 순서*: 메시지 블록에서 메시지를 보내거나 받는 원래 순서를 유지할지 여부를 지정 합니다. 미리 정의 된 각 메시지 블록 형식은 메시지를 보내거나 받는 원래 순서를 유지 합니다.

- *소스 수*: 메시지 블록에서 읽을 수 있는 최대 소스 수입니다.

- *대상 개수*: 메시지 블록이 쓸 수 있는 최대 대상 수입니다.

다음 표에서는 이러한 특성이 다양 한 메시지 블록 형식과 어떻게 관련 되는지를 보여 줍니다.

|메시지 블록 형식|전파 유형 (원본, 대상 또는 둘 다)|메시지 순서 지정 (정렬 또는 정렬 되지 않음)|원본 수|대상 개수|
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|
|`unbounded_buffer`|모두|주문됨|Unbounded|Unbounded|
|`overwrite_buffer`|모두|주문됨|Unbounded|Unbounded|
|`single_assignment`|모두|주문됨|Unbounded|Unbounded|
|`call`|대상|주문됨|Unbounded|해당 사항 없음|
|`transformer`|모두|주문됨|Unbounded|1|
|`choice`|모두|주문됨|10|1|
|`join`|모두|주문됨|Unbounded|1|
|`multitype_join`|모두|주문됨|10|1|
|`timer`|원본|해당 사항 없음|해당 사항 없음|1|

다음 섹션에서는 메시지 블록 형식에 대해 자세히 설명 합니다.

[[맨 위로](#top)이동]

## <a name="unbounded_buffer-class"></a><a name="unbounded_buffer"></a> unbounded_buffer 클래스

[Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) 클래스는 범용 비동기 메시징 구조를 나타냅니다. 이 클래스는 여러 소스가 기록하거나 여러 대상이 읽을 수 있는 메시지의 FIFO(선입 선출) 큐를 저장합니다. 대상이 개체에서 메시지를 받으면 `unbounded_buffer` 해당 메시지는 메시지 큐에서 제거 됩니다. 따라서 `unbounded_buffer` 개체에 대상이 여러 개 있을 수 있지만 하나의 대상만 각 메시지를 받습니다. `unbounded_buffer` 클래스는 여러 메시지를 다른 구성 요소에 전달하려고 할 때 유용하고 해당 구성 요소는 각 메시지를 수신해야 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스를 사용 하는 방법의 기본 구조를 보여 줍니다 `unbounded_buffer` . 이 예제에서는 세 개의 값을 `unbounded_buffer` 개체에 보낸 다음 동일한 개체에서 해당 값을 다시 읽습니다.

[!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]

이 예제는 다음과 같은 출력을 생성합니다.

```Output
334455
```

클래스를 사용 하는 방법을 보여 주는 전체 예제는 `unbounded_buffer` [방법: 다양 한 Producer-Consumer 패턴 구현](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="overwrite_buffer-class"></a><a name="overwrite_buffer"></a> overwrite_buffer 클래스

[Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 클래스는 클래스와 유사 `unbounded_buffer` 합니다. 단, `overwrite_buffer` 개체는 하나의 메시지만 저장 합니다. 또한 대상이 개체에서 메시지를 받으면 `overwrite_buffer` 해당 메시지는 버퍼에서 제거 되지 않습니다. 따라서 여러 대상이 하나의 메시지 복사본을 수신합니다.

`overwrite_buffer`클래스는 여러 메시지를 다른 구성 요소에 전달 하려는 경우에 유용 하지만 해당 구성 요소에는 최신 값만 필요 합니다. 이 클래스는 여러 구성 요소에 메시지를 브로드캐스트하려고 할 때도 유용합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스를 사용 하는 방법의 기본 구조를 보여 줍니다 `overwrite_buffer` . 이 예제에서는 세 개의 값을 `overwrite _buffer` 개체에 보낸 다음 동일한 개체에서 현재 값을 세 번 읽습니다. 이 예제는 클래스에 대 한 예제와 비슷합니다 `unbounded_buffer` . 그러나 클래스는 `overwrite_buffer` 하나의 메시지만 저장 합니다. 또한 개체를 읽은 후에는 개체에서 메시지를 제거 하지 않습니다 `overwrite_buffer` .

[!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]

이 예제는 다음과 같은 출력을 생성합니다.

```Output
555555
```

클래스를 사용 하는 방법을 보여 주는 전체 예제는 `overwrite_buffer` [방법: 다양 한 Producer-Consumer 패턴 구현](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="single_assignment-class"></a><a name="single_assignment"></a> single_assignment 클래스

[Concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) 클래스는 클래스와 유사 `overwrite_buffer` 합니다. 단, `single_assignment` 개체는 한 번만 쓸 수 있습니다. `overwrite_buffer` 클래스처럼 대상이 `single_assignment` 개체에서 메시지를 수신할 때 해당 메시지는 해당 개체에서 제거되지 않습니다. 따라서 여러 대상이 하나의 메시지 복사본을 수신합니다. `single_assignment`클래스는 여러 구성 요소에 메시지 하나를 브로드캐스팅하 려는 경우에 유용 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스를 사용 하는 방법의 기본 구조를 보여 줍니다 `single_assignment` . 이 예제에서는 세 개의 값을 `single_assignment` 개체에 보낸 다음 동일한 개체에서 현재 값을 세 번 읽습니다. 이 예제는 클래스에 대 한 예제와 비슷합니다 `overwrite_buffer` . `overwrite_buffer`및 클래스는 모두 `single_assignment` 단일 메시지를 저장 하지만 클래스는 `single_assignment` 한 번만 쓸 수 있습니다.

[!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]

이 예제는 다음과 같은 출력을 생성합니다.

```Output
333333
```

클래스를 사용 하는 방법을 보여 주는 전체 예제는 `single_assignment` [연습: 미래 구현](../../parallel/concrt/walkthrough-implementing-futures.md)을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="call-class"></a><a name="call"></a> call 클래스

[Concurrency:: call](../../parallel/concrt/reference/call-class.md) 클래스는 데이터를 받을 때 작업 함수를 수행 하는 메시지 수신자 역할을 합니다. 이 작업 함수는 람다 식, 함수 개체 또는 함수 포인터 일 수 있습니다. `call`개체는 메시지를 보내는 다른 구성 요소와 병렬로 동작 하기 때문에 일반 함수 호출과 다르게 동작 합니다. `call`개체가 메시지를 받을 때 작업을 수행 하는 경우 해당 메시지를 큐에 추가 합니다. 모든 `call` 개체는 대기열에 있는 메시지를 받은 순서 대로 처리 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스를 사용 하는 방법의 기본 구조를 보여 줍니다 `call` . 이 예제에서는 `call` 콘솔에 수신 하는 각 값을 출력 하는 개체를 만듭니다. 그런 다음이 예제에서는 세 개의 값을 개체에 보냅니다 `call` . 개체는 `call` 별도의 스레드에서 메시지를 처리 하기 때문에이 예제에서는 카운터 변수와 [이벤트](../../parallel/concrt/reference/event-class.md) 개체를 사용 하 여 `call` 함수가 반환 되기 전에 개체가 모든 메시지를 처리 하도록 합니다 `wmain` .

[!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]

이 예제는 다음과 같은 출력을 생성합니다.

```Output
334455
```

클래스를 사용 하는 방법을 보여 주는 전체 예제는 `call` [방법: 호출 및 변환기 클래스에 작업 함수 제공](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="transformer-class"></a><a name="transformer"></a> 변환기 클래스

[Concurrency:: 변환기](../../parallel/concrt/reference/transformer-class.md) 클래스는 메시지 수신자와 메시지 전송자 역할을 합니다. `transformer`클래스는 `call` 데이터를 받을 때 사용자 정의 작업 함수를 수행 하기 때문에 클래스와 유사 합니다. 그러나 클래스는 `transformer` 작업 함수의 결과를 수신자 개체에도 보냅니다. 개체와 마찬가지로 `call` 개체는 `transformer` 메시지를 보내는 다른 구성 요소와 병렬로 작동 합니다. `transformer`개체가 메시지를 받을 때 작업을 수행 하는 경우 해당 메시지를 큐에 추가 합니다. 모든 `transformer` 개체는 대기열에 있는 메시지를 받은 순서 대로 처리 합니다.

`transformer`클래스는 메시지를 하나의 대상으로 보냅니다. `_PTarget`생성자의 매개 변수를로 설정 하는 경우 `NULL` 나중에 [concurrency:: link_target](reference/source-block-class.md#link_target) 메서드를 호출 하 여 대상을 지정할 수 있습니다.

에이전트 라이브러리에서 제공 하는 다른 모든 비동기 메시지 블록 형식과 달리 `transformer` 클래스는 다른 입력 및 출력 형식에 대해 작동할 수 있습니다. 데이터를 한 형식에서 다른 형식으로 변환 하는이 기능을 통해 `transformer` 클래스는 많은 동시 네트워크에서 키 구성 요소가 됩니다. 또한 개체의 작업 함수에서 보다 세분화 된 병렬 기능을 추가할 수 있습니다 `transformer` .

### <a name="example"></a>예제

다음 예제에서는 클래스를 사용 하는 방법의 기본 구조를 보여 줍니다 `transformer` . 이 예제에서는 `transformer` **`int`** 값을 출력으로 생성 하기 위해 0.33에 따라 각 입력 값을 여러 개의 개체를 만듭니다 **`double`** . 그런 다음이 예제에서는 동일한 개체에서 변환 된 값을 받아 `transformer` 콘솔에 출력 합니다.

[!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]

이 예제는 다음과 같은 출력을 생성합니다.

```Output
10.8914.5218.15
```

클래스를 사용 하는 방법을 보여 주는 전체 예제는 `transformer` [방법: 데이터 파이프라인에서 변환기 사용](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="choice-class"></a><a name="choice"></a> choice 클래스

[Concurrency:: choice](../../parallel/concrt/reference/choice-class.md) 클래스는 소스 집합에서 사용 가능한 첫 번째 메시지를 선택 합니다. `choice`클래스는 데이터 흐름 메커니즘 대신 제어 흐름 메커니즘을 나타냅니다. [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md) 항목에서는 데이터 흐름 및 제어 흐름 간의 차이점을 설명 합니다.

Choice 개체에서 읽기 `WaitForMultipleObjects` 는 `bWaitAll` 매개 변수가로 설정 된 경우 Windows API 함수를 호출 하는 것과 비슷합니다 `FALSE` . 그러나 클래스는 `choice` 외부 동기화 개체가 아닌 이벤트 자체에 데이터를 바인딩합니다.

일반적으로 `choice` 클래스를 [concurrency:: receive](reference/concurrency-namespace-functions.md#receive) 함수와 함께 사용 하 여 응용 프로그램에서 제어 흐름을 구동 합니다. `choice`형식이 다른 메시지 버퍼를 선택 해야 하는 경우 클래스를 사용 합니다. `single_assignment`형식이 같은 메시지 버퍼를 선택 해야 하는 경우 클래스를 사용 합니다.

소스를 개체에 연결 하는 순서는 `choice` 선택한 메시지를 결정할 수 있기 때문에 중요 합니다. 예를 들어 이미 메시지를 포함 하는 여러 메시지 버퍼를 개체에 연결 하는 경우를 고려해 보세요 `choice` . `choice`개체는 연결 된 첫 번째 소스에서 메시지를 선택 합니다. 모든 원본을 연결한 후 `choice` 개체는 각 원본에서 메시지를 수신 하는 순서를 유지 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스를 사용 하는 방법의 기본 구조를 보여 줍니다 `choice` . 이 예제에서는 [concurrency:: make_choice](reference/concurrency-namespace-functions.md#make_choice) 함수를 사용 하 여 `choice` 세 가지 메시지 블록 중에서 선택 하는 개체를 만듭니다. 그런 다음이 예제에서는 다양 한 피보나치 수를 계산 하 고 각 결과를 다른 메시지 블록에 저장 합니다. 그런 다음이 예제에서는 먼저 완료 된 작업을 기반으로 하는 메시지를 콘솔에 출력 합니다.

[!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]

이 예제에서는 다음과 같은 샘플 출력을 생성 합니다.

```Output
fib35 received its value first. Result = 9227465
```

<sup>35 번째</sup> 피보나치 수를 계산 하는 작업은 먼저 완료 되도록 보장 되지 않으므로이 예제의 출력은 다를 수 있습니다.

이 예제에서는 [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) 알고리즘을 사용 하 여 피보나치 수를 병렬로 계산 합니다. 에 대 한 자세한 내용은 `parallel_invoke` [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요.

클래스를 사용 하는 방법을 보여 주는 전체 예제는 `choice` [방법: 완료 된 작업 중에서 선택](../../parallel/concrt/how-to-select-among-completed-tasks.md)을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="join-and-multitype_join-classes"></a><a name="join"></a> 조인 및 multitype_join 클래스

[Concurrency:: join](../../parallel/concrt/reference/join-class.md) 및 [concurrency:: multitype_join](../../parallel/concrt/reference/multitype-join-class.md) 클래스를 사용 하면 소스 집합의 각 멤버가 메시지를 받을 때까지 기다릴 수 있습니다. `join`클래스는 일반적인 메시지 유형을 가진 소스 개체에 대해 작동 합니다. `multitype_join`클래스는 서로 다른 메시지 유형을 가질 수 있는 소스 개체에 대해 작동 합니다.

`join`또는 개체에서 읽기 `multitype_join` `WaitForMultipleObjects` 는 `bWaitAll` 매개 변수가로 설정 된 경우 Windows API 함수를 호출 하는 것과 비슷합니다 `TRUE` . 그러나 개체와 마찬가지로 `choice` `join` 및 `multitype_join` 개체는 외부 동기화 개체가 아닌 이벤트 자체에 데이터를 바인딩하는 이벤트 메커니즘을 사용 합니다.

개체를 읽으면 `join` std::[vector](../../standard-library/vector-class.md) 개체가 생성 됩니다. 개체를 읽으면 `multitype_join` std::[tuple](../../standard-library/tuple-class.md) 개체가 생성 됩니다. 요소는 이러한 개체에 해당 소스 버퍼가 나 개체에 연결 되는 것과 동일한 순서로 `join` 나타납니다 `multitype_join` . 소스 버퍼를 또는 개체에 연결 하는 순서는 `join` `multitype_join` 결과 또는 개체의 요소 순서와 연결 되므로 `vector` `tuple` 조인에서 기존 소스 버퍼의 연결을 해제 하지 않는 것이 좋습니다. 이렇게 하면 지정 되지 않은 동작이 발생할 수 있습니다.

### <a name="greedy-versus-non-greedy-joins"></a>Greedy 및 Non-greedy 조인

`join`및 `multitype_join` 클래스는 greedy 조인과 non-greedy 조인의 개념을 지원 합니다. *Greedy 조인은* 모든 메시지를 사용할 수 있을 때까지 메시지를 사용할 수 있게 되 면 각 소스의 메시지를 수락 합니다. *Non-greedy 조인은* 두 단계로 메시지를 수신 합니다. 먼저 non-greedy 조인은 각 소스에서 메시지를 제공할 때까지 대기 합니다. 둘째, 모든 원본 메시지를 사용할 수 있게 되 면 non-greedy 조인은 각 메시지를 예약 하려고 시도 합니다. 각 메시지를 예약할 수 있는 경우 모든 메시지를 사용 하 여 대상에 전파 합니다. 그렇지 않으면 메시지 예약을 해제 하거나 취소 하 고 각 소스가 메시지를 받을 때까지 기다립니다.

Greedy 조인은 메시지를 즉시 허용 하므로 non-greedy 조인 보다 성능이 우수 합니다. 그러나 드문 경우 이지만 non-greedy 조인은 교착 상태가 발생할 수 있습니다. 하나 이상의 공유 원본 개체가 포함 된 조인이 여러 개 있는 경우 non-greedy 조인을 사용 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스를 사용 하는 방법의 기본 구조를 보여 줍니다 `join` . 이 예제에서는 [concurrency:: make_join](reference/concurrency-namespace-functions.md#make_join) 함수를 사용 하 여 `join` 세 개체에서 받는 개체를 만듭니다 `single_assignment` . 이 예제에서는 다양 한 피보나치 수를 계산 하 고, 각 결과를 다른 개체에 저장 한 `single_assignment` 다음 개체가 보유 하 고 있는 각 결과를 콘솔에 출력 `join` 합니다. 이 예제는 클래스가 `choice` `join` 모든 소스 메시지 블록이 메시지를 받을 때까지 대기 한다는 점을 제외 하 고 클래스의 예제와 비슷합니다.

[!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]

이 예제는 다음과 같은 출력을 생성합니다.

```Output
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008
```

이 예제에서는 [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) 알고리즘을 사용 하 여 피보나치 수를 병렬로 계산 합니다. 에 대 한 자세한 내용은 `parallel_invoke` [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요.

클래스 사용 방법을 보여 주는 전체 예제 `join` [는 방법: 완료 된 작업 중에서 선택](../../parallel/concrt/how-to-select-among-completed-tasks.md) 및 [연습: Join을 사용 하 여 교착 상태 방지](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="timer-class"></a><a name="timer"></a> timer 클래스

Concurrency::[timer 클래스](../../parallel/concrt/reference/timer-class.md) 는 메시지 원본 역할을 합니다. `timer`지정 된 시간이 경과 된 후 개체에서 대상으로 메시지를 보냅니다. `timer`클래스는 메시지 전송을 지연 하거나 메시지를 정기적으로 전송 하려는 경우에 유용 합니다.

`timer`클래스는 메시지를 하나의 대상에만 보냅니다. `_PTarget`생성자의 매개 변수를로 설정 하는 경우 `NULL` 나중에 [Concurrency:: ISource:: link_target](reference/source-block-class.md#link_target) 메서드를 호출 하 여 대상을 지정할 수 있습니다.

`timer`개체는 반복 되거나 반복 되지 않을 수 있습니다. 반복 타이머를 만들려면 **`true`** `_Repeating` 생성자를 호출할 때 매개 변수에 대 한를 전달 합니다. 그렇지 않으면 **`false`** `_Repeating` 매개 변수를 전달 하 여 반복 되지 않는 타이머를 만듭니다. 타이머가 반복 되는 경우 각 간격 후에 동일한 메시지를 대상으로 보냅니다.

에이전트 라이브러리는 `timer` 개체를 시작 되지 않은 상태로 만듭니다. Timer 개체를 시작 하려면 [concurrency:: timer:: start](reference/timer-class.md#start) 메서드를 호출 합니다. 개체를 중지 하려면 `timer` 개체를 삭제 하거나 [concurrency:: timer:: stop](reference/timer-class.md#stop) 메서드를 호출 합니다. 반복 되는 타이머를 일시 중지 하려면 [concurrency:: timer::p ause](reference/timer-class.md#pause) 메서드를 호출 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스를 사용 하는 방법의 기본 구조를 보여 줍니다 `timer` . 이 예제에서는 `timer` 및 `call` 개체를 사용 하 여 시간이 오래 걸리는 작업의 진행률을 보고 합니다.

[!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]

이 예제에서는 다음과 같은 샘플 출력을 생성 합니다.

```Output
Computing fib(42)..................................................result is 267914296
```

클래스를 사용 하는 방법을 보여 주는 전체 예제는 `timer` [방법: 정기적으로 메시지 보내기](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="message-filtering"></a><a name="filtering"></a> 메시지 필터링

메시지 블록 개체를 만들 때 메시지 블록이 메시지를 수락 하거나 거부 하는지 여부를 결정 하는 *필터 함수* 를 제공할 수 있습니다. 필터 함수는 메시지 블록이 특정 값만 받도록 보장 하는 유용한 방법입니다.

다음 예제에서는 `unbounded_buffer` 필터 함수를 사용 하 여 짝수만 허용 하는 개체를 만드는 방법을 보여 줍니다. `unbounded_buffer`개체는 홀수를 거부 하므로 짝수의 숫자를 대상 블록에 전파 하지 않습니다.

[!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]

이 예제는 다음과 같은 출력을 생성합니다.

```Output
0 2 4 6 8
```

필터 함수는 람다 함수, 함수 포인터 또는 함수 개체 일 수 있습니다. 모든 필터 함수는 다음 형식 중 하나를 사용 합니다.

```Output
bool (T)
bool (T const &)
```

불필요 한 데이터 복사를 제거 하려면 값으로 전파 되는 집계 형식이 있는 경우 두 번째 형식을 사용 합니다.

메시지 필터링은 구성 요소가 데이터를 받을 때 계산을 수행 하는 데이터 *흐름* 프로그래밍 모델을 지원 합니다. 필터 함수를 사용 하 여 네트워크를 통과 하는 메시지의 데이터 흐름을 제어 하는 예제는 [방법: 메시지 블록 필터 사용](../../parallel/concrt/how-to-use-a-message-block-filter.md), [연습: 데이터 흐름 에이전트 만들기](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)및 [연습: Image-Processing 네트워크 만들기](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="message-reservation"></a><a name="reservation"></a> 메시지 예약

메시지 *예약* 을 사용 하면 메시지 블록에서 나중에 사용할 메시지를 예약할 수 있습니다. 일반적으로 메시지 예약은 직접 사용 되지 않습니다. 그러나 메시지 예약을 이해 하면 미리 정의 된 메시지 블록 형식의 동작을 보다 잘 이해할 수 있습니다.

Non-greedy 및 greedy 조인을 고려 합니다. 이러한 두 가지 모두 메시지 예약을 사용 하 여 나중에 사용할 메시지를 예약 합니다. 앞에서 설명한 것 처럼 non-greedy 조인은 두 단계로 메시지를 수신 합니다. 첫 번째 단계에서 non-greedy `join` 개체는 각 소스에서 메시지를 받을 때까지 대기 합니다. 그런 다음 non-greedy 조인은 각 메시지를 예약 하려고 시도 합니다. 각 메시지를 예약할 수 있는 경우 모든 메시지를 사용 하 여 대상에 전파 합니다. 그렇지 않으면 메시지 예약을 해제 하거나 취소 하 고 각 소스가 메시지를 받을 때까지 기다립니다.

여러 소스에서 입력 메시지를 읽는 greedy 조인은 메시지 예약을 사용 하 여 각 소스에서 메시지를 수신 하기 위해 대기 하는 동안 추가 메시지를 읽습니다. 예를 들어 메시지 블록 및에서 메시지를 수신 하는 greedy 조인을 고려 합니다 `A` `B` . Greedy 조인이 B의 메시지 두 개를 받지만에서 메시지를 아직 받지 않은 경우 `A` greedy 조인은에서 두 번째 메시지의 고유한 메시지 식별자를 저장 `B` 합니다. Greedy 조인이에서 메시지를 수신 `A` 하 고 이러한 메시지를 전파 한 후에는 저장 된 메시지 식별자를 사용 하 여의 두 번째 메시지를 `B` 계속 사용할 수 있는지 확인 합니다.

사용자 고유의 사용자 지정 메시지 블록 형식을 구현할 때 메시지 예약을 사용할 수 있습니다. 사용자 지정 메시지 블록 형식을 만드는 방법에 대 한 예제는 [연습: 사용자 지정 메시지 블록 만들기](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="see-also"></a>참고 항목

[비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)
