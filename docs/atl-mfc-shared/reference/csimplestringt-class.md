---
title: CSimpleStringT 클래스
ms.date: 10/18/2018
f1_keywords:
- CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::PCXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::PXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::Append
- ATLSIMPSTR/ATL::CSimpleStringT::AppendChar
- ATLSIMPSTR/ATL::CSimpleStringT::CopyChars
- ATLSIMPSTR/ATL::CSimpleStringT::CopyCharsOverlapped
- ATLSIMPSTR/ATL::CSimpleStringT::Empty
- ATLSIMPSTR/ATL::CSimpleStringT::FreeExtra
- ATLSIMPSTR/ATL::CSimpleStringT::GetAllocLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetAt
- ATLSIMPSTR/ATL::CSimpleStringT::GetBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::GetBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetManager
- ATLSIMPSTR/ATL::CSimpleStringT::GetString
- ATLSIMPSTR/ATL::CSimpleStringT::IsEmpty
- ATLSIMPSTR/ATL::CSimpleStringT::LockBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::Preallocate
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::SetAt
- ATLSIMPSTR/ATL::CSimpleStringT::SetManager
- ATLSIMPSTR/ATL::CSimpleStringT::SetString
- ATLSIMPSTR/ATL::CSimpleStringT::StringLength
- ATLSIMPSTR/ATL::CSimpleStringT::Truncate
- ATLSIMPSTR/ATL::CSimpleStringT::UnlockBuffer
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
ms.openlocfilehash: c033346b7a687a1c6778ad23e30ee0e73c787ad8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865083"
---
# <a name="csimplestringt-class"></a>CSimpleStringT 클래스

이 클래스는 `CSimpleStringT` 개체를 나타냅니다.

## <a name="syntax"></a>구문

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>매개 변수

*BaseType*<br/>
문자열 클래스의 문자 형식입니다. 다음 중 하나일 수 있습니다.

- **char** (ANSI 문자열의 경우).

- **wchar_t** (유니코드 문자열의 경우).

- TCHAR.H (ANSI 및 유니코드 문자열 모두)

## <a name="members"></a>구성원

### <a name="public-typedefs"></a>공용 형식 정의

