---
description: CInternetSession 클래스에 대해 자세히 알아보세요.
title: CInternetSession 클래스
ms.date: 06/20/2018
f1_keywords:
- CInternetSession
- AFXINET/CInternetSession
- AFXINET/CInternetSession::CInternetSession
- AFXINET/CInternetSession::Close
- AFXINET/CInternetSession::EnableStatusCallback
- AFXINET/CInternetSession::GetContext
- AFXINET/CInternetSession::GetCookie
- AFXINET/CInternetSession::GetCookieLength
- AFXINET/CInternetSession::GetFtpConnection
- AFXINET/CInternetSession::GetGopherConnection
- AFXINET/CInternetSession::GetHttpConnection
- AFXINET/CInternetSession::OnStatusCallback
- AFXINET/CInternetSession::OpenURL
- AFXINET/CInternetSession::SetCookie
- AFXINET/CInternetSession::SetOption
helpviewer_keywords:
- CInternetSession [MFC], CInternetSession
- CInternetSession [MFC], Close
- CInternetSession [MFC], EnableStatusCallback
- CInternetSession [MFC], GetContext
- CInternetSession [MFC], GetCookie
- CInternetSession [MFC], GetCookieLength
- CInternetSession [MFC], GetFtpConnection
- CInternetSession [MFC], GetGopherConnection
- CInternetSession [MFC], GetHttpConnection
- CInternetSession [MFC], OnStatusCallback
- CInternetSession [MFC], OpenURL
- CInternetSession [MFC], SetCookie
- CInternetSession [MFC], SetOption
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
ms.openlocfilehash: 54ea5369bc0df2821cd9ac527a4ed91cfdc2c19f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339659"
---
# <a name="cinternetsession-class"></a>CInternetSession 클래스

한 개 또는 여러 개의 동시 인터넷 세션을 만들어 초기화하며, 필요한 경우 프록시 서버에 대한 연결을 설명합니다.

