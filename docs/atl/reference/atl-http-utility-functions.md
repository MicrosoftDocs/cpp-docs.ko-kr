---
description: '자세한 정보: ATL HTTP 유틸리티 함수'
title: ATL HTTP 유틸리티 함수
ms.date: 11/04/2016
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
ms.openlocfilehash: fb8cc8789db45095f969dd9513dcf70a9bd0d05c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165370"
---
# <a name="atl-http-utility-functions"></a>ATL HTTP 유틸리티 함수

이러한 함수는 Url 조작을 지원 합니다.

|함수|설명|
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes 안전 하지 않은 문자 및 공백을 이스케이프 시퀀스로 변환 하는 것을 포함 하는 URL입니다.|
|[AtlCombineUrl](#atlcombineurl)|기준 URL과 상대 URL을 단일 정식 URL로 결합 합니다.|
|[AtlEscapeUrl](#atlescapeurl)|안전 하지 않은 모든 문자를 이스케이프 시퀀스로 변환 합니다.|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|특정 인터넷 프로토콜 또는 체계와 연결 된 기본 포트 번호를 가져옵니다.|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|문자를 URL에서 사용할 수 있는지 여부를 확인 합니다.|
|[AtlUnescapeUrl](#atlunescapeurl)|이스케이프 된 문자를 원래 값으로 다시 변환 합니다.|
|[RGBToHtml](#rgbtohtml)|[Colorref](/windows/win32/gdi/colorref) 값을 해당 색 값에 해당 하는 HTML 텍스트로 변환 합니다.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|시스템 시간을 HTTP 헤더에서 사용하기에 적합한 형식의 문자열로 변환하려면 이 함수를 호출합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="atlcanonicalizeurl"></a><a name="atlcanonicalizeurl"></a> AtlCanonicalizeUrl

안전하지 않은 문자와 공백을 이스케이프 시퀀스로 변환하는 등 URL을 정식화하려면 이 함수를 호출합니다.

```cpp
inline BOOL AtlCanonicalizeUrl(
   LPCTSTR szUrl,
   LPTSTR szCanonicalized,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>매개 변수

*szUrl*<br/>
정식화 할 URL입니다.

*szCanonicalized*<br/>
정규화 된 URL을 받기 위해 호출자가 할당 한 버퍼입니다.

*pdwMaxLength*<br/>
*Szcanonicalized* 의 문자 길이를 포함 하는 변수에 대 한 포인터입니다. 함수가 성공 하면 변수는 종료 null 문자를 포함 하 여 버퍼에 쓴 문자 수를 받습니다. 함수가 실패 하면 변수는 종료 null 문자에 대 한 공간을 포함 하 여 버퍼의 필요한 길이 (바이트)를 받습니다.

*dwFlags*<br/>
이 함수의 동작을 제어 하 ATL_URL 플래그입니다.

- ATL_URL_BROWSER_MODE "#" 또는 "?" 뒤에 문자를 인코딩하거나 디코드 하지 않으며 "?" 뒤에 후행 공백을 제거 하지 않습니다. 이 값을 지정 하지 않으면 전체 URL이 인코딩되고 후행 공백이 제거 됩니다.

- ATL_URL_DECODE는 URL을 구문 분석 하기 전에 모든% XX 시퀀스를 이스케이프 시퀀스를 포함 하는 문자로 변환 합니다.

- ATL_URL_ENCODE_PERCENT은 발생 한 백분율 기호를 인코딩합니다. 기본적으로 백분율 기호는 인코딩되지 않습니다.

- ATL_URL_ENCODE_SPACES_ONLY 공간만 인코딩합니다.

- ATL_URL_ESCAPE 모든 이스케이프 시퀀스 (% XX)를 해당 문자로 변환 합니다.

- ATL_URL_NO_ENCODE 안전 하지 않은 문자를 이스케이프 시퀀스로 변환 하지 않습니다.

- ATL_URL_NO_META는 URL에서 메타 시퀀스 (예: "." 및 ".")를 제거 하지 않습니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

는 현재 버전의 [InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw) 처럼 동작 하지만 WinInet 또는 Internet Explorer를 설치 하지 않아도 됩니다.

## <a name="atlcombineurl"></a><a name="atlcombineurl"></a> AtlCombineUrl

기본 URL과 상대 URL을 단일 정규 URL로 결합하려면 이 함수를 호출합니다.

```cpp
inline BOOL AtlCombineUrl(
   LPCTSTR szBaseUrl,
   LPCTSTR szRelativeUrl,
   LPTSTR szBuffer,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>매개 변수

*szBaseUrl*<br/>
기본 URL입니다.

*szRelativeUrl*<br/>
기준 URL을 기준으로 하는 URL입니다.

*szBuffer*<br/>
정규화 된 URL을 받기 위해 호출자가 할당 한 버퍼입니다.

*pdwMaxLength*<br/>
*Szbuffer* 의 문자 길이를 포함 하는 변수에 대 한 포인터입니다. 함수가 성공 하면 변수는 종료 null 문자를 포함 하 여 버퍼에 쓴 문자 수를 받습니다. 함수가 실패 하면 변수는 종료 null 문자에 대 한 공간을 포함 하 여 버퍼의 필요한 길이 (바이트)를 받습니다.

*dwFlags*<br/>
이 함수의 동작을 제어 하는 플래그입니다. [AtlCanonicalizeUrl](#atlcanonicalizeurl)를 참조 하세요.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

는 현재 버전의 [InternetCombineUrl](/windows/win32/api/wininet/nf-wininet-internetcombineurlw) 처럼 동작 하지만 WinInet 또는 Internet Explorer를 설치 하지 않아도 됩니다.

## <a name="atlescapeurl"></a><a name="atlescapeurl"></a> AtlEscapeUrl

모든 안전하지 않은 문자를 이스케이프 시퀀스로 변환하려면 이 함수를 호출합니다.

```cpp
inline BOOL AtlEscapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();

inline BOOL AtlEscapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>매개 변수

*lpszStringIn*<br/>
변환할 URL입니다.

*lpszStringOut*<br/>
변환 된 URL이 기록 될 호출자가 할당 한 버퍼입니다.

*pdwStrLen*<br/>
DWORD 변수에 대 한 포인터입니다. 함수가 성공 하면 *pdwStrLen* 는 종료 null 문자를 포함 하 여 버퍼에 쓴 문자 수를 수신 합니다. 함수가 실패 하면 변수는 종료 null 문자에 대 한 공간을 포함 하 여 버퍼의 필요한 길이 (바이트)를 받습니다. 이 메서드의 와이드 문자 버전을 사용 하는 경우 *pdwStrLen* 는 바이트 수가 아니라 필요한 문자 수를 수신 합니다.

*dwMaxLength*<br/>
*LpszStringOut* 버퍼의 크기입니다.

*dwFlags*<br/>
이 함수의 동작을 제어 하 ATL_URL 플래그입니다. 가능한 값에 대해서는 [ATLCanonicalizeUrl](#atlcanonicalizeurl) 을 참조 하세요.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="atlgetdefaulturlport"></a><a name="atlgetdefaulturlport"></a> 워크플로

특정 인터넷 프로토콜 또는 체계와 관련된 기본 포트 번호를 가져오려면 이 함수를 호출합니다.

```cpp
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();
```

### <a name="parameters"></a>매개 변수

*m_nScheme*<br/>
포트 번호를 가져올 체계를 식별 하는 [ATL_URL_SCHEME](atl-url-scheme-enum.md) 값입니다.

### <a name="return-value"></a>반환 값

지정 된 체계와 관련 된 [ATL_URL_PORT](atl-typedefs.md#atl_url_port) 또는 구성표를 인식할 수 없는 경우 ATL_URL_INVALID_PORT_NUMBER입니다.

## <a name="atlisunsafeurlchar"></a><a name="atlisunsafeurlchar"></a> AtlIsUnsafeUrlChar

URL에서 문자를 안전하게 사용할 수 있는지 확인하려면 이 함수를 호출합니다.

```cpp
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();
```

### <a name="parameters"></a>매개 변수

*chIn*<br/>
안전을 위해 테스트할 문자입니다.

### <a name="return-value"></a>반환 값

입력 문자가 안전 하지 않으면 TRUE를 반환 하 고 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

Url에 사용 하지 않아야 하는 문자는이 함수를 사용 하 여 테스트 하 고 [AtlCanonicalizeUrl](#atlcanonicalizeurl)를 사용 하 여 변환할 수 있습니다.

## <a name="atlunescapeurl"></a><a name="atlunescapeurl"></a> AtlUnescapeUrl

이스케이프된 문자를 원래 값으로 다시 변환하려면 이 함수를 호출합니다.

```cpp
inline BOOL AtlUnescapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();

inline BOOL AtlUnescapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();
```

### <a name="parameters"></a>매개 변수

*lpszStringIn*<br/>
변환할 URL입니다.

*lpszStringOut*<br/>
변환 된 URL이 기록 될 호출자가 할당 한 버퍼입니다.

*pdwStrLen*<br/>
DWORD 변수에 대 한 포인터입니다. 함수가 성공 하면 변수는 종료 null 문자를 포함 하 여 버퍼에 쓴 문자 수를 받습니다. 함수가 실패 하면 변수는 종료 null 문자에 대 한 공간을 포함 하 여 버퍼의 필요한 길이 (바이트)를 받습니다.

*dwMaxLength*<br/>
*LpszStringOut* 버퍼의 크기입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

[AtlEscapeUrl](#atlescapeurl)에 의해 적용 되는 변환 프로세스를 반대로 바꿉니다.

## <a name="rgbtohtml"></a><a name="rgbtohtml"></a> RGBToHtml

[Colorref](/windows/win32/gdi/colorref) 값을 해당 색 값에 해당 하는 HTML 텍스트로 변환 합니다.

```cpp
bool inline RGBToHtml(
   COLORREF color,
   LPTSTR pbOut,
   long nBuffer);
```

### <a name="parameters"></a>매개 변수

*color*<br/>
RGB 색 값입니다.

*Pout*<br/>
HTML 색 값에 대 한 텍스트를 받을 호출자가 할당 한 버퍼입니다. 버퍼에는 null 종결자를 위한 공간을 포함 하 여 8 자 이상의 공간이 있어야 합니다.

*nBuffer*<br/>
버퍼의 크기 (바이트)입니다 (null 종결자의 공간 포함).

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

HTML 색 값은 색의 빨간색, 녹색 및 파랑 구성 요소 각각에 대해 2 자리를 사용 하는 파운드 기호 (예: #FFFFFF은 흰색)입니다.

## <a name="systemtimetohttpdate"></a><a name="systemtimetohttpdate"></a> SystemTimeToHttpDate

시스템 시간을 HTTP 헤더에서 사용하기에 적합한 형식의 문자열로 변환하려면 이 함수를 호출합니다.

```cpp
inline void SystemTimeToHttpDate(
   const SYSTEMTIME& st,
   CStringA& strTime);
```

### <a name="parameters"></a>매개 변수

*세인트*<br/>
HTTP 형식 문자열로 가져올 시스템 시간입니다.

*strTime*<br/>
RFC 2616 ( [https://www.ietf.org/rfc/rfc2616.txt](https://www.ietf.org/rfc/rfc2616.txt) ) 및 rfc 1123 ()에 정의 된 HTTP 날짜 시간을 받을 문자열 변수에 대 한 참조 [https://www.ietf.org/rfc/rfc1123.txt](https://www.ietf.org/rfc/rfc1123.txt) 입니다.

## <a name="see-also"></a>참고 항목

[개념](../active-template-library-atl-concepts.md)<br/>
[ATL COM 데스크톱 구성 요소](../atl-com-desktop-components.md)<br/>
[InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw)
