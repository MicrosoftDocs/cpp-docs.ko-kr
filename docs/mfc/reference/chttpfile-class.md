---
description: '자세히 알아보기: CHttpFile 클래스'
title: CHttpFile 클래스
ms.date: 11/04/2016
f1_keywords:
- CHttpFile
- AFXINET/CHttpFile
- AFXINET/CHttpFile::CHttpFile
- AFXINET/CHttpFile::AddRequestHeaders
- AFXINET/CHttpFile::EndRequest
- AFXINET/CHttpFile::GetFileURL
- AFXINET/CHttpFile::GetObject
- AFXINET/CHttpFile::GetVerb
- AFXINET/CHttpFile::QueryInfo
- AFXINET/CHttpFile::QueryInfoStatusCode
- AFXINET/CHttpFile::SendRequest
- AFXINET/CHttpFile::SendRequestEx
helpviewer_keywords:
- CHttpFile [MFC], CHttpFile
- CHttpFile [MFC], AddRequestHeaders
- CHttpFile [MFC], EndRequest
- CHttpFile [MFC], GetFileURL
- CHttpFile [MFC], GetObject
- CHttpFile [MFC], GetVerb
- CHttpFile [MFC], QueryInfo
- CHttpFile [MFC], QueryInfoStatusCode
- CHttpFile [MFC], SendRequest
- CHttpFile [MFC], SendRequestEx
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
ms.openlocfilehash: 95beff477e19ef15235ceb7235aa0240ec07ff65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209973"
---
# <a name="chttpfile-class"></a>CHttpFile 클래스

