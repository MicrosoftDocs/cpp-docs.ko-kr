---
description: '자세한 정보: 인터넷 클라이언트 응용 프로그램을 만들기 위한 MFC 클래스'
title: 인터넷 클라이언트 애플리케이션을 만들기 위한 MFC 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
ms.openlocfilehash: c68110182b01d9c425090a926ee1e352ca3d3bdf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280679"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>인터넷 클라이언트 애플리케이션을 만들기 위한 MFC 클래스

MFC는 인터넷 클라이언트 응용 프로그램을 작성 하기 위한 다음과 같은 클래스와 전역 함수를 제공 합니다. 들여쓰기는 클래스가 위의 들여쓰지 않은 클래스에서 파생 되었음을 나타냅니다. `CGopherFile` 및는와 같이 `CHttpFile` 에서 파생 `CInternetFile` 됩니다. 이러한 클래스 및 전역 함수는 AFXINET.H에서 선언 됩니다. AFX에 선언 된를 제외 하 고는 h `CFileFind` 입니다.

## <a name="classes"></a>클래스

- [CInternetSession](reference/cinternetsession-class.md)

- [CInternetConnection](reference/cinternetconnection-class.md)

  - [CFtpConnection](reference/cftpconnection-class.md)

  - [CGopherConnection](reference/cgopherconnection-class.md)

  - [CHttpConnection](reference/chttpconnection-class.md)

- [CInternetFile](reference/cinternetfile-class.md)

  - [CGopherFile](reference/cgopherfile-class.md)

  - [CHttpFile](reference/chttpfile-class.md)

- [CFileFind](reference/cfilefind-class.md)

  - [CFtpFileFind](reference/cftpfilefind-class.md)

  - [CGopherFileFind](reference/cgopherfilefind-class.md)

- [CGopherLocator](reference/cgopherlocator-class.md)

- [CInternetException](reference/cinternetexception-class.md)

## <a name="global-functions"></a>전역 함수

- [AfxParseURL](reference/internet-url-parsing-globals.md#afxparseurl)

- [AfxGetInternetHandleType](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [AfxThrowInternetException](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>참고 항목

[Win32 인터넷 확장 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[인터넷 클라이언트 클래스의 필수 구성 요소](prerequisites-for-internet-client-classes.md)<br/>
[MFC WinInet 클래스를 사용 하 여 인터넷 클라이언트 응용 프로그램 작성](writing-an-internet-client-application-using-mfc-wininet-classes.md)
