---
description: '자세한 정보: Windows 소켓: 소켓 클래스에서 파생'
title: 'Windows 소켓: 소켓 클래스에서 파생시키기'
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from socket classes
- Windows Sockets [MFC], deriving from socket classes
- sockets [MFC], deriving from socket classes
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
ms.openlocfilehash: ba3526ddde4d254ff044fa09588d7764b16fb719
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132966"
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows 소켓: 소켓 클래스에서 파생시키기

이 문서에서는 소켓 클래스 중 하나에서 고유한 클래스를 파생 하 여 얻을 수 있는 몇 가지 기능을 설명 합니다.

[Casyncsocket](../mfc/reference/casyncsocket-class.md) 또는 [CSocket](../mfc/reference/csocket-class.md) 에서 고유한 소켓 클래스를 파생 시켜 고유한 기능을 추가할 수 있습니다. 특히 이러한 클래스는 재정의할 수 있는 여러 가상 멤버 함수를 제공 합니다. 이러한 함수에는 [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive), [onsend](../mfc/reference/casyncsocket-class.md#onsend), [Onsend](../mfc/reference/casyncsocket-class.md#onaccept), [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect)및 [OnClose](../mfc/reference/casyncsocket-class.md#onclose)가 포함 됩니다. 파생 소켓 클래스의 함수를 재정의 하 여 네트워크 이벤트가 발생할 때 제공 하는 알림을 활용할 수 있습니다. 프레임 워크는 이러한 알림 콜백 함수를 호출 하 여 읽을 수 있는 데이터의 수신과 같은 중요 한 소켓 이벤트를 알립니다. 알림 기능에 대 한 자세한 내용은 [Windows 소켓: 소켓 알림](../mfc/windows-sockets-socket-notifications.md)을 참조 하세요.

또한 클래스 `CSocket` 는 [OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending) 멤버 함수 (고급 재정의 가능)를 제공 합니다. 소켓이 Windows 기반 메시지를 펌프 하는 동안 MFC는이 함수를 호출 합니다. `OnMessagePending`를 재정의 하 여 Windows에서 특정 메시지를 검색 하 고이에 응답할 수 있습니다.

클래스에 제공 된의 기본 버전은 `OnMessagePending` `CSocket` 차단 호출이 완료 될 때까지 기다리는 동안 WM_PAINT 메시지의 메시지 큐를 검사 합니다. 그리기 메시지를 디스패치 하 여 디스플레이 품질을 개선 합니다. 유용한 작업을 수행 하는 것 외에도 함수를 직접 재정의할 수 있는 방법을 보여 줍니다. 또 다른 예로 다음 작업에을 사용 하는 것이 좋습니다 `OnMessagePending` . 네트워크 트랜잭션이 완료 될 때까지 기다리는 동안 모덜리스 대화 상자를 표시 한다고 가정 합니다. 이 대화 상자에는 사용자가 너무 오래 걸리는 차단 트랜잭션을 취소 하는 데 사용할 수 있는 취소 단추가 있습니다. `OnMessagePending`재정의는이 모덜리스 대화 상자와 관련 된 메시지를 펌프가 될 수 있습니다.

재정의에서 `OnMessagePending` **TRUE** 또는의 기본 클래스 버전에 대 한 호출의 반환을 반환 합니다 `OnMessagePending` . 완료 하려는 작업을 수행 하는 경우 기본 클래스 버전을 호출 합니다.

자세한 내용은 다음을 참조하세요.

- [Windows 소켓: 소켓과 함께 소켓 사용](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 소켓: CAsyncSocket 클래스 사용](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 소켓: 차단](../mfc/windows-sockets-blocking.md)

- [Windows 소켓: 바이트 순서 지정](../mfc/windows-sockets-byte-ordering.md)

- [Windows 소켓: 문자열 변환](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>참고 항목

[MFC의 Windows 소켓](../mfc/windows-sockets-in-mfc.md)