## <a name="syntax"></a>구문

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CInternetSession:: CInternetSession](#cinternetsession)|`CInternetSession` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CInternetSession:: Close](#close)|인터넷 세션이 종료 될 때 인터넷 연결을 닫습니다.|
|[CInternetSession:: EnableStatusCallback](#enablestatuscallback)|상태 콜백 루틴을 설정 합니다.|
|[CInternetSession:: GetContext](#getcontext)|인터넷 세션이 종료 될 때 인터넷 연결을 닫습니다.|
|[CInternetSession:: GetCookie](#getcookie)|지정 된 URL 및 모든 부모 Url에 대 한 쿠키를 반환 합니다.|
|[CInternetSession:: GetCookieLength](#getcookielength)|버퍼에 저장 된 쿠키의 길이를 지정 하는 변수를 검색 합니다.|
|[CInternetSession:: GetFtpConnection](#getftpconnection)|서버와 FTP 세션을 엽니다. 사용자에 대 한 로그입니다.|
|[CInternetSession:: GetGopherConnection](#getgopherconnection)|연결을 열려고 하는 응용 프로그램에 대 한 gopher 서버를 엽니다.|
|[CInternetSession:: GetHttpConnection](#gethttpconnection)|연결을 열려고 하는 응용 프로그램에 대 한 HTTP 서버를 엽니다.|
|[CInternetSession:: OnStatusCallback](#onstatuscallback)|상태 콜백이 활성화 된 경우 작업의 상태를 업데이트 합니다.|
|[CInternetSession:: OpenURL](#openurl)|URL을 구문 분석 하 고 엽니다.|
|[CInternetSession:: SetCookie](#setcookie)|지정 된 URL에 대 한 쿠키를 설정 합니다.|
|[CInternetSession:: SetOption](#setoption)|인터넷 세션에 대 한 옵션을 설정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CInternetSession:: operator HINTERNET](#operator_hinternet)|현재 인터넷 세션에 대 한 핸들입니다.|

## <a name="remarks"></a>설명

응용 프로그램 기간 동안 인터넷 연결을 유지 해야 하는 경우에는 `CInternetSession` [CWinApp](../../mfc/reference/cwinapp-class.md)클래스의 멤버를 만들 수 있습니다.

인터넷 세션을 설정 하면 [Openurl](#openurl)을 호출할 수 있습니다. `CInternetSession` 그런 다음 [AfxParseURL](internet-url-parsing-globals.md#afxparseurl)전역 함수를 호출 하 여 URL을 구문 분석 합니다. 는 프로토콜 형식에 관계 없이 `CInternetSession` URL을 해석 하 고 관리 합니다. URL 리소스 "file://"로 식별 된 로컬 파일에 대 한 요청을 처리할 수 있습니다. `OpenURL` 는 전달 된 이름이 로컬 파일인 경우 [CStdioFile](../../mfc/reference/cstdiofile-class.md) 개체에 대 한 포인터를 반환 합니다.

를 사용 하 여 인터넷 서버에서 URL을 여는 경우 `OpenURL` 사이트에서 정보를 읽을 수 있습니다. 서버에 있는 파일에 대 한 서비스 관련 작업 (예: HTTP, FTP 또는 gopher)을 수행 하려면 해당 서버와의 적절 한 연결을 설정 해야 합니다. 특정 서비스에 대 한 특정 종류의 연결을 직접 열려면 다음 멤버 함수 중 하나를 사용 합니다.

- [GetGopherConnection](#getgopherconnection) gopher 서비스에 대 한 연결을 엽니다.

- [GETHTTPCONNECTION](#gethttpconnection) HTTP 서비스에 대 한 연결을 엽니다.

- FTP 서비스에 대 한 연결을 여는 데 대 한 [Getftpconnection](#getftpconnection) 입니다.

[SetOption](#setoption) 를 사용 하면 제한 시간 값, 다시 시도 횟수 등 세션의 쿼리 옵션을 설정할 수 있습니다.

`CInternetSession` 멤버 함수 [Setcookie](#setcookie), [Getcookie](#getcookie)및 [GetCookieLength](#getcookielength) 는 서버 및 스크립트가 클라이언트 워크스테이션에 대 한 상태 정보를 유지 관리 하는 Win32 쿠키 데이터베이스를 관리 하는 방법을 제공 합니다.

기본 인터넷 프로그래밍 태스크에 대 한 자세한 내용은 [인터넷 첫 단계: WinInet](../../mfc/wininet-basics.md)문서를 참조 하세요. MFC WinInet 클래스를 사용 하는 방법에 대 한 일반적인 내용은 [wininet을 사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md)문서를 참조 하세요.

> [!NOTE]
> `CInternetSession` 지원 되지 않는 서비스 형식에 대해 [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) 를 throw 합니다. 현재 FTP, HTTP, gopher 및 파일의 서비스 유형만 지원 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>요구 사항

**헤더:** afxinet.h

## <a name="cinternetsessioncinternetsession"></a><a name="cinternetsession"></a> CInternetSession:: CInternetSession

이 멤버 함수는 개체를 만들 때 호출 됩니다 `CInternetSession` .

```cpp
CInternetSession(
    LPCTSTR pstrAgent = NULL,
    DWORD_PTR dwContext = 1,
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,
    LPCTSTR pstrProxyName = NULL,
    LPCTSTR pstrProxyBypass = NULL,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>매개 변수

*pstrAgent*<br/>
인터넷 함수를 호출 하는 응용 프로그램 또는 엔터티의 이름을 식별 하는 문자열에 대 한 포인터입니다 (예: "Microsoft 인터넷 브라우저"). *Pstragent* 가 null (기본값) 이면 프레임 워크는 전역 함수 [AfxGetAppName](application-information-and-management.md#afxgetappname)를 호출 합니다 .이 함수는 응용 프로그램의 이름을 포함 하는 null로 끝나는 문자열을 반환 합니다. 일부 프로토콜은이 문자열을 사용 하 여 서버에서 응용 프로그램을 식별 합니다.

*dwContext*<br/>
작업에 대 한 컨텍스트 식별자입니다. *Dwcontext* 는 [Cinternetsession:: onstatuscallback](#onstatuscallback)에서 반환 하는 작업의 상태 정보를 식별 합니다. 기본값은 1로 설정 됩니다. 그러나 작업에 대해 특정 컨텍스트 ID를 명시적으로 할당할 수 있습니다. 개체와 해당 개체에서 수행 하는 모든 작업은 해당 컨텍스트 ID와 연결 됩니다.

*dwAccessType*<br/>
필요한 액세스 유형입니다. 다음은 유효한 값 이며,이 중 하나는 정확히 제공 될 수 있습니다.

- 레지스트리에서 미리 구성 된 설정을 사용 하 여 연결을 INTERNET_OPEN_TYPE_PRECONFIG 합니다. 이 액세스 형식은 기본값으로 설정 됩니다. TIS 프록시를 통해 연결 하려면 *dwAccessType* 를이 값으로 설정 합니다. 그런 다음 레지스트리를 적절 하 게 설정 합니다.

- INTERNET_OPEN_TYPE_DIRECT 인터넷에 직접 연결 합니다.

- INTERNET_OPEN_TYPE_PROXY CERN 프록시를 통해 연결 합니다.

다른 유형의 프록시로 연결 하는 방법에 대 한 자세한 내용은 [일반적인 FTP 클라이언트 응용 프로그램의 단계](../../mfc/steps-in-a-typical-ftp-client-application.md)를 참조 하세요.

*pstrProxyName*<br/>
*DwAccessType* 이 INTERNET_OPEN_TYPE_PROXY로 설정 된 경우 기본 설정 된 CERN 프록시의 이름입니다. 기본값은 NULL입니다.

*pstrProxyBypass*<br/>
선택적 서버 주소 목록을 포함 하는 문자열에 대 한 포인터입니다. 이러한 주소는 프록시 액세스를 사용할 때 우회할 수 있습니다. NULL 값이 제공 되 면 레지스트리에서 바이패스 목록을 읽습니다. 이 매개 변수는 *dwAccessType* 이 INTERNET_OPEN_TYPE_PROXY로 설정 된 경우에만 의미가 있습니다.

*dwFlags*<br/>
다양 한 캐싱 옵션을 나타냅니다. 기본값은 0으로 설정 됩니다. 가능한 값은 다음과 같습니다.

- INTERNET_FLAG_DONT_CACHE는 로컬 또는 게이트웨이 서버에서 데이터를 캐시 하지 않습니다.

- INTERNET_FLAG_OFFLINE 다운로드 작업은 영구적 캐시만을 통해 충족 됩니다. 항목이 캐시에 없으면 적절 한 오류 코드가 반환 됩니다. 이 플래그 **는 비트 or** ( **&#124;**) 연산자와 함께 사용할 수 있습니다.

### <a name="remarks"></a>설명

`CInternetSession` 는 응용 프로그램에서 호출 하는 첫 번째 인터넷 함수입니다. 내부 데이터 구조를 초기화 하 고 응용 프로그램에서 나중에 호출할 수 있도록 준비 합니다.

인터넷 연결을 열 수 없는 경우 `CInternetSession` 는 [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)을 throw 합니다.

### <a name="example"></a>예제

[Cftpfilefind](../../mfc/reference/cftpfilefind-class.md)의 예제를 참조 하세요.

## <a name="cinternetsessionclose"></a><a name="close"></a> CInternetSession:: Close

응용 프로그램에서 개체 사용을 마친 경우이 멤버 함수를 호출 `CInternetSession` 합니다.

```cpp
virtual void Close();
```

### <a name="example"></a>예제

[Cftpfilefind](../../mfc/reference/cftpfilefind-class.md)의 예제를 참조 하세요.

## <a name="cinternetsessionenablestatuscallback"></a><a name="enablestatuscallback"></a> CInternetSession:: EnableStatusCallback

상태 콜백을 사용 하도록 설정 하려면이 멤버 함수를 호출 합니다.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
콜백이 사용 되는지 여부를 지정 합니다. 기본값은 TRUE입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출이 실패 하면 throw 된 [Cinternetexception](../../mfc/reference/cinternetexception-class.md) 개체를 검사 하 여 오류의 원인을 확인 합니다.

### <a name="remarks"></a>설명

상태 콜백을 처리할 때 응용 프로그램의 상태 표시줄에서 작업의 진행 상황 (예: 이름 확인, 서버에 연결 등)에 대 한 상태를 제공할 수 있습니다. 작업 상태를 표시 하는 작업은 장기 작업 중에 특히 좋습니다.

요청을 처리 하는 동안 콜백이 발생 하기 때문에 응용 프로그램은 네트워크에 대 한 데이터 처리량의 저하를 방지 하기 위해 콜백에서 최대한 적은 시간을 소비 해야 합니다. 예를 들어 대화 상자를 콜백에 넣는 작업은 서버가 요청을 종료 하는 데 시간이 오래 걸릴 수 있습니다.

콜백이 보류 중인 동안에는 상태 콜백을 제거할 수 없습니다.

모든 작업을 비동기적으로 처리 하려면 고유한 스레드를 만들거나 MFC를 사용 하지 않고 WinInet 함수를 사용 해야 합니다.

## <a name="cinternetsessiongetcontext"></a><a name="getcontext"></a> CInternetSession:: GetContext

이 멤버 함수를 호출 하 여 특정 응용 프로그램 세션에 대 한 컨텍스트 값을 가져옵니다.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>반환 값

응용 프로그램에서 정의한 컨텍스트 식별자입니다.

### <a name="remarks"></a>설명

[Onstatuscallback](#onstatuscallback) 은에서 반환 된 컨텍스트 ID를 사용 하 여 `GetContext` 특정 응용 프로그램의 상태를 보고 합니다. 예를 들어 사용자가 상태 정보를 반환 하는 인터넷 요청을 활성화 하는 경우 상태 콜백은 컨텍스트 ID를 사용 하 여 해당 특정 요청에 대 한 상태를 보고 합니다. 사용자가 상태 정보를 반환 하는 두 개의 개별 인터넷 요청을 활성화 하는 경우는 `OnStatusCallback` 컨텍스트 식별자를 사용 하 여 해당 요청에 대 한 상태를 반환 합니다. 따라서 컨텍스트 식별자는 모든 상태 콜백 작업에 사용 되며 세션이 종료 될 때까지 세션과 연결 됩니다.

비동기 작업에 대 한 자세한 내용은 [인터넷 첫 단계: WinInet](../../mfc/wininet-basics.md)문서를 참조 하세요.

## <a name="cinternetsessiongetcookie"></a><a name="getcookie"></a> CInternetSession:: GetCookie

이 멤버 함수는 Windows SDK 설명 된 대로 Win32 함수 [Internetgetcookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew)의 동작을 구현 합니다.

```cpp
static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPTSTR pstrCookieData,
    DWORD dwBufLen);

static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    CString& strCookieData);
```

### <a name="parameters"></a>매개 변수

*pstrUrl*<br/>
URL을 포함 하는 문자열에 대 한 포인터입니다.

*pstrCookieName*<br/>
지정 된 URL에 대해 가져올 쿠키의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pstrCookieData*<br/>
첫 번째 오버 로드에서 쿠키 데이터를 받는 버퍼의 주소를 포함 하는 문자열에 대 한 포인터입니다. 이 값은 NULL 일 수 있습니다. 두 번째 오버 로드에서 쿠키 데이터를 받을 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체에 대 한 참조입니다.

*Dw Flen*<br/>
*PstrCookieData* 버퍼의 크기를 지정 하는 변수입니다. 함수가 성공 하면 버퍼는 *pstrCookieData* 버퍼에 복사 된 데이터의 양을 수신 합니다. *PstrCookieData* 가 NULL 인 경우이 매개 변수는 모든 쿠키 데이터를 복사 하는 데 필요한 버퍼의 크기를 지정 하는 값을 받습니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 그렇지 않으면 FALSE를 반환 합니다. 호출이 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인 합니다. 다음 오류 값이 적용 됩니다.

- ERROR_NO_MORE_ITEMS 지정 된 URL과 모든 부모에 대 한 쿠키가 없습니다.

- *Dwbuflen* 에 전달 된 값을 ERROR_INSUFFICIENT_BUFFER 모든 쿠키 데이터를 복사할 수 없습니다. *Dw와 Flen* 에서 반환 되는 값은 모든 데이터를 가져오는 데 필요한 버퍼의 크기입니다.

### <a name="remarks"></a>설명

두 번째 오버 로드에서 MFC는 제공 된 개체에 쿠키 데이터를 검색 합니다 `CString` .

## <a name="cinternetsessiongetcookielength"></a><a name="getcookielength"></a> CInternetSession:: GetCookieLength

이 멤버 함수를 호출 하 여 버퍼에 저장 된 쿠키의 길이를 가져옵니다.

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>매개 변수

*pstrUrl*<br/>
URL을 포함 하는 문자열에 대 한 포인터

*pstrCookieName*<br/>
쿠키의 이름을 포함 하는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

버퍼에 저장 된 쿠키의 길이를 나타내는 DWORD 값입니다. *PstrCookieName* 에 지정 된 이름의 쿠키가 없는 경우 0입니다.

### <a name="remarks"></a>설명

이 값은 [Getcookie](#getcookie)에서 사용 됩니다.

## <a name="cinternetsessiongetftpconnection"></a><a name="getftpconnection"></a> CInternetSession:: GetFtpConnection

이 멤버 함수를 호출 하 여 FTP 연결을 설정 하 고 개체에 대 한 포인터를 가져옵니다 `CFtpConnection` .

```cpp
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>매개 변수

*pstrServer*<br/>
FTP 서버 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pstrUserName*<br/>
로그인 할 사용자의 이름을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. NULL 인 경우 기본값은 anonymous입니다.

*pstrPassword*<br/>
로그인 하는 데 사용할 암호를 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. *Pstrpassword* 와 *pstrpassword* 이 모두 NULL 인 경우 기본 익명 암호는 사용자의 전자 메일 이름입니다. *Pstrpassword* 가 null 또는 빈 문자열이 고 *PSTRPASSWORD* 이 null이 아닌 경우 빈 암호가 사용 됩니다. 다음 표에서는 *Pstrusername* 및 *pstrusername* 의 네 가지 가능한 설정에 대 한 동작을 설명 합니다.

| *pstrUserName*  | *pstrPassword*  | FTP 서버에 전송 되는 사용자 이름 | FTP 서버로 보낸 암호 |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL 또는 ""   |   NULL 또는 ""   |         "anonymous"         |      사용자의 전자 메일 이름      |
| NULL이 아닌 문자열 |   NULL 또는 ""   |       *pstrUserName*        |             " "             |
|      NULL       | NULL이 아닌 문자열 |            오류            |            오류            |
| NULL이 아닌 문자열 | NULL이 아닌 문자열 |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
서버에서 사용할 TCP/IP 포트를 식별 하는 번호입니다.

*bPassive*<br/>
이 FTP 세션의 수동 또는 활성 모드를 지정 합니다. TRUE로 설정 하면 Win32 API를 `dwFlag` INTERNET_FLAG_PASSIVE으로 설정 합니다.

### <a name="return-value"></a>반환 값

[Cftpconnection](../../mfc/reference/cftpconnection-class.md) 개체에 대 한 포인터입니다. 호출이 실패 하면 throw 된 [Cinternetexception](../../mfc/reference/cinternetexception-class.md) 개체를 검사 하 여 오류의 원인을 확인 합니다.

### <a name="remarks"></a>설명

`GetFtpConnection` FTP 서버에 연결 하 고 개체에 대 한 포인터를 만들어 반환 `CFTPConnection` 합니다. 서버에서 특정 작업을 수행 하지 않습니다. 예를 들어 파일을 읽거나 쓰려면 이러한 작업을 별도의 단계로 수행 해야 합니다. 파일 검색, 파일 열기 및 파일 읽기/쓰기에 대 한 자세한 내용은 [Cftpconnection](../../mfc/reference/cftpconnection-class.md) 및 [C\filefilefind](../../mfc/reference/cftpfilefind-class.md) 클래스를 참조 하세요. 일반적인 FTP 연결 작업을 수행 하는 단계는 [WinInet을 사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md) 문서를 참조 하세요.

### <a name="example"></a>예제

[Cftpfilefind](../../mfc/reference/cftpfilefind-class.md)의 예제를 참조 하세요.

## <a name="cinternetsessiongetgopherconnection"></a><a name="getgopherconnection"></a> CInternetSession:: GetGopherConnection

이 멤버 함수를 호출 하 여 새 gopher 연결을 설정 하 고 개체에 대 한 포인터를 가져옵니다 `CGopherConnection` .

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>매개 변수

*pstrServer*<br/>
Gopher 서버 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pstrUserName*<br/>
사용자 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pstrPassword*<br/>
액세스 암호를 포함 하는 문자열에 대 한 포인터입니다.

*nPort*<br/>
서버에서 사용할 TCP/IP 포트를 식별 하는 번호입니다.

### <a name="return-value"></a>반환 값

[CGopherConnection](../../mfc/reference/cgopherconnection-class.md) 개체에 대 한 포인터입니다. 호출이 실패 하면 throw 된 [Cinternetexception](../../mfc/reference/cinternetexception-class.md) 개체를 검사 하 여 오류의 원인을 확인 합니다.

### <a name="remarks"></a>설명

`GetGopherConnection` gopher 서버에 연결 하 고 개체에 대 한 포인터를 만들어 반환 `CGopherConnection` 합니다. 서버에서 특정 작업을 수행 하지 않습니다. 예를 들어 데이터를 읽거나 쓰려면 이러한 작업을 별도의 단계로 수행 해야 합니다. 파일 검색, 파일 열기 및 파일 읽기/쓰기에 대 한 자세한 내용은 [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md)및 [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) 클래스를 참조 하세요. FTP 사이트를 검색 하는 방법에 대 한 자세한 내용은 구성원 함수 [Openurl](#openurl)을 참조 하세요. 일반적인 gopher 연결 작업을 수행 하는 단계는 [WinInet을 사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md) 문서를 참조 하세요.

## <a name="cinternetsessiongethttpconnection"></a><a name="gethttpconnection"></a> CInternetSession:: GetHttpConnection

이 멤버 함수를 호출 하 여 HTTP 연결을 설정 하 고 개체에 대 한 포인터를 가져옵니다 `CHttpConnection` .

```cpp
CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);

CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);
```

### <a name="parameters"></a>매개 변수

*pstrServer*<br/>
HTTP 서버 이름을 포함 하는 문자열에 대 한 포인터입니다.

*nPort*<br/>
서버에서 사용할 TCP/IP 포트를 식별 하는 번호입니다.

*pstrUserName*<br/>
사용자 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pstrPassword*<br/>
액세스 암호를 포함 하는 문자열에 대 한 포인터입니다.

*dwflags*<br/>
플래그의 조합 `INTERNET_FLAG_*` 입니다. *DwFlags* 값에 대 한 설명은 [CHttpConnection:: openrequest](../../mfc/reference/chttpconnection-class.md#openrequest) 의 **설명 섹션에 있는 표** 를 참조 하세요.

### <a name="return-value"></a>반환 값

[CHttpConnection](../../mfc/reference/chttpconnection-class.md) 개체에 대 한 포인터입니다. 호출이 실패 하면 throw 된 [Cinternetexception](../../mfc/reference/cinternetexception-class.md) 개체를 검사 하 여 오류의 원인을 확인 합니다.

### <a name="remarks"></a>설명

`GetHttpConnection` HTTP 서버에 연결 하 고 개체에 대 한 포인터를 만들어 반환 `CHttpConnection` 합니다. 서버에서 특정 작업을 수행 하지 않습니다. 예를 들어 HTTP 헤더를 쿼리하려면 별도의 단계로이 작업을 수행 해야 합니다. HTTP 서버에 대 한 연결을 사용 하 여 수행할 수 있는 작업에 대 한 자세한 내용은 [CHttpConnection](../../mfc/reference/chttpconnection-class.md) 및 [CHttpFile](../../mfc/reference/chttpfile-class.md) 클래스를 참조 하세요. HTTP 사이트를 검색 하는 방법에 대 한 자세한 내용은 멤버 함수 [Openurl](#openurl)을 참조 하세요. 일반적인 HTTP 연결 작업을 수행 하는 단계는 [WinInet을 사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md) 문서를 참조 하세요.

## <a name="cinternetsessiononstatuscallback"></a><a name="onstatuscallback"></a> CInternetSession:: OnStatusCallback

이 멤버 함수는 상태 콜백이 활성화 되 고 작업이 보류 중인 경우 상태를 업데이트 하기 위해 프레임 워크에서 호출 됩니다.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>매개 변수

*dwContext*<br/>
응용 프로그램에서 제공 하는 컨텍스트 값입니다.

*dwInternetStatus*<br/>
콜백이 생성 되는 이유를 나타내는 상태 코드입니다. 가능한 값에 대 한 테이블은 **설명** 을 참조 하세요.

*lpvStatusInformation*<br/>
이 콜백과 관련 된 정보를 포함 하는 버퍼에 대 한 포인터입니다.

*dwStatusInformationLength*<br/>
*Lpvstatusinformation* 의 크기입니다.

### <a name="remarks"></a>설명

상태 콜백을 활용 하려면 먼저 [Enablestatuscallback](#enablestatuscallback) 을 호출 해야 합니다.

*Dwinternetstatus* 매개 변수는 수행 중인 작업을 나타내며 *Lpvstatusinformation* 의 내용을 결정 합니다. *Dwstatusinformationlength* 는 *Lpvstatusinformation* 에 포함 된 데이터의 길이를 나타냅니다. *Dwinternetstatus* 에 대 한 다음 상태 값은 다음과 같이 정의 됩니다.

|값|의미|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|*Lpvstatusinformation* 에 포함 된 이름의 IP 주소를 조회 합니다.|
|INTERNET_STATUS_NAME_RESOLVED|*Lpvstatusinformation* 에 포함 된 이름의 IP 주소를 발견 했습니다.|
|INTERNET_STATUS_CONNECTING_TO_SERVER|*Lpvstatusinformation* 이 가리키는 소켓 주소 ([SOCKADDR](/windows/win32/winsock/sockaddr-2))에 연결 합니다.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|*Lpvstatusinformation* 이 가리키는 소켓 주소 (SOCKADDR)에 연결 했습니다.|
|INTERNET_STATUS_SENDING_REQUEST|서버에 정보 요청을 보내는 중입니다. *Lpvstatusinformation* 매개 변수가 NULL입니다.|
|INTERNET_STATUS_ REQUEST_SENT|서버에 정보 요청을 보냈습니다. *Lpvstatusinformation* 매개 변수가 NULL입니다.|
|INTERNET_STATUS_RECEIVING_RESPONSE|서버가 요청에 응답 하기를 기다리는 중입니다. *Lpvstatusinformation* 매개 변수가 NULL입니다.|
|INTERNET_STATUS_RESPONSE_RECEIVED|서버에서 응답을 받았습니다. *Lpvstatusinformation* 매개 변수가 NULL입니다.|
|INTERNET_STATUS_CLOSING_CONNECTION|서버에 대 한 연결을 닫는 중입니다. *Lpvstatusinformation* 매개 변수가 NULL입니다.|
|INTERNET_STATUS_CONNECTION_CLOSED|서버에 대 한 연결을 닫았습니다. *Lpvstatusinformation* 매개 변수가 NULL입니다.|
|INTERNET_STATUS_HANDLE_CREATED|Win32 API 함수 [Internetconnect](/windows/win32/api/wininet/nf-wininet-internetconnectw) 에서 새 핸들을 만들었음을 나타내는 데 사용 됩니다. 이렇게 하면 연결에 너무 오래 걸리는 경우 응용 프로그램은 다른 스레드에서 Win32 함수 [Internetclosehandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle) 을 호출할 수 있습니다. 이러한 함수에 대 한 자세한 내용은 Windows SDKfor를 참조 하세요.|
|INTERNET_STATUS_HANDLE_CLOSING|이 핸들 값을 종료 했습니다.|

상태 콜백 루틴이 수행 되기 전에 약간의 동작이 필요 하도록이 멤버 함수를 재정의 합니다.

> [!NOTE]
> 상태 콜백에는 스레드 상태 보호가 필요 합니다. 공유 라이브러리에서 MFC를 사용 하는 경우 재정의의 시작 부분에 다음 줄을 추가 합니다.

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

비동기 작업에 대 한 자세한 내용은 [인터넷 첫 단계: WinInet](../../mfc/wininet-basics.md)문서를 참조 하세요.

## <a name="cinternetsessionopenurl"></a><a name="openurl"></a> CInternetSession:: OpenURL

이 멤버 함수를 호출 하 여 HTTP 서버에 지정 된 요청을 보내고 클라이언트에서 요청과 함께 보낼 추가 RFC822, MIME 또는 HTTP 헤더를 지정할 수 있도록 합니다.

```cpp
CStdioFile* OpenURL(
    LPCTSTR pstrURL,
    DWORD_PTR dwContext = 1,
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLength = 0);
```

### <a name="parameters"></a>매개 변수

*pstrURL*<br/>
읽기를 시작할 URL의 이름에 대 한 포인터입니다. File:, ftp:, gopher: 또는 http:로 시작 하는 Url만 지원 됩니다. *PstrURL* 가 NULL 인 경우 어설션 합니다.

*dwContext*<br/>
콜백에서 반환 된 핸들과 함께 전달 되는 응용 프로그램 정의 값입니다.

*dwFlags*<br/>
이 연결을 처리 하는 방법을 설명 하는 플래그입니다. 유효한 플래그에 대 한 자세한 내용은 **설명 부분** 을 참조 하십시오. 유효한 플래그는 다음과 같습니다.

- 기본값을 INTERNET_FLAG_TRANSFER_ASCII 합니다. 파일을 ASCII 텍스트로 전송 합니다.

- 파일을 이진 파일로 전송 INTERNET_FLAG_TRANSFER_BINARY 합니다.

- 로컬에 캐시 된 경우에도 네트워크에서 데이터를 가져올 INTERNET_FLAG_RELOAD.

- INTERNET_FLAG_DONT_CACHE는 데이터를 로컬로 또는 게이트웨이에서 캐시 하지 않습니다.

- INTERNET_FLAG_SECURE이 플래그는 HTTP 요청에만 적용 됩니다. SSL(Secure Sockets Layer) 또는 PCT를 사용 하 여 통신에 보안 트랜잭션을 요청 합니다.

- 가능 하면 `OpenUrl` 각 연결 요청에 대해 새 세션을 만드는 대신에서 생성 된 새 요청에 대 한 기존 연결을 서버에 다시 사용 합니다. INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT

- FTP 사이트에 사용 되는 INTERNET_FLAG_PASSIVE입니다. 수동 FTP 의미 체계를 사용 합니다. 의 [Cinternetconnection](../../mfc/reference/cinternetconnection-class.md) 에 사용 `OpenURL` 됩니다.

*pstrHeaders*<br/>
HTTP 서버로 보낼 헤더를 포함 하는 문자열에 대 한 포인터입니다.

*dwHeadersLength*<br/>
추가 헤더의 길이 (문자)입니다. 이 값이-1L이 고 *Pstrheaders* 가 NULL이 아닌 경우 *pstrheaders* 가 0으로 끝나고 길이가 계산 된 것으로 간주 됩니다.

### <a name="return-value"></a>반환 값

FTP, GOPHER, HTTP 및 파일 형식 인터넷 서비스에 대 한 파일 핸들을 반환 합니다. 구문 분석에 실패 한 경우 NULL을 반환 합니다.

반환 되는 포인터는 `OpenURL` *pstrURL* 의 서비스 유형에 따라 달라 집니다. 다음 표에서는 가능한 포인터가 `OpenURL` 반환 될 수 있음을 보여 줍니다.

|URL 형식|반환|
|--------------|-------------|
|`file://`|`CStdioFile*`|
|`http://`|`CHttpFile*`|
|`gopher://`|`CGopherFile*`|
|`ftp://`|`CInternetFile*`|

### <a name="remarks"></a>설명

*DwFlags* 매개 변수는 INTERNET_FLAG_TRANSFER_ASCII 또는 INTERNET_FLAG_TRANSFER_BINARY를 포함 해야 하지만 둘 다 포함 해야 하는 것은 아닙니다. 나머지 플래그는 비트 **or** 연산자 ( **&#124;**)와 함께 사용할 수 있습니다.

`OpenURL`는 Win32 함수를 래핑하고 `InternetOpenURL` 인터넷 서버에서 데이터를 다운로드 하 고 검색 하 고 읽기만 허용 합니다. `OpenURL` 원격 위치에서 파일 조작을 허용 하지 않으므로 [Cinternetconnection](../../mfc/reference/cinternetconnection-class.md) 개체가 필요 하지 않습니다.

파일에 쓰기와 같이 연결별 (프로토콜 관련) 함수를 사용 하려면 세션을 열고 특정 종류의 연결을 연 다음 해당 연결을 사용 하 여 원하는 모드에서 파일을 열어야 합니다. `CInternetConnection`연결 관련 함수에 대 한 자세한 내용은을 참조 하세요.

## <a name="cinternetsessionoperator-hinternet"></a><a name="operator_hinternet"></a> CInternetSession:: operator HINTERNET

이 연산자를 사용 하 여 현재 인터넷 세션에 대 한 Windows 핸들을 가져옵니다.

```cpp
operator HINTERNET() const;
```

## <a name="cinternetsessionsetcookie"></a><a name="setcookie"></a> CInternetSession:: SetCookie

지정 된 URL에 대 한 쿠키를 설정 합니다.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>매개 변수

*pstrUrl*<br/>
쿠키를 설정 해야 하는 URL을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*pstrCookieName*<br/>
쿠키의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pstrCookieData*<br/>
URL과 연결할 실제 문자열 데이터를 포함 하는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 그렇지 않으면 FALSE를 반환 합니다. 특정 오류 코드를 가져오려면를 호출 합니다. `GetLastError.`

### <a name="remarks"></a>설명

이 멤버 함수는 Windows SDK 설명 된 대로 Win32 메시지 [Internetsetcookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew)의 동작을 구현 합니다.

## <a name="cinternetsessionsetoption"></a><a name="setoption"></a> CInternetSession:: SetOption

이 멤버 함수를 호출 하 여 인터넷 세션에 대 한 옵션을 설정 합니다.

```cpp
BOOL SetOption(
    DWORD dwOption,
    LPVOID lpBuffer,
    DWORD dwBufferLength,
    DWORD dwFlags = 0);

BOOL SetOption(
    DWORD dwOption,
    DWORD dwValue,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>매개 변수

*dwOption*<br/>
설정할 인터넷 옵션입니다. 가능한 옵션의 목록은 Windows SDKfor [옵션 플래그](/windows/win32/WinInet/option-flags) 를 참조 하세요.

*lpBuffer*<br/>
옵션 설정을 포함 하는 버퍼입니다.

*dwBufferLength*<br/>
*Lpbuffer* 의 길이 또는 *dwvalue* 의 크기입니다.

*dwValue*<br/>
옵션 설정을 포함 하는 DWORD입니다.

*dwFlags*<br/>
다양 한 캐싱 옵션을 나타냅니다. 기본값은 0으로 설정 됩니다. 가능한 값은 다음과 같습니다.

- INTERNET_FLAG_DONT_CACHE는 로컬 또는 게이트웨이 서버에서 데이터를 캐시 하지 않습니다.

- INTERNET_FLAG_OFFLINE 다운로드 작업은 영구적 캐시만을 통해 충족 됩니다. 항목이 캐시에 없으면 적절 한 오류 코드가 반환 됩니다. 이 플래그 **는 비트 or** ( **&#124;**) 연산자와 함께 사용할 수 있습니다.

### <a name="return-value"></a>반환 값

작업에 성공 하면 TRUE 값이 반환 됩니다. 오류가 발생 한 경우 FALSE 값이 반환 됩니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 클래스](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection 클래스](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection 클래스](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection 클래스](../../mfc/reference/cgopherconnection-class.md)
