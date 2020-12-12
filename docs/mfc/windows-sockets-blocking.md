---
description: '자세한 정보: Windows 소켓: 차단'
title: 'Windows 소켓: 차단'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
ms.openlocfilehash: 21d1a2fb635f3d45e639c950a7ad1748dc3dda74
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197454"
---
# <a name="windows-sockets-blocking"></a>Windows 소켓: 차단

이 문서 및 두 개의 참조 문서에서는 Windows 소켓 프로그래밍의 몇 가지 문제를 설명합니다. 이 문서는 차단에 대해 설명합니다. 다른 문제는 [Windows 소켓: 바이트 순서](../mfc/windows-sockets-byte-ordering.md) 지정 및 [Windows 소켓: 문자열 변환](../mfc/windows-sockets-converting-strings.md)문서에서 설명 합니다.

[Casyncsocket](../mfc/reference/casyncsocket-class.md)클래스를 사용 하거나 클래스에서 파생 하는 경우 이러한 문제를 직접 관리 해야 합니다. 클래스를 사용 하거나 [CSocket](../mfc/reference/csocket-class.md)클래스에서 파생 하는 경우 MFC는 사용자를 위해 관리 합니다.

## <a name="blocking"></a>차단

소켓은 "차단 모드" 또는 "비차단 모드"일 수 있습니다. 차단(또는 동기) 모드에서 소켓의 함수는 작업을 완료할 수 있을 때가지 반환되지 않습니다. 이를 차단이라고 부르는 이유는 함수가 호출되는 소켓이 호출이 반환될 때까지 아무 것도 할 수 없이 차단되기 때문입니다. 예를 들어, 멤버 함수에 대 한 호출은 `Receive` 보내는 응용 프로그램이 보낼 때까지 기다리는 동안 완료 하는 데 시간이 오래 걸릴 수 있습니다 .이는를 사용 `CSocket` 하거나 차단 하는을 사용 하는 경우입니다 `CAsyncSocket` . `CAsyncSocket`개체가 비블로킹 모드 (비동기 작업) 이면 호출이 즉시 반환 되 고 [GetLastError](../mfc/reference/casyncsocket-class.md#getlasterror) 멤버 함수로 검색할 수 있는 현재 오류 코드는 **WSAEWOULDBLOCK** 입니다 .이는 호출에서 해당 모드로 인해 즉시 반환 되지 않았다는 것을 나타냅니다. ( `CSocket` **WSAEWOULDBLOCK** 를 반환 하지 않습니다. 이 클래스는 사용자를 위해 차단을 관리합니다.)

32비트 및 64비트 운영 체제(예: Windows 95 또는 Windows 98)와 16비트 운영 체제(예: Windows 3.1)에서는 소켓의 동작이 달라집니다. 16비트 운영 체제와 달리 32비트 및 64비트 운영 체제는 선점형 멀티태스킹을 사용하며 다중 스레딩을 제공합니다. 32비트 및 64비트 운영 체제에서는 별개의 작업자 스레드에 소켓을 넣을 수 있습니다. 스레드에 있는 소켓은 애플리케이션의 다른 작업을 간섭하지 않고, 차단 시 컴퓨팅 시간을 소비하지 않고 차단할 수 있습니다. 다중 스레드 프로그래밍에 대 한 자세한 내용은 [다중 스레딩](../parallel/multithreading-support-for-older-code-visual-cpp.md)문서를 참조 하세요.

> [!NOTE]
> 다중 스레드 애플리케이션에서는 `CSocket`의 차단 특성을 사용해서 사용자 인터페이스의 응답성에 영향을 주지 않고 프로그램의 디자인을 간소화할 수 있습니다. 주 스레드에서 사용자 인터페이스를 처리하고 대체 스레드에서 `CSocket` 프로세싱을 처리함으로써 이러한 논리적 작업을 구분할 수 있습니다. 다중 스레드가 아닌 애플리케이션에서 이러한 두 작업은 서로 결합되어 단일 스레드로 처리되어야 합니다. 즉, 필요에 따라 통신 요청을 처리할 수 있도록 `CAsyncSocket`을 사용하거나, 오래 걸리는 동기 작업 중에 사용자 작업을 처리할 수 있도록 `CSocket::OnMessagePending`을 재정의합니다.

이 설명의 나머지 부분은 16비트 운영 체제를 대상으로 하는 프로그래머를 위한 것입니다.

일반적으로 `CAsyncSocket`을 사용 중이면 차단 작업 사용을 피하고 대신 비동기적으로 작업을 수행해야 합니다. 비동기 작업에서, 예를 들어,를 호출한 후 **WSAEWOULDBLOCK** 오류 코드를 수신 하는 시점부터 `Receive` `OnReceive` 다시 읽을 수 있음을 알리기 위해 멤버 함수가 호출 될 때까지 기다립니다. 비동기 호출은 [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)와 같은 소켓의 적절 한 콜백 알림 함수를 다시 호출 하 여 수행 됩니다.

Windows에서 차단 호출은 좋지 않은 방법으로 고려됩니다. 기본적으로 [Casyncsocket](../mfc/reference/casyncsocket-class.md) 은 비동기 호출을 지원 하 고 콜백 알림을 사용 하 여 차단을 직접 관리 해야 합니다. 반면에 [CSocket](../mfc/reference/csocket-class.md)클래스는 동기적입니다. 이 클래스는 사용자를 위해 Windows 메시지를 제공하고 차단을 관리합니다.

차단에 대한 자세한 내용은 Windows Sockets 사양을 참조하십시오. "On" 함수에 대 한 자세한 내용은 [windows 소켓: 소켓 알림](../mfc/windows-sockets-socket-notifications.md) 및 [Windows 소켓: 소켓 클래스에서 파생](../mfc/windows-sockets-deriving-from-socket-classes.md)을 참조 하세요.

자세한 내용은 다음을 참조하세요.

- [Windows 소켓: CAsyncSocket 클래스 사용](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 소켓: 소켓과 함께 소켓 사용](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 소켓: 배경](../mfc/windows-sockets-background.md)

- [Windows 소켓: 스트림 소켓](../mfc/windows-sockets-stream-sockets.md)

- [Windows 소켓: 데이터 그램 소켓](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>참고 항목

[MFC의 Windows 소켓](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket:: OnSend](../mfc/reference/casyncsocket-class.md#onsend)
