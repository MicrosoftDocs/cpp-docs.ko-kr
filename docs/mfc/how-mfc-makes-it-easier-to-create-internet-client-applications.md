---
description: '자세한 정보: MFC를 사용 하 여 인터넷 클라이언트 응용 프로그램을 보다 쉽게 만들 수 있습니다.'
title: MFC를 사용하여 인터넷 클라이언트 애플리케이션을 손쉽게 만드는 방법
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
- MFC, Internet applications
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
ms.openlocfilehash: 7cc201c67cf4964e5bd561cd173186bc57feb89b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343604"
---
# <a name="how-mfc-makes-it-easier-to-create-internet-client-applications"></a>MFC를 사용하여 인터넷 클라이언트 애플리케이션을 손쉽게 만드는 방법

Microsoft Foundation Classes는 MFC 프로그래머에 게 친숙 한 컨텍스트를 제공 하는 방식으로 Win32 인터넷 확장 (WinInet) 함수를 캡슐화 합니다. MFC는 [CStdioFile](reference/cstdiofile-class.md) 클래스에서 파생 된 세 가지 인터넷 파일 클래스 ([cinternetfile](reference/cinternetfile-class.md), [CHttpFile](reference/chttpfile-class.md)및 [CGopherFile](reference/cgopherfile-class.md))를 제공 합니다. 이러한 클래스를 사용 하 여 로컬 파일에 사용 된 프로그래머에 게 친숙 한 인터넷 데이터를 검색 하 고 조작할 수 있을 뿐만 아니라 `CStdioFile` 이러한 클래스를 사용 하면 일관 되 고 투명 한 방식으로 로컬 파일 및 인터넷 파일을 처리할 수 있습니다.

MFC WinInet 클래스는 `CStdioFile` 인터넷을 통해 전송 되는 데이터와 동일한 기능을 제공 합니다. 이러한 클래스는 HTTP, FTP 및 gopher 용 인터넷 프로토콜을 고급 응용 프로그램 프로그래밍 인터페이스로 추상화 하 여 응용 프로그램을 인터넷에서 인식 하는 빠르고 간단한 경로를 제공 합니다. 예를 들어 FTP 서버에 연결 하는 경우에도 낮은 수준에서 여러 단계가 필요 하지만, MFC 개발자는를 호출 하 여 `CInternetSession::GetFTPConnection` 해당 연결을 만들어야 합니다.

또한 MFC WinInet 클래스는 다음과 같은 이점을 제공 합니다.

- 버퍼링 된 i/o

- 데이터에 대 한 형식이 안전한 핸들

- 대부분의 함수에 대 한 기본 매개 변수

- 일반적인 인터넷 오류에 대 한 예외 처리

- 열린 핸들 및 연결의 자동 정리

## <a name="see-also"></a>참고 항목

[Win32 인터넷 확장 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[WinInet을 사용 하 여 인터넷 클라이언트 응용 프로그램을 보다 쉽게 만들 수 있습니다.](how-wininet-makes-it-easier-to-create-internet-client-applications.md)
