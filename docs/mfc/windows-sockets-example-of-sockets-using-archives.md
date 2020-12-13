---
description: '자세한 정보: Windows 소켓: 아카이브를 사용 하는 소켓 예제'
title: 'Windows 소켓: 아카이브를 사용하는 소켓의 예'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 726df9093f71a7c72fc72794044a417c5425d2a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132928"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows 소켓: 아카이브를 사용하는 소켓의 예

이 문서에서는 [CSocket](../mfc/reference/csocket-class.md)클래스를 사용 하는 예를 보여 줍니다. 이 예제에서는 `CArchive` 개체를 통해 소켓을 통해 데이터를 직렬화 합니다. 이는 파일에 대 한 문서 serialization이 아닙니다.

다음 예에서는 보관을 사용 하 여 개체를 통해 데이터를 보내고 받는 방법을 보여 줍니다 `CSocket` . 예제는 응용 프로그램의 두 인스턴스 (동일한 컴퓨터 또는 네트워크 상의 다른 컴퓨터)가 데이터를 교환 하도록 설계 되었습니다. 한 인스턴스는 다른 인스턴스가 받아서 승인 하는 데이터를 보냅니다. 두 응용 프로그램 모두 exchange를 시작할 수 있으며 다른 응용 프로그램의 서버 또는 클라이언트로 작동할 수 있습니다. 다음 함수는 응용 프로그램의 뷰 클래스에서 정의 됩니다.

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

이 예제에 대 한 가장 중요 한 점은 해당 구조가 MFC 함수의 구조와 유사 하다는 것입니다 `Serialize` . `PacketSerialize`멤버 함수는 절이 포함 된 문으로 구성 됩니다 **`if`** **`else`** . 함수는 두 개의 [CArchive](../mfc/reference/carchive-class.md) 참조를 *Ardata* 및 *ardata* 매개 변수로 받습니다. *Ardata* archive 개체가 저장 (송신) 하도록 설정 된 경우 **`if`** 분기가 실행 됩니다. 그렇지 않으면 *ardata* 가 로드 (수신)에 대해 설정 된 경우이 함수는 분기를 사용 합니다. **`else`** MFC의 serialization에 대 한 자세한 내용은 [serialization](../mfc/how-to-make-a-type-safe-collection.md)을 참조 하세요.

> [!NOTE]
> *Arack* archive 개체는 *arack* 와 반대 되는 것으로 간주 됩니다. *Ardata* 가 송신을 위한 경우 *ardata* 는를 받고 그 반대의 경우도 마찬가지입니다.

전송의 경우 예제 함수는 데모용으로 임의의 데이터를 생성할 때마다 지정 된 횟수 만큼 반복 합니다. 응용 프로그램은 파일 등의 일부 원본에서 실제 데이터를 가져옵니다. *Ardata* archive의 삽입 연산자 ( **<<** )는 세 개의 연속 데이터 청크 스트림을 전송 하는 데 사용 됩니다.

- 데이터의 특성을 지정 하는 "헤더" (이 경우 *Bvalue* 변수의 값 및 전송 되는 복사본의 수)입니다.

   이 예제에서는 두 항목이 임의로 생성 됩니다.

- 지정 된 데이터 복사본 수입니다.

   내부 **`for`** 루프는 지정 된 횟수 만큼 *bvalue* 를 보냅니다.

- 수신자가 해당 사용자에 게 표시 하는 *Strtext* 라는 문자열입니다.

수신의 경우이 함수는 아카이브의 추출 연산자 ()를 사용 하 여 **>>** 보관 파일에서 데이터를 가져오는 것을 제외 하 고는 유사 하 게 작동 합니다. 수신 응용 프로그램은 수신 하는 데이터를 확인 하 고, 마지막 "수신" 메시지를 표시 한 다음, 전송 응용 프로그램에서 표시 하기 위해 "전송 됨" 이라는 메시지를 다시 보냅니다.

이 통신 모델에서 *Strtext* 변수에 전송 되는 메시지 "Received" 라는 단어는 통신의 다른 쪽 끝에 표시 되기 위한 것 이므로 받는 사용자에 게 특정 수의 데이터 패킷을 받았음을 지정 합니다. 수신자는 원래 보낸 사람의 화면에 표시 하기 위해 "전송 됨" 이라는 유사한 문자열을 사용 하 여 회신 합니다. 두 문자열이 모두 수신 되 면 통신이 성공 했음을 나타냅니다.

> [!CAUTION]
> 설정된(MFC 이외) 서버와 통신하도록 MFC 클라이언트 프로그램을 작성하는 경우 아카이브를 통해 C++ 개체를 전송하지 마십시오. 서버가 보내려는 개체의 종류를 이해 하는 MFC 응용 프로그램이 아닌 경우 개체를 수신 하 고 deserialize 할 수 없습니다. [Windows 소켓: 바이트 순서](../mfc/windows-sockets-byte-ordering.md) 지정 문서의 예에서는 이러한 유형의 통신을 보여 줍니다.

자세한 내용은 Windows 소켓 사양: **htonl**, **htons**, **ntohl**, **ntohs** 을 참조 하세요. 또한 자세한 내용은 다음을 참조 하세요.

- [Windows 소켓: 소켓 클래스에서 파생](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows 소켓: 소켓과 보관 파일의 작동 방식](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows 소켓: 배경](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>참고 항목

[MFC의 Windows 소켓](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive:: IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive:: operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive:: operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject:: Serialize](../mfc/reference/cobject-class.md#serialize)
