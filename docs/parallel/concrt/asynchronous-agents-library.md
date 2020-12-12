---
description: '자세한 정보: 비동기 에이전트 라이브러리'
title: 비동기 에이전트 라이브러리
ms.date: 11/19/2018
helpviewer_keywords:
- Agents Library
- Asynchronous Agents Library
ms.assetid: d2a72a31-8ba6-4220-ad7a-e403a6acaa42
ms.openlocfilehash: 5d56bd84078d4c1a89fc489fba37edeb03b3739f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338303"
---
# <a name="asynchronous-agents-library"></a>비동기 에이전트 라이브러리

비동기 에이전트 라이브러리 또는 단지 *에이전트 라이브러리* 는 동시성 사용 응용 프로그램 개발의 견고성을 높일 수 있는 프로그래밍 모델을 제공 합니다. 에이전트 라이브러리는 정교 하지 않은 데이터 흐름 및 파이프라인 작업을 위해 행위자 기반 프로그래밍 모델 및 in-process 메시지 전달을 촉진 하는 c + + 템플릿 라이브러리입니다. 에이전트 라이브러리는 동시성 런타임의 일정 및 리소스 관리 구성 요소를 기반으로 합니다.

## <a name="programming-model"></a>프로그래밍 모델

에이전트 라이브러리는 제어 흐름 대신 데이터 흐름을 기반으로 하는 비동기 통신 모델을 통해 격리 된 구성 요소를 연결할 수 있도록 하 여 공유 된 상태에 대 한 대안을 제공 합니다. 데이터 *흐름* 은 필요한 모든 데이터를 사용할 수 있는 경우 계산을 수행 하는 프로그래밍 모델을 나타냅니다. *제어 흐름* 은 계산이 미리 결정 된 순서에 따라 결정 되는 프로그래밍 모델을 나타냅니다.

데이터 흐름 프로그래밍 모델은 프로그램의 개별 구성 요소가 메시지를 전달하여 서로 통신하는 *메시지 전달* 개념과 관련됩니다.

에이전트 라이브러리는 *비동기 에이전트*, *비동기 메시지 블록* 및 *메시지 전달 함수* 의 세 가지 구성 요소로 구성 됩니다. 에이전트는 상태를 유지 관리 하 고 메시지 블록 및 메시지 전달 함수를 사용 하 여 다른 및 외부 구성 요소와 통신 합니다. 메시지 전달 함수를 사용 하면 에이전트가 외부 구성 요소와 메시지를 주고 받을 수 있습니다. 비동기 메시지 블록은 메시지를 저장 하 고 에이전트가 동기화 된 방식으로 통신할 수 있도록 합니다.

