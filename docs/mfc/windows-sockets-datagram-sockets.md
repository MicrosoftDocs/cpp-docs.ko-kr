---
description: '자세한 정보: Windows 소켓: 데이터 그램 소켓'
title: 'Windows 소켓: 데이터그램 소켓'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
ms.openlocfilehash: 8de374d6e96348504d4b1fc126c1607c029cd6c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132979"
---
# <a name="windows-sockets-datagram-sockets"></a>Windows 소켓: 데이터그램 소켓

이 문서에서는 사용 가능한 두 Windows 소켓 유형 중 하나인 데이터 그램 소켓에 대해 설명 합니다. (다른 형식은 [스트림 소켓](../mfc/windows-sockets-stream-sockets.md)입니다.)

데이터 그램 소켓은 시퀀싱 또는 reliably 보장 되지 않는 양방향 데이터 흐름을 지원 합니다. 데이터 그램이 안정적이 지 않을 수도 있습니다. 이러한 사용자는 도착 하지 못할 수 있습니다. 데이터 그램 데이터는 잘못 된 순서로 도착할 수 있으며 중복 될 수 있지만, 레코드가 수신자의 내부 크기 제한 보다 작은 경우 데이터의 레코드 경계는 유지 됩니다. 사용자는 시퀀싱 및 안정성을 관리할 책임이 있습니다. 안정성은 LAN (local area network)에는 적합 하지만 인터넷과 같은 광역 네트워크 [WAN]에서는 더 저렴 합니다.

데이터 그램은 "연결 없음"입니다. 즉, 명시적 연결이 설정 되지 않습니다. 지정 된 소켓에 데이터 그램 메시지를 보내고 지정 된 소켓에서 메시지를 받을 수 있습니다.

데이터 그램 소켓의 예로는 네트워크에서 시스템 클럭을 동기화 된 상태로 유지 하는 응용 프로그램이 있습니다. 이는 많은 수의 네트워크 주소에 메시지 브로드캐스팅 이상의 설정에서 데이터 그램 소켓의 추가 기능을 보여 줍니다.

데이터 그램 소켓은 레코드 지향 데이터에 대 한 스트림 소켓 보다 좋습니다. 데이터 그램 소켓에 대 한 자세한 내용은 Windows SDK에서 사용할 수 있는 Windows 소켓 사양을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[MFC의 Windows 소켓](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows 소켓: 배경](../mfc/windows-sockets-background.md)
