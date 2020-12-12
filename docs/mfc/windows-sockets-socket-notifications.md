---
description: '자세한 정보: Windows 소켓: 소켓 알림'
title: 'Windows 소켓: 소켓 알림'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
ms.openlocfilehash: 856e954050753545a7ff64d3e111c648dc0284d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207659"
---
# <a name="windows-sockets-socket-notifications"></a>Windows 소켓: 소켓 알림

이 문서에서는 소켓 클래스의 알림 함수에 대해 설명 합니다. 이러한 멤버 함수는 프레임 워크가 중요 한 이벤트의 소켓 개체에 알리기 위해 호출 하는 콜백 함수입니다. 알림 함수는 다음과 같습니다.

- [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive): [Receive](../mfc/reference/casyncsocket-class.md#receive)를 호출 하 여 검색 하기 위해 버퍼에 데이터가 있음을 소켓에 알립니다.

- [Onsend](../mfc/reference/casyncsocket-class.md#onsend): 이제 [send](../mfc/reference/casyncsocket-class.md#send)를 호출 하 여 데이터를 보낼 수 있음을이 소켓에 알립니다.

- [Onaccept](../mfc/reference/casyncsocket-class.md#onaccept): [accept](../mfc/reference/casyncsocket-class.md#accept)를 호출 하 여 보류 중인 연결 요청을 수락할 수 있음을 수신 대기 소켓에 알립니다.

- [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect):이 연결 소켓에 연결 시도가 완료 되었음을 알립니다. 성공 또는 오류 일 수도 있습니다.

- [OnClose](../mfc/reference/casyncsocket-class.md#onclose):이 소켓에 연결 된 소켓이 닫 혔 음을 알립니다.

    > [!NOTE]
    >  추가 알림 함수는 [OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata)입니다. 이 알림은 보내는 소켓에 보낼 송신 소켓에 "대역 외" 데이터가 있음을 알려 줍니다. 대역외 데이터는 연결 된 각 스트림 소켓 쌍과 연결 된 논리적으로 독립적인 채널입니다. 대역 외 채널은 일반적으로 "긴급" 데이터를 전송 하는 데 사용 됩니다. MFC는 대역 외 데이터를 지원 합니다. [Casyncsocket](../mfc/reference/casyncsocket-class.md) 클래스에서 작업 하는 고급 사용자는 대역 외 채널을 사용 해야 할 수 있지만, [CSocket](../mfc/reference/csocket-class.md) 클래스의 사용자는 사용 하지 않는 것이 좋습니다. 이러한 데이터를 전달 하기 위한 두 번째 소켓을 만드는 것이 더 쉬운 방법입니다. 대역외 데이터에 대 한 자세한 내용은 Windows SDK에서 사용할 수 있는 Windows 소켓 사양을 참조 하십시오.

클래스에서 파생 하는 경우 `CAsyncSocket` 응용 프로그램에 관련 된 이러한 네트워크 이벤트에 대 한 알림 함수를 재정의 해야 합니다. 클래스에서 클래스를 파생 하는 경우 `CSocket` 관심 있는 알림 함수를 재정의할지 여부를 선택 합니다. 자체를 사용할 수도 있습니다 `CSocket` .이 경우 알림 함수는 기본적으로 아무 작업도 수행 하지 않습니다.

이러한 함수는 재정의 가능한 콜백 함수입니다. `CAsyncSocket` 및는 `CSocket` 메시지를 알림으로 변환 하지만 알림 함수를 사용 하려는 경우 응답 하는 방식을 구현 해야 합니다. 알림 함수는 읽을 데이터의 존재와 같이 소켓에 관심 있는 이벤트를 알릴 때 호출 됩니다.

MFC는 알림 함수를 호출 하 여 알림을 받을 때 소켓 동작을 사용자 지정할 수 있도록 합니다. 예를 들어 알림 함수에서를 호출할 수 있습니다. 즉, `Receive` `OnReceive` 읽을 데이터가 있다는 알림이 표시 되 면를 호출 하 `Receive` 여 읽습니다. 이 방법은 필요 하지 않지만 유효한 시나리오입니다. 또는 알림 함수를 사용 하 여 진행률을 추적 하 고 **추적** 메시지를 인쇄 하는 등의 작업을 할 수 있습니다.

파생 소켓 클래스에서 알림 함수를 재정의 하 고 구현을 제공 하 여 이러한 알림을 활용할 수 있습니다.

데이터를 받거나 보내는 등의 작업을 수행 하는 동안 `CSocket` 개체는 동기화 됩니다. 동기 상태에서 다른 소켓에 대해 수행 되는 모든 알림은 큐에 대기 하는 동안 현재 소켓이 원하는 알림을 대기 합니다. 예를 들어를 호출 하는 동안 `Receive` 소켓은 읽기 알림을 원합니다. 소켓이 동기 작업을 완료 하 고 다시 비동기 상태가 되 면 다른 소켓은 대기 중인 알림 수신을 시작할 수 있습니다.

> [!NOTE]
> 에서 `CSocket` `OnConnect` 알림 함수는 호출 되지 않습니다. 연결의 경우 `Connect` 연결이 완료 될 때 (성공 또는 오류 발생)를 반환 하는를 호출 합니다. 연결 알림이 처리 되는 방법은 MFC 구현에 자세히 설명 되어 있습니다.

각 알림 기능에 대 한 자세한 내용은 `CAsyncSocket` *MFC 참조* 의 클래스 아래에 있는 함수를 참조 하세요. 소스 코드와 MFC 샘플에 대 한 정보는 [Mfc 샘플](../overview/visual-cpp-samples.md#mfc-samples)을 참조 하세요.

자세한 내용은 다음을 참조하세요.

- [Windows 소켓: CAsyncSocket 클래스 사용](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 소켓: 소켓 클래스에서 파생](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows 소켓: 소켓과 보관 파일의 작동 방식](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows 소켓: 차단](../mfc/windows-sockets-blocking.md)

- [Windows 소켓: 바이트 순서 지정](../mfc/windows-sockets-byte-ordering.md)

- [Windows 소켓: 문자열 변환](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>참고 항목

[MFC의 Windows 소켓](../mfc/windows-sockets-in-mfc.md)
