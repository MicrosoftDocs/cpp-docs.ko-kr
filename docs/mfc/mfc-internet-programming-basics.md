---
description: '자세한 정보: MFC 인터넷 프로그래밍 기본 사항'
title: MFC 인터넷 프로그래밍 기본 사항
ms.date: 11/19/2018
helpviewer_keywords:
- ISAPI extensions, programming with ISAPI
- Internet applications [MFC]
- ISAPI
- ActiveX controls [MFC], Internet
- programming [MFC], Internet
- Web applications [MFC], MFC classes
- ISAPI filters [MFC], programming with ISAPI
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], writing
- Internet applications [MFC], Active technology
- Active technology [MFC]
- Internet content [MFC]
- WinInet classes [MFC]
ms.assetid: 6df2dfd0-6e3f-4587-9d01-2a32f00f8a6f
ms.openlocfilehash: 0c38a5eba3a49791c472d5da0f733a18422058ba
ms.sourcegitcommit: 6183207b11575d7b44ebd7c18918e916a0d8c63d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97951452"
---
# <a name="mfc-internet-programming-basics"></a>MFC 인터넷 프로그래밍 기본 사항

Microsoft는 클라이언트 및 서버 응용 프로그램을 모두 프로그래밍 하기 위한 많은 Api를 제공 합니다. 인터넷을 위해 많은 새로운 응용 프로그램을 작성 하 고, 기술, 브라우저 기능 및 보안 옵션이 변경 됨에 따라 새로운 유형의 응용 프로그램이 작성 됩니다. 브라우저는 클라이언트 컴퓨터에서 실행 되며, World Wide Web에 대 한 액세스를 제공 하 고 텍스트, 그래픽, ActiveX 컨트롤 및 문서를 포함 하는 HTML 페이지를 표시 합니다. 서버는 FTP, HTTP 및 gopher 서비스를 제공 하 고 CGI를 사용 하 여 서버 확장 응용 프로그램을 실행 합니다. 사용자 지정 응용 프로그램은 인터넷에서 정보를 검색 하 고 데이터를 제공할 수 있습니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. 자세한 내용은 [ActiveX Controls](activex-controls.md)을 참조 하세요.

![클라이언트 및 서버 응용 프로그램](../mfc/media/vc38bq1.gif "클라이언트 및 서버 응용 프로그램")

MFC는 인터넷 프로그래밍을 지 원하는 클래스를 제공 합니다. [COleControl](reference/colecontrol-class.md) 및 [CDOCOBJECTSERVER](reference/cdocobjectserver-class.md) 및 관련 MFC 클래스를 사용 하 여 ActiveX 컨트롤 및 활성 문서를 작성할 수 있습니다. [Cinternetsession](reference/cinternetsession-class.md), [CCAsyncMonikerFile connection](reference/cftpconnection-class.md)및 [](reference/casyncmonikerfile-class.md) 와 같은 MFC 클래스를 사용 하 여 FTP, HTTP, gopher 등의 인터넷 프로토콜을 사용 하 여 파일 및 정보를 검색할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용

- [인터넷 관련 MFC 클래스](internet-related-mfc-classes.md)

- [항목 별 인터넷 정보](internet-information-by-topic.md)

- [작업별 인터넷 정보](internet-information-by-task.md)

- [인터넷의 액티브 기술](active-technology-on-the-internet.md)

- [WinInet 기본 사항](wininet-basics.md)

- [HTML 기본 사항](html-basics.md)

## <a name="related-sections"></a>관련 단원

- [인터넷의 ActiveX 컨트롤](activex-controls-on-the-internet.md)

- [인터넷의 비동기 모니커](asynchronous-monikers-on-the-internet.md)

- [Win32 인터넷 확장 (WinInet)](win32-internet-extensions-wininet.md)

- [MFC 인터넷 프로그래밍 작업](mfc-internet-programming-tasks.md)

- [응용 프로그램 디자인 선택](application-design-choices.md)

- [MFC 응용 프로그램 작성](writing-mfc-applications.md)

- [인터넷 응용 프로그램 테스트](testing-internet-applications.md)

- [인터넷 보안](internet-security-cpp.md)

- [DHTML 컨트롤에 대 한 ATL 지원](../atl/atl-support-for-dhtml-controls.md)

## <a name="websites-for-more-information"></a><a name="_core_web_sites_for_more_information"></a> 추가 정보를 위한 웹 사이트

Microsoft 인터넷 기술에 대 한 자세한 내용은 [네트워킹 및 인터넷](/windows/win32/networking)을 참조 하십시오.

[W3C (World Wide Web 컨소시엄)](https://www.w3.org/) 는 HTML, HTTP, CGI 및 기타 World Wide Web 기술에 대 한 사양을 게시 합니다.

## <a name="more-internet-help"></a><a name="_core_more_internet_help"></a> 추가 인터넷 도움말

Windows SDK OLE 섹션에는 OLE 프로그래밍에 대 한 추가 정보가 포함 되어 있습니다. 이 정보는 MFC 클래스가 아니라 Win32 WinInet 함수를 직접 사용 하는 방법에 대 한 자세한 정보를 제공 합니다. 또한 인터넷 기술에 대 한 개요 정보도 포함 되어 있습니다.
