---
description: '자세히 알아보기: 동기화 데이터 구조'
title: 동기화 데이터 구조
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: d5e2e9e6d79f1e71a8f18f98d69fb794597d0ccb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169348"
---
# <a name="synchronization-data-structures"></a>동기화 데이터 구조

동시성 런타임는 여러 스레드의 공유 데이터에 대 한 액세스를 동기화 할 수 있는 여러 데이터 구조를 제공 합니다. 이러한 데이터 구조는 자주 수정 하는 공유 데이터를 포함 하는 경우에 유용 합니다. 예를 들어 중요 한 섹션과 같은 동기화 개체는 공유 리소스를 사용할 수 있을 때까지 다른 스레드가 대기 하도록 합니다. 따라서 이러한 개체를 사용 하 여 자주 사용 되는 데이터에 대 한 액세스를 동기화 하는 경우 응용 프로그램의 확장성이 손실 될 수 있습니다. [PPL (병렬 패턴 라이브러리)](../../parallel/concrt/parallel-patterns-library-ppl.md) 은 [동시성:: 결합할](../../parallel/concrt/reference/combinable-class.md) 수 있는 클래스를 제공 합니다 .이 클래스를 사용 하면 동기화 하지 않고도 여러 스레드나 작업 간에 리소스를 공유할 수 있습니다. 클래스에 대 한 자세한 내용은 `combinable` [병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)를 참조 하세요.

## <a name="sections"></a><a name="top"></a> 섹션이

이 항목에서는 다음과 같은 비동기 메시지 블록 형식에 대해 자세히 설명 합니다.

