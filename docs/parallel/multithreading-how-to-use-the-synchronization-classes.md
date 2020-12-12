---
description: '자세한 정보: 다중 스레딩: MFC 동기화 클래스를 사용 하는 방법'
title: '다중 스레딩: MFC 동기화 클래스를 사용 하는 방법'
ms.date: 08/27/2018
helpviewer_keywords:
- MFC [C++], multithreading
- threading [MFC], synchronization classes
- resources [C++], multithreading
- thread-safe classes [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], thread-safe class design
- threading [C++], synchronization
- multithreading [C++], synchronization classes
- threading [C++], thread-safe class design
ms.assetid: f266d4c6-0454-4bda-9758-26157ef74cc5
ms.openlocfilehash: a62bdba992ef8b65c14991da26e098f545c30ccd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149918"
---
# <a name="multithreading-how-to-use-the-mfc-synchronization-classes"></a>다중 스레딩: MFC 동기화 클래스를 사용 하는 방법

스레드 간에 리소스 액세스를 동기화 하는 것은 다중 스레드 응용 프로그램을 작성할 때 일반적으로 발생 합니다. 두 개 이상의 스레드가 동시에 동일한 데이터에 액세스 하면 원치 않는 결과가 발생할 수 있습니다. 예를 들어 한 스레드가 구조체의 콘텐츠를 업데이트 하는 동안 다른 스레드가 동일한 구조체의 내용을 읽고 있을 수 있습니다. 읽기 스레드가 수신 하는 데이터 (이전 데이터, 새로 작성 된 데이터 또는 둘 다를 혼합 하 여)를 알 수 없습니다. MFC는이 문제를 해결 하는 데 도움이 되는 다양 한 동기화 및 동기화 액세스 클래스를 제공 합니다. 이 항목에서는 사용 가능한 클래스와 이러한 클래스를 사용 하 여 일반적인 다중 스레드 응용 프로그램에서 스레드로부터 안전한 클래스를 만드는 방법에 대해 설명 합니다.

일반적인 다중 스레드 응용 프로그램에는 스레드 간에 공유 되는 리소스를 나타내는 클래스가 있습니다. 제대로 설계 되 고 스레드로부터 안전 하 게 보호 되는 클래스에서는 동기화 함수를 호출할 필요가 없습니다. 모든 항목은 클래스에 대해 내부적으로 처리 되므로 클래스를 사용 하는 방법에 대 한 정보를 얻을 수 있을 뿐만 아니라 클래스를 사용 하는 방법에 집중할 수 있습니다. 완전히 스레드로부터 안전 하 게 보호 되는 클래스를 만드는 효과적인 방법은 동기화 클래스를 리소스 클래스에 병합 하는 것입니다. 동기화 클래스를 공유 클래스에 병합 하는 것은 간단한 프로세스입니다.

예를 들어 연결 된 계정 목록을 유지 관리 하는 응용 프로그램을 사용 합니다. 이 응용 프로그램은 별도의 창에서 최대 3 개의 계정을 검사할 수 있지만 특정 시간에 하나만 업데이트할 수 있습니다. 계정이 업데이트 되 면 업데이트 된 데이터가 네트워크를 통해 데이터 보관에 전송 됩니다.

이 예제 응용 프로그램에서는 세 가지 유형의 동기화 클래스를 모두 사용 합니다. 최대 3 개의 계정을 한 번에 검사할 수 있으므로 [CSemaphore](../mfc/reference/csemaphore-class.md) 를 사용 하 여 세 개의 뷰 개체에 대 한 액세스를 제한 합니다. 네 번째 계정을 보려는 시도가 발생 하면 응용 프로그램은 처음 3 개의 windows 중 하나가 닫히거나 실패할 때까지 대기 합니다. 계정이 업데이트 되 면 응용 프로그램은 [CCriticalSection](../mfc/reference/ccriticalsection-class.md) 를 사용 하 여 한 번에 하나의 계정만 업데이트 되도록 합니다. 업데이트에 성공 하면 이벤트가 신호를 받을 때까지 대기 하는 스레드를 해제 하는 [CEvent](../mfc/reference/cevent-class.md)신호를 보냅니다. 이 스레드는 새 데이터를 데이터 보관 파일로 보냅니다.

