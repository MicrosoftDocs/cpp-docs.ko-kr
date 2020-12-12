---
description: '자세히 알아보기: 응용 프로그램 디자인 선택'
title: 애플리케이션 디자인 선택
ms.date: 09/12/2019
helpviewer_keywords:
- design
- application design [MFC], design goals
- application design [MFC], Internet applications
- Internet applications [MFC], designing applications
- Internet [MFC], vs. intranets
- applications [MFC], Internet
- server applications [MFC], vs. client applications on Internet
- client applications [MFC], vs. server applications on Internet
ms.assetid: 9b96172c-b4d4-4c69-bfb2-226ce0de6d08
ms.openlocfilehash: 0402cfe8cb58ed538e1429d2edc4f95cc9a23a0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335927"
---
# <a name="application-design-choices"></a>애플리케이션 디자인 선택

이 문서에서는 인터넷을 사용할 때 고려해 야 할 몇 가지 디자인 문제에 대해 설명 합니다.

이 문서에서 다루는 항목은 다음과 같습니다.

- [인트라넷 및 인터넷](#_core_intranet_versus_internet)

- [클라이언트 또는 서버 응용 프로그램](#_core_client_or_server_application)

- [웹 페이지](#_core_the_web_page)

- [브라우저 또는 Stand-Alone 응용 프로그램](#_core_browser_or_standalone)

- [인터넷의 COM](#_core_com_on_the_internet)

- [클라이언트 데이터 다운로드 서비스](#_core_client_data_download_services)

지금 프로그램 작성을 시작할 준비가 되었으면 [MFC 응용 프로그램 작성](writing-mfc-applications.md)을 참조 하세요.

## <a name="intranet-versus-internet"></a><a name="_core_intranet_versus_internet"></a> 인트라넷 및 인터넷

많은 응용 프로그램은 인터넷에서 실행 되며 브라우저 및 인터넷 액세스를 사용 하는 모든 사용자가 액세스할 수 있습니다. 또한 기업은 TCP/IP 프로토콜 및 웹 브라우저를 사용 하는 회사 전체 네트워크 인 인트라넷을 구현 합니다. 인트라넷은 회사 전체의 정보를 위한 쉽게 업그레이드할 때 중앙의 중앙 소스를 제공 합니다. 이러한 소프트웨어는 소프트웨어를 업그레이드 하는 데 사용할 수 있습니다. tabulating 설문 조사를 제공 하 고, 고객 지원 및 정보 제공에 사용할 수 있습니다. 다음 표에서는 인터넷 및 인트라넷의 기능을 비교 합니다.

|인터넷|Intranet|
|--------------|--------------|
|낮은 대역폭|높은 대역폭|
|데이터 및 시스템의 보안 감소|데이터 및 시스템에 대 한 제어 된 액세스|
|최소 콘텐츠 제어|높은 수준의 콘텐츠 제어|

## <a name="client-or-server-application"></a><a name="_core_client_or_server_application"></a> 클라이언트 또는 서버 응용 프로그램

클라이언트 컴퓨터 또는 서버 컴퓨터에서 응용 프로그램을 실행할 수 있습니다. 응용 프로그램이 서버에 저장 된 다음 인터넷을 통해 다운로드 되 고 클라이언트 컴퓨터에서 실행 될 수도 있습니다. MFC WinInet 클래스는 클라이언트 응용 프로그램에서 파일을 다운로드 하는 데 사용 됩니다. MFC 및 비동기 모니커 클래스는 파일 및 컨트롤 속성을 다운로드 하는 데 사용 됩니다. ActiveX 컨트롤 및 활성 문서에 대 한 클래스는 클라이언트 응용 프로그램과 서버에서 다운로드 되어 클라이언트에서 실행 되는 응용 프로그램에 사용 됩니다.

## <a name="the-web-page-html-active-documents-activex-controls"></a><a name="_core_the_web_page"></a> 웹 페이지: HTML, 액티브 문서, ActiveX 컨트롤

Microsoft에서는 웹 페이지에서 콘텐츠를 제공 하는 여러 가지 방법을 제공 합니다. 웹 페이지는 개체 태그와 같은 표준 HTML 또는 HTML 확장을 사용 하 여 ActiveX 컨트롤과 같은 동적 콘텐츠를 제공할 수 있습니다.

웹 브라우저는 일반적으로 HTML 페이지를 표시 합니다. 활성 문서는 COM 사용 브라우저의 단순 지점 및 클릭 인터페이스에 응용 프로그램의 데이터를 표시할 수도 있습니다. 활성 문서 서버는 자체 메뉴와 도구 모음을 사용 하 여 전체 클라이언트 영역에 문서 전체 프레임을 표시할 수 있습니다.

작성 하는 ActiveX 컨트롤은 서버에서 비동기적으로 다운로드 하 여 웹 페이지에 표시할 수 있습니다. VBScript와 같은 스크립팅 언어를 사용 하 여 서버에 정보를 보내기 전에 클라이언트 쪽 유효성 검사를 수행할 수 있습니다.

## <a name="browser-or-stand-alone-application"></a><a name="_core_browser_or_standalone"></a> 브라우저 또는 Stand-Alone 응용 프로그램

HTML 페이지에 포함 된 ActiveX 컨트롤 및 브라우저에 표시 되는 액티브 문서 서버를 작성할 수 있습니다. 웹 서버에서 ISAPI 응용 프로그램을 실행 하는 요청을 제출 하는 단추를 포함 하는 HTML 페이지를 작성할 수 있습니다. 브라우저 응용 프로그램을 사용 하지 않고 인터넷 프로토콜을 사용 하 여 파일을 다운로드 하 고 사용자에 게 정보를 표시 하는 독립 실행형 응용 프로그램을 작성할 수 있습니다.

## <a name="com-on-the-internet"></a><a name="_core_com_on_the_internet"></a> 인터넷의 COM

ActiveX 컨트롤, 활성 문서 및 비동기 모니커는 모두 COM (구성 요소 개체 모델) 기술을 사용 합니다.

ActiveX 컨트롤은 인터넷 사이트의 문서와 페이지에 동적 콘텐츠를 제공 합니다. COM을 사용 하면 활성 문서를 사용 하 여 ActiveX 컨트롤 및 전체 프레임 문서를 빌드할 수 있습니다.

비동기 모니커는 데이터를 다운로드 하는 증분 또는 점진적 수단을 포함 하 여 컨트롤이 인터넷 환경에서 잘 작동 하도록 하는 기능을 제공 합니다. 또한 컨트롤은 동시에 데이터를 비동기적으로 검색할 수 있는 다른 컨트롤에서 잘 작동 해야 합니다.

## <a name="client-data-download-services"></a><a name="_core_client_data_download_services"></a> 클라이언트 데이터 다운로드 서비스

클라이언트에 데이터를 전송 하는 데 도움이 되는 두 가지 Api 집합은 WinInet 및 비동기 모니커에 있습니다. HTML 페이지에 많은 .gif 및 .avi 파일과 ActiveX 컨트롤이 있는 경우 비동기 모니커를 사용 하거나 WinInet을 비동기식으로 사용 하 여 비동기적으로 다운로드 하 여 사용자에 대 한 응답성을 높일 수 있습니다.

인터넷에서 일반적인 작업은 데이터를 전송 하는 것입니다. 활성 기술을 이미 사용 중인 경우 (예: ActiveX 컨트롤이 있는 경우) 비동기 모니커를 사용 하 여 데이터를 다운로드할 때 점진적으로 렌더링할 수 있습니다. WinInet을 사용 하 여 HTTP, FTP 및 gopher와 같은 일반적인 인터넷 프로토콜을 통해 데이터를 전송할 수 있습니다. 두 방법 모두 프로토콜 독립성을 제공 하 고 WinSock 및 TCP/IP를 사용 하는 추상 계층을 제공 합니다. [WinSock](windows-sockets-in-mfc.md) 을 직접 사용할 수 있습니다.

다음 표에는 MFC를 사용 하 여 인터넷을 통해 데이터를 전송 하는 몇 가지 방법이 요약 되어 있습니다.

|이 프로토콜 사용|다음 조건에서|이러한 클래스 사용|
|-----------------------|----------------------------|-------------------------|
|[비동기 모니커를 사용 하 여 인터넷 다운로드](asynchronous-monikers-on-the-internet.md)|COM, ActiveX 컨트롤 및 인터넷 프로토콜을 사용 하는 비동기 전송에 사용 됩니다.|[CAsyncMonikerFile](reference/casyncmonikerfile-class.md), [CDataPathProperty](reference/cdatapathproperty-class.md)|
|[WinInet](win32-internet-extensions-wininet.md)|HTTP, FTP 및 gopher의 인터넷 프로토콜입니다. 동기적 또는 비동기적으로 데이터를 전송 하 고 시스템 차원의 캐시에 저장할 수 있습니다.|[Cinternetsession](reference/cinternetsession-class.md), [cCGopherFileFind filefind](reference/cftpfilefind-class.md), [](reference/cgopherfilefind-class.md)등이 있습니다.|
|[WinSock](windows-sockets-in-mfc.md)|효율성 및 제어를 최대화 합니다. 소켓 및 TCP/IP 프로토콜을 이해 해야 합니다.|[CSocket](reference/csocket-class.md), [CAsyncSocket](reference/casyncsocket-class.md)|

## <a name="see-also"></a>참고 항목

[MFC 인터넷 프로그래밍 작업](mfc-internet-programming-tasks.md)<br/>
[MFC 인터넷 프로그래밍 기본 사항](mfc-internet-programming-basics.md)<br/>
[Win32 인터넷 확장 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[인터넷의 비동기 모니커](asynchronous-monikers-on-the-internet.md)
