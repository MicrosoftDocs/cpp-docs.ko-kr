---
description: '자세한 정보: PPL에서 취소'
title: PPL에서의 취소
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms, canceling [Concurrency Runtime]
- canceling parallel algorithms [Concurrency Runtime]
- parallel tasks, canceling [Concurrency Runtime]
- cancellation in the PPL
- parallel work trees [Concurrency Runtime]
- canceling parallel tasks [Concurrency Runtime]
ms.assetid: baaef417-b2f9-470e-b8bd-9ed890725b35
ms.openlocfilehash: c15d3901df8968dd6d410e8305880585637a3fee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250675"
---
# <a name="cancellation-in-the-ppl"></a>PPL에서의 취소

이 문서에서는 PPL(병렬 패턴 라이브러리)에서 취소의 역할, 병렬 작업을 취소하는 방법 및 병렬 작업이 취소될 경우를 확인하는 방법에 대해 설명합니다.

> [!NOTE]
> 런타임에서는 예외 처리를 사용하여 취소를 구현합니다. 코드에서 이들 예외를 catch 또는 처리하지 마세요. 또한 작업에 대한 함수 본문에 예외로부터 안전한 코드를 작성하는 것이 좋습니다. 예를 들어 작업 본문에서 예외가 throw 될 때 리소스를 올바르게 처리 하기 위해 RAII ( *Resource Instance Initialization* ) 패턴을 사용할 수 있습니다. RAII 패턴을 사용 하 여 취소할 수 있는 작업에서 리소스를 정리 하는 전체 예제는 [연습: User-Interface 스레드에서 작업 제거](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)를 참조 하세요.

## <a name="key-points"></a>요점

- 취소는 공동 작업이고 취소를 요청하는 코드와 취소에 응답하는 작업 간의 조정을 포함합니다.

- 가능하면 취소 토큰을 사용하여 작업을 취소하세요. [Concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) 클래스는 취소 토큰을 정의 합니다.

