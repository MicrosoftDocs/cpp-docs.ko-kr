---
description: '자세한 정보: 말아 클래스'
title: 말아 클래스
ms.date: 05/06/2019
f1_keywords:
- CUrl
- ATLUTIL/ATL::CUrl
- ATLUTIL/ATL::CUrl::CUrl
- ATLUTIL/ATL::CUrl::Canonicalize
- ATLUTIL/ATL::CUrl::Clear
- ATLUTIL/ATL::CUrl::CrackUrl
- ATLUTIL/ATL::CUrl::CreateUrl
- ATLUTIL/ATL::CUrl::GetExtraInfo
- ATLUTIL/ATL::CUrl::GetExtraInfoLength
- ATLUTIL/ATL::CUrl::GetHostName
- ATLUTIL/ATL::CUrl::GetHostNameLength
- ATLUTIL/ATL::CUrl::GetPassword
- ATLUTIL/ATL::CUrl::GetPasswordLength
- ATLUTIL/ATL::CUrl::GetPortNumber
- ATLUTIL/ATL::CUrl::GetScheme
- ATLUTIL/ATL::CUrl::GetSchemeName
- ATLUTIL/ATL::CUrl::GetSchemeNameLength
- ATLUTIL/ATL::CUrl::GetUrlLength
- ATLUTIL/ATL::CUrl::GetUrlPath
- ATLUTIL/ATL::CUrl::GetUrlPathLength
- ATLUTIL/ATL::CUrl::GetUserName
- ATLUTIL/ATL::CUrl::GetUserNameLength
- ATLUTIL/ATL::CUrl::SetExtraInfo
- ATLUTIL/ATL::CUrl::SetHostName
- ATLUTIL/ATL::CUrl::SetPassword
- ATLUTIL/ATL::CUrl::SetPortNumber
- ATLUTIL/ATL::CUrl::SetScheme
- ATLUTIL/ATL::CUrl::SetSchemeName
- ATLUTIL/ATL::CUrl::SetUrlPath
- ATLUTIL/ATL::CUrl::SetUserName
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
ms.openlocfilehash: e8453c4dd1abbfdcb6d794b89fd55f37d7b3f286
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140298"
---
# <a name="curl-class"></a>말아 클래스

