---
description: '자세한 정보: Windows 소켓: 작업 순서'
title: 'Windows 소켓: 작업 순서'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], operations
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- sockets [MFC], operations
- stream sockets [MFC]
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
ms.openlocfilehash: 89870de642abcc8e0584c2c5dc93860eda9785e8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263376"
---
# <a name="windows-sockets-sequence-of-operations"></a>Windows 소켓: 작업 순서

이 문서에서는 서버 소켓과 클라이언트 소켓에 대 한 작업 순서를 나란히 보여 줍니다. 소켓은 개체를 사용 하기 때문에 `CArchive` 반드시 [스트림 소켓](../mfc/windows-sockets-stream-sockets.md)입니다.

## <a name="sequence-of-operations-for-a-stream-socket-communication"></a>스트림 소켓 통신용 작업 시퀀스

개체를 생성 하는 시점까지 `CSocketFile` 다음 시퀀스는 및 둘 다에 대해 몇 가지 매개 변수 차이를 사용 하 여 정확 합니다 `CAsyncSocket` `CSocket` . 이 시점부터 시퀀스는에만 해당 됩니다 `CSocket` . 다음 표에서는 클라이언트와 서버 간의 통신을 설정 하는 작업의 순서를 보여 줍니다.

### <a name="setting-up-communication-between-a-server-and-a-client"></a>서버와 클라이언트 간의 통신 설정

|서버|Client|
|------------|------------|
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5||
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|
|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> 또는<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> -또는 둘 다|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> 또는<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> -또는 둘 다|
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> 또는<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> 또는<br /><br /> `arOut << dwValue;`6|

1. 여기서 *Nport* 는 포트 번호입니다. 포트에 대 한 자세한 내용은 [Windows 소켓: 포트 및 소켓 주소](../mfc/windows-sockets-ports-and-socket-addresses.md) 를 참조 하십시오.

2. 클라이언트에서 연결할 수 있도록 서버는 항상 포트를 지정 해야 합니다. `Create`호출에서 주소를 지정 하기도 합니다. 클라이언트 쪽에서 사용 가능한 모든 포트를 사용 하도록 MFC에 요청 하는 기본 매개 변수를 사용 합니다.

3. 여기서 *Nport* 는 포트 번호이 고 *straddr* 는 컴퓨터 주소 또는 IP (인터넷 프로토콜) 주소입니다.

4. 컴퓨터 주소는 "ftp.microsoft.com", "microsoft.com" 등의 여러 가지 형식을 사용할 수 있습니다. IP 주소는 "점으로 구분 된 숫자" 형식 "127.54.67.32"을 사용 합니다. `Connect`함수는 주소가 점으로 표시 되는지 확인 합니다 (숫자가 네트워크에서 유효한 컴퓨터 인지 확인 하지 않음). 그렇지 않은 경우는 `Connect` 컴퓨터 이름을 다른 형식 중 하나로 가정 합니다.

5. 서버 쪽에서를 호출 하는 경우 `Accept` 새 소켓 개체에 대 한 참조를 전달 합니다. 먼저이 개체를 생성 해야 하지만이 개체에 대해를 호출 하지는 않습니다 `Create` . 이 소켓 개체가 범위를 벗어나면 연결이 닫힙니다. MFC는 **소켓** 핸들에 새 개체를 연결 합니다. 표시 된 것 처럼 스택에서 또는 힙에서 소켓을 생성할 수 있습니다.

6. 보관 및 소켓 파일은 범위를 벗어날 때 닫힙니다. 또한 소켓 개체의 소멸자는 개체가 범위를 벗어나면 해당 개체에 대 한 [Close](../mfc/reference/casyncsocket-class.md#close) 멤버 함수를 호출 합니다.

## <a name="additional-notes-about-the-sequence"></a>시퀀스에 대 한 추가 참고 사항

위의 표에 나와 있는 호출 시퀀스는 스트림 소켓에 대 한 것입니다. 연결 없는 데이터 그램 소켓에는 [Casyncsocket:: Connect](../mfc/reference/casyncsocket-class.md#connect), [Listen](../mfc/reference/casyncsocket-class.md#listen)및 [Accept](../mfc/reference/casyncsocket-class.md#accept) 호출이 필요 하지 않습니다 (필요에 따라 사용할 수 있음 `Connect` ). 대신 클래스를 사용 하는 경우 `CAsyncSocket` 데이터 그램 소켓은 `CAsyncSocket::SendTo` 및 `ReceiveFrom` 멤버 함수를 사용 합니다. 데이터 그램 소켓과 함께를 사용 하는 경우 `Connect` 및를 `Send` 사용 `Receive` 합니다. `CArchive` 는 데이터 그램에서 작동 하지 않기 때문에 `CSocket` 소켓이 데이터 그램이 면 보관과 함께를 사용 하지 마십시오.

[Csocketfile](../mfc/reference/csocketfile-class.md) 은의 일부 기능을 지원 하지 않습니다. `CFile` `CFile` `Seek` 소켓 통신에 적합 하지 않은와 같은 멤버는 사용할 수 없습니다. 이로 인해 일부 기본 MFC `Serialize` 함수는와 호환 되지 않습니다 `CSocketFile` . 이는 특히 클래스에 적용 됩니다 `CEditView` . 를 `CEditView` 사용 하 여 개체에 연결 된 개체를 통해 데이터를 직렬화 하지 않아야 합니다. `CArchive` `CSocketFile` `CEditView::SerializeRaw` `CEditView::Serialize` (문서화 되지 않음)를 대신 사용 하세요. [SerializeRaw](../mfc/reference/ceditview-class.md#serializeraw) 함수는를 `Seek` 지원 하지 않는와 같은 함수가 파일 개체에 있을 것으로 예상 합니다 `CSocketFile` .

자세한 내용은 다음을 참조하세요.

- [Windows 소켓: 소켓과 함께 소켓 사용](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 소켓: CAsyncSocket 클래스 사용](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 소켓: 포트 및 소켓 주소](../mfc/windows-sockets-ports-and-socket-addresses.md)

- [Windows 소켓: 스트림 소켓](../mfc/windows-sockets-stream-sockets.md)

- [Windows 소켓: 데이터 그램 소켓](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>참고 항목

[MFC의 Windows 소켓](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket 클래스](../mfc/reference/csocket-class.md)<br/>
[CAsyncSocket::Create](../mfc/reference/casyncsocket-class.md#create)<br/>
[CAsyncSocket:: Close](../mfc/reference/casyncsocket-class.md#close)
