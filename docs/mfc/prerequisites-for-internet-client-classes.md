---
description: '자세한 정보: 인터넷 클라이언트 클래스의 필수 구성 요소'
title: 인터넷 클라이언트 클래스의 필수 구성 요소
ms.date: 11/04/2016
helpviewer_keywords:
- Internet files [MFC], writing to
- Internet [MFC], connections
- FTP (File Transfer Protocol), MFC classes
- Gopher prerequisites [MFC]
- files [MFC], writing to
- classes [MFC], connections
- HTTP [MFC], prerequisites for Internet clients
- connections [MFC], classes for
- Internet client class prerequisites [MFC]
- files [MFC], reading
- URLs [MFC], Internet client applications
- prerequisites, Internet client classes [MFC]
- Gopher client applications [MFC]
ms.assetid: c51d1dfe-260c-4228-8100-e4efd90e9599
ms.openlocfilehash: 9159aa6b3ae4918e406524be05e00fca66cd28a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205878"
---
# <a name="prerequisites-for-internet-client-classes"></a>인터넷 클라이언트 클래스의 필수 구성 요소

인터넷 클라이언트에서 수행 하는 일부 작업 (예: 파일 읽기)에는 필수 구성 요소 작업 (이 경우에는 인터넷 연결 설정)이 있습니다. 다음 표에서는 일부 클라이언트 작업에 대 한 필수 구성 요소를 나열 합니다.

### <a name="general-internet-url-ftp-gopher-or-http"></a>일반 인터넷 URL (FTP, Gopher 또는 HTTP)

