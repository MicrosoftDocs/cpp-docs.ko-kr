---
description: '자세한 정보: MFC WinInet을 사용 하 여 인터넷 클라이언트 응용 프로그램 작성'
title: MFC WinInet 클래스를 사용하여 인터넷 클라이언트 애플리케이션 작성
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC]
- WinInet classes [MFC], programming
- Internet client applications [MFC], writing
- Internet applications [MFC], WinInet
- Internet applications [MFC], client applications
- MFC, Internet applications
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
ms.openlocfilehash: 61cfe3e9892f2bde6d233728b7b95ca0edd16ee8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189134"
---
# <a name="writing-an-internet-client-application-using-mfc-wininet-classes"></a>MFC WinInet 클래스를 사용하여 인터넷 클라이언트 애플리케이션 작성

모든 인터넷 클라이언트 응용 프로그램의 기본은 인터넷 세션입니다. MFC는 [Cinternetsession](../mfc/reference/cinternetsession-class.md)클래스의 개체로 인터넷 세션을 구현 합니다. 이 클래스를 사용 하 여 하나의 인터넷 세션 또는 여러 개의 동시 세션을 만들 수 있습니다.

서버와 통신 하려면 [Cinternetconnection](../mfc/reference/cinternetconnection-class.md) 개체와도 필요 `CInternetSession` 합니다. `CInternetConnection` [Cinternetsession:: GetGetHttpConnection connection](../mfc/reference/cinternetsession-class.md#getftpconnection), [Cinternetsession::](../mfc/reference/cinternetsession-class.md#gethttpconnection)또는 [cinternetsession:: GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection)를 사용 하 여를 만들 수 있습니다. 이러한 각 호출은 프로토콜 유형에만 적용 됩니다. 이러한 호출은 서버에서 읽기 또는 쓰기를 위해 파일을 열지 않습니다. 데이터를 읽거나 쓰려면 별도의 단계로 파일을 열어야 합니다.

대부분의 인터넷 세션에서 `CInternetSession` 개체는 [Cinternetfile](../mfc/reference/cinternetfile-class.md) 개체를 사용 하 여 직접 작동 합니다.

- 인터넷 세션의 경우 [Cinternetsession](../mfc/reference/cinternetsession-class.md)의 인스턴스를 만들어야 합니다.

- 인터넷 세션에서 데이터를 읽거나 쓰는 경우의 인스턴스 `CInternetFile` (또는 해당 하위 클래스, [CHttpFile](../mfc/reference/chttpfile-class.md) 또는 [CGopherFile](../mfc/reference/cgopherfile-class.md))를 만들어야 합니다. 데이터를 읽는 가장 쉬운 방법은 [Cinternetsession:: OpenURL](../mfc/reference/cinternetsession-class.md#openurl)을 호출 하는 것입니다. 이 함수는 사용자가 제공 하는 URL (Universal Resource Locator)을 구문 분석 하 고, URL로 지정 된 서버에 대 한 연결을 열고, 읽기 전용 개체를 반환 `CInternetFile` 합니다. `CInternetSession::OpenURL` 한 프로토콜 유형에 국한 되지 않습니다. 동일한 호출은 FTP, HTTP 또는 gopher URL에 대해 작동 합니다. `CInternetSession::OpenURL` 로컬 파일 에서도 작동 합니다 (대신을 반환 함 `CStdioFile` `CInternetFile` ).

- 인터넷 세션에서 데이터를 읽거나 쓰지 않지만 FTP 디렉터리에서 파일을 삭제 하는 등의 기타 작업을 수행 하는 경우에는 인스턴스를 만들 필요가 없습니다 `CInternetFile` .

개체를 만드는 방법에는 두 가지가 있습니다 `CInternetFile` .

- 를 사용 `CInternetSession::OpenURL` 하 여 서버 연결을 설정 하는 경우를 호출 하면이 `OpenURL` 반환 `CStdioFile` 됩니다.

- `CInternetSession::GetFtpConnection`, 또는를 사용 `GetGopherConnection` 하 여 `GetHttpConnection` 서버 연결을 설정 하 `CFtpConnection::OpenFile` `CGopherConnection::OpenFile` `CHttpConnection::OpenRequest` 는 `CInternetFile` `CGopherFile` `CHttpFile` 경우 각각, 또는를 호출 하 여, 또는을 반환 해야 합니다.

인터넷 클라이언트 응용 프로그램을 구현 하는 단계는 `OpenURL` 또는 기능 중 하나를 사용 하 여 프로토콜 관련 클라이언트를 사용 하 여 일반 인터넷 클라이언트를 만들지 여부에 따라 달라 집니다 `GetConnection` .

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [FTP, HTTP 및 gopher를 사용 하 여 일반적으로 작동 하는 인터넷 클라이언트 응용 프로그램을 작성 어떻게 할까요?](../mfc/steps-in-a-typical-internet-client-application.md)

- [파일을 여는 FTP 클라이언트 응용 프로그램 작성 어떻게 할까요?](../mfc/steps-in-a-typical-ftp-client-application.md)

- [파일을 열지 않지만 파일 삭제와 같은 디렉터리 작업을 수행 하는 FTP 클라이언트 응용 프로그램을 어떻게 할까요? 작성 합니다.](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)

- [Gopher 클라이언트 응용 프로그램 작성 어떻게 할까요?](../mfc/steps-in-a-typical-gopher-client-application.md)

- [HTTP 클라이언트 응용 프로그램 어떻게 할까요? 쓰기](../mfc/steps-in-a-typical-http-client-application.md)

## <a name="see-also"></a>참고 항목

[Win32 인터넷 확장 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[인터넷 클라이언트 응용 프로그램을 만들기 위한 MFC 클래스](../mfc/mfc-classes-for-creating-internet-client-applications.md)<br/>
[인터넷 클라이언트 클래스의 필수 구성 요소](../mfc/prerequisites-for-internet-client-classes.md)
