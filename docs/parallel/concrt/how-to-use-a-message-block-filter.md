---
title: '방법: 메시지 블록 필터 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
ms.openlocfilehash: ac58ef2240d2ea6ba34b334106c08595e70b02e8
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008637"
---
# <a name="how-to-use-a-message-block-filter"></a>방법: 메시지 블록 필터 사용

이 문서에서는 필터 함수를 사용 하 여 비동기 메시지 블록이 해당 메시지의 페이로드를 기준으로 메시지를 수락 하거나 거부 하도록 설정 하는 방법을 보여 줍니다.

Concurrency: [: unbounded_buffer](reference/unbounded-buffer-class.md), [concurrency:: call](../../parallel/concrt/reference/call-class.md)또는 [concurrency:: 변환기](../../parallel/concrt/reference/transformer-class.md)와 같은 메시지 블록 개체를 만들 때 메시지 블록이 메시지를 수락 하거나 거부 하는지 여부를 결정 하는 *필터 함수* 를 제공할 수 있습니다. 필터 함수는 메시지 블록이 특정 값만 받도록 보장 하는 유용한 방법입니다.

필터 함수는 메시지 블록을 연결 하 여 *데이터 흐름 네트워크*를 구성할 수 있으므로 중요 합니다. 데이터 흐름 네트워크에서 메시지 블록은 특정 조건을 충족 하는 메시지만 처리 하 여 데이터 흐름을 제어 합니다. 조건문, 루프 등의 제어 구조를 사용 하 여 데이터 흐름이 규제 되는 제어 흐름 모델과 비교 합니다.

이 문서에서는 메시지 필터를 사용 하는 방법에 대 한 기본 예를 제공 합니다. 메시지 필터 및 데이터 흐름 모델을 사용 하 여 메시지 블록을 연결 하는 추가 예제는 [연습: 데이터 흐름 에이전트 만들기](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) 및 [연습: Image-Processing 네트워크 만들기](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)를 참조 하세요.

## <a name="example-count_primes-function"></a>예: count_primes 함수

`count_primes`들어오는 메시지를 필터링 하지 않는 메시지 블록의 기본 사용법을 보여 주는 다음 함수를 살펴보겠습니다. 메시지 블록은 [std:: vector](../../standard-library/vector-class.md) 개체에 소수를 추가 합니다. `count_primes`함수는 메시지 블록에 여러 개의 숫자를 보내고, 메시지 블록에서 출력 값을 수신 하 고, 콘솔에 프라임 된 숫자를 출력 합니다.

[!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]

`transformer`개체는 모든 입력 값을 처리 하지만 소수 값만 필요로 합니다. 메시지 발신자가 프라임 번호만 전송 하도록 응용 프로그램을 작성할 수 있지만 메시지 수신자의 요구 사항은 항상 알 수 없습니다.

## <a name="example-count_primes_filter-function"></a>예: count_primes_filter 함수

다음 함수는 `count_primes_filter` 함수와 동일한 작업을 수행 합니다 `count_primes` . 그러나 `transformer` 이 버전의 개체는 필터 함수를 사용 하 여 소수 인 값만 수락 합니다. 작업을 수행 하는 함수는 프라임 번호만 받습니다. 따라서 함수를 호출할 필요가 없습니다 `is_prime` .

개체는 소수를 수신 하기 때문에 `transformer` `transformer` 개체 자체는 소수를 보유할 수 있습니다. 즉, `transformer` 개체에 소수를 추가할 때는이 예제의 개체가 필요 하지 않습니다 `vector` .

[!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]

`transformer`이제 개체가 소수 인 값만 처리 합니다. 이전 예제에서 개체는 `transformer` 모든 메시지를 처리 합니다. 따라서 이전 예제는 보내는 메시지와 동일한 수의 메시지를 받아야 합니다. 이 예제에서는 [concurrency:: send](reference/concurrency-namespace-functions.md#send) 함수의 결과를 사용 하 여 개체에서 받을 메시지 수를 확인 합니다 `transformer` . `send`함수는 메시지 **`true`** 버퍼가 메시지를 수락 하 고 메시지 버퍼가 메시지를 거부할 때를 반환 **`false`** 합니다. 따라서 메시지 버퍼가 메시지를 수락 하는 횟수는 소수 수와 일치 합니다.

## <a name="example-finished-message-block-filter-code-sample"></a>예: 완료 된 메시지 블록 필터 코드 샘플

다음 코드에서는 전체 예제를 보여 줍니다. 이 예제에서는 함수와 함수를 모두 호출 합니다 `count_primes` `count_primes_filter` .

[!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `primes-filter.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc primes-filter**

## <a name="robust-programming"></a>강력한 프로그래밍

필터 함수는 람다 함수, 함수 포인터 또는 함수 개체 일 수 있습니다. 모든 필터 함수는 다음 형식 중 하나를 사용 합니다.

```Output
bool (T)
bool (T const &)
```

불필요 한 데이터 복사를 제거 하려면 값으로 전송 되는 집계 형식이 있는 경우 두 번째 형식을 사용 합니다.

## <a name="see-also"></a>참조

[비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[연습: 데이터 흐름 에이전트 만들기](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[연습: Image-Processing 네트워크 만들기](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[변환기 클래스](../../parallel/concrt/reference/transformer-class.md)
