---
description: '자세한 정보: Windows 소켓: 바이트 순서 지정'
title: 'Windows 소켓: 바이트 순서 지정'
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: d143967fdcc9b4d1dac772bf0fe25b67d70aef53
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118656"
---
# <a name="windows-sockets-byte-ordering"></a>Windows 소켓: 바이트 순서 지정

이 문서 및 두 개의 참조 문서에서는 Windows 소켓 프로그래밍의 몇 가지 문제를 설명합니다. 이 문서에서는 바이트 순서 지정에 대해 설명 합니다. 다른 문제는 [Windows 소켓: 차단](../mfc/windows-sockets-blocking.md) 및 [Windows 소켓: 문자열 변환](../mfc/windows-sockets-converting-strings.md)문서에서 설명 합니다.

[Casyncsocket](../mfc/reference/casyncsocket-class.md)클래스를 사용 하거나 클래스에서 파생 하는 경우 이러한 문제를 직접 관리 해야 합니다. 클래스를 사용 하거나 [CSocket](../mfc/reference/csocket-class.md)클래스에서 파생 하는 경우 MFC는 사용자를 위해 관리 합니다.

## <a name="byte-ordering"></a>바이트 순서 지정

컴퓨터 아키텍처 마다 다른 바이트 순서를 사용 하 여 데이터를 저장 하는 경우가 있습니다. 예를 들어 Intel 기반 컴퓨터는 Macintosh (Motorola) 컴퓨터의 반대 순서로 데이터를 저장 합니다. "작은 Endian" 라는 Intel 바이트 순서는 네트워크 표준 "빅 Endian" 순서의 반대 이기도 합니다. 다음 표에서는 이러한 용어에 대해 설명 합니다.

### <a name="big--and-little-endian-byte-ordering"></a>빅 및 Little-Endian 바이트 순서 지정

|바이트 순서 지정|의미|
|-------------------|-------------|
|Big-Endian|가장 중요 한 바이트는 단어의 왼쪽 끝에 있습니다.|
|Little-Endian|가장 중요 한 바이트는 단어의 오른쪽 끝에 있습니다.|

일반적으로 네트워크를 통해 보내고 받는 데이터에 대 한 바이트 순서 변환에 대해 걱정할 필요가 없지만 바이트 순서를 변환 해야 하는 경우가 있습니다.

## <a name="when-you-must-convert-byte-orders"></a>바이트 순서를 변환 해야 하는 경우

다음과 같은 경우에는 바이트 순서를 변환 해야 합니다.

- 다른 컴퓨터로 보내는 데이터가 아니라 네트워크에서 해석 해야 하는 정보를 전달 합니다. 예를 들어 네트워크에서 인식 해야 하는 포트 및 주소를 전달할 수 있습니다.

- 통신 중인 서버 응용 프로그램이 MFC 응용 프로그램이 아닙니다 .이 응용 프로그램에 대 한 소스 코드가 없습니다. 이는 두 컴퓨터가 같은 바이트 순서를 공유 하지 않는 경우 바이트 순서 변환을 호출 합니다.

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>바이트 순서를 변환 하지 않아도 되는 경우

다음과 같은 상황에서 바이트 순서를 변환 하는 작업을 방지할 수 있습니다.

- 양쪽 끝의 컴퓨터는 바이트 교체에 동의할 수 없으며 두 컴퓨터에서 모두 동일한 바이트 순서를 사용 합니다.

- 통신할 서버는 MFC 응용 프로그램입니다.

- 통신 하는 서버에 대 한 소스 코드가 있으므로 바이트 순서를 변환 해야 하는지 여부를 명시적으로 알 수 있습니다.

- 서버를 MFC로 이식할 수 있습니다. 이 작업은 매우 간단 하며 결과는 일반적으로 작고 속도가 더 빠릅니다.

[Casyncsocket](../mfc/reference/casyncsocket-class.md)을 사용 하려면 필요한 바이트 순서 변환을 직접 관리 해야 합니다. Windows 소켓은 "빅 Endian" 바이트 순서 모델을 표준화 하 고이 순서와 다른 순서 간에 변환 하는 함수를 제공 합니다. 그러나 [CSocket](../mfc/reference/csocket-class.md)과 함께 사용 하는 [CArchive](../mfc/reference/carchive-class.md)는 반대 ("작은 Endian") 순서를 사용 하지만 `CArchive` 바이트 순서 변환에 대 한 세부 정보를 처리 합니다. 응용 프로그램에서이 표준 순서를 사용 하거나 Windows 소켓 바이트 순서 변환 함수를 사용 하 여 코드를 더 이식 가능 하 게 만들 수 있습니다.

