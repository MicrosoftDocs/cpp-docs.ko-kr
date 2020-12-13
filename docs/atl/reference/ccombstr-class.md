---
description: '자세히 알아보기: CComBSTR 클래스'
title: CComBSTR 클래스
ms.date: 11/04/2016
f1_keywords:
- CComBSTR
- ATLBASE/ATL::CComBSTR
- ATLBASE/ATL::CComBSTR::CComBSTR
- ATLBASE/ATL::CComBSTR::Append
- ATLBASE/ATL::CComBSTR::AppendBSTR
- ATLBASE/ATL::CComBSTR::AppendBytes
- ATLBASE/ATL::CComBSTR::ArrayToBSTR
- ATLBASE/ATL::CComBSTR::AssignBSTR
- ATLBASE/ATL::CComBSTR::Attach
- ATLBASE/ATL::CComBSTR::BSTRToArray
- ATLBASE/ATL::CComBSTR::ByteLength
- ATLBASE/ATL::CComBSTR::Copy
- ATLBASE/ATL::CComBSTR::CopyTo
- ATLBASE/ATL::CComBSTR::Detach
- ATLBASE/ATL::CComBSTR::Empty
- ATLBASE/ATL::CComBSTR::Length
- ATLBASE/ATL::CComBSTR::LoadString
- ATLBASE/ATL::CComBSTR::ReadFromStream
- ATLBASE/ATL::CComBSTR::ToLower
- ATLBASE/ATL::CComBSTR::ToUpper
- ATLBASE/ATL::CComBSTR::WriteToStream
- ATLBASE/ATL::CComBSTR::m_str
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
ms.openlocfilehash: 1ddb830846747f0e3efe36f02be07ce1a45b353e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152310"
---
# <a name="ccombstr-class"></a>CComBSTR 클래스

이 클래스는 [BSTR](/previous-versions/windows/desktop/automat/bstr)s에 대 한 래퍼입니다.

## <a name="syntax"></a>구문

