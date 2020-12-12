---
description: '자세히 알아보기: CGopherConnection 클래스'
title: CGopherConnection 클래스
ms.date: 11/04/2016
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
ms.openlocfilehash: c75cdea4df7a0f5ecbead3770f572d482432382d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184090"
---
# <a name="cgopherconnection-class"></a>CGopherConnection 클래스

Gopher 인터넷 서버 연결을 관리합니다.

> [!NOTE]
> 클래스 `CGopherConnection` , `CGopherFile` , `CGopherFileFind` `CGopherLocator` 및 해당 멤버는 Windows XP 플랫폼에서 작동 하지 않으므로 더 이상 사용 되지 않지만 이전 플랫폼에서는 계속 작동 합니다.

## <a name="syntax"></a>구문

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|`CGopherConnection` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CGopherConnection:: CreateLocator](#createlocator)|Gopher 서버에서 파일을 찾기 위한 [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) 개체를 만듭니다.|
|[CGopherConnection:: GetAttribute](#getattribute)|Gopher 개체에 대 한 특성 정보를 검색 합니다.|
|[CGopherConnection:: System.windows.forms.openfiledialog.openfile](#openfile)|Gopher 파일을 엽니다.|

## <a name="remarks"></a>설명

Gopher 서비스는 MFC WinInet 클래스에서 인식 하는 세 가지 인터넷 서비스 중 하나입니다.

클래스에는 `CGopherConnection` [System.windows.forms.openfiledialog.openfile](#openfile), [Createlocator](#createlocator)및 [getattribute](#getattribute)와 같이 gopher 서비스를 관리 하는 세 개의 추가 멤버 함수 및 생성자가 포함 되어 있습니다.

Gopher 인터넷 서버와 통신 하려면 먼저 [cinternetsession](../../mfc/reference/cinternetsession-class.md)의 인스턴스를 만든 다음 개체를 만들고이에 대 한 포인터를 반환 하는 [Cinternetsession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)를 호출 해야 합니다 `CGopherConnection` . 개체를 직접 만들지는 않습니다 `CGopherConnection` .

에서 다른 MFC 인터넷 클래스로 작업 하는 방법에 대 한 자세한 내용은 `CGopherConnection` WinInet을 [사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md)문서를 참조 하세요. 다른 두 가지 지원 되는 인터넷 서비스를 사용 하는 방법에 대 한 자세한 내용은 FTP 및 HTTP 클래스 [CHttpConnection 및 c](../../mfc/reference/chttpconnection-class.md) [연결](../../mfc/reference/cftpconnection-class.md)을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>요구 사항

**헤더:** afxinet.h

## <a name="cgopherconnectioncgopherconnection"></a><a name="cgopherconnection"></a> CGopherConnection::CGopherConnection

이 멤버 함수를 호출 하 여 개체를 생성 `CGopherConnection` 합니다.

```
CGopherConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CGopherConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>매개 변수

*pSession*<br/>
관련 된 [Cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체에 대 한 포인터입니다.

*hConnected*<br/>
현재 인터넷 세션의 창 핸들입니다.

*pstrServer*<br/>
FTP 서버 이름을 포함 하는 문자열에 대 한 포인터입니다.

*dwContext*<br/>
작업에 대 한 컨텍스트 식별자입니다. *Dwcontext* 는 [Cinternetsession:: onstatuscallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)에서 반환 하는 작업의 상태 정보를 식별 합니다. 기본값은 1로 설정 됩니다. 그러나 작업에 대해 특정 컨텍스트 ID를 명시적으로 할당할 수 있습니다. 개체와 해당 개체에서 수행 하는 모든 작업은 해당 컨텍스트 ID와 연결 됩니다.

*pstrUserName*<br/>
로그인 할 사용자의 이름을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. NULL 인 경우 기본값은 anonymous입니다.

*pstrPassword*<br/>
로그인 하는 데 사용할 암호를 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. *Pstrpassword* 와 *pstrpassword* 이 모두 NULL 인 경우 기본 익명 암호는 사용자의 전자 메일 이름입니다. *Pstrpassword* 가 null 또는 빈 문자열이 고 *PSTRPASSWORD* 이 null이 아닌 경우 빈 암호가 사용 됩니다. 다음 표에서는 *Pstrusername* 및 *pstrusername* 의 네 가지 가능한 설정에 대 한 동작을 설명 합니다.

|*pstrUserName*|*pstrPassword*|FTP 서버에 전송 되는 사용자 이름|FTP 서버로 보낸 암호|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL 또는 ""|NULL 또는 ""|"anonymous"|사용자의 전자 메일 이름|
|NULL이 아닌 문자열|NULL 또는 ""|*pstrUserName*|" "|
|Null이 아닌 NULL 문자열입니다.|오류|오류||
|NULL이 아닌 문자열|NULL이 아닌 문자열|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
서버에서 사용할 TCP/IP 포트를 식별 하는 번호입니다.

### <a name="remarks"></a>설명

을 직접 만들지는 않습니다 `CGopherConnection` . 대신 개체를 만들고이에 대 한 포인터를 반환 하는 [Cinternetsession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)를 호출 `CGopherConnection` 합니다.

## <a name="cgopherconnectioncreatelocator"></a><a name="createlocator"></a> CGopherConnection:: CreateLocator

Gopher 서버에서 파일을 찾거나 식별 하는 gopher 로케이터를 만들려면이 멤버 함수를 호출 합니다.

```
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType);

static CGopherLocator CreateLocator(LPCTSTR pstrLocator);

static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>매개 변수

*pstrDisplayString*<br/>
검색할 gopher 문서 또는 디렉터리의 이름을 포함 하는 문자열에 대 한 포인터입니다. *Pstrdisplaystring* 매개 변수가 NULL 이면 gopher 서버에 대 한 기본 디렉터리가 반환 됩니다.

*pstrSelectorString*<br/>
항목을 검색 하기 위해 gopher 서버로 보낼 선택기 문자열에 대 한 포인터입니다. *pstrSelectorString* 는 NULL 일 수 있습니다.

*dwGopherType*<br/>
이는 *pstrSelectorString* 가 디렉터리 또는 문서를 참조 하는지 여부와 요청이 gopher 인지, 아니면 gopher 이상 인지를 지정 합니다. Windows SDK에서 구조 [GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw) 의 특성을 참조 하세요.

*pstrLocator*<br/>
열려는 파일을 식별 하는 문자열에 대 한 포인터입니다. 일반적으로이 문자열은 [CGopherFileFind:: GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator)호출에서 반환 됩니다.

*pstrServerName*<br/>
Gopher 서버 이름을 포함 하는 문자열에 대 한 포인터입니다.

*nPort*<br/>
이 연결에 대 한 인터넷 포트를 식별 하는 번호입니다.

### <a name="return-value"></a>반환 값

[CGopherLocator](../../mfc/reference/cgopherlocator-class.md) 개체입니다.

### <a name="remarks"></a>설명

멤버 함수의 정적 버전은 서버를 지정 해야 하지만 비정적 버전은 연결 개체의 서버 이름을 사용 합니다.

Gopher 서버에서 정보를 검색 하기 위해 응용 프로그램은 먼저 gopher 로케이터를 가져와야 합니다. 그런 다음 응용 프로그램은 로케이터를 불투명 토큰으로 처리 해야 합니다. 즉, 응용 프로그램은 로케이터를 사용할 수 있지만 직접 조작 하거나 비교할 수는 없습니다. 일반적으로 응용 프로그램에서는 [CGopherFileFind:: FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) 멤버 함수를 호출 하는 데 로케이터를 사용 하 여 특정 정보를 검색 합니다.

## <a name="cgopherconnectiongetattribute"></a><a name="getattribute"></a> CGopherConnection:: GetAttribute

Gopher 서버에서 항목에 대 한 특정 특성 정보를 검색 하려면이 멤버 함수를 호출 합니다.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>매개 변수

*refLocator*<br/>
[CGopherLocator](../../mfc/reference/cgopherlocator-class.md) 개체에 대 한 참조입니다.

*strRequestedAttributes*<br/>
요청 된 특성의 이름을 지정 하는 공백으로 구분 된 문자열입니다.

*strResult*<br/>
로케이터 형식을 받는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

## <a name="cgopherconnectionopenfile"></a><a name="openfile"></a> CGopherConnection:: System.windows.forms.openfiledialog.openfile

이 멤버 함수를 호출 하 여 gopher 서버에서 파일을 엽니다.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>매개 변수

*refLocator*<br/>
[CGopherLocator](../../mfc/reference/cgopherlocator-class.md) 개체에 대 한 참조입니다.

*dwFlags*<br/>
INTERNET_FLAG_ * 플래그의 조합입니다. INTERNET_FLAG_ 플래그에 대 한 자세한 내용은 [Cinternetsession:: OpenUrl](../../mfc/reference/cinternetsession-class.md#openurl) 을 참조 하세요 \* .

*pstrView*<br/>
파일 뷰 문자열에 대 한 포인터입니다. 서버에 파일의 여러 뷰가 있는 경우이 매개 변수는 열려는 파일 뷰를 지정 합니다. *Pstrview* 가 NULL 이면 기본 파일 뷰가 사용 됩니다.

*dwContext*<br/>
열려는 파일의 컨텍스트 ID입니다. *Dwcontext* 에 대 한 자세한 내용은 **설명** 을 참조 하세요.

### <a name="return-value"></a>반환 값

열 [CGopherFile](../../mfc/reference/cgopherfile-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

*Dwcontext* 기본값을 재정의 하 여 컨텍스트 식별자를 선택한 값으로 설정 합니다. 컨텍스트 식별자는 `CGopherConnection` 해당 [Cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체에서 만든 개체의이 특정 작업과 연결 됩니다. 값은 [Cinternetsession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) 으로 반환 되어 식별 된 작업에 대 한 상태를 제공 합니다. 컨텍스트 식별자에 대 한 자세한 내용은 [인터넷 첫 단계: WinInet](../../mfc/wininet-basics.md) 문서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CInternetConnection 클래스](../../mfc/reference/cinternetconnection-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection 클래스](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection 클래스](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection 클래스](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator 클래스](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile 클래스](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession 클래스](../../mfc/reference/cinternetsession-class.md)