이 클래스는 URL을 나타냅니다. 이를 통해 기존 URL 문자열을 구문 분석 하거나 처음부터 문자열을 작성 하 든 관계 없이 URL의 각 요소를 개별적으로 조작할 수 있습니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CUrl
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[말아 넘기기:: 말아](#curl)|생성자입니다.|
|[말아:: ~ 말아](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[말아 넘기기:: 정식화](#canonicalize)|URL 문자열을 정규 형식으로 변환 하려면이 메서드를 호출 합니다.|
|[말아 넘기기:: Clear](#clear)|모든 URL 필드를 지우려면이 메서드를 호출 합니다.|
|[말아 넘기기:: CrackUrl](#crackurl)|URL을 디코딩하고 구문 분석 하려면이 메서드를 호출 합니다.|
|[말아 넘기기:: CreateUrl](#createurl)|URL을 만들려면이 메서드를 호출 합니다.|
|[말아 넘기기:: GetExtraInfo](#getextrainfo)|URL에서 *텍스트 또는 텍스트* 와 같은 추가 정보를 가져오려면이 메서드 를 호출 합니다.|
|[말아 넘기기:: GetExtraInfoLength](#getextrainfolength)|URL에서 검색할 추가 정보 (예: *텍스트* 또는 # *텍스트*)의 길이를 가져오려면이 메서드를 호출 합니다.|
|[말아 넘기기:: GetHostName](#gethostname)|URL에서 호스트 이름을 가져오려면이 메서드를 호출 합니다.|
|[말아 넘기기:: GetHostNameLength](#gethostnamelength)|호스트 이름의 길이를 가져오려면이 메서드를 호출 합니다.|
|[말아:: GetPassword](#getpassword)|URL에서 암호를 가져오려면이 메서드를 호출 합니다.|
|[말아:: GetPasswordLength](#getpasswordlength)|암호 길이를 가져오려면이 메서드를 호출 합니다.|
|[말아 넘기기:: GetPortNumber](#getportnumber)|ATL_URL_PORT의 측면에서 포트 번호를 가져오려면이 메서드를 호출 합니다.|
|[말아 넘기기:: GetScheme](#getscheme)|URL 스키마를 가져오려면이 메서드를 호출 합니다.|
|[말아 넘기기:: GetSchemeName](#getschemename)|URL 체계 이름을 가져오려면이 메서드를 호출 합니다.|
|[말아 넘기기:: GetSchemeNameLength](#getschemenamelength)|URL 체계 이름의 길이를 가져오려면이 메서드를 호출 합니다.|
|[말아 넘기기:: GetUrlLength](#geturllength)|URL 길이를 가져오려면이 메서드를 호출 합니다.|
|[말아 넘기기:: GetUrlPath](#geturlpath)|URL 경로를 가져오려면이 메서드를 호출 합니다.|
|[말아 넘기기:: GetUrlPathLength](#geturlpathlength)|URL 경로 길이를 가져오려면이 메서드를 호출 합니다.|
|[말아 넘기기:: GetUserName](#getusername)|URL에서 사용자 이름을 가져오려면이 메서드를 호출 합니다.|
|[말아 넘기기:: GetUserNameLength](#getusernamelength)|사용자 이름의 길이를 가져오려면이 메서드를 호출 합니다.|
|[말아 넘기기:: SetExtraInfo](#setextrainfo)|URL의 추가 정보 (예: *텍스트 또는 텍스트* *)를* 설정 하려면이 메서드를 호출 합니다.|
|[말아 넘기기:: SetHostName](#sethostname)|호스트 이름을 설정 하려면이 메서드를 호출 합니다.|
|[말아 넘기기:: SetPassword](#setpassword)|암호를 설정 하려면이 메서드를 호출 합니다.|
|[말아 넘기기:: SetPortNumber](#setportnumber)|ATL_URL_PORT의 측면에서 포트 번호를 설정 하려면이 메서드를 호출 합니다.|
|[말아 넘기기:: SetScheme](#setscheme)|URL 체계를 설정 하려면이 메서드를 호출 합니다.|
|[말아 넘기기:: SetSchemeName](#setschemename)|URL 체계 이름을 설정 하려면이 메서드를 호출 합니다.|
|[말아 넘기기:: SetUrlPath](#seturlpath)|URL 경로를 설정 하려면이 메서드를 호출 합니다.|
|[말아 넘기기:: SetUserName](#setusername)|사용자 이름을 설정 하려면이 메서드를 호출 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[말아 넘기기:: operator =](#operator_eq)|지정 된 `CUrl` 개체를 현재 개체에 할당 합니다 `CUrl` .|

## <a name="remarks"></a>설명

`CUrl` 경로 또는 포트 번호와 같은 URL의 필드를 조작할 수 있습니다. `CUrl` 는 다음과 같은 형식의 Url을 인식 합니다.

\<Scheme>://\<UserName>:\<Password>\@\<HostName>:\<PortNumber>/\<UrlPath>\<ExtraInfo>

일부 필드는 선택 사항입니다. 예를 들어 다음 URL을 살펴보세요.

`http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents`

[말아 넘기기:: CrackUrl](#crackurl) 는 다음과 같이 구문 분석 합니다.

- 구성표: "http" 또는 [ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)

- 사용자 이름: "사용자"

- 암호: "비밀"

- 호스트 이름: " `www.microsoft.com` "

- PortNumber: 80

- UrlPath: "visualc/stuff.htm"

- ExtraInfo: "#contents"

UrlPath 필드를 조작 하려면 (예를 들어) [Geturlpath](#geturlpath), [GetUrlPathLength](#geturlpathlength)및 [seturlpath](#seturlpath)를 사용 합니다. [Createurl](#createurl) 을 사용 하 여 전체 url 문자열을 만듭니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="curlcanonicalize"></a><a name="canonicalize"></a> 말아 넘기기:: 정식화

URL 문자열을 정규 형식으로 변환 하려면이 메서드를 호출 합니다.

```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>매개 변수

*dwFlags*<br/>
정형화를 제어 하는 플래그입니다. 플래그가 지정 되지 않은 경우 (*dwFlags* = 0) 메서드는 안전 하지 않은 모든 문자 및 meta 시퀀스 (예: \\ ., \ ... 및 \\ ...)를 이스케이프 시퀀스로 변환 합니다. *dwFlags* 은 다음 값 중 하나일 수 있습니다.

- ATL_URL_BROWSER_MODE: "#" 또는 "" 뒤에 문자를 인코딩하거나 디코드 하지 않고 "" 뒤에 후행 공백을 제거 하지 않습니다. 이 값을 지정 하지 않으면 전체 URL이 인코딩되고 후행 공백이 제거 됩니다.

- ATL_URL _DECODE: URL을 구문 분석 하기 전에 모든% XX 시퀀스를 이스케이프 시퀀스를 포함 하는 문자로 변환 합니다.

- ATL_URL _ENCODE_PERCENT: 발생 한% 기호를 인코딩합니다. 기본적으로 백분율 기호는 인코딩되지 않습니다.

- ATL_URL _ENCODE_SPACES_ONLY: 공백만 인코딩합니다.

- ATL_URL _NO_ENCODE: 안전 하지 않은 문자를 이스케이프 시퀀스로 변환 하지 않습니다.

- ATL_URL _NO_META: URL에서 메타 시퀀스 (예: "." 및 ".")를 제거 하지 않습니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

정규 형식으로 변환 하려면 안전 하지 않은 문자 및 공백을 이스케이프 시퀀스로 변환 해야 합니다.

## <a name="curlclear"></a><a name="clear"></a> 말아 넘기기:: Clear

모든 URL 필드를 지우려면이 메서드를 호출 합니다.

```
inline void Clear() throw();
```

## <a name="curlcrackurl"></a><a name="crackurl"></a> 말아 넘기기:: CrackUrl

URL을 디코딩하고 구문 분석 하려면이 메서드를 호출 합니다.

```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>매개 변수

*lpszUrl*<br/>
URL입니다.

*dwFlags*<br/>
구문 분석 후 *lpszUrl* 의 모든 이스케이프 문자를 실제 값으로 변환 하려면 ATL_URL_DECODE 또는 ATL_URL_ESCAPE를 지정 합니다. Visual C++ 2005 이전에는 구문 분석 전에 모든 이스케이프 문자를 변환 ATL_URL_DECODE.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="curlcreateurl"></a><a name="createurl"></a> 말아 넘기기:: CreateUrl

이 메서드는 말아 개체의 구성 요소 필드에서 URL 문자열을 생성 합니다.

```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```

### <a name="parameters"></a>매개 변수

*lpszUrl*<br/>
전체 URL 문자열을 보유할 문자열 버퍼입니다.

*pdwMaxLength*<br/>
*LpszUrl* 문자열 버퍼의 최대 길이입니다.

*dwFlags*<br/>
*LpszUrl* 의 모든 이스케이프 문자를 실제 값으로 변환 하려면 ATL_URL_ESCAPE를 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 다음 형식을 사용 하 여 전체 URL 문자열을 생성 하기 위해 개별 필드를 추가 합니다.

**\<scheme>://\<user>:\<pass>\@\<domain>:\<port>\<path>\<extra>**

이 메서드를 호출할 때 *Pdwmaxlength* 매개 변수는 처음에 *lpszUrl* 매개 변수가 참조 하는 문자열 버퍼의 최대 길이를 포함 해야 합니다. *Pdwmaxlength* 매개 변수의 값은 URL 문자열의 실제 길이를 사용 하 여 업데이트 됩니다.

### <a name="example"></a>예제

이 샘플에서는 말아 넘기기 개체를 만들고 해당 URL 문자열을 검색 하는 방법을 보여 줍니다.

[!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]

## <a name="curlcurl"></a><a name="curl"></a> 말아 넘기기:: 말아

생성자입니다.

```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```

### <a name="parameters"></a>매개 변수

*url*<br/>
`CUrl`URL을 만들기 위해 복사할 개체입니다.

## <a name="curlcurl"></a><a name="dtor"></a> 말아:: ~ 말아

소멸자입니다.

```
~CUrl() throw();
```

## <a name="curlgetextrainfo"></a><a name="getextrainfo"></a> 말아 넘기기:: GetExtraInfo

URL에서 *텍스트 또는 텍스트* 와 같은 추가 정보를 가져오려면이 메서드 를 호출 합니다.

```
inline LPCTSTR GetExtraInfo() const throw();
```

### <a name="return-value"></a>반환 값

추가 정보를 포함 하는 문자열을 반환 합니다.

## <a name="curlgetextrainfolength"></a><a name="getextrainfolength"></a> 말아 넘기기:: GetExtraInfoLength

URL에서 검색할 추가 정보 (예: *텍스트* 또는 # *텍스트*)의 길이를 가져오려면이 메서드를 호출 합니다.

```
inline DWORD GetExtraInfoLength() const throw();
```

### <a name="return-value"></a>반환 값

추가 정보를 포함 하는 문자열의 길이를 반환 합니다.

## <a name="curlgethostname"></a><a name="gethostname"></a> 말아 넘기기:: GetHostName

URL에서 호스트 이름을 가져오려면이 메서드를 호출 합니다.

```
inline LPCTSTR GetHostName() const throw();
```

### <a name="return-value"></a>반환 값

호스트 이름을 반환 합니다.

## <a name="curlgethostnamelength"></a><a name="gethostnamelength"></a> 말아 넘기기:: GetHostNameLength

호스트 이름의 길이를 가져오려면이 메서드를 호출 합니다.

```
inline DWORD GetHostNameLength() const throw();
```

### <a name="return-value"></a>반환 값

호스트 이름 길이를 반환 합니다.

## <a name="curlgetpassword"></a><a name="getpassword"></a> 말아:: GetPassword

URL에서 암호를 가져오려면이 메서드를 호출 합니다.

```
inline LPCTSTR GetPassword() const throw();
```

### <a name="return-value"></a>반환 값

암호를 반환 합니다.

## <a name="curlgetpasswordlength"></a><a name="getpasswordlength"></a> 말아:: GetPasswordLength

암호 길이를 가져오려면이 메서드를 호출 합니다.

```
inline DWORD GetPasswordLength() const throw();
```

### <a name="return-value"></a>반환 값

암호 길이를 반환 합니다.

## <a name="curlgetportnumber"></a><a name="getportnumber"></a> 말아 넘기기:: GetPortNumber

포트 번호를 가져오려면이 메서드를 호출 합니다.

```
inline ATL_URL_PORT GetPortNumber() const throw();
```

### <a name="return-value"></a>반환 값

포트 번호를 반환 합니다.

## <a name="curlgetscheme"></a><a name="getscheme"></a> 말아 넘기기:: GetScheme

URL 스키마를 가져오려면이 메서드를 호출 합니다.

```
inline ATL_URL_SCHEME GetScheme() const throw();
```

### <a name="return-value"></a>반환 값

URL의 체계를 설명 하는 [ATL_URL_SCHEME](atl-url-scheme-enum.md) 값을 반환 합니다.

## <a name="curlgetschemename"></a><a name="getschemename"></a> 말아 넘기기:: GetSchemeName

URL 체계 이름을 가져오려면이 메서드를 호출 합니다.

```
inline LPCTSTR GetSchemeName() const throw();
```

### <a name="return-value"></a>반환 값

URL 체계 이름 (예: "http" 또는 "ftp")을 반환 합니다.

## <a name="curlgetschemenamelength"></a><a name="getschemenamelength"></a> 말아 넘기기:: GetSchemeNameLength

URL 체계 이름의 길이를 가져오려면이 메서드를 호출 합니다.

```
inline DWORD GetSchemeNameLength() const throw();
```

### <a name="return-value"></a>반환 값

URL 스키마 이름 길이를 반환 합니다.

## <a name="curlgeturllength"></a><a name="geturllength"></a> 말아 넘기기:: GetUrlLength

URL 길이를 가져오려면이 메서드를 호출 합니다.

```
inline DWORD GetUrlLength() const throw();
```

### <a name="return-value"></a>반환 값

URL 길이를 반환 합니다.

## <a name="curlgeturlpath"></a><a name="geturlpath"></a> 말아 넘기기:: GetUrlPath

URL 경로를 가져오려면이 메서드를 호출 합니다.

```
inline LPCTSTR GetUrlPath() const throw();
```

### <a name="return-value"></a>반환 값

URL 경로를 반환 합니다.

## <a name="curlgeturlpathlength"></a><a name="geturlpathlength"></a> 말아 넘기기:: GetUrlPathLength

URL 경로 길이를 가져오려면이 메서드를 호출 합니다.

```
inline DWORD GetUrlPathLength() const throw();
```

### <a name="return-value"></a>반환 값

URL 경로 길이를 반환 합니다.

## <a name="curlgetusername"></a><a name="getusername"></a> 말아 넘기기:: GetUserName

URL에서 사용자 이름을 가져오려면이 메서드를 호출 합니다.

```
inline LPCTSTR GetUserName() const throw();
```

### <a name="return-value"></a>반환 값

사용자 이름을 반환 합니다.

## <a name="curlgetusernamelength"></a><a name="getusernamelength"></a> 말아 넘기기:: GetUserNameLength

사용자 이름의 길이를 가져오려면이 메서드를 호출 합니다.

```
inline DWORD GetUserNameLength() const throw();
```

### <a name="return-value"></a>반환 값

사용자 이름 길이를 반환 합니다.

## <a name="curloperator-"></a><a name="operator_eq"></a> 말아 넘기기:: operator =

지정 된 `CUrl` 개체를 현재 개체에 할당 합니다 `CUrl` .

```
CUrl& operator= (const CUrl& urlThat) throw();
```

### <a name="parameters"></a>매개 변수

*url*<br/>
`CUrl`현재 개체로 복사할 개체입니다.

### <a name="return-value"></a>반환 값

현재 개체에 대 한 참조를 반환 합니다.

## <a name="curlsetextrainfo"></a><a name="setextrainfo"></a> 말아 넘기기:: SetExtraInfo

URL의 추가 정보 (예: *텍스트 또는 텍스트* *)를* 설정 하려면이 메서드를 호출 합니다.

```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```

### <a name="parameters"></a>매개 변수

*lpszInfo*<br/>
URL에 포함할 추가 정보를 포함 하는 문자열입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="curlsethostname"></a><a name="sethostname"></a> 말아 넘기기:: SetHostName

호스트 이름을 설정 하려면이 메서드를 호출 합니다.

```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```

### <a name="parameters"></a>매개 변수

*lpszHost*<br/>
호스트 이름입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="curlsetpassword"></a><a name="setpassword"></a> 말아 넘기기:: SetPassword

암호를 설정 하려면이 메서드를 호출 합니다.

```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```

### <a name="parameters"></a>매개 변수

*lpszPass*<br/>
암호입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="curlsetportnumber"></a><a name="setportnumber"></a> 말아 넘기기:: SetPortNumber

포트 번호를 설정 하려면이 메서드를 호출 합니다.

```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```

### <a name="parameters"></a>매개 변수

*nPrt*<br/>
포트 번호.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="curlsetscheme"></a><a name="setscheme"></a> 말아 넘기기:: SetScheme

URL 체계를 설정 하려면이 메서드를 호출 합니다.

```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```

### <a name="parameters"></a>매개 변수

*nScheme*<br/>
구성표에 대 한 [ATL_URL_SCHEME](atl-url-scheme-enum.md) 값 중 하나입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이름으로 체계를 설정할 수도 있습니다 ( [말아 넘기기:: SetSchemeName](#setschemename)참조).

## <a name="curlsetschemename"></a><a name="setschemename"></a> 말아 넘기기:: SetSchemeName

URL 체계 이름을 설정 하려면이 메서드를 호출 합니다.

```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```

### <a name="parameters"></a>매개 변수

*lpszSchm*<br/>
URL 스키마 이름입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

[ATL_URL_SCHEME](atl-url-scheme-enum.md) 상수를 사용 하 여 체계를 설정할 수도 있습니다 ( [말아 넘기기:: setscheme](#setscheme)참조).

## <a name="curlseturlpath"></a><a name="seturlpath"></a> 말아 넘기기:: SetUrlPath

URL 경로를 설정 하려면이 메서드를 호출 합니다.

```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```

### <a name="parameters"></a>매개 변수

*lpszPath*<br/>
URL 경로입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="curlsetusername"></a><a name="setusername"></a> 말아 넘기기:: SetUserName

사용자 이름을 설정 하려면이 메서드를 호출 합니다.

```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```

### <a name="parameters"></a>매개 변수

*lpszUser*<br/>
사용자 이름입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="see-also"></a>참고 항목

[클래스](../../atl/reference/atl-classes.md)
