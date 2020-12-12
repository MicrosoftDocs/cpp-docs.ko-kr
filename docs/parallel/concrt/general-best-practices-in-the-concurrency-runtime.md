---
description: '자세한 정보: 동시성 런타임의 일반 모범 사례'
title: 동시성 런타임의 유용한 일반 정보
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
ms.openlocfilehash: a0de8d9a0070bfc0691aeb9484c755cbfcbb40b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197428"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>동시성 런타임의 유용한 일반 정보

이 문서에서는 동시성 런타임의 여러 영역에 적용 되는 모범 사례에 대해 설명 합니다.

## <a name="sections"></a><a name="top"></a> 섹션이

이 문서는 다음 섹션으로 구성됩니다.

- [가능 하면 협조적 동기화 구문 사용](#synchronization)

- [생성 되지 않는 긴 작업을 방지 합니다.](#yield)

- [초과 구독을 사용 하 여 차단 또는 대기 시간이 긴 작업 오프셋](#oversubscription)

- [가능 하면 동시 메모리 관리 함수 사용](#memory)

- [RAII를 사용 하 여 동시성 개체의 수명 관리](#raii)

- [전역 범위에서 동시성 개체를 만들지 마십시오.](#global-scope)

- [공유 데이터 세그먼트에서 동시성 개체 사용 안 함](#shared-data)

## <a name="use-cooperative-synchronization-constructs-when-possible"></a><a name="synchronization"></a> 가능 하면 협조적 동기화 구문 사용

동시성 런타임는 외부 동기화 개체를 요구 하지 않는 많은 동시성 안전 구문을 제공 합니다. 예를 들어 [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 클래스는 동시성이 보장 되는 추가 및 요소 액세스 작업을 제공 합니다. 여기서는 동시성이 안전 함을 의미 하는 포인터가 나 반복기는 항상 유효 합니다. 요소 초기화 나 특정 트래버스 주문의 보장은 아닙니다. 그러나 리소스에 단독으로 액세스 해야 하는 경우 런타임은 [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md), [concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)및 [concurrency:: event](../../parallel/concrt/reference/event-class.md) 클래스를 제공 합니다. 이러한 형식은 협조적으로 동작 합니다. 따라서 작업 스케줄러는 첫 번째 태스크에서 데이터를 기다리는 동안 처리 리소스를 다른 컨텍스트에 다시 할당할 수 있습니다. 가능 하면 협조적으로 동작 하지 않는 Windows API에서 제공 하는 것과 같은 다른 동기화 메커니즘 대신 이러한 동기화 유형을 사용 합니다. 이러한 동기화 형식 및 코드 예제에 대 한 자세한 내용은 [동기화 데이터 구조](../../parallel/concrt/synchronization-data-structures.md) 및 [Windows API와 동기화 데이터 구조 비교](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="avoid-lengthy-tasks-that-do-not-yield"></a><a name="yield"></a> 생성 되지 않는 긴 작업을 방지 합니다.

작업 스케줄러는 협조적으로 동작 하기 때문에 작업 간에 공평 하 게 제공 되지 않습니다. 따라서 태스크가 다른 작업을 시작 하지 못하게 할 수 있습니다. 이는 일부 경우에 허용 되지만 교착 상태 또는 고갈를 일으킬 수 있는 경우도 있습니다.

다음 예제에서는 할당 된 처리 리소스 수보다 많은 작업을 수행 합니다. 첫 번째 작업은 작업 스케줄러로 생성 되지 않으므로 두 번째 작업은 첫 번째 작업이 완료 될 때까지 시작 되지 않습니다.

[!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]

이 예제는 다음과 같은 출력을 생성합니다.

1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000

두 작업 간에 공동 작업을 가능 하 게 하는 몇 가지 방법이 있습니다. 한 가지 방법은 장기 실행 작업에서 작업 스케줄러를 때때로 생성 하는 것입니다. 다음 예제에서는 `task` 다른 작업을 실행할 수 있도록 [concurrency:: Context:: Yield](reference/context-class.md#yield) 메서드를 호출 하 여 작업 스케줄러에 대 한 실행을 양보 하도록 함수를 수정 합니다.

[!code-cpp[concrt-cooperative-tasks#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_2.cpp)]

이 예제는 다음과 같은 출력을 생성합니다.

```Output
1: 250000000
2: 250000000
1: 500000000
2: 500000000
1: 750000000
2: 750000000
1: 1000000000
2: 1000000000
```

`Context::Yield`메서드는 현재 스레드가 속한 스케줄러, 경량 작업 또는 다른 운영 체제 스레드에 대해 다른 활성 스레드만 생성 합니다. 이 메서드는 [concurrency:: task_group](reference/task-group-class.md) 또는 [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) 개체에서 실행 되도록 예약 되었지만 아직 시작 되지 않은 작업에는 적용 되지 않습니다.

장기 실행 작업 간에 공동 작업을 가능 하 게 하는 다른 방법이 있습니다. 대량 작업을 더 작은 하위 작업으로 나눌 수 있습니다. 시간이 오래 걸리는 작업 중에 초과 구독을 사용 하도록 설정할 수도 있습니다. 초과 구독을 사용하면 사용 가능한 하드웨어 수보다 많은 스레드를 만들 수 있습니다. 초과 구독은 디스크에서 데이터를 읽거나 네트워크를 연결 하는 등 시간이 오래 걸리는 작업이 많은 대기 시간을 포함 하는 경우에 특히 유용 합니다. 간단한 작업 및 초과 구독에 대 한 자세한 내용은 [작업 스케줄러](../../parallel/concrt/task-scheduler-concurrency-runtime.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="use-oversubscription-to-offset-operations-that-block-or-have-high-latency"></a><a name="oversubscription"></a> 초과 구독을 사용 하 여 차단 또는 대기 시간이 긴 작업 오프셋

동시성 런타임는 [동시성:: critical_section](../../parallel/concrt/reference/critical-section-class.md)와 같은 동기화 기본 형식을 제공 하 여 작업을 협조적으로 차단 하 고 양보할 수 있게 합니다. 한 작업이 협조적으로 차단 하거나 생성 하는 경우 첫 번째 태스크에서 데이터를 기다리는 동안 작업 스케줄러가 다른 컨텍스트에 처리 리소스를 다시 할당할 수 있습니다.

동시성 런타임에서 제공 하는 협조적 차단 메커니즘을 사용할 수 없는 경우가 있습니다. 예를 들어 사용 하는 외부 라이브러리는 다른 동기화 메커니즘을 사용할 수 있습니다. 또 다른 예는 Windows API 함수를 사용 `ReadFile` 하 여 네트워크 연결에서 데이터를 읽는 경우와 같이 대기 시간이 많은 작업을 수행 하는 경우입니다. 이러한 경우에는 초과 구독을 사용 하 여 다른 태스크가 유휴 상태일 때 다른 작업을 실행할 수 있습니다. 초과 구독을 사용하면 사용 가능한 하드웨어 수보다 많은 스레드를 만들 수 있습니다.

지정 된 URL에서 파일을 다운로드 하는 다음 함수를 살펴보겠습니다 `download` . 이 예제에서는 [concurrency:: Context:: Oversubscribe](reference/context-class.md#oversubscribe) 메서드를 사용 하 여 활성 스레드 수를 일시적으로 늘립니다.

[!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]

함수는 `GetHttpFile` 잠재적으로 잠재적으로 잠재적인 작업을 수행 하므로 현재 태스크가 데이터를 대기 하는 동안 초과 구독을 사용 하 여 다른 작업을 실행할 수 있습니다. 이 예제의 전체 버전을 보려면 [방법: 초과 구독을 사용 하 여 대기 시간 오프셋](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)을 참조 하십시오.

[[맨 위로](#top)이동]

## <a name="use-concurrent-memory-management-functions-when-possible"></a><a name="memory"></a> 가능 하면 동시 메모리 관리 함수 사용

수명이 비교적 짧은 작은 개체를 자주 할당 하는 세분화 된 작업이 있는 경우 [concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc) 및 [Concurrency:: Free](reference/concurrency-namespace-functions.md#free)를 사용 하 여 메모리 관리 함수를 사용 합니다. 동시성 런타임는 실행 중인 각 스레드에 대해 별도의 메모리 캐시를 보유 합니다. `Alloc`및 `Free` 함수는 잠금이나 메모리 장벽을 사용 하지 않고 이러한 캐시에서 메모리를 할당 하 고 해제 합니다.

이러한 메모리 관리 함수에 대 한 자세한 내용은 [작업 스케줄러](../../parallel/concrt/task-scheduler-concurrency-runtime.md)를 참조 하세요. 이러한 함수를 사용 하는 예제는 [방법: Alloc 및 Free를 사용 하 여 메모리 성능 향상](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="use-raii-to-manage-the-lifetime-of-concurrency-objects"></a><a name="raii"></a> RAII를 사용 하 여 동시성 개체의 수명 관리

동시성 런타임는 예외 처리를 사용 하 여 취소와 같은 기능을 구현 합니다. 따라서 런타임을 호출 하거나 런타임을 호출 하는 다른 라이브러리를 호출할 때 예외 로부터 안전한 코드를 작성 합니다.

RAII ( *리소스 획득* ) 패턴은 지정 된 범위에서 동시성 개체의 수명을 안전 하 게 관리 하는 한 가지 방법입니다. RAII 패턴에서 데이터 구조가 스택에 할당 됩니다. 해당 데이터 구조는 생성 될 때 리소스를 초기화 하거나 획득 하 고, 데이터 구조가 소멸 될 때 해당 리소스를 소멸 하거나 해제 합니다. RAII 패턴은 바깥쪽 범위가 끝나기 전에 소멸자가 호출 되도록 합니다. 이 패턴은 함수에 여러 문이 포함 된 경우에 유용 **`return`** 합니다. 이 패턴은 예외 안전 코드를 작성 하는 데도 도움이 됩니다. **`throw`** 문에서 스택이 해제 되도록 하면 RAII 개체에 대 한 소멸자가 호출 됩니다. 따라서 리소스는 항상 올바르게 삭제 되거나 해제 됩니다.

런타임은 RAII 패턴을 사용 하는 여러 클래스 (예: [concurrency:: critical_section:: scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class) 및 [concurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class))를 정의 합니다. 이러한 도우미 클래스를 범위 지정 *잠금* 이라고 합니다. 이러한 클래스는 [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) 또는 [concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 개체를 사용 하는 경우 몇 가지 이점을 제공 합니다. 이러한 클래스의 생성자는 제공 된 또는 개체에 대 한 액세스 권한을 얻습니다. `critical_section` `reader_writer_lock` 소멸자는 해당 개체에 대 한 액세스를 해제 합니다. 범위 잠금이 제거 될 때 상호 배제 개체에 대 한 액세스를 자동으로 해제 하기 때문에 기본 개체의 잠금을 수동으로 해제 하지 않습니다.

`account`외부 라이브러리에 의해 정의 되므로 수정할 수 없는 다음 클래스를 생각해 보세요.

[!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]

다음 예에서는 개체에 대해 병렬로 여러 트랜잭션을 수행 합니다 `account` . `critical_section` `account` 클래스는 동시성이 안전 하지 않으므로이 예제에서는 개체를 사용 하 여 개체에 대 한 액세스를 동기화 `account` 합니다. 각 병렬 작업은 개체를 사용 하 여 `critical_section::scoped_lock` `critical_section` 작업이 성공 하거나 실패할 때 개체의 잠금이 해제 되도록 합니다. 계정 잔액이 음수 이면 `withdraw` 예외를 throw 하 여 작업이 실패 합니다.

[!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]

이 예제에서는 다음과 같은 샘플 출력을 생성 합니다.

```Output
Balance before deposit: 1924
Balance after deposit: 2924
Balance before withdrawal: 2924
Balance after withdrawal: -76
Balance before withdrawal: -76
Error details:
    negative balance: -76
```

RAII 패턴을 사용 하 여 동시성 개체의 수명을 관리 하는 추가 예제는 [연습: User-Interface 스레드에서 작업 제거](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md), [방법: 컨텍스트 클래스를 사용 하 여 협조적 세마포 구현](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)및 [방법: 초과 구독을 사용 하 여 대기 시간 오프셋](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)을 참조 하세요.

[[맨 위로](#top)이동]

## <a name="do-not-create-concurrency-objects-at-global-scope"></a><a name="global-scope"></a> 전역 범위에서 동시성 개체를 만들지 마십시오.

전역 범위에서 동시성 개체를 만드는 경우 교착 상태나 메모리 액세스 위반 등의 문제가 애플리케이션에서 발생할 수 있습니다.

예를 들어 동시성 런타임 개체를 만드는 경우 런타임은 아직 만들어지지 않은 경우 기본 스케줄러를 만듭니다. 전역 개체 생성 중에 만들어지는 런타임 개체가 적절하게 런타임이 이 기본 스케줄러를 만들게 합니다. 그러나 이 프로세스에는 내부 잠금이 사용되므로 동시성 런타임 인프라를 지원하는 다른 개체의 초기화를 방해할 수 있습니다. 이 내부 잠금은 아직 초기화되지 않은 다른 인프라 개체에 필요할 수 있기 때문에 교착 상태가 애플리케이션에서 발생할 수 있습니다.

다음 예제에서는 전역 [concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) 개체를 만드는 방법을 보여 줍니다. 이 패턴은 `Scheduler` 클래스뿐 아니라 동시성 런타임에서 제공하는 다른 모든 형식에도 적용됩니다. 애플리케이션에서 예기치 않은 동작이 발생할 수 있기 때문에 이 패턴을 따르지 않는 것이 좋습니다.

[!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]

개체를 만드는 올바른 방법의 예는 `Scheduler` [작업 스케줄러](../../parallel/concrt/task-scheduler-concurrency-runtime.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="do-not-use-concurrency-objects-in-shared-data-segments"></a><a name="shared-data"></a> 공유 데이터 세그먼트에서 동시성 개체 사용 안 함

동시성 런타임은 공유 데이터 섹션에서 동시성 개체를 사용 하는 것을 지원 하지 않습니다. 예를 들어 [data_seg](../../preprocessor/data-seg.md) 지시문에서 만든 데이터 섹션을 지원 하지 않습니다 `#pragma` . 프로세스 경계에서 공유 되는 동시성 개체는 런타임에 일관 되지 않거나 유효 하지 않은 상태로 전환할 수 있습니다.

[[맨 위로](#top)이동]

## <a name="see-also"></a>참고 항목

[동시성 런타임 모범 사례](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[PPL(병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[비동기 에이전트 라이브러리](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[작업 Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[동기화 데이터 구조](../../parallel/concrt/synchronization-data-structures.md)<br/>
[동기화 데이터 구조와 Windows API의 비교](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
[방법: Alloc 및 Free를 사용 하 여 메모리 성능 개선](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)<br/>
[방법: 초과 구독을 사용 하 여 대기 시간 오프셋](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)<br/>
[방법: 컨텍스트 클래스를 사용 하 여 협조적 세마포 구현](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[연습: User-Interface 스레드에서 작업 제거](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
[병렬 패턴 라이브러리의 모범 사례](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[비동기 에이전트 라이브러리의 모범 사례](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