|작업|필수 조건|
|------------|------------------|
|연결을 설정합니다.|[Cinternetsession](reference/cinternetsession-class.md) 을 만들어 인터넷 클라이언트 응용 프로그램의 기반을 설정 합니다.|
|URL을 엽니다.|연결을 설정합니다. [Cinternetsession:: OpenURL](reference/cinternetsession-class.md#openurl)을 호출 합니다. `OpenURL`함수는 읽기 전용 리소스 개체를 반환 합니다.|
|URL 데이터를 읽습니다.|URL을 엽니다. [Cinternetfile:: Read](reference/cinternetfile-class.md#read)를 호출 합니다.|
|인터넷 옵션을 설정 합니다.|연결을 설정합니다. [Cinternetsession:: SetOption](reference/cinternetsession-class.md#setoption)를 호출 합니다.|
|상태 정보를 사용 하 여 호출할 함수를 설정 합니다.|연결을 설정합니다. [Cinternetsession:: EnableStatusCallback](reference/cinternetsession-class.md#enablestatuscallback)을 호출 합니다. [Cinternetsession:: OnStatusCallback](reference/cinternetsession-class.md#onstatuscallback) 을 재정의 하 여 호출을 처리 합니다.|

### <a name="ftp"></a>FTP

|작업|필수 조건|
|------------|------------------|
|FTP 연결을 설정 합니다.|이 인터넷 클라이언트 응용 프로그램의 기반으로 [Cinternetsession](reference/cinternetsession-class.md) 을 만듭니다. [Cinternetsession:: GetFtpConnection](reference/cinternetsession-class.md#getftpconnection) 을 호출 하 여 [cinternetsession](reference/cftpconnection-class.md) 개체를 만듭니다.|
|첫 번째 리소스를 찾습니다.|FTP 연결을 설정 합니다. [Cftpfilefind](reference/cftpfilefind-class.md) 개체를 만듭니다. [Cftpfilefind:: FindFile](reference/cftpfilefind-class.md#findfile)을 호출 합니다.|
|사용 가능한 모든 리소스를 열거 합니다.|첫 번째 파일을 찾습니다. FALSE가 반환 될 때까지 [Cftpfilefind:: FindNextFile](reference/cftpfilefind-class.md#findnextfile) 을 호출 합니다.|
|FTP 파일을 엽니다.|FTP 연결을 설정 합니다. Csystem.windows.forms.openfiledialog.openfile [connection::](reference/cftpconnection-class.md#openfile) 를 호출 하 여 [cftpconnection](reference/cinternetfile-class.md) 개체를 만들고 엽니다.|
|FTP 파일을 읽습니다.|읽기 권한이 있는 FTP 파일을 엽니다. [Cinternetfile:: Read](reference/cinternetfile-class.md#read)를 호출 합니다.|
|FTP 파일에 씁니다.|쓰기 권한이 있는 FTP 파일을 엽니다. [Cinternetfile:: Write](reference/cinternetfile-class.md#write)를 호출 합니다.|
|서버에서 클라이언트의 디렉터리를 변경 합니다.|FTP 연결을 설정 합니다. [CSetCurrentDirectory connection::](reference/cftpconnection-class.md#setcurrentdirectory)를 호출 합니다.|
|서버에서 클라이언트의 현재 디렉터리를 검색 합니다.|FTP 연결을 설정 합니다. [Cftpconnection:: GetCurrentDirectory](reference/cftpconnection-class.md#getcurrentdirectory)를 호출 합니다.|

### <a name="http"></a>HTTP

|작업|필수 조건|
|------------|------------------|
|HTTP 연결을 설정 합니다.|이 인터넷 클라이언트 응용 프로그램의 기반으로 [Cinternetsession](reference/cinternetsession-class.md) 을 만듭니다. [Cinternetsession:: GetHttpConnection](reference/cinternetsession-class.md#gethttpconnection) 를 호출 하 여 [CHttpConnection](reference/chttpconnection-class.md) 개체를 만듭니다.|
|HTTP 파일을 엽니다.|HTTP 연결을 설정 합니다. [CHttpConnection:: OpenRequest](reference/chttpconnection-class.md#openrequest) 를 호출 하 여 [CHttpFile](reference/chttpfile-class.md) 개체를 만듭니다. [CHttpFile:: AddRequestHeaders](reference/chttpfile-class.md#addrequestheaders)를 호출 합니다. [CHttpFile:: sendrequest가](reference/chttpfile-class.md#sendrequest)를 호출 합니다.|
|HTTP 파일을 읽습니다.|HTTP 파일을 엽니다. [Cinternetfile:: Read](reference/cinternetfile-class.md#read)를 호출 합니다.|
|HTTP 요청에 대 한 정보를 가져옵니다.|HTTP 연결을 설정 합니다. [CHttpConnection:: OpenRequest](reference/chttpconnection-class.md#openrequest) 를 호출 하 여 [CHttpFile](reference/chttpfile-class.md) 개체를 만듭니다. [CHttpFile:: QueryInfo](reference/chttpfile-class.md#queryinfo)를 호출 합니다.|

### <a name="gopher"></a>고

|작업|필수 조건|
|------------|------------------|
|Gopher 연결을 설정 합니다.|이 인터넷 클라이언트 응용 프로그램의 기반으로 [Cinternetsession](reference/cinternetsession-class.md) 을 만듭니다. [Cinternetsession:: GetGopherConnection](reference/cinternetsession-class.md#getgopherconnection) 를 호출 하 여 [CGopherConnection](reference/cgopherconnection-class.md)를 만듭니다.|
|현재 디렉터리에서 첫 번째 파일을 찾습니다.|Gopher 연결을 설정 합니다. [CGopherFileFind](reference/cgopherfilefind-class.md) 개체를 만듭니다. [CGopherConnection:: CreateLocator](reference/cgopherconnection-class.md#createlocator) 를 호출 하 여 [CGopherLocator](reference/cgopherlocator-class.md) 개체를 만듭니다. [CGopherFileFind:: FindFile](reference/cgopherfilefind-class.md#findfile)에 로케이터를 전달 합니다. 나중에 필요한 경우 [CGopherFileFind:: GetLocator](reference/cgopherfilefind-class.md#getlocator) 를 호출 하 여 파일의 로케이터를 가져옵니다.|
|사용 가능한 모든 파일을 열거 합니다.|첫 번째 파일을 찾습니다. FALSE가 반환 될 때까지 [CGopherFileFind:: FindNextFile](reference/cgopherfilefind-class.md#findnextfile) 을 호출 합니다.|
|Gopher 파일을 엽니다.|Gopher 연결을 설정 합니다. [CGopherConnection:: CreateLocator](reference/cgopherconnection-class.md#createlocator) 를 사용 하 여 gopher 로케이터를 만들거나 [CGopherFileFind:: getlocator](reference/cgopherfilefind-class.md#getlocator)를 사용 하 여 로케이터를 찾습니다. [CGopherConnection:: system.windows.forms.openfiledialog.openfile](reference/cgopherconnection-class.md#openfile)를 호출 합니다.|
|Gopher 파일을 읽습니다.|Gopher 파일을 엽니다. [CGopherFile](reference/cgopherfile-class.md)를 사용 합니다.|

## <a name="see-also"></a>참고 항목

[Win32 인터넷 확장 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[인터넷 클라이언트 응용 프로그램을 만들기 위한 MFC 클래스](mfc-classes-for-creating-internet-client-applications.md)<br/>
[MFC WinInet 클래스를 사용 하 여 인터넷 클라이언트 응용 프로그램 작성](writing-an-internet-client-application-using-mfc-wininet-classes.md)
