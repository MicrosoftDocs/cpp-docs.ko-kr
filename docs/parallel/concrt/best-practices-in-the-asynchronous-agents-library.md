---
description: '자세한 정보: 비동기 에이전트 라이브러리의 모범 사례'
title: 비동기 에이전트 라이브러리의 모범 사례
ms.date: 11/04/2016
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
ms.openlocfilehash: 5468d5c7a0ddb3a0a87d0675dfb3f19385ccc8b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205722"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>비동기 에이전트 라이브러리의 모범 사례

이 문서에서는 비동기 에이전트 라이브러리를 효과적으로 사용 하는 방법을 설명 합니다. 에이전트 라이브러리는 정교 하지 않은 데이터 흐름 및 파이프라인 작업을 위해 행위자 기반 프로그래밍 모델 및 in-process 메시지 전달을 촉진 합니다.

에이전트 라이브러리에 대 한 자세한 내용은 [비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)를 참조 하십시오.

## <a name="sections"></a><a name="top"></a> 섹션이

이 문서는 다음 섹션으로 구성됩니다.

- [에이전트를 사용 하 여 상태 격리](#isolation)

- [제한 메커니즘을 사용 하 여 데이터 파이프라인의 메시지 수 제한](#throttling)

- [데이터 파이프라인에서 Fine-Grained 작업 수행 안 함](#fine-grained)

- [값으로 많은 메시지 페이로드를 전달 하지 마십시오.](#large-payloads)

- [소유권이 정의 되지 않은 경우 데이터 네트워크에서 shared_ptr 사용](#ownership)

## <a name="use-agents-to-isolate-state"></a><a name="isolation"></a> 에이전트를 사용 하 여 상태 격리

에이전트 라이브러리는 비동기 메시지 전달 메커니즘을 통해 격리 된 구성 요소를 연결할 수 있도록 하 여 공유 된 상태에 대 한 대안을 제공 합니다. 비동기 에이전트는 다른 구성 요소에서 내부 상태를 격리할 때 가장 효과적입니다. 상태를 격리 하면 여러 구성 요소가 일반적으로 공유 데이터에 대해 작동 하지 않습니다. 상태 격리를 사용 하면 공유 메모리의 경합이 줄어들기 때문에 응용 프로그램을 확장할 수 있습니다. 또한 상태 격리를 사용 하면 구성 요소에서 공유 데이터에 대 한 액세스를 동기화 할 필요가 없기 때문에 교착 상태 및 경합 상태의 가능성이 줄어듭니다.

일반적으로 에이전트 클래스의 또는 섹션에서 데이터 멤버를 보유 하 **`private`** **`protected`** 고, 메시지 버퍼를 사용 하 여 상태 변경 내용을 전달 함으로써 에이전트의 상태를 격리 합니다. 다음 예제에서는 `basic_agent` [concurrency:: agent](../../parallel/concrt/reference/agent-class.md)에서 파생 되는 클래스를 보여 줍니다. `basic_agent`클래스는 두 개의 메시지 버퍼를 사용 하 여 외부 구성 요소와 통신 합니다. 메시지 버퍼 하나는 들어오는 메시지를 보유 합니다. 다른 메시지 버퍼는 나가는 메시지를 보유 합니다.

[!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]

에이전트를 정의 하 고 사용 하는 방법에 대 한 전체 예제는 [연습: Agent-Based 응용 프로그램 만들기](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md) 및 [연습: 데이터 흐름 에이전트 만들기](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="use-a-throttling-mechanism-to-limit-the-number-of-messages-in-a-data-pipeline"></a><a name="throttling"></a> 제한 메커니즘을 사용 하 여 데이터 파이프라인의 메시지 수 제한

여러 메시지 버퍼 형식 (예: [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md))은 무제한의 메시지를 보유할 수 있습니다. 메시지 공급자가 소비자가 이러한 메시지를 처리할 수 있는 것 보다 빠르게 데이터 파이프라인에 메시지를 보내는 경우 응용 프로그램은 메모리 부족 또는 메모리 부족 상태를 입력할 수 있습니다. 데이터 파이프라인에서 동시에 활성화 되는 메시지 수를 제한 하기 위해 세마포와 같은 제한 메커니즘을 사용할 수 있습니다.

다음 기본 예제에서는 세마포를 사용 하 여 데이터 파이프라인의 메시지 수를 제한 하는 방법을 보여 줍니다. 데이터 파이프라인은 [concurrency:: wait](reference/concurrency-namespace-functions.md#wait) 함수를 사용 하 여 최소 100 밀리초를 사용 하는 작업을 시뮬레이션 합니다. 발신자는 소비자가 해당 메시지를 처리할 수 있는 것 보다 더 빠르게 메시지를 생성 하기 때문에이 예제에서는 `semaphore` 응용 프로그램이 활성 메시지 수를 제한할 수 있도록 클래스를 정의 합니다.

[!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]

`semaphore`개체는 파이프라인에서 동시에 최대 두 개의 메시지를 처리 하도록 제한 합니다.

이 예제의 생산자는 소비자에 게 비교적 적은 수의 메시지를 보냅니다. 따라서이 예제에서는 잠재적 메모리 부족 또는 메모리 부족 상태를 보여 주지 않습니다. 그러나이 메커니즘은 데이터 파이프라인에 비교적 많은 수의 메시지가 포함 된 경우에 유용 합니다.

이 예제에서 사용 되는 세마포 클래스를 만드는 방법에 대 한 자세한 내용은 [방법: 컨텍스트 클래스를 사용 하 여 협조적 세마포 구현](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="do-not-perform-fine-grained-work-in-a-data-pipeline"></a><a name="fine-grained"></a> 데이터 파이프라인에서 Fine-Grained 작업 수행 안 함

에이전트 라이브러리는 데이터 파이프라인에서 수행 하는 작업이 매우 정교 하지 않은 경우에 가장 유용 합니다. 예를 들어 한 응용 프로그램 구성 요소는 파일 또는 네트워크 연결에서 데이터를 읽고 경우에 따라 해당 데이터를 다른 구성 요소에 보낼 수 있습니다. 에이전트 라이브러리에서 메시지를 전파 하는 데 사용 하는 프로토콜을 사용 하면 메시지 전달 메커니즘이 PPL ( [병렬 패턴 라이브러리](../../parallel/concrt/parallel-patterns-library-ppl.md) )에서 제공 하는 작업 병렬 구문 보다 더 많은 오버 헤드가 발생 합니다. 따라서 데이터 파이프라인에서 수행 하는 작업이이 오버 헤드를 오프셋할 만큼 충분 한지 확인 해야 합니다.

데이터 파이프라인은 태스크가 정교 하지 않은 경우에 가장 효과적 이지만 데이터 파이프라인의 각 단계는 작업 그룹 및 병렬 알고리즘과 같은 PPL 구문을 사용 하 여 세분화 된 작업을 수행할 수 있습니다. 각 처리 단계에서 세분화 된 병렬 처리를 사용 하는 정교 하지 않은 데이터 네트워크에 대 한 예제는 [연습: Image-Processing 네트워크 만들기](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="do-not-pass-large-message-payloads-by-value"></a><a name="large-payloads"></a> 값으로 많은 메시지 페이로드를 전달 하지 마십시오.

경우에 따라 런타임은 한 메시지 버퍼에서 다른 메시지 버퍼로 전달 되는 모든 메시지의 복사본을 만듭니다. 예를 들어 [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 클래스는 각 대상에 수신 되는 모든 메시지의 복사본을 제공 합니다. 또한 런타임은 메시지 버퍼에서 메시지를 쓰고 메시지를 읽을 수 있도록 [concurrency:: send](reference/concurrency-namespace-functions.md#send) 및 [concurrency:: receive](reference/concurrency-namespace-functions.md#receive) 와 같은 메시지 전달 함수를 사용 하는 경우 메시지 데이터의 복사본을 만듭니다. 이 메커니즘을 사용 하면 공유 데이터에 동시에 쓸 수 없는 위험을 방지할 수 있지만 메시지 페이로드가 비교적 클 때 메모리 성능이 저하 될 수 있습니다.

페이로드가 많은 메시지를 전달할 때 포인터나 참조를 사용 하 여 메모리 성능을 향상 시킬 수 있습니다. 다음 예제에서는 동일한 메시지 유형에 포인터를 전달 하기 위해 값으로 많은 메시지를 전달 하는 것을 비교 합니다. 이 예제에서는 `producer` `consumer` 개체에 대해 작동 하는 두 개의 에이전트 유형인 및를 정의 합니다 `message_data` . 이 예에서는 생산자 에이전트가 여러 개체를 소비자에 게 보내는 데 필요한 시간 및 `message_data` 생산자 에이전트가 소비자에 게 개체에 대 한 여러 포인터를 보내는 데 필요한 시간을 비교 합니다 `message_data` .

[!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]

이 예제에서는 다음과 같은 샘플 출력을 생성 합니다.

```Output
Using message_data...
took 437ms.
Using message_data*...
took 47ms.
```

포인터를 사용 하는 버전은 런타임에서 `message_data` 생산자 로부터 소비자에 게 전달 하는 모든 개체의 전체 복사본을 만들 필요가 없기 때문에 더 나은 성능을 발휘 합니다.

[[맨 위로](#top)이동]

## <a name="use-shared_ptr-in-a-data-network-when-ownership-is-undefined"></a><a name="ownership"></a> 소유권이 정의 되지 않은 경우 데이터 네트워크에서 shared_ptr 사용

메시지 전달 파이프라인이 나 네트워크를 통해 메시지를 보낼 때 일반적으로 네트워크의 맨 앞에 있는 각 메시지에 대해 메모리를 할당 하 고 네트워크의 끝에서 해당 메모리를 해제 합니다. 이 메커니즘은 효과적으로 작동 하지만 사용할 수 없는 경우가 있습니다. 예를 들어 데이터 네트워크에 여러 개의 끝 노드가 포함 된 경우를 고려해 보세요. 이 경우에는 메시지에 대 한 메모리를 해제 하기 위한 명확한 위치가 없습니다.

이 문제를 해결 하기 위해 여러 구성 요소가 포인터를 소유할 수 있도록 하는 메커니즘 (예: [std:: shared_ptr](../../standard-library/shared-ptr-class.md))을 사용할 수 있습니다. `shared_ptr`리소스를 소유 하는 최종 개체가 제거 되 면 리소스도 해제 됩니다.

다음 예제에서는를 사용 하 여 `shared_ptr` 여러 메시지 버퍼에서 포인터 값을 공유 하는 방법을 보여 줍니다. 이 예제에서는 [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 개체를 세 개의 [concurrency:: call](../../parallel/concrt/reference/call-class.md) 개체에 연결 합니다. `overwrite_buffer`클래스는 각 대상에 메시지를 제공 합니다. 데이터 네트워크의 끝에는 여러 개의 데이터 소유자가 있기 때문에이 예제에서는를 사용 `shared_ptr` 하 여 각 `call` 개체에서 메시지의 소유권을 공유할 수 있도록 합니다.

[!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]

이 예제에서는 다음과 같은 샘플 출력을 생성 합니다.

```Output
Creating resource 42...
receiver1: received resource 42
Creating resource 64...
receiver2: received resource 42
receiver1: received resource 64
Destroying resource 42...
receiver2: received resource 64
Destroying resource 64...
```

## <a name="see-also"></a>참고 항목

[동시성 런타임 모범 사례](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[연습: Agent-Based 응용 프로그램 만들기](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
[연습: 데이터 흐름 에이전트 만들기](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[연습: Image-Processing 네트워크 만들기](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[병렬 패턴 라이브러리의 모범 사례](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[동시성 런타임의 일반적인 모범 사례](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