|속성|Description|
|----------|-----------------|
|[CSimpleStringT::P CXSTR](#pcxstr)|상수 문자열에 대 한 포인터입니다.|
|[CSimpleStringT::P XSTR](#pxstr)|문자열에 대 한 포인터입니다.|

### <a name="public-constructors"></a>Public 생성자

|속성|Description|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|`CSimpleStringT` 개체를 다양 한 방식으로 생성 합니다.|
|[CSimpleStringT:: ~ CSimpleStringT](#dtor)|소멸자|

### <a name="public-methods"></a>Public 메서드

|속성|Description|
|----------|-----------------|
|[CSimpleStringT:: Append](#append)|기존 `CSimpleStringT` 개체에 `CSimpleStringT` 개체를 추가 합니다.|
|[CSimpleStringT:: AppendChar](#appendchar)|기존 `CSimpleStringT` 개체에 문자를 추가 합니다.|
|[CSimpleStringT:: CopyChars](#copychars)|문자 또는 문자를 다른 문자열에 복사 합니다.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|문자열이 겹치는 다른 문자열에 문자 또는 문자를 복사 합니다.|
|[CSimpleStringT:: Empty](#empty)|문자열의 길이가 0이 되도록 합니다.|
|[CSimpleStringT:: FreeExtra](#freeextra)|문자열 개체에서 이전에 할당 한 추가 메모리를 해제 합니다.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|`CSimpleStringT` 개체의 할당 된 길이를 검색 합니다.|
|[CSimpleStringT:: GetAt](#getat)|지정 된 위치에 있는 문자를 반환 합니다.|
|[CSimpleStringT:: GetBuffer](#getbuffer)|`CSimpleStringT`의 문자에 대 한 포인터를 반환 합니다.|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|지정 된 길이로 잘라내는 `CSimpleStringT`의 문자에 대 한 포인터를 반환 합니다.|
|[CSimpleStringT:: GetLength](#getlength)|`CSimpleStringT` 개체의 문자 수를 반환 합니다.|
|[CSimpleStringT:: GetManager](#getmanager)|`CSimpleStringT` 개체의 메모리 관리자를 검색 합니다.|
|[CSimpleStringT:: GetString](#getstring)|문자열을 검색 합니다.|
|[CSimpleStringT:: IsEmpty](#isempty)|`CSimpleStringT` 개체에 문자가 포함 되어 있지 않은지 여부를 테스트 합니다.|
|[CSimpleStringT:: LockBuffer](#lockbuffer)|참조 횟수를 사용 하지 않도록 설정 하 고 버퍼의 문자열을 보호 합니다.|
|[CSimpleStringT::P 다시 할당](#preallocate)|문자 버퍼에 대 한 특정 메모리 양을 할당 합니다.|
|[CSimpleStringT:: ReleaseBuffer](#releasebuffer)|`GetBuffer`에서 반환 된 버퍼의 제어를 해제 합니다.|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|`GetBuffer`에서 반환 된 버퍼의 제어를 해제 합니다.|
|[CSimpleStringT:: SetAt](#setat)|지정 된 위치에 문자를 설정 합니다.|
|[CSimpleStringT:: SetManager](#setmanager)|`CSimpleStringT` 개체의 메모리 관리자를 설정 합니다.|
|[CSimpleStringT:: SetString](#setstring)|`CSimpleStringT` 개체의 문자열을 설정 합니다.|
|[CSimpleStringT:: StringLength](#stringlength)|지정 된 문자열의 문자 수를 반환 합니다.|
|[CSimpleStringT:: Truncate](#truncate)|문자열을 지정 된 길이로 자릅니다.|
|[CSimpleStringT:: UnlockBuffer](#unlockbuffer)|참조 횟수를 사용 하도록 설정 하 고 버퍼에서 문자열을 해제 합니다.|

### <a name="public-operators"></a>Public 연산자

|속성|Description|
|----------|-----------------|
|[CSimpleStringT:: operator PCXSTR](#operator_pcxstr)|`CSimpleStringT` 개체에 저장 된 문자를 C 스타일 문자열로 직접 액세스 합니다.|
|[CSimpleStringT:: operator\[\]](#operator_at)|`GetAt`에 대 한 연산자 대체를 지정 된 위치에 반환 합니다.|
|[CSimpleStringT:: operator + =](#operator_add_eq)|새 문자열을 기존 문자열의 끝에 연결 합니다.|
|[CSimpleStringT:: operator =](#operator_eq)|`CSimpleStringT` 개체에 새 값을 할당 합니다.|

### <a name="remarks"></a>설명

`CSimpleStringT`은 시각적 개체 C++에서 지 원하는 다양 한 문자열 클래스의 기본 클래스입니다. 문자열 개체의 메모리 관리와 기본 버퍼 조작을 최소한으로 지원 합니다. 고급 문자열 개체는 [CStringT 클래스](../../atl-mfc-shared/reference/cstringt-class.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** atlsimpstr

## <a name="append"></a>CSimpleStringT:: Append

기존 `CSimpleStringT` 개체에 `CSimpleStringT` 개체를 추가 합니다.

### <a name="syntax"></a>구문

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>매개 변수

*strSrc*<br/>
추가할 `CSimpleStringT` 개체입니다.

*pszSrc*<br/>
추가할 문자를 포함 하는 문자열에 대 한 포인터입니다.

*nLength*<br/>
추가할 문자 수입니다.

### <a name="remarks"></a>설명

기존 `CSimpleStringT` 개체를 다른 `CSimpleStringT` 개체에 추가 하려면이 메서드를 호출 합니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::Append`의 사용법을 보여줍니다.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

##  <a name="appendchar"></a>CSimpleStringT:: AppendChar

기존 `CSimpleStringT` 개체에 문자를 추가 합니다.

### <a name="syntax"></a>구문

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>매개 변수

*ch*<br/>
추가할 문자입니다.

### <a name="remarks"></a>설명

지정 된 문자를 기존 `CSimpleStringT` 개체의 끝에 추가 하려면이 함수를 호출 합니다.

##  <a name="copychars"></a>CSimpleStringT:: CopyChars

`CSimpleStringT` 개체에 문자를 복사 합니다.

### <a name="syntax"></a>구문

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>매개 변수

*pchDest*<br/>
문자열에 대 한 포인터입니다.

*pchSrc*<br/>
복사할 문자를 포함 하는 문자열에 대 한 포인터입니다.

*nChars*<br/>
복사할 *Pchsrc* 문자 수입니다.

### <a name="remarks"></a>설명

*Pchsrc* 에서 *pchsrc* 문자열로 문자를 복사 하려면이 메서드를 호출 합니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::CopyChars`의 사용법을 보여줍니다.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

##  <a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped

`CSimpleStringT` 개체에 문자를 복사 합니다.

### <a name="syntax"></a>구문

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>매개 변수

*pchDest*<br/>
문자열에 대 한 포인터입니다.

*pchSrc*<br/>
복사할 문자를 포함 하는 문자열에 대 한 포인터입니다.

*nChars*<br/>
복사할 *Pchsrc* 문자 수입니다.

### <a name="remarks"></a>설명

*Pchsrc* 에서 *pchsrc* 문자열로 문자를 복사 하려면이 메서드를 호출 합니다. `CopyChars`와 달리 `CopyCharsOverlapped`는 겹칠 수 있는 문자 버퍼에서 복사할 수 있는 안전한 방법을 제공 합니다.

### <a name="example"></a>예제

[CSimpleStringT:: CopyChars](#copychars)의 예제 또는 `CSimpleStringT::SetString`에 대 한 소스 코드 (atlsimpstr에 있음)를 참조 하세요.

##  <a name="ctor"></a>CSimpleStringT::CSimpleStringT

`CSimpleStringT` 개체를 생성합니다.

### <a name="syntax"></a>구문

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>매개 변수

*strSrc*<br/>
이 `CSimpleStringT` 개체에 복사할 기존 `CSimpleStringT` 개체입니다.

*pchSrc*<br/>
길이가 *Nlength*인 문자 배열에 대 한 포인터로, null이 끝나지 않습니다.

*pszSrc*<br/>
이 `CSimpleStringT` 개체로 복사할 null 종료 문자열입니다.

*nLength*<br/>
`pch`의 문자 수입니다.

*pStringMgr*<br/>
`CSimpleStringT` 개체의 메모리 관리자에 대 한 포인터입니다. `CSimpleStringT`에 대 한 `IAtlStringMgr` 및 메모리 관리에 대 한 자세한 내용은 [메모리 관리 및 CStringT](../memory-management-with-cstringt.md)를 참조 하십시오.

### <a name="remarks"></a>설명

새 `CSimpleStringT` 개체를 생성합니다. 생성자는 입력 데이터를 새 할당 된 저장소에 복사 하므로 메모리 예외가 발생할 수 있습니다.

### <a name="example"></a>예제

다음 예제에서는 ATL **typedef** `CSimpleString`를 사용 하 여 `CSimpleStringT::CSimpleStringT`를 사용 하는 방법을 보여 줍니다. `CSimpleString`은 일반적으로 사용 되는 클래스 템플릿 `CSimpleStringT`의 특수화입니다.

```cpp
CSimpleString s1(pMgr);
// Empty string
CSimpleString s2(_T("cat"), pMgr);
// From a C string literal

CSimpleString s3(s2);
// Copy constructor
CSimpleString s4(s2 + _T(" ") + s3);

// From a string expression
CSimpleString s5(_T("xxxxxx"), 6, pMgr);
// s5 = "xxxxxx"
```

##  <a name="empty"></a>CSimpleStringT:: Empty

이 `CSimpleStringT` 개체를 빈 문자열로 만들고 메모리를 적절 하 게 해제 합니다.

### <a name="syntax"></a>구문

```
void Empty() throw();
```

### <a name="remarks"></a>설명

자세한 내용은 [문자열: CString 예외 정리](../cstring-exception-cleanup.md)를 참조 하세요.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::Empty`의 사용법을 보여줍니다.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="freeextra"></a>CSimpleStringT:: FreeExtra

이전에 문자열에 의해 할당 되었지만 더 이상 필요 하지 않은 추가 메모리를 해제 합니다.

### <a name="syntax"></a>구문

```
void FreeExtra();
```

### <a name="remarks"></a>설명

이렇게 하면 문자열 개체에서 사용 하는 메모리 오버 헤드가 줄어듭니다. 메서드는 [Getlength](#getlength)에서 반환 된 정확한 길이에 버퍼를 다시 할당 합니다.

### <a name="example"></a>예제

```cpp
CAtlString basestr;
IAtlStringMgr* pMgr;

pMgr= basestr.GetManager();
ASSERT(pMgr != NULL);

// Create a CSimpleString with 28 characters
CSimpleString str(_T("Many sports are fun to play."), 28, pMgr);
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// Assigning a smaller string won't cause CSimpleString to free its
// memory, because it assumes the string will grow again anyway.
str = _T("Soccer is best!");
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// This call forces CSimpleString to release the extra
// memory it doesn't need.
str.FreeExtra();
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());
```

### <a name="remarks"></a>설명

이 예제의 출력은 다음과 같습니다.

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

##  <a name="getalloclength"></a>CSimpleStringT::GetAllocLength

`CSimpleStringT` 개체의 할당 된 길이를 검색 합니다.

### <a name="syntax"></a>구문

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Return Value

이 개체에 할당 된 문자 수입니다.

### <a name="remarks"></a>설명

이 `CSimpleStringT` 개체에 할당 되는 문자 수를 확인 하려면이 메서드를 호출 합니다. 이 함수를 호출 하는 예제는 [Freeextra](#freeextra) 를 참조 하세요.

##  <a name="getat"></a>CSimpleStringT:: GetAt

`CSimpleStringT` 개체에서 문자 하나를 반환 합니다.

### <a name="syntax"></a>구문

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>매개 변수

*iChar*<br/>
`CSimpleStringT` 개체에 있는 문자의 0부터 시작 하는 인덱스입니다. *IChar* 매개 변수는 0 보다 크거나 같고 [getlength](#getlength)에서 반환 된 값 보다 작아야 합니다. 그렇지 않으면 `GetAt`에서 예외를 생성 합니다.

### <a name="return-value"></a>Return Value

문자열의 지정 된 위치에 있는 문자를 포함 하는 `XCHAR`입니다.

### <a name="remarks"></a>설명

*IChar*로 지정 된 문자를 반환 하려면이 메서드를 호출 합니다. 오버 로드 된 첨자 ( **[]** ) 연산자는 `GetAt`에 대 한 편리한 별칭입니다. `GetAt`를 사용 하 여 예외를 생성 하지 않고 null 종결자에 주소를 지정할 수 있습니다. 그러나 `GetLength`로 계산 되지 않고 반환 되는 값은 0입니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::GetAt`를 사용 하는 방법을 보여 줍니다.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

##  <a name="getbuffer"></a>CSimpleStringT:: GetBuffer

`CSimpleStringT` 개체의 내부 문자 버퍼에 대 한 포인터를 반환 합니다.

### <a name="syntax"></a>구문

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>매개 변수

*nMinBufferLength*<br/>
문자 버퍼에서 보유할 수 있는 최소 문자 수입니다. 이 값에는 null 종결자를 위한 공간이 포함 되지 않습니다.

*Nminbufferlength* 가 현재 `GetBuffer` 버퍼의 길이 보다 크면 현재 버퍼를 삭제 하 고 요청한 크기의 버퍼로 바꾸고 개체 참조 횟수를 0으로 다시 설정 합니다. 이전에이 버퍼에서 [Lockbuffer](#lockbuffer) 를 호출한 경우 버퍼 잠금이 손실 됩니다.

### <a name="return-value"></a>Return Value

개체의 (null로 끝나는) 문자 버퍼에 대 한 `PXSTR` 포인터입니다.

### <a name="remarks"></a>설명

`CSimpleStringT` 개체의 버퍼 내용을 반환 하려면이 메서드를 호출 합니다. 반환 된 `PXSTR`는 상수가 아니므로 `CSimpleStringT` 콘텐츠를 직접 수정할 수 있습니다.

`GetBuffer`에서 반환 된 포인터를 사용 하 여 문자열 내용을 변경 하는 경우 다른 `CSimpleStringT` 멤버 메서드를 사용 하기 전에 [Releasebuffer](#releasebuffer) 를 호출 해야 합니다.

`ReleaseBuffer`를 호출한 후에는 `GetBuffer`에서 반환 된 주소가 유효 하지 않을 수 있습니다. 추가 `CSimpleStringT` 작업으로 인해 `CSimpleStringT` 버퍼가 다시 할당 될 수 있기 때문입니다. `CSimpleStringT`길이를 변경 하지 않으면 버퍼가 재할당 되지 않습니다.

버퍼 메모리는 `CSimpleStringT` 개체가 제거 될 때 자동으로 해제 됩니다.

문자열 길이를 직접 추적 하는 경우에는 null 종결 문자를 추가 하면 안 됩니다. 그러나 `ReleaseBuffer`를 사용 하 여 버퍼를 해제할 때 최종 문자열 길이를 지정 해야 합니다. 종료 null 문자를 추가 하는 경우 길이에-1 (기본값)을 전달 해야 합니다. 그런 다음 `ReleaseBuffer`는 버퍼 길이를 결정 합니다.

`GetBuffer` 요청을 충족 하는 데 필요한 메모리가 부족 한 경우이 메서드는 CMemoryException *을 throw 합니다.

### <a name="example"></a>예제

```cpp
CSimpleString s(_T("abcd"), pMgr);
LPTSTR pBuffer = s.GetBuffer(10);
int sizeOfBuffer = s.GetAllocLength();

// Directly access CSimpleString buffer
_tcscpy_s(pBuffer, sizeOfBuffer, _T("Hello"));
ASSERT(_tcscmp(s, _T("Hello")) == 0);
s.ReleaseBuffer();
```

##  <a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength

`CSimpleStringT` 개체의 내부 문자 버퍼에 대 한 포인터를 반환 하 고, 필요한 경우 *n 길이*에 지정 된 길이와 정확히 일치 하는 경우 해당 길이를 자르거나 증가 시킵니다.

### <a name="syntax"></a>구문

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>매개 변수

*nLength*<br/>
문자 버퍼의 정확한 크기 (문자 `CSimpleStringT`)입니다.

### <a name="return-value"></a>Return Value

개체의 (null로 끝나는) 문자 버퍼에 대 한 `PXSTR` 포인터입니다.

### <a name="remarks"></a>설명

`CSimpleStringT` 개체에 대 한 내부 버퍼의 지정 된 길이를 검색 하려면이 메서드를 호출 합니다. 반환 된 `PXSTR` 포인터는 **const** 가 아니므로 `CSimpleStringT` 콘텐츠를 직접 수정할 수 있습니다.

[GetBufferSetLength](#getbuffersetlength) 에서 반환 된 포인터를 사용 하 여 문자열 내용을 변경 하는 경우 다른 `CSimpleStringT` 메서드를 사용 하기 전에 `ReleaseBuffer`를 호출 하 여 `CsimpleStringT` 내부 상태를 업데이트 합니다.

`ReleaseBuffer`를 호출한 후에는 `GetBufferSetLength`에서 반환 된 주소가 유효 하지 않을 수 있습니다. 추가 `CSimpleStringT` 작업으로 인해 `CSimpleStringT` 버퍼가 다시 할당 될 수 있기 때문입니다. `CSimpleStringT`길이를 변경 하지 않으면 버퍼가 다시 할당 되지 않습니다.

버퍼 메모리는 `CSimpleStringT` 개체가 제거 될 때 자동으로 해제 됩니다.

문자열 길이를 직접 추적 하는 경우에는 종료 null 문자를 추가 하지 마세요. `ReleaseBuffer`를 사용 하 여 버퍼를 해제할 때 최종 문자열 길이를 지정 해야 합니다. `ReleaseBuffer`를 호출할 때 종료 null 문자를 추가 하는 경우 `ReleaseBuffer`길이에 대해-1 (기본값)을 전달 하 고 `ReleaseBuffer`는 버퍼에 대 한 `strlen`를 수행 하 여 해당 길이를 확인 합니다.

참조 횟수 계산에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- Windows SDK에서 [참조 횟수를 통해 개체 수명 관리](/windows/win32/com/managing-object-lifetimes-through-reference-counting)

- Windows SDK에서 [참조 계산을 구현](/windows/win32/com/implementing-reference-counting) 합니다.

- Windows SDK에서 [참조 횟수를 관리 하기 위한 규칙](/windows/win32/com/rules-for-managing-reference-counts) 입니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::GetBufferSetLength`의 사용법을 보여줍니다.

```cpp
CSimpleString str(pMgr);
LPTSTR pstr = str.GetBufferSetLength(3);
pstr[0] = _T('C');
pstr[1] = _T('u');
pstr[2] = _T('p');

// No need for trailing zero or call to ReleaseBuffer()
// because GetBufferSetLength() set it for us.

str += _T(" soccer is best!");
ASSERT(_tcscmp(str, _T("Cup soccer is best!")) == 0);
```

##  <a name="getlength"></a>CSimpleStringT:: GetLength

`CSimpleStringT` 개체의 문자 수를 반환 합니다.

### <a name="syntax"></a>구문

```
int GetLength() const throw();
```

### <a name="return-value"></a>Return Value

문자열에 있는 문자 수입니다.

### <a name="remarks"></a>설명

개체의 문자 수를 반환 하려면이 메서드를 호출 합니다. 개수는 null 종결자를 포함 하지 않습니다.

MBCS (멀티 바이트 문자 집합)의 경우 각 8 비트 문자를 계산 `GetLength` 합니다. 즉, 한 멀티 바이트 문자의 선행 및 후행 바이트는 2 바이트로 계산 됩니다. 이 함수를 호출 하는 예제는 [Freeextra](#freeextra) 를 참조 하세요.

##  <a name="getmanager"></a>CSimpleStringT:: GetManager

`CSimpleStringT` 개체의 메모리 관리자를 검색 합니다.

### <a name="syntax"></a>구문

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Return Value

`CSimpleStringT` 개체의 메모리 관리자에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`CSimpleStringT` 개체에서 사용 하는 메모리 관리자를 검색 하려면이 메서드를 호출 합니다. 메모리 관리자 및 문자열 개체에 대 한 자세한 내용은 [메모리 관리 및 CStringT](../memory-management-with-cstringt.md)를 참조 하십시오.

##  <a name="getstring"></a>CSimpleStringT:: GetString

문자열을 검색 합니다.

### <a name="syntax"></a>구문

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Return Value

Null로 끝나는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`CSimpleStringT` 개체와 연결 된 문자열을 검색 하려면이 메서드를 호출 합니다.

> [!NOTE]
>  반환 된 `PCXSTR` 포인터는 **const** 이며 `CSimpleStringT` 콘텐츠를 직접 수정할 수 없습니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::GetString`의 사용법을 보여줍니다.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

##  <a name="isempty"></a>CSimpleStringT:: IsEmpty

`CSimpleStringT` 개체에서 빈 조건을 테스트 합니다.

### <a name="syntax"></a>구문

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Return Value

`CSimpleStringT` 개체의 길이가 0 이면 TRUE를 반환 하 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

개체에 빈 문자열이 포함 되어 있는지 확인 하려면이 메서드를 호출 합니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::IsEmpty`의 사용법을 보여줍니다.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="lockbuffer"></a>CSimpleStringT:: LockBuffer

참조 횟수를 사용 하지 않도록 설정 하 고 버퍼의 문자열을 보호 합니다.

### <a name="syntax"></a>구문

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Return Value

`CSimpleStringT` 개체 또는 null로 끝나는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`CSimpleStringT` 개체의 버퍼를 잠그려면이 메서드를 호출 합니다. `LockBuffer`를 호출 하 여 참조 횟수에 대해-1을 사용 하 여 문자열의 복사본을 만듭니다. 참조 횟수 값이-1 인 경우 버퍼의 문자열은 "잠긴" 상태에 있는 것으로 간주 됩니다. 잠긴 상태에서 문자열은 다음 두 가지 방법으로 보호 됩니다.

- 해당 문자열이 잠긴 문자열에 할당 된 경우에도 다른 문자열은 잠긴 문자열에 있는 데이터에 대 한 참조를 가져올 수 없습니다.

- 다른 문자열을 잠긴 문자열로 복사 하더라도 잠긴 문자열은 다른 문자열을 참조 하지 않습니다.

버퍼에서 문자열을 잠그면 버퍼에 대 한 문자열의 단독 보류가 그대로 유지 됩니다.

`LockBuffer`완료 한 후 [Unlockbuffer](#unlockbuffer) 를 호출 하 여 참조 횟수를 1로 다시 설정 합니다.

> [!NOTE]
>  잠긴 버퍼에서 [Getbuffer](#getbuffer) 를 호출 하 고 `GetBuffer` 매개 변수 `nMinBufferLength`를 현재 버퍼의 길이 보다 큰 값으로 설정 하면 버퍼 잠금이 손실 됩니다. `GetBuffer`에 대 한 호출은 현재 버퍼를 소멸 시키고 요청한 크기의 버퍼로 바꾸고 참조 횟수를 0으로 다시 설정 합니다.

참조 횟수 계산에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- Windows SDK에서 [참조 횟수를 통해 개체 수명 관리](/windows/win32/com/managing-object-lifetimes-through-reference-counting)

- Windows SDK에서 [참조 계산 구현](/windows/win32/com/implementing-reference-counting)

- Windows SDK에서 [참조 횟수를 관리 하기 위한 규칙](/windows/win32/com/rules-for-managing-reference-counts)

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::LockBuffer`의 사용법을 보여줍니다.

```cpp
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```

##  <a name="operator_at"></a>CSimpleStringT:: operator\[\]

이 함수를 호출 하 여 문자 배열의 단일 문자에 액세스 합니다.

### <a name="syntax"></a>구문

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>매개 변수

*iChar*<br/>
문자열에 있는 문자의 0부터 시작 하는 인덱스입니다.

### <a name="remarks"></a>설명

오버 로드 된 첨자 ( **[]** ) 연산자는 *iChar*의 0부터 시작 하는 인덱스에 의해 지정 된 단일 문자를 반환 합니다. 이 연산자는 [GetAt](#getat) 멤버 함수를 편리 하 게 대체 합니다.

> [!NOTE]
>  첨자 ( **[]** ) 연산자를 사용 하 여 `CSimpleStringT`의 문자 값을 가져올 수 있지만이 연산자를 사용 하 여 `CSimpleStringT`의 문자 값을 변경할 수는 없습니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::operator []`의 사용법을 보여줍니다.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="operator_at"></a>CSimpleStringT:: operator \[\]

이 함수를 호출 하 여 문자 배열의 단일 문자에 액세스 합니다.

### <a name="syntax"></a>구문

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>매개 변수

*iChar*<br/>
문자열에 있는 문자의 0부터 시작 하는 인덱스입니다.

### <a name="remarks"></a>설명

오버 로드 된 첨자 ( **[]** ) 연산자는 *iChar*의 0부터 시작 하는 인덱스에 의해 지정 된 단일 문자를 반환 합니다. 이 연산자는 [GetAt](#getat) 멤버 함수를 편리 하 게 대체 합니다.

> [!NOTE]
>  첨자 ( **[]** ) 연산자를 사용 하 여 `CSimpleStringT`의 문자 값을 가져올 수 있지만이 연산자를 사용 하 여 `CSimpleStringT`의 문자 값을 변경할 수는 없습니다.

##  <a name="operator_add_eq"></a>CSimpleStringT:: operator + =

새 문자열 또는 문자를 기존 문자열의 끝에 조인 합니다.

### <a name="syntax"></a>구문

```
CSimpleStringT& operator +=(PCXSTR pszSrc);
CSimpleStringT& operator +=(const CSimpleStringT& strSrc);
template<int t_nSize>
CSimpleStringT& operator+=(const CStaticString< XCHAR, t_nSize >& strSrc);
CSimpleStringT& operator +=(char ch);
CSimpleStringT& operator +=(unsigned char ch);
CSimpleStringT& operator +=(wchar_t ch);
```

#### <a name="parameters"></a>매개 변수

*pszSrc*<br/>
Null로 끝나는 문자열에 대 한 포인터입니다.

*strSrc*<br/>
기존 `CSimpleStringT` 개체에 대 한 포인터입니다.

*ch*<br/>
추가할 문자입니다.

### <a name="remarks"></a>설명

연산자는 다른 `CSimpleStringT` 개체 또는 문자를 허용 합니다. 이 `CSimpleStringT` 개체에 추가 된 문자에 대해 새 저장소가 할당 될 수 있으므로이 연결 연산자를 사용할 때마다 메모리 예외가 발생할 수 있습니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::operator +=`의 사용법을 보여줍니다.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

##  <a name="operator_eq"></a>CSimpleStringT:: operator =

`CSimpleStringT` 개체에 새 값을 할당 합니다.

### <a name="syntax"></a>구문

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>매개 변수

*pszSrc*<br/>
Null로 끝나는 문자열에 대 한 포인터입니다.

*strSrc*<br/>
기존 `CSimpleStringT` 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

대상 문자열 (왼쪽)이 이미 새 데이터를 저장할 수 있을 만큼 크면 새 메모리 할당이 수행 되지 않습니다. 할당 연산자를 사용할 때마다 메모리 예외가 발생할 수 있습니다. 일반적으로 새 저장소는 결과 `CSimpleStringT` 개체를 저장 하기 위해 할당 됩니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::operator =`의 사용법을 보여줍니다.

```cpp
CSimpleString s1(pMgr), s2(pMgr);
// Empty CSimpleStringT objects

s1 = _T("cat");
// s1 = "cat"
ASSERT(_tcscmp(s1, _T("cat")) == 0);

s2 = s1;               // s1 and s2 each = "cat"
ASSERT(_tcscmp(s2, _T("cat")) == 0);

s1 = _T("the ") + s1;
// Or expressions
ASSERT(_tcscmp(s1, _T("the cat")) == 0);

s1 = _T("x");
// Or just individual characters
ASSERT(_tcscmp(s1, _T("x")) == 0);
```

##  <a name="operator_pcxstr"></a>CSimpleStringT:: operator PCXSTR

`CSimpleStringT` 개체에 저장 된 문자를 C 스타일 문자열로 직접 액세스 합니다.

### <a name="syntax"></a>구문

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Return Value

문자열 데이터에 대 한 문자 포인터입니다.

### <a name="remarks"></a>설명

문자는 복사 되지 않습니다. 포인터만 반환 됩니다. 이 연산자는 주의 해야 합니다. 문자 포인터를 가져온 후 `CString` 개체를 변경 하는 경우에는 포인터를 무효화 하는 메모리 재할당이 발생할 수 있습니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::operator PCXSTR`의 사용법을 보여줍니다.

```cpp
// If the prototype of a function is known to the compiler,
// the PCXSTR cast operator may be invoked implicitly.

CSimpleString strSports(L"Soccer is Best!", pMgr);
WCHAR sz[1024];

wcscpy_s(sz, strSports);

// If the prototype isn't known or is a va_arg prototype,
// you must invoke the cast operator explicitly. For example,
// the va_arg part of a call to swprintf_s() needs the cast:

swprintf_s(sz, 1024, L"I think that %s!\n", (PCWSTR)strSports);

// While the format parameter is known to be an PCXSTR and
// therefore doesn't need the cast:

swprintf_s(sz, 1024, strSports);

// Note that some situations are ambiguous. This line will
// put the address of the strSports object to stdout:

wcout << strSports;

// while this line will put the content of the string out:

wcout << (PCWSTR)strSports;
```

##  <a name="pcxstr"></a>CSimpleStringT::P CXSTR

상수 문자열에 대 한 포인터입니다.

### <a name="syntax"></a>구문

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

##  <a name="preallocate"></a>CSimpleStringT::P 다시 할당

`CSimpleStringT` 개체에 대 한 특정 바이트 크기를 할당 합니다.

### <a name="syntax"></a>구문

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>매개 변수

*nLength*<br/>
문자 버퍼의 정확한 크기 (문자 `CSimpleStringT`)입니다.

### <a name="remarks"></a>설명

`CSimpleStringT` 개체에 대 한 특정 버퍼 크기를 할당 하려면이 메서드를 호출 합니다.

문자 버퍼에 대 한 공간을 할당할 수 없는 경우 `CSimpleStringT`에서 STATUS_NO_MEMORY 예외를 생성 합니다. 기본적으로 메모리 할당은 `HeapAlloc` 또는 `HeapReAlloc`WIN32 API 함수에 의해 수행 됩니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::Preallocate`의 사용법을 보여줍니다.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

##  <a name="pxstr"></a>CSimpleStringT::P XSTR

문자열에 대 한 포인터입니다.

### <a name="syntax"></a>구문

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

##  <a name="releasebuffer"></a>CSimpleStringT:: ReleaseBuffer

[Getbuffer](#getbuffer)에서 할당 한 버퍼의 제어를 해제 합니다.

### <a name="syntax"></a>구문

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>매개 변수

*nNewLength*<br/>
Null 종결자를 제외 하 고 문자 수로 표시 되는 문자열의 새 길이입니다. 문자열이 null로 종료 되는 경우-1 기본값은 `CSimpleStringT` 크기를 문자열의 현재 길이로 설정 합니다.

### <a name="remarks"></a>설명

문자열 개체의 버퍼를 다시 할당 하거나 해제 하려면이 메서드를 호출 합니다. 버퍼의 문자열이 null로 종료 된 것을 알고 있으면 *Nnewlength* 인수를 생략할 수 있습니다. 문자열이 null로 종료 되지 않은 경우에는 *Nnewlength* 를 사용 하 여 길이를 지정 합니다. `ReleaseBuffer`를 호출한 후 또는 다른 `CSimpleStringT` 작업을 호출한 후 [Getbuffer](#getbuffer) 에서 반환 된 주소가 잘못 되었습니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::ReleaseBuffer`의 사용법을 보여줍니다.

```cpp
const int bufferSize = 1024;
CSimpleString s(_T("abc"), pMgr);
LPTSTR p = s.GetBuffer(bufferSize);
_tcscpy_s(p, bufferSize, _T("abc"));

// use the buffer directly
ASSERT(s.GetLength() == 3);

// String length = 3
s.ReleaseBuffer();

// Surplus memory released, p is now invalid.
ASSERT(s.GetLength() == 3);

// Length still 3
```

##  <a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

[Getbuffer](#getbuffer)에서 할당 한 버퍼의 제어를 해제 합니다.

### <a name="syntax"></a>구문

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>매개 변수

*nNewLength*<br/>
해제 되는 문자열의 길이입니다.

### <a name="remarks"></a>설명

이 함수는 string 개체에 대 한 올바른 길이를 전달 해야 한다는 점을 제외 하 고 [Releasebuffer](#releasebuffer) 와 기능적으로 비슷합니다.

##  <a name="setat"></a>CSimpleStringT:: SetAt

`CSimpleStringT` 개체에서 단일 문자를 설정 합니다.

### <a name="syntax"></a>구문

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>매개 변수

*iChar*<br/>
`CSimpleStringT` 개체에 있는 문자의 0부터 시작 하는 인덱스입니다. *IChar* 매개 변수는 0 보다 크거나 같고 [getlength](#getlength)에서 반환 된 값 보다 작아야 합니다.

*ch*<br/>
새 문자입니다.

### <a name="remarks"></a>설명

*IChar*에 있는 문자를 덮어쓰려면이 메서드를 호출 합니다. *IChar* 가 기존 문자열의 범위를 초과 하는 경우이 메서드는 문자열을 확대 하지 않습니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::SetAt`의 사용법을 보여줍니다.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

##  <a name="setmanager"></a>CSimpleStringT:: SetManager

`CSimpleStringT` 개체의 메모리 관리자를 지정 합니다.

### <a name="syntax"></a>구문

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>매개 변수

*pStringMgr*<br/>
새 메모리 관리자에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`CSimpleStringT` 개체에서 사용 하는 새 메모리 관리자를 지정 하려면이 메서드를 호출 합니다. 메모리 관리자 및 문자열 개체에 대 한 자세한 내용은 [메모리 관리 및 CStringT](../memory-management-with-cstringt.md)를 참조 하십시오.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::SetManager`의 사용법을 보여줍니다.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

##  <a name="setstring"></a>CSimpleStringT:: SetString

`CSimpleStringT` 개체의 문자열을 설정 합니다.

### <a name="syntax"></a>구문

```
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>매개 변수

*pszSrc*<br/>
Null로 끝나는 문자열에 대 한 포인터입니다.

*nLength*<br/>
*PszSrc*의 문자 수입니다.

### <a name="remarks"></a>설명

`CSimpleStringT` 개체에 문자열을 복사 합니다. `SetString`는 버퍼의 이전 문자열 데이터를 덮어씁니다.

두 버전 `SetString`의 모두 *pszSrc* 이 null 포인터 인지 여부를 확인 하 고, 있는 경우 E_INVALIDARG 오류를 throw 합니다.

`SetString`의 단일 매개 변수 버전은 null로 끝나는 문자열을 *pszSrc* 하는 것으로 예상 합니다.

`SetString`의 두 매개 변수 버전에는 null로 끝나는 문자열을 *pszSrc* 하는 것도 필요 합니다. Null 종결자를 먼저 발견 하지 않는 한 문자열 길이로 *Nlength* 를 사용 합니다.

`SetString`의 두 매개 변수 버전은 *pszSrc* 가 `CSimpleStringT`에서 현재 버퍼의 위치를 가리키는지 여부도 확인 합니다. 이 특수 한 경우에 `SetString`는 문자열 데이터를 버퍼에 다시 복사할 때 문자열 데이터를 덮어쓰지 않는 메모리 복사 함수를 사용 합니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::SetString`의 사용법을 보여줍니다.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

##  <a name="stringlength"></a>CSimpleStringT:: StringLength

지정 된 문자열의 문자 수를 반환 합니다.

### <a name="syntax"></a>구문

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>매개 변수

*psz*<br/>
Null로 끝나는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>Return Value

*Psz*의 문자 수입니다. null 종결자를 계산 하지 않습니다.

### <a name="remarks"></a>설명

*Psz*가 가리키는 문자열의 문자 수를 검색 하려면이 메서드를 호출 합니다.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::StringLength`의 사용법을 보여줍니다.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

##  <a name="truncate"></a>CSimpleStringT:: Truncate

문자열을 새 길이로 자릅니다.

### <a name="syntax"></a>구문

```
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>매개 변수

*nNewLength*<br/>
문자열의 새 길이입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 문자열의 내용을 새 길이로 자릅니다.

> [!NOTE]
>  할당 된 버퍼 길이에는 영향을 주지 않습니다. 현재 버퍼를 줄이거나 늘리려면 [Freeextra](#freeextra) 및 사전 [할당](#preallocate)을 참조 하세요.

### <a name="example"></a>예제

다음 예에서는 `CSimpleStringT::Truncate`의 사용법을 보여줍니다.

```cpp
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
```

##  <a name="unlockbuffer"></a>CSimpleStringT:: UnlockBuffer

`CSimpleStringT` 개체의 버퍼 잠금을 해제 합니다.

### <a name="syntax"></a>구문

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>설명

문자열의 참조 횟수를 1로 다시 설정 하려면이 메서드를 호출 합니다.

`CSimpleStringT` 소멸자는 `UnlockBuffer`를 자동으로 호출 하 여 소멸자가 호출 될 때 버퍼가 잠기지 않도록 합니다. 이 메서드에 대 한 예제는 [Lockbuffer](#lockbuffer)를 참조 하세요.

##  <a name="dtor"></a>CSimpleStringT:: ~ CSimpleStringT

`CSimpleStringT` 개체를 제거합니다.

### <a name="syntax"></a>구문

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>설명

`CSimpleStringT` 개체를 삭제 하려면이 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)
