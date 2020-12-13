---
description: '자세한 정보: 인터넷의 액티브 기술'
title: 인터넷의 액티브 기술
ms.date: 09/12/2018
helpviewer_keywords:
- Internet applications [MFC], Active technology
ms.assetid: 6f782aa1-5c2f-47a2-9e63-ddd0829d5a08
ms.openlocfilehash: 4f8035e0af233eac55c00a84679f79d214978219
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150243"
---
# <a name="active-technology-on-the-internet"></a>인터넷의 액티브 기술

활성 기술은 개발자가 글로벌 인터넷을 위한 흥미로운 동적 콘텐츠 및 응용 프로그램 또는 인트라넷으로 알려진 회사의 내부 네트워크를 만들 수 있도록 하는 개방형 플랫폼입니다. Microsoft에서 제공 하는 인터넷 프로그래밍의 주요 기술은 아래에 설명 되어 있습니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

## <a name="activex-controls"></a>ActiveX 컨트롤

ActiveX 컨트롤 (이전의 OLE 컨트롤)은 웹 페이지 또는 ActiveX 컨트롤 컨테이너의 다른 응용 프로그램에 삽입할 수 있는 개체입니다. 예를 들어 단추, 주식 시세표 및 차트 컨트롤이 있습니다. 자세한 내용은 [인터넷의 ActiveX 컨트롤](activex-controls-on-the-internet.md)을 참조 하십시오.

## <a name="internet-data-download-services"></a>인터넷 데이터 다운로드 서비스

일반 프로토콜 (HTTP, FTP 및 gopher)을 사용 하 여 인터넷을 통해 데이터를 다운로드할 수 있습니다. MFC WinInet 클래스를 사용 하면 TCP/IP 및 WinSock 프로토콜을 추상화 하 여 HTTP, FTP 및 gopher 프로토콜을 사용 하 여 데이터를 쉽게 전송할 수 있습니다. MFC 비동기 모니커 클래스는를 차단 하지 않고 파일을 다운로드 하는 방법을 제공 하 고, 많은 개체를 비동기적으로 렌더링 합니다. 자세한 내용은 [Win32 Internet Extensions (WinInet)](win32-internet-extensions-wininet.md)를 참조 하십시오.

## <a name="active-scripts"></a>액티브 스크립트

VBScript 및 기타 스크립팅 언어는 컨트롤을 연결 하 고 웹 페이지에 대화형 기능을 추가 합니다. 스크립팅은 서버에서 클라이언트로 처리를 이동 합니다. 예를 들어 클라이언트에서 양식 항목의 유효성을 검사 한 다음 서버로 보낼 수 있습니다.

## <a name="html-extensions"></a>HTML 확장

컨트롤 및 스크립팅을 지원 하기 위해 개체 태그와 같은 HTML 확장이 추가 되었습니다.

## <a name="see-also"></a>참고 항목

[MFC 인터넷 프로그래밍 기본 사항](mfc-internet-programming-basics.md)<br/>
[인터넷의 ActiveX 컨트롤](activex-controls-on-the-internet.md)<br/>
[Win32 인터넷 확장 (WinInet)](win32-internet-extensions-wininet.md)
