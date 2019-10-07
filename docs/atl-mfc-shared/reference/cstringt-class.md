---
title: CStringT 클래스
ms.date: 03/27/2019
f1_keywords:
- CStringT
- ATLSTR/ATL::CStringT
- ATLSTR/ATL::CStringT::CStringT
- ATLSTR/ATL::CStringT::AllocSysString
- ATLSTR/ATL::CStringT::AnsiToOem
- ATLSTR/ATL::CStringT::AppendFormat
- ATLSTR/ATL::CStringT::Collate
- ATLSTR/ATL::CStringT::CollateNoCase
- ATLSTR/ATL::CStringT::Compare
- ATLSTR/ATL::CStringT::CompareNoCase
- ATLSTR/ATL::CStringT::Delete
- ATLSTR/ATL::CStringT::Find
- ATLSTR/ATL::CStringT::FindOneOf
- ATLSTR/ATL::CStringT::Format
- ATLSTR/ATL::CStringT::FormatMessage
- ATLSTR/ATL::CStringT::FormatMessageV
- ATLSTR/ATL::CStringT::FormatV
- ATLSTR/ATL::CStringT::GetEnvironmentVariable
- ATLSTR/ATL::CStringT::Insert
- ATLSTR/ATL::CStringT::Left
- ATLSTR/ATL::CStringT::LoadString
- ATLSTR/ATL::CStringT::MakeLower
- ATLSTR/ATL::CStringT::MakeReverse
- ATLSTR/ATL::CStringT::MakeUpper
- ATLSTR/ATL::CStringT::Mid
- ATLSTR/ATL::CStringT::OemToAnsi
- ATLSTR/ATL::CStringT::Remove
- ATLSTR/ATL::CStringT::Replace
- ATLSTR/ATL::CStringT::ReverseFind
- ATLSTR/ATL::CStringT::Right
- ATLSTR/ATL::CStringT::SetSysString
- ATLSTR/ATL::CStringT::SpanExcluding
- ATLSTR/ATL::CStringT::SpanIncluding
- ATLSTR/ATL::CStringT::Tokenize
- ATLSTR/ATL::CStringT::Trim
- ATLSTR/ATL::CStringT::TrimLeft
- ATLSTR/ATL::CStringT::TrimRight
- CSTRINGT/CStringT
- CSTRINGT/CStringT::CStringT
- CSTRINGT/CStringT::AllocSysString
- CSTRINGT/CStringT::AnsiToOem
- CSTRINGT/CStringT::AppendFormat
- CSTRINGT/CStringT::Collate
- CSTRINGT/CStringT::CollateNoCase
- CSTRINGT/CStringT::Compare
- CSTRINGT/CStringT::CompareNoCase
- CSTRINGT/CStringT::Delete
- CSTRINGT/CStringT::Find
- CSTRINGT/CStringT::FindOneOf
- CSTRINGT/CStringT::Format
- CSTRINGT/CStringT::FormatMessage
- CSTRINGT/CStringT::FormatMessageV
- CSTRINGT/CStringT::FormatV
- CSTRINGT/CStringT::GetEnvironmentVariable
- CSTRINGT/CStringT::Insert
- CSTRINGT/CStringT::Left
- CSTRINGT/CStringT::LoadString
- CSTRINGT/CStringT::MakeLower
- CSTRINGT/CStringT::MakeReverse
- CSTRINGT/CStringT::MakeUpper
- CSTRINGT/CStringT::Mid
- CSTRINGT/CStringT::OemToAnsi
- CSTRINGT/CStringT::Remove
- CSTRINGT/CStringT::Replace
- CSTRINGT/CStringT::ReverseFind
- CSTRINGT/CStringT::Right
- CSTRINGT/CStringT::SetSysString
- CSTRINGT/CStringT::SpanExcluding
- CSTRINGT/CStringT::SpanIncluding
- CSTRINGT/CStringT::Tokenize
- CSTRINGT/CStringT::Trim
- CSTRINGT/CStringT::TrimLeft
- CSTRINGT/CStringT::TrimRight
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
ms.openlocfilehash: a411ed54a73a0dee49ebbd9ccacbd7c6f8e69ca5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491635"
---
# <a name="cstringt-class"></a>CStringT 클래스

이 클래스는 개체 `CStringT` 를 나타냅니다.

## <a name="syntax"></a>구문

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>매개 변수

*BaseType*<br/>
문자열 클래스의 문자 형식입니다. 다음 중 하나일 수 있습니다.

- **char** (ANSI 문자열의 경우).

- **wchar_t** (유니코드 문자열의 경우).

- TCHAR.H (ANSI 및 유니코드 문자열 모두)

*StringTraits*<br/>
문자열 클래스에 CRT (C 런타임) 라이브러리를 지원 해야 하 고 문자열 리소스가 있는 위치를 확인 합니다. 다음 중 하나일 수 있습니다.

- **StrTraitATL < wchar_t** &#124; **char** &#124; &#124; tchar.h, ChTraitsCRT < wchar_t char tchar.h > > &#124;

   클래스는 CRT 지원이 필요 하며, `m_hInstResource` (응용 프로그램의 모듈 클래스의 멤버)에 지정 된 모듈에서 리소스 문자열을 검색 합니다.

- **StrTraitATL < wchar_t** &#124; **char** &#124; &#124; tchar.h, ChTraitsOS < wchar_t char tchar.h > > &#124;

   클래스는 CRT 지원이 필요 하지 않으며, `m_hInstResource` (응용 프로그램의 모듈 클래스의 멤버)에 지정 된 모듈에서 리소스 문자열을 검색 합니다.

- **StrTraitMFC < wchar_t** &#124; **char** &#124; &#124; tchar.h, ChTraitsCRT < wchar_t char tchar.h > > &#124;

   클래스는 CRT 지원이 필요 하며 표준 MFC 검색 알고리즘을 사용 하 여 리소스 문자열을 검색 합니다.

- **StrTraitMFC < wchar_t** &#124; **char** &#124; &#124; tchar.h, ChTraitsOS < wchar_t char tchar.h > > &#124;

   클래스는 CRT 지원이 필요 하지 않으며 표준 MFC 검색 알고리즘을 사용 하 여 리소스 문자열을 검색 합니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|Description|
