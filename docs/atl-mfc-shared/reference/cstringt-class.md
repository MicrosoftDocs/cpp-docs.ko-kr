---
title: CStringT 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f8a66f87b3c4a2c6712a1db93f97361a25b6955
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366629"
---
# <a name="cstringt-class"></a>CStringT 클래스
이 클래스는 나타냅니다는 `CStringT` 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```  
 
template<typename BaseType, class StringTraits>  
class CStringT :   
public CSimpleStringT<BaseType,
                      _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                      ::c_bIsMFCDLLTraits>  
 
```  
  
#### <a name="parameters"></a>매개 변수  
 `BaseType`  
 String 클래스의 문자 형식입니다. 다음 중 하나일 수 있습니다.  
  
- `char` (용 ANSI 문자열)입니다.  
  
- `wchar_t` (용 유니코드 문자열)입니다.  
  
- **TCHAR** (ANSI 및 유니코드 문자열)에 대 한 합니다.  
  
 `StringTraits`  
 String 클래스 경우 런타임은 CRT (C) 라이브러리 지원 및 문자열 리소스를 찾는 필요를 결정 합니다. 다음 중 하나일 수 있습니다.  
  
- **StrTraitATL < wchar_t** &#124; `char` &#124; **TCHAR, ChTraitsCRT < wchar_t** &#124; `char` &#124; **TCHAR >>**  
  
     클래스에 지정 된 모듈에서 리소스 문자열을 검색 하 고 CRT 지원에 필요한 `m_hInstResource` (응용 프로그램의 모듈 클래스의 멤버).  
  
- **StrTraitATL < wchar_t** &#124; `char` &#124; **TCHAR, ChTraitsOS < wchar_t** &#124; `char` &#124; **TCHAR >>**  
  
     클래스는 CRT 지원 및 리소스 문자열에 지정 된 모듈에 대해 검색 필요 하지 `m_hInstResource` (응용 프로그램의 모듈 클래스의 멤버).  
  
- **StrTraitMFC < wchar_t** &#124; `char` &#124; **TCHAR, ChTraitsCRT < wchar_t** &#124; `char` &#124; **TCHAR >>**  
  
     클래스에는 CRT 지원 및 표준 MFC 검색 알고리즘을 사용 하 여 리소스 문자열을 검색 합니다.  
  
