---
description: '자세한 정보: 방법: 다양 한 Producer-Consumer 패턴 구현'
title: '방법: 다양한 공급자/소비자 패턴 구현'
ms.date: 11/04/2016
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
ms.openlocfilehash: 5742d3ba213997efc54aeca360c99fd11b0cf712
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209908"
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>방법: 다양한 공급자/소비자 패턴 구현

이 항목에서는 응용 프로그램에서 생산자-소비자 패턴을 구현 하는 방법에 대해 설명 합니다. 이 패턴에서 *생산자* 는 메시지 블록에 메시지를 보내고 *소비자* 는 해당 블록에서 메시지를 읽습니다.

이 항목에서는 두 가지 시나리오를 보여 줍니다. 첫 번째 시나리오에서 소비자는 생산자가 보내는 각 메시지를 받아야 합니다. 두 번째 시나리오에서 소비자는 주기적으로 데이터를 폴링합니다. 따라서 각 메시지를 수신할 필요가 없습니다.

이 항목의 두 예제에서는 에이전트, 메시지 블록 및 메시지 전달 함수를 사용 하 여 생산자에서 소비자로 메시지를 전송 합니다. 생산자 에이전트는 [concurrency:: send](reference/concurrency-namespace-functions.md#send) 함수를 사용 하 여 [Concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) 개체에 메시지를 씁니다. 소비자 에이전트는 [concurrency:: receive](reference/concurrency-namespace-functions.md#receive) 함수를 사용 하 여 [Concurrency:: ISource](../../parallel/concrt/reference/isource-class.md) 개체에서 메시지를 읽습니다. 두 에이전트 모두 센티널 값을 포함 하 여 처리의 끝을 조정 합니다.

비동기 에이전트에 대 한 자세한 내용은 [비동기 에이전트](../../parallel/concrt/asynchronous-agents.md)를 참조 하세요. 메시지 블록 및 메시지 전달 함수에 대 한 자세한 내용은 [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md) 및 [메시지 전달 함수](../../parallel/concrt/message-passing-functions.md)를 참조 하세요.

## <a name="example-send-series-of-numbers-to-consumer-agent"></a>예: 소비자 에이전트로 일련의 숫자 보내기

이 예에서 생산자 에이전트는 일련의 숫자를 소비자 에이전트로 보냅니다. 소비자는 이러한 각 숫자를 받고 평균을 계산 합니다. 응용 프로그램은 평균을 콘솔에 씁니다.

이 예제에서는 [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) 개체를 사용 하 여 생산자가 메시지를 큐에 대기 시킬 수 있도록 합니다. `unbounded_buffer`클래스는 `ITarget` 및를 구현 `ISource` 하므로 생산자와 소비자는 공유 버퍼에서 메시지를 보내고 받을 수 있습니다. `send`및 `receive` 함수는 생산자의 데이터를 소비자에 게 전파 하는 작업을 조정 합니다.

[!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]

이 예제의 결과는 다음과 같습니다.

```Output
The average is 50.
```

## <a name="example-send-series-of-stock-quotes-to-consumer-agent"></a>예: 소비자 에이전트로 일련의 주식 시세 보내기

이 예에서 생산자 에이전트는 일련의 주식 시세를 소비자 에이전트로 보냅니다. 소비자 에이전트는 주기적으로 현재 견적을 읽고 콘솔에 출력 합니다.

이 예제는 [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 개체를 사용 하 여 생산자가 소비자와 하나의 메시지를 공유할 수 있도록 하는 점을 제외 하 고는 이전 예제와 유사 합니다. 이전 예제와 같이 클래스는 `overwrite_buffer` 및를 `ITarget` 구현 `ISource` 하므로 생산자와 소비자가 공유 메시지 버퍼에 대해 작업을 수행할 수 있습니다.

[!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]

이 예제에서는 다음 샘플 출력을 생성 합니다.

```Output
Current quote is 24.44.
Current quote is 24.44.
Current quote is 24.65.
Current quote is 24.99.
Current quote is 23.76.
Current quote is 22.30.
Current quote is 25.89.
```

개체와 달리 `unbounded_buffer` `receive` 함수는 개체에서 메시지를 제거 하지 않습니다 `overwrite_buffer` . 생산자가 메시지를 덮어쓰기 전에 소비자가 메시지 버퍼를 두 번 이상 읽으면 수신자는 매번 동일한 메시지를 받습니다.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `producer-consumer.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

**cl.exe/EHsc producer-consumer**

## <a name="see-also"></a>참고 항목

[비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[비동기 에이전트](../../parallel/concrt/asynchronous-agents.md)<br/>
[비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[메시지 전달 함수](../../parallel/concrt/message-passing-functions.md)
