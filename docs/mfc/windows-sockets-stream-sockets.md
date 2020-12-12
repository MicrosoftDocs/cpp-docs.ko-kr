---
description: '자세한 정보: Windows 소켓: 스트림 소켓'
title: 'Windows 소켓: 스트림 소켓'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- stream sockets [MFC]
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
ms.openlocfilehash: b9e40be06ebb1de04466b5f13a46fe82fb3b0bd2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207646"
---
# <a name="windows-sockets-stream-sockets"></a>Windows 소켓: 스트림 소켓

이 문서에서는 사용 가능한 두 Windows 소켓 유형 중 하나인 스트림 소켓에 대해 설명 합니다. 다른 형식은 [데이터 그램 소켓](../mfc/windows-sockets-datagram-sockets.md)입니다.

스트림 소켓은 레코드 경계가 없는 데이터 흐름을 제공 합니다. 즉, 양방향 (응용 프로그램은 전이중 이며 소켓을 통해 전송 및 수신할 수 있음)을 포함 하는 바이트 스트림입니다. 스트림은 시퀀싱 된 reliably 데이터를 제공 하는 데 의존할 수 있습니다. ("시퀀싱"은 패킷이 전송 된 순서 대로 전달 됨을 의미 합니다. "Reliably"은 특정 패킷을 한 번만 가져오는 것을 의미 합니다. 스트림 메시지의 수신이 보장 되며 스트림은 많은 양의 데이터를 처리 하는 데 적합 합니다.

네트워크 전송 계층이 적절 한 크기의 패킷으로 데이터를 분할 하거나 그룹화 할 수 있습니다. `CSocket`이 클래스는 압축 및 압축 해제를 처리 합니다.

스트림은 명시적 연결을 기반으로 합니다. 소켓 A는 소켓 B에 대 한 연결을 요청 합니다. 소켓 B는 연결 요청을 허용 하거나 거부 합니다.

전화 통화는 스트림에 대 한 좋은 비유를 제공 합니다. 정상적인 상황에서 수신 파티는 중복 또는 손실 없이 말하는 순서 대로 말하는 내용을 수신 합니다. 스트림 소켓은 예를 들어 FTP (파일 전송 프로토콜) 등의 구현에서 적절 하 게 사용할 수 있으므로 임의의 크기의 ASCII 또는 이진 파일을 쉽게 전송할 수 있습니다.

스트림 소켓은 데이터의 도착을 보장 해야 하는 경우와 데이터 크기가 큰 경우 데이터 그램 소켓에 더 좋습니다. 스트림 소켓에 대 한 자세한 내용은 Windows 소켓 사양을 참조 하십시오. 사양은 Windows SDK에서 사용할 수 있습니다.

Stream sockets를 사용 하면 네트워크에서 수신 하는 모든 소켓에 브로드캐스트하는 데 데이터 그램 소켓을 사용 하도록 설계 된 응용 프로그램 보다 더 우수 합니다.

- 브로드캐스트 모델에는 네트워크 홍수 (또는 "스톰") 문제가 발생 합니다.

- 이후에 채택 된 클라이언트 서버 모델이 더 효율적입니다.

- 스트림 모델은 데이터 그램 모델에 없는 안정적인 데이터 전송을 제공 합니다.

- 최종 모델은 유니코드와 ANSI 소켓 응용 프로그램 간에 통신 하는 기능을 활용 하 여 클래스 CArchive는 CSocket 클래스에 적합 합니다.

    > [!NOTE]
    >  클래스를 사용 하 `CSocket` 는 경우 스트림을 사용 해야 합니다. 소켓 형식을 **SOCK_DGRAM** 로 지정 하면 MFC 어설션이 실패 합니다.

## <a name="see-also"></a>참고 항목

[MFC의 Windows 소켓](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows 소켓: 배경](../mfc/windows-sockets-background.md)
