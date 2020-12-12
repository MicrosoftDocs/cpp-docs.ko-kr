---
description: '자세한 정보: 일반적인 HTTP 클라이언트 응용 프로그램의 단계'
title: 일반적인 HTTP 클라이언트 애플리케이션의 단계
ms.date: 11/04/2016
helpviewer_keywords:
- HTTP client applications [MFC]
- client applications [MFC], HTTP
- Internet applications [MFC], HTTP client applications
- applications [MFC], HTTP client
- Internet client applications [MFC], HTTP table
- WinInet classes [MFC], HTTP
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
ms.openlocfilehash: 0f08ca7629c389df67b579b8c20acceeb16b0cd3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216602"
---
# <a name="steps-in-a-typical-http-client-application"></a>일반적인 HTTP 클라이언트 애플리케이션의 단계

다음 표에서는 일반적인 HTTP 클라이언트 응용 프로그램에서 수행할 수 있는 단계를 보여 줍니다.

|목표|수행할 작업|효과|
|---------------|----------------------|-------------|
|HTTP 세션을 시작 합니다.|[Cinternetsession](../mfc/reference/cinternetsession-class.md) 개체를 만듭니다.|WinInet을 초기화하고 서버에 연결합니다.|
|HTTP 서버에 연결 합니다.|[Cinternetsession:: GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection)를 사용 합니다.|[CHttpConnection](../mfc/reference/chttpconnection-class.md) 개체를 반환 합니다.|
|HTTP 요청을 엽니다.|[CHttpConnection:: OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest)를 사용 합니다.|[CHttpFile](../mfc/reference/chttpfile-class.md) 개체를 반환 합니다.|
|HTTP 요청을 보냅니다.|[CHttpFile:: AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders) 및 [CHttpFile:: sendrequest가](../mfc/reference/chttpfile-class.md#sendrequest)를 사용 합니다.|파일을 찾습니다. 파일을 찾을 수 없으면 FALSE를 반환합니다.|
|파일에서 읽습니다.|[CHttpFile](../mfc/reference/chttpfile-class.md)를 사용 합니다.|제공 하는 버퍼를 사용 하 여 지정 된 바이트 수를 읽습니다.|
|예외를 처리합니다.|[Cinternetexception](../mfc/reference/cinternetexception-class.md) 클래스를 사용 합니다.|모든 공용 인터넷 예외 형식을 처리합니다.|
|HTTP 세션을 종료 합니다.|[Cinternetsession](../mfc/reference/cinternetsession-class.md) 개체를 삭제 합니다.|열린 파일 핸들 및 연결을 자동으로 정리합니다.|

## <a name="see-also"></a>참고 항목

[Win32 인터넷 확장 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[인터넷 클라이언트 클래스의 필수 구성 요소](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[MFC WinInet 클래스를 사용 하 여 인터넷 클라이언트 응용 프로그램 작성](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
