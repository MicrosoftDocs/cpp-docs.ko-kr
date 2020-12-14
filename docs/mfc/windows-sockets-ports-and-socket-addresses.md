---
description: '자세한 정보: Windows 소켓: 포트 및 소켓 주소'
title: 'Windows 소켓: 포트 및 소켓 주소'
ms.date: 11/04/2016
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
ms.openlocfilehash: 354505796ff60cc8968b2e10a2aac98be2eb4666
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263402"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows 소켓: 포트 및 소켓 주소

이 문서에서는 Windows 소켓에서 사용 되는 "포트" 및 "주소" 라는 용어에 대해 설명 합니다.

## <a name="port"></a><a name="_core_port"></a> 포트인

포트는 서비스를 제공할 수 있는 고유한 프로세스를 식별 합니다. 현재 컨텍스트에서 포트는 Windows 소켓을 지 원하는 응용 프로그램과 연결 됩니다. 각 Windows 소켓 응용 프로그램을 고유 하 게 식별 하 여 한 번에 한 컴퓨터에서 둘 이상의 Windows 소켓 응용 프로그램을 실행할 수 있도록 하는 것이 좋습니다.

특정 포트는 FTP와 같은 일반적인 서비스에 예약 되어 있습니다. 이러한 종류의 서비스를 제공 하지 않는 한 이러한 포트를 사용 하지 않는 것이 좋습니다. Windows 소켓 사양은 이러한 예약 된 포트에 대해 자세히 설명 합니다. WINSOCK 파일입니다. H도 나열 합니다.

Windows 소켓 DLL에서 사용할 수 있는 포트를 선택할 수 있도록 하려면 포트 값으로 0을 전달 합니다. MFC에서 1024 보다 큰 포트 값을 선택 합니다. [Casyncsocket:: GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) 멤버 함수를 호출 하 여 MFC에서 선택한 포트 값을 검색할 수 있습니다.

## <a name="socket-address"></a><a name="_core_socket_address"></a> 소켓 주소

각 소켓 개체는 네트워크의 IP (인터넷 프로토콜) 주소와 연결 됩니다. 일반적으로 주소는 "ftp.microsoft.com"와 같은 컴퓨터 이름 또는 "128.56.22.8"와 같은 점으로 표시 되는 숫자입니다.

소켓을 만들려고 할 때 일반적으로 고유한 주소를 지정할 필요가 없습니다.

> [!NOTE]
> 컴퓨터에 네트워크 카드가 여러 개 있거나 (또는 응용 프로그램이 해당 컴퓨터에서 언젠가 실행 될 수 있음) 각각 다른 네트워크를 나타내는 것일 수 있습니다. 그렇다면 소켓이 사용할 네트워크 카드를 지정 하는 주소를 지정 해야 할 수 있습니다. 이는 고급 사용량과 가능한 이식성 문제입니다.

자세한 내용은 다음을 참조하세요.

- [Windows 소켓: CAsyncSocket 클래스 사용](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 소켓: 소켓과 함께 소켓 사용](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 소켓: 소켓과 보관 파일의 작동 방식](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows 소켓: 스트림 소켓](../mfc/windows-sockets-stream-sockets.md)

- [Windows 소켓: 데이터 그램 소켓](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>참고 항목

[MFC의 Windows 소켓](../mfc/windows-sockets-in-mfc.md)