HTTP 서버에서 파일을 요청하고 읽는 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CHttpFile:: CHttpFile](#chttpfile)|`CHttpFile` 개체를 만듭니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CHttpFile:: AddRequestHeaders](#addrequestheaders)|HTTP 서버로 전송 된 요청에 헤더를 추가 합니다.|
|[CHttpFile:: EndRequest](#endrequest)|[Sendrequestex](#sendrequestex) 멤버 함수를 사용 하 여 HTTP 서버로 전송 된 요청을 종료 합니다.|
|[CHttpFile:: GetFileURL](#getfileurl)|지정 된 파일의 URL을 가져옵니다.|
|[CHttpFile:: GetObject](#getobject)|HTTP 서버에 대 한 요청에 있는 동사의 대상 개체를 가져옵니다.|
|[CHttpFile:: GetVerb](#getverb)|HTTP 서버에 대 한 요청에 사용 된 동사를 가져옵니다.|
|[CHttpFile:: QueryInfo](#queryinfo)|HTTP 서버에서 응답 또는 요청 헤더를 반환 합니다.|
|[CHttpFile:: QueryInfoStatusCode](#queryinfostatuscode)|HTTP 요청과 연결 된 상태 코드를 검색 하 여 제공 된 `dwStatusCode` 매개 변수에 배치 합니다.|
|[CHttpFile:: Sendrequest가](#sendrequest)|HTTP 서버에 요청을 보냅니다.|
|[CHttpFile:: SendRequestEx](#sendrequestex)|의 [Write](../../mfc/reference/cinternetfile-class.md#write) 또는 [writestring](../../mfc/reference/cinternetfile-class.md#writestring) 메서드를 사용 하 여 HTTP 서버에 요청을 보냅니다 `CInternetFile` .|

## <a name="remarks"></a>설명

인터넷 세션이 HTTP 서버에서 데이터를 읽는 경우의 인스턴스를 만들어야 합니다 `CHttpFile` .

에서 다른 MFC 인터넷 클래스로 작업 하는 방법에 대 한 자세한 내용은 `CHttpFile` WinInet을 [사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>요구 사항

**헤더:** afxinet.h

## <a name="chttpfileaddrequestheaders"></a><a name="addrequestheaders"></a> CHttpFile:: AddRequestHeaders

Http 요청 핸들에 하나 이상의 HTTP 요청 헤더를 추가 하려면이 멤버 함수를 호출 합니다.

```
BOOL AddRequestHeaders(
    LPCTSTR pstrHeaders,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW,
    int dwHeadersLen = -1);

BOOL AddRequestHeaders(
    CString& str,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW);
```

### <a name="parameters"></a>매개 변수

*pstrHeaders*<br/>
요청에 추가할 머리글이 나 헤더를 포함 하는 문자열에 대 한 포인터입니다. 각 헤더는 CR/LF 쌍으로 종료 해야 합니다.

*dwFlags*<br/>
새 헤더의 의미 체계를 수정 합니다. 다음 중 하나일 수 있습니다.

- 플래그를 사용 하 여 다음 헤더에 있는 첫 번째 헤더를 추가 하는 것과 같은 이름의 헤더를 병합 HTTP_ADDREQ_FLAG_COALESCE 합니다. 예를 들어 "Accept: text/ \* " 다음에 "accept: audio/"를 입력 하면 \* 단일 헤더 "accept: text/ \* , audio/"가 생성 \* 됩니다. 결합 된 또는 별도의 헤더로 전송 된 요청에 의해 수신 된 데이터와 관련 하 여 결합 된 스키마를 확인 하는 것은 호출 응용 프로그램에 따라 다릅니다.

- HTTP_ADDREQ_FLAG_REPLACE 제거를 수행 하 고를 추가 하 여 현재 헤더를 바꿉니다. 헤더 이름은 현재 헤더를 제거 하는 데 사용 되 고 전체 값은 새 헤더를 추가 하는 데 사용 됩니다. 헤더 값이 비어 있고 헤더가 있으면 제거 됩니다. 비어 있지 않으면 헤더 값이 대체 됩니다.

- HTTP_ADDREQ_FLAG_ADD_IF_NEW 헤더가 아직 없는 경우에만 해당 헤더를 추가 합니다. 하나가 있으면 오류가 반환 됩니다.

- REPLACE와 함께 사용 되는 HTTP_ADDREQ_FLAG_ADD입니다. 헤더가 없으면 헤더를 추가 합니다.

*dwHeadersLen*<br/>
*Pstrheaders* 의 길이 (문자)입니다. -1L 이면 *Pstrheaders* 가 0으로 종료 된 것으로 간주 되 고 길이가 계산 됩니다.

*str*<br/>
추가할 요청 헤더 또는 헤더를 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

`AddRequestHeaders` HTTP 요청 핸들에 추가 자유 형식 헤더를 추가 합니다. HTTP 서버에 전송 되는 정확한 요청을 세부적으로 제어 해야 하는 정교한 클라이언트에서 사용 하기 위한 것입니다.

> [!NOTE]
> 응용 프로그램은 HTTP_ADDREQ_FLAG_ADD 또는 HTTP_ADDREQ_FLAG_ADD_IF_NEW를 사용 하 여 호출에 대해 *Pstrheaders* 또는 *str* 의 여러 헤더를 전달할 수 있습니다 `AddRequestHeaders` . 응용 프로그램에서 HTTP_ADDREQ_FLAG_REMOVE 또는 HTTP_ADDREQ_FLAG_REPLACE를 사용 하 여 헤더를 제거 하거나 바꾸려고 하면 *lpszHeaders* 에서 하나의 헤더만 제공할 수 있습니다.

## <a name="chttpfilechttpfile"></a><a name="chttpfile"></a> CHttpFile:: CHttpFile

이 멤버 함수를 호출 하 여 개체를 생성 `CHttpFile` 합니다.

```
CHttpFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrObject,
    LPCTSTR pstrServer,
    LPCTSTR pstrVerb,
    DWORD_PTR dwContext);

CHttpFile(
    HINTERNET hFile,
    LPCTSTR pstrVerb,
    LPCTSTR pstrObject,
    CHttpConnection* pConnection);
```

### <a name="parameters"></a>매개 변수

*hFile*<br/>
인터넷 파일에 대 한 핸들입니다.

*hSession*<br/>
인터넷 세션에 대 한 핸들입니다.

*pstrObject*<br/>
개체를 포함 하는 문자열에 대 한 포인터 `CHttpFile` 입니다.

*pstrServer*<br/>
서버 이름이 포함 된 문자열에 대 한 포인터입니다.

*pstrVerb*<br/>
요청을 보낼 때 사용할 메서드를 포함 하는 문자열에 대 한 포인터입니다. POST, HEAD 또는 GET이 될 수 있습니다.

*dwContext*<br/>
개체에 대 한 컨텍스트 식별자 `CHttpFile` 입니다. 이 매개 변수에 대 한 자세한 내용은 **설명 부분** 을 참조 하십시오.

*pConnection*<br/>
[CHttpConnection](../../mfc/reference/chttpconnection-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

개체를 직접 생성 하지 `CHttpFile` 않고 대신 [Cinternetsession:: openurl](../../mfc/reference/cinternetsession-class.md#openurl) 또는 [CHttpConnection:: openurl](../../mfc/reference/chttpconnection-class.md#openrequest) 를 대신 호출 합니다.

의 기본값은 `dwContext` MFC에서 `CHttpFile` 개체를 만든 [cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체의 개체로 보냅니다 `CHttpFile` . `CInternetSession::OpenURL`또는 `CHttpConnection` 를 호출 하 여 개체를 생성 하는 경우 `CHttpFile` 기본값을 재정의 하 여 컨텍스트 식별자를 선택한 값으로 설정할 수 있습니다. 컨텍스트 식별자가 식별 된 개체에 대 한 상태를 제공 하기 위해 [Cinternetsession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) 으로 반환 됩니다. 컨텍스트 식별자에 대 한 자세한 내용은 [인터넷 첫 단계: WinInet](../../mfc/wininet-basics.md) 문서를 참조 하세요.

## <a name="chttpfileendrequest"></a><a name="endrequest"></a> CHttpFile:: EndRequest

[Sendrequestex](#sendrequestex) 멤버 함수를 사용 하 여 HTTP 서버로 전송 된 요청을 종료 하려면이 멤버 함수를 호출 합니다.

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>매개 변수

*dwFlags*<br/>
작업을 설명 하는 플래그입니다. 적절 한 플래그 목록은 Windows SDK의 [HttpEndRequest](/windows/win32/api/wininet/nf-wininet-httpendrequestw) 를 참조 하세요.

*lpBuffIn*<br/>
작업에 사용 되는 입력 버퍼를 설명 하는 초기화 된 [INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) 에 대 한 포인터입니다.

*dwContext*<br/>
`CHttpFile` 작업에 대한 컨텍스트 식별자입니다. 이 매개 변수에 대 한 자세한 내용은 설명 부분을 참조 하십시오.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출이 실패 하면 throw 된 [Cinternetexception](../../mfc/reference/cinternetexception-class.md) 개체를 검사 하 여 오류의 원인을 확인 합니다.

### <a name="remarks"></a>설명

*Dwcontext* 의 기본값은 MFC에서 `CHttpFile` 개체를 만든 [cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체의 개체로 보냅니다 `CHttpFile` . [Cinternetsession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) 또는 [CHttpConnection](../../mfc/reference/chttpconnection-class.md) 를 호출 하 여 개체를 생성 하는 경우 `CHttpFile` 기본값을 재정의 하 여 컨텍스트 식별자를 선택한 값으로 설정할 수 있습니다. 컨텍스트 식별자가 식별 된 개체에 대 한 상태를 제공 하기 위해 [Cinternetsession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) 으로 반환 됩니다. 컨텍스트 식별자에 대 한 자세한 내용은 [Internet First 단계: WinInet](../../mfc/wininet-basics.md) 문서를 참조 하세요.

## <a name="chttpfilegetfileurl"></a><a name="getfileurl"></a> CHttpFile:: GetFileURL

HTTP 파일의 이름을 URL로 가져오려면이 멤버 함수를 호출 합니다.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>반환 값

이 파일과 관련 된 리소스를 참조 하는 URL을 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체입니다.

### <a name="remarks"></a>설명

[Sendrequest가](#sendrequest) 또는 `CHttpFile` [openurl](../../mfc/reference/cinternetsession-class.md#openurl)에 의해 성공적으로 만들어진 개체에 대 한 호출이 성공한 후에만이 멤버 함수를 사용 합니다.

## <a name="chttpfilegetobject"></a><a name="getobject"></a> CHttpFile:: GetObject

이 멤버 함수를 호출 하 여이와 연결 된 개체의 이름을 가져옵니다 `CHttpFile` .

```
CString GetObject() const;
```

### <a name="return-value"></a>반환 값

개체의 이름을 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체입니다.

### <a name="remarks"></a>설명

[Sendrequest가](#sendrequest) 또는 `CHttpFile` [openurl](../../mfc/reference/cinternetsession-class.md#openurl)에 의해 성공적으로 만들어진 개체에 대 한 호출이 성공한 후에만이 멤버 함수를 사용 합니다.

## <a name="chttpfilegetverb"></a><a name="getverb"></a> CHttpFile:: GetVerb

이 멤버 함수를 호출 하 여이와 연결 된 HTTP 동사 (또는 메서드)를 가져옵니다 `CHttpFile` .

```
CString GetVerb() const;
```

### <a name="return-value"></a>반환 값

HTTP 동사 (또는 메서드)의 이름을 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체입니다.

### <a name="remarks"></a>설명

[Sendrequest가](#sendrequest) 또는 `CHttpFile` [openurl](../../mfc/reference/cinternetsession-class.md#openurl)에 의해 성공적으로 만들어진 개체에 대 한 호출이 성공한 후에만이 멤버 함수를 사용 합니다.

## <a name="chttpfilequeryinfo"></a><a name="queryinfo"></a> CHttpFile:: QueryInfo

HTTP 요청에서 응답 또는 요청 헤더를 반환 하려면이 멤버 함수를 호출 합니다.

```
BOOL QueryInfo(
    DWORD dwInfoLevel,
    LPVOID lpvBuffer,
    LPDWORD lpdwBufferLength,
    LPDWORD lpdwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    CString& str,
    LPDWORD dwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    SYSTEMTIME* pSysTime,
    LPDWORD dwIndex = NULL) const;
```

### <a name="parameters"></a>매개 변수

*dwInfoLevel*<br/>
쿼리할 특성 및 요청 된 정보 유형을 지정 하는 다음 플래그의 조합입니다.

- HTTP_QUERY_CUSTOM 헤더 이름을 찾고 출력의 *Lpvbuffer* 에서이 값을 반환 합니다. 헤더가 없으면 HTTP_QUERY_CUSTOM 어설션이 throw 됩니다.

- HTTP_QUERY_FLAG_REQUEST_HEADERS 일반적으로 응용 프로그램은 응답 헤더를 쿼리 하지만 응용 프로그램은이 플래그를 사용 하 여 요청 헤더를 쿼리할 수도 있습니다.

- 해당 값이 날짜/시간 문자열 (예: "마지막 수정 시간") 인 헤더에 대 한 HTTP_QUERY_FLAG_SYSTEMTIME이 플래그는 응용 프로그램이 데이터를 구문 분석 하지 않아도 되는 표준 Win32 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체로 헤더 값을 반환 합니다. 이 플래그를 사용 하는 경우 함수의 재정의를 사용 하는 것이 좋습니다 `SYSTEMTIME` .

- 값이 숫자 (예: 상태 코드) 인 헤더에 대 한 HTTP_QUERY_FLAG_NUMBER이 플래그는 데이터를 32 비트 숫자로 반환 합니다.

가능한 값 목록은 **설명** 섹션을 참조 하세요.

*lpvBuffer*<br/>
정보를 받는 버퍼에 대 한 포인터입니다.

*lpdwBufferLength*<br/>
입력 시 데이터 버퍼의 길이를 포함 하는 값을 문자 또는 바이트 수로 가리킵니다. 이 매개 변수에 대 한 자세한 내용은 **설명** 섹션을 참조 하세요.

*lpdwIndex*<br/>
0부터 시작 하는 헤더 인덱스에 대 한 포인터입니다. NULL일 수 있습니다. 이 플래그를 사용 하 여 이름이 같은 여러 헤더를 열거 합니다. 입력 시 *lpdwIndex* 는 반환할 지정 된 헤더의 인덱스를 나타냅니다. 출력에서 *lpdwIndex* 는 다음 헤더의 인덱스를 나타냅니다. 다음 인덱스를 찾을 수 없으면 ERROR_HTTP_HEADER_NOT_FOUND 반환 됩니다.

*str*<br/>
반환 된 정보를 받는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 개체에 대 한 참조입니다.

*dwIndex*<br/>
인덱스 값입니다. *LpdwIndex* 를 참조 하세요.

*pSysTime*<br/>
Win32 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

[Sendrequest가](#sendrequest) 또는 `CHttpFile` [openurl](../../mfc/reference/cinternetsession-class.md#openurl)에 의해 성공적으로 만들어진 개체에 대 한 호출이 성공한 후에만이 멤버 함수를 사용 합니다.

에서 다음 형식의 데이터를 검색할 수 있습니다 `QueryInfo` .

- 문자열 (기본값)

- `SYSTEMTIME` ("데이터:" "Expires:" 등의 경우)

- DWORD (STATUS_CODE, CONTENT_LENGTH 등)

문자열이 버퍼에 기록 되 고 멤버 함수가 성공 하면에는 `lpdwBufferLength` NULL 종결 문자에 대해 문자에서 1을 뺀 문자열의 길이가 포함 됩니다.

가능한 *dwInfoLevel* 값은 다음과 같습니다.

- HTTP_QUERY_MIME_VERSION

- HTTP_QUERY_CONTENT_TYPE

- HTTP_QUERY_CONTENT_TRANSFER_ENCODING

- HTTP_QUERY_CONTENT_ID

- HTTP_QUERY_CONTENT_DESCRIPTION

- HTTP_QUERY_CONTENT_LENGTH

- HTTP_QUERY_ALLOWED_METHODS

- HTTP_QUERY_PUBLIC_METHODS

- HTTP_QUERY_DATE

- HTTP_QUERY_EXPIRES

- HTTP_QUERY_LAST_MODIFIED

- HTTP_QUERY_MESSAGE_ID

- HTTP_QUERY_URI

- HTTP_QUERY_DERIVED_FROM

- HTTP_QUERY_LANGUAGE

- HTTP_QUERY_COST

- HTTP_QUERY_WWW_LINK

- HTTP_QUERY_PRAGMA

- HTTP_QUERY_VERSION

- HTTP_QUERY_STATUS_CODE

- HTTP_QUERY_STATUS_TEXT

- HTTP_QUERY_RAW_HEADERS

- HTTP_QUERY_RAW_HEADERS_CRLF

## <a name="chttpfilequeryinfostatuscode"></a><a name="queryinfostatuscode"></a> CHttpFile:: QueryInfoStatusCode

이 멤버 함수를 호출 하 여 HTTP 요청과 연결 된 상태 코드를 가져오고 제공 된 *Dwstatuscode* 매개 변수에 넣습니다.

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>매개 변수

*dwStatusCode*<br/>
상태 코드에 대 한 참조입니다. 상태 코드는 요청한 이벤트의 성공 또는 실패를 표시 합니다. 상태 코드에 대 한 설명은 **주의** 를 참조 하십시오.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

[Sendrequest가](#sendrequest) 또는 `CHttpFile` [openurl](../../mfc/reference/cinternetsession-class.md#openurl)에 의해 성공적으로 만들어진 개체에 대 한 호출이 성공한 후에만이 멤버 함수를 사용 합니다.

HTTP 상태 코드는 요청의 성공 또는 실패를 나타내는 그룹으로 분류 됩니다. 다음 표에서는 상태 코드 그룹 및 가장 일반적인 HTTP 상태 코드에 대해 간략하게 설명 합니다.

|그룹|의미|
|-----------|-------------|
|200-299|Success|
|300-399|정보 산업|
|400-499|요청 오류|
|500-599|서버 오류|

일반적인 HTTP 상태 코드:

|상태 코드|의미|
|-----------------|-------------|
|200|URL이 있는 경우 전송은 다음과 같습니다.|
|400|이해할 없는 요청|
|404|요청한 URL을 찾을 수 없습니다.|
|405|서버에서 요청 된 메서드를 지원 하지 않습니다.|
|500|알 수 없는 서버 오류|
|503|서버 용량 도달|

## <a name="chttpfilesendrequest"></a><a name="sendrequest"></a> CHttpFile:: Sendrequest가

이 멤버 함수를 호출 하 여 HTTP 서버에 요청을 보냅니다.

```
BOOL SendRequest(
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLen = 0,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);

BOOL SendRequest(
    CString& strHeaders,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);
```

### <a name="parameters"></a>매개 변수

*pstrHeaders*<br/>
보낼 헤더의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*dwHeadersLen*<br/>
*Pstrheaders* 로 식별 되는 헤더의 길이입니다.

*lpOptional*<br/>
요청 헤더 바로 다음에 보낼 선택적 데이터입니다. 이는 POST 및 PUT 작업에 일반적으로 사용 됩니다. 보낼 선택적 데이터가 없는 경우 NULL 일 수 있습니다.

*dwOptionalLen*<br/>
*Lpoptional* 의 길이입니다.

*strHeaders*<br/>
보내는 요청에 대 한 헤더의 이름을 포함 하는 문자열입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출이 실패 하면 throw 된 [Cinternetexception](../../mfc/reference/cinternetexception-class.md) 개체를 검사 하 여 오류의 원인을 확인 합니다.

## <a name="chttpfilesendrequestex"></a><a name="sendrequestex"></a> CHttpFile:: SendRequestEx

이 멤버 함수를 호출 하 여 HTTP 서버에 요청을 보냅니다.

```
BOOL SendRequestEx(
    DWORD dwTotalLen,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);

BOOL SendRequestEx(
    LPINTERNET_BUFFERS lpBuffIn,
    LPINTERNET_BUFFERS lpBuffOut,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>매개 변수

*dwTotalLen*<br/>
요청에서 보낼 바이트 수입니다.

*dwFlags*<br/>
작업을 설명 하는 플래그입니다. 적절 한 플래그 목록은 Windows SDK [Httpsendrequestex](/windows/win32/api/wininet/nf-wininet-httpsendrequestexw) 를 참조 하십시오.

*dwContext*<br/>
`CHttpFile` 작업에 대한 컨텍스트 식별자입니다. 이 매개 변수에 대 한 자세한 내용은 설명 부분을 참조 하십시오.

*lpBuffIn*<br/>
작업에 사용 되는 입력 버퍼를 설명 하는 초기화 된 [INTERNET_BUFFERS](/windows/win32/api/wininet/ns-wininet-internet_buffersw) 에 대 한 포인터입니다.

*lpBuffOut*<br/>
작업에 사용 되는 출력 버퍼를 설명 하는 초기화 된 INTERNET_BUFFERS에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값입니다. 호출이 실패 하면 throw 된 [Cinternetexception](../../mfc/reference/cinternetexception-class.md) 개체를 검사 하 여 오류의 원인을 확인 합니다.

### <a name="remarks"></a>설명

이 함수를 사용 하면 응용 프로그램에서의 [Write](../../mfc/reference/cinternetfile-class.md#write) 및 [writestring](../../mfc/reference/cinternetfile-class.md#writestring) 메서드를 사용 하 여 데이터를 보낼 수 있습니다 `CInternetFile` . 이 함수의 재정의를 호출 하기 전에 보낼 데이터의 길이를 알고 있어야 합니다. 첫 번째 재정의를 사용 하 여 보내려는 데이터의 길이를 지정할 수 있습니다. 두 번째 재정의는 버퍼를 자세히 설명 하는 데 사용할 수 있는 INTERNET_BUFFERS 구조체에 대 한 포인터를 허용 합니다.

콘텐츠를 파일에 쓴 후 [EndRequest](#endrequest) 를 호출 하 여 작업을 종료 합니다.

*Dwcontext* 의 기본값은 MFC에서 `CHttpFile` 개체를 만든 [cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체의 개체로 보냅니다 `CHttpFile` . [Cinternetsession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) 또는 [CHttpConnection](../../mfc/reference/chttpconnection-class.md) 를 호출 하 여 개체를 생성 하는 경우 `CHttpFile` 기본값을 재정의 하 여 컨텍스트 식별자를 선택한 값으로 설정할 수 있습니다. 컨텍스트 식별자가 식별 된 개체에 대 한 상태를 제공 하기 위해 [Cinternetsession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) 으로 반환 됩니다. 컨텍스트 식별자에 대 한 자세한 내용은 [인터넷 첫 단계: WinInet](../../mfc/wininet-basics.md) 문서를 참조 하세요.

### <a name="example"></a>예제

이 코드 조각은 LOCALHOST 서버에서 MFCISAPI.DLL 이라는 DLL로 문자열의 내용을 보냅니다. 이 예제에서는에 대 한 호출을 하나만 사용 `WriteString` 하지만 여러 호출을 사용 하 여 블록에서 데이터를 보내는 것은 허용 됩니다.

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>참고 항목

[CInternetFile 클래스](../../mfc/reference/cinternetfile-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile 클래스](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 클래스](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection 클래스](../../mfc/reference/chttpconnection-class.md)