## <a name="designing-a-thread-safe-class"></a><a name="_mfc_designing_a_thread.2d.safe_class"></a> Thread-Safe 클래스 디자인

클래스를 완전히 스레드로부터 안전 하 게 만들려면 먼저 적절 한 동기화 클래스를 공유 클래스에 데이터 멤버로 추가 합니다. 이전 계정 관리 예제에서는 데이터 `CSemaphore` 멤버가 뷰 클래스에 추가 되 고, `CCriticalSection` 데이터 멤버가 연결 된 목록 클래스에 추가 되 고, 데이터 `CEvent` 멤버가 데이터 저장소 클래스에 추가 됩니다.

그런 다음 클래스의 데이터를 수정 하거나 제어 되는 리소스에 액세스 하는 모든 멤버 함수에 동기화 호출을 추가 합니다. 각 함수에서 [Csinglelock](../mfc/reference/csinglelock-class.md) 또는 [CMultiLock](../mfc/reference/cmultilock-class.md) 개체를 만들고 해당 개체의 함수를 호출 해야 합니다 `Lock` . 잠금 개체가 범위를 벗어나서 소멸 되 면 개체의 소멸자가를 호출 하 여 `Unlock` 리소스를 해제 합니다. 물론 `Unlock` 원하는 경우 직접 호출할 수 있습니다.

스레드로부터 안전한 클래스를 이러한 방식으로 디자인 하면 스레드로부터 안전 하지 않은 클래스로 쉽게 다중 스레드 응용 프로그램에서 사용할 수 있습니다. 단, 보안 수준이 높습니다. 동기화 개체 및 동기화 액세스 개체를 리소스의 클래스에 캡슐화 하면 동기화 코드를 유지 관리할 때의 단점 없이 완전히 스레드로부터 안전 하 게 프로그래밍할 때 모든 이점을 누릴 수가 제공 됩니다.

다음 코드 예제에서는 `m_CritSection` `CCriticalSection` 공유 리소스 클래스와 개체에 선언 된 데이터 멤버 (형식)를 사용 하 여이 메서드를 보여 줍니다 `CSingleLock` . 에서 파생 되는 공유 리소스의 동기화는 `CWinThread` `CSingleLock` 개체의 주소를 사용 하 여 개체를 만들어 시도 합니다 `m_CritSection` . 리소스를 잠그려고 시도 하면 공유 개체에서 작업이 수행 됩니다. 작업이 완료 되 면를 호출 하 여 리소스의 잠금이 해제 됩니다 `Unlock` .

```cpp
CSingleLock singleLock(&m_CritSection);
singleLock.Lock();
// resource locked
//.usage of shared resource...

singleLock.Unlock();
```

> [!NOTE]
> `CCriticalSection`다른 MFC 동기화 클래스와 달리에는 시간 제한의 잠금 요청 옵션이 없습니다. 스레드가 사용 가능 해질 때까지 대기 하는 시간은 무한 합니다.

이 방법의 단점은 클래스는 동기화 개체를 추가 하지 않고 동일한 클래스 보다 약간 느리게 된다는 것입니다. 또한 두 개 이상의 스레드가 개체를 삭제할 가능성이 있는 경우 병합 된 방법이 항상 작동 하지 않을 수 있습니다. 이 경우 별도의 동기화 개체를 유지 관리 하는 것이 좋습니다.

여러 상황에서 사용할 동기화 클래스를 결정 하는 방법에 대 한 자세한 내용은 [다중 스레딩: 동기화 클래스 사용 시기](multithreading-when-to-use-the-synchronization-classes.md)를 참조 하세요. 동기화에 대 한 자세한 내용은 Windows SDK의 [동기화](/windows/win32/Sync/synchronization) 를 참조 하세요. MFC의 다중 스레딩 지원에 대 한 자세한 내용은 [c + + 및 mfc를 사용 하는 다중 스레딩](multithreading-with-cpp-and-mfc.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[C++ 및 MFC에서 다중 스레딩](multithreading-with-cpp-and-mfc.md)