- **StrTraitMFC < wchar_t** &#124; `char` &#124; **TCHAR, ChTraitsOS < wchar_t** &#124; `char` &#124; **TCHAR >>**  
  
     클래스에는 CRT 지원 및 표준 MFC 검색 알고리즘을 사용 하 여 리소스 문자열을 검색 필요 하지 않습니다.  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CStringT::CStringT](#cstringt)|생성 된 `CStringT` 다양 한 방법으로 개체입니다.|  
|[CStringT:: ~ CStringT](#_dtorcstringt)|`CStringT` 개체를 제거합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CStringT::AllocSysString](#allocsysstring)|할당 한 `BSTR` 에서 `CStringT` 데이터입니다.|  
|[CStringT::AnsiToOem](#ansitooem)|ANSI 문자 집합을 OEM 문자 집합으로 내부 변환을 만듭니다.|  
|[CStringT::AppendFormat](#appendformat)|서식이 지정 된 데이터를 기존 추가 `CStringT` 개체입니다.|  
|[CStringT::Collate](#collate)|(대 소문자를 구분, 사용 하 여 로캘 관련 정보)에 두 문자열을 비교 합니다.|  
|[CStringT::CollateNoCase](#collatenocase)|(대/소문자를 구분 하지 않는, 사용 하 여 로캘 관련 정보)에 두 문자열을 비교 합니다.|  
|[CStringT::Compare](#compare)|두 문자열 (대/소문자 구분)을 비교 합니다.|  
|[CStringT::CompareNoCase](#comparenocase)|두 문자열 (대/소문자 구분)을 비교 합니다.|  
|[CStringT::Delete](#delete)|문자열에서 문자 또는 문자를 삭제합니다.|  
|[CStringT::Find](#find)|문자 또는 더 큰 문자열 내의 하위 문자열을 찾습니다.|  
|[CStringT::FindOneOf](#findoneof)|집합에서 일치 하는 첫 번째 문자를 찾습니다.|  
|[CStringT::Format](#format)|으로 된 문자열의 형식을 `sprintf` 않습니다.|  
|[CStringT::FormatMessage](#formatmessage)|메시지 문자열의 형식을 지정 합니다.|  
|[CStringT::FormatMessageV](#formatmessagev)|가변 인수 목록을 사용 하 여 메시지 문자열의 형식을 지정 합니다.|  
|[CStringT::FormatV](#formatv)|가변 인수 목록을 사용 하 여 문자열의 형식을 지정 합니다.|  
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|문자열의 지정한 환경 변수 값으로 설정합니다.|  
|[CStringT::Insert](#insert)|문자열 내에서 지정된 된 인덱스에서 단일 문자 또는 부분 문자열을 삽입합니다.|  
|[CStringT::Left](#left)|문자열의 왼쪽된 부분을 추출합니다.|  
|[CStringT::LoadString](#loadstring)|기존 로드 `CStringT` Windows 리소스에서 개체입니다.|  
|[CStringT::MakeLower](#makelower)|이 문자열을 소문자로에 있는 모든 문자가 변환 합니다.|  
|[CStringT::MakeReverse](#makereverse)|문자열을 반대로 바꿉니다.|  
|[CStringT::MakeUpper](#makeupper)|이 문자열을 대문자로에 있는 모든 문자가 변환 합니다.|  
|[CStringT::Mid](#mid)|문자열의 가운데 부분을 추출합니다.|  
|[CStringT::OemToAnsi](#oemtoansi)|OEM 문자 집합에서 ANSI 문자 집합을 변환 하는 내부 변환을 만듭니다.|  
|[CStringT::Remove](#remove)|제거는 문자열에서 문자를 표시 합니다.|  
|[CStringT::Replace](#replace)|대체 문자 다른 문자와 함께 표시 됩니다.|  
|[CStringT::ReverseFind](#reversefind)|더 큰 문자열; 내 문자를 찾습니다. 끝에서 시작합니다.|  
|[CStringT::Right](#right)|문자열의 오른쪽 부분을 추출합니다.|  
|[CStringT::SetSysString](#setsysstring)|기존 설정 `BSTR` 개체의 데이터로 `CStringT` 개체입니다.|  
|[CStringT::SpanExcluding](#spanexcluding)|로 식별 되는 문자 집합에 없는 첫 번째 문자로 시작 하는 문자열에서 문자를 추출 `pszCharSet`합니다.|  
|[CStringT::SpanIncluding](#spanincluding)|집합의 문자만 포함 된 하위 문자열을 추출 합니다.|  
|[CStringT::Tokenize](#tokenize)|추출 대상 문자열에 토큰을 지정 합니다.|  
|[CStringT::Trim](#trim)|문자열에서 선행 및 후행 공백 문자를 모두 삭제합니다.|  
|[CStringT::TrimLeft](#trimleft)|문자열에서 선행 공백 문자를 삭제.|  
|[CStringT::TrimRight](#trimright)|후행 공백 문자는 문자열에서 삭제.|  
  
### <a name="operators"></a>연산자  
  
|||  
|-|-|  
|[operator =](#operator_eq)|에 새 값을 할당 한 `CStringT` 개체입니다.|  
|[CStringT::operator +](#operator_add)|두 문자열 또는 문자 및 문자열을 연결합니다.|  
|[CStringT::operator + =](#operator_add_eq)|기존 문자열의 끝에 새 문자열을 연결합니다.|  
|[CStringT::operator = =](#operator_eq_eq)|두 문자열은 논리적으로 동일한 경우를 결정 합니다.|  
|[CStringT::operator! =](#operator_neq)|두 문자열 하지 논리적으로 같은지 확인 합니다.|  
|[CStringT::operator &lt;](#operator_lt)|연산자의 왼쪽에 문자열 보다 작은 있는지 여부를 결정 오른쪽에 문자열입니다.|  
|[CStringT::operator &gt;](#operator_gt)|문자열 연산자의 왼쪽에서 오른쪽에 문자열 보다 큰 인지 여부를 확인 합니다.|  
|[CStringT::operator &lt;=](#operator_lt_eq)|문자열 연산자의 왼쪽에서 오른쪽에 문자열 보다 작거나 인지 여부를 확인 합니다.|  
|[CStringT::operator &gt;=](#operator_gt_eq)|문자열 연산자의 왼쪽에서 오른쪽에 문자열 보다 크거나 인지 여부를 확인 합니다.|  
  
## <a name="remarks"></a>설명  
 `CStringT` 상속 [CSimpleStringT 클래스](../../atl-mfc-shared/reference/csimplestringt-class.md)합니다. 순서 지정 및 검색, 문자 조작 같은 고급 기능을 구현 `CStringT`합니다.  
  
> [!NOTE]
> `CStringT` 개체는 예외를 throw 할 수 있습니다. 이럴 때는 `CStringT` 개체 어떤 이유로 든 메모리가 부족 합니다.  
  
 A `CStringT` 개체의 가변 길이 문자 시퀀스로 구성 됩니다. `CStringT` 함수 및 연산자의 Basic 것과 비슷한 구문을 사용 하 여 제공 합니다. 연결 및 간소화 된 메모리 관리와 함께 비교 연산자 확인 `CStringT` 개체 일반 문자 배열 보다 사용 하기 쉽습니다.  
  
> [!NOTE]
>  만들 수 있지만 `CStringT` 에 대 한 권장 인스턴스를 포함 하는 null 문자를 포함 합니다. 메서드 및 연산자를 호출 `CStringT` 포함 된 null 문자를 포함 하는 개체에 의도 하지 않은 결과가 발생할 수 있습니다.  
  
 다양 한 조합을 사용 하 여는 `BaseType` 및 `StringTraits` 매개 변수를 `CStringT` 수는 다음 형식에서 돌아와가 미리 정의한 ATL 라이브러리 개체입니다.  
  
 ATL 응용 프로그램에서 사용 하 여 하는 경우:  
  
 `CString``CStringA`, 및 `CStringW` (MFC90 MFC DLL에서 내보낸. DLL), 사용자 Dll에서 하지 않습니다. 이렇게 하지 않으려면 `CStringT` 에서 여러 번 정의 되 고 있습니다.  
  
> [!NOTE]
>  코드에 설명 된 링커 오류에 대 한 해결을 포함 하는 경우 [Linking Errors When You Import CString-Derived 클래스 "(Q309801)](https://support.microsoft.com/help/309801/you-may-receive-an-lnk2019-error-message-when-you-build-a-visual-c-200), 해당 코드를 제거 해야 합니다. 더 이상 필요 없는 합니다.  
  
 다음 문자열 유형은 MFC 기반 응용 프로그램 내에서 사용할 수 있습니다.  
  
|CStringT 유형|선언|  
|-------------------|-----------------|  
|`CStringA`|ANSI 문자 CRT 지 원하는 문자열을 입력 합니다.|  
|`CStringW`|유니코드 문자는 CRT 지 원하는 문자열을 입력 합니다.|  
|`CString`|CRT 지 원하는 ANSI 및 유니코드 문자 형식입니다.|  
  
 다음 문자열에 사용할 수 있는 유형은 프로젝트 위치 **ATL_CSTRING_NO_CRT** 정의 됩니다.  
  
|CStringT 유형|선언|  
|-------------------|-----------------|  
|**CAtlStringA**|ANSI 문자 CRT 지원 하지 않는 문자열을 입력 합니다.|  
|**CAtlStringW**|유니코드 문자는 CRT 지원 하지 않는 문자열을 입력 합니다.|  
|**CAtlString**|CRT 지원 하지 않는 ANSI 및 유니코드 문자 형식입니다.|  
  
 다음 문자열에 사용할 수 있는 유형은 프로젝트 위치 **ATL_CSTRING_NO_CRT** 정의 되어 있지 않습니다.  
  
|CStringT 유형|선언|  
|-------------------|-----------------|  
|**CAtlStringA**|ANSI 문자 CRT 지 원하는 문자열을 입력 합니다.|  
|**CAtlStringW**|유니코드 문자는 CRT 지 원하는 문자열을 입력 합니다.|  
|**CAtlString**|CRT 지 원하는 ANSI 및 유니코드 문자 형식입니다.|  
  
 `CString` 개체의도 특징이 있습니다.  
  
- `CStringT` 개체는 연결 작업의 결과로 증가할 수 있습니다.  
  
- `CStringT` 개체는 준수 "의미 체계를 값입니다." 에 참여 한 `CStringT` 실제 문자열로, 문자열에 대 한 포인터가 아니라 개체입니다.  
  
-   대신 자유롭게 사용할 수 있습니다 `CStringT` 개체에 대 한 `PCXSTR` 함수 인수입니다.  
  
-   문자열 버퍼에 대 한 사용자 지정 메모리 관리 합니다. 자세한 내용은 참조 [메모리 관리 및 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)합니다.  
  
## <a name="cstringt-predefined-types"></a>CStringT 미리 정의 된 형식  
 때문에 `CStringT` 템플릿 인수를 사용 하 여 문자 형식 정의 (두 [wchar_t](../../c-runtime-library/standard-types.md) 또는 [char](../../c-runtime-library/standard-types.md)) 지원, 메서드 매개 변수 형식을 복잡할 수 시간에 있습니다. 이 문제를 단순화 하려면 미리 정의 된 형식 집합이 정의 되 고 전체에서 사용 된 `CStringT` 클래스입니다. 다음 표에서 다양 한 형식을 보여 줍니다.  
  
|이름|설명|  
|----------|-----------------|  
|`XCHAR`|단일 문자 (중 하나 `wchar_t` 또는 `char`)와 같은 문자 형식으로는 `CStringT` 개체입니다.|  
|**YCHAR**|단일 문자 (중 하나 `wchar_t` 또는 `char`) 반대 문자 형식으로 `CStringT` 개체입니다.|  
|`PXSTR`|문자열에 대 한 포인터 (중 하나 `wchar_t` 또는 `char`)와 같은 문자 형식으로는 `CStringT` 개체입니다.|  
|**PYSTR**|문자열에 대 한 포인터 (중 하나 `wchar_t` 또는 `char`) 반대 문자 형식으로 `CStringT` 개체입니다.|  
|`PCXSTR`|에 대 한 포인터는 **const** 문자열 (중 하나 `wchar_t` 또는 `char`)와 같은 문자 형식으로는 `CStringT` 개체입니다.|  
|**PCYSTR**|에 대 한 포인터는 **const** 문자열 (중 하나 `wchar_t` 또는 `char`) 반대 문자 형식으로 `CStringT` 개체입니다.|  
  
> [!NOTE]
>  이전에 문서화 되지 않은 메서드를 사용 하는 코드 `CString` (같은 **AssignCopy**)는 다음과 같은 문서화 된 방법을 사용 하는 코드로 바꾸어야 `CStringT` (같은 `GetBuffer` 또는 `ReleaseBuffer`). 이러한 메서드는 상속 `CSimpleStringT`합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)  
  
 `CStringT`  
  
## <a name="requirements"></a>요구 사항  
  
|Header|에 대 한 사용|  
|------------|-------------|  
|cstringt.h|MFC 전용 string 개체|  
|atlstr.h|비 MFC 문자열 개체|  
  
##  <a name="allocsysstring"></a>  CStringT::AllocSysString  
 자동화 호환 문자열 형식의 할당 `BSTR` 의 내용을 복사 하 고는 `CStringT` null 종결 문자를 포함 하 여 메서드를 개체입니다.  
  
```  
BSTR AllocSysString() const;  
```  
  
### <a name="return-value"></a>반환 값  
 새로 할당 된 문자열입니다.  
  
### <a name="remarks"></a>설명  
 MFC 프로그램의 한 [CMemoryException 클래스](../../mfc/reference/cmemoryexception-class.md) 메모리가 부족 하 여 없으면 throw 됩니다. ATL 프로그램에는 [CAtlException](../../atl/reference/catlexception-class.md) throw 됩니다. 이 함수는 자동화에 대 한 문자열을 반환 하려면 일반적으로 사용 됩니다.  
  

 일반적으로이 문자열은 COM 함수에 전달 하는 경우 매개 변수를 다음이 필요 호출자가 문자열을 해제 하는 [in]로 합니다. 사용 하 여이 작업을 수행할 수 있습니다 [SysFreeString](https://msdn.microsoft.com/library/windows/desktop/ms221481.aspx)Windows SDK에 설명 된 대로 합니다. 자세한 내용은 참조 [BSTR에 대해 메모리를 해제 하 고 Allocating](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)합니다.  
  
 Windows에서 OLE 할당 함수에 대 한 자세한 내용은 참조 [SysAllocString](https://msdn.microsoft.com/library/windows/desktop/ms221458.aspx) Windows sdk에서입니다.  

  
### <a name="example"></a>예제  
 다음 예에서는 `CStringT::AllocSysString`의 사용법을 보여줍니다.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]  
  
##  <a name="ansitooem"></a>  CStringT::AnsiToOem  
 이에 있는 모든 문자가 변환 `CStringT` ANSI 문자 집합을 OEM 문자 집합에서에서 개체입니다.  
  
```  
void AnsiToOem();
```  
  
### <a name="remarks"></a>설명  
 함수를 사용할 수 없는 경우 `_UNICODE` 정의 됩니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]  
  
##  <a name="appendformat"></a>  CStringT::AppendFormat  
 서식이 지정 된 데이터를 기존 추가 `CStringT` 개체입니다.  
  
```  
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```  
  
### <a name="parameters"></a>매개 변수  
 `pszFormat`  
 형식 컨트롤 문자열입니다.  
  
 `nFormatID`  
 형식 컨트롤 문자열을 포함 하는 문자열 리소스 식별자입니다.  
  
 `argument`  
 선택적 인수입니다.  
  
### <a name="remarks"></a>설명  
 서식을 지정 하 고 일련의 문자 및 값에 추가 하는이 함수는 `CStringT`합니다. 각 선택적 인수 (있는 경우)이 변환 되 고 해당 형식 사양에 따라 추가 `pszFormat` 또는 식별 되는 문자열 리소스에서 `nFormatID`합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]  
  
##  <a name="collate"></a>  CStringT::Collate  
 제네릭 텍스트 함수를 사용 하 여 두 문자열을 비교 `_tcscoll`합니다.  
  
```  
int Collate(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `psz`  
 다른 문자열 비교에 사용 됩니다.  
  
### <a name="return-value"></a>반환 값  
 <이 경우 0, 0 문자열이 동일한 경우 `CStringT` 개체는 보다 작은 `psz`, 또는 > 0이 `CStringT` 개체 보다 크면 `psz`합니다.  
  
### <a name="remarks"></a>설명  
 제네릭 텍스트 함수인 `_tcscoll`, TCHAR에 정의 된 합니다. H, 하거나 매핑됩니다 `strcoll`, `wcscoll`, 또는 `_mbscoll`컴파일 타임에 정의 된 문자 집합에 따라 합니다. 각 함수에 따라 사용 중인 코드 페이지에 따라 문자열의 대/소문자 구분 비교를 수행 하는 현재 합니다. 자세한 내용은 참조 [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)합니다.  
  
##  <a name="collatenocase"></a>  CStringT::CollateNoCase  
 제네릭 텍스트 함수를 사용 하 여 두 문자열을 비교 `_tcscoll`합니다.  
  
```  
int CollateNoCase(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `psz`  
 다른 문자열 비교에 사용 됩니다.  
  
### <a name="return-value"></a>반환 값  
 문자열이 없으면 0 동일한 (대/소문자 무시), < 0이 `CStringT` 개체는 보다 작은 `psz` (대/소문자 무시) 또는 > 0이 `CStringT` 개체 보다 크면 `psz` (대/소문자 무시).  
  
### <a name="remarks"></a>설명  
 제네릭 텍스트 함수인 `_tcscoll`, TCHAR에 정의 된 합니다. H, 하거나 매핑됩니다 `stricoll`, `wcsicoll`, 또는 `_mbsicoll`컴파일 타임에 정의 된 문자 집합에 따라 합니다. 각 함수에서 현재 사용 중인 코드 페이지에 따라는 문자열의 대/소문자 구분 비교를 수행 합니다. 자세한 내용은 참조 [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]  
  
##  <a name="compare"></a>  CStringT::Compare  
 두 문자열 (대/소문자 구분)을 비교 합니다.  
  
```  
int Compare(PCXSTR psz) const; 
```  
  
### <a name="parameters"></a>매개 변수  
 `psz`  
 다른 문자열 비교에 사용 됩니다.  
  
### <a name="return-value"></a>반환 값  
 <이 경우 0, 0 문자열이 동일한 경우 `CStringT` 개체는 보다 작은 `psz`, 또는 > 0이 `CStringT` 개체 보다 크면 `psz`합니다.  
  
### <a name="remarks"></a>설명  
 제네릭 텍스트 함수인 `_tcscmp`, TCHAR에 정의 된 합니다. H, 하거나 매핑됩니다 `strcmp`, `wcscmp`, 또는 `_mbscmp`컴파일 타임에 정의 된 문자 집합에 따라 합니다. 각 함수는 문자열의 대/소문자 구분 비교를 수행 하 고 로캘에 의해 영향을 받지 않습니다. 자세한 내용은 참조 [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)합니다.  
  
 문자열에 내장된 된 null이 있으면 비교의 목적을 위해 문자열 포함 된 첫 번째 null 문자에서 잘린 것으로 간주 됩니다.  
  
### <a name="example"></a>예제  
 다음 예에서는 `CStringT::Compare`의 사용법을 보여줍니다.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]  
  
##  <a name="comparenocase"></a>  CStringT::CompareNoCase  
 두 문자열 (대/소문자 구분)을 비교 합니다.  
  
```  
int CompareNoCase(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `psz`  
 다른 문자열 비교에 사용 됩니다.  
  
### <a name="return-value"></a>반환 값  
 문자열이 동일한 경우 0 (대/소문자 무시), < 0이 `CStringT` 개체는 보다 작은 `psz` (대/소문자 무시) 또는 > 0이 `CStringT` 개체 보다 크면 `psz` (대/소문자 무시).  
  
### <a name="remarks"></a>설명  
 제네릭 텍스트 함수인 `_tcsicmp`, TCHAR에 정의 된 합니다. H, 하거나 매핑됩니다 `_stricmp`, `_wcsicmp` 또는 `_mbsicmp`컴파일 타임에 정의 된 문자 집합에 따라 합니다. 각 함수는 문자열의 대/소문자 구분 비교를 수행합니다. 비교에 따라 달라 집니다는 `LC_CTYPE` 로캘의 측면 아닌 `LC_COLLATE`합니다. 자세한 내용은 참조 [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)합니다.  
  
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
 `pch`  
 길이 문자 배열에 대 한 포인터 `nLength`null로 끝나는 없습니다.  
  
 `nLength`  
 에 있는 문자의 수 `pch`합니다.  
  
 `ch`  
 단일 문자입니다.  
  
 `pszSrc`  
 이 복사 되는 null로 끝나는 문자열 `CStringT` 개체입니다.  
  
 `pStringMgr`  
 에 대 한 메모리 관리자에 대 한 포인터는 `CStringT` 개체입니다. 대 한 자세한 내용은 `IAtlStringMgr` 및 메모리 관리에 대 한 `CStringT`, 참조 [CStringT 클래스를 사용한 메모리 관리](../../atl-mfc-shared/memory-management-with-cstringt.md)합니다.  
  
 `strSrc`  
 기존 `CStringT` 이 복사 되는 개체 `CStringT` 개체입니다. 대 한 자세한 내용은 `CThisString` 및 `CThisSimpleString`, 설명 섹션을 참조 합니다.  
  
 `varSrc`  
 이 복사 되는 variant 개체 `CStringT` 개체입니다.  
  
 `BaseType`  
 String 클래스의 문자 형식입니다. 다음 중 하나일 수 있습니다.  
  
 `char` (용 ANSI 문자열)입니다.  
  
 `wchar_t` (용 유니코드 문자열)입니다.  
  
 `TCHAR` (문자열에 대 한 ANSI 및 유니코드 문자)입니다.  
  
 `bMFCDLL`  
 프로젝트는 MFC DLL (TRUE) 인지 여부를 지정 하는 부울 값 (FALSE)입니다.  
  
 `SystemString`  
 해야 `System::String`, 및 /clr을 사용한 프로젝트를 컴파일해야 합니다.  
  
 `pString`  
 에 대 한 핸들을 `CStringT` 개체입니다.  
  
### <a name="remarks"></a>설명  
 알고 있어야 새 할당 된 저장소에 입력된 데이터를 복사 하는 생성자를 때문에 메모리 예외가 발생할 수 있습니다. 이러한 생성자 중 일부는 역할 변환 함수를 참고 합니다. 예를 들어, 대체할 수 있습니다는 `LPTSTR` 여기서는 `CStringT` 개체가 필요 합니다.  
  
- `CStringT`( `LPCSTR` `lpsz` ): 유니코드 생성 `CStringT` ANSI 문자열에서 합니다. 또한 다음 예제에서와 같이 문자열 리소스를 로드이 생성자를 사용할 수 있습니다.  
  
- `CStringT(` `LPCWSTR` `lpsz` ): 생성 된 `CStringT` 유니코드 문자열에서입니다.  
  
- `CStringT`( `const unsigned char*` `psz` ): 생성할 수는 `CStringT` 에 대 한 포인터에서 `unsigned char`합니다.  
  
> [!NOTE]
>  정의 **_CSTRING_DISABLE_NARROW_WIDE_CONVERSION** 간의 암시적 문자열 변환 하지 않으려면 매크로 [!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)] 및 [!INCLUDE[TLA#tla_unicode](../../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] 문자열입니다. 매크로는 변환을 지 원하는 컴파일 생성자에서 제외 합니다.  
  
 `strSrc` 매개 변수 수는 `CStringT` 또는 `CThisSimpleString` 개체입니다. 에 대 한 `CStringT`, 기본 인스턴스와 중 하나를 사용 하 여 ( `CString`, `CStringA`, 또는 `CStringW`);에 대 한 `CThisSimpleString`를 사용 하 여는 `this` 포인터입니다. `CThisSimpleString` 인스턴스를 선언 된 [CSimpleStringT 클래스](../../atl-mfc-shared/reference/csimplestringt-class.md), 보다 작은 기본 제공 기능으로는 더 작은 문자열 클래스인는 `CStringT` 클래스입니다.  
  
 연산자를 오버 로드 `CSimpleStringT<>&()` 생성 한 `CStringT` 에서 개체는 `CSimpleStringT` 선언 합니다.  
  
> [!NOTE]
>  만들 수 있지만 `CStringT` 에 대 한 권장 인스턴스를 포함 하는 null 문자를 포함 합니다. 메서드 및 연산자를 호출 `CStringT` 포함 된 null 문자를 포함 하는 개체에 의도 하지 않은 결과가 발생할 수 있습니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]  
  
##  <a name="_dtorcstringt"></a>  CStringT:: ~ CStringT  
 소멸 된 `CStringT` 개체입니다.  
  
```  
~CStringT() throw();
```  
  
### <a name="remarks"></a>설명  
 소멸 된 `CStringT` 개체입니다.  
  
##  <a name="delete"></a>  CStringT::Delete  
 지정된 된 인덱스에서 문자로 시작 하는 문자열에서 문자 또는 문자를 삭제 합니다.  
  
```  
int Delete(int iIndex, int nCount = 1);
```  
  
### <a name="parameters"></a>매개 변수  
 `iIndex`  
 첫 번째 문자의 0부터 시작 인덱스는 `CStringT` 삭제할 개체입니다.  
  
 `nCount`  
 제거할 문자 수를 지정 합니다.  
  
### <a name="return-value"></a>반환 값  
 변경 된 문자열의 길이입니다.  
  
### <a name="remarks"></a>설명  
 경우 `nCount` 문자열의 나머지 문자열이 제거 되므로 보다 깁니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]  
  
```Output  
Before: Soccer is best,
    but hockey is quicker!  
After: Soccer best,
    but hockey is quicker!  
```  
  
##  <a name="find"></a>  CStringT::Find  
 문자 또는 부분 문자열의 첫 번째 일치 항목에 대 한이 문자열을 검색합니다.  
  
```  
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `pszSub`  
 검색할 부분 문자열입니다.  
  
 `iStart`  
 를 사용 하 여 검색을 시작 하는 문자열 또는 0부터에서 시작 하는 문자의 인덱스입니다.  
  
 `ch`  
 검색할 단일 문자입니다.  
  
### <a name="return-value"></a>반환 값  
 이 첫 번째 문자의 0부터 시작 인덱스 `CStringT` 요청한 하위 문자열 또는 문자를 일치 하는 개체; 하위 문자열 또는 문자 발견 되지 않으면-1입니다.  
  
### <a name="remarks"></a>설명  
 함수는 단일 문자를 모두 허용 하도록 오버 로드 (실행 시 함수 처럼 `strchr`) 및 문자열 (비슷합니다 `strstr`).  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]  
  
##  <a name="findoneof"></a>  CStringT::FindOneOf  
 이 문자열에 포함 된 모든 문자와 일치 하는 첫 번째 문자에 대 한 검색 `pszCharSet`합니다.  
  
```  
int FindOneOf(PCXSTR pszCharSet) const throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `pszCharSet`  
 일치에 대 한 문자를 포함 하는 문자열입니다.  
  
### <a name="return-value"></a>반환 값  
 또한이 문자열의 첫 번째 문자의 0부터 시작 인덱스 `pszCharSet`; 일치 하는 경우-1입니다.  
  
### <a name="remarks"></a>설명  
 에 문자의 첫 번째 항목을 찾습니다 `pszCharSet`합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]  
  
##  <a name="format"></a>  CStringT::Format  
 서식이 지정 된 데이터를 씁니다는 `CStringT` 같은 방식으로 [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) C 스타일 문자 배열에 데이터의 형식을 지정 합니다.  
  
```  
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```  
  
### <a name="parameters"></a>매개 변수  
 `nFormatID`  
 형식 컨트롤 문자열을 포함 하는 문자열 리소스 식별자입니다.  
  
 `pszFormat`  
 형식 컨트롤 문자열입니다.  
  
 `argument`  
 선택적 인수입니다.  
  
### <a name="remarks"></a>설명  
 포맷 하 고 일련의 문자 및 값을 저장 하는이 함수는 `CStringT`합니다. 각 선택적 인수 (있는 경우) 변환 되어 해당 형식 사양에 따라 출력 `pszFormat` 또는 식별 되는 문자열 리소스에서 `nFormatID`합니다.  
  
 문자열 개체 자체에 대 한 매개 변수로 제공 되는 호출이 실패 `Format`합니다. 예를 들어 다음 코드를 사용 하면 예기치 않은 결과:  
  
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
 `nFormatID`  
 형식이 지정 되지 않은 메시지 텍스트가 포함 된 문자열 리소스 식별자입니다.  
  
 `pszFormat`  
 형식 컨트롤 문자열을 가리킵니다. 삽입을 위해 검색 고 그에 따라 서식이 지정 될 됩니다. 서식 문자열은 실행 시간 함수와 비슷합니다 `printf`-매개 변수는 임의의 순서로 삽입할 수를 고려한 점을 제외 하 고 형식 문자열 스타일입니다.  
  
 `argument`  
 선택적 인수입니다.  
  
### <a name="remarks"></a>설명  
 함수는 입력으로 메시지 정의 필요 합니다. 메시지 정의 의해 결정 됩니다 `pszFormat` 또는 식별 되는 문자열 리소스에서 `nFormatID`합니다. 서식이 지정 된 메시지 텍스트를 복사 하는 함수는 `CStringT` 처리 포함 된 모든 개체를 요청 하는 경우 시퀀스를 삽입 합니다.  
  
> [!NOTE]
> `FormatMessage` 새로 형식이 지정 된 문자열에 대 한 시스템 메모리를 할당 하려고 시도 합니다. 이 시도가 실패 하면 메모리 예외를 자동으로 throw 됩니다.  
  
 각 삽입에 해당 매개 변수 다음 있어야 합니다.는 `pszFormat` 또는 `nFormatID` 매개 변수입니다. 메시지 텍스트 내에서 동적으로 메시지 서식을 지정 하기 위한 몇 가지 이스케이프 시퀀스는 지원 됩니다. 자세한 내용은 참조는 Windows [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) Windows SDK에는 함수입니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]  
  
##  <a name="formatmessagev"></a>  CStringT::FormatMessageV  
 가변 인수 목록을 사용 하 여 메시지 문자열의 형식을 지정 합니다.  
  
```  
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```  
  
### <a name="parameters"></a>매개 변수  
 `pszFormat`  
 형식 컨트롤 문자열을 가리킵니다. 삽입을 위해 검색 고 그에 따라 서식이 지정 될 됩니다. 서식 문자열은 실행 시간 함수와 비슷합니다 `printf`-매개 변수는 임의의 순서로 삽입할 수를 고려한 점을 제외 하 고 형식 문자열 스타일입니다.  
  
 `pArgList`  
 인수 목록에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 함수를 입력으로 메시지 정의 필요에 따른 `pszFormat`합니다. 서식이 지정 된 메시지 텍스트와 변수를 인수 목록에서 함수는 복사는 `CStringT` 처리 포함 된 모든 개체를 요청 하는 경우 시퀀스를 삽입 합니다.  
  
> [!NOTE]
> `FormatMessageV` 호출 [CStringT::FormatMessage](#formatmessage), 새로 형식이 지정 된 문자열에 대 한 시스템 메모리를 할당 하려고 하 합니다. 이 시도가 실패 하면 메모리 예외를 자동으로 throw 됩니다.  
  
 자세한 내용은 참조는 Windows [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) Windows SDK에는 함수입니다.  
  
##  <a name="formatv"></a>  CStringT::FormatV  
 가변 인수 목록을 사용 하 여 메시지 문자열의 형식을 지정 합니다.  
  
```  
void FormatV(PCXSTR pszFormat, va_list args);
```  
  
### <a name="parameters"></a>매개 변수  
 `pszFormat`  
 형식 컨트롤 문자열을 가리킵니다. 삽입을 위해 검색 고 그에 따라 서식이 지정 될 됩니다. 서식 문자열은 실행 시간 함수와 비슷합니다 `printf`-매개 변수는 임의의 순서로 삽입할 수를 고려한 점을 제외 하 고 형식 문자열 스타일입니다.  
  
 `args`  
 인수 목록에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 서식이 지정 된 문자열과에 인수의 변수 목록 작성는 `CStringT` 문자열 같은 방식으로 `vsprintf_s` C 스타일 문자 배열에 데이터의 형식을 지정 합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]  
  
##  <a name="getenvironmentvariable"></a>  CStringT::GetEnvironmentVariable  
 문자열의 지정한 환경 변수 값으로 설정합니다.  
  
```  
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```  
  
### <a name="parameters"></a>매개 변수  
 `pszVar`  
 환경 변수를 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 0이 아니고, 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 호출 프로세스의 환경 블록에서 지정 된 변수의 값을 검색합니다. 값 형식이 문자의 null로 끝나는 문자열의 형식입니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]  
  
##  <a name="insert"></a>  CStringT::Insert  
 문자열 내에서 지정된 된 인덱스에서 단일 문자 또는 부분 문자열을 삽입합니다.  
  
```  
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```  
  
### <a name="parameters"></a>매개 변수  
 `iIndex`  
 앞에서 삽입 수행 됩니다 문자의 인덱스입니다.  
  
 `psz`  
 삽입할 수는 부분 문자열에 대 한 포인터입니다.  
  
 `ch`  
 삽입할 문자입니다.  
  
### <a name="return-value"></a>반환 값  
 변경 된 문자열의 길이입니다.  
  
### <a name="remarks"></a>설명  
 `iIndex` 매개 변수는 첫 번째 문자는 문자 또는 부분 문자열에 대 한 공간을 만들기 위해 이동할 수를 식별 합니다. 경우 `nIndex` 가 0 이면 삽입 하는 전체 문자열 하기 전에 발생 합니다. 경우 `nIndex` 함수 문자열의 길이 현재 문자열을 연결 하 고 새 자료 하나 제공 하는 보다 높은 `ch` 또는 `psz`합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]  
  
##  <a name="left"></a>  CStringT::Left  
 이 `nCount` 개체에서 맨 왼쪽 `CStringT` 문자를 추출하고 추출된 부분 문자열의 복사본을 반환합니다.  
  
```  
CStringT Left(int nCount) const; 
```  
  
### <a name="parameters"></a>매개 변수  
 `nCount`  
 이 `CStringT` 개체에서 추출할 문자의 수입니다.  
  
### <a name="return-value"></a>반환 값  
 지정된 문자 범위의 복사본을 포함하는 `CStringT` 개체입니다. 반환된 `CStringT` 개체가 비어 있을 수 있습니다.  
  
### <a name="remarks"></a>설명  
 `nCount`가 문자열 길이를 초과하는 경우 전체 문자열이 추출됩니다. `Left`는 기본 `Left` 함수와 유사합니다.  
  
 멀티 바이트 문자 집합(MBCS)의 경우 `nCount`가 각 8비트 시퀀스를 문자로 처리하므로, `nCount`가 멀티 바이트 문자 수에 2를 곱하여 반환합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]  
  
##  <a name="loadstring"></a>  CStringT::LoadString  
 로 식별 되는 Windows 문자열 리소스를 읽고 `nID`를 기존 `CStringT` 개체입니다.  
  
```  
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```  
  
### <a name="parameters"></a>매개 변수  
 `hInstance`  
 모듈의 인스턴스 핸들입니다.  
  
 `nID`  
 Windows 문자열 리소스 id입니다.  
  
 `wLanguageID`  
 문자열 리소스의 언어입니다.  
  
### <a name="return-value"></a>반환 값  
 리소스 로드에 성공 하면 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 문자열 리소스 로드 ( `nID`)에서 지정된 된 모듈 ( `hInstance`) 지정된 된 언어를 사용 하 여 ( `wLanguage`).  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]  
  
##  <a name="makelower"></a>  CStringT::MakeLower  
 변환 된 `CStringT` 개체 소문자로 된 문자열입니다.  
  
```  
CStringT& MakeLower();
```  
  
### <a name="return-value"></a>반환 값  
 결과 소문자 문자열입니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]  
  
##  <a name="makereverse"></a>  CStringT::MakeReverse  
 문자 순서를 반대로 바꿉니다는 `CStringT` 개체입니다.  
  
```  
CStringT& MakeReverse();
```  
  
### <a name="return-value"></a>반환 값  
 결과 문자열을 반대로 바뀝니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]  
  
##  <a name="makeupper"></a>  CStringT::MakeUpper  
 변환에서 `CStringT` 개체 대문자로 된 문자열입니다.  
  
```  
CStringT& MakeUpper();
```  
  
### <a name="return-value"></a>반환 값  
 결과 대문자 문자열입니다.  
  
### <a name="remarks"></a>설명  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]  
  
##  <a name="mid"></a>  CStringT::Mid  
 길이의 부분 문자열을 추출 `nCount` 이 문자 `CStringT` 위치에서 시작 하는 개체 `iFirst` (0부터 시작)입니다.  
  
```  
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const; 
```  
  
### <a name="parameters"></a>매개 변수  
 `iFirst`  
 이 첫 번째 문자의 0부터 시작 인덱스 `CStringT` 추출된 된 부분 문자열에 포함 될 개체입니다.  
  
 `nCount`  
 이 `CStringT` 개체에서 추출할 문자의 수입니다. 이 매개 변수가 제공 되지 않은 경우 문자열의 나머지가 추출 됩니다.  
  
### <a name="return-value"></a>반환 값  
 지정된 문자 범위의 복사본을 포함하는 `CStringT` 개체입니다. 반환 된 `CStringT` 개체는 비어 있을 수 있습니다.  
  
### <a name="remarks"></a>설명  
 함수 추출된 된 부분 문자열의 복사본을 반환 합니다. `Mid` 비슷합니다 기본 Mid 함수 (점을 제외 하 고 basic에서 인덱스는 1부터 시작)입니다.  
  
 멀티 바이트 문자 집합 (MBCS)에 대 한 `nCount` 멀티 바이트 문자는 두 개의 문자로 계산 하나에 각 8 비트 문자, 즉, 한 겹치는 기간 및 후행 바이트를 가리킵니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]  
  
##  <a name="oemtoansi"></a>  CStringT::OemToAnsi  
 이에 있는 모든 문자가 변환 `CStringT` OEM 문자 집합을 ANSI 문자 집합에서에서 개체입니다.  
  
```  
void OemToAnsi();
```  
  
### <a name="remarks"></a>설명  
 이 함수를 사용할 수 없는 경우 `_UNICODE` 정의 됩니다.  
  
### <a name="example"></a>예제  
 예를 참조 [CStringT::AnsiToOem](#ansitooem)합니다.  
  
##  <a name="operator_add"></a>  CStringT::operator +  
 두 문자열 또는 문자 및 문자열을 연결합니다.  
  
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
 `ch1`  
 문자열로 연결할 ANSI 또는 유니코드 문자입니다.  
  
 `ch2`  
 문자열로 연결할 ANSI 또는 유니코드 문자입니다.  
  
 `str1`  
 A `CStringT` 문자열 또는 문자와 연결할입니다.  
  
 `str2`  
 A `CStringT` 문자열 또는 문자와 연결할입니다.  
  
 `psz1`  
 연결 된 문자열 또는 문자를 null로 끝나는 문자열에 대 한 포인터입니다.  
  
 `psz2`  
 문자열 또는 문자와 연결할 문자열에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 7 개의 오버 로드에는 유형이 있는데는 `CStringT::operator+` 함수입니다. 첫 번째 버전을 두 개의 기존 연결 `CStringT` 개체입니다. 다음 두 concatenate는 `CStringT` 개체 및 null로 끝나는 문자열. 다음 두 concatenate는 `CStringT` 개체 및 ANSI 문자입니다. 마지막 두 concatenate는 `CStringT` 개체 및 유니코드 문자입니다.  
  
> [!NOTE]
>  만들 수 있지만 `CStringT` 에 대 한 권장 인스턴스를 포함 하는 null 문자를 포함 합니다. 메서드 및 연산자를 호출 `CStringT` 포함 된 null 문자를 포함 하는 개체에 의도 하지 않은 결과가 발생할 수 있습니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]  
  
##  <a name="operator_add_eq"></a>  CStringT::operator + =  
 문자열의 끝 문자를 연결합니다.  
  
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
 str  
 `CThisSimpleString` 개체에 대한 참조입니다.  
  
 `bMFCDLL`  
 프로젝트가 MFC DLL 인지 여부를 지정 하는 부울입니다.  
  
 `BaseType`  
 문자열 기본 형식입니다.  
  
 `var`  
 이 문자열에 연결 하는 variant 개체입니다.  
  
 `ch`  
 문자열로 연결할 ANSI 또는 유니코드 문자입니다.  
  
 `pszSrc`  
 연결 문자열은 원래 문자열에 대 한 포인터입니다.  
  
 `strSrc`  
 A `CStringT` 하 고이 문자열과 연결할 합니다.  
  
### <a name="remarks"></a>설명  
 다른 연산자 받아들이며 `CStringT` 개체, 문자 포인터 또는 단일 문자입니다. 알고 있어야이에 추가 된 문자에 대 한 새 저장소를 할당할 수 있으므로이 연결 연산자를 사용할 때마다 예외가 발생할 수 있습니다 메모리 `CStringT` 개체입니다.  
  
 에 대 한 내용은 `CThisSimpleString`의 설명 섹션을 참조 [CStringT::CStringT](#cstringt)합니다.  
  
> [!NOTE]
>  만들 수 있지만 `CStringT` 에 대 한 권장 인스턴스를 포함 하는 null 문자를 포함 합니다. 메서드 및 연산자를 호출 `CStringT` 포함 된 null 문자를 포함 하는 개체에 의도 하지 않은 결과가 발생할 수 있습니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]  
  
##  <a name="operator_eq_eq"></a>  CStringT::operator = =  
 두 문자열이 논리적으로 동일한 지를 결정 합니다.  
  
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
 `ch1`  
 비교에 ANSI 또는 유니코드 문자입니다.  
  
 `ch2`  
 비교에 ANSI 또는 유니코드 문자입니다.  
  
 `str1`  
 A `CStringT` 비교 합니다.  
  
 `str2`  
 A `CStringT` 비교 합니다.  
  
 `psz1`  
 비교에 대 한 null로 끝나는 문자열에 대 한 포인터입니다.  
  
 `psz2`  
 비교에 대 한 null로 끝나는 문자열에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 여부를 테스트 하는 문자열 또는 왼쪽에 문자가 문자열 또는 문자를 오른쪽에 따라 TRUE 또는 FALSE를 반환 합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]  
  
##  <a name="operator_neq"></a>  CStringT::operator! =  
 논리적으로 하지 두 문자열이 같은지를 확인 합니다.  
  
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
 `ch1`  
 문자열로 연결할 ANSI 또는 유니코드 문자입니다.  
  
 `ch2`  
 문자열로 연결할 ANSI 또는 유니코드 문자입니다.  
  
 `str1`  
 A `CStringT` 비교 합니다.  
  
 `str2`  
 A `CStringT` 비교 합니다.  
  
 `psz1`  
 비교에 대 한 null로 끝나는 문자열에 대 한 포인터입니다.  
  
 `psz2`  
 비교에 대 한 null로 끝나는 문자열에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 문자열 또는 왼쪽에 문자를 문자열 또는 오른쪽에는 문자와 같지 않은지 테스트 합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]  
  
##  <a name="operator_lt"></a>  CStringT::operator &lt;  
 문자열 연산자의 왼쪽에서 오른쪽에 문자열 보다 작은지 여부를 결정 합니다.  
  
```  
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `str1`  
 A `CStringT` 비교 합니다.  
  
 `str2`  
 A `CStringT` 비교 합니다.  
  
 `psz1`  
 비교에 대 한 null로 끝나는 문자열에 대 한 포인터입니다.  
  
 `psz2`  
 비교에 대 한 null로 끝나는 문자열에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 될 때까지 문자는 문자열 간에 사전순으로 비교 합니다.  
  
-   해당하는 두 문자가 같지 않음이 확인될 때까지. 이 경우 해당 비교 결과를 문자열 간의 비교 결과로 가져옵니다.  
  
-   같지 않은 문자는 없으나 한 문자열의 문자 수가 다른 문자열보다 많음이 확인될 때까지. 이 경우 더 짧은 문자열이 더 긴 문자열보다 작은 것으로 간주합니다.  
  
-   같지 않은 문자가 없으며 문자열의 문자 수도 같음이 확인될 때까지. 이 경우 두 문자열은 동일한 것으로 간주합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]  
  
##  <a name="operator_gt"></a>  CStringT::operator &gt;  
 문자열 연산자의 왼쪽에서 오른쪽에 문자열 보다 큰지 여부를 결정 합니다.  
  
```  
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `str1`  
 A `CStringT` 비교 합니다.  
  
 `str2`  
 A `CStringT` 비교 합니다.  
  
 `psz1`  
 비교에 대 한 null로 끝나는 문자열에 대 한 포인터입니다.  
  
 `psz2`  
 비교에 대 한 null로 끝나는 문자열에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 될 때까지 문자는 문자열 간에 사전순으로 비교 합니다.  
  
-   해당하는 두 문자가 같지 않음이 확인될 때까지. 이 경우 해당 비교 결과를 문자열 간의 비교 결과로 가져옵니다.  
  
-   같지 않은 문자는 없으나 한 문자열의 문자 수가 다른 문자열보다 많음이 확인될 때까지. 이 경우 더 짧은 문자열이 더 긴 문자열보다 작은 것으로 간주합니다.  
  
-   같지 않은 문자가 없으며 문자열의 문자 수도 같음이 확인될 때까지. 이 경우 두 문자열은 동일한 것으로 간주합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]  
  
##  <a name="operator_lt_eq"></a>  CStringT::operator &lt;=  
 문자열 연산자의 왼쪽에서 오른쪽에 문자열 보다 작거나 인지 확인 합니다.  
  
```  
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `str1`  
 A `CStringT` 비교 합니다.  
  
 `str2`  
 A `CStringT` 비교 합니다.  
  
 `psz1`  
 비교에 대 한 null로 끝나는 문자열에 대 한 포인터입니다.  
  
 `psz2`  
 비교에 대 한 null로 끝나는 문자열에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 될 때까지 문자는 문자열 간에 사전순으로 비교 합니다.  
  
-   해당하는 두 문자가 같지 않음이 확인될 때까지. 이 경우 해당 비교 결과를 문자열 간의 비교 결과로 가져옵니다.  
  
-   같지 않은 문자는 없으나 한 문자열의 문자 수가 다른 문자열보다 많음이 확인될 때까지. 이 경우 더 짧은 문자열이 더 긴 문자열보다 작은 것으로 간주합니다.  
  
-   같지 않은 문자가 없으며 문자열의 문자 수도 같음이 확인될 때까지. 이 경우 두 문자열은 동일한 것으로 간주합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]  
  
##  <a name="operator_gt_eq"></a>  CStringT::operator &gt;=  
 문자열 연산자의 왼쪽에서 오른쪽에 문자열 보다 크거나 인지 확인 합니다.  
  
```  
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `str1`  
 A `CStringT` 비교 합니다.  
  
 `str2`  
 A `CStringT` 비교 합니다.  
  
 `psz1`  
 비교에 대 한 문자열에 대 한 포인터입니다.  
  
 `psz2`  
 비교에 대 한 문자열에 대 한 포인터입니다.  
  
### <a name="remarks"></a>설명  
 될 때까지 문자는 문자열 간에 사전순으로 비교 합니다.  
  
-   해당하는 두 문자가 같지 않음이 확인될 때까지. 이 경우 해당 비교 결과를 문자열 간의 비교 결과로 가져옵니다.  
  
-   같지 않은 문자는 없으나 한 문자열의 문자 수가 다른 문자열보다 많음이 확인될 때까지. 이 경우 더 짧은 문자열이 더 긴 문자열보다 작은 것으로 간주합니다.  
  
-   같지 않은 문자가 없으며 문자열의 문자 수도 같음이 확인될 때까지. 이 경우 두 문자열은 동일한 것으로 간주합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]  
  
##  <a name="remove"></a>  CStringT::Remove  
 문자열에서 지정 된 문자의 모든 인스턴스를 제거합니다.  
  
```  
int Remove(XCHAR chRemove);
```  
  
### <a name="parameters"></a>매개 변수  
 `chRemove`  
 문자열에서 제거할 문자입니다.  
  
### <a name="return-value"></a>반환 값  
 문자열에서 제거 하는 문자 수를 지정 합니다. 문자열이 변경 되지 않은 경우 0입니다.  
  
### <a name="remarks"></a>설명  
 문자에 대 한 비교는 대/소문자 구분.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]  
  
##  <a name="replace"></a>  CStringT::Replace  
 두 가지 버전의 `Replace`합니다. 첫 번째 버전을 다른 부분 문자열을 사용 하 여 하나 이상의 부분 문자열의 복사본을 대체 합니다. 두 부분 문자열은 null로 끝납니다. 두 번째 버전은 다른 문자를 사용 하 여 하나 이상의 문자의 복사본을 대체 합니다. 두 버전 모두에 저장 된 문자 데이터에서 작동 `CStringT`합니다.  
  
```  
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```  
  
### <a name="parameters"></a>매개 변수  
 `pszOld`  
 교체는 null로 끝나는 문자열에 대 한 포인터 `pszNew`합니다.  
  
 `pszNew`  
 대체 하는 null로 끝나는 문자열에 대 한 포인터 `pszOld`합니다.  
  
 `chOld`  
 교체 문자 `chNew`합니다.  
  
 `chNew`  
 문자 대체 `chOld`합니다.  
  
### <a name="return-value"></a>반환 값  
 문자열이 변경 되지 않은 경우에 문자 또는 부분 문자열 또는 0의 대체 인스턴스 수를 반환 합니다.  
  
### <a name="remarks"></a>설명  
 `Replace` 문자열 길이 변경할 수 `pszNew` 및 `pszOld` 동일한 길이에 없고 오래 된 부분 문자열의 여러 복사본을 새 변경할 수 있습니다. 함수는 대/소문자 구분 일치를 수행합니다.  
  
 몇 가지 `CStringT` 인스턴스가 `CString`, `CStringA`, 및 `CStringW`합니다.  
  
 에 대 한 `CStringA`, `Replace` ANSI 또는 멀티 바이트 (MBCS) 문자를 사용 합니다. 에 대 한 `CStringW`, `Replace` 와이드 문자의 작동 합니다.  
  
 에 대 한 `CString`, 문자 데이터 형식이 다음 표에 상수를 정의 하는 여부에 따라 컴파일 타임에 선택 됩니다.  
  
|정의 된 상수|문자 데이터 형식|  
|----------------------|-------------------------|  
|`_UNICODE`|와이드 문자|  
|`_MBCS`|멀티 바이트 문자|  
|모두|단일 바이트 문자|  
|Both|Undefined|  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]  
  
##  <a name="reversefind"></a>  CStringT::ReverseFind  
 이 검색 `CStringT` 문자의 마지막 일치 항목에 대 한 개체입니다.  
  
```  
int ReverseFind(XCHAR ch) const throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `ch`  
 검색할 문자입니다.  
  
### <a name="return-value"></a>반환 값  
 이 마지막 문자의 0부터 시작 인덱스 `CStringT` 문자를 찾을 수 없는 경우 요청 된 문자 또는-1을 일치 하는 개체입니다.  
  
### <a name="remarks"></a>설명  
 함수는 런타임에 함수와 비슷하지만 `strrchr`합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]  
  
##  <a name="right"></a>  CStringT::Right  
 마지막 추출 (즉, 가장 오른쪽) `nCount` 이 문자 `CStringT` 개체 추출된 된 부분 문자열의 복사본을 반환 합니다.  
  
```  
CStringT Right(int nCount) const; 
```  
  
### <a name="parameters"></a>매개 변수  
 `nCount`  
 이 `CStringT` 개체에서 추출할 문자의 수입니다.  
  
### <a name="return-value"></a>반환 값  
 지정된 문자 범위의 복사본을 포함하는 `CStringT` 개체입니다. 반환 된 `CStringT` 개체는 비어 있을 수 있습니다.  
  
### <a name="remarks"></a>설명  
 `nCount`가 문자열 길이를 초과하는 경우 전체 문자열이 추출됩니다. `Right` 기본 비슷합니다 `Right` (제외 작동 basic에서 인덱스는 0부터 시작)입니다.  
  
 멀티 바이트 문자 집합 (MBCS)에 대 한 `nCount` 멀티 바이트 문자는 두 개의 문자로 계산 하나에 각 8 비트 문자, 즉, 한 겹치는 기간 및 후행 바이트를 가리킵니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]  
  
##  <a name="setsysstring"></a>  CStringT::SetSysString  
 다시 할당는 `BSTR` 가리키는 `pbstr` 의 내용을 복사 하 고는 `CStringT` 포함 하 여 메서드를 개체는 `NULL` 문자입니다.  
  
```  
BSTR SetSysString(BSTR* pbstr) const; 
```  
  
### <a name="parameters"></a>매개 변수  
 `pbstr`  
 문자열에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 새 문자열입니다.  
  
### <a name="remarks"></a>설명  
 콘텐츠에 따라는 `CStringT` 값, 개체는 `BSTR` 에서 참조 `pbstr` 변경할 수 있습니다. 함수에서 throw 한 `CMemoryException` 메모리가 부족 하 여 있는 경우.  
  
 이 함수는 자동화에 대 한 참조로 전달 되는 문자열 값을 변경 하려면 일반적으로 사용 됩니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]  
  
##  <a name="spanexcluding"></a>  CStringT::SpanExcluding  
 로 식별 되는 문자 집합에 없는 첫 번째 문자로 시작 하는 문자열에서 문자를 추출 `pszCharSet`합니다.  
  
```  
CStringT SpanExcluding(PCXSTR pszCharSet) const; 
```  
  
### <a name="parameters"></a>매개 변수  
 `pszCharSet`  
 문자열의 문자 집합으로 해석 합니다.  
  
### <a name="return-value"></a>반환 값  
 에 속하지 않은 문자열의 문자를 포함 하는 부분 문자열 `pszCharSet`문자열의 첫 번째 문자부터 시작 하 고 또한 문자열에서 찾은 첫 번째 문자로 끝나는 `pszCharSet` (즉, 첫 번째 문자부터는 문자열을 최대 하지만 문자열의 첫 번째 문자를 제외 하 고 찾을 `pszCharSet`). 경우에 없는 문자에는 전체 문자열을 반환 `pszCharSet` 문자열에 있습니다.  
  
### <a name="remarks"></a>설명  
 `SpanExcluding` 추출 하 고 앞에 있는 문자를 맨 처음 발견 되는 모든 문자를 반환 `pszCharSet` (즉,에서 문자 `pszCharSet` 및 문자열에 따라 모든 문자는 반환 되지 않습니다). 문자가 경우 `pszCharSet` 다음 문자열에 있으면 `SpanExcluding` 전체 문자열을 반환 합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]  
  
##  <a name="spanincluding"></a>  CStringT::SpanIncluding  
 로 식별 되는 문자 집합에 있는 첫 번째 문자로 시작 하는 문자열에서 문자를 추출 `pszCharSet`합니다.  
  
```  
CStringT SpanIncluding(PCXSTR pszCharSet) const; 
```  
  
### <a name="parameters"></a>매개 변수  
 `pszCharSet`  
 문자열의 문자 집합으로 해석 합니다.  
  
### <a name="return-value"></a>반환 값  
 에 있는 문자열에 문자를 포함 하는 하위 문자열 `pszCharSet`, 문자열에서 첫 번째 문자부터 시작 및 끝 문자에 속하지 않은 문자열에서 발견 되 면 `pszCharSet`합니다. `SpanIncluding` 문자열의 첫 번째 문자가 집합에 없는 경우 빈 부분 문자열을 반환 합니다.  
  
### <a name="remarks"></a>설명  
 문자열의 첫 번째 문자에에서 없는 경우 문자 집합을 다음 `SpanIncluding` 빈 문자열을 반환 합니다. 그렇지 않으면 집합에 있는 연속 된 문자 시퀀스를 반환 합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]  
  
##  <a name="tokenize"></a>  CStringT::Tokenize  
 대상 문자열에서 다음 토큰을 찾습니다.  
  
```  
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const; 
```  
  
### <a name="parameters"></a>매개 변수  
 `pszTokens`  
 토큰 구분 기호를 포함 하는 문자열입니다. 이러한 구분 기호 순서가 중요 합니다.  
  
 `iStart`  
 검색을 시작할 0부터 시작 하는 인덱스입니다.  
  
### <a name="return-value"></a>반환 값  
 A `CStringT` 현재 토큰 값을 포함 하는 개체입니다.  
  
### <a name="remarks"></a>설명  
 `Tokenize` 함수는 대상 문자열에서 다음 토큰을 찾습니다. 문자 집합이 `pszTokens` 찾을 토큰의 사용 가능한 구분 기호를 지정 합니다. 호출할 때마다 `Tokenize` 함수에서 시작 `iStart`선행 구분 기호 생략 하 고, 반환 된 `CStringT` 다음 구분 기호 문자까지 문자의 문자열이 현재 토큰을 포함 하는 개체입니다. 값 `iStart` 문자열의 끝에 도달한 경우 끝 구분 기호 또는-1을 다음 위치로 업데이트 됩니다. 일련의 호출을으로 대상 문자열의 나머지 부분에서 더 많은 토큰 나누어질 수 `Tokenize`를 사용 하 여 `iStart` 읽어야 하는 다음 토큰 문자열의 위치를 추적 하기 위해. 더 이상 토큰이 없는 경우 함수는 빈 문자열을 반환 하 고 `iStart` -1로 설정 됩니다.  
  
 CRT 달리와 같은 함수를 토큰화 [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), `Tokenize` 대상 문자열을 수정 하지는 않습니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]  
  
### <a name="remarks"></a>설명  
 이 예제에서 출력은 다음과 같습니다.  
  
 `Resulting Token: First`  
  
 `Resulting Token: Second`  
  
 `Resulting Token: Third`  
  
##  <a name="trim"></a>  CStringT::Trim  
 선행 및 후행 문자열에서 문자를 삭제 합니다.  
  
```  
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```  
  
### <a name="parameters"></a>매개 변수  
 `chTarget`  
 대상 문자 트리밍입니다.  
  
 `pszTargets`  
 대상 트리밍될 문자를 포함 하는 문자열에 대 한 포인터입니다. 모든 선행 및 후행 문자가 `pszTarget` 에서 잘립니다는 `CStringT` 개체입니다.  
  
### <a name="return-value"></a>반환 값  
 잘라낸된 문자열을 반환합니다.  
  
### <a name="remarks"></a>설명  
 다음 중 하나를의 선행 항목과 후행 항목이 모두 제거합니다.  
  
-   로 지정 된 문자 `chTarget.`  
  
-   지정 된 문자열에서 문자를 모두 `pszTargets.`  
  
-   공백입니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]  
  
### <a name="remarks"></a>설명  
 이 예제에서 출력은 다음과 같습니다.  
  
 `Before: "******Soccer is best, but liquor is quicker!!!!!"`  
  
 `After : "Soccer is best, but liquor is quicker"`  
  
##  <a name="trimleft"></a>  CStringT::TrimLeft  
 문자열에서 선행 문자를 삭제 합니다.  
  
```  
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```  
  
### <a name="parameters"></a>매개 변수  
 `chTarget`  
 대상 문자 트리밍입니다.  
  
 `pszTargets`  
 대상 트리밍될 문자를 포함 하는 문자열에 대 한 포인터입니다. 에 있는 문자의 선행 항목을 모두 `pszTarget` 에서 잘립니다는 `CStringT` 개체입니다.  
  
### <a name="return-value"></a>반환 값  
 결과 잘라낸된 문자열입니다.  
  
### <a name="remarks"></a>설명  
 다음 중 하나를의 선행 항목과 후행 항목이 모두 제거합니다.  
  
-   로 지정 된 문자 `chTarget.`  
  
-   지정 된 문자열에서 문자를 모두 `pszTargets.`  
  
-   공백입니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]  
  
##  <a name="trimright"></a>  CStringT::TrimRight  
 문자열에서 후행 문자를 삭제 합니다.  
  
```  
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```  
  
### <a name="parameters"></a>매개 변수  
 `chTarget`  
 대상 문자 트리밍입니다.  
  
 `pszTargets`  
 대상 트리밍될 문자를 포함 하는 문자열에 대 한 포인터입니다. 모든 후행 문자가 `pszTarget` 에서 잘립니다는 `CStringT` 개체입니다.  
  
### <a name="return-value"></a>반환 값  
 반환 된 `CStringT` 잘라낸된 문자열을 포함 하는 개체입니다.  
  
### <a name="remarks"></a>설명  
 후행 횟수는 다음 중 하나를 제거 합니다.  
  
-   로 지정 된 문자 `chTarget.`  
  
-   지정 된 문자열에서 문자를 모두 `pszTargets.`  
  
-   공백입니다.  
  
 `CStringT& TrimRight(XCHAR chTarget)` 문자에 대 한 매개 변수를 하나를 적용 하 고의 끝에서 해당 문자의 모든 복사본을 제거 하는 버전 `CStringT` 문자열 데이터입니다. 문자열의 끝에서 시작 하 고 앞 부분 작동 합니다. 에 다른 문자를 발견 하면 때나 중지 `CSTringT` 문자 데이터가 부족 합니다.  
  
 `CStringT& TrimRight(PCXSTR pszTargets)` 버전을 찾으려고 다른 모든 문자를 포함 하는 null로 끝나는 문자열을 수락 합니다. 해당 문자가 복사본을 모두 제거는 `CStringT` 개체입니다. 문자열의 끝에서 시작 하 고 앞 부분 작동 합니다. 대상 문자열에 없는 문자를 발견 하면 때나 중지 `CStringT` 문자 데이터가 부족 합니다. 전체 대상 문자열의 끝에 부분 문자열에 일치 하도록 시도 하지 않습니다 `CStringT`합니다.  
  
 `CStringT& TrimRight()` 버전 매개 변수 없이 사용 하려면 필요 합니다. 줄일 때의 끝에서 후행 공백 문자는 `CStringT` 문자열입니다. 공백 문자는 줄 바꿈, 공백 또는 탭 수 있습니다.  
  
-  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]  
  
## <a name="see-also"></a>참고 항목  
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)   
 [CSimpleStringT 클래스](../../atl-mfc-shared/reference/csimplestringt-class.md)


