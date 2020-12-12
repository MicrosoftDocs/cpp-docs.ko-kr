---
description: '자세한 정보: Windows 소켓: CAsyncSocket 클래스 사용'
title: 'Windows 소켓: CAsyncSocket 클래스 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
ms.openlocfilehash: 9fbf385a2e327588685fdcb996465386628e5e4d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118604"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows 소켓: CAsyncSocket 클래스 사용

이 문서에서는 [Casyncsocket](../mfc/reference/casyncsocket-class.md)클래스를 사용 하는 방법을 설명 합니다. 이 클래스는 Windows 소켓 API를 매우 낮은 수준에서 캡슐화 합니다. `CAsyncSocket` 는 네트워크 통신에 대해 자세히 알고 있지만 네트워크 이벤트 알림을 위한 콜백을 사용 하려는 프로그래머를 위한 것입니다. 이 문서에서는이 가정에 따라 기본 명령만 제공 합니다. `CAsyncSocket`MFC 응용 프로그램에서 여러 네트워크 프로토콜을 처리할 수 있을 뿐만 아니라 유연성이 저하 되지 않도록 하려면를 사용 하는 것이 좋습니다. 보다 일반적인 클래스의 대체 모델을 사용할 때 보다 직접 통신을 직접 프로그래밍 하 여 효율성을 높일 수도 있습니다 `CSocket` .

`CAsyncSocket` 는 *MFC 참조* 에 설명 되어 있습니다. Visual C++은 Windows SDK에 있는 Windows 소켓 사양도 제공 합니다. 세부 정보는 그대로 유지 됩니다. Visual C++에 대 한 예제 응용 프로그램을 제공 하지 않습니다 `CAsyncSocket` .

네트워크 통신에 대해 잘 알고 있지 않은 경우 간단한 솔루션을 사용 하려면 개체에 [CSocket](../mfc/reference/csocket-class.md) 클래스를 사용 `CArchive` 합니다. 자세한 내용은 [Windows 소켓: 보관 파일에 소켓 사용](../mfc/windows-sockets-using-sockets-with-archives.md) 을 참조 하세요.

이 문서에서는 다음 내용을 설명합니다.

- 개체 만들기 및 사용 `CAsyncSocket`