MFC 소켓을 사용 하는 이상적인 사례는 두 end에서 모두 MFC를 사용 하 여 통신의 양쪽 끝을 작성 하는 경우입니다. FTP 서버와 같은 비 MFC 응용 프로그램과 통신 하는 응용 프로그램을 작성 하는 경우 Windows 소켓 변환 루틴 **ntohs**, **ntohl**, **htons** 및 **htonl** 를 사용 하 여 보관 개체에 데이터를 전달 하기 전에 직접 바이트 교체를 관리 해야 합니다. 비 MFC 응용 프로그램과 통신 하는 데 사용 되는 이러한 함수의 예는이 문서의 뒷부분에 나옵니다.

> [!NOTE]
> 통신의 다른 쪽 끝이 MFC 응용 프로그램이 아닌 경우 수신기가이를 처리할 수 없기 때문에에서 파생 된 c + + 개체를 보관으로 스트리밍하는 것도 피해 야 합니다 `CObject` . [Windows 소켓: 보관 파일에 소켓 사용](../mfc/windows-sockets-using-sockets-with-archives.md)에 대 한 참고를 참조 하세요.

바이트 주문에 대 한 자세한 내용은 Windows SDK에서 사용할 수 있는 Windows 소켓 사양을 참조 하십시오.

## <a name="a-byte-order-conversion-example"></a>Byte-Order 변환 예

다음 예제에서는 보관을 사용 하는 개체에 대 한 serialization 함수를 보여 줍니다 `CSocket` . 또한 Windows 소켓 API에서 바이트 순서 변환 함수를 사용 하는 방법을 보여 줍니다.

이 예제에서는 소스 코드에 액세스할 수 없는 비 MFC 서버 응용 프로그램과 통신 하는 클라이언트를 작성 하는 시나리오를 제공 합니다. 이 시나리오에서는 비 MFC 서버에서 표준 네트워크 바이트 순서를 사용 한다고 가정 합니다. 반면, MFC 클라이언트 응용 프로그램은 개체를 포함 하는 개체를 사용 `CArchive` `CSocket` 하며, `CArchive` 네트워크 표준과 반대 되는 "작은 Endian" 바이트 순서를 사용 합니다.

통신을 계획 하는 비 MFC 서버가 다음과 같은 메시지 패킷에 대해 설정 된 프로토콜을 사용 한다고 가정 합니다.

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

MFC 용어로 다음과 같이 표현 됩니다.

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

C + +에서은 **`struct`** 기본적으로 클래스와 동일 합니다. 구조체에는 `Message` `Serialize` 위에 선언 된 멤버 함수와 같은 멤버 함수가 있을 수 있습니다. `Serialize`멤버 함수는 다음과 같습니다.

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

이 예제에서는 한 쪽 끝에 비 MFC 서버 응용 프로그램의 바이트 순서와 `CArchive` 다른 쪽 end의 mfc 클라이언트 응용 프로그램에서 사용 되는의 차이를 명확 하 게 하기 때문에 데이터의 바이트 순서 변환을 호출 합니다. 이 예에서는 Windows 소켓이 제공 하는 몇 가지 바이트 순서 변환 함수를 보여 줍니다. 다음 표에서는 이러한 함수에 대해 설명 합니다.

### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows 소켓 Byte-Order 변환 함수

|함수|용도|
|--------------|-------------|
|**ntohs**|16 비트 수량을 네트워크 바이트 순서에서 호스트 바이트 순서 (빅 Endian-Endian)로 변환 합니다.|
|**ntohl**|32 비트 수량을 네트워크 바이트 순서에서 호스트 바이트 순서 (빅 Endian-Endian)로 변환 합니다.|
|**Htons**|16 비트 수량을 호스트 바이트 순서에서 네트워크 바이트 순서 (작은 Endian에서 빅 Endian)로 변환 합니다.|
|**Htonl**|32 비트 수량을 호스트 바이트 순서에서 네트워크 바이트 순서 (작은 Endian에서 빅 Endian)로 변환 합니다.|

이 예의 또 다른 점은 통신의 다른 쪽 끝에 있는 소켓 응용 프로그램이 비 MFC 응용 프로그램이 면 다음과 같은 작업을 수행 하지 않도록 해야 한다는 것입니다.

`ar << pMsg;`

여기서 `pMsg` 는 클래스에서 파생 된 c + + 개체에 대 한 포인터입니다 `CObject` . 그러면 개체와 관련 된 추가 MFC 정보가 전송 되며, MFC 응용 프로그램의 경우 처럼 서버에서이 정보를 인식 하지 못합니다.

자세한 내용은 다음을 참조하세요.

- [Windows 소켓: CAsyncSocket 클래스 사용](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 소켓: 배경](../mfc/windows-sockets-background.md)

- [Windows 소켓: 스트림 소켓](../mfc/windows-sockets-stream-sockets.md)

- [Windows 소켓: 데이터 그램 소켓](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>참고 항목

[MFC의 Windows 소켓](../mfc/windows-sockets-in-mfc.md)
