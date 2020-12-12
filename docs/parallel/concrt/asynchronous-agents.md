---
description: '자세한 정보: 비동기 에이전트'
title: 비동기 에이전트
ms.date: 11/19/2018
helpviewer_keywords:
- asynchronous agents
- agents [Concurrency Runtime]
ms.assetid: 6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a
ms.openlocfilehash: 38d2325404d83443ed0bd054793ca200a562359f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338295"
---
# <a name="asynchronous-agents"></a>비동기 에이전트

*비동기 에이전트* 또는 just-in-time *에이전트* 는 다른 에이전트와 비동기 방식으로 작동 하 여 더 큰 컴퓨팅 작업을 해결 하는 응용 프로그램 구성 요소입니다. 에이전트는 설정 된 수명 주기를 가진 태스크로 간주 합니다. 예를 들어 한 에이전트는 입력/출력 장치 (예: 키보드, 디스크의 파일 또는 네트워크 연결)에서 데이터를 읽을 수 있으며, 다른 에이전트는 해당 데이터를 사용할 수 있게 되 면 해당 데이터에 대 한 작업을 수행할 수 있습니다. 첫 번째 에이전트는 메시지 전달을 사용 하 여 두 번째 에이전트에 더 많은 데이터를 사용할 수 있음을 알립니다. 동시성 런타임 작업 스케줄러를 사용 하면 효율적인 선점 없이도 에이전트가 협조적으로 차단 하 고 양보할 수 있습니다.

에이전트 라이브러리는 [concurrency:: agent](../../parallel/concrt/reference/agent-class.md) 클래스를 정의 하 여 비동기 에이전트를 나타냅니다. `agent` 는 가상 메서드 [concurrency:: agent:: run](reference/agent-class.md#run)을 선언 하는 추상 클래스입니다. `run`메서드는 에이전트가 수행 하는 작업을 실행 합니다. `run`는 추상 이므로에서 파생 되는 모든 클래스에서이 메서드를 구현 해야 합니다 `agent` .

## <a name="agent-life-cycle"></a>에이전트 수명 주기

에이전트에는 설정 된 수명 주기가 있습니다. [Concurrency:: agent_status](reference/concurrency-namespace-enums.md#agent_status) 열거형은 에이전트의 다양 한 상태를 정의 합니다. 다음 그림은 에이전트가 한 상태에서 다른 상태로 진행 되는 방식을 보여 주는 상태 다이어그램입니다. 이 그림에서 실선은 응용 프로그램에서 호출 하는 메서드를 나타냅니다. 점선은 런타임에서 호출 되는 메서드를 나타냅니다.

![에이전트 상태 다이어그램](../../parallel/concrt/media/agentstate.png "에이전트 상태 다이어그램")

다음 표에서는 열거형의 각 상태에 대해 설명 합니다 `agent_status` .

|에이전트 상태|설명|
|-----------------|-----------------|
|`agent_created`|에이전트의 실행이 예약 되어 있지 않습니다.|
|`agent_runnable`|런타임에서 실행을 위해 에이전트를 예약 하 고 있습니다.|
|`agent_started`|에이전트가 시작 되었으며 실행 되 고 있습니다.|
|`agent_done`|에이전트가 완료 되었습니다.|
|`agent_canceled`|에이전트가 상태를 입력 하기 전에 취소 되었습니다 `started` .|

`agent_created` 는 에이전트의 초기 상태 `agent_runnable` 이며 `agent_started` 활성 상태 이며 `agent_done` 및 `agent_canceled` 는 터미널 상태입니다.

[Concurrency:: agent:: status](reference/agent-class.md#status) 메서드를 사용 하 여 개체의 현재 상태를 검색 `agent` 합니다. 메서드는 `status` 동시성이 안전 하지만 에이전트 상태는 메서드가 반환 하는 시간에 따라 변경 될 수 있습니다 `status` . 예를 들어, `agent_started` 메서드를 호출할 때 에이전트가 상태가 될 수 `status` 있지만 `agent_done` 메서드가 반환 된 후의 상태로 이동 될 수 있습니다 `status` .

## <a name="methods-and-features"></a>메서드 및 기능

다음 표에서는 클래스에 속하는 몇 가지 중요 한 메서드를 보여 줍니다 `agent` . 모든 클래스 메서드에 대 한 자세한 내용은 `agent` [에이전트 클래스](../../parallel/concrt/reference/agent-class.md)를 참조 하세요.

|메서드|설명|
|------------|-----------------|
|[start](reference/agent-class.md#start)|개체의 `agent` 실행을 예약 하 고 `agent_runnable` 상태로 설정 합니다.|
|[실행할지](reference/agent-class.md#run)|개체에서 수행할 작업을 실행 합니다 `agent` .|
|[완료](reference/agent-class.md#done)|에이전트를 `agent_done` 상태로 이동 합니다.|
|[cancel](../../parallel/concrt/cancellation-in-the-ppl.md#cancel)|에이전트가 시작 되지 않은 경우이 메서드는 에이전트의 실행을 취소 하 고 `agent_canceled` 상태로 설정 합니다.|
|[status](reference/agent-class.md#status)|개체의 현재 상태를 검색 `agent` 합니다.|
|[대기한](reference/agent-class.md#wait)|`agent`개체가 또는 상태가 될 때까지 기다립니다 `agent_done` `agent_canceled` .|
|[wait_for_all](reference/agent-class.md#wait_for_all)|제공 된 모든 `agent` 개체가 또는 상태로 전환 될 때까지 기다립니다 `agent_done` `agent_canceled` .|
|[wait_for_one](reference/agent-class.md#wait_for_one)|제공 된 개체 중 하나 이상이 `agent` 또는 상태로 전환 될 때까지 `agent_done` 기다립니다 `agent_canceled` .|

에이전트 개체를 만든 후 [concurrency:: agent:: start](reference/agent-class.md#start) 메서드를 호출 하 여 실행을 예약 합니다. 런타임은 `run` 에이전트를 예약 하 고 상태를 설정 하 고 나면 메서드를 호출 합니다 `agent_runnable` .

런타임에서는 비동기 에이전트에서 throw 되는 예외를 관리 하지 않습니다. 예외 처리 및 에이전트에 대 한 자세한 내용은 [예외 처리](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)를 참조 하세요.

## <a name="example"></a>예제

기본 에이전트 기반 응용 프로그램을 만드는 방법을 보여 주는 예제는 [연습: Agent-Based 응용 프로그램 만들기](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)