- [critical_section](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock 및 scoped_lock_read](#scoped_lock)

- [event](#event)

## <a name="critical_section"></a><a name="critical_section"></a> critical_section

[Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) 클래스는 다른 작업을 선점 하는 대신 다른 작업에 양보 하는 협조적 상호 제외 개체를 나타냅니다. 중요 섹션은 여러 스레드에서 공유 데이터에 대 한 단독 읽기 및 쓰기 액세스를 필요로 하는 경우에 유용 합니다.

`critical_section`클래스가 재진입이 아닌 경우 [Concurrency:: critical_section:: lock](reference/critical-section-class.md#lock) 메서드는 이미 잠금을 소유 하 고 있는 스레드에서 호출 하는 경우 [concurrency:: improper_lock](../../parallel/concrt/reference/improper-lock-class.md) 형식의 예외를 throw 합니다.

### <a name="methods-and-features"></a>메서드 및 기능

다음 표에서는 클래스에 의해 정의 되는 중요 한 메서드를 보여 줍니다 `critical_section` .

|메서드|설명|
|------------|-----------------|
|[lock](reference/critical-section-class.md#lock)|임계 영역을 가져옵니다. 호출 컨텍스트는 잠금을 획득할 때까지 차단 됩니다.|
|[try_lock](reference/critical-section-class.md#try_lock)|임계 영역을 가져오려고 시도 하지만 차단 하지는 않습니다.|
|[잠금을](reference/critical-section-class.md#unlock)|임계 영역을 해제 합니다.|

[[맨 위로](#top)이동]

## <a name="reader_writer_lock"></a><a name="reader_writer_lock"></a> reader_writer_lock

[Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 클래스는 공유 데이터에 대 한 스레드로부터 안전한 읽기/쓰기 작업을 제공 합니다. 여러 스레드가 공유 리소스에 대 한 동시 읽기 액세스를 요구 하지만 해당 공유 리소스에 거의 쓰지 않는 경우 판독기/작성기 잠금을 사용 합니다. 이 클래스는 한 번에 하나의 스레드만 개체에 대 한 쓰기 권한을 제공 합니다.

`reader_writer_lock` `critical_section` `critical_section` 개체에서 공유 리소스에 대 한 단독 액세스 권한을 획득 하 여 동시 읽기 액세스를 방지 하기 때문에 클래스는 클래스 보다 더 나은 성능을 얻을 수 있습니다.

클래스와 마찬가지로 `critical_section` 클래스는 `reader_writer_lock` 다른 작업을 선점 하는 대신 다른 작업에 양보 하는 협조적 상호 제외 개체를 나타냅니다.

공유 리소스에 써야 하는 스레드가 판독기/작성기 잠금을 획득 하는 경우에도 해당 리소스에 액세스 해야 하는 다른 스레드는 작성기가 잠금을 해제할 때까지 차단 됩니다. `reader_writer_lock`클래스는 대기 판독기를 차단 해제 하기 전에 대기 중인 기록기의 차단을 해제 하는 잠금입니다 *쓰기 기본 설정* 잠금의 예입니다.

클래스와 마찬가지로 `critical_section` 클래스는 `reader_writer_lock` 재진입 성이 아닙니다. [Concurrency:: reader_writer_lock:: lock](reference/reader-writer-lock-class.md#lock) 및 [concurrency:: reader_writer_lock:: lock_read](reference/reader-writer-lock-class.md#lock_read) 메서드는 `improper_lock` 이미 잠금을 소유한 스레드에 의해 호출 될 경우 형식의 예외를 throw 합니다.

> [!NOTE]
> `reader_writer_lock`클래스가 재진입이 아닌 경우 읽기 전용 잠금을 판독기/writer 잠금으로 업그레이드 하거나 읽기 전용 잠금으로 판독기/writer 잠금을 다운 그레이드할 수 없습니다. 이러한 작업 중 하나를 수행 하면 지정 되지 않은 동작이 생성 됩니다.

### <a name="methods-and-features"></a>메서드 및 기능

다음 표에서는 클래스에 의해 정의 되는 중요 한 메서드를 보여 줍니다 `reader_writer_lock` .

|메서드|설명|
|------------|-----------------|
|[lock](reference/reader-writer-lock-class.md#lock)|잠금에 대 한 읽기/쓰기 액세스 권한을 얻습니다.|
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|잠금에 대 한 읽기/쓰기 액세스를 얻으려고 시도 하지만 차단 하지는 않습니다.|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|잠금에 대 한 읽기 전용 액세스를 가져옵니다.|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|잠금에 대 한 읽기 전용 액세스를 얻으려고 시도 하지만 차단 하지는 않습니다.|
|[잠금을](reference/reader-writer-lock-class.md#unlock)|잠금을 해제합니다.|

[[맨 위로](#top)이동]

## <a name="scoped_lock-and-scoped_lock_read"></a><a name="scoped_lock"></a> scoped_lock 및 scoped_lock_read

`critical_section`및 `reader_writer_lock` 클래스는 상호 제외 개체를 사용 하는 방법을 간소화 하는 중첩 된 도우미 클래스를 제공 합니다. 이러한 도우미 클래스를 범위 지정 *잠금* 이라고 합니다.

`critical_section`클래스에는 [concurrency:: critical_section:: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) 클래스가 포함 되어 있습니다. 생성자는 제공 된 개체에 대 한 액세스 권한을 획득 합니다. `critical_section` 소멸자는 해당 개체에 대 한 액세스 권한을 해제 합니다. 클래스에는 `reader_writer_lock` 제공 된 개체에 대 한 쓰기 액세스를 관리 한다는 점을 제외 하 고와 유사한 [concurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) 클래스가 포함 되어 있습니다 `critical_section::scoped_lock` `reader_writer_lock` . 클래스에는 `reader_writer_lock` [concurrency:: reader_writer_lock:: scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class) 클래스도 포함 되어 있습니다. 이 클래스는 제공 된 개체에 대 한 읽기 액세스를 관리 `reader_writer_lock` 합니다.

범위가 지정 된 잠금은 및 개체를 수동으로 작업할 때 몇 가지 이점을 제공 `critical_section` `reader_writer_lock` 합니다. 일반적으로 스택에 범위가 지정 된 잠금을 할당 합니다. 범위가 지정 된 잠금은 상호 제외 개체가 제거 될 때 자동으로 액세스를 해제 합니다. 따라서 기본 개체를 수동으로 잠금 해제 하지 않습니다. 이는 함수에 문이 여러 개 포함 된 경우에 유용 **`return`** 합니다. 범위가 지정 된 잠금은 예외 안전 코드를 작성 하는 데 도움이 될 수도 있습니다. **`throw`** 문이 스택을 해제 하면 활성 범위 잠금의 소멸자가 호출 되므로 상호 제외 개체가 항상 올바르게 해제 됩니다.

> [!NOTE]
> , 및 클래스를 사용 하는 경우 `critical_section::scoped_lock` `reader_writer_lock::scoped_lock` `reader_writer_lock::scoped_lock_read` 기본 상호 제외 개체에 대 한 액세스를 수동으로 해제 하지 마십시오. 이렇게 하면 런타임이 잘못 된 상태가 될 수 있습니다.

## <a name="event"></a><a name="event"></a> 이벤트

[Concurrency:: event](../../parallel/concrt/reference/event-class.md) 클래스는 상태가 신호를 받거나 신호를 받을 수 없는 동기화 개체를 나타냅니다. 공유 데이터에 대 한 액세스를 보호 하기 위해 중요 한 섹션과 같은 동기화 개체와 달리 이벤트는 실행 흐름을 동기화 합니다.

`event`클래스는 한 작업이 다른 작업에 대해 작업을 완료 한 경우에 유용 합니다. 예를 들어 한 작업은 네트워크 연결 또는 파일에서 데이터를 읽기 위해 다른 작업에 신호를 보낼 수 있습니다.

### <a name="methods-and-features"></a>메서드 및 기능

다음 표에서는 클래스에 정의 된 몇 가지 중요 한 메서드를 보여 줍니다 `event` .

|메서드|설명|
|------------|-----------------|
|[대기한](reference/event-class.md#wait)|이벤트가 신호를 받을 때까지 기다립니다.|
|[set](reference/event-class.md#set)|이벤트를 신호 받음 상태로 설정 합니다.|
|[reset](reference/event-class.md#reset)|이벤트를 신호를 받지 않는 상태로 설정 합니다.|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|여러 이벤트가 신호를 받을 때까지 대기 합니다.|

### <a name="example"></a>예제

클래스를 사용 하는 방법을 보여 주는 예제는 `event` [동기화 데이터 구조와 Windows API의 비교](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)를 참조 하세요.

[[맨 위로](#top)이동]

## <a name="related-sections"></a>관련 단원

[동기화 데이터 구조와 Windows API의 비교](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
동기화 데이터 구조와 Windows API에서 제공 하는 동작을 비교 합니다.

[동시성 런타임](../../parallel/concrt/concurrency-runtime.md)<br/>
병렬 프로그래밍을 간소화하는 동시성 런타임에 대해 설명하고 관련 항목의 링크를 제공합니다.
