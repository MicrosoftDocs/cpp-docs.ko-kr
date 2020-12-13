---
description: '자세한 정보: 연습: 데이터 흐름 에이전트 만들기'
title: '연습: 데이터 흐름 에이전트 만들기'
ms.date: 04/25/2019
helpviewer_keywords:
- creating dataflow agents [Concurrency Runtime]
- dataflow agents, creating [Concurrency Runtime]
ms.assetid: 9db5ce3f-c51b-4de1-b79b-9ac2a0cbd130
ms.openlocfilehash: 2f7f2435d5a4ede1dd48a4dee672ed7affbdfd9f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163862"
---
# <a name="walkthrough-creating-a-dataflow-agent"></a>연습: 데이터 흐름 에이전트 만들기

이 문서에서는 제어 흐름 대신 데이터 흐름을 기반으로 하는 에이전트 기반 응용 프로그램을 만드는 방법을 보여 줍니다.

*제어 흐름* 은 프로그램의 작업 실행 순서를 나타냅니다. 제어 흐름은 조건문, 루프 등의 제어 구조를 사용 하 여 규제 됩니다. 또는 데이터 *흐름* 은 필요한 모든 데이터를 사용할 수 있는 경우에만 계산을 수행 하는 프로그래밍 모델을 나타냅니다. 데이터 흐름 프로그래밍 모델은 프로그램의 독립적인 구성 요소가 메시지를 전송 하 여 서로 통신 하는 메시지 전달 개념과 관련이 있습니다.

비동기 에이전트는 제어 흐름 및 데이터 흐름 프로그래밍 모델을 모두 지원 합니다. 대부분의 경우에는 제어 흐름 모델이 적합 하지만 데이터 흐름 모델은 에이전트에서 데이터를 수신 하 고 해당 데이터의 페이로드를 기반으로 하는 작업을 수행 하는 경우 등에 적합 합니다.

## <a name="prerequisites"></a>사전 요구 사항

이 연습을 시작 하기 전에 다음 문서를 읽어 보세요.

- [비동기 에이전트](../../parallel/concrt/asynchronous-agents.md)

- [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)

- [방법: 메시지 블록 필터 사용](../../parallel/concrt/how-to-use-a-message-block-filter.md)

## <a name="sections"></a><a name="top"></a> 섹션이

이 연습에는 다음과 같은 섹션이 있습니다.