```
class CComBSTR
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComBSTR:: CComBSTR](#ccombstr)|생성자입니다.|
|[CComBSTR:: ~ CComBSTR](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComBSTR:: Append](#append)|에 문자열을 추가 `m_str` 합니다.|
|[CComBSTR:: AppendBSTR](#appendbstr)|BSTR을에 추가 `m_str` 합니다.|
|[CComBSTR:: AppendBytes](#appendbytes)|에 지정 된 바이트 수를 추가 `m_str` 합니다.|
|[CComBSTR:: ArrayToBSTR](#arraytobstr)|Safearray의 각 요소에 대 한 첫 번째 문자에서 BSTR을 만들고 개체에 연결 `CComBSTR` 합니다.|
|[CComBSTR:: 할당 Bstr](#assignbstr)|BSTR를에 할당 `m_str` 합니다.|
|[CComBSTR:: Attach](#attach)|BSTR을 개체에 연결 `CComBSTR` 합니다.|
|[CComBSTR:: BSTRToArray](#bstrtoarray)|배열의 각 요소가 개체의 문자인 0부터 시작 하는 1 차원 safearray를 만듭니다 `CComBSTR` .|
|[CComBSTR:: By-](#bytelength)|의 길이 `m_str` (바이트)를 반환 합니다.|
|[CComBSTR:: Copy](#copy)|의 복사본을 반환 `m_str` 합니다.|
|[CComBSTR:: CopyTo](#copyto)|`m_str` **[Out]** 매개 변수를 통해의 복사본을 반환 합니다.|
|[CComBSTR::D etach](#detach)|`m_str`개체에서 분리 `CComBSTR` 합니다.|
|[CComBSTR:: Empty](#empty)|해제 `m_str` 합니다.|
|[CComBSTR:: Length](#length)|의 길이를 반환 `m_str` 합니다.|
|[CComBSTR:: LoadString](#loadstring)|문자열 리소스를 로드 합니다.|
|[CComBSTR:: ReadFromStream](#readfromstream)|스트림에서 BSTR 개체를 로드 합니다.|
|[CComBSTR:: ToLower](#tolower)|문자열을 소문자로 변환 합니다.|
|[CComBSTR:: ToUpper](#toupper)|문자열을 대문자로 변환 합니다.|
|[CComBSTR:: WriteToStream](#writetostream)|`m_str`을 스트림에 저장 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CComBSTR:: operator BSTR](#operator_bstr)|개체를 `CComBSTR` BSTR로 캐스팅 합니다.|
|[CComBSTR:: operator!](#operator_not)|가 NULL 인지 여부에 따라 TRUE 또는 FALSE를 반환 `m_str` 합니다.|
|[CComBSTR:: operator! =](#operator_neq)|을 `CComBSTR` 문자열과 비교 합니다.|
|[CComBSTR:: operator &](#operator_amp)|의 주소를 반환 `m_str` 합니다.|
|[CComBSTR:: operator + =](#operator_add_eq)|`CComBSTR`개체에를 추가 합니다.|
|[CComBSTR:: operator <](#operator_lt)|을 `CComBSTR` 문자열과 비교 합니다.|
|[CComBSTR:: operator =](#operator_eq)|에 값을 할당 `m_str` 합니다.|
|[CComBSTR:: operator = =](#operator_eq_eq)|을 `CComBSTR` 문자열과 비교 합니다.|
|[CComBSTR:: operator >](#operator_gt)|을 `CComBSTR` 문자열과 비교 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComBSTR:: m_str](#m_str)|개체와 연결 된 BSTR을 포함 `CComBSTR` 합니다.|

## <a name="remarks"></a>설명

`CComBSTR`클래스는 길이 접두사가 있는 문자열인 bstr의 래퍼입니다. 길이는 문자열에 있는 데이터 앞의 메모리 위치에 정수로 저장 됩니다.

[BSTR](/previous-versions/windows/desktop/automat/bstr) 은 null로 계산 되는 마지막 문자 뒤에 null로 종료 되지만 문자열 내에 null 문자가 포함 될 수도 있습니다. 문자열 길이는 첫 번째 null 문자가 아닌 문자 수에 따라 결정 됩니다.

> [!NOTE]
> `CComBSTR`클래스는 ANSI 또는 유니코드 문자열을 인수로 사용 하는 다양 한 멤버 (생성자, 할당 연산자 및 비교 연산자)를 제공 합니다. 임시 유니코드 문자열이 내부적으로 생성 되는 경우가 많으므로 이러한 함수의 ANSI 버전은 유니코드 항목 보다 효율성이 떨어집니다. 효율성을 위해 가능한 경우 유니코드 버전을 사용 합니다.

> [!NOTE]
> Visual Studio .NET에서 구현 된 향상 된 조회 동작 때문에 `bstr = L"String2" + bstr;` 이전 릴리스에서 컴파일될 수 있는와 같은 코드는 대신로 구현 해야 합니다 `bstr = CStringW(L"String2") + bstr` .

을 사용 하는 경우의 주의 사항 목록은 `CComBSTR` [CComBSTR을 사용한 프로그래밍](../../atl/programming-with-ccombstr-atl.md)을 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="ccombstrappend"></a><a name="append"></a> CComBSTR:: Append

*BstrSrc* 의 *LPSZ* 또는 BSTR 멤버를 추가 하 여 [m_str](#m_str)합니다.

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>매개 변수

*bstrSrc*<br/>
진행 `CComBSTR` 추가할 개체입니다.

*ch*<br/>
진행 추가할 문자입니다.

*lpsz*<br/>
진행 추가할 0으로 끝나는 문자열입니다. LPCOLESTR 오버 로드 또는 LPCSTR 버전을 통해 ANSI 문자열을 통해 유니코드 문자열을 전달할 수 있습니다.

*nLen*<br/>
진행 *Lpsz* 에서 추가할 문자 수입니다.

### <a name="return-value"></a>반환 값

성공 하거나 표준 HRESULT 오류 값을 S_OK 합니다.

### <a name="remarks"></a>설명

ANSI 문자열은 추가 되기 전에 유니코드로 변환 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

## <a name="ccombstrappendbstr"></a><a name="appendbstr"></a> CComBSTR:: AppendBSTR

[M_str](#m_str)에 지정 된 BSTR을 추가 합니다.

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>매개 변수

*®*<br/>
진행 추가할 BSTR입니다.

### <a name="return-value"></a>반환 값

성공 하거나 표준 HRESULT 오류 값을 S_OK 합니다.

### <a name="remarks"></a>설명

일반 와이드 문자열을이 메서드에 전달 하지 마십시오. 컴파일러가 오류를 catch 할 수 없고 런타임 오류가 발생 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

## <a name="ccombstrappendbytes"></a><a name="appendbytes"></a> CComBSTR:: AppendBytes

변환 하지 않고 [m_str](#m_str) 에 지정 된 바이트 수를 추가 합니다.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>매개 변수

*lpsz*<br/>
진행 추가할 바이트 배열에 대 한 포인터입니다.

*®*<br/>
진행 추가할 바이트 수입니다.

### <a name="return-value"></a>반환 값

성공 하거나 표준 HRESULT 오류 값을 S_OK 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

## <a name="ccombstrarraytobstr"></a><a name="arraytobstr"></a> CComBSTR:: ArrayToBSTR

개체에 들어 있는 모든 기존 문자열 `CComBSTR` 을 해제 한 다음 safearray의 각 요소에 대 한 첫 번째 문자에서 BSTR을 만들고 개체에 연결 `CComBSTR` 합니다.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>매개 변수

*.Psrc*<br/>
진행 문자열을 만드는 데 사용 되는 요소를 포함 하는 safearray입니다.

### <a name="return-value"></a>반환 값

성공 하거나 표준 HRESULT 오류 값을 S_OK 합니다.

## <a name="ccombstrassignbstr"></a><a name="assignbstr"></a> CComBSTR:: 할당 Bstr

[M_str](#m_str)에 BSTR을 할당 합니다.

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>매개 변수

*bstrSrc*<br/>
진행 현재 개체에 할당할 BSTR `CComBSTR` 입니다.

### <a name="return-value"></a>반환 값

성공 하거나 표준 HRESULT 오류 값을 S_OK 합니다.

## <a name="ccombstrattach"></a><a name="attach"></a> CComBSTR:: Attach

`CComBSTR` [M_str](#m_str) 멤버를 *src* 로 설정 하 여 BSTR을 개체에 연결 합니다.

```cpp
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>매개 변수

