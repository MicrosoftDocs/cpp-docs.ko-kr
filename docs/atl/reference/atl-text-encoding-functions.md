---
description: '자세한 정보: ATL 텍스트 인코딩 함수'
title: ATL 텍스트 인코딩 함수
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
ms.assetid: 2ae1648b-2b87-4112-92aa-0069fcfd23da
ms.openlocfilehash: 1cc0848fed5832d0d91752c4c52d1e7310df0932
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165253"
---
# <a name="atl-text-encoding-functions"></a>ATL 텍스트 인코딩 함수

이러한 함수는 텍스트 인코딩 및 디코딩을 지원 합니다.

|함수|설명|
|-|-|
|[AtlGetHexValue](#atlgethexvalue)|16진수의 숫자 값을 가져오려면 이 함수를 호출합니다.|
|[가 나 Getversion](#atlgetversion)|사용 중인 ATL 라이브러리의 버전을 가져오려면이 함수를 호출 합니다.  |
|[AtlHexDecode](#atlhexdecode)|[AtlHexEncode](#atlhexencode)에 대 한 이전 호출과 같이 16 진수 텍스트로 인코딩된 데이터의 문자열을 디코딩합니다.|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|지정된 길이의 16진수로 인코딩된 문자열에서 디코딩된 데이터를 포함할 수 있는 버퍼를 바이트 크기로 가져오려면 이 함수를 호출합니다.|
|[AtlHexEncode](#atlhexencode)|16진수 텍스트 문자열로 일부 데이터를 인코딩하려면 이 함수를 호출합니다.|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.|
|[AtlHexValue](#atlhexvalue)|16진수의 숫자 값을 가져오려면 이 함수를 호출합니다. |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|유니코드 문자열을 UTF-8로 변환하려면 이 함수를 호출합니다. |
|[BEncode](#bencode)|"B" 인코딩을 사용하여 일부 데이터를 변환하려면 이 함수를 호출합니다.|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.|
|[EscapeXML](#escapexml)|XML에서 사용하기에 안전하지 않은 문자를 안전한 문자로 변환하려면 이 함수를 호출합니다.|
|[GetExtendedChars](#getextendedchars)|문자열에서 확장된 문자 수를 가져오려면 이 함수를 호출합니다.|
|[IsExtendedChar](#isextendedchar)|지정 된 문자가 확장 문자 (32 미만, 126 보다 큼, 탭, 줄 바꿈 또는 캐리지 리턴) 인지 여부를 확인 하려면이 함수를 호출 합니다.|
|[QEncode](#qencode)|"Q" 인코딩을 사용하여 일부 데이터를 변환하려면 이 함수를 호출합니다.  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.|
|[QPDecode](#qpdecode)|[Qpencode](#qpencode)에 대 한 이전 호출과 같이 따옴표를 사용한 인쇄 가능 형식으로 인코딩된 데이터 문자열을 디코딩합니다.|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|지정된 길이의 quoted-printable로 인코딩된 문자열에서 디코딩된 데이터를 포함할 수 있는 버퍼를 바이트 크기로 가져오려면 이 함수를 호출합니다.|
|[QPEncode](#qpencode)|quoted-printable 형식으로 일부 데이터를 인코딩하려면 이 함수를 호출합니다.|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.|
|[UUDecode](#uudecode)|[UUEncode](#uuencode)의 이전 호출과 같이 uuencode 된 데이터의 문자열을 디코딩합니다.|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|지정된 길이의 uuencode된 문자열에서 디코딩된 데이터를 포함할 수 있는 버퍼를 바이트 크기로 가져오려면 이 함수를 호출합니다.|
|[UUEncode](#uuencode)|일부 데이터를 uuencode하려면 이 함수를 호출합니다. |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="atlgethexvalue"></a><a name="atlgethexvalue"></a> AtlGetHexValue

16진수의 숫자 값을 가져오려면 이 함수를 호출합니다.

```cpp
inline char AtlGetHexValue(char chIn) throw();
```

### <a name="parameters"></a>매개 변수

*chIn*<br/>
16 진수 문자 ' 0 '-' 9 ', ' 으로만 구성-'F ' 또는 ' 으로만 구성-'F '입니다.

### <a name="return-value"></a>반환 값

16 진수로 해석 된 입력 문자의 숫자 값입니다. 예를 들어 ' 0 '의 입력은 값 0을 반환 하 고 ' A ' 입력은 값 10을 반환 합니다. 입력 문자가 16 진수가 아니면이 함수는-1을 반환 합니다.

## <a name="atlgetversion"></a><a name="atlgetversion"></a> 가 나 Getversion

사용 중인 ATL 라이브러리의 버전을 가져오려면이 함수를 호출 합니다.

```cpp
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);
```

### <a name="parameters"></a>매개 변수

*되지만*<br/>
예약 된 포인터입니다.

### <a name="return-value"></a>반환 값

컴파일하거나 실행 중인 ATL 라이브러리 버전의 DWORD 정수 값을 반환 합니다.

## <a name="example"></a>예제

다음과 같이 함수를 호출 해야 합니다.

[!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="atlhexdecode"></a><a name="atlhexdecode"></a> AtlHexDecode

[AtlHexEncode](#atlhexencode)에 대 한 이전 호출과 같이 16 진수 텍스트로 인코딩된 데이터의 문자열을 디코딩합니다.

```cpp
inline BOOL AtlHexDecode(
   LPCSTR pSrcData,
   int nSrcLen,
   LPBYTE pbDest,
   int* pnDestLen) throw();
```

### <a name="parameters"></a>매개 변수

*pSrcData*<br/>
디코딩할 데이터를 포함 하는 문자열입니다.

*nSrcLen*<br/>
*Psrcdata* 의 문자 길이입니다.

*Pdest*<br/>
디코딩된 데이터를 받기 위해 호출자가 할당 한 버퍼입니다.

*pnDestLen*<br/>
*Pdest* 의 길이 (바이트)를 포함 하는 변수에 대 한 포인터입니다. 함수가 성공 하면 변수가 버퍼에 쓴 바이트 수를 받습니다. 함수가 실패 하면 변수는 버퍼의 필요한 길이 (바이트)를 받습니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="atlhexdecodegetrequiredlength"></a><a name="atlhexdecodegetrequiredlength"></a> AtlHexDecodeGetRequiredLength

지정된 길이의 16진수로 인코딩된 문자열에서 디코딩된 데이터를 포함할 수 있는 버퍼를 바이트 크기로 가져오려면 이 함수를 호출합니다.

```cpp
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>매개 변수

*nSrcLen*<br/>
인코딩된 문자열의 문자 수입니다.

### <a name="return-value"></a>반환 값

*NSrcLen* 문자의 디코딩된 문자열을 보유할 수 있는 버퍼에 필요한 바이트 수입니다.

## <a name="atlhexencode"></a><a name="atlhexencode"></a> AtlHexEncode

16진수 텍스트 문자열로 일부 데이터를 인코딩하려면 이 함수를 호출합니다.

```cpp
inline BOOL AtlHexEncode(
   const BYTE * pbSrcData,
   int nSrcLen,
   LPSTR szDest,
int * pnDestLen) throw();
```

### <a name="parameters"></a>매개 변수

*pbSrcData*<br/>
인코딩할 데이터를 포함 하는 버퍼입니다.

*nSrcLen*<br/>
인코딩할 데이터의 길이 (바이트)입니다.

*szDest*<br/>
인코딩된 데이터를 받기 위해 호출자가 할당 한 버퍼입니다.

*pnDestLen*<br/>
*Szdest* 의 문자 길이를 포함 하는 변수에 대 한 포인터입니다. 함수가 성공 하면 변수가 버퍼에 쓴 문자 수를 받습니다. 함수가 실패 하면 변수는 버퍼의 문자에 필요한 길이를 받습니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

원본 데이터의 각 바이트는 2 개의 16 진수 문자로 인코딩됩니다.

## <a name="atlhexencodegetrequiredlength"></a><a name="atlhexencodegetrequiredlength"></a> AtlHexEncodeGetRequiredLength

지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.

```cpp
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>매개 변수

*nSrcLen*<br/>
인코딩할 데이터의 바이트 수입니다.

### <a name="return-value"></a>반환 값

*NSrcLen* bytes의 인코딩된 데이터를 보유할 수 있는 버퍼에 필요한 문자 수입니다.

## <a name="atlhexvalue"></a><a name="atlhexvalue"></a> AtlHexValue

16진수의 숫자 값을 가져오려면 이 함수를 호출합니다.

```cpp
inline short AtlHexValue(char chIn) throw();
```

### <a name="parameters"></a>매개 변수

*chIn*<br/>
16 진수 문자 ' 0 '-' 9 ', ' 으로만 구성-'F ' 또는 ' 으로만 구성-'F '입니다.

### <a name="return-value"></a>반환 값

16 진수로 해석 된 입력 문자의 숫자 값입니다. 예를 들어 ' 0 '의 입력은 값 0을 반환 하 고 ' A ' 입력은 값 10을 반환 합니다. 입력 문자가 16 진수가 아니면이 함수는-1을 반환 합니다.

## <a name="atlunicodetoutf8"></a><a name="atlunicodetoutf8"></a> AtlUnicodeToUTF8

유니코드 문자열을 UTF-8로 변환하려면 이 함수를 호출합니다.

```cpp
ATL_NOINLINE inline int AtlUnicodeToUTF8(
   LPCWSTR wszSrc,
   int nSrc,
   LPSTR szDest,
   int nDest) throw();
```

### <a name="parameters"></a>매개 변수

*wszSrc*<br/>
변환할 유니코드 문자열입니다.

*nSrc*<br/>
유니코드 문자열의 문자 길이입니다.

*szDest*<br/>
변환 된 문자열을 받는 호출자가 할당 한 버퍼입니다.

*nDest*<br/>
버퍼의 길이 (바이트)입니다.

### <a name="return-value"></a>반환 값

변환 된 문자열의 문자 수를 반환 합니다.

### <a name="remarks"></a>설명

변환 된 문자열에 필요한 버퍼 크기를 확인 하려면 *Szdest* 및 *ndest* 에 대해 0을 전달 하는이 함수를 호출 합니다.

## <a name="bencode"></a><a name="bencode"></a> 코드 코드

"B" 인코딩을 사용하여 일부 데이터를 변환하려면 이 함수를 호출합니다.

```cpp
inline BOOL BEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet) throw();
```

### <a name="parameters"></a>매개 변수

*pbSrcData*<br/>
인코딩할 데이터를 포함 하는 버퍼입니다.

*nSrcLen*<br/>
인코딩할 데이터의 길이 (바이트)입니다.

*szDest*<br/>
인코딩된 데이터를 받기 위해 호출자가 할당 한 버퍼입니다.

*pnDestLen*<br/>
*Szdest* 의 문자 길이를 포함 하는 변수에 대 한 포인터입니다. 함수가 성공 하면 변수가 버퍼에 쓴 문자 수를 받습니다. 함수가 실패 하면 변수는 버퍼의 문자에 필요한 길이를 받습니다.

*pszCharSet*<br/>
변환에 사용할 문자 집합입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

"B" 인코딩 스키마는 RFC 2047 ()에 설명 되어 [https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt) 있습니다.

## <a name="bencodegetrequiredlength"></a><a name="bencodegetrequiredlength"></a> BEncodeGetRequiredLength

지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.

```cpp
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>매개 변수

*nSrcLen*<br/>
인코딩할 데이터의 바이트 수입니다.

*nCharsetLen*<br/>
변환에 사용할 문자 집합의 문자 길이입니다.

### <a name="return-value"></a>반환 값

*NSrcLen* bytes의 인코딩된 데이터를 보유할 수 있는 버퍼에 필요한 문자 수입니다.

### <a name="remarks"></a>설명

"B" 인코딩 스키마는 RFC 2047 ()에 설명 되어 [https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt) 있습니다.

## <a name="escapexml"></a><a name="escapexml"></a> EscapeXML

XML에서 사용하기에 안전하지 않은 문자를 안전한 문자로 변환하려면 이 함수를 호출합니다.

```cpp
inline int EscapeXML(
   const wchar_t * szIn,
   int nSrcLen,
   wchar_t * szEsc,
   int nDestLen,
   DWORD dwFlags = ATL_ESC_FLAG_NONE) throw();
```

### <a name="parameters"></a>매개 변수

*szIn*<br/>
변환할 문자열입니다.

*nSrclen*<br/>
변환할 문자열의 문자 길이입니다.

*szEsc*<br/>
변환 된 문자열을 받는 호출자가 할당 한 버퍼입니다.

*nDestLen*<br/>
호출자가 할당 한 버퍼의 문자 길이입니다.

*dwFlags*<br/>
변환을 수행 하는 방법을 설명 하는 ATL_ESC 플래그입니다.

- 기본 동작을 ATL_ESC_FLAG_NONE 합니다. 따옴표와 아포스트로피는 변환 되지 않습니다.
- ATL_ESC_FLAG_ATTR 인용 부호와 아포스트로피는 각각 및로 변환 됩니다 `&quot;` `&apos;` .

### <a name="return-value"></a>반환 값

변환 된 문자열의 문자 길이입니다.

### <a name="remarks"></a>설명

이 함수에서 수행할 수 있는 변환이 다음 표에 나와 있습니다.

|원본|대상|
|------------|-----------------|
|\<|&lt;|
|>|&gt;|
|&|&amp;|
|'|&apos;|
|"|&quot;|

## <a name="getextendedchars"></a><a name="getextendedchars"></a> GetExtendedChars

문자열에서 확장된 문자 수를 가져오려면 이 함수를 호출합니다.

```cpp
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();
```

### <a name="parameters"></a>매개 변수

*szSrc*<br/>
분석할 문자열입니다.

*nSrcLen*<br/>
문자열의 길이 (문자)입니다.

### <a name="return-value"></a>반환 값

[IsExtendedChar](#isextendedchar)에 의해 결정 된 대로 문자열 내에서 발견 된 확장 문자 수를 반환 합니다.

## <a name="isextendedchar"></a><a name="isextendedchar"></a> IsExtendedChar

지정 된 문자가 확장 문자 (32 미만, 126 보다 큼, 탭, 줄 바꿈 또는 캐리지 리턴) 인지 여부를 확인 하려면이 함수를 호출 합니다.

```cpp
inline int IsExtendedChar(char ch) throw();
```

### <a name="parameters"></a>매개 변수

*ch*<br/>
테스트할 문자입니다.

### <a name="return-value"></a>반환 값

문자가 확장 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.

## <a name="qencode"></a><a name="qencode"></a> QEncode

"Q" 인코딩을 사용하여 일부 데이터를 변환하려면 이 함수를 호출합니다.

```cpp
inline BOOL QEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet,
   int* pnNumEncoded = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*pbSrcData*<br/>
인코딩할 데이터를 포함 하는 버퍼입니다.

*nSrcLen*<br/>
인코딩할 데이터의 길이 (바이트)입니다.

*szDest*<br/>
인코딩된 데이터를 받기 위해 호출자가 할당 한 버퍼입니다.

*pnDestLen*<br/>
*Szdest* 의 문자 길이를 포함 하는 변수에 대 한 포인터입니다. 함수가 성공 하면 변수가 버퍼에 쓴 문자 수를 받습니다. 함수가 실패 하면 변수는 버퍼의 문자에 필요한 길이를 받습니다.

*pszCharSet*<br/>
변환에 사용할 문자 집합입니다.

*pnNumEncoded*<br/>
반환 시 변환 해야 하는 안전 하지 않은 문자 수를 포함 하는 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

"Q" 인코딩 스키마는 RFC 2047 ()에 설명 되어 [https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt) 있습니다.

## <a name="qencodegetrequiredlength"></a><a name="qencodegetrequiredlength"></a> QEncodeGetRequiredLength

지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.

```cpp
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>매개 변수

*nSrcLen*<br/>
인코딩할 데이터의 바이트 수입니다.

*nCharsetLen*<br/>
변환에 사용할 문자 집합의 문자 길이입니다.

### <a name="return-value"></a>반환 값

*NSrcLen* bytes의 인코딩된 데이터를 보유할 수 있는 버퍼에 필요한 문자 수입니다.

### <a name="remarks"></a>설명

"Q" 인코딩 스키마는 RFC 2047 ()에 설명 되어 [https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt) 있습니다.

## <a name="qpdecode"></a><a name="qpdecode"></a> QPDecode

[Qpencode](#qpencode)에 대 한 이전 호출과 같이 따옴표를 사용한 인쇄 가능 형식으로 인코딩된 데이터 문자열을 디코딩합니다.

```cpp
inline BOOL QPDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>매개 변수

*pbSrcData*<br/>
진행 디코딩할 데이터를 포함 하는 버퍼입니다.

*nSrcLen*<br/>
진행 *Pbsrcdata* 의 길이 (바이트)입니다.

*szDest*<br/>
제한이 디코딩된 데이터를 받기 위해 호출자가 할당 한 버퍼입니다.

*pnDestLen*<br/>
제한이 *Szdest* 의 길이 (바이트)를 포함 하는 변수에 대 한 포인터입니다. 함수가 성공 하면 변수가 버퍼에 쓴 바이트 수를 받습니다. 함수가 실패 하면 변수는 버퍼의 필요한 길이 (바이트)를 받습니다.

*dwFlags*<br/>
진행 변환을 수행 하는 방법을 설명 하는 ATLSMTP_QPENCODE 플래그입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

따옴표로 묶은 인쇄 가능한 인코딩 체계는 RFC 2045 ()에 설명 되어 [https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt) 있습니다.

## <a name="qpdecodegetrequiredlength"></a><a name="qpdecodegetrequiredlength"></a> QPDecodeGetRequiredLength

지정된 길이의 quoted-printable로 인코딩된 문자열에서 디코딩된 데이터를 포함할 수 있는 버퍼를 바이트 크기로 가져오려면 이 함수를 호출합니다.

```cpp
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>매개 변수

*nSrcLen*<br/>
인코딩된 문자열의 문자 수입니다.

### <a name="return-value"></a>반환 값

*NSrcLen* 문자의 디코딩된 문자열을 보유할 수 있는 버퍼에 필요한 바이트 수입니다.

### <a name="remarks"></a>설명

따옴표로 묶은 인쇄 가능한 인코딩 체계는 RFC 2045 ()에 설명 되어 [https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt) 있습니다.

## <a name="qpencode"></a><a name="qpencode"></a> QPEncode

quoted-printable 형식으로 일부 데이터를 인코딩하려면 이 함수를 호출합니다.

```cpp
inline BOOL QPEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>매개 변수

*pbSrcData*<br/>
인코딩할 데이터를 포함 하는 버퍼입니다.

*nSrcLen*<br/>
인코딩할 데이터의 길이 (바이트)입니다.

*szDest*<br/>
인코딩된 데이터를 받기 위해 호출자가 할당 한 버퍼입니다.

*pnDestLen*<br/>
*Szdest* 의 문자 길이를 포함 하는 변수에 대 한 포인터입니다. 함수가 성공 하면 변수가 버퍼에 쓴 문자 수를 받습니다. 함수가 실패 하면 변수는 버퍼의 문자에 필요한 길이를 받습니다.

*dwFlags*<br/>
변환을 수행 하는 방법을 설명 하는 ATLSMTP_QPENCODE 플래그입니다.

- 줄의 시작 부분에 마침표가 표시 되는 경우에는 인코딩 뿐만 아니라 출력에도 추가 됩니다. ATLSMTP_QPENCODE_DOT

- ATLSMTP_QPENCODE_TRAILING_SOFT `=\r\n` 인코딩된 문자열에 추가 합니다.

따옴표로 묶은 인쇄 가능한 인코딩 체계는 [RFC 2045](https://www.ietf.org/rfc/rfc2045.txt)에 설명 되어 있습니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

따옴표로 묶은 인쇄 가능한 인코딩 체계는 RFC 2045 ()에 설명 되어 [https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt) 있습니다.

## <a name="qpencodegetrequiredlength"></a><a name="qpencodegetrequiredlength"></a> QPEncodeGetRequiredLength

지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.

```cpp
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>매개 변수

*nSrcLen*<br/>
인코딩할 데이터의 바이트 수입니다.

### <a name="return-value"></a>반환 값

*NSrcLen* bytes의 인코딩된 데이터를 보유할 수 있는 버퍼에 필요한 문자 수입니다.

### <a name="remarks"></a>설명

따옴표로 묶은 인쇄 가능한 인코딩 체계는 RFC 2045 ()에 설명 되어 [https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt) 있습니다.

## <a name="uudecode"></a><a name="uudecode"></a> UUDecode

[UUEncode](#uuencode)의 이전 호출과 같이 uuencode 된 데이터의 문자열을 디코딩합니다.

```cpp
inline BOOL UUDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   BYTE* pbDest,
   int* pnDestLen) throw ();
```

### <a name="parameters"></a>매개 변수

*pbSrcData*<br/>
디코딩할 데이터를 포함 하는 문자열입니다.

*nSrcLen*<br/>
*Pbsrcdata* 의 길이 (바이트)입니다.

*Pdest*<br/>
디코딩된 데이터를 받기 위해 호출자가 할당 한 버퍼입니다.

*pnDestLen*<br/>
*Pdest* 의 길이 (바이트)를 포함 하는 변수에 대 한 포인터입니다. 함수가 성공 하면 변수가 버퍼에 쓴 바이트 수를 받습니다. 함수가 실패 하면 변수는 버퍼의 필요한 길이 (바이트)를 받습니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 uuencoding 구현은 POSIX P 1003.2 b/p s 사양을 따릅니다.

## <a name="uudecodegetrequiredlength"></a><a name="uudecodegetrequiredlength"></a> UUDecodeGetRequiredLength

지정된 길이의 uuencode된 문자열에서 디코딩된 데이터를 포함할 수 있는 버퍼를 바이트 크기로 가져오려면 이 함수를 호출합니다.

```cpp
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>매개 변수

*nSrcLen*<br/>
인코딩된 문자열의 문자 수입니다.

### <a name="return-value"></a>반환 값

*NSrcLen* 문자의 디코딩된 문자열을 보유할 수 있는 버퍼에 필요한 바이트 수입니다.

### <a name="remarks"></a>설명

이 uuencoding 구현은 POSIX P 1003.2 b/p s 사양을 따릅니다.

## <a name="uuencode"></a><a name="uuencode"></a> UUEncode

일부 데이터를 uuencode하려면 이 함수를 호출합니다.

```cpp
inline BOOL UUEncode(
   const BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCTSTR lpszFile = _T("file"),
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>매개 변수

*pbSrcData*<br/>
인코딩할 데이터를 포함 하는 버퍼입니다.

*nSrcLen*<br/>
인코딩할 데이터의 길이 (바이트)입니다.

*szDest*<br/>
인코딩된 데이터를 받기 위해 호출자가 할당 한 버퍼입니다.

*pnDestLen*<br/>
*Szdest* 의 문자 길이를 포함 하는 변수에 대 한 포인터입니다. 함수가 성공 하면 변수가 버퍼에 쓴 문자 수를 받습니다. 함수가 실패 하면 변수는 버퍼의 문자에 필요한 길이를 받습니다.

*lpszFile*<br/>
ATLSMTP_UUENCODE_HEADER이 *dwFlags* 에 지정 된 경우 헤더에 추가할 파일입니다.

*dwFlags*<br/>
이 함수의 동작을 제어 하는 플래그입니다.

- 헤더가 인코딩될 ATLSMTP_UUENCODE_HEADE입니다.

- 끝을 인코딩할 ATLSMTP_UUENCODE_END 합니다.

- ATLSMTP_UUENCODE_DOT 데이터 stuffing 수행 됩니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 uuencoding 구현은 POSIX P 1003.2 b/p s 사양을 따릅니다.

## <a name="uuencodegetrequiredlength"></a><a name="uuencodegetrequiredlength"></a> UUEncodeGetRequiredLength

지정된 크기의 데이터에서 디코딩된 문자열을 포함할 수 있는 버퍼를 문자 크기로 가져오려면 이 함수를 호출합니다.

```cpp
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>매개 변수

*nSrcLen*<br/>
인코딩할 데이터의 바이트 수입니다.

### <a name="return-value"></a>반환 값

*NSrcLen* bytes의 인코딩된 데이터를 보유할 수 있는 버퍼에 필요한 문자 수입니다.

### <a name="remarks"></a>설명

이 uuencoding 구현은 POSIX P 1003.2 b/p s 사양을 따릅니다.

## <a name="see-also"></a>참고 항목

[개념](../active-template-library-atl-concepts.md)<br/>
[ATL COM 데스크톱 구성 요소](../atl-com-desktop-components.md)
