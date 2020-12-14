---
description: '자세한 정보: 인터넷 URL 전역 및 도우미 구문 분석'
title: 전역 및 도우미를 구문 분석 하는 인터넷 URL
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 4dca0946686759a3880c73aa425edcc724d8772d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219501"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>전역 및 도우미를 구문 분석 하는 인터넷 URL

클라이언트가 인터넷 서버에 쿼리를 보내는 경우 URL 구문 분석 globals 중 하나를 사용 하 여 클라이언트에 대 한 정보를 추출할 수 있습니다. 도우미 함수는 다른 인터넷 기능을 제공 합니다.

## <a name="internet-url-parsing-globals"></a>인터넷 URL 전역 구문 분석

|Name|설명|
|-|-|
|[AfxParseURL](#afxparseurl)|URL 문자열을 구문 분석 하 고 서비스 및 해당 구성 요소의 형식을 반환 합니다.|
|[AfxParseURLEx](#afxparseurlex)|URL 문자열을 구문 분석 하 고 사용자 이름과 암호를 제공 하는 것은 물론 서비스 및 해당 구성 요소의 형식을 반환 합니다.|

## <a name="other-internet-helpers"></a>기타 인터넷 도우미

|Name|설명|
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|인터넷 연결과 관련 된 예외를 throw 합니다.|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|인터넷 핸들의 유형을 결정 합니다.|

## <a name="afxparseurl"></a><a name="afxparseurl"></a> AfxParseURL

이 전역은 [Cinternetsession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)에 사용 됩니다.

```
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort);
```

### <a name="parameters"></a>매개 변수

*pstrURL*<br/>
구문 분석할 URL이 포함 된 문자열에 대 한 포인터입니다.

*dwServiceType*<br/>
인터넷 서비스의 유형을 나타냅니다. 가능한 값은 다음과 같습니다.

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
서비스 유형 뒤에 나오는 URL의 첫 번째 세그먼트입니다.

*strObject*<br/>
URL이 참조 하는 개체입니다 (비어 있을 수 있음).

*nPort*<br/>
URL의 서버 또는 개체 부분 (있는 경우) 중 하나에서 결정 됩니다.

### <a name="return-value"></a>반환 값

URL이 성공적으로 구문 분석 되 면 0이 아닌 값입니다. 그렇지 않고 비어 있거나 알려진 인터넷 서비스 유형을 포함 하지 않는 경우 0입니다.

### <a name="remarks"></a>설명

URL 문자열을 구문 분석 하 고 서비스 및 해당 구성 요소의 형식을 반환 합니다.

예를 들어, `AfxParseURL` *Service://server/dir/dir/object.ext:port* 형식의 url을 구문 분석 하 고 다음과 같이 저장 된 해당 구성 요소를 반환 합니다.

*Strserver* = = "server"

*strObject* = = "/sv/sv/p\object\object.ext"

*Nport* = = #port

*Dwservicetype* = = #service

> [!NOTE]
> 이 함수를 호출 하려면 프로젝트에 AFXINET.H를 포함 해야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxinet.h

## <a name="afxparseurlex"></a><a name="afxparseurlex"></a> AfxParseURLEx

이 전역 함수는 [AfxParseURL](#afxparseurl) 의 확장 버전으로, [cinternetsession:: openurl](../../mfc/reference/cinternetsession-class.md#openurl)에 사용 됩니다.

```
BOOL AFXAPI AfxParseURLEx(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort,
    CString& strUsername,
    CString& strPassword,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>매개 변수

*pstrURL*<br/>
구문 분석할 URL이 포함 된 문자열에 대 한 포인터입니다.

*dwServiceType*<br/>
인터넷 서비스의 유형을 나타냅니다. 가능한 값은 다음과 같습니다.

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
서비스 유형 뒤에 나오는 URL의 첫 번째 세그먼트입니다.

*strObject*<br/>
URL이 참조 하는 개체입니다 (비어 있을 수 있음).

*nPort*<br/>
URL의 서버 또는 개체 부분 (있는 경우) 중 하나에서 결정 됩니다.

*strUsername*<br/>
사용자의 이름을 포함 하는 개체에 대 한 참조 `CString` 입니다.

*strPassword*<br/>
사용자의 암호를 포함 하는 개체에 대 한 참조 `CString` 입니다.

*dwFlags*<br/>
URL을 구문 분석 하는 방법을 제어 하는 플래그입니다. 은 다음 값을 조합 하 여 사용할 수 있습니다.

|값|의미|
|-----------|-------------|
|ICU_DECODE|% XX 이스케이프 시퀀스를 문자로 변환 합니다.|
|ICU_NO_ENCODE|안전 하지 않은 문자를 이스케이프 시퀀스로 변환 하지 마십시오.|
|ICU_NO_META|메타 시퀀스 (예: "\.")를 제거 하지 마십시오. "\..") URL에서.|
|ICU_ENCODE_SPACES_ONLY|공백만 인코딩합니다.|
|ICU_BROWSER_MODE|' # ' 또는 ' ' 뒤에 문자를 인코딩하거나 디코드 하지 말고 ' ' 뒤에 후행 공백을 제거 하지 마십시오. 이 값을 지정 하지 않으면 전체 URL이 인코딩되고 후행 공백이 제거 됩니다.|

플래그가 없는 MFC 기본값을 사용 하는 경우 함수는 안전 하지 않은 모든 문자 및 meta 시퀀스 (예: \\ ., \ ... 및 \\ ...)를 이스케이프 시퀀스로 변환 합니다.

### <a name="return-value"></a>반환 값

URL이 성공적으로 구문 분석 되 면 0이 아닌 값입니다. 그렇지 않고 비어 있거나 알려진 인터넷 서비스 유형을 포함 하지 않는 경우 0입니다.

### <a name="remarks"></a>설명

URL 문자열을 구문 분석 하 고 서비스 및 해당 구성 요소의 유형과 사용자의 이름과 암호를 제공 합니다. 플래그는 안전 하지 않은 문자를 처리 하는 방법을 표시 합니다.

> [!NOTE]
> 이 함수를 호출 하려면 프로젝트에 AFXINET.H를 포함 해야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxinet.h

## <a name="afxgetinternethandletype"></a><a name="afxgetinternethandletype"></a> AfxGetInternetHandleType

이 전역 함수를 사용 하 여 인터넷 핸들의 형식을 확인 합니다.

### <a name="syntax"></a>구문

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>매개 변수

*hQuery*<br/>
인터넷 쿼리에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

WININET에서 정의한 인터넷 서비스 유형입니다. 이러한 인터넷 서비스 목록은 설명 섹션을 참조 하세요. 핸들이 NULL 이거나 인식 되지 않는 경우 함수는 AFX_INET_SERVICE_UNK을 반환 합니다.

### <a name="remarks"></a>설명

다음 목록에는에서 반환 될 수 있는 인터넷 유형이 나와 있습니다 `AfxGetInternetHandleType` .

- INTERNET_HANDLE_TYPE_INTERNET

- INTERNET_HANDLE_TYPE_CONNECT_FTP

- INTERNET_HANDLE_TYPE_CONNECT_GOPHER

- INTERNET_HANDLE_TYPE_CONNECT_HTTP

- INTERNET_HANDLE_TYPE_FTP_FIND

- INTERNET_HANDLE_TYPE_FTP_FIND_HTML

- INTERNET_HANDLE_TYPE_FTP_FILE

- INTERNET_HANDLE_TYPE_FTP_FILE_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FIND

- INTERNET_HANDLE_TYPE_GOPHER_FIND_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FILE

- INTERNET_HANDLE_TYPE_GOPHER_FILE_HTML

- INTERNET_HANDLE_TYPE_HTTP_REQUEST

> [!NOTE]
> 이 함수를 호출 하려면 프로젝트에 AFXINET.H를 포함 해야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxinet.h

## <a name="afxthrowinternetexception"></a><a name="afxthrowinternetexception"></a> AfxThrowInternetException

인터넷 예외를 throw 합니다.

### <a name="syntax"></a>구문

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>매개 변수

*dwContext*<br/>
오류를 발생 시킨 작업에 대 한 컨텍스트 식별자입니다. *Dwcontext* 의 기본값은 원래 [cinternetsession](cinternetsession-class.md) 에 지정 되 고 [Cinternetsession](cinternetconnection-class.md)및 [cinternetsession](cinternetfile-class.md)파생 클래스로 전달 됩니다. 연결 또는 파일에서 수행 되는 특정 작업의 경우 일반적으로 기본 *Dwcontext* 를 사용 하 여 기본값을 재정의 합니다. 그러면이 값이 [Cinternetsession:: OnStatusCallback](cinternetsession-class.md#onstatuscallback) 으로 반환 되어 특정 작업의 상태를 식별 합니다.

*dwError*<br/>
예외를 일으킨 오류입니다.

### <a name="remarks"></a>설명

운영 체제 오류 코드를 기반으로 원인을 결정 해야 합니다.

> [!NOTE]
> 이 함수를 호출 하려면 프로젝트에 AFXINET.H를 포함 해야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxinet.h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](mfc-macros-and-globals.md)<br/>
[CInternetException 클래스](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
