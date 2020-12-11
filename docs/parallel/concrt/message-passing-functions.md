---
description: '자세한 정보: 메시지 전달 함수'
title: 메시지 전달 함수
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 77e221f5d2116c1bfc2690d247161979af04ac06
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159858"
---
# <a name="message-passing-functions"></a>메시지 전달 함수

비동기 에이전트 라이브러리는 구성 요소 간에 메시지를 전달 하는 데 사용할 수 있는 여러 함수를 제공 합니다.

이러한 메시지 전달 함수는 다양 한 메시지 블록 형식과 함께 사용 됩니다. 동시성 런타임에서 정의한 메시지 블록 형식에 대 한 자세한 내용은 [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)을 참조 하세요.

## <a name="sections"></a><a name="top"></a> 섹션이

이 항목에서는 다음 메시지 전달 함수에 대해 설명 합니다.

- [send 및 asend](#send)

- [수신 및 try_receive](#receive)

- [예제](#examples)

## <a name="send-and-asend"></a><a name="send"></a> send 및 asend

[Concurrency:: send](reference/concurrency-namespace-functions.md#send) 함수는 지정 된 대상에 동기적으로 메시지를 보내고 [concurrency:: asend](reference/concurrency-namespace-functions.md#asend) 함수는 지정 된 대상에 비동기적으로 메시지를 보냅니다. `send`및 함수는 모두 `asend` 메시지를 수락 하거나 거부 함을 나타내는 대상이 될 때까지 대기 합니다.

`send`함수는 대상이 반환 되기 전에 메시지를 수락 하거나 거부할 때까지 대기 합니다. `send`이 함수는 **`true`** 메시지가 전달 된 경우을 반환 하 고 **`false`** 그렇지 않으면를 반환 합니다. 함수는 `send` 동기적으로 작동 하므로 `send` 함수가 반환 되기 전에 대상이 메시지를 받을 때까지 대기 합니다.

반대로 함수는 `asend` 대상에서 메시지를 반환 하기 전에 메시지를 수락 하거나 거부할 때까지 기다리지 않습니다. 대신 함수는 `asend` **`true`** 대상에서 메시지를 수락 하 고 최종적으로이를 사용 하는 경우를 반환 합니다. 그렇지 않으면를 `asend` 반환 **`false`** 하 여 대상이 메시지를 거부 했거나 메시지를 전송할지 여부에 대 한 결정을 연기 했음을 나타냅니다.

[[맨 위로](#top)이동]

## <a name="receive-and-try_receive"></a><a name="receive"></a> 수신 및 try_receive

[Concurrency:: receive](reference/concurrency-namespace-functions.md#receive) 및 [concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive) 함수는 지정 된 소스에서 데이터를 읽습니다. `receive`함수는 데이터를 사용할 수 있을 때까지 대기 하는 반면 `try_receive` 함수는 즉시 반환 됩니다.

`receive`계속 하려면 데이터를 만들어야 하는 경우 함수를 사용 합니다. `try_receive`현재 컨텍스트를 차단 하지 않거나 계속할 데이터를 갖지 않아도 되는 경우 함수를 사용 합니다.

[[맨 위로](#top)이동]

## <a name="examples"></a><a name="examples"></a> 예

및 함수를 사용 하는 예제는 `send` `asend` `receive` 다음 항목을 참조 하세요.

- [비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)

- [방법: 다양 한 Producer-Consumer 패턴 구현](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [방법: 호출 및 변환기 클래스에 작업 함수 제공](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [방법: 데이터 파이프라인에서 변환기 사용](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [방법: 완료 된 작업 중에서 선택](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [방법: 정기적으로 메시지 보내기](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [방법: 메시지 블록 필터 사용](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[맨 위로](#top)이동]

## <a name="see-also"></a>참고 항목

[비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[비동기 메시지 블록](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[send 함수](reference/concurrency-namespace-functions.md#send)<br/>
[asend 함수](reference/concurrency-namespace-functions.md#asend)<br/>
[receive 함수](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive 함수](reference/concurrency-namespace-functions.md#try_receive)
