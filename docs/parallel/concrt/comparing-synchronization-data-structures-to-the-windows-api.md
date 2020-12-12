---
description: '자세히 알아보기: 동기화 데이터 구조와 Windows API의 비교'
title: 동기화 데이터 구조와 Windows API의 비교
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
ms.openlocfilehash: b5c633c61d070e2cd687b6281597694a7533fe0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318418"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>동기화 데이터 구조와 Windows API의 비교

이 항목에서는 동시성 런타임에서 제공 하는 동기화 데이터 구조와 Windows API에서 제공 하는 동기화 데이터 구조의 동작을 비교 합니다.

동시성 런타임에서 제공 하는 동기화 데이터 구조는 *협조적 스레딩 모델* 을 따릅니다. 협조적 스레딩 모델에서 동기화 기본 형식은 다른 스레드에 대 한 처리 리소스를 명시적으로 생성 합니다. 이는 제어 스케줄러 또는 운영 체제에서 처리 리소스를 다른 스레드로 전송 하는 *선점형 스레딩 모델과* 다릅니다.

## <a name="critical_section"></a>critical_section

[Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) 클래스는 `CRITICAL_SECTION` 한 프로세스의 스레드에서만 사용할 수 있기 때문에 Windows 구조체와 유사 합니다. Windows API의 중요 한 섹션에 대 한 자세한 내용은 [임계 영역 개체](/windows/win32/Sync/critical-section-objects)를 참조 하세요.

## <a name="reader_writer_lock"></a>reader_writer_lock

[Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 클래스는 WINDOWS의 SRW (슬림 판독기/기록기) 잠금과 비슷합니다. 다음 표에서는 유사점과 차이점에 대해 설명 합니다.

| 기능 | `reader_writer_lock` 클래스 | SRW 잠금 |
|--|--|--|
| 비 재진입 | 예 | 예 |
| 판독기를 작성기로 승격할 수 있습니다 (업그레이드 지원). | 아니요 | 아니요 |
| 작성기의 수준을 판독기로 내릴 수 있습니다 (다운 그레이드 지원). | 아니요 | 아니요 |
| 쓰기 기본 설정 잠금 | 예 | 아니요 |
| 기록기에 대 한 FIFO 액세스 | 예 | 아니요 |

SRW 잠금에 대 한 자세한 내용은 Platform SDK의 [srw (슬림 판독기/Writer) 잠금](/windows/win32/sync/slim-reader-writer--srw--locks) 을 참조 하세요.

## <a name="event"></a>이벤트

[Concurrency:: event](../../parallel/concrt/reference/event-class.md) 클래스는 명명 되지 않은 Windows 수동 다시 설정 이벤트와 비슷합니다. 그러나 개체는 `event` 협조적으로 동작 하지만 Windows 이벤트는 미리 동작 합니다. Windows 이벤트에 대 한 자세한 내용은 [이벤트 개체](/windows/win32/Sync/event-objects)를 참조 하세요.

## <a name="example"></a>예제

### <a name="description"></a>설명

클래스와 Windows 이벤트의 차이를 더 잘 이해 하려면 `event` 다음 예제를 참조 하세요. 이 예제에서는 스케줄러가 최대 두 개의 동시 작업을 만든 다음 `event` 클래스 및 Windows 수동 다시 설정 이벤트를 사용 하는 두 개의 유사한 함수를 호출할 수 있도록 합니다. 각 함수는 먼저 공유 이벤트가 신호를 받을 때까지 대기 하는 여러 작업을 만듭니다. 각 함수는 실행 중인 작업을 생성 한 다음 이벤트에 신호를 보냅니다. 각 함수는 신호를 받은 이벤트를 기다립니다.

### <a name="code"></a>코드

[!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]

### <a name="comments"></a>주석

이 예제에서는 다음과 같은 샘플 출력을 생성 합니다.

```Output
Cooperative event:
    Context 0: waiting on an event.
    Context 1: waiting on an event.
    Context 2: waiting on an event.
    Context 3: waiting on an event.
    Context 4: waiting on an event.
    Setting the event.
    Context 5: received the event.
    Context 6: received the event.
    Context 7: received the event.
    Context 8: received the event.
    Context 9: received the event.
Windows event:
    Context 10: waiting on an event.
    Context 11: waiting on an event.
    Setting the event.
    Context 12: received the event.
    Context 14: waiting on an event.
    Context 15: received the event.
    Context 16: waiting on an event.
    Context 17: received the event.
    Context 18: waiting on an event.
    Context 19: received the event.
    Context 13: received the event.
```

`event`클래스가 협조적으로 동작 하기 때문에 이벤트에서 신호를 받은 상태로 전환 될 때 스케줄러가 처리 리소스를 다른 컨텍스트에 다시 할당할 수 있습니다. 따라서 클래스를 사용 하는 버전에서 더 많은 작업을 수행 `event` 합니다. Windows 이벤트를 사용 하는 버전에서는 대기 중인 각 태스크가 다음 작업을 시작 하기 전에 신호를 받은 상태로 전환 되어야 합니다.

태스크에 대 한 자세한 내용은 [작업 병렬 처리](../../parallel/concrt/task-parallelism-concurrency-runtime.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[동기화 데이터 구조](../../parallel/concrt/synchronization-data-structures.md)