*src*<br/>
진행 개체에 연결할 BSTR입니다.

### <a name="remarks"></a>설명

일반 와이드 문자열을이 메서드에 전달 하지 마십시오. 컴파일러가 오류를 catch 할 수 없고 런타임 오류가 발생 합니다.

> [!NOTE]
> 가 NULL이 아닌 경우이 메서드는 `m_str` 를 어설션 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstrbstrtoarray"></a><a name="bstrtoarray"></a> CComBSTR:: BSTRToArray

배열의 각 요소가 개체의 문자인 0부터 시작 하는 1 차원 safearray를 만듭니다 `CComBSTR` .

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>매개 변수

*ppArray*<br/>
제한이 함수의 결과를 저장 하는 데 사용 되는 safearray에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하거나 표준 HRESULT 오류 값을 S_OK 합니다.

## <a name="ccombstrbytelength"></a><a name="bytelength"></a> CComBSTR:: By-

는 종료 null 문자를 제외 하 고의 바이트 수를 반환 `m_str` 합니다.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>반환 값

[M_str](#m_str) 멤버의 길이 (바이트)입니다.

### <a name="remarks"></a>설명

가 NULL 인 경우 0 `m_str` 을 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

## <a name="ccombstrccombstr"></a><a name="ccombstr"></a> CComBSTR:: CComBSTR

생성자입니다. 기본 생성자는 [m_str](#m_str) 멤버를 NULL로 설정 합니다.

```
CComBSTR() throw();
CComBSTR(const CComBSTR& src);
CComBSTR(REFGUID  guid);
CComBSTR(int nSize);
CComBSTR(int nSize, LPCOLESTR sz);
CComBSTR(int nSize, LPCSTR sz);
CComBSTR(LPCOLESTR pSrc);
CComBSTR(LPCSTR pSrc);
CComBSTR(CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="parameters"></a>매개 변수

*nSize*<br/>
진행 *Sz* 에서 복사할 문자 수 또는의 처음 크기 (문자 수) `CComBSTR` 입니다.

*sz*<br/>
[in] 복사할 문자열입니다. 유니코드 버전은 LPCOLESTR을 지정 합니다. ANSI 버전은 LPCSTR을 지정 합니다.

*.Psrc*<br/>
[in] 복사할 문자열입니다. 유니코드 버전은 LPCOLESTR을 지정 합니다. ANSI 버전은 LPCSTR을 지정 합니다.

*src*<br/>
[in] `CComBSTR` 개체입니다.

*guid*<br/>
진행 구조체에 대 한 참조 `GUID` 입니다.

### <a name="remarks"></a>설명

복사 생성자는 `m_str` *SRC* 의 BSTR 멤버 복사본으로 설정 합니다. 생성자는를 `REFGUID` 사용 하 여 GUID를 문자열로 변환 하 `StringFromGUID2` 고 결과를 저장 합니다.

다른 생성자는 `m_str`을 지정된 문자열의 복사본으로 설정합니다. *NSize* 에 대 한 값을 전달 하면 *nSize* 문자만 복사 된 다음 종료 null 문자가 됩니다.

`CComBSTR`은 이동 의미 체계를 지원합니다. 이동 생성자(rvalue 참조(`&&`)를 가져오는 생성자)를 사용하면 개체 복사에 대한 오버헤드 없이 인수로 전달한 이전 개체와 동일한 기본 데이터를 사용하는 새 개체를 만들 수 있습니다.

소멸자는 `m_str`에서 가리키는 문자열을 해제합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

## <a name="ccombstrccombstr"></a><a name="dtor"></a> CComBSTR:: ~ CComBSTR

소멸자입니다.

```
~CComBSTR();
```

### <a name="remarks"></a>설명

소멸자는 `m_str`에서 가리키는 문자열을 해제합니다.

## <a name="ccombstrcopy"></a><a name="copy"></a> CComBSTR:: Copy

의 복사본을 할당 하 고 반환 `m_str` 합니다.

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>반환 값

[M_str](#m_str) 멤버의 복사본입니다. `m_str`가 null 이면 null을 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

## <a name="ccombstrcopyto"></a><a name="copyto"></a> CComBSTR:: CopyTo

매개 변수를 통해 [m_str](#m_str) 의 복사본을 할당 하 고 반환 합니다.

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>매개 변수

*pbstr*<br/>
제한이 이 메서드에 의해 할당 된 문자열을 반환할 BSTR의 주소입니다.

*pvarDest*<br/>
제한이 이 메서드에 의해 할당 된 문자열을 반환할 VARIANT의 주소입니다.

### <a name="return-value"></a>반환 값

복사의 성공 또는 실패를 나타내는 표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

이 메서드를 호출한 후 *Pvardest* 가 가리키는 변형은 VT_BSTR 형식이 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

## <a name="ccombstrdetach"></a><a name="detach"></a> CComBSTR::D etach

개체에서 [m_str](#m_str) 를 분리 하 `CComBSTR` 고 `m_str` 를 NULL로 설정 합니다.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>반환 값

개체와 연결 된 BSTR `CComBSTR` 입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

## <a name="ccombstrempty"></a><a name="empty"></a> CComBSTR:: Empty

[M_str](#m_str) 멤버를 해제 합니다.

```cpp
void Empty() throw();
```

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

## <a name="ccombstrlength"></a><a name="length"></a> CComBSTR:: Length

는 종료 null 문자를 제외 하 고의 문자 수를 반환 `m_str` 합니다.

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>반환 값

[M_str](#m_str) 멤버의 길이입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

## <a name="ccombstrloadstring"></a><a name="loadstring"></a> CComBSTR:: LoadString

*NID* 로 지정 된 문자열 리소스를 로드 하 여이 개체에 저장 합니다.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>매개 변수

Windows SDK [Loadstring](/windows/win32/api/winuser/nf-winuser-loadstringw) 을 참조 하십시오.

### <a name="return-value"></a>반환 값

문자열이 성공적으로 로드 되 면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

첫 번째 함수는 *hInst* 매개 변수를 통해 식별 된 모듈에서 리소스를 로드 합니다. 두 번째 함수는이 프로젝트에서 사용 되는 [CComModule](../../atl/reference/ccommodule-class.md)파생 개체와 연결 된 리소스 모듈에서 리소스를 로드 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

## <a name="ccombstrm_str"></a><a name="m_str"></a> CComBSTR:: m_str

개체와 연결 된 BSTR을 포함 `CComBSTR` 합니다.

```
BSTR m_str;
```

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

## <a name="ccombstroperator-bstr"></a><a name="operator_bstr"></a> CComBSTR:: operator BSTR

개체를 `CComBSTR` BSTR로 캐스팅 합니다.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>설명

`CComBSTR` **[IN] BSTR** 매개 변수가 있는 함수에 개체를 전달할 수 있습니다.

### <a name="example"></a>예제

[CComBSTR:: m_str](#m_str)의 예제를 참조 하세요.

## <a name="ccombstroperator-"></a><a name="operator_not"></a> CComBSTR:: operator!

BSTR 문자열이 NULL 인지 여부를 확인 합니다.

```
bool operator!() const throw();
```

### <a name="return-value"></a>반환 값

[M_str](#m_str) 멤버가 NULL 이면 TRUE를 반환 하 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 연산자는 빈 문자열이 아닌 NULL 값을 확인 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_neq"></a> CComBSTR:: operator! =

[= = 연산자](#operator_eq_eq)의 논리적 반대를 반환 합니다.

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>매개 변수

*bstrSrc*<br/>
[in] `CComBSTR` 개체입니다.

*pszSrc*<br/>
진행 0으로 끝나는 문자열입니다.

*아님*<br/>
진행 NULL 이어야 합니다.

### <a name="return-value"></a>반환 값

비교할 항목이 개체와 같지 않으면 TRUE를 반환 하 고 `CComBSTR` , 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

`CComBSTR`는 사용자의 기본 로캘 컨텍스트에서와 비교 됩니다. 최종 비교 연산자는 포함 된 문자열을 NULL과 비교 합니다.

## <a name="ccombstroperator-amp"></a><a name="operator_amp"></a> CComBSTR:: operator &amp;

[M_str](#m_str) 멤버에 저장 된 BSTR의 주소를 반환 합니다.

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>설명

`CComBstr operator &` 에는 메모리 누수를 식별 하는 데 도움이 되는 특수 어설션이 연결 되어 있습니다. 멤버를 초기화할 때 프로그램에서을 어설션 `m_str` 합니다. 이 어설션은 프로그래머가를 사용 하 여 `& operator` `m_str` 의 첫 번째 할당을 해제 하지 않고 멤버에 새 값을 할당 하는 경우를 식별 하기 위해 만들어졌습니다 `m_str` . 가 `m_str` NULL 인 경우 프로그램은 m_str 아직 할당 되지 않은 것으로 가정 합니다. 이 경우 프로그램은를 어설션 하지 않습니다.

이 어설션은 기본적으로 사용 하도록 설정 되어 있지 않습니다. 이 어설션을 사용 하도록 설정 하려면 ATL_CCOMBSTR_ADDRESS_OF_ASSERT를 정의 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_add_eq"></a> CComBSTR:: operator + =

개체에 문자열을 추가 `CComBSTR` 합니다.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>매개 변수

*bstrSrc*<br/>
진행 `CComBSTR` 추가할 개체입니다.

*pszSrc*<br/>
진행 추가할 0으로 끝나는 문자열입니다.

### <a name="remarks"></a>설명

`CComBSTR`는 사용자의 기본 로캘 컨텍스트에서와 비교 됩니다. LPCOLESTR 비교는 `memcmp` 각 문자열의 원시 데이터를 사용 하 여 수행 됩니다. LPCSTR 비교는 *pszSrc* 의 임시 유니코드 복사본이 생성 된 후와 동일한 방법으로 수행 됩니다. 최종 비교 연산자는 포함 된 문자열을 NULL과 비교 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

## <a name="ccombstroperator-lt"></a><a name="operator_lt"></a> CComBSTR:: operator &lt;

을 `CComBSTR` 문자열과 비교 합니다.

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>반환 값

비교할 항목이 개체 보다 작은 경우 TRUE를 반환 하 고 `CComBSTR` , 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

사용자의 기본 로캘을 사용 하 여 비교가 수행 됩니다.

## <a name="ccombstroperator-"></a><a name="operator_eq"></a> CComBSTR:: operator =

[M_str](#m_str) 멤버를 *psrc* 의 복사본 또는 *src* 의 BSTR 멤버 복사본으로 설정 합니다. 이동 할당 연산자는 `src` 복사 하지 않고 이동 합니다.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>설명

*Psrc* 매개 변수는 유니코드 버전에 대 한 LPCOLESTR 또는 ANSI 버전용 lpcstr을 지정 합니다.

### <a name="example"></a>예제

[CComBSTR:: Copy](#copy)의 예제를 참조 하세요.

## <a name="ccombstroperator-"></a><a name="operator_eq_eq"></a> CComBSTR:: operator = =

을 `CComBSTR` 문자열과 비교 합니다. `CComBSTR`는 사용자의 기본 로캘 컨텍스트에서와 비교 됩니다.

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>매개 변수

*bstrSrc*<br/>
[in] `CComBSTR` 개체입니다.

*pszSrc*<br/>
진행 0으로 끝나는 문자열입니다.

*아님*<br/>
진행 NULL 이어야 합니다.

### <a name="return-value"></a>반환 값

비교할 항목이 개체와 같으면 TRUE `CComBSTR` 이 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

최종 비교 연산자는 포함 된 문자열을 NULL과 비교 합니다.

## <a name="ccombstroperator-gt"></a><a name="operator_gt"></a> CComBSTR:: operator &gt;

을 `CComBSTR` 문자열과 비교 합니다.

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>반환 값

비교할 항목이 개체 보다 크면 TRUE를 반환 하 고 `CComBSTR` , 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

사용자의 기본 로캘을 사용 하 여 비교가 수행 됩니다.

## <a name="ccombstrreadfromstream"></a><a name="readfromstream"></a> CComBSTR:: ReadFromStream

[M_str](#m_str) 멤버를 지정 된 스트림에 포함 된 BSTR로 설정 합니다.

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>매개 변수

*pStream*<br/>
진행 데이터를 포함 하는 스트림의 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

`ReadToStream`[WriteToStream](#writetostream)를 호출 하 여 작성 한 데이터 형식과 호환 되도록 현재 위치의 스트림 콘텐츠가 필요 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

## <a name="ccombstrtolower"></a><a name="tolower"></a> CComBSTR:: ToLower

포함 된 문자열을 소문자로 변환 합니다.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

`CharLowerBuff`변환을 수행 하는 방법에 대 한 자세한 내용은을 참조 하십시오.

## <a name="ccombstrtoupper"></a><a name="toupper"></a> CComBSTR:: ToUpper

포함 된 문자열을 대문자로 변환 합니다.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

`CharUpperBuff`변환을 수행 하는 방법에 대 한 자세한 내용은을 참조 하십시오.

## <a name="ccombstrwritetostream"></a><a name="writetostream"></a> CComBSTR:: WriteToStream

[M_str](#m_str) 멤버를 스트림에 저장 합니다.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>매개 변수

*pStream*<br/>
진행 스트림의 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

[Readfromstream](#readfromstream) 함수를 사용 하 여 스트림의 콘텐츠에서 BSTR을 다시 만들 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)<br/>
[ATL 및 MFC 문자열 변환 매크로](string-conversion-macros.md)
