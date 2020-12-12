---
description: '자세한 정보: 컨텍스트'
title: 컨텍스트
ms.date: 11/04/2016
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
ms.openlocfilehash: 70c97b74afaaa755a85532c7bc08a3a5c5fe3e17
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325773"
---
# <a name="contexts"></a>컨텍스트

이 문서에서는 동시성 런타임 컨텍스트의 역할에 대해 설명 합니다. 스케줄러에 연결 된 스레드를 *실행 컨텍스트나* *컨텍스트* 라고 합니다. [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) 함수와 concurrency::[Context 클래스](../../parallel/concrt/reference/context-class.md) 를 사용 하면 컨텍스트의 동작을 제어할 수 있습니다. 함수를 사용 `wait` 하 여 지정 된 시간 동안 현재 컨텍스트를 일시 중단 합니다. `Context`컨텍스트가 차단, 차단 해제 및 양보 될 때 또는 현재 컨텍스트를 oversubscribe 할 때 더 많은 제어가 필요한 경우 클래스를 사용 합니다.

> [!TIP]
> 동시성 런타임은 기본 스케줄러를 제공하므로 애플리케이션에서 스케줄러를 만들 필요가 없습니다. 작업 스케줄러는 응용 프로그램의 성능을 미세 조정 하는 데 도움이 되므로 동시성 런타임를 처음 접하는 경우 [PPL (병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md) 또는 [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md) 를 사용 하는 것이 좋습니다.

## <a name="the-wait-function"></a>Wait 함수

[Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) 함수는 지정 된 시간 (밀리초) 동안 현재 컨텍스트의 실행을 협조적으로 생성 합니다. 런타임에서는 양보 시간을 사용 하 여 다른 작업을 수행 합니다. 지정 된 시간이 경과 된 후 런타임은 실행을 위해 컨텍스트를 다시 예약 합니다. 따라서 함수는 `wait` 매개 변수에 제공 된 값 보다 오래 된 현재 컨텍스트를 일시 중단할 수 있습니다 `milliseconds` .

매개 변수에 0을 전달 `milliseconds` 하면 다른 모든 활성 컨텍스트를 사용 하 여 작업을 수행할 수 있을 때까지 런타임이 현재 컨텍스트를 일시 중단 합니다. 이렇게 하면 다른 모든 활성 태스크에 대 한 작업을 생성할 수 있습니다.

### <a name="example"></a>예제

함수를 사용 하 여 `wait` 현재 컨텍스트를 생성 하 고 다른 컨텍스트를 실행할 수 있도록 하는 예제는 [방법: 일정 그룹을 사용 하 여 실행 순서에 영향](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)을 참조 하세요.

## <a name="the-context-class"></a>컨텍스트 클래스

Concurrency::[context 클래스](../../parallel/concrt/reference/context-class.md) 는 실행 컨텍스트에 대 한 프로그래밍 추상화를 제공 하 고, 현재 컨텍스트를 협조적으로 차단, 차단 해제 및 양보 하는 기능 및 현재 컨텍스트를 oversubscribe 하는 기능을 제공 하는 두 가지 중요 한 기능을 제공 합니다.

### <a name="cooperative-blocking"></a>협조적 차단

`Context`클래스를 사용 하 여 현재 실행 컨텍스트를 차단 하거나 생성할 수 있습니다. 차단 또는 생성은 리소스를 사용할 수 없기 때문에 현재 컨텍스트를 계속할 수 없는 경우에 유용 합니다.

[Concurrency:: context:: Block](reference/context-class.md#block) 메서드는 현재 컨텍스트를 차단 합니다. 차단 된 컨텍스트는 런타임에서 다른 작업을 수행할 수 있도록 처리 리소스를 생성 합니다. [Concurrency:: context:: 차단 해제](reference/context-class.md#unblock) 메서드는 차단 된 컨텍스트를 차단 해제 합니다. 메서드는를 호출 하는 것과 `Context::Unblock` 다른 컨텍스트에서 호출 되어야 합니다 `Context::Block` . 런타임에서는 컨텍스트를 차단 해제 하려는 경우 [concurrency:: context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) 을 throw 합니다.

컨텍스트를 협조적으로 차단 및 차단 해제 하기 위해 일반적으로 [concurrency:: context:: CurrentContext](reference/context-class.md#currentcontext) 를 호출 하 여 현재 스레드와 연결 된 개체에 대 한 포인터를 검색 하 `Context` 고 그 결과를 저장 합니다. 그런 다음 메서드를 호출 `Context::Block` 하 여 현재 컨텍스트를 차단 합니다. 나중에 `Context::Unblock` 개별 컨텍스트에서를 호출 하 여 차단 된 컨텍스트의 차단을 해제 합니다.

및에 대 한 각 호출 쌍을 일치 시켜야 합니다 `Context::Block` `Context::Unblock` . 런타임에서는 [](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) `Context::Block` `Context::Unblock` 다른 메서드에 대 한 일치 하는 호출 없이 또는 메서드가 연속적으로 호출 될 때 concurrency:: context_unblock_unbalanced을 throw 합니다. 그러나를 호출 하기 전에를 호출할 필요가 없습니다 `Context::Block` `Context::Unblock` . 예를 들어 한 컨텍스트가 `Context::Unblock` 동일한 컨텍스트에 대해 다른 컨텍스트를 호출 하기 전에를 호출 하 `Context::Block` 는 경우 해당 컨텍스트는 차단 해제 된 상태로 유지 됩니다.

[Concurrency:: Context:: Yield](reference/context-class.md#yield) 메서드는 런타임이 다른 작업을 수행한 다음 실행을 위해 컨텍스트를 다시 예약할 수 있도록 실행을 생성 합니다. 메서드를 호출 하면 `Context::Block` 런타임에서 컨텍스트를 다시 예약 하지 않습니다.

#### <a name="example"></a>예제

, 및 메서드를 사용 하 여 협조적 세마포 클래스를 구현 하는 예제는 `Context::Block` `Context::Unblock` `Context::Yield` [방법: 컨텍스트 클래스를 사용 하 여 협조적 세마포 구현](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)을 참조 하세요.

##### <a name="oversubscription"></a>초과 구독

기본 스케줄러는 사용 가능한 하드웨어 스레드와 동일한 수의 스레드를 만듭니다. *초과 구독* 을 사용 하 여 지정 된 하드웨어 스레드에 대 한 추가 스레드를 만들 수 있습니다.

계산을 많이 수행 하는 작업의 경우에는 일반적으로 추가 오버 헤드가 발생 하므로 초과 구독이 확장 되지 않습니다. 그러나 디스크에서 데이터를 읽거나 네트워크를 연결 하는 등의 대기 시간이 많은 작업의 경우에는 초과 구독이 일부 응용 프로그램의 전반적인 효율성을 향상 시킬 수 있습니다.

> [!NOTE]
> 동시성 런타임을 통해 생성된 스레드에서만 초과 구독을 사용하도록 설정하십시오. 시간 초과는 런타임에 의해 생성 되지 않은 스레드에서 호출 된 경우 (주 스레드 포함)에는 영향을 주지 않습니다.

현재 컨텍스트에서 초과 구독을 사용 하도록 설정 하려면 매개 변수를로 설정 하 여 [concurrency:: context:: Oversubscribe](reference/context-class.md#oversubscribe) 메서드를 호출 합니다 `_BeginOversubscription` **`true`** . 동시성 런타임에서 만든 스레드에서 초과 구독을 사용 하도록 설정 하면 런타임에서 추가 스레드 하나를 만듭니다. 초과 구독을 필요로 하는 모든 작업이 완료 되 면 `Context::Oversubscribe` `_BeginOversubscription` 매개 변수를로 설정 하 여를 호출 **`false`** 합니다.

현재 컨텍스트에서 초과 구독을 여러 번 사용 하도록 설정할 수 있지만 사용 하도록 설정 하는 것과 동일한 횟수를 사용 하지 않도록 설정 해야 합니다. 초과 구독을 중첩할 수도 있습니다. 즉, 구독을 사용 하는 다른 작업에서 만든 작업은 해당 컨텍스트를 oversubscribe 수도 있습니다. 그러나 중첩 된 작업과 부모를 모두 동일한 컨텍스트에 속하면의 가장 바깥쪽 호출만 `Context::Oversubscribe` 추가 스레드를 생성 합니다.

> [!NOTE]
> 사용 하도록 설정 하기 전에 시간 초과를 사용 하지 않도록 설정 하면 런타임에서 [concurrency:: invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) 을 throw 합니다.

###### <a name="example"></a>예제

초과 구독을 사용 하 여 네트워크 연결에서 데이터를 읽는 경우 발생 하는 대기 시간을 오프셋 하는 예제는 [방법: 초과 구독을 사용 하 여 대기 시간 오프셋](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[작업 Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[방법: 일정 그룹을 사용 하 여 실행 순서에 영향을 줍니다.](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)<br/>
[방법: 컨텍스트 클래스를 사용 하 여 협조적 세마포 구현](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[방법: 초과 구독을 사용 하 여 대기 시간 오프셋](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)
