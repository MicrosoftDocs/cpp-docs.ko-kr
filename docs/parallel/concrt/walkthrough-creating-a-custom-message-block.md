---
description: '자세한 정보: 연습: 사용자 지정 메시지 블록 만들기'
title: '연습: 사용자 지정 메시지 블록 만들기'
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: 2347284c4541ef52579a2179c6387b435b1d382f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163849"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>연습: 사용자 지정 메시지 블록 만들기

이 문서에서는 들어오는 메시지를 우선 순위별로 정렬 하는 사용자 지정 메시지 블록 형식을 만드는 방법을 설명 합니다.

기본 제공 메시지 블록 형식은 다양 한 기능을 제공 하지만 사용자 고유의 메시지 블록 형식을 만들어 응용 프로그램의 요구 사항에 맞게 사용자 지정할 수 있습니다. 비동기 에이전트 라이브러리에서 제공 하는 기본 제공 메시지 블록 형식에 대 한 설명은 [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

## <a name="prerequisites"></a>사전 요구 사항

이 연습을 시작 하기 전에 다음 문서를 읽어 보세요.

- [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)

- [메시지 전달 함수](../../parallel/concrt/message-passing-functions.md)

## <a name="sections"></a><a name="top"></a> 섹션이

이 연습에는 다음과 같은 섹션이 있습니다.

- [사용자 지정 메시지 블록 디자인](#design)

- [Priority_buffer 클래스 정의](#class)

- [전체 예제](#complete)

## <a name="designing-a-custom-message-block"></a><a name="design"></a> 사용자 지정 메시지 블록 디자인

메시지 블록은 메시지를 보내고 받는 동작에 참여 합니다. 메시지를 보내는 메시지 블록을 *소스 블록* 이라고 합니다. 메시지를 수신 하는 메시지 블록을 *대상 블록* 이라고 합니다. 메시지를 보내고 받는 메시지 블록을 *전파자 블록* 이라고 합니다. 에이전트 라이브러리는 추상 클래스 [concurrency:: ISource](../../parallel/concrt/reference/isource-class.md) 를 사용 하 여 소스 블록을 나타내고 추상 클래스 [Concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) 를 사용 하 여 대상 블록을 나타냅니다. 소스로 작동 하는 메시지 블록 형식은에서 파생 되며 `ISource` 대상으로 작동 하는 메시지 블록 형식은에서 파생 `ITarget` 됩니다.

및에서 직접 메시지 블록 형식을 파생할 수는 있지만 `ISource` , `ITarget` 에이전트 라이브러리는 모든 메시지 블록 형식에 공통적인 기능을 대부분 수행 하는 세 가지 기본 클래스를 정의 합니다. 예를 들어 오류를 처리 하 고 메시지 블록을 동시에 안전 하 게 연결할 수 있습니다. [Concurrency:: source_block](../../parallel/concrt/reference/source-block-class.md) 클래스는에서 파생 되 `ISource` 고 메시지를 다른 블록으로 보냅니다. [Concurrency:: target_block](../../parallel/concrt/reference/target-block-class.md) 클래스는에서 파생 되 `ITarget` 고 다른 블록에서 메시지를 받습니다. [Concurrency::p ropagator_block](../../parallel/concrt/reference/propagator-block-class.md) 클래스는 및에서 `ISource` 파생 `ITarget` 되 고 메시지를 다른 블록으로 보내고 다른 블록에서 메시지를 받습니다. 메시지 블록의 동작에 집중할 수 있도록 이러한 세 가지 기본 클래스를 사용 하 여 인프라 세부 정보를 처리 하는 것이 좋습니다.

`source_block`, `target_block` 및 클래스는 `propagator_block` 소스 블록과 대상 블록 간의 연결 또는 링크를 관리 하는 형식에서 매개 변수화 된 템플릿 및 메시지 처리 방법을 관리 하는 형식입니다. 에이전트 라이브러리는 링크 관리, [concurrency:: single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) 및 [concurrency:: multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md)를 수행 하는 두 가지 형식을 정의 합니다. `single_link_registry`클래스를 사용 하면 메시지 블록이 하나의 소스 나 하나의 대상에 연결 될 수 있습니다. `multi_link_registry`클래스를 사용 하면 메시지 블록이 여러 원본 또는 여러 대상에 연결 될 수 있습니다. 에이전트 라이브러리는 메시지 관리, [동시성:: ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md)를 수행 하는 하나의 클래스를 정의 합니다. `ordered_message_processor`클래스를 사용 하면 메시지 블록에서 메시지를 받은 순서 대로 메시지를 처리할 수 있습니다.

메시지 블록의 원본 및 대상과 관련 된 방법을 더 잘 이해 하려면 다음 예제를 참조 하세요. 이 예제에서는 [concurrency:: 변환기](../../parallel/concrt/reference/transformer-class.md) 클래스의 선언을 보여 줍니다.

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

`transformer`클래스는에서 파생 `propagator_block` 되므로 소스 블록과 대상 블록 역할을 모두 수행 합니다. 형식의 메시지 `_Input` 를 수락 하 고 형식의 메시지를 보냅니다 `_Output` . `transformer`클래스는 `single_link_registry` 모든 대상 블록에 대 한 링크 관리자로 지정 하 고 `multi_link_registry` 모든 소스 블록에 대 한 링크 관리자로 지정 합니다. 따라서 개체에는 `transformer` 최대 하나의 대상과 개수에 제한 없이 원본을 사용할 수 있습니다.

에서 파생 되는 클래스는 `source_block` [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message)및 [resume_propagation](reference/source-block-class.md#resume_propagation)의 6 가지 메서드를 구현 해야 합니다. 에서 파생 되는 클래스는 `target_block` [propagate_message](reference/propagator-block-class.md#propagate_message) 메서드를 구현 해야 하며 필요에 따라 [send_message](reference/propagator-block-class.md#send_message) 메서드를 구현할 수 있습니다. 에서 파생 `propagator_block` 하는 것은 및에서 파생 하는 것과 기능적으로 동일 `source_block` `target_block` 합니다.

메서드는 들어오는 모든 메시지 `propagate_to_any_targets` 를 비동기적으로 처리 하 고 나가는 메시지를 전파 하기 위해 런타임에서 호출 됩니다. `accept_message`메서드는 메시지를 수락 하기 위해 대상 블록에 의해 호출 됩니다. 와 같은 많은 메시지 블록 형식은 `unbounded_buffer` 메시지를 수신 하는 첫 번째 대상에만 메시지를 보냅니다. 따라서 메시지의 소유권을 대상으로 전송 합니다. [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)와 같은 다른 메시지 블록 형식은 각 대상 블록에 메시지를 제공 합니다. 따라서는 `overwrite_buffer` 각 대상에 대해 메시지의 복사본을 만듭니다.

`reserve_message`,, `consume_message` 및 메서드는 메시지 `release_message` `resume_propagation` 블록이 메시지 예약에 참여할 수 있도록 합니다. 대상 블록은 `reserve_message` 메시지를 제공 하 고 나중에 사용할 수 있도록 메시지를 예약 해야 하는 경우 메서드를 호출 합니다. 대상 블록이 메시지를 예약 하 고 나면 메서드를 호출 하 여 `consume_message` 해당 메시지를 사용 하거나 메서드를 호출 하 여 예약을 취소할 수 있습니다 `release_message` . `accept_message`메서드와 마찬가지로의 구현은 `consume_message` 메시지 소유권을 양도 하거나 메시지 복사본을 반환할 수 있습니다. 대상 블록이 예약 된 메시지를 사용 하거나 해제 한 후에는 런타임에서 메서드를 호출 합니다 `resume_propagation` . 일반적으로이 메서드는 큐의 다음 메시지부터 시작 하 여 메시지 전파를 계속 합니다.

런타임은 메서드를 호출 `propagate_message` 하 여 다른 블록에서 현재로 메시지를 비동기적으로 전송 합니다. `send_message`메서드는 `propagate_message` 비동기 대신 동기적으로 대상 블록에 메시지를 보내는 점을 제외 하 고는와 유사 합니다. 의 기본 구현은 `send_message` 들어오는 모든 메시지를 거부 합니다. 메시지에서 대상 블록과 연결 된 선택적 필터 함수를 전달 하지 않는 경우 런타임은 이러한 메서드 중 하나를 호출 하지 않습니다. 메시지 필터에 대 한 자세한 내용은 [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="defining-the-priority_buffer-class"></a><a name="class"></a> Priority_buffer 클래스 정의

`priority_buffer`클래스는 들어오는 메시지를 우선 순위에 따라 먼저 정렬 한 다음 메시지를 받은 순서 대로 정렬 하는 사용자 지정 메시지 블록 형식입니다. `priority_buffer`클래스는 메시지 큐를 포함 하기 때문에 [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) 클래스와 비슷하며, 소스 및 대상 메시지 블록 역할을 모두 수행 하 고 여러 원본과 대상을 모두 포함할 수 있기 때문입니다. 그러나는 `unbounded_buffer` 메시지 전파가 원본에서 메시지를 수신 하는 순서 대로만 메시지를 전파 합니다.

`priority_buffer`클래스는 및 요소를 포함 하는 std::[tuple](../../standard-library/tuple-class.md) 형식의 메시지를 받습니다 `PriorityType` `Type` . `PriorityType` 각 메시지의 우선 순위를 보유 하는 형식을 참조 합니다. `Type` 메시지의 데이터 부분을 참조 합니다. `priority_buffer`클래스는 형식의 메시지를 보냅니다 `Type` . `priority_buffer`또한 클래스는 들어오는 메시지에 대 한 [std::p riority_queue](../../standard-library/priority-queue-class.md) 개체와 보내는 메시지에 대 한 std::[queue](../../standard-library/queue-class.md) 개체 라는 두 개의 메시지 큐를 관리 합니다. 메시지를 우선 순위별로 정렬 하는 것은 `priority_buffer` 개체가 여러 메시지를 동시에 받거나 소비자가 메시지를 읽기 전에 여러 메시지를 수신 하는 경우에 유용 합니다.

에서 파생 되는 클래스에서 구현 해야 하는 일곱 가지 메서드 외에 `propagator_block` `priority_buffer` 도 클래스는 및 메서드를 재정의 합니다 `link_target_notification` `send_message` . `priority_buffer`또한 클래스는 두 개의 public 도우미 메서드인 `enqueue` 및를 정의 하 `dequeue` 고 개인 도우미 메서드인를 정의 `propagate_priority_order` 합니다.

다음 절차에서는 클래스를 구현 하는 방법을 설명 합니다 `priority_buffer` .

#### <a name="to-define-the-priority_buffer-class"></a>Priority_buffer 클래스를 정의 하려면

1. C + + 헤더 파일을 만들고 이름을로 `priority_buffer.h` 합니다. 또는 프로젝트의 일부인 기존 헤더 파일을 사용할 수 있습니다.

1. 에서 `priority_buffer.h` 다음 코드를 추가 합니다.

    [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. `std`네임 스페이스에서 concurrency::[message](../../parallel/concrt/reference/message-class.md) 개체에 대해 작동 하는 [std:: less](../../standard-library/less-struct.md) 및 [std:: 큰지](../../standard-library/greater-struct.md) 특수화를 정의 합니다.

    [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   `priority_buffer`클래스는 개체 `message` 에 개체를 저장 `priority_queue` 합니다. 이러한 형식 특수화를 사용 하면 우선 순위 큐에서 우선 순위에 따라 메시지를 정렬할 수 있습니다. 우선 순위는 개체의 첫 번째 요소입니다 `tuple` .

1. `concurrencyex`네임 스페이스에서 클래스를 선언 합니다 `priority_buffer` .

    [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   `priority_buffer` 클래스는 `propagator_block`에서 파생됩니다. 따라서 메시지를 보내고 받을 수 있습니다. 클래스에는 `priority_buffer` 형식의 메시지를 수신 하는 대상이 여러 개 있을 수 있습니다 `Type` . 또한 형식의 메시지를 보내는 여러 소스가 있을 수 있습니다 `tuple<PriorityType, Type>` .

1. **`private`** 클래스의 섹션에서 `priority_buffer` 다음 멤버 변수를 추가 합니다.

    [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   `priority_queue`개체는 들어오는 메시지를 보유 하며 `queue` 개체는 나가는 메시지를 보유 합니다. `priority_buffer`개체는 여러 메시지를 동시에 받을 수 있습니다. `critical_section` 개체는 입력 메시지의 큐에 대 한 액세스를 동기화 합니다.

1. 섹션에서 **`private`** 복사 생성자와 대입 연산자를 정의 합니다. 이렇게 하면 `priority_queue` 개체를 할당할 수 없습니다.

    [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. 섹션에서 **`public`** 많은 메시지 블록 형식에 공통적인 생성자를 정의 합니다. 소멸자도 정의 합니다.

    [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. 섹션에서 **`public`** 및 메서드를 정의 합니다 `enqueue` `dequeue` . 이러한 도우미 메서드는 개체에서 메시지를 보내고 받을 수 있는 대체 방법을 제공 `priority_buffer` 합니다.

    [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

1. 섹션에서 **`protected`** 메서드를 정의 합니다 `propagate_to_any_targets` .

    [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   `propagate_to_any_targets`메서드는 입력 큐의 앞에 있는 메시지를 출력 큐에 전송 하 고 출력 큐의 모든 메시지를 전파 합니다.

1. 섹션에서 **`protected`** 메서드를 정의 합니다 `accept_message` .

    [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   대상 블록이 메서드를 호출 하는 경우 `accept_message` `priority_buffer` 클래스는 메시지의 소유권을 해당 메시지를 수락 하는 첫 번째 대상 블록으로 전송 합니다. 이는의 동작과 유사 `unbounded_buffer` 합니다.

1. 섹션에서 **`protected`** 메서드를 정의 합니다 `reserve_message` .

    [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   `priority_buffer`클래스를 사용 하면 제공 된 메시지 식별자가 큐 앞에 있는 메시지의 식별자와 일치 하는 경우 대상 블록이 메시지를 예약할 수 있습니다. 즉, `priority_buffer` 개체에서 추가 메시지를 아직 받지 않고 현재 메시지를 아직 전파 하지 않은 경우 대상에서 메시지를 예약할 수 있습니다.

1. 섹션에서 **`protected`** 메서드를 정의 합니다 `consume_message` .

    [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   대상 블록은 `consume_message` 예약 된 메시지의 소유권을 전송 하기 위해를 호출 합니다.

1. 섹션에서 **`protected`** 메서드를 정의 합니다 `release_message` .

    [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   대상 블록은 `release_message` 를 호출 하 여 메시지에 대 한 예약을 취소 합니다.

1. 섹션에서 **`protected`** 메서드를 정의 합니다 `resume_propagation` .

    [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   `resume_propagation`대상 블록이 예약 된 메시지를 사용 하거나 해제 한 후 런타임에서를 호출 합니다. 이 메서드는 출력 큐에 있는 모든 메시지를 전파 합니다.

1. 섹션에서 **`protected`** 메서드를 정의 합니다 `link_target_notification` .

    [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   `_M_pReservedFor`멤버 변수는 기본 클래스인로 정의 됩니다 `source_block` . 이 멤버 변수는 출력 큐의 앞에 있는 메시지에 대 한 예약을 보유 하는 대상 블록 (있는 경우)을 가리킵니다. `link_target_notification`새 대상이 개체에 연결 되 면 런타임에서를 호출 합니다 `priority_buffer` . 이 메서드는 예약을 보유 하 고 있는 대상이 없으면 출력 큐에 있는 모든 메시지를 전파 합니다.

1. 섹션에서 **`private`** 메서드를 정의 합니다 `propagate_priority_order` .

    [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   이 메서드는 출력 큐의 모든 메시지를 전파 합니다. 대상 블록 중 하나가 메시지를 수락 하기 전까지 큐의 모든 메시지는 모든 대상 블록에 제공 됩니다. `priority_buffer`클래스는 보내는 메시지의 순서를 유지 합니다. 따라서이 메서드는 대상 블록에 다른 메시지를 제공 하기 전에 대상 블록에서 출력 큐의 첫 번째 메시지를 수락 해야 합니다.

1. 섹션에서 **`protected`** 메서드를 정의 합니다 `propagate_message` .

    [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   `propagate_message`메서드를 사용 하면 `priority_buffer` 클래스가 메시지 받는 사람 또는 대상으로 동작할 수 있습니다. 이 메서드는 제공 된 소스 블록이 제공 하는 메시지를 받고 해당 메시지를 우선 순위 큐에 삽입 합니다. `propagate_message`그런 다음 메서드는 모든 출력 메시지를 대상 블록으로 비동기적으로 보냅니다.

   [Concurrency:: asend](reference/concurrency-namespace-functions.md#asend) 함수를 호출할 때 또는 메시지 블록이 다른 메시지 블록에 연결 된 경우 런타임은이 메서드를 호출 합니다.

1. 섹션에서 **`protected`** 메서드를 정의 합니다 `send_message` .

    [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   메서드는와 `send_message` 유사 `propagate_message` 합니다. 그러나 출력 메시지를 비동기적이 아닌 동기적으로 보냅니다.

   [Concurrency:: send](reference/concurrency-namespace-functions.md#send) 함수를 호출 하는 경우와 같이 동기 전송 작업 중에 런타임은이 메서드를 호출 합니다.

클래스에는 `priority_buffer` 많은 메시지 블록 형식에서 일반적인 생성자 오버 로드가 포함 되어 있습니다. 일부 생성자 오버 로드는 [concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) 또는 [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) 개체를 사용 합니다 .이 개체를 사용 하면 특정 작업 스케줄러에서 메시지 블록을 관리할 수 있습니다. 다른 생성자 오버 로드는 필터 함수를 사용 합니다. 필터 함수를 사용 하면 메시지 블록에서 페이로드를 기준으로 메시지를 수락 하거나 거부할 수 있습니다. 메시지 필터에 대 한 자세한 내용은 [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요. 작업 스케줄러에 대 한 자세한 내용은 [작업 스케줄러](../../parallel/concrt/task-scheduler-concurrency-runtime.md)를 참조 하세요.

이 클래스는 메시지를 `priority_buffer` 우선 순위별로 정렬 한 다음 메시지를 받은 순서 대로 정렬 하므로이 클래스는 [concurrency:: asend](reference/concurrency-namespace-functions.md#asend) 함수를 호출 하거나 메시지 블록이 다른 메시지 블록에 연결 된 경우와 같이 메시지를 비동기적으로 받을 때 가장 유용 합니다.

[[맨 위로](#top)이동]

## <a name="the-complete-example"></a><a name="complete"></a> 전체 예제

다음 예제에서는 클래스의 전체 정의를 보여 줍니다 `priority_buffer` .

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

다음 예제에서는 `asend` 개체에 대해 많은 및 [concurrency:: receive](reference/concurrency-namespace-functions.md#receive) 작업을 동시에 수행 합니다 `priority_buffer` .

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

이 예제에서는 다음 샘플 출력을 생성 합니다.

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

`priority_buffer`클래스는 우선 순위에 따라 메시지를 먼저 정렬 한 다음 메시지를 받은 순서 대로 정렬 합니다. 이 예제에서 우선 순위가 더 높은 메시지는 큐 앞에 삽입 됩니다.

[[맨 위로](#top)이동]

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나, 클래스의 정의를 라는 파일 `priority_buffer` `priority_buffer.h` 의 및 테스트 프로그램에 붙여넣은 `priority_buffer.cpp` 후 Visual studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

**cl.exe/EHsc priority_buffer**

## <a name="see-also"></a>참고 항목

[동시성 런타임 연습](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[메시지 전달 함수](../../parallel/concrt/message-passing-functions.md)
