---
description: '자세한 정보: Windows 소켓: 보관 파일을 사용 하 여 소켓 사용 방법'
title: 'Windows 소켓: 소켓과 아카이브를 함께 사용하는 방법'
ms.date: 11/19/2018
helpviewer_keywords:
- Windows Sockets [MFC], synchronous
- sockets [MFC], synchronous operation
- sockets [MFC], with archives
- synchronous state socket
- Windows Sockets [MFC], with archives
- two-state socket object
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
ms.openlocfilehash: 19b24a9942b7405304c9037091266b4535bffbc3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263545"
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows 소켓: 소켓과 아카이브를 함께 사용하는 방법

이 문서에서는 Windows 소켓을 통해 데이터를 보내고 받기 쉽도록 [CSocket](../mfc/reference/csocket-class.md) 개체, [csocketfile](../mfc/reference/csocketfile-class.md) 개체 및 [CArchive](../mfc/reference/carchive-class.md) 개체를 결합 하는 방법을 설명 합니다.

[Windows 소켓: 아카이브를 사용 하는 소켓의 예](../mfc/windows-sockets-example-of-sockets-using-archives.md) 에서는 함수를 제공 합니다 `PacketSerialize` . 예제의 archive 개체는 `PacketSerialize` MFC [직렬화](../mfc/reference/cobject-class.md#serialize) 함수에 전달 된 보관 개체와 매우 유사 하 게 작동 합니다. 중요 한 차이점은 소켓의 경우 보관은 표준 [CFile](../mfc/reference/cfile-class.md) 개체 (일반적으로 디스크 파일에 연결 됨)에 연결 되지 않고 개체에 연결 된다는 것입니다 `CSocketFile` . 개체는 디스크 파일에 연결 하는 대신 `CSocketFile` 개체에 연결 `CSocket` 됩니다.

`CArchive`개체는 버퍼를 관리 합니다. 저장 (송신) 보관의 버퍼가 가득 차면 연결 된 `CFile` 개체는 버퍼의 내용을 씁니다. 소켓에 연결 된 보관의 버퍼를 플러시하는 것은 메시지를 보내는 것과 같습니다. 로딩 (수신) 보관의 버퍼가 가득 차면 `CFile` 개체는 버퍼를 다시 사용할 수 있을 때까지 읽기를 중지 합니다.

클래스는 `CSocketFile` 에서 파생 `CFile` 되지만 위치 지정 함수 ( [](../mfc/reference/cfile-class.md) `Seek` , `GetLength` , `SetLength` 등), 잠금 함수 ( `LockRange` , `UnlockRange` ) 또는 `GetPosition` 함수와 같은 CFile 멤버 함수는 지원 하지 않습니다. 모든 [Csocketfile](../mfc/reference/csocketfile-class.md) 개체는 연결 된 개체와의 바이트 시퀀스를 쓰거나 읽어야 합니다 `CSocket` . 파일이 관련 되어 있지 않기 때문에 및 등의 작업은 `Seek` `GetPosition` 적절 하지 않습니다. `CSocketFile` 는에서 파생 `CFile` 되므로 일반적으로 이러한 멤버 함수를 모두 상속 합니다. 이를 방지 하기 위해에서 지원 되지 않는 `CFile` 멤버 함수를 재정의 `CSocketFile` 하 여 [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)를 throw 합니다.

`CSocketFile`개체는 개체의 멤버 함수 `CSocket` 를 호출 하 여 데이터를 보내거나 받습니다.

다음 그림은 통신의 양쪽에 있는 이러한 개체 간의 관계를 보여 줍니다.

![CArchive, CSocketFile 및 CSocket](../mfc/media/vc38ia1.gif "CArchive, CSocketFile 및 CSocket") <br/>
CArchive, CSocketFile 및 CSocket

이 처럼 복잡 한 이유는 소켓의 세부 정보를 직접 관리할 필요가 없도록 하는 것입니다. 소켓, 파일 및 보관 파일을 만든 다음 보관 파일에 삽입 하거나 보관 파일에서 추출 하 여 데이터를 보내거나 받는 것을 시작 합니다. [CArchive](../mfc/reference/carchive-class.md), [Csocketfile](../mfc/reference/csocketfile-class.md)및 [CSocket](../mfc/reference/csocket-class.md) 은 백그라운드에서 세부 정보를 관리 합니다.

`CSocket`개체는 실제로 비동기 (일반적인 상태)와 같은 두 가지 상태 개체 이며 경우에 따라 동기식입니다. 비동기 상태에서 소켓은 프레임 워크에서 비동기 알림을 받을 수 있습니다. 그러나 데이터를 받거나 보내는 등의 작업을 수행 하는 동안에는 소켓이 동기식이 됩니다. 즉, 소켓은 동기 작업이 완료 될 때까지 추가 비동기 알림을 받지 않습니다. 모드를 전환 하므로 예를 들어 다음과 같은 작업을 수행할 수 있습니다.

[!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]

가 `CSocket` 두 개의 상태 개체로 구현 되지 않은 경우 이전 알림을 처리 하는 동안 동일한 종류의 이벤트에 대 한 추가 알림을 받을 수 있습니다. 예를 들어를 `OnReceive` 처리 하는 동안 알림을 받을 수 있습니다 `OnReceive` . 위의 코드 조각에서 보관 파일을 추출 하면 `str` 재귀가 발생할 수 있습니다. 상태를 전환 하면에서 `CSocket` 추가 알림을 방지 하 여 재귀가 방지 됩니다. 일반 규칙은 알림 내에 알림이 없습니다.

> [!NOTE]
> 는 `CSocketFile` 개체 없이 (제한 된) 파일로도 사용할 수 있습니다 `CArchive` . 기본적으로 `CSocketFile` 생성자의 *bArchiveCompatible* 매개 변수는 **TRUE** 입니다. 이는 파일 개체를 보관에 사용할 수 있도록 지정 합니다. Archive 없이 file 개체를 사용 하려면 *bArchiveCompatible* 매개 변수에서 **FALSE** 를 전달 합니다.

"보관 호환" 모드에서 `CSocketFile` 개체는 더 나은 성능을 제공 하 고 "교착 상태"의 위험을 줄입니다. 교착 상태는 송신 및 수신 소켓이 서로 대기 중이거나 공통 리소스를 기다리는 경우에 발생 합니다. 이 상황은 개체가 개체를 사용 하는 `CArchive` 방식으로 작동 하는 경우에 발생할 수 있습니다 `CSocketFile` `CFile` . 에서 `CFile` 보관은 요청 된 것 보다 더 짧은 바이트를 수신 하는 경우 파일의 끝에 도달한 것으로 간주할 수 있습니다. 그러나를 사용 하는 경우 `CSocketFile` 데이터는 메시지를 기반으로 합니다. 버퍼는 여러 메시지를 포함할 수 있으므로 요청 된 바이트 수를 초과 하면 파일의 끝을 의미 하지 않습니다. 이 경우 응용 프로그램은에서와 같이 차단 하지 않으며 `CFile` 버퍼가 비어 있을 때까지 버퍼에서 메시지를 계속 읽을 수 있습니다. 의 [Isbufferempty](../mfc/reference/carchive-class.md#isbufferempty) 함수는 `CArchive` 이러한 경우 보관의 버퍼 상태를 모니터링 하는 데 유용 합니다.

자세한 내용은 [Windows 소켓: 보관 파일에 소켓 사용](../mfc/windows-sockets-using-sockets-with-archives.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC의 Windows 소켓](../mfc/windows-sockets-in-mfc.md)<br/>
[CObject:: Serialize](../mfc/reference/cobject-class.md#serialize)