|----------|-----------------|
|[CStringT::CStringT](#cstringt)|개체를 `CStringT` 다양 한 방식으로 생성 합니다.|
|[CStringT::~CStringT](#_dtorcstringt)|`CStringT` 개체를 제거합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|Description|
|----------|-----------------|
|[CStringT::AllocSysString](#allocsysstring)|데이터에서 `CStringT` BSTR을 할당 합니다.|
|[CStringT::AnsiToOem](#ansitooem)|ANSI 문자 집합에서 OEM 문자 집합으로의 내부 변환을 수행 합니다.|
|[CStringT::AppendFormat](#appendformat)|기존 `CStringT` 개체에 형식이 지정 된 데이터를 추가 합니다.|
|[CStringT::Collate](#collate)|두 문자열을 비교 합니다 (대/소문자 구분, 로캘 관련 정보 사용).|
|[CStringT::CollateNoCase](#collatenocase)|두 문자열을 비교 합니다 (대/소문자 구분 안 함, 로캘 관련 정보 사용).|
|[CStringT::Compare](#compare)|두 문자열을 비교 합니다 (대/소문자 구분).|
|[CStringT::CompareNoCase](#comparenocase)|두 문자열을 비교 합니다 (대/소문자 구분 안 함).|
|[CStringT::Delete](#delete)|문자열에서 문자를 하나 이상 삭제 합니다.|
|[CStringT::Find](#find)|더 큰 문자열 안에서 문자 또는 부분 문자열을 찾습니다.|
|[CStringT::FindOneOf](#findoneof)|집합에서 일치 하는 첫 번째 문자를 찾습니다.|
|[CStringT::Format](#format)|문자열과 같이 `sprintf` 문자열의 형식을 지정 합니다.|
|[CStringT::FormatMessage](#formatmessage)|메시지 문자열의 형식을 지정 합니다.|
|[CStringT::FormatMessageV](#formatmessagev)|가변 인수 목록을 사용 하 여 메시지 문자열의 형식을 지정 합니다.|
|[CStringT::FormatV](#formatv)|인수의 변수 목록을 사용 하 여 문자열의 형식을 지정 합니다.|
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|문자열을 지정 된 환경 변수의 값으로 설정 합니다.|
|[CStringT::Insert](#insert)|문자열 내의 지정 된 인덱스에 단일 문자 또는 부분 문자열을 삽입 합니다.|
|[CStringT::Left](#left)|문자열의 왼쪽 부분을 추출 합니다.|
|[CStringT::LoadString](#loadstring)|Windows 리소스에서 `CStringT` 기존 개체를 로드 합니다.|
|[CStringT::MakeLower](#makelower)|이 문자열의 모든 문자를 소문자로 변환 합니다.|
|[CStringT::MakeReverse](#makereverse)|문자열을 반대로 바꿉니다.|
|[CStringT::MakeUpper](#makeupper)|이 문자열의 모든 문자를 대문자로 변환 합니다.|
|[CStringT::Mid](#mid)|문자열의 가운데 부분을 추출 합니다.|
|[CStringT::OemToAnsi](#oemtoansi)|OEM 문자 집합에서 ANSI 문자 집합으로의 내부 변환을 수행 합니다.|
|[CStringT::Remove](#remove)|문자열에서 표시 된 문자를 제거 합니다.|
|[CStringT::Replace](#replace)|표시 된 문자를 다른 문자로 바꿉니다.|
|[CStringT::ReverseFind](#reversefind)|큰 문자열 안에서 문자를 찾습니다. 끝부터 시작 합니다.|
|[CStringT::Right](#right)|문자열의 오른쪽 부분을 추출 합니다.|
|[CStringT::SetSysString](#setsysstring)|`CStringT` 개체의 데이터를 사용 하 여 기존 BSTR 개체를 설정 합니다.|
|[CStringT::SpanExcluding](#spanexcluding)|는로 `pszCharSet`식별 되는 문자 집합에 포함 되지 않은 첫 번째 문자부터 시작 하 여 문자열에서 문자를 추출 합니다.|
|[CStringT::SpanIncluding](#spanincluding)|집합의 문자만 포함 하는 부분 문자열을 추출 합니다.|
|[CStringT::Tokenize](#tokenize)|대상 문자열에서 지정 된 토큰을 추출 합니다.|
|[CStringT::Trim](#trim)|문자열에서 선행 및 후행 공백 문자를 모두 자릅니다.|
|[CStringT::TrimLeft](#trimleft)|문자열에서 선행 공백 문자를 자릅니다.|
|[CStringT::TrimRight](#trimright)|문자열에서 후행 공백 문자를 잘라냅니다.|

### <a name="operators"></a>연산자

|||
|-|-|
|[CStringT:: operator =](#operator_eq)|`CStringT` 개체에 새 값을 할당 합니다.|
|[CStringT:: operator +](#operator_add)|두 문자열 또는 문자와 문자열을 연결 합니다.|
|[CStringT:: operator + =](#operator_add_eq)|새 문자열을 기존 문자열의 끝에 연결 합니다.|
|[CStringT:: operator = =](#operator_eq_eq)|두 문자열이 논리적으로 같은지 여부를 확인 합니다.|
|[CStringT:: operator! =](#operator_neq)|두 문자열이 논리적으로 같지 않은 지 여부를 확인 합니다.|
|[CStringT:: operator&lt;](#operator_lt)|연산자의 좌 변에 있는 문자열이 우변에 있는 문자열 보다 작거나 같은지 여부를 확인 합니다.|
|[CStringT:: operator&gt;](#operator_gt)|연산자의 좌 변에 있는 문자열이 우변에 있는 문자열 보다 큰지 여부를 확인 합니다.|
|[CStringT:: operator&lt;=](#operator_lt_eq)|연산자의 좌 변에 있는 문자열이 우변에 있는 문자열 보다 작거나 같은지 여부를 확인 합니다.|
|[CStringT:: operator&gt;=](#operator_gt_eq)|연산자의 좌 변에 있는 문자열이 우변에 있는 문자열 보다 크거나 같은지 여부를 확인 합니다.|

## <a name="remarks"></a>설명

`CStringT`[CSimpleStringT 클래스](../../atl-mfc-shared/reference/csimplestringt-class.md)에서 상속 됩니다. 문자 조작, 순서 지정, 검색 등의 고급 기능은에 의해 `CStringT`구현 됩니다.

> [!NOTE]
> `CStringT`개체는 예외를 throw 할 수 있습니다. 이는 어떤 이유로 `CStringT` 든 개체에 메모리가 부족 한 경우에 발생 합니다.

개체 `CStringT` 는 가변 길이 문자 시퀀스로 구성 됩니다. `CStringT`Basic의 구문과 유사한 구문을 사용 하 여 함수 및 연산자를 제공 합니다. 연결 및 비교 연산자를 간소화 된 메모리 관리와 함께 사용 `CStringT` 하면 일반 문자 배열 보다 개체를 더 쉽게 사용할 수 있습니다.

> [!NOTE]
>  포함 된 null 문자를 포함 `CStringT` 하는 인스턴스를 만들 수 있지만이를 방지 하는 것이 좋습니다. 포함 된 null 문자를 `CStringT` 포함 하는 개체에 대해 메서드 및 연산자를 호출 하면 의도 하지 않은 결과가 발생할 수 있습니다.

`BaseType` 및 매개 `StringTraits` 변수의`CStringT` 다양 한 조합을 사용 하 여 개체는 ATL 라이브러리에 의해 미리 정의 된 다음 형식으로 제공 될 수 있습니다.

ATL 응용 프로그램에서를 사용 하는 경우:

`CString`, `CStringA` 및`CStringW` 는 MFC DLL (MFC90)에서 내보내집니다. DLL), 사용자 Dll은 그렇지 않습니다. 이는 곱하기가 정의 `CStringT` 되지 않도록 하기 위해 수행 됩니다.

> [!NOTE]
>  코드에 [CStringT를 사용 하 여 문자열 클래스 내보내기](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md)에서 설명한 링커 오류에 대 한 해결 방법이 포함 되어 있으면 해당 코드를 제거 해야 합니다. 더 이상 필요 하지 않습니다.

MFC 기반 응용 프로그램 내에서 사용할 수 있는 문자열 형식은 다음과 같습니다.

|CStringT 형식|선언|
|-------------------|-----------------|
|`CStringA`|CRT를 지 원하는 ANSI 문자 형식 문자열입니다.|
|`CStringW`|CRT를 지 원하는 유니코드 문자 형식 문자열입니다.|
|`CString`|ANSI 및 유니코드 문자 형식이 CRT를 지원 합니다.|

ATL_CSTRING_NO_CRT가 정의 된 프로젝트에서 사용할 수 있는 문자열 형식은 다음과 같습니다.

|CStringT 형식|선언|
|-------------------|-----------------|
|`CAtlStringA`|CRT를 지원 하지 않는 ANSI 문자 형식 문자열입니다.|
|`CAtlStringW`|CRT를 지원 하지 않는 유니코드 문자 형식 문자열입니다.|
|`CAtlString`|ANSI 및 유니코드 문자 형식이 CRT를 지원 하지 않습니다.|

ATL_CSTRING_NO_CRT가 정의 되지 않은 프로젝트에서 사용할 수 있는 문자열 형식은 다음과 같습니다.

|CStringT 형식|선언|
|-------------------|-----------------|
|`CAtlStringA`|CRT를 지 원하는 ANSI 문자 형식 문자열입니다.|
|`CAtlStringW`|CRT를 지 원하는 유니코드 문자 형식 문자열입니다.|
|`CAtlString`|ANSI 및 유니코드 문자 형식이 CRT를 지원 합니다.|

`CString`개체에는 다음과 같은 특성도 있습니다.

- `CStringT`개체는 연결 작업의 결과로 증가할 수 있습니다.

- `CStringT`개체는 "값 의미 체계"를 따릅니다. `CStringT` 개체를 문자열에 대 한 포인터가 아닌 실제 문자열로 간주 합니다.

- 함수 인수에 대 `CStringT` 한 `PCXSTR` 개체를 자유롭게 대체할 수 있습니다.

- 문자열 버퍼에 대 한 사용자 지정 메모리 관리. 자세한 내용은 [메모리 관리 및 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)를 참조 하세요.

## <a name="cstringt-predefined-types"></a>CStringT 미리 정의 된 형식

는 `CStringT` 템플릿 인수를 사용 하 여 지원 되는 문자 형식 ( [wchar_t](../../c-runtime-library/standard-types.md) 또는 [char](../../c-runtime-library/standard-types.md))을 정의 하므로 때때로 메서드 매개 변수 형식이 복잡할 수 있습니다. 이 문제를 간소화 하기 위해 미리 정의 된 형식 집합이 `CStringT` 클래스 전체에서 정의 되 고 사용 됩니다. 다음 표에서는 다양 한 유형을 나열 합니다.

|이름|Description|
|----------|-----------------|
|`XCHAR`|`CStringT` 개체와 동일한 문자 형식을 사용 하는 단일 문자 ( **wchar_t** 또는 **char**)입니다.|
|`YCHAR`|`CStringT` 개체와 반대 문자 형식을 사용 하는 단일 문자 ( **wchar_t** 또는 **char**)입니다.|
|`PXSTR`|`CStringT` 개체와 동일한 문자 형식을 사용 하는 문자열 ( **wchar_t** 또는 **char**)에 대 한 포인터입니다.|
|`PYSTR`|`CStringT` 개체와 반대편 문자 형식을 사용 하는 문자열 ( **wchar_t** 또는 **char**)에 대 한 포인터입니다.|
|`PCXSTR`|개체`CStringT` 와 동일한 문자 형식을 사용 하는 **const** 문자열 ( **wchar_t** 또는 **char**)에 대 한 포인터입니다.|
|`PCYSTR`|개체`CStringT` 와 반대 문자 형식을 사용 하는 **const** 문자열 ( **wchar_t** 또는 **char**)에 대 한 포인터입니다.|

> [!NOTE]
>  이전에 문서화 되지 않은 메서드 `CString` ( `AssignCopy`예:)를 사용 하는 코드는 다음의 `CStringT` 문서화 된 `GetBuffer` 메서드 (예: 또는 `ReleaseBuffer`)를 사용 하는 코드로 대체 되어야 합니다. 이러한 메서드는에서 `CSimpleStringT`상속 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>요구 사항

|헤더|사용 방법|
|------------|-------------|
|cstringt.h|MFC 전용 문자열 개체|
|atlstr.h|비 MFC 문자열 개체|

##  <a name="allocsysstring"></a>  CStringT::AllocSysString

BSTR 형식의 자동화 호환 문자열을 할당 하 고 종결 null 문자를 포함 하 여 `CStringT` 개체의 내용을 복사 합니다.

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>반환 값

새로 할당 된 문자열입니다.

### <a name="remarks"></a>설명

MFC 프로그램에서 메모리가 충분 하지 않으면 [Cmemoryexception 클래스가](../../mfc/reference/cmemoryexception-class.md) throw 됩니다. ATL 프로그램에서는 오류를 [발생](../../atl/reference/catlexception-class.md) 합니다. 이 함수는 일반적으로 자동화를 위해 문자열을 반환 하는 데 사용 됩니다.

일반적으로이 문자열이 COM 함수에 [in] 매개 변수로 전달 되 면 호출자가 문자열을 해제 해야 합니다. Windows SDK에 설명 된 대로 [Sysfreestring](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)을 사용 하 여이 작업을 수행할 수 있습니다. 자세한 내용은 [BSTR의 메모리 할당 및 해제](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)를 참조 하세요.

Windows의 OLE 할당 함수에 대 한 자세한 내용은 Windows SDK의 [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) 를 참조 하십시오.

### <a name="example"></a>예제

다음 예에서는 `CStringT::AllocSysString`의 사용법을 보여줍니다.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

##  <a name="ansitooem"></a>  CStringT::AnsiToOem

이 `CStringT` 개체의 모든 문자를 ANSI 문자 집합에서 OEM 문자 집합으로 변환 합니다.

```
void AnsiToOem();
```

### <a name="remarks"></a>설명

_UNICODE가 정의 된 경우에는 함수를 사용할 수 없습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

##  <a name="appendformat"></a>  CStringT::AppendFormat

기존 `CStringT` 개체에 형식이 지정 된 데이터를 추가 합니다.

```
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>매개 변수

*pszFormat*<br/>
형식 컨트롤 문자열입니다.

*nFormatID*<br/>
형식 컨트롤 문자열을 포함 하는 문자열 리소스 식별자입니다.

*argument*<br/>
선택적 인수입니다.

### <a name="remarks"></a>설명

이 함수는 일련의 문자 및 값을 형식 지정 하 고 `CStringT`에 추가 합니다. 각 선택적 인수 (있는 경우)는 *pszFormat* 의 해당 형식 사양에 따라 변환 되 고 *nFormatID*에 의해 식별 된 문자열 리소스에서 추가 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

##  <a name="collate"></a>  CStringT::Collate

제네릭 텍스트 함수 `_tcscoll`를 사용 하 여 두 문자열을 비교 합니다.

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>매개 변수

*psz*<br/>
비교에 사용 되는 다른 문자열입니다.

### <a name="return-value"></a>반환 값

문자열이 같으면 0이 고, `CStringT` 이 개체가 *psz*보다 작은 경우 0을 <이 고,이 `CStringT` 개체가 *psz*보다 크면 0을 > 합니다.

### <a name="remarks"></a>설명

Tchar.h에 정의 된 일반 `_tcscoll`텍스트 함수입니다. H는 컴파일 시간에 `strcoll`정의 `wcscoll`된 문자 `_mbscoll`집합에 따라, 또는에 매핑됩니다. 각 함수는 현재 사용 중인 코드 페이지에 따라 문자열에 대 한 대/소문자를 구분 하는 비교를 수행 합니다. 자세한 내용은 [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)를 참조 하세요.

##  <a name="collatenocase"></a>  CStringT::CollateNoCase

제네릭 텍스트 함수 `_tcscoll`를 사용 하 여 두 문자열을 비교 합니다.

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>매개 변수

*psz*<br/>
비교에 사용 되는 다른 문자열입니다.

### <a name="return-value"></a>반환 값

문자열이 동일한 경우 (대/소문자 무시) 0 < `CStringT` 이 개체가 *psz* (대/소문자 무시) 보다 작은 경우 0을 반환 하 고,이 `CStringT` 개체가 *psz* (대/소문자 무시) 보다 큰 경우 0을 > 합니다.

### <a name="remarks"></a>설명

Tchar.h에 정의 된 일반 `_tcscoll`텍스트 함수입니다. H는 컴파일 시간에 `stricoll`정의 `wcsicoll`된 문자 `_mbsicoll`집합에 따라, 또는에 매핑됩니다. 각 함수는 현재 사용 중인 코드 페이지에 따라 문자열에 대 한 대/소문자를 구분 하지 않는 비교를 수행 합니다. 자세한 내용은 [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

##  <a name="compare"></a>  CStringT::Compare

두 문자열을 비교 합니다 (대/소문자 구분).

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>매개 변수

*psz*<br/>
비교에 사용 되는 다른 문자열입니다.

### <a name="return-value"></a>반환 값

문자열이 같으면 0이 고, `CStringT` 이 개체가 *psz*보다 작은 경우 0을 <이 고,이 `CStringT` 개체가 *psz*보다 크면 0을 > 합니다.

### <a name="remarks"></a>설명

Tchar.h에 정의 된 일반 `_tcscmp`텍스트 함수입니다. H는 컴파일 시간에 `strcmp`정의 `wcscmp`된 문자 `_mbscmp`집합에 따라, 또는에 매핑됩니다. 각 함수는 문자열의 대/소문자를 구분 하는 비교를 수행 하며 로캘의 영향을 받지 않습니다. 자세한 내용은 [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)를 참조 하세요.

문자열에 포함 된 null이 포함 된 경우 비교를 위해 문자열은 첫 번째 포함 된 null 문자에서 잘린 것으로 간주 됩니다.

### <a name="example"></a>예제

다음 예에서는 `CStringT::Compare`의 사용법을 보여줍니다.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

##  <a name="comparenocase"></a>  CStringT::CompareNoCase

두 문자열을 비교 합니다 (대/소문자 구분 안 함).

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>매개 변수

*psz*<br/>
비교에 사용 되는 다른 문자열입니다.

### <a name="return-value"></a>반환 값

문자열이 동일한 경우 (대/소문자 무시) 0 < `CStringT` 이 개체가 *psz* (대/소문자 무시) 보다 작은 경우 0을 반환 하 고,이 `CStringT` 개체가 *psz* (대/소문자 무시) 보다 큰 경우 0을 > 합니다.

### <a name="remarks"></a>설명

Tchar.h에 정의 된 일반 `_tcsicmp`텍스트 함수입니다. H는 컴파일 시간에 `_stricmp`정의 `_wcsicmp` 된 `_mbsicmp`문자 집합에 따라 또는에 매핑됩니다. 각 함수는 문자열의 대/소문자를 구분 하지 않는 비교를 수행 합니다. 비교는 로캘의 LC_CTYPE 측면에 따라 달라 지지만 LC_COLLATE는 그렇지 않습니다. 자세한 내용은 [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

##  <a name="cstringt"></a>  CStringT::CStringT

`CStringT` 개체를 생성합니다.

```
CStringT() throw() :
    CThisSimpleString(StringTraits::GetDefaultManager());

explicit CStringT(IAtlStringMgr* pStringMgr) throw() :
    CThisSimpleString( pStringMgr);

CStringT(const VARIANT& varSrc);

CStringT(const VARIANT& varSrc, IAtlStringMgr* pStringMgr);

CStringT(const CStringT& strSrc) :
    CThisSimpleString( strSrc);

operator CSimpleStringT<
                    BaseType,
                    !_CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                    :: c_bIsMFCDLLTraits> &()

template <bool bMFCDLL>
CStringT(const CSimpleStringT<BaseType, bMFCDLL>& strSrc) :
    CThisSimpleString( strSrc);

template <class SystemString>
CStringT(SystemString^ pString) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(const YCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(LPCSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CStringT(LPCWSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(const unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

/*CSTRING_EXPLICIT*/ CStringT(char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const unsigned char* pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(char ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength) :
    CThisSimpleString( pch, nLength, StringTraits::GetDefaultManager());

CStringT(const YCHAR* pch, int nLength) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength, AtlStringMgr* pStringMgr) :
    CThisSimpleString( pch, nLength, pStringMgr);

CStringT(const YCHAR* pch, int nLength, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);
```

### <a name="parameters"></a>매개 변수

*pch*<br/>
길이가 *nlength*이 고 null로 끝나지 않는 문자 배열에 대 한 포인터입니다.

*nLength*<br/>
*Pch*의 문자 수입니다.

*ch*<br/>
단일 문자입니다.

*pszSrc*<br/>
이 `CStringT` 개체로 복사 될 null로 끝나는 문자열입니다.

*pStringMgr*<br/>
`CStringT` 개체의 메모리 관리자에 대 한 포인터입니다. 및의 `IAtlStringMgr` `CStringT`메모리 관리에 대 한 자세한 내용은 [CStringT를 사용 하 여 메모리 관리](../../atl-mfc-shared/memory-management-with-cstringt.md)를 참조 하세요.

*strSrc*<br/>
`CStringT` 이`CStringT` 개체에 복사할 기존 개체입니다. `CThisString` 및`CThisSimpleString`에 대 한 자세한 내용은 설명 부분을 참조 하세요.

*varSrc*<br/>
이 `CStringT` 개체로 복사할 variant 개체입니다.

*BaseType*<br/>
문자열 클래스의 문자 형식입니다. 다음 중 하나일 수 있습니다.

**char** (ANSI 문자열의 경우).

**wchar_t** (유니코드 문자열의 경우).

TCHAR.H (ANSI 및 유니코드 문자열 모두)

*bMFCDLL*<br/>
프로젝트가 MFC DLL 인지 (TRUE) 아니면 그렇지 않은지 (FALSE) 여부를 지정 하는 부울입니다.

*SystemString*<br/>
는 여야 `System::String`하 고 프로젝트는/clr을 사용 하 여 컴파일해야 합니다.

*pString*<br/>
`CStringT` 개체에 대 한 핸들입니다.

### <a name="remarks"></a>설명

생성자는 입력 데이터를 새 할당 된 저장소에 복사 하기 때문에 메모리 예외가 발생할 수 있음을 알고 있어야 합니다. 이러한 생성자 중 일부는 변환 함수 역할을 합니다. 이를 통해 `CStringT` 개체가 예상 되는 LPTSTR를 대체할 수 있습니다.

- `CStringT`( `LPCSTR` `lpsz` ): ANSI 문자열에서 `CStringT` 유니코드를 생성 합니다. 또한 아래 예제와 같이이 생성자를 사용 하 여 문자열 리소스를 로드할 수 있습니다.

- `CStringT(` `LPCWSTR` `lpsz` ): 유니코드 문자열 `CStringT` 에서을 생성 합니다.

- `CStringT`( `const unsigned char*` `psz` ): **부호 없는 char**에 대 `CStringT` 한 포인터에서를 생성할 수 있습니다.

> [!NOTE]
>  _CSTRING_DISABLE_NARROW_WIDE_CONVERSION 매크로를 정의 하 여 ANSI 문자열과 유니코드 문자열 간의 암시적 문자열 변환을 해제 합니다. 매크로는 변환을 지 원하는 컴파일 생성자에서 제외 됩니다.

*Strsrc* 매개 변수는 `CStringT` 또는 `CThisSimpleString` 개체 일 수 있습니다. 의 `CStringT`경우 기본 인스턴스화 (`CString`, `CStringA`또는 `CStringW`) 중 하나를 사용 합니다 .의 `CThisSimpleString`경우 **this** 포인터를 사용 합니다. `CThisSimpleString`[CSimpleStringT 클래스](../../atl-mfc-shared/reference/csimplestringt-class.md)의 인스턴스를 선언 합니다 .이 클래스는 `CStringT` 클래스 보다 기본 제공 기능이 적은 작은 문자열 클래스입니다.

오버 로드 연산자 `CSimpleStringT<>&()` 는 `CSimpleStringT` 선언 `CStringT` 에서 개체를 생성 합니다.

> [!NOTE]
>  포함 된 null 문자를 포함 `CStringT` 하는 인스턴스를 만들 수 있지만이를 방지 하는 것이 좋습니다. 포함 된 null 문자를 `CStringT` 포함 하는 개체에 대해 메서드 및 연산자를 호출 하면 의도 하지 않은 결과가 발생할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

##  <a name="_dtorcstringt"></a>  CStringT::~CStringT

개체를 `CStringT` 소멸 시킵니다.

```
~CStringT() throw();
```

### <a name="remarks"></a>설명

개체를 `CStringT` 소멸 시킵니다.

##  <a name="delete"></a>  CStringT::Delete

문자열에서 지정 된 인덱스에 있는 문자로 시작 하는 문자를 하나 이상 삭제 합니다.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
삭제할 `CStringT` 개체에서 첫 번째 문자의 0부터 시작 하는 인덱스입니다.

*nCount*<br/>
제거할 문자 수입니다.

### <a name="return-value"></a>반환 값

변경 된 문자열의 길이입니다.

### <a name="remarks"></a>설명

*Ncount* 가 문자열 보다 길면 나머지 문자열이 제거 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

##  <a name="find"></a>  CStringT::Find

이 문자열에서 문자 또는 하위 문자열의 첫 번째 일치 항목을 검색 합니다.

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>매개 변수

*pszSub*<br/>
검색할 부분 문자열입니다.

*iStart*<br/>
검색을 시작할 문자열에 있는 문자의 인덱스 이거나, 처음부터 시작 하는 경우 0입니다.

*ch*<br/>
검색할 단일 문자입니다.

### <a name="return-value"></a>반환 값

이 `CStringT` 개체에서 요청 된 부분 문자열 또는 문자와 일치 하는 첫 번째 문자의 0부터 시작 하는 인덱스이 고, 부분 문자열이 나 문자를 찾을 수 없으면-1입니다.

### <a name="remarks"></a>설명

함수는 단일 문자 (런타임 함수와 `strchr`비슷함) 및 문자열 ( `strstr`과 유사)을 모두 허용 하도록 오버 로드 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

##  <a name="findoneof"></a>  CStringT::FindOneOf

이 문자열에서 *pszCharSet*에 포함 된 문자와 일치 하는 첫 번째 문자를 검색 합니다.

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>매개 변수

*pszCharSet*<br/>
일치 하는 문자를 포함 하는 문자열입니다.

### <a name="return-value"></a>반환 값

*PszCharSet*에도 있는이 문자열에 있는 첫 번째 문자의 0부터 시작 하는 인덱스입니다. 일치 하는 항목이 없으면-1입니다.

### <a name="remarks"></a>설명

*PszCharSet*에서 처음 발견 되는 문자를 찾습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

##  <a name="format"></a>  CStringT::Format

[Sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)가 데이터를 C 스타일 문자 배열로 서식 지정 하는 것과 동일한 방식으로 `CStringT`에 형식이 지정된 데이터를 씁니다.

```
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>매개 변수

*nFormatID*<br/>
형식 컨트롤 문자열을 포함 하는 문자열 리소스 식별자입니다.

*pszFormat*<br/>
형식 컨트롤 문자열입니다.

*argument*<br/>
선택적 인수입니다.

### <a name="remarks"></a>설명

이 함수는 일련의 문자 및 값의 형식을 지정 하 고 `CStringT`에 저장 합니다. 각 선택적 인수 (있는 경우)는 *pszFormat* 의 해당 형식 사양에 따라 변환 되 고 출력 되며 *nFormatID*로 식별 된 문자열 리소스에서 출력 됩니다.

문자열 개체 자체를에 대 `Format`한 매개 변수로 제공 하면 호출이 실패 합니다. 예를 들어 다음 코드는 예측할 수 없는 결과를 발생 시킵니다.

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

자세한 내용은 [형식 사양 구문: printf 및 wprintf 함수](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)를 참조하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

##  <a name="formatmessage"></a>  CStringT::FormatMessage

메시지 문자열의 형식을 지정 합니다.

```
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>매개 변수

*nFormatID*<br/>
서식이 지정 되지 않은 메시지 텍스트를 포함 하는 문자열 리소스 식별자입니다.

*pszFormat*<br/>
형식 컨트롤 문자열을 가리킵니다. 그러면 삽입이 검색 되 고 그에 따라 형식이 지정 됩니다. 서식 문자열은 임의의 순서로 매개 변수를 삽입할 수 있도록 하는 경우를 제외 하 고는 런타임 함수 *printf*스타일 형식 문자열과 비슷합니다.

*argument*<br/>
선택적 인수입니다.

### <a name="remarks"></a>설명

함수에는 입력으로 메시지 정의가 필요 합니다. 메시지 정의는 *pszFormat* 또는 *nFormatID*에 의해 식별 된 문자열 리소스에서 결정 됩니다. 함수는 서식이 지정 된 메시지 텍스트를 `CStringT` 개체에 복사 하 고 요청 된 경우 포함 된 삽입 시퀀스를 처리 합니다.

> [!NOTE]
> `FormatMessage`새로 서식이 지정 된 문자열에 대 한 시스템 메모리를 할당 하려고 합니다. 이 시도가 실패 하면 메모리 예외가 자동으로 throw 됩니다.

각 삽입에는 *pszFormat* 또는 *nFormatID* 매개 변수 다음에 해당 하는 매개 변수가 있어야 합니다. 메시지 텍스트 내에서 메시지에 동적으로 서식을 지정 하기 위해 여러 이스케이프 시퀀스가 지원 됩니다. 자세한 내용은 Windows SDK의 Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) 함수를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

##  <a name="formatmessagev"></a>  CStringT::FormatMessageV

가변 인수 목록을 사용 하 여 메시지 문자열의 형식을 지정 합니다.

```
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>매개 변수

*pszFormat*<br/>
형식 컨트롤 문자열을 가리킵니다. 그러면 삽입이 검색 되 고 그에 따라 형식이 지정 됩니다. 서식 문자열은 임의 순서로 매개 변수를 삽입할 수 `printf`있도록 하는 경우를 제외 하 고 런타임 함수 스타일 형식 문자열과 비슷합니다.

*pArgList*<br/>
인수 목록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

함수는 *pszFormat*에 의해 결정 되는 메시지 정의를 입력으로 사용 해야 합니다. 함수는 서식이 지정 된 메시지 텍스트와 인수의 변수 목록을 `CStringT` 개체에 복사 하 고 요청 된 경우 포함 된 삽입 시퀀스를 처리 합니다.

> [!NOTE]
> `FormatMessageV`는 새 형식의 문자열에 대해 시스템 메모리를 할당 하려고 하는 [CStringT:: FormatMessage](#formatmessage)를 호출 합니다. 이 시도가 실패 하면 메모리 예외가 자동으로 throw 됩니다.

자세한 내용은 Windows SDK의 Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) 함수를 참조 하세요.

##  <a name="formatv"></a>  CStringT::FormatV

가변 인수 목록을 사용 하 여 메시지 문자열의 형식을 지정 합니다.

```
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>매개 변수

*pszFormat*<br/>
형식 컨트롤 문자열을 가리킵니다. 그러면 삽입이 검색 되 고 그에 따라 형식이 지정 됩니다. 서식 문자열은 임의 순서로 매개 변수를 삽입할 수 `printf`있도록 하는 경우를 제외 하 고 런타임 함수 스타일 형식 문자열과 비슷합니다.

*args*<br/>
인수 목록에 대 한 포인터입니다.

### <a name="remarks"></a>설명

데이터 형식을 C 스타일 문자 배열로 지정 하는 것 `CStringT` `vsprintf_s` 과 동일한 방식으로 문자열에 인수의 변수 목록과 형식이 지정 된 문자열을 씁니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

##  <a name="getenvironmentvariable"></a>  CStringT::GetEnvironmentVariable

문자열을 지정 된 환경 변수의 값으로 설정 합니다.

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>매개 변수

*pszVar*<br/>
환경 변수를 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

호출 프로세스의 환경 블록에서 지정 된 변수의 값을 검색 합니다. 값은 null로 끝나는 문자열의 형식입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

##  <a name="insert"></a>  CStringT::Insert

문자열 내의 지정 된 인덱스에 단일 문자 또는 부분 문자열을 삽입 합니다.

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
삽입을 수행 하기 전의 문자 인덱스입니다.

*psz*<br/>
삽입할 부분 문자열에 대 한 포인터입니다.

*ch*<br/>
삽입할 문자입니다.

### <a name="return-value"></a>반환 값

변경 된 문자열의 길이입니다.

### <a name="remarks"></a>설명

*Iindex* 매개 변수는 문자 또는 부분 문자열을 위한 공간을 만들기 위해 이동 하는 첫 번째 문자를 식별 합니다. *Nindex* 가 0 이면 전체 문자열 앞에 삽입이 발생 합니다. *Nindex* 가 문자열의 길이 보다 높으면 함수는 현재 문자열과 *ch* 또는 *psz*가 제공 하는 새 자료를 연결 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

##  <a name="left"></a>  CStringT::Left

이`CStringT` 개체에서 맨 왼쪽 *n 개수* 문자를 추출 하 고 추출 된 부분 문자열의 복사본을 반환 합니다.

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>매개 변수

*nCount*<br/>
이 `CStringT` 개체에서 추출할 문자의 수입니다.

### <a name="return-value"></a>반환 값

지정된 문자 범위의 복사본을 포함하는 `CStringT` 개체입니다. 반환된 `CStringT` 개체가 비어 있을 수 있습니다.

### <a name="remarks"></a>설명

*N 수가* 문자열 길이를 초과 하면 전체 문자열이 추출 됩니다. `Left`는 기본 `Left` 함수와 유사합니다.

MBCS (멀티 바이트 문자 집합)의 경우 *ncount* 는 각 8 비트 시퀀스를 문자로 처리 하므로 *ncount* 는 멀티 바이트 문자 수를 2로 곱한 값을 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

##  <a name="loadstring"></a>  CStringT::LoadString

*NID*로 식별 되는 Windows 문자열 리소스를 기존 `CStringT` 개체로 읽습니다.

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>매개 변수

*hInstance*<br/>
모듈 인스턴스에 대 한 핸들입니다.

*nID*<br/>
Windows 문자열 리소스 ID입니다.

*wLanguageID*<br/>
문자열 리소스의 언어입니다.

### <a name="return-value"></a>반환 값

리소스 로드가 성공한 경우 0이 아님 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

지정 된 언어 (*Wlanguage*)를 사용 하 여 지정 된 모듈 (*hinstance*)에서 문자열 리소스 (*nID*)를 로드 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

##  <a name="makelower"></a>  CStringT::MakeLower

`CStringT` 개체를 소문자 문자열로 변환 합니다.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>반환 값

결과 소문자 문자열입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

##  <a name="makereverse"></a>  CStringT::MakeReverse

`CStringT` 개체의 문자 순서를 반대로 바꿉니다.

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>반환 값

결과의 반전 된 문자열입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

##  <a name="makeupper"></a>  CStringT::MakeUpper

`CStringT` 개체를 대문자 문자열로 변환 합니다.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>반환 값

결과 대문자 문자열입니다.

### <a name="remarks"></a>설명

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

##  <a name="mid"></a>  CStringT::Mid

위치 *ifirst* (0부터 시작)에서 시작 `CStringT` 하 여이 개체에서 길이 *ncount* 문자의 부분 문자열을 추출 합니다.

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>매개 변수

*iFirst*<br/>
이 `CStringT` 개체에서 추출 된 부분 문자열에 포함할 첫 번째 문자의 0부터 시작 하는 인덱스입니다.

*nCount*<br/>
이 `CStringT` 개체에서 추출할 문자의 수입니다. 이 매개 변수를 지정 하지 않으면 문자열의 나머지가 추출 됩니다.

### <a name="return-value"></a>반환 값

지정된 문자 범위의 복사본을 포함하는 `CStringT` 개체입니다. 반환 `CStringT` 된 개체는 비어 있을 수 있습니다.

### <a name="remarks"></a>설명

함수는 추출 된 부분 문자열의 복사본을 반환 합니다. `Mid`는 basic Mid 함수와 비슷합니다 (Basic의 인덱스는 1부터만).

MBCS (멀티 바이트 문자 집합)의 경우 *Ncount* 는 각 8 비트 문자를 참조 합니다. 즉, 한 멀티 바이트 문자의 선행 및 후행 바이트는 두 문자로 계산 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

##  <a name="oemtoansi"></a>  CStringT::OemToAnsi

이 `CStringT` 개체의 모든 문자를 OEM 문자 집합에서 ANSI 문자 집합으로 변환 합니다.

```
void OemToAnsi();
```

### <a name="remarks"></a>설명

_UNICODE가 정의 된 경우에는이 함수를 사용할 수 없습니다.

### <a name="example"></a>예제

[CStringT:: AnsiToOem](#ansitooem)의 예제를 참조 하세요.

##  <a name="operator_eq"></a>  CStringT::operator =

문자열에 새 값을 할당 합니다.

```
CStringT& operator=(const CStringT& strSrc);

template<bool bMFCDLL>
CStringT& operator=(const CSimpleStringT<BaseType, bMFCDLL>& str);

CStringT& operator=(PCXSTR pszSrc);
CStringT& operator=(PCYSTR pszSrc);
CStringT& operator=(const unsigned char* pszSrc);
CStringT& operator=(XCHAR ch);
CStringT& operator=(YCHAR ch);
CStringT& operator=(const VARIANT& var);
```

### <a name="parameters"></a>매개 변수

*strSrc*<br/>
`CStringT` 이 문자열에 할당할입니다.

*str*<br/>
`CThisSimpleString` 개체에 대한 참조입니다.

*bMFCDLL*<br/>
프로젝트가 MFC DLL 인지 여부를 지정 하는 부울입니다.

*BaseType*<br/>
문자열 기본 형식입니다.

*var*<br/>
이 문자열에 할당할 variant 개체입니다.

*ch*<br/>
문자열에 할당할 ANSI 또는 유니코드 문자입니다.

*pszSrc*<br/>
할당 되는 원본 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

대입 연산자는 다른 `CStringT` 개체, 문자 포인터 또는 단일 문자를 허용 합니다. 새 저장소를 할당할 수 있으므로이 연산자를 사용할 때마다 메모리 예외가 발생할 수 있습니다.

에 `CThisSimpleString`대 한 자세한 내용은 [cstringt:: cstringt](#cstringt)의 설명 섹션을 참조 하세요.

> [!NOTE]
> 포함 된 null 문자를 포함 `CStringT` 하는 인스턴스를 만들 수 있지만이를 방지 하는 것이 좋습니다. 포함 된 null 문자를 `CStringT` 포함 하는 개체에 대해 메서드 및 연산자를 호출 하면 의도 하지 않은 결과가 발생할 수 있습니다.

##  <a name="operator_add"></a>CStringT:: operator +

두 문자열 또는 문자와 문자열을 연결 합니다.

```
friend CStringT operator+(const CStringT& str1, const CStringT& str2);
friend CStringT operator+(const CStringT& str1, PCXSTR psz2);
friend CStringT operator+(PCXSTR psz1, const CStringT& str2,);
friend CStringT operator+(char ch1, const CStringT& str2,);
friend CStringT operator+(const CStringT& str1, char ch2);
friend CStringT operator+(const CStringT& str1, wchar_t ch2);
friend CStringT operator+(wchar_t ch1, const CStringT& str2,);
```

### <a name="parameters"></a>매개 변수

*ch1*<br/>
문자열과 연결할 ANSI 또는 유니코드 문자입니다.

*ch2*<br/>
문자열과 연결할 ANSI 또는 유니코드 문자입니다.

*str1*<br/>
`CStringT` 문자열 또는 문자와 연결할입니다.

*str2*<br/>
`CStringT` 문자열 또는 문자와 연결할입니다.

*psz1*<br/>
문자열이 나 문자와 연결할 null로 끝나는 문자열에 대 한 포인터입니다.

*psz2*<br/>
문자열 또는 문자를 연결 하는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`CStringT::operator+` 함수에는 7 개의 오버 로드 형식이 있습니다. 첫 번째 버전에서는 두 개의 `CStringT` 기존 개체를 연결 합니다. 다음 두 가지는 `CStringT` 개체와 null로 끝나는 문자열을 연결 합니다. 다음 두 가지는 `CStringT` 개체와 ANSI 문자를 연결 합니다. 마지막 두 개는 `CStringT` 개체와 유니코드 문자를 연결 합니다.

> [!NOTE]
>  포함 된 null 문자를 포함 `CStringT` 하는 인스턴스를 만들 수 있지만이를 방지 하는 것이 좋습니다. 포함 된 null 문자를 `CStringT` 포함 하는 개체에 대해 메서드 및 연산자를 호출 하면 의도 하지 않은 결과가 발생할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

##  <a name="operator_add_eq"></a>CStringT:: operator + =

문자를 문자열의 끝 부분에 연결 합니다.

```
CStringT& operator+=(const CThisSimpleString& str);

template<bool bMFCDLL>
CStringT& operator+=(const const CSimpleStringT<BaseType, bMFCDLL>& str);

template<int t_nSize>
CStringT& operator+=(const CStaticString<XCHAR, t_nSize>& strSrc);
CStringT& operator+=(PCXSTR pszSrc);
CStringT& operator+=(PCYSTR pszSrc);
CStringT& operator+=(char ch);
CStringT& operator+=(unsigned char ch);
CStringT& operator+=(wchar_t ch);
CStringT& operator+=(const VARIANT& var);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
`CThisSimpleString` 개체에 대한 참조입니다.

*bMFCDLL*<br/>
프로젝트가 MFC DLL 인지 여부를 지정 하는 부울입니다.

*BaseType*<br/>
문자열 기본 형식입니다.

*var*<br/>
이 문자열에 연결할 variant 개체입니다.

*ch*<br/>
문자열과 연결할 ANSI 또는 유니코드 문자입니다.

*pszSrc*<br/>
연결 되는 원본 문자열에 대 한 포인터입니다.

*strSrc*<br/>
`CStringT` 이 문자열에 연결할입니다.

### <a name="remarks"></a>설명

연산자는 다른 `CStringT` 개체, 문자 포인터 또는 단일 문자를 허용 합니다. 이 `CStringT` 개체에 추가 된 문자에 대해 새 저장소를 할당할 수 있으므로이 연결 연산자를 사용할 때마다 메모리 예외가 발생할 수 있습니다.

에 `CThisSimpleString`대 한 자세한 내용은 [cstringt:: cstringt](#cstringt)의 설명 섹션을 참조 하세요.

> [!NOTE]
>  포함 된 null 문자를 포함 `CStringT` 하는 인스턴스를 만들 수 있지만이를 방지 하는 것이 좋습니다. 포함 된 null 문자를 `CStringT` 포함 하는 개체에 대해 메서드 및 연산자를 호출 하면 의도 하지 않은 결과가 발생할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

##  <a name="operator_eq_eq"></a>  CStringT::operator ==

두 문자열이 논리적으로 같은지 여부를 확인 합니다.

```
friend bool operator==(const CStringT& str1, const CStringT& str2) throw();
friend bool operator==(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator==(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator==(const CStringT& str1, XCHAR ch2) throw();
friend bool operator==(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator==(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator==(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>매개 변수

*ch1*<br/>
비교할 ANSI 또는 유니코드 문자입니다.

*ch2*<br/>
비교할 ANSI 또는 유니코드 문자입니다.

*str1*<br/>
`CStringT` 비교할입니다.

*str2*<br/>
`CStringT` 비교할입니다.

*psz1*<br/>
비교할 null로 끝나는 문자열에 대 한 포인터입니다.

*psz2*<br/>
비교할 null로 끝나는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

좌 변에 있는 문자열 또는 문자가 우변에 있는 문자열 또는 문자와 같은지 테스트 하 고 그에 따라 TRUE 또는 FALSE를 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

##  <a name="operator_neq"></a>  CStringT::operator !=

두 문자열이 논리적으로 같지 않은지 여부를 확인 합니다.

```
friend bool operator!=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator!=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator!=(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator!=(const CStringT& str1, XCHAR ch2) throw();
friend bool operator!=(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator!=(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator!=(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>매개 변수

*ch1*<br/>
문자열과 연결할 ANSI 또는 유니코드 문자입니다.

*ch2*<br/>
문자열과 연결할 ANSI 또는 유니코드 문자입니다.

*str1*<br/>
`CStringT` 비교할입니다.

*str2*<br/>
`CStringT` 비교할입니다.

*psz1*<br/>
비교할 null로 끝나는 문자열에 대 한 포인터입니다.

*psz2*<br/>
비교할 null로 끝나는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

좌 변에 있는 문자열 또는 문자가 우변에 있는 문자열 또는 문자와 같지 않은 지 테스트 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

##  <a name="operator_lt"></a>CStringT:: operator&lt;

연산자의 좌 변에 있는 문자열이 우변에 있는 문자열 보다 적은지 여부를 확인 합니다.

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>매개 변수

*str1*<br/>
`CStringT` 비교할입니다.

*str2*<br/>
`CStringT` 비교할입니다.

*psz1*<br/>
비교할 null로 끝나는 문자열에 대 한 포인터입니다.

*psz2*<br/>
비교할 null로 끝나는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

문자열을 사전순으로 비교 하는 문자, 문자 기준 문자:

- 해당하는 두 문자가 같지 않음이 확인될 때까지. 이 경우 해당 비교 결과를 문자열 간의 비교 결과로 가져옵니다.

- 같지 않은 문자는 없으나 한 문자열의 문자 수가 다른 문자열보다 많음이 확인될 때까지. 이 경우 더 짧은 문자열이 더 긴 문자열보다 작은 것으로 간주합니다.

- 같지 않은 문자가 없으며 문자열의 문자 수도 같음이 확인될 때까지. 이 경우 두 문자열은 동일한 것으로 간주합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

##  <a name="operator_gt"></a>CStringT:: operator&gt;

연산자의 좌 변에 있는 문자열이 우변에 있는 문자열 보다 큰지 여부를 확인 합니다.

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>매개 변수

*str1*<br/>
`CStringT` 비교할입니다.

*str2*<br/>
`CStringT` 비교할입니다.

*psz1*<br/>
비교할 null로 끝나는 문자열에 대 한 포인터입니다.

*psz2*<br/>
비교할 null로 끝나는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

문자열을 사전순으로 비교 하는 문자, 문자 기준 문자:

- 해당하는 두 문자가 같지 않음이 확인될 때까지. 이 경우 해당 비교 결과를 문자열 간의 비교 결과로 가져옵니다.

- 같지 않은 문자는 없으나 한 문자열의 문자 수가 다른 문자열보다 많음이 확인될 때까지. 이 경우 더 짧은 문자열이 더 긴 문자열보다 작은 것으로 간주합니다.

- 같지 않은 문자가 없으며 문자열의 문자 수도 같음이 확인될 때까지. 이 경우 두 문자열은 동일한 것으로 간주합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

##  <a name="operator_lt_eq"></a>CStringT:: operator&lt;=

연산자의 좌 변에 있는 문자열이 우변에 있는 문자열 보다 작거나 같은지 여부를 확인 합니다.

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>매개 변수

*str1*<br/>
`CStringT` 비교할입니다.

*str2*<br/>
`CStringT` 비교할입니다.

*psz1*<br/>
비교할 null로 끝나는 문자열에 대 한 포인터입니다.

*psz2*<br/>
비교할 null로 끝나는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

문자열을 사전순으로 비교 하는 문자, 문자 기준 문자:

- 해당하는 두 문자가 같지 않음이 확인될 때까지. 이 경우 해당 비교 결과를 문자열 간의 비교 결과로 가져옵니다.

- 같지 않은 문자는 없으나 한 문자열의 문자 수가 다른 문자열보다 많음이 확인될 때까지. 이 경우 더 짧은 문자열이 더 긴 문자열보다 작은 것으로 간주합니다.

- 같지 않은 문자가 없으며 문자열의 문자 수도 같음이 확인될 때까지. 이 경우 두 문자열은 동일한 것으로 간주합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

##  <a name="operator_gt_eq"></a>CStringT:: operator&gt;=

연산자의 좌 변에 있는 문자열이 우변에 있는 문자열 보다 크거나 같은지 여부를 확인 합니다.

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>매개 변수

*str1*<br/>
`CStringT` 비교할입니다.

*str2*<br/>
`CStringT` 비교할입니다.

*psz1*<br/>
비교할 문자열에 대 한 포인터입니다.

*psz2*<br/>
비교할 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

문자열을 사전순으로 비교 하는 문자, 문자 기준 문자:

- 해당하는 두 문자가 같지 않음이 확인될 때까지. 이 경우 해당 비교 결과를 문자열 간의 비교 결과로 가져옵니다.

- 같지 않은 문자는 없으나 한 문자열의 문자 수가 다른 문자열보다 많음이 확인될 때까지. 이 경우 더 짧은 문자열이 더 긴 문자열보다 작은 것으로 간주합니다.

- 같지 않은 문자가 없으며 문자열의 문자 수도 같음이 확인될 때까지. 이 경우 두 문자열은 동일한 것으로 간주합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

##  <a name="remove"></a>  CStringT::Remove

문자열에서 지정 된 문자의 모든 인스턴스를 제거 합니다.

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>매개 변수

*chRemove*<br/>
문자열에서 제거할 문자입니다.

### <a name="return-value"></a>반환 값

문자열에서 제거 되는 문자 수입니다. 문자열이 변경 되지 않은 경우 0입니다.

### <a name="remarks"></a>설명

문자 비교는 대/소문자를 구분 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

##  <a name="replace"></a>  CStringT::Replace

에 `Replace`는 두 가지 버전이 있습니다. 첫 번째 버전은 다른 부분 문자열을 사용 하 여 부분 문자열의 복사본을 하나 이상 대체 합니다. 두 부분 문자열이 모두 null로 종결 됩니다. 두 번째 버전은 다른 문자를 사용 하 여 하나 이상의 문자 복사본을 대체 합니다. 두 버전 모두에 `CStringT`저장 된 문자 데이터에 대해 작동 합니다.

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>매개 변수

*pszOld*<br/>
*PszNew*로 대체 될 null로 끝나는 문자열에 대 한 포인터입니다.

*pszNew*<br/>
*PszOld*를 대체 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*chOld*<br/>
*Chnew*로 바꿀 문자입니다.

*chNew*<br/>
*Chold*문자를 바꾸는 문자입니다.

### <a name="return-value"></a>반환 값

는 문자 또는 부분 문자열의 대체 된 인스턴스 수를 반환 하 고, 문자열이 변경 되지 않은 경우에는 0을 반환 합니다.

### <a name="remarks"></a>설명

`Replace`*pszNew* 및 *pszOld* 의 길이는 같을 필요가 없으며 이전 부분 문자열의 복사본을 여러 개 새 항목으로 변경할 수 있으므로는 문자열 길이를 변경할 수 있습니다. 함수는 대/소문자를 구분 하는 일치를 수행 합니다.

인스턴스의 예는 `CString`, `CStringA` 및`CStringW`입니다. `CStringT`

의 `CStringA` 경우`Replace` 은 (는) ANSI 또는 멀티 바이트 (MBCS) 문자를 사용 합니다. 의 `CStringW` 경우`Replace` 와이드 문자를 사용 합니다.

의 `CString`경우 문자 데이터 형식은 다음 표의 상수가 정의 되었는지 여부에 따라 컴파일 타임에 선택 됩니다.

|정의 된 상수|문자 데이터 형식|
|----------------------|-------------------------|
|_UNICODE|와이드 문자|
|_MBCS|멀티 바이트 문자|
|아니면|싱글바이트 문자|
|Both|Undefined|

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

##  <a name="reversefind"></a>  CStringT::ReverseFind

이 `CStringT` 개체에서 마지막으로 일치 하는 문자를 검색 합니다.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>매개 변수

*ch*<br/>
검색할 문자입니다.

### <a name="return-value"></a>반환 값

이 개체에서 요청 된 문자와 일치 하는 마지막 문자의 `CStringT` 인덱스 (0부터 시작)이 고, 문자가 없으면-1입니다.

### <a name="remarks"></a>설명

함수는 런타임 함수와 `strrchr`유사 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

##  <a name="right"></a>  CStringT::Right

이`CStringT` 개체에서 마지막 (가장 오른쪽) *n 개수* 문자를 추출 하 고 추출 된 부분 문자열의 복사본을 반환 합니다.

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>매개 변수

*nCount*<br/>
이 `CStringT` 개체에서 추출할 문자의 수입니다.

### <a name="return-value"></a>반환 값

지정된 문자 범위의 복사본을 포함하는 `CStringT` 개체입니다. 반환 `CStringT` 된 개체는 비어 있을 수 있습니다.

### <a name="remarks"></a>설명

*N 수가* 문자열 길이를 초과 하면 전체 문자열이 추출 됩니다. `Right`basic의 인덱스는 0 `Right` 부터 시작 하는 점을 제외 하 고는 basic 함수와 비슷합니다.

MBCS (멀티 바이트 문자 집합)의 경우 *Ncount* 는 각 8 비트 문자를 참조 합니다. 즉, 한 멀티 바이트 문자의 선행 및 후행 바이트는 두 문자로 계산 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

##  <a name="setsysstring"></a>  CStringT::SetSysString

*Pstr* 가 가리키는 BSTR을 다시 할당 하 고 NULL 문자를 포함 `CStringT` 하 여 개체의 내용을 복사 합니다.

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>매개 변수

*pbstr*<br/>
문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

새 문자열입니다.

### <a name="remarks"></a>설명

`CStringT` 개체의 내용에 따라 *pstr* 에서 참조 하는 BSTR의 값이 변경 될 수 있습니다. 메모리가 부족 한 경우 `CMemoryException` 함수는을 throw 합니다.

이 함수는 일반적으로 자동화에 대 한 참조로 전달 된 문자열의 값을 변경 하는 데 사용 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

##  <a name="spanexcluding"></a>  CStringT::SpanExcluding

*PszCharSet*로 식별 되는 문자 집합에 없는 문자열에서 첫 번째 문자로 시작 하 여 문자를 추출 합니다.

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>매개 변수

*pszCharSet*<br/>
문자 집합으로 해석 되는 문자열입니다.

### <a name="return-value"></a>반환 값

문자열의 첫 번째 문자로 시작 하 여 *pszCharSet* 에 있는 첫 번째 문자로 끝나는 문자열의 *문자를 포함*하는 부분 문자열입니다 (즉, 첫 번째 문자로 시작). 문자열의 문자는 *pszCharSet*발견 된 문자열의 첫 번째 문자를 제외 합니다. *PszCharSet* 의 문자가 문자열에 없는 경우 전체 문자열을 반환 합니다.

### <a name="remarks"></a>설명

`SpanExcluding`*pszCharSet* 에서 첫 번째 문자 앞에 나오는 모든 문자를 추출 하 고 반환 합니다. 즉, *pszCharSet* 의 문자와 문자열에서 뒤에 오는 모든 문자는 반환 되지 않습니다. 문자열`SpanExcluding` 에서 *pszCharSet* 의 문자가 발견 되지 않으면는 전체 문자열을 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

##  <a name="spanincluding"></a>  CStringT::SpanIncluding

*PszCharSet*로 식별 되는 문자 집합에 있는 첫 번째 문자부터 시작 하 여 문자열에서 문자를 추출 합니다.

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>매개 변수

*pszCharSet*<br/>
문자 집합으로 해석 되는 문자열입니다.

### <a name="return-value"></a>반환 값

*PszCharSet*에 있는 문자열의 문자를 포함 하는 부분 문자열입니다 .이 문자열의 첫 번째 문자부터 시작 하 여 *pszCharSet*에 없는 문자열에 문자가 있는 경우 끝납니다. `SpanIncluding`문자열의 첫 번째 문자가 지정 된 집합에 없으면 빈 부분 문자열을 반환 합니다.

### <a name="remarks"></a>설명

문자열의 첫 문자가 문자 집합 `SpanIncluding` 에 없는 경우는 빈 문자열을 반환 합니다. 그렇지 않으면 집합에 있는 일련의 연속 문자를 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

##  <a name="tokenize"></a>  CStringT::Tokenize

대상 문자열에서 다음 토큰을 찾습니다.

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>매개 변수

*pszTokens*<br/>
토큰 구분 기호를 포함 하는 문자열입니다. 이러한 구분 기호의 순서는 중요 하지 않습니다.

*iStart*<br/>
검색을 시작할 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

현재 토큰 값을 포함 하는 개체입니다.`CStringT`

### <a name="remarks"></a>설명

함수 `Tokenize` 는 대상 문자열에서 다음 토큰을 찾습니다. *PszTokens* 의 문자 집합은 찾을 토큰의 가능한 구분 기호를 지정 합니다. 함수를 `Tokenize` 호출할 때마다 *istart*에서 시작 하 고 선행 구분 기호를 건너뛰고 다음 구분 기호 `CStringT` 문자 까지의 문자 문자열인 현재 토큰을 포함 하는 개체를 반환 합니다. *Istart* 의 값은 끝 구분 기호 문자 다음의 위치로 업데이트 되거나 문자열의 끝에 도달한 경우-1로 업데이트 됩니다. 다음 토큰을 읽을 문자열의 위치를 추적 하기 위해 *istart* 를 사용 하 여에 대 `Tokenize`한 일련의 호출로 대상 문자열의 나머지 부분에서 더 많은 토큰을 분할할 수 있습니다. 토큰이 더 이상 없는 경우 함수는 빈 문자열을 반환 하 고 *Istart* 는-1로 설정 됩니다.

[Strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md) `Tokenize` 와 같은 CRT 토큰화 함수와 달리 대상 문자열은 수정 되지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>설명

이 예제의 출력은 다음과 같습니다.

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

##  <a name="trim"></a>  CStringT::Trim

문자열에서 선행 및 후행 문자를 자릅니다.

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>매개 변수

*chTarget*<br/>
트리밍할 대상 문자입니다.

*pszTargets*<br/>
트리밍할 대상 문자를 포함 하는 문자열에 대 한 포인터입니다. *PszTarget* 의 모든 선행 및 후행 문자는 `CStringT` 개체에서 잘립니다.

### <a name="return-value"></a>반환 값

잘린 문자열을 반환 합니다.

### <a name="remarks"></a>설명

다음 중 하나의 선행 항목과 후행 항목을 모두 제거 합니다.

- *Chtarget*으로 지정 된 문자입니다.

- *PszTargets*로 지정 된 문자열에 있는 모든 문자입니다.

- 공백.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>설명

이 예제의 출력은 다음과 같습니다.

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

##  <a name="trimleft"></a>  CStringT::TrimLeft

문자열에서 선행 문자를 자릅니다.

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>매개 변수

*chTarget*<br/>
트리밍할 대상 문자입니다.

*pszTargets*<br/>
트리밍할 대상 문자를 포함 하는 문자열에 대 한 포인터입니다. *PszTarget* 의 모든 선행 문자는 `CStringT` 개체에서 잘립니다.

### <a name="return-value"></a>반환 값

잘린 결과 문자열입니다.

### <a name="remarks"></a>설명

다음 중 하나의 선행 항목과 후행 항목을 모두 제거 합니다.

- *Chtarget*으로 지정 된 문자입니다.

- *PszTargets*로 지정 된 문자열에 있는 모든 문자입니다.

- 공백.

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

##  <a name="trimright"></a>  CStringT::TrimRight

문자열에서 후행 문자를 잘라냅니다.

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>매개 변수

*chTarget*<br/>
트리밍할 대상 문자입니다.

*pszTargets*<br/>
트리밍할 대상 문자를 포함 하는 문자열에 대 한 포인터입니다. *PszTarget* 의 후행 문자는 모두 `CStringT` 개체에서 잘립니다.

### <a name="return-value"></a>반환 값

잘린 문자열 `CStringT` 을 포함 하는 개체를 반환 합니다.

### <a name="remarks"></a>설명

다음 중 하나의 후행 항목을 제거 합니다.

- *Chtarget*으로 지정 된 문자입니다.

- *PszTargets*로 지정 된 문자열에 있는 모든 문자입니다.

- 공백.

버전 `CStringT& TrimRight(XCHAR chTarget)` 은 하나의 문자 매개 변수를 허용 하 고 문자열 데이터의 `CStringT` 끝에서 해당 문자의 모든 복사본을 제거 합니다. 문자열의 끝부터 시작 하 여 앞으로 작동 합니다. 다른 문자 `CSTringT` 를 찾거나에서 문자 데이터가 부족할 때 중지 됩니다.

버전 `CStringT& TrimRight(PCXSTR pszTargets)` 은 검색할 다른 모든 문자를 포함 하는 null로 끝나는 문자열을 허용 합니다. `CStringT` 개체의 해당 문자에 대 한 모든 복사본을 제거 합니다. 문자열의 끝에서 시작 하 여 앞으로 작동 합니다. 대상 문자열 `CStringT` 에 없는 문자를 찾거나에서 문자 데이터가 부족할 때 중지 됩니다. 전체 대상 문자열을의 `CStringT`끝 부분에 있는 부분 문자열과 일치 시 키 지 않습니다.

버전 `CStringT& TrimRight()` 에는 매개 변수가 필요 하지 않습니다. `CStringT` 문자열의 끝에서 후행 공백 문자를 모두 자릅니다. 공백 문자는 줄 바꿈, 공백 또는 탭 일 수 있습니다.

-

### <a name="example"></a>예제

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>참고자료

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT 클래스](../../atl-mfc-shared/reference/csimplestringt-class.md)
