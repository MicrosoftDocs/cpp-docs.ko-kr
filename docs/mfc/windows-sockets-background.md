---
description: '자세한 정보: Windows 소켓: 배경'
title: 'Windows 소켓: 배경'
ms.date: 11/04/2016
helpviewer_keywords:
- record-oriented data [MFC]
- e-mail [MFC]
- Internet Protocol Suite
- mail [MFC]
- communications [MFC], domain
- Windows Sockets [MFC], stream sockets
- mail [MFC], programming for
- sockets [MFC], stream sockets
- datagram sockets [MFC]
- SOCKET handle
- data types [MFC], socket
- e-mail [MFC], programming for
- X Window servers
- sequenced data flow
- stream sockets [MFC]
ms.assetid: f60d4ed2-bf23-4a0e-98d2-fee77e8473dd
ms.openlocfilehash: 9ac373f5f81dfe3914664d14122a7a6bd46cda40
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214470"
---
# <a name="windows-sockets-background"></a>Windows 소켓: 배경

이 문서에서는 Windows 소켓의 특성과 용도에 대해 설명 합니다. 또한이 문서는 다음과 같습니다.

- [용어 "소켓"을 정의](#_core_definition_of_a_socket)합니다.

- [소켓 핸들 데이터 형식을 설명](#_core_the_socket_data_type)합니다.

- [소켓의 용도를 설명](#_core_uses_for_sockets)합니다.

Windows 소켓 사양은 Microsoft Windows 용 이진 호환 네트워크 프로그래밍 인터페이스를 정의 합니다. Windows 소켓은 캘리포니아 Berkeley의 대학에서 Berkeley 소프트웨어 배포 (BSD, 릴리스 4.3)의 UNIX 소켓 구현을 기반으로 합니다. 이 사양에는 BSD 스타일의 소켓 루틴 및 Windows 고유의 확장이 모두 포함 되어 있습니다. Windows 소켓을 사용 하면 응용 프로그램이 Windows 소켓 API를 준수 하는 모든 네트워크에서 통신할 수 있습니다. Win32에서 Windows 소켓은 스레드로부터의 안전성을 제공 합니다.

많은 네트워크 소프트웨어 공급 업체는 TCP/IP (전송 제어 프로토콜/인터넷 프로토콜), XNS (Xerox Network System), Digital Corporation Corporation의 DECNet 프로토콜, Novell Corporation의 Internet Packet Exchange/시퀀싱 압축 된 Exchange (IPX/SPX) 및 기타를 비롯 한 네트워크 프로토콜에서 Windows 소켓을 지원 합니다. 현재 Windows 소켓 사양은 TCP/IP에 대 한 소켓 추상화를 정의 하지만 모든 네트워크 프로토콜은 Windows 소켓을 구현 하는 자체 버전의 DLL (동적 연결 라이브러리)을 제공 하 여 Windows 소켓을 준수할 수 있습니다. Windows 소켓으로 작성 된 상용 응용 프로그램의 예로는 X Windows 서버, 터미널 에뮬레이터 및 전자 메일 시스템이 있습니다.

> [!NOTE]
> Windows 소켓의 용도는 네트워크에 대 한 지식이 필요 하지 않도록 기본 네트워크를 추상화 하 여 소켓을 지 원하는 모든 네트워크에서 응용 프로그램을 실행할 수 있도록 하는 것입니다. 따라서이 설명서에서는 네트워크 프로토콜의 세부 정보에 대해 설명 하지 않습니다.

MFC 라이브러리 (MFC)는 두 개의 클래스를 제공 하 여 Windows 소켓 API를 사용한 프로그래밍을 지원 합니다. 이러한 클래스 중 하나 `CSocket` 는 네트워크 통신 프로그래밍을 간소화 하는 높은 수준의 추상화를 제공 합니다.

Windows 소켓 사양, Windows 소켓: Microsoft Windows의 네트워크 컴퓨팅을 위한 오픈 인터페이스 (현재 버전 1.1)는 TCP/IP 커뮤니티의 많은 개인 및 회사에서 개방 된 네트워킹 표준으로 개발 되었으며 무료로 사용할 수 있습니다. 소켓 프로그래밍 모델은 현재 인터넷 프로토콜 모음을 사용 하 여 하나의 "통신 도메인"을 지원 합니다. 사양은 Windows SDK에서 사용할 수 있습니다.

> [!TIP]
> 소켓은 인터넷 프로토콜 모음을 사용 하기 때문에 "information 고속도로"에서 인터넷 통신을 지 원하는 응용 프로그램의 기본 경로입니다.

## <a name="definition-of-a-socket"></a><a name="_core_definition_of_a_socket"></a> 소켓 정의

소켓은 통신 엔드포인트로, Windows 소켓 응용 프로그램이 네트워크를 통해 데이터 패킷을 보내거나 받는 데 사용할 수 있는 개체입니다. 소켓은 형식을 포함 하 고 실행 중인 프로세스와 연결 되며 이름을 가질 수 있습니다. 현재 소켓은 일반적으로 인터넷 프로토콜 모음을 사용 하는 동일한 "통신 도메인"의 다른 소켓과만 데이터를 교환 합니다.

두 종류의 소켓은 양방향입니다. 양방향으로 양방향으로 통신할 수 있는 데이터 흐름입니다 (전이중).

두 개의 소켓 형식을 사용할 수 있습니다.

- 스트림 소켓

   스트림 소켓은 레코드 경계 없는 데이터 흐름을 제공 합니다. 바이트 스트림입니다. 스트림은 배달 되도록 보장 되며 올바르게 시퀀싱 되 고 reliably 됩니다.

- 데이터그램 소켓

   데이터 그램 소켓은 배달 되지 않을 수 있는 레코드 지향 데이터 흐름을 지원 하며 전송 또는 reliably 시퀀싱 되지 않을 수 있습니다.

"시퀀싱"은 패킷이 전송 된 순서 대로 전달 됨을 의미 합니다. "Reliably"은 특정 패킷을 한 번만 가져오는 것을 의미 합니다.

> [!NOTE]
> XNS와 같은 일부 네트워크 프로토콜에서 스트림은 바이트 스트림이 아닌 레코드의 스트림으로 기록 될 수 있습니다. 그러나 보다 일반적인 TCP/IP 프로토콜에서 스트림은 바이트 스트림입니다. Windows 소켓은 기본 프로토콜과 독립적인 추상화 수준을 제공 합니다.

이러한 형식 및 해당 상황에서 사용할 소켓 종류에 대 한 자세한 내용은 [Windows 소켓: 스트림 소켓](../mfc/windows-sockets-stream-sockets.md) 및 [Windows 소켓: 데이터 그램 소켓](../mfc/windows-sockets-datagram-sockets.md)을 참조 하세요.

## <a name="the-socket-data-type"></a><a name="_core_the_socket_data_type"></a> SOCKET 데이터 형식입니다.

각 MFC 소켓 개체는 Windows 소켓 개체에 대 한 핸들을 캡슐화 합니다. 이 핸들의 데이터 형식은 **소켓** 입니다. **소켓** 핸들은 창의와 유사 합니다 `HWND` . MFC 소켓 클래스는 캡슐화 된 핸들에 대 한 작업을 제공 합니다.

**소켓** 데이터 형식은 Windows SDK에 자세히 설명 되어 있습니다. Windows 소켓에서 "소켓 데이터 형식 및 오류 값"을 참조 하세요.

## <a name="uses-for-sockets"></a><a name="_core_uses_for_sockets"></a> 소켓 사용

소켓은 세 개 이상의 통신 컨텍스트에서 매우 유용 합니다.

- 클라이언트/서버 모델.

- 메시징 응용 프로그램과 같은 피어 투 피어 시나리오.

- 수신 응용 프로그램에서 메시지를 함수 호출로 해석 하도록 하 여 RPC (원격 프로시저 호출)를 만듭니다.

> [!TIP]
> MFC 소켓을 사용 하는 이상적인 사례는 두 end에서 모두 MFC를 사용 하 여 통신의 양쪽 끝을 작성 하는 경우입니다. 비 MFC 응용 프로그램과 통신 하는 경우의 사례를 관리 하는 방법을 비롯 하 여이 항목에 대 한 자세한 내용은 [Windows 소켓: 바이트 순서](../mfc/windows-sockets-byte-ordering.md)지정을 참조 하세요.

자세한 내용은 Windows 소켓 사양: **ntohs**, **ntohl**, **htons**, **htonl** 을 참조 하세요. 또한 다음 항목을 참조 하세요.

- [Windows 소켓: 소켓과 함께 소켓 사용](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 소켓: 아카이브를 사용 하는 소켓의 예](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows 소켓: CAsyncSocket 클래스 사용](../mfc/windows-sockets-using-class-casyncsocket.md)

## <a name="see-also"></a>참고 항목

[MFC의 Windows 소켓](../mfc/windows-sockets-in-mfc.md)