다음 그림에서는 두 에이전트에서 메시지 블록 및 메시지 전달 함수를 사용 하 여 통신 하는 방법을 보여 줍니다. 이 그림에서는 `agent1` `agent2` [concurrency:: send](reference/concurrency-namespace-functions.md#send) 함수 및 [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) 개체를 사용 하 여에 메시지를 보냅니다. `agent2` 는 [concurrency:: receive](reference/concurrency-namespace-functions.md#receive) 함수를 사용 하 여 메시지를 읽습니다. `agent2` 는 동일한 메서드를 사용 하 여에 메시지를 보냅니다 `agent1` . 파선 화살표는 에이전트 간 데이터 흐름을 나타냅니다. 실선 화살표는 에이전트를 쓰거나 읽는 메시지 블록에 연결 합니다.

![에이전트 라이브러리의 구성 요소](../../parallel/concrt/media/agent_librarycomp.png "에이전트 라이브러리의 구성 요소")

이 그림을 구현 하는 코드 예제는이 항목의 뒷부분에 나와 있습니다.

에이전트 프로그래밍 모델에는 이벤트와 같은 다른 동시성 및 동기화 메커니즘에 비해 여러 가지 이점이 있습니다. 한 가지 이점은 메시지 전달을 사용 하 여 개체 간의 상태 변경을 전송 하 여 공유 리소스에 대 한 액세스를 격리 하 여 확장성을 향상 시키는 것입니다. 메시지 전달의 이점은 외부 동기화 개체에 연결 하는 대신 데이터에 동기화를 연결 하는 것입니다. 이렇게 하면 구성 요소 간의 데이터 전송을 간소화 하 고 응용 프로그램에서 프로그래밍 오류를 제거할 수 있습니다.

## <a name="when-to-use-the-agents-library"></a>에이전트 라이브러리를 사용 하는 경우

여러 작업이 비동기적으로 서로 통신 해야 하는 경우 에이전트 라이브러리를 사용 합니다. 메시지 블록 및 메시지 전달 함수를 사용 하면 잠금과 같은 동기화 메커니즘을 요구 하지 않고 병렬 응용 프로그램을 작성할 수 있습니다. 이를 통해 응용 프로그램 논리에 집중할 수 있습니다.

에이전트 프로그래밍 모델은 종종 *데이터 파이프라인* 또는 *네트워크* 를 만드는 데 사용 됩니다. 데이터 파이프라인은 각각 더 큰 목표에 기여 하는 특정 작업을 수행 하는 일련의 구성 요소입니다. 데이터 흐름 파이프라인의 모든 구성 요소는 다른 구성 요소에서 메시지를 받을 때 작업을 수행 합니다. 해당 작업의 결과는 파이프라인 또는 네트워크의 다른 구성 요소에 전달 됩니다. 구성 요소는 [PPL (병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md)과 같은 다른 라이브러리의 보다 세분화 된 동시성 기능을 사용할 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는이 항목의 앞부분에 나와 있는 그림을 구현 합니다.

[!code-cpp[concrt-basic-agents#1](../../parallel/concrt/codesnippet/cpp/asynchronous-agents-library_1.cpp)]

이 예제는 다음과 같은 출력을 생성합니다.

```Output
agent1: sending request...
agent2: received 'request'.
agent2: sending response...
agent1: received '42'.
```

다음 항목에서는이 예제에서 사용 되는 기능에 대해 설명 합니다.

## <a name="related-topics"></a>관련 항목

[비동기 에이전트](../../parallel/concrt/asynchronous-agents.md)<br/>
대규모 컴퓨팅 작업을 해결 하는 비동기 에이전트의 역할에 대해 설명 합니다.

[비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
에이전트 라이브러리에서 제공 하는 다양 한 메시지 블록 형식을 설명 합니다.

[메시지 전달 함수](../../parallel/concrt/message-passing-functions.md)<br/>
에이전트 라이브러리에서 제공 하는 다양 한 메시지 전달 루틴에 대해 설명 합니다.

[방법: 다양 한 Producer-Consumer 패턴 구현](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br/>
응용 프로그램에서 생산자-소비자 패턴을 구현 하는 방법을 설명 합니다.

[방법: 호출 및 변환기 클래스에 작업 함수 제공](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br/>
[Concurrency:: call](../../parallel/concrt/reference/call-class.md) 및 [concurrency:: 변환기](../../parallel/concrt/reference/transformer-class.md) 클래스에 작업 함수를 제공 하는 여러 가지 방법을 보여 줍니다.

[방법: 데이터 파이프라인에서 변환기 사용](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
데이터 파이프라인에서 [concurrency:: 변환기](../../parallel/concrt/reference/transformer-class.md) 클래스를 사용 하는 방법을 보여 줍니다.

[방법: 완료 된 작업 중에서 선택](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br/>
[Concurrency:: choice](../../parallel/concrt/reference/choice-class.md) 및 [concurrency:: join](../../parallel/concrt/reference/join-class.md) 클래스를 사용 하 여 검색 알고리즘을 완료 하는 첫 번째 작업을 선택 하는 방법을 보여 줍니다.

[방법: 정기적으로 메시지 보내기](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br/>
[Concurrency:: timer](../../parallel/concrt/reference/timer-class.md) 클래스를 사용 하 여 일정 한 간격으로 메시지를 보내는 방법을 보여 줍니다.

[방법: 메시지 블록 필터 사용](../../parallel/concrt/how-to-use-a-message-block-filter.md)<br/>
필터를 사용 하 여 비동기 메시지 블록이 메시지를 수락 하거나 거부 하도록 설정 하는 방법을 보여 줍니다.

[PPL(병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
응용 프로그램에서 병렬 알고리즘과 같은 다양 한 병렬 패턴을 사용 하는 방법을 설명 합니다.

[동시성 런타임](../../parallel/concrt/concurrency-runtime.md)<br/>
병렬 프로그래밍을 간소화하는 동시성 런타임에 대해 설명하고 관련 항목의 링크를 제공합니다.