- 취소 토큰을 사용 하는 경우 [concurrency:: cancellation_token_source:: cancel](reference/cancellation-token-source-class.md#cancel) 메서드를 사용 하 여 취소를 시작 하 고 [concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) 함수를 사용 하 여 취소에 응답 합니다. [Concurrency:: cancellation_token:: is_canceled](reference/cancellation-token-class.md#is_canceled) 메서드를 사용 하 여 다른 작업에서 취소를 요청 했는지 여부를 확인 합니다.

- 취소는 즉시 발생하지 않습니다. 작업 또는 작업 그룹이 취소 된 경우 새 작업이 시작 되지 않지만 활성 작업에서 취소를 확인 하 고 취소에 응답 해야 합니다.

- 값 기반 연속은 선행 작업의 취소 토큰을 상속합니다. 작업 기반 연속은 선행 작업의 취소 토큰을 상속하지 않습니다.

- 개체를 사용 하지만 작업을 취소 가능한 하지 않으려는 생성자 또는 함수를 호출 하는 경우 [concurrency:: cancellation_token:: none](reference/cancellation-token-class.md#none) 메서드를 사용 `cancellation_token` 합니다. 또한 취소 토큰을 [concurrency:: task](../../parallel/concrt/reference/task-class.md) 생성자 또는 [concurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) 함수에 전달 하지 않으면 해당 작업은 취소 가능한 되지 않습니다.

## <a name="in-this-document"></a><a name="top"></a> 이 문서의

- [병렬 작업 트리](#trees)

- [병렬 작업 취소](#tasks)

  - [취소 토큰을 사용하여 병렬 작업 취소](#tokens)

  - [cancel 메서드를 사용하여 병렬 작업 취소](#cancel)

  - [예외를 사용하여 병렬 작업 취소](#exceptions)

- [병렬 알고리즘 취소](#algorithms)

- [취소를 사용하지 않는 경우](#when)

## <a name="parallel-work-trees"></a><a name="trees"></a> 병렬 작업 트리

PPL에서는 작업 및 작업 그룹을 사용하여 세분화된 작업 및 계산을 관리합니다. 작업 그룹을 중첩 하 여 병렬 작업 *트리* 를 만들 수 있습니다. 다음 그림은 병렬 작업 트리를 보여 줍니다. 이 그림에서 `tg1` 및 `tg2`는 작업 그룹을 나타내고, `t1`, `t2`, `t3`, `t4` 및 `t5`는 작업 그룹에서 수행하는 작업을 나타냅니다.

![병렬 작업 트리](../../parallel/concrt/media/parallelwork_trees.png "병렬 작업 트리")

다음 예제에서는 그림의 트리를 만드는 데 필요한 코드를 보여 줍니다. 이 예제에서 `tg1` 및 `tg2` 은 [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) 개체이 고,,, 및는 `t1` `t2` `t3` `t4` `t5` [concurrency:: task_handle](../../parallel/concrt/reference/task-handle-class.md) 개체입니다.

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

또한 [concurrency:: task_group](reference/task-group-class.md) 클래스를 사용 하 여 비슷한 작업 트리를 만들 수 있습니다. [Concurrency:: task](../../parallel/concrt/reference/task-class.md) 클래스는 작업 트리의 개념도 지원 합니다. 그러나 `task` 트리는 종속성 트리입니다. `task` 트리에서 미래 작업은 현재 작업 후에 완료됩니다. 작업 그룹 트리에서 내부 작업은 외부 작업 전에 완료됩니다. 작업 및 작업 그룹 간의 차이점에 대 한 자세한 내용은 [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="canceling-parallel-tasks"></a><a name="tasks"></a> 병렬 작업 취소

병렬 작업을 취소하는 방법은 여러 가지가 있습니다. 여러 방법 중에 취소 토큰을 사용하는 것이 좋습니다. 작업 그룹 에서도 [concurrency:: task_group:: cancel](reference/task-group-class.md#cancel) 메서드와 [concurrency:: structured_task_group:: cancel](reference/structured-task-group-class.md#cancel) 메서드를 지원 합니다. 마지막 방법은 작업 함수의 본문에서 예외를 throw하는 것입니다. 어떤 방법을 선택하더라도 취소는 즉시 발생하지 않습니다. 작업 또는 작업 그룹이 취소 된 경우 새 작업이 시작 되지 않지만 활성 작업에서 취소를 확인 하 고 취소에 응답 해야 합니다.

병렬 작업을 취소 하는 더 많은 예제를 보려면 [연습: 작업 및 XML HTTP 요청을 사용 하 여 연결](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [방법: 취소를 사용 하 여 병렬 루프 중단](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)및 [방법: 예외 처리를 사용 하 여 병렬 루프 중단](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)을 참조 하세요.

### <a name="using-a-cancellation-token-to-cancel-parallel-work"></a><a name="tokens"></a> 취소 토큰을 사용 하 여 병렬 작업 취소

`task`, `task_group` 및 `structured_task_group` 클래스는 취소 토큰을 사용하는 방법으로 취소 기능을 지원합니다. PPL은 이러한 용도로 [concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) 및 [concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) 클래스를 정의 합니다. 취소 토큰을 사용하여 작업을 취소하면 런타임에서 해당 토큰을 구독하는 새 작업을 시작하지 않습니다. 이미 활성화 된 작업은 [is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) 멤버 함수를 사용 하 여 취소 토큰을 모니터링 하 고 가능한 경우 중지할 수 있습니다.

취소를 시작 하려면 [concurrency:: cancellation_token_source:: cancel](reference/cancellation-token-source-class.md#cancel) 메서드를 호출 합니다. 다음 방법으로 취소에 응답합니다.

- 개체의 경우 `task` [concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) 함수를 사용 합니다. `cancel_current_task`는 현재 작업 및 모든 값 기반 연속을 취소합니다. 작업 또는 해당 연속에 연결 된 취소 *토큰* 은 취소 하지 않습니다.

- 작업 그룹 및 병렬 알고리즘의 경우 [concurrency:: is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) 함수를 사용 하 여 취소를 감지 하 고이 함수가 반환 될 때 작업 본문에서 가능한 한 빨리 반환 **`true`** 합니다. (작업 그룹에서 `cancel_current_task`를 호출하지 마세요.)

다음 예제에서는 작업 취소의 첫 번째 기본 패턴을 보여 줍니다. 작업 본문에서는 때때로 루프 내부에 취소가 있는지 확인합니다.

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

`cancel_current_task` 함수가 throw하므로 현재 루프 또는 함수에서 명시적으로 반환할 필요가 없습니다.

> [!TIP]
> 또는 대신 [concurrency:: interruption_point](reference/concurrency-namespace-functions.md#interruption_point) 함수를 호출할 수 있습니다 `cancel_current_task` .

작업을 취소됨 상태로 전환하므로 취소에 응답할 때 `cancel_current_task`를 호출해야 합니다. `cancel_current_task`를 호출하지 않고 조기에 반환하는 경우 작업이 완료됨 상태로 전환되고 값 기반 연속이 실행됩니다.

> [!CAUTION]
> 코드에서 `task_canceled`를 throw하지 마세요. 대신 `cancel_current_task`를 호출하세요.

작업이 취소 됨 상태로 종료 되 면 [concurrency:: task:: get](reference/task-class.md#get) 메서드는 [concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md)을 throw 합니다. 반대로 [concurrency:: task:: wait](reference/task-class.md#wait) 는 [task_status:: canceled](reference/concurrency-namespace-enums.md#task_group_status) 를 반환 하 고을 throw 하지 않습니다.) 다음 예제에서는 작업 기반 연속에 대 한이 동작을 보여 줍니다. 작업 기반 연속은 선행 작업이 취소되어도 항상 호출됩니다.

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

값 기반 연속은 명시적 토큰을 사용하여 생성된 경우가 아니면 선행 작업의 토큰을 상속하므로 선행 작업이 실행 중이어도 연속이 즉시 취소됨 상태로 전환됩니다. 따라서 취소 후에 선행 작업에서 throw되는 예외는 연속 작업에 전파되지 않습니다. 취소는 항상 선행 작업의 상태를 재정의합니다. 다음 예제는 이전 예제와 비슷하지만 값 기반 연속에 대한 동작을 보여 줍니다.

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> 취소 토큰을 `task` 생성자 또는 [concurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) 함수에 전달 하지 않으면 해당 작업은 취소 가능한 되지 않습니다. 또한 모든 작업을 동시에 취소하려면 중첩된 작업(다른 작업의 본문 내에 생성된 작업)의 생성자에 같은 취소 토큰을 전달해야 합니다.

취소 토큰이 취소될 때 임의의 코드를 실행해야 할 수 있습니다. 예를 들어 사용자가 사용자 인터페이스에서 **취소** 단추를 선택 하 여 작업을 취소 하는 경우 사용자가 다른 작업을 시작할 때까지 해당 단추를 사용 하지 않도록 설정할 수 있습니다. 다음 예제에서는 [concurrency:: cancellation_token:: register_callback](reference/cancellation-token-class.md#register_callback) 메서드를 사용 하 여 취소 토큰이 취소 될 때 실행 되는 콜백 함수를 등록 하는 방법을 보여 줍니다.

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

문서 [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md) 는 값 기반 및 작업 기반 연속 간의 차이점을 설명 합니다. `cancellation_token` 개체를 연속 작업에 제공하지 않으면 연속은 다음 방법으로 선행 작업에서 취소 토큰을 상속합니다.

- 값 기반 연속은 항상 선행 작업의 취소 토큰을 상속합니다.

- 작업 기반 연속은 항상 선행 작업의 취소 토큰을 상속하지 않습니다. 작업 기반 연속을 취소 가능하도록 설정하는 유일한 방법은 취소 토큰을 명시적으로 전달하는 것입니다.

결함이 있는 작업(예외를 throw하는 작업)은 이들 동작에 영향을 미치지 않습니다. 이 경우 값 기반 연속이 취소 됩니다. 작업 기반 연속은 취소 되지 않습니다.

> [!CAUTION]
> 다른 작업에서 생성된 작업(중첩된 작업)은 부모 작업의 취소 토큰을 상속하지 않습니다. 값 기반 연속만 선행 작업의 취소 토큰을 상속합니다.

> [!TIP]
> 개체를 사용 하는 생성자 또는 함수를 호출 하 고 작업을 취소 가능한 하지 않으려면 [concurrency:: cancellation_token:: none](reference/cancellation-token-class.md#none) 메서드를 사용 `cancellation_token` 합니다.

`task_group` 또는 `structured_task_group` 개체의 생성자에 취소 토큰을 제공할 수도 있습니다. 이 방법의 중요한 측면은 자식 작업 그룹이 이 취소 토큰을 상속한다는 점입니다. 를 호출 하기 위해를 실행 하는 [concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) 함수를 사용 하 여이 개념을 보여 주는 예제는 `parallel_for` 이 문서의 뒷부분에 나오는 [병렬 알고리즘 취소](#algorithms) 를 참조 하세요.

[[맨 위로](#top)이동]

#### <a name="cancellation-tokens-and-task-composition"></a>취소 토큰 및 작업 컴퍼지션

[Concurrency:: when_all](reference/concurrency-namespace-functions.md#when_all) 및 [concurrency:: when_any](reference/concurrency-namespace-functions.md#when_all) 함수는 여러 작업을 구성 하 여 공통 패턴을 구현 하는 데 도움이 될 수 있습니다. 이 섹션에서는 이들 함수에서 취소 토큰을 사용하는 방법을 보여 줍니다.

및 함수에 취소 토큰을 제공 하는 `when_all` 경우 `when_any` 해당 함수는 취소 토큰이 취소 되거나 참가자 작업 중 하나가 취소 된 상태로 끝나거나 예외를 throw 하는 경우에만 취소 됩니다.

`when_all` 함수는 취소 토큰을 제공하지 않을 경우 전체 작업을 구성하는 각 작업에서 취소 토큰을 상속합니다. 에서 반환 되는 작업은 `when_all` 이러한 토큰 중 하나라도 취소 되 고 참가자 작업 중 하나 이상이 아직 시작 되지 않았거나 실행 되 고 있지 않을 때 취소 됩니다. 작업 중 하나가 예외를 throw 하는 경우에도 비슷한 동작이 발생 합니다 .에서 반환 되는 작업은 `when_all` 해당 예외와 함께 즉시 취소 됩니다.

런타임에서는 해당 작업이 완료될 때 `when_any` 함수에서 반환되는 작업에 대한 취소 토큰을 선택합니다. 완료됨 상태로 종료된 참가 작업이 없거나 하나 이상의 작업이 예외를 throw하면 throw된 작업의 하나가 `when_any`를 완료하기 위해 선택되고 해당 토큰이 최종 작업의 토큰으로 선택됩니다. 완료됨 상태로 종료된 작업이 두 개 이상이면 `when_any` 작업에서 반환된 작업이 완료됨 상태로 끝납니다. 다른 실행 중인 작업이 나중에 완료되더라도 `when_any`에서 반환된 작업이 즉시 취소되지 않도록 런타임에서는 완료 시 토큰이 취소되지 않은 완료된 작업을 선택하려고 시도합니다.

[[맨 위로](#top)이동]

### <a name="using-the-cancel-method-to-cancel-parallel-work"></a><a name="cancel"></a> Cancel 메서드를 사용 하 여 병렬 작업 취소

[Concurrency:: task_group:: cancel](reference/task-group-class.md#cancel) 및 [concurrency:: structured_task_group:: cancel](reference/structured-task-group-class.md#cancel) 메서드는 작업 그룹을 취소 됨 상태로 설정 합니다. `cancel`이 호출되고 나면 작업 그룹이 미래 작업을 시작하지 않습니다. `cancel` 메서드는 여러 자식 작업을 통해 호출할 수 있습니다. 취소 된 작업을 수행 하면 concurrency [:: task_group:: wait](reference/task-group-class.md#wait) 및 [concurrency:: structured_task_group:: wait](reference/structured-task-group-class.md#wait) 메서드가 [concurrency:: canceled](reference/concurrency-namespace-enums.md#task_group_status)를 반환 합니다.

작업 그룹이 취소 되 면 각 자식 작업에서 런타임에 대 한 호출이 *중단 지점을* 트리거할 수 있습니다. 그러면 런타임에서 내부 예외 형식을 throw 하 고 catch 하 여 활성 작업을 취소 합니다. 동시성 런타임은 특정 중단 지점을 정의하지 않고 런타임에 대한 호출에서 발생할 수 없습니다. 런타임에서는 취소를 수행하기 위해 throw할 예외를 처리해야 합니다. 따라서 작업 본문에서 알 수 없는 예외를 처리하지 마세요.

자식 작업은 시간이 오래 걸리는 작업을 수행하지만 런타임으로 호출하지 않을 경우 주기적으로 취소를 확인하고 시기적절하게 종료되어야 합니다. 다음 예제에서는 작업이 취소되는 시기를 결정하는 한 가지 방법을 보여 줍니다. `t4` 작업은 오류가 발생할 때 부모 작업 그룹을 취소합니다. `t5` 작업은 때때로 `structured_task_group::is_canceling` 메서드를 호출하여 취소가 있는지 확인합니다. 부모 작업 그룹이 취소되면 `t5` 작업은 메시지를 인쇄하고 종료됩니다.

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

이 예에서는 작업 루프의 100<sup>번째</sup> 반복 마다 취소를 확인 합니다. 취소를 확인하는 빈도는 수행하는 작업량 및 작업이 취소에 응답해야 하는 속도에 따라 달라집니다.

부모 작업 그룹 개체에 대 한 액세스 권한이 없는 경우 [concurrency:: is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) 함수를 호출 하 여 부모 작업 그룹이 취소 되었는지 여부를 확인 합니다.

`cancel` 메서드는 자식 작업에만 영향을 미칩니다. 예를 들어 병렬 작업 트리 그림에서 작업 그룹 `tg1`을 취소하면 트리의 모든 작업(`t1`, `t2`, `t3`, `t4` 및 `t5`)이 영향을 받습니다. 중첩된 작업 그룹 `tg2`를 취소하면 `t4` 및 `t5` 작업만 영향을 받습니다.

`cancel` 메서드를 호출하면 모든 자식 작업 그룹도 취소됩니다. 그러나 취소는 병렬 작업 트리에 있는 작업 그룹의 모든 부모에 영향을 미치지 않습니다. 다음 예제에서는 병렬 작업 트리 그룹에서 빌드하는 방식으로 이를 보여 줍니다.

이들 예제의 첫 번째에서는 작업 그룹 `tg2`의 자식인 `t4` 작업에 대한 작업 함수를 만듭니다. 작업 함수는 루프에서 `work` 함수를 호출합니다. `work`에 대한 호출에 실패하면 작업에서 해당 부모 작업 그룹이 취소됩니다. 이로 인해 작업 그룹 `tg2`가 취소됨 상태로 전환되지만 작업 그룹 `tg1`은 취소되지 않습니다.

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

이 두 번째 예제는 작업에서 작업 그룹 `tg1`을 취소한다는 점을 제외하고 첫 번째 예제와 비슷합니다. 이는 트리의 모든 작업(`t1`, `t2`, `t3`, `t4` 및 `t5`)에 영향을 미칩니다.

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

`structured_task_group` 클래스는 스레드로부터 안전하지 않습니다 따라서 부모 `structured_task_group` 개체의 메서드를 호출하는 자식 작업에서는 지정되지 않은 동작이 생성됩니다. 이 규칙의 예외는 `structured_task_group::cancel` 및 [concurrency:: structured_task_group:: is_canceling](reference/structured-task-group-class.md#is_canceling) 메서드입니다. 자식 작업에서는 이들 메서드를 호출하여 부모 작업 그룹을 취소하고 취소가 있는지 확인할 수 있습니다.

> [!CAUTION]
> 취소 토큰을 사용하여 `task` 개체의 자식으로 실행되는 작업 그룹에서 수행되는 작업을 취소할 수 있지만 `task_group::cancel` 또는 `structured_task_group::cancel` 메서드를 사용하여 작업 그룹에서 실행되는 `task` 개체를 취소할 수는 없습니다.

[[맨 위로](#top)이동]

### <a name="using-exceptions-to-cancel-parallel-work"></a><a name="exceptions"></a> 예외를 사용 하 여 병렬 작업 취소

병렬 작업 트리를 취소할 때 취소 토큰 및 `cancel` 메서드를 사용하는 것이 예외 처리보다 더 효율적입니다. 취소 토큰 및 `cancel` 메서드는 하향식으로 작업과 모든 자식 작업을 취소합니다. 반대로 예외 처리는 상향식으로 작동하고 예외가 위쪽으로 전파될 때 각 자식 작업 그룹을 개별적으로 취소해야 합니다. [예외 처리](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) 항목에서는 동시성 런타임에서 예외를 사용 하 여 오류를 전달 하는 방법을 설명 합니다. 그러나 일부 예외는 오류를 나타내지 않습니다. 예를 들어 검색 알고리즘에서는 결과를 발견하면 연결된 작업을 취소할 수 있습니다. 하지만 앞에서 설명한 대로 예외 처리는 `cancel` 메서드를 사용하여 병렬 작업을 취소하는 방법보다 덜 효율적입니다.

> [!CAUTION]
> 필요한 경우에만 예외를 사용하여 병렬 작업을 취소하는 것이 좋습니다. 취소 토큰 및 작업 그룹 `cancel` 메서드는 더 효율적이고 오류가 발생할 가능성이 감소합니다.

작업 그룹에 전달하는 작업 함수의 본문에서 예외를 throw하면 런타임에서는 해당 예외를 저장하고 작업 그룹이 완료되기를 기다리는 컨텍스트에 해당 예외를 마샬링합니다. `cancel` 메서드처럼 런타임에서는 아직 시작되지 않은 모든 작업을 무시하고 새 작업을 수락하지 않습니다.

이 세 번째 예제는 작업 `t4`가 예외를 throw하여 작업 그룹 `tg2`를 취소한다는 점을 제외하고 두 번째 예제와 비슷합니다. 이 예제에서는 블록을 사용 하 여 **`try`** - **`catch`** 작업 그룹이 자식 작업이 완료 될 때까지 대기 하는 경우 취소를 확인 `tg2` 합니다. 첫 번째 예제처럼 이로 인해 작업 그룹 `tg2`가 취소됨 상태로 전환되지만 작업 그룹 `tg1`은 취소되지 않습니다.

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

네 번째 예제에서는 예외 처리를 사용하여 전체 작업 트리를 취소합니다. 예제에서는 작업 그룹 `tg2`가 자식 작업을 기다릴 때가 아니라 작업 그룹 `tg1`이 자식 작업이 완료되기를 기다릴 때 예외를 catch합니다. 두 번째 예제처럼 이로 인해 트리의 두 작업 그룹 `tg1` 및 `tg2`는 모두 취소됨 상태로 전환됩니다.

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

`task_group::wait` 및 `structured_task_group::wait` 메서드는 자식 작업이 예외를 throw할 때 throw하므로 이들 메서드에서 반환 값을 받을 수 없습니다.

[[맨 위로](#top)이동]

## <a name="canceling-parallel-algorithms"></a><a name="algorithms"></a> 병렬 알고리즘 취소

PPL의 병렬 알고리즘(예: `parallel_for`)은 작업 그룹에 빌드됩니다. 따라서 대부분 같은 방법을 사용하여 병렬 알고리즘을 취소할 수 있습니다.

다음 예제에서는 병렬 알고리즘을 취소하는 여러 가지 방법을 보여 줍니다.

다음 예제에서는 `run_with_cancellation_token` 함수를 사용하여 `parallel_for` 알고리즘을 호출합니다. `run_with_cancellation_token` 함수는 취소 토큰을 인수로 사용하고 제공된 작업 함수를 동기적으로 호출합니다. 병렬 알고리즘은 작업에 빌드되므로 부모 작업의 취소 토큰을 상속합니다. 따라서 `parallel_for`가 취소에 응답할 수 있습니다.

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

다음 예제에서는 [concurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait) 메서드를 사용 하 여 알고리즘을 호출 합니다 `parallel_for` . `structured_task_group::run_and_wait` 메서드는 제공된 작업이 완료되기를 기다립니다. `structured_task_group` 개체를 사용하면 작업 함수가 작업을 취소할 수 있습니다.

[!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
The task group status is: canceled.
```

다음 예제에서는 예외 처리를 사용하여 `parallel_for` 루프를 취소합니다. 런타임에서는 예외를 호출하는 컨텍스트에 마샬링합니다.

[!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
Caught 50
```

다음 예제에서는 부울 플래그를 사용하여 `parallel_for` 루프에서 취소를 조정합니다. 이 예제에서는 전체 작업 집합을 취소하는 데 `cancel` 메서드나 예외 처리를 사용하지 않으므로 모든 작업이 실행됩니다. 따라서 이 방법에서는 취소 메커니즘보다 더 계산적인 오버헤드가 발생할 수 있습니다.

[!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]

각 취소 방법에는 다른 방법에 비해 장점이 있습니다. 특정 요구 사항에 맞는 방법을 선택하세요.

[[맨 위로](#top)이동]

## <a name="when-not-to-use-cancellation"></a><a name="when"></a> 취소를 사용 하지 않는 경우

관련 작업 그룹의 각 멤버가 시기적절하게 종료될 수 있으면 취소를 사용하는 것이 좋습니다. 그러나 애플리케이션에 대해 취소가 적절하지 않을 수 있는 몇 가지 시나리오가 있습니다. 예를 들어 작업 취소는 공동 작업이므로 개별 작업이 차단된 경우에도 전체 작업 집합은 취소되지 않습니다. 예를 들어 한 작업이 아직 시작되지 않았지만 이 작업이 다른 활성 작업을 차단 해제할 경우 작업 그룹이 취소되면 이 작업은 시작되지 않습니다. 이로 인해 애플리케이션에서 교착 상태가 발생할 수 있습니다. 취소 사용이 적절하지 않을 수 있는 두 번째 예는 작업이 취소되지만 자식 작업이 리소스 해제와 같은 중요한 작업을 수행하는 경우입니다. 전체 작업 집합은 부모 작업이 취소될 때 취소되므로 해당 작업이 실행되지 않습니다. 이 점을 보여 주는 예제는 병렬 패턴 라이브러리의 모범 사례 항목에서 [취소 및 예외 처리가 개체 소멸에 미치는 영향 이해](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) 섹션을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[방법: 취소를 사용 하 여 병렬 루프 중단](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|취소를 사용하여 병렬 검색 알고리즘을 구현하는 방법을 보여 줍니다.|
|[방법: 예외 처리를 사용 하 여 병렬 루프 중단](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|`task_group` 클래스를 사용하여 기본적인 트리 구조에 대한 검색 알고리즘을 작성하는 방법을 보여 줍니다.|
|[예외 처리](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|작업 그룹, 간단한 작업 및 비동기 에이전트에서 throw한 예외를 런타임에서 처리하는 방법 및 애플리케이션에 예외에 응답하는 방법을 설명합니다.|
|[작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|작업이 작업 그룹과 관련되는 방식 및 애플리케이션에서 구조화되지 않은 작업과 구조화된 작업을 사용하는 방법을 설명합니다.|
|[병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)|데이터 컬렉션에 대한 작업을 동시에 수행하는 병렬 알고리즘을 설명합니다.|
|[PPL(병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md)|병렬 패턴 라이브러리에 대해 간략하게 설명합니다.|

## <a name="reference"></a>참조

[작업 클래스 (동시성 런타임)](../../parallel/concrt/reference/task-class.md)

[cancellation_token_source 클래스](../../parallel/concrt/reference/cancellation-token-source-class.md)

[cancellation_token 클래스](../../parallel/concrt/reference/cancellation-token-class.md)

[task_group 클래스](reference/task-group-class.md)

[structured_task_group 클래스](../../parallel/concrt/reference/structured-task-group-class.md)

[parallel_for 함수](reference/concurrency-namespace-functions.md#parallel_for)
