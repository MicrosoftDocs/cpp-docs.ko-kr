---
description: '자세히 알아보기: WinInet을 사용 하 여 인터넷 클라이언트 응용 프로그램을 보다 쉽게 만들 수 있습니다.'
title: WinInet을 사용하여 인터넷 클라이언트 애플리케이션을 손쉽게 만드는 방법
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
ms.openlocfilehash: efee0b201a165fab8aaf838eedb2ba83b9a5b946
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330131"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>WinInet을 사용하여 인터넷 클라이언트 애플리케이션을 손쉽게 만드는 방법

Win32 인터넷 확장 또는 WinInet은 gopher, FTP, HTTP 등의 일반적인 인터넷 프로토콜에 대 한 액세스를 제공 합니다. WinInet을 사용 하 여 WinSock, TCP/IP 또는 특정 인터넷 프로토콜의 세부 정보를 처리 하지 않고도 더 높은 수준의 프로그래밍으로 인터넷 클라이언트 응용 프로그램을 작성할 수 있습니다. WinInet은 친숙 한 Win32 API 인터페이스를 사용 하 여 세 가지 프로토콜에 대해 일관적인 함수 집합을 제공 합니다. 이러한 일관성은 기본 프로토콜이 변경 될 때 (예: FTP에서 HTTP로) 변경 해야 하는 코드 변경을 최소화 합니다.

Visual C++는 WinInet을 사용 하는 두 가지 방법을 제공 합니다. Win32 인터넷 함수를 직접 호출할 수 있습니다. 자세한 내용은 Windows SDK OLE 설명서를 참조 하거나, [MFC wininet 클래스](mfc-classes-for-creating-internet-client-applications.md)를 통해 wininet을 사용할 수 있습니다.

**WinInet을 사용 하 여 다음을 수행할 수 있습니다.**

- HTML 페이지를 다운로드 합니다.

   HTTP는 HTML 페이지를 서버에서 클라이언트 브라우저로 전송 하는 데 사용 되는 프로토콜입니다.

- FTP 요청을 전송 하 여 파일을 업로드 또는 다운로드 하거나 디렉터리 목록을 가져옵니다.

   일반적인 요청은 파일을 다운로드 하는 익명 로그온입니다.

- Gopher의 메뉴 시스템을 사용 하 여 인터넷의 리소스에 액세스 합니다.

   메뉴 항목은 다른 메뉴, 검색할 수 있는 인덱싱된 데이터베이스, 뉴스 그룹 또는 파일을 비롯 한 여러 가지 형식일 수 있습니다.

세 가지 프로토콜 모두에 대해 연결을 설정 하 고, 서버에 요청을 수행 하 고, 연결을 닫습니다.

**MFC WinInet 클래스를 사용 하면 다음과 같은 작업을 쉽게 수행할 수 있습니다.**

- 하드 드라이브에서 파일을 읽는 것 처럼 쉽게 HTTP, FTP 및 gopher 서버에서 정보를 읽습니다.

- WinSock 또는 TCP/IP에 직접 프로그래밍 하지 않고 HTTP, FTP 및 gopher 프로토콜을 사용 합니다.

   Win32 인터넷 기능을 사용 하는 개발자는 TCP/IP 또는 Windows 소켓에 대해 잘 알고 있지 않아도 됩니다. WinSock 및 TCP/IP 프로토콜을 직접 사용 하 여 소켓 수준에서 프로그래밍 할 수 있지만, MFC WinInet 클래스를 사용 하 여 인터넷을 통해 HTTP, FTP 및 gopher 프로토콜에 액세스 하는 것이 훨씬 쉽습니다. 많은 일반적인 작업의 경우 개발자는 사용 중인 특정 프로토콜의 세부 정보를 알 필요가 없습니다.

컴퓨터에서 인터넷의 다른 컴퓨터에 대 한 클라이언트로 수행할 수 있는 많은 작업은 시간이 오래 걸릴 수 있습니다. 이러한 작업의 속도는 일반적으로 네트워크 연결 속도에 따라 제한 되지만 다른 네트워크 트래픽과 작업의 복잡도에 의해 영향을 받을 수도 있습니다. 예를 들어 원격 FTP 서버에 연결 하려면 먼저 컴퓨터에서 해당 서버 이름을 조회 하 여 해당 주소를 찾아야 합니다. 그러면 응용 프로그램은 해당 주소에서 서버에 대 한 연결을 시도 합니다. 연결이 열리면 컴퓨터와 원격 서버에서 파일 전송 프로토콜을 사용 하 여 대화를 시작한 후에 실제로 연결을 사용 하 여 파일을 검색할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Win32 인터넷 확장 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[MFC를 사용 하 여 인터넷 클라이언트 응용 프로그램을 손쉽게 만드는 방법](how-mfc-makes-it-easier-to-create-internet-client-applications.md)