- [기본 Control-Flow 에이전트 만들기](#control-flow)

- [기본 데이터 흐름 에이전트 만들기](#dataflow)

- [Message-Logging 에이전트 만들기](#logging)

## <a name="creating-a-basic-control-flow-agent"></a><a name="control-flow"></a> 기본 Control-Flow 에이전트 만들기

클래스를 정의 하는 다음 예제를 참조 `control_flow_agent` 하세요. `control_flow_agent`클래스는 세 개의 메시지 버퍼 (하나의 입력 버퍼와 두 개의 출력 버퍼)에서 작동 합니다. `run`메서드는 루프에서 소스 메시지 버퍼를 읽고 조건문을 사용 하 여 프로그램 실행 흐름을 지시 합니다. 에이전트는 0이 아닌 값에 대해 카운터 하나를 증가 시키고 0이 아닌 양수 값에 대해 다른 카운터를 증가 시킵니다. 에이전트가 센티널 값 0을 받은 후에는 카운터의 값을 출력 메시지 버퍼로 보냅니다. `negatives`및 `positives` 메서드를 사용 하면 응용 프로그램에서 에이전트의 음수 및 양수 값의 개수를 읽을 수 있습니다.

[!code-cpp[concrt-dataflow-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_1.cpp)]

이 예에서는 에이전트에서 제어 흐름의 기본 사용을 설정 하지만 제어 흐름 기반 프로그래밍의 직렬 특성을 보여 줍니다. 입력 메시지 버퍼에서 여러 메시지를 사용할 수 있는 경우에도 각 메시지는 순차적으로 처리 되어야 합니다. 데이터 흐름 모델을 사용 하면 조건문의 두 분기가 동시에 평가 됩니다. 데이터 흐름 모델을 사용 하면 데이터를 사용할 수 있게 되 면 데이터에 대해 작동 하는 더 복잡 한 메시징 네트워크를 만들 수도 있습니다.

[[맨 위로](#top)이동]

## <a name="creating-a-basic-dataflow-agent"></a><a name="dataflow"></a> 기본 데이터 흐름 에이전트 만들기

이 섹션에서는 `control_flow_agent` 데이터 흐름 모델을 사용 하 여 동일한 작업을 수행 하도록 클래스를 변환 하는 방법을 보여 줍니다.

데이터 흐름 에이전트는 각각 특정 용도로 사용 되는 메시지 버퍼의 네트워크를 만들어 작동 합니다. 특정 메시지 블록은 필터 함수를 사용 하 여 페이로드를 기준으로 메시지를 수락 하거나 거부 합니다. Filter 함수는 메시지 블록이 특정 값만 받도록 합니다.

#### <a name="to-convert-the-control-flow-agent-to-a-dataflow-agent"></a>제어 흐름 에이전트를 데이터 흐름 에이전트로 변환 하려면

1. 클래스의 본문을 `control_flow_agent` 다른 클래스 (예:)에 복사 `dataflow_agent` 합니다. 또는 클래스의 이름을 바꿀 수 있습니다 `control_flow_agent` .

1. 메서드에서를 호출 하는 루프의 본문을 제거 `receive` `run` 합니다.

[!code-cpp[concrt-dataflow-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_2.cpp)]

1. `run`메서드에서 및 변수를 초기화 한 후 `negative_count` `positive_count` `countdown_event` 활성 작업의 수를 추적 하는 개체를 추가 합니다.

[!code-cpp[concrt-dataflow-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_3.cpp)]

   `countdown_event`클래스는이 항목의 뒷부분에 나와 있습니다.

1. 데이터 흐름 네트워크에 참여 하는 메시지 버퍼 개체를 만듭니다.

[!code-cpp[concrt-dataflow-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_4.cpp)]

1. 메시지 버퍼를 연결 하 여 네트워크를 구성 합니다.

[!code-cpp[concrt-dataflow-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_5.cpp)]

1. `event`및 `countdown event` 개체가 설정 될 때까지 기다립니다. 이러한 이벤트는 에이전트가 센티널 값을 받고 모든 작업이 완료 되었음을 신호로 알립니다.

[!code-cpp[concrt-dataflow-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_6.cpp)]

다음 다이어그램에서는 클래스의 전체 데이터 흐름 네트워크를 보여 줍니다 `dataflow_agent` .

![데이터 흐름 네트워크](../../parallel/concrt/media/concrt_dataflow.png "데이터 흐름 네트워크")

다음 표에서는 네트워크의 멤버를 설명합니다.

|멤버|설명|
|------------|-----------------|
|`increment_active`|활성 이벤트 카운터를 증가 시키고 입력 값을 네트워크의 나머지 부분에 전달 하는 [concurrency:: 변환기](../../parallel/concrt/reference/transformer-class.md) 개체입니다.|
|`negatives`, `positives`|[concurrency::](../../parallel/concrt/reference/call-class.md) 숫자의 수를 늘리고 활성 이벤트 카운터를 감소 시키는 개체를 호출 합니다. 각각의 개체는 필터를 사용 하 여 음수 또는 양수를 허용 합니다.|
|`sentinel`|센티널 값 0만 허용 하 고 활성 이벤트 카운터를 감소 시키는 [concurrency:: call](../../parallel/concrt/reference/call-class.md) 개체입니다.|
|`connector`|원본 메시지 버퍼를 내부 네트워크에 연결 하는 [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) 개체입니다.|

메서드는 `run` 별도의 스레드에서 호출 되기 때문에 네트워크가 완전히 연결 되기 전에 다른 스레드에서 네트워크에 메시지를 보낼 수 있습니다. `_source`데이터 멤버는 `unbounded_buffer` 응용 프로그램에서 에이전트로 전송 되는 모든 입력을 버퍼링 하는 개체입니다. 네트워크에서 모든 입력 메시지를 처리 하는지 확인 하기 위해 에이전트는 먼저 네트워크의 내부 노드를 연결 하 고 해당 네트워크의 시작을 `connector` 데이터 멤버에 연결 합니다 `_source` . 그러면 네트워크가 구성 될 때 메시지가 처리 되지 않습니다.

이 예제의 네트워크는 제어 흐름이 아닌 데이터 흐름을 기반으로 하기 때문에 네트워크는 각 입력 값의 처리를 완료 하 고 센티널 노드가 해당 값을 받았음을 에이전트와 통신 해야 합니다. 이 예제에서는 개체를 사용 하 여 `countdown_event` 모든 입력 값이 처리 되었음을 알리고, [concurrency:: event](../../parallel/concrt/reference/event-class.md) 개체를 사용 하 여 센티널 노드가 해당 값을 받았음을 표시 합니다. `countdown_event`클래스는 `event` 카운터 값이 0에 도달할 때 신호를 보내는 개체를 사용 합니다. 데이터 흐름 네트워크의 헤드는 값을 받을 때마다 카운터를 증가 시킵니다. 네트워크의 모든 터미널 노드는 입력 값을 처리 한 후 카운터를 감소 시킵니다. 에이전트는 데이터 흐름 네트워크를 구성 하 고 나면 센티널 노드가 개체를 설정 하 `event` 고 `countdown_event` 개체가 카운터가 0에 도달 했음을 알리기 위해 대기 합니다.

다음 예제에서는 `control_flow_agent` , 및 클래스를 보여 줍니다 `dataflow_agent` `countdown_event` . `wmain`함수는 `control_flow_agent` 및 개체를 만들고 `dataflow_agent` 함수를 사용 하 여 `send_values` 일련의 난수 값을 에이전트로 보냅니다.

[!code-cpp[concrt-dataflow-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_7.cpp)]

이 예제에서는 다음과 같은 샘플 출력을 생성 합니다.

```Output
Control-flow agent:
There are 500523 negative numbers.
There are 499477 positive numbers.
Dataflow agent:
There are 500523 negative numbers.
There are 499477 positive numbers.
```

### <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `dataflow-agent.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

**cl.exe/EHsc dataflow-agent**

[[맨 위로](#top)이동]

## <a name="creating-a-message-logging-agent"></a><a name="logging"></a> Message-Logging 에이전트 만들기

다음 예제에서는 클래스를 보여 줍니다. 클래스는 `log_agent` 클래스와 유사 합니다 `dataflow_agent` . `log_agent`클래스는 로그 메시지를 파일 및 콘솔에 기록 하는 비동기 로깅 에이전트를 구현 합니다. `log_agent`클래스를 사용 하면 응용 프로그램에서 메시지를 정보, 경고 또는 오류로 분류할 수 있습니다. 또한 응용 프로그램에서 각 로그 범주를 파일, 콘솔 또는 둘 다에 쓸지 여부를 지정할 수 있습니다. 이 예제에서는 모든 로그 메시지를 파일에 기록 하 고 오류 메시지만 콘솔에 기록 합니다.

[!code-cpp[concrt-log-filter#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_8.cpp)]

이 예제에서는 콘솔에 다음 출력을 기록 합니다.

```Output
error: This is a sample error message.
```

또한이 예제에서는 다음 텍스트를 포함 하는 log.txt 파일을 생성 합니다.

```Output
info: ===Logging started.===
warning: This is a sample warning message.
error: This is a sample error message.
info: ===Logging finished.===
```

### <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `log-filter.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

**cl.exe/EHsc log-filter**

[[맨 위로](#top)이동]

## <a name="see-also"></a>참고 항목

[동시성 런타임 연습](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
