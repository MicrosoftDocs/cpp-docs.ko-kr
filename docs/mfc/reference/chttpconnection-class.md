---
description: '자세히 알아보기: CHttpConnection 클래스'
title: CHttpConnection 클래스
ms.date: 03/27/2019
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
ms.openlocfilehash: 19a99f0f4eb6844d60a6e42a079214e1c70628fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143652"
---
# <a name="chttpconnection-class"></a>CHttpConnection 클래스

HTTP 서버와의 연결을 관리합니다.

## <a name="syntax"></a>구문

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CHttpConnection:: CHttpConnection](#chttpconnection)|`CHttpConnection` 개체를 만듭니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CHttpConnection::OpenRequest](#openrequest)|HTTP 요청을 엽니다.|

## <a name="remarks"></a>설명

HTTP는 MFC WinInet 클래스에서 구현 하는 세 가지 인터넷 서버 프로토콜 중 하나입니다.

클래스에는 `CHttpConnection` HTTP 프로토콜을 사용 하 여 서버에 대 한 연결을 관리 하는 생성자 및 [openrequest](#openrequest)멤버 함수가 포함 되어 있습니다.

HTTP 서버와 통신 하려면 먼저 [Cinternetsession](../../mfc/reference/cinternetsession-class.md)의 인스턴스를 만든 다음 [CHttpConnection](#chttpconnection) 개체를 만들어야 합니다. 개체를 직접 만들지는 않습니다. 대신 개체를 `CHttpConnection` 만들고 해당 개체에 대 한 포인터를 반환 하는 [Cinternetsession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)를 호출 `CHttpConnection` 합니다.

에서 다른 MFC 인터넷 클래스로 작업 하는 방법에 대 한 자세한 내용은 `CHttpConnection` WinInet을 [사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md)문서를 참조 하세요. 다른 두 가지 지원 되는 인터넷 프로토콜인 gopher와 FTP를 사용 하 여 서버에 연결 하는 방법에 대 한 자세한 내용은 [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) 및 [cftpconnection](../../mfc/reference/cftpconnection-class.md)클래스를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>요구 사항

**헤더:** afxinet.h

## <a name="chttpconnectionchttpconnection"></a><a name="chttpconnection"></a> CHttpConnection:: CHttpConnection

이 멤버 함수를 호출 하 여 개체를 생성 `CHttpConnection` 합니다.

```
CHttpConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>매개 변수

*pSession*<br/>
[Cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체에 대 한 포인터입니다.

*hConnected*<br/>
인터넷 연결에 대 한 핸들입니다.

*pstrServer*<br/>
서버 이름을 포함 하는 문자열에 대 한 포인터입니다.

*dwContext*<br/>
개체에 대 한 컨텍스트 식별자 `CInternetConnection` 입니다. *Dwcontext* 에 대 한 자세한 내용은 **설명** 부분을 참조 하세요.

*nPort*<br/>
이 연결에 대 한 인터넷 포트를 식별 하는 번호입니다.

*pstrUserName*<br/>
로그인 할 사용자의 이름을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. NULL 인 경우 기본값은 anonymous입니다.

*pstrPassword*<br/>
로그인 하는 데 사용할 암호를 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. *Pstrpassword* 와 *pstrpassword* 이 모두 NULL 인 경우 기본 익명 암호는 사용자의 전자 메일 이름입니다. *Pstrpassword* 가 null 또는 빈 문자열이 고 *PSTRPASSWORD* 이 null이 아닌 경우 빈 암호가 사용 됩니다. 다음 표에서는 *Pstrusername* 및 *pstrusername* 의 네 가지 가능한 설정에 대 한 동작을 설명 합니다.

|*pstrUserName*|*pstrPassword*|FTP 서버에 전송 되는 사용자 이름|FTP 서버로 보낸 암호|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL 또는 ""|NULL 또는 ""|"anonymous"|사용자의 전자 메일 이름|
|NULL이 아닌 문자열|NULL 또는 ""|*pstrUserName*|" "|
|NULL |NULL이 아닌 문자열|오류|오류|
|NULL이 아닌 문자열|NULL이 아닌 문자열|*pstrUserName*|*pstrPassword*|

*dwFlags*<br/>
플래그의 조합 `INTERNET_FLAG_*` 입니다. *DwFlags* 값에 대 한 설명은 [CHttpConnection:: openrequest](#openrequest) 의 **설명 섹션에 있는 표** 를 참조 하세요.

### <a name="remarks"></a>설명

을 직접 만들지는 않습니다 `CHttpConnection` . 대신 [Cinternetsession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)를 호출 하 여 개체를 만듭니다.

## <a name="chttpconnectionopenrequest"></a><a name="openrequest"></a> CHttpConnection:: OpenRequest

HTTP 연결을 열려면 이 멤버 함수를 호출합니다.

```
CHttpFile* OpenRequest(
    LPCTSTR pstrVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);

CHttpFile* OpenRequest(
    int nVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);
```

### <a name="parameters"></a>매개 변수

*pstrVerb*<br/>
요청에 사용할 동사를 포함하는 문자열에 대한 포인터입니다. NULL 인 경우 "GET"이 사용 됩니다.

*pstrObjectName*<br/>
지정된 동사의 대상 개체를 포함하는 문자열에 대한 포인터입니다. 이 문자열은 일반적으로 파일 이름, 실행 모듈 또는 검색 지정자입니다.

*pstrReferer*<br/>
요청에서 URL (*pstrObjectName*)을 가져온 문서의 주소 (url)를 지정 하는 문자열에 대 한 포인터입니다. NULL 인 경우 HTTP 헤더가 지정 되지 않습니다.

*dwContext*<br/>
`OpenRequest` 작업에 대한 컨텍스트 식별자입니다. *Dwcontext* 에 대 한 자세한 내용은 설명 부분을 참조 하세요.

*ppstrAcceptTypes*<br/>
클라이언트에서 허용 하는 콘텐츠 형식을 나타내는 문자열에 대 한 LPCTSTR 포인터의 null로 끝나는 배열에 대 한 포인터입니다. *Ppstraccepttypes* 가 NULL 인 경우 서버는 클라이언트가 "text/*" 유형의 문서만 허용 하는 것으로 해석 합니다. 즉, 텍스트 문서만, 그림 또는 기타 이진 파일이 아닙니다. 콘텐츠 형식 첨부 HTTP POST 및 PUT 등 첨부된 정보가 있는 쿼리에 대한 데이터의 형식을 식별하는 CGI 변수 CONTENT_TYPE과 같습니다.

*pstrVersion*<br/>
HTTP 버전을 정의하는 문자열에 대한 포인터입니다. NULL 인 경우 "HTTP/1.0"이 사용 됩니다.

*dwFlags*<br/>
INTERNET_ * FLAG_ 플래그의 조합입니다. 가능한 *dwFlags* 값에 대 한 설명은 설명 섹션을 참조 하세요.

*nVerb*<br/>
HTTP 요청 형식과 관련된 숫자입니다. 다음 중 하나일 수 있습니다.

|HTTP 요청 형식|*Nverb* 값|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>반환 값

요청 된 [CHttpFile](../../mfc/reference/chttpfile-class.md) 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

*dwFlags* 은 다음 중 하나일 수 있습니다.

|인터넷 플래그|설명|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|캐시가 아니라 원본 서버에서 요청한 파일, 개체 또는 디렉터리 목록을 다운로드합니다.|
|INTERNET_FLAG_DONT_CACHE|반환 된 엔터티를 캐시에 추가 하지 않습니다.|
|INTERNET_FLAG_MAKE_PERSISTENT|반환된 엔터티를 영구 엔터티로 캐시에 추가합니다. 즉, 표준 캐시 정리, 일관성 검사 또는 가비지 수집에서이 항목을 캐시에서 제거할 수 없습니다.|
|INTERNET_FLAG_SECURE|보안 트랜잭션 의미 체계를 사용합니다. SSL/PCT를 사용 하 여로 변환 되며 HTTP 요청 에서만 의미가 있습니다.|
|INTERNET_FLAG_NO_AUTO_REDIRECT|HTTP와만 사용 되며, [CHttpFile:: sendrequest가](../../mfc/reference/chttpfile-class.md#sendrequest)에서 리디렉션이 자동으로 처리 되지 않도록 지정 합니다.|

`dwContext` 기본값을 재정의하여 컨텍스트 식별자를 설정한 값으로 설정합니다. 컨텍스트 식별자는 `CHttpConnection` 해당 [Cinternetsession](../../mfc/reference/cinternetsession-class.md) 개체에서 만든 개체의이 특정 작업과 연결 됩니다. 값은 [Cinternetsession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) 으로 반환 되어 식별 된 작업에 대 한 상태를 제공 합니다. 컨텍스트 식별자에 대 한 자세한 내용은 [인터넷 첫 단계: WinInet](../../mfc/wininet-basics.md) 문서를 참조 하세요.

이 함수를 사용할 경우 예외가 throw될 수 있습니다.

## <a name="see-also"></a>참고 항목

[CInternetConnection 클래스](../../mfc/reference/cinternetconnection-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 클래스](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile 클래스](../../mfc/reference/chttpfile-class.md)