- [CAsyncSocket을 사용 하는 사용자의 책임](#_core_your_responsibilities_with_casyncsocket)입니다.

## <a name="creating-and-using-a-casyncsocket-object"></a><a name="_core_creating_and_using_a_casyncsocket_object"></a> CAsyncSocket 개체 만들기 및 사용

#### <a name="to-use-casyncsocket"></a>CAsyncSocket을 사용 하려면

1. [Casyncsocket](../mfc/reference/casyncsocket-class.md) 개체를 생성 하 고 개체를 사용 하 여 기본 **소켓** 핸들을 만듭니다.

   소켓 생성은 2 단계 생성의 MFC 패턴을 따릅니다.

   예를 들어:

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     또는

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   위의 첫 번째 생성자는 `CAsyncSocket` 스택에서 개체를 만듭니다. 두 번째 생성자는 힙에서을 만듭니다 `CAsyncSocket` . 위의 첫 번째 [Create](../mfc/reference/casyncsocket-class.md#create) 호출은 기본 매개 변수를 사용 하 여 스트림 소켓을 만듭니다. 두 번째 `Create` 호출은 지정 된 포트와 주소를 사용 하 여 데이터 그램 소켓을 만듭니다. 두 버전 중 하나를 `Create` 생성 방법으로 사용할 수 있습니다.

   의 매개 변수는 `Create` 다음과 같습니다.

   - "Port": 정수 (short)입니다.

      서버 소켓의 경우 포트를 지정 해야 합니다. 클라이언트 소켓의 경우 일반적으로이 매개 변수의 기본값을 그대로 사용 하 여 Windows 소켓에서 포트를 선택할 수 있습니다.

   - 소켓 형식: **SOCK_STREAM** (기본값) 또는 **SOCK_DGRAM** 입니다.

   - "Ftp.microsoft.com" 또는 "128.56.22.8"와 같은 소켓 "address"입니다.

      네트워크의 IP (인터넷 프로토콜) 주소입니다. 이 매개 변수에는 항상 기본값을 사용 하는 것이 좋습니다.

   "포트" 및 "소켓 주소" 라는 용어는 [Windows 소켓: 포트 및 소켓 주소](../mfc/windows-sockets-ports-and-socket-addresses.md)에 설명 되어 있습니다.

1. 소켓이 클라이언트 인 경우 [Casyncsocket:: connect](../mfc/reference/casyncsocket-class.md#connect)를 사용 하 여 소켓 개체를 서버 소켓에 연결 합니다.

     또는

   소켓이 서버인 경우 클라이언트의 연결 시도에 대 한 수신 대기를 시작 하도록 ( [Casyncsocket:: Listen](../mfc/reference/casyncsocket-class.md#listen)사용) 소켓을 설정 합니다. 연결 요청이 수신 되 면 [Casyncsocket:: accept](../mfc/reference/casyncsocket-class.md#accept)를 사용 하 여 수락 합니다.

   연결을 승인한 후에는 암호 유효성 검사와 같은 작업을 수행할 수 있습니다.

    > [!NOTE]
    >  `Accept`멤버 함수는 비어 있는 새 개체에 대 한 참조를 `CSocket` 매개 변수로 사용 합니다. 을 호출 하기 전에이 개체를 생성 해야 `Accept` 합니다. 이 소켓 개체가 범위를 벗어나면 연결이 닫힙니다. `Create`이 새 소켓 개체에 대해를 호출 하지 마세요. 예제는 [Windows 소켓: 작업 순서](../mfc/windows-sockets-sequence-of-operations.md)문서를 참조 하세요.

1. `CAsyncSocket`Windows 소켓 API 함수를 캡슐화 하는 개체의 멤버 함수를 호출 하 여 다른 소켓과의 통신을 수행 합니다.

   *MFC 참조* 의 Windows 소켓 사양 및 [casyncsocket](../mfc/reference/casyncsocket-class.md) 클래스를 참조 하세요.

1. 개체를 삭제 `CAsyncSocket` 합니다.

   스택에 소켓 개체를 만든 경우 포함 하는 함수가 범위를 벗어나면 해당 소멸자가 호출 됩니다. 연산자를 사용 하 여 힙에서 소켓 개체를 만든 경우 연산자를 사용 하 여 **`new`** 개체를 제거 해야 **`delete`** 합니다.

   소멸자는 개체를 삭제 하기 전에 개체의 [Close](../mfc/reference/casyncsocket-class.md#close) 멤버 함수를 호출 합니다.

코드에서이 시퀀스의 예 (개체의 경우)는 `CSocket` [Windows 소켓: 작업 시퀀스](../mfc/windows-sockets-sequence-of-operations.md)를 참조 하세요.

## <a name="your-responsibilities-with-casyncsocket"></a><a name="_core_your_responsibilities_with_casyncsocket"></a> CAsyncSocket을 사용한 사용자의 책임

[Casyncsocket](../mfc/reference/casyncsocket-class.md)클래스의 개체를 만들 때 개체는 Windows **소켓** 핸들을 캡슐화 하 고이 핸들에 대 한 작업을 제공 합니다. 를 사용 하 `CAsyncSocket` 는 경우 API를 직접 사용 하는 경우 발생할 수 있는 모든 문제를 처리 해야 합니다. 예를 들어:

- "차단" 시나리오.

- 전송 컴퓨터와 수신 컴퓨터 간의 바이트 순서 차이입니다.

- 유니코드 및 MBCS (멀티 바이트 문자 집합) 문자열을 변환 합니다.

이러한 용어에 대 한 정의 및 추가 정보는 [windows 소켓: 차단](../mfc/windows-sockets-blocking.md), [Windows 소켓: 바이트 순서](../mfc/windows-sockets-byte-ordering.md)지정, [windows 소켓: 문자열 변환](../mfc/windows-sockets-converting-strings.md)을 참조 하세요.

이러한 문제에도 불구 하 `CAsycnSocket` 고 응용 프로그램에 필요한 모든 유연성과 제어가 필요한 경우 클래스를 적절 하 게 선택할 수 있습니다. 그렇지 않은 경우 대신 클래스를 사용 하는 것을 고려해 야 합니다 `CSocket` . `CSocket` 사용자의 많은 세부 정보를 숨깁니다. 차단 호출 중에 Windows 메시지를 펌프 하 고 `CArchive` 바이트 순서 차이 및 문자열 변환을 관리 하는에 대 한 액세스를 제공 합니다.

자세한 내용은 다음을 참조하세요.

- [Windows 소켓: 배경](../mfc/windows-sockets-background.md)

- [Windows 소켓: 스트림 소켓](../mfc/windows-sockets-stream-sockets.md)

- [Windows 소켓: 데이터 그램 소켓](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>참고 항목

[MFC의 Windows 소켓](../mfc/windows-sockets-in-mfc.md)
