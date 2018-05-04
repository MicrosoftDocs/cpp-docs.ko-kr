---
title: CTokenPrivileges 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
dev_langs:
- C++
helpviewer_keywords:
- CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6c9886b79739f42329b0f306c8bce6afc2d9fa0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="ctokenprivileges-class"></a>CTokenPrivileges 클래스
이 클래스는에 대 한 래퍼는 **TOKEN_PRIVILEGES** 구조입니다.  
  
> [!IMPORTANT]
>  이 클래스 및 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```
class CTokenPrivileges
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|생성자입니다.|  
|[CTokenPrivileges::~CTokenPrivileges](#dtor)|소멸자입니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CTokenPrivileges::Add](#add)|하나 이상의 권한을 추가 하는 `CTokenPrivileges` 개체입니다.|  
|[CTokenPrivileges::Delete](#delete)|권한을 삭제는 `CTokenPrivileges` 개체입니다.|  
|[CTokenPrivileges::DeleteAll](#deleteall)|모든 권한을 삭제는 `CTokenPrivileges` 개체입니다.|  
|[CTokenPrivileges::GetCount](#getcount)|권한 항목 수를 반환 합니다.는 `CTokenPrivileges` 개체입니다.|  
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|검색에 포함 된 권한 이름을 모두 표시는 `CTokenPrivileges` 개체입니다.|  
|[CTokenPrivileges::GetLength](#getlength)|버퍼 크기를 보유 하는 데 필요한 바이트 단위로 반환는 **TOKEN_PRIVILEGES** 가 나타내는 구조는 `CTokenPrivileges` 개체입니다.|  
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Locally unique identifier (Luid)와 특성 플래그에서 검색 된 `CTokenPrivileges` 개체입니다.|  
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|권한 이름과 특성 플래그에서 검색 된 `CTokenPrivileges` 개체입니다.|  
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|에 대 한 포인터를 반환 합니다.는 **TOKEN_PRIVILEGES** 구조입니다.|  
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|지정 된 권한 이름과 연결 된 특성을 검색 합니다.|  
  
### <a name="public-operators"></a>Public 연산자  
  
|이름|설명|  
|----------|-----------------|  
|[CTokenPrivileges::operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|값에 대 한 포인터에 캐스팅은 **TOKEN_PRIVILEGES** 구조입니다.|  
|[CTokenPrivileges::operator =](#operator_eq)|대입 연산자입니다.|  
  
## <a name="remarks"></a>설명  
 [액세스 토큰](http://msdn.microsoft.com/library/windows/desktop/aa374909) 프로세스 또는 스레드의 보안 컨텍스트를 설명 하 고 Windows 시스템에 로그온 한 각 사용자에 게 할당 하는 개체입니다.  
  
 액세스 토큰은 각 사용자에 게 부여 된 다양 한 보안 권한을 설명 하기 위해 사용 됩니다. 고유한 로컬 식별자 라고 하는 64 비트 숫자의 권한으로 구성 됩니다 ( [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261))과 설명자 문자열입니다.  
  
 `CTokenPrivileges` 클래스에 대 한 래퍼는는 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) 구조체이 고 0 이나 더 많은 권한이 포함 되어 있습니다. 삭제 되거나 제공 된 클래스 메서드를 사용 하 여 쿼리 된 권한은 추가할 수 있습니다.  
  
 Windows에서 액세스 제어 모델에 대 한 소개를 참조 하십시오. [액세스 제어](http://msdn.microsoft.com/library/windows/desktop/aa374860) Windows sdk에서입니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlsecurity.h  
  
##  <a name="add"></a>  CTokenPrivileges::Add  
 하나 이상의 권한을 추가 하는 `CTokenPrivileges` 액세스 토큰 개체입니다.  
  
```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);  
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 `pszPrivilege`  
 WINNT에 정의 된 대로 권한의 이름을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. H 헤더 파일입니다.  
  
 `bEnable`  
 True 이면 권한은 사용 하도록 설정 합니다. False 인 경우 권한은 사용할 수 없습니다.  
  
 `rPrivileges`  
 에 대 한 참조는 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) 구조입니다. 권한과 특성은이 구조에서 복사 하 고에 추가 된 `CTokenPrivileges` 개체입니다.  
  
### <a name="return-value"></a>반환 값  
 이 메서드의 첫 번째 형태 권한을 성공적으로 추가 되 면 false 그렇지 않은 경우 true를 반환 합니다.  
  
##  <a name="ctokenprivileges"></a>  CTokenPrivileges::CTokenPrivileges  
 생성자입니다.  
  
```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );  
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 `rhs`  
 `CTokenPrivileges` 새 개체에 할당할 개체입니다.  
  
 `rPrivileges`  
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) 새 서버에 할당 하는 구조 `CTokenPrivileges` 개체입니다.  
  
### <a name="remarks"></a>설명  
 `CTokenPrivileges` 를 사용 하 여 개체를 만들 수 있습니다는 **TOKEN_PRIVILEGES** 구조 또는 이전에 정의한 `CTokenPrivileges` 개체입니다.  
  
##  <a name="dtor"></a>  CTokenPrivileges::~CTokenPrivileges  
 소멸자입니다.  
  
```
virtual ~CTokenPrivileges() throw();
```  
  
### <a name="remarks"></a>설명  
 소멸자는 할당 된 모든 리소스를 해제합니다.  
  
##  <a name="delete"></a>  CTokenPrivileges::Delete  
 권한을 삭제는 `CTokenPrivileges` 액세스 토큰 개체입니다.  
  
```
bool Delete(LPCTSTR pszPrivilege) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 `pszPrivilege`  
 WINNT에 정의 된 대로 권한의 이름을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. H 헤더 파일입니다. 예를 들어이 매개 변수 se_security_name 권한, 상수 또는 "SeSecurityPrivilege"는 해당 문자열을 지정할 수 있습니다.  
  
### <a name="return-value"></a>반환 값  
 권한을 삭제 했습니다.이 고, false가 그렇지 않으면 true를 반환 합니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 제한 된 토큰을 만들기 위한 도구로 유용 합니다.  
  
##  <a name="deleteall"></a>  CTokenPrivileges::DeleteAll  
 모든 권한을 삭제는 `CTokenPrivileges` 액세스 토큰 개체입니다.  
  
```
void DeleteAll() throw();
```  
  
### <a name="remarks"></a>설명  
 에 포함 된 모든 권한을 삭제는 `CTokenPrivileges` 액세스 토큰 개체입니다.  
  
##  <a name="getdisplaynames"></a>  CTokenPrivileges::GetDisplayNames  
 검색에 포함 된 권한 이름을 모두 표시는 `CTokenPrivileges` 액세스 토큰 개체입니다.  
  
```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 `pDisplayNames`  
 `CString` 개체의 배열에 대한 포인터입니다. **CNames** typedef 정의: **CTokenPrivileges::CAtlArray\<CString >** 합니다.  
  
### <a name="remarks"></a>설명  
 매개 변수 `pDisplayNames` 의 배열에 대 한 포인터 `CString` 개체에 해당 하는 권한을에 포함 된 표시 이름을 수신할는 `CTokenPrivileges` 개체입니다. 이 메서드는 WINNT의 권한 정의 섹션에 지정 된 권한에 대 한 표시 이름을 검색 합니다. 8.  
  
 이 메서드를 표시할 수 있는 이름 검색: 예를 들어 특성 이름은 SE_REMOTE_SHUTDOWN_NAME 표시할 수 있는 이름이 "원격 시스템에서 강제 종료 합니다." 시스템 이름을 가져오려면 [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)합니다.  
  
##  <a name="getcount"></a>  CTokenPrivileges::GetCount  
 권한 항목 수를 반환 합니다.는 `CTokenPrivileges` 개체입니다.  
  
```
UINT GetCount() const throw();
```  
  
### <a name="return-value"></a>반환 값  
 에 포함 된 권한 수를 반환 된 `CTokenPrivileges` 개체입니다.  
  
##  <a name="getlength"></a>  CTokenPrivileges::GetLength  
 길이 반환 된 `CTokenPrivileges` 개체입니다.  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>반환 값  
 보유 하는 데 필요한 바이트 수를 반환는 **TOKEN_PRIVILEGES** 가 나타내는 구조는 `CTokenPrivileges` 를 포함 한 모든 권한 항목이 포함 된 개체입니다.  
  
##  <a name="getluidsandattributes"></a>  CTokenPrivileges::GetLuidsAndAttributes  
 Locally unique identifier (Luid)와 특성 플래그에서 검색 된 `CTokenPrivileges` 개체입니다.  
  
```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 `pPrivileges`  
 배열에 대 한 포인터 [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261) 개체입니다. **CLUIDArray** 로 정의 하는 typedef **CAtlArray\<LUID > CLUIDArray**합니다.  
  
 `pAttributes`  
 DWORD 개체의 배열에 대 한 포인터입니다. 이 매개 변수가 지정 하지 않거나 NULL 인 경우 특성 검색 되지 않습니다. **CAttributes** 로 정의 하는 typedef **CAtlArray \<DWORD > CAttributes**합니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 모든에 포함 된 권한을 열거 합니다는 `CTokenPrivileges` 토큰 개체를 액세스 하 고 배열 개체에 개별 Luid 및 특성 플래그 (옵션)를 배치 합니다.  
  
##  <a name="getnamesandattributes"></a>  CTokenPrivileges::GetNamesAndAttributes  
 검색의 이름 및 특성 플래그는 `CTokenPrivileges` 개체입니다.  
  
```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 *pNames*  
 배열에 대 한 포인터 `CString` 개체입니다. **CNames** 로 정의 하는 typedef **CAtlArray \<CString > CNames**합니다.  
  
 `pAttributes`  
 DWORD 개체의 배열에 대 한 포인터입니다. 이 매개 변수가 지정 하지 않거나 NULL 인 경우 특성 검색 되지 않습니다. **CAttributes** 로 정의 하는 typedef **CAtlArray \<DWORD > CAttributes**합니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 모든에 포함 된 권한을 열거 합니다는 `CTokenPrivileges` 개체를 array 개체를 이름 및 특성 플래그 (옵션)를 추가 합니다.  
  
 이 메서드를 표시할 수 있는 이름 대신 특성 이름을 검색 합니다: 예를 들어 특성 이름은 SE_REMOTE_SHUTDOWN_NAME 시스템 이름이 "SeRemoteShutdownPrivilege." 표시 이름을 얻으려면 메서드를 사용 하 여 [CTokenPrivileges::GetDisplayNames](#getdisplaynames)합니다.  
  
##  <a name="getptoken_privileges"></a>  CTokenPrivileges::GetPTOKEN_PRIVILEGES  
 에 대 한 포인터를 반환 합니다.는 **TOKEN_PRIVILEGES** 구조입니다.  
  
```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```  
  
### <a name="return-value"></a>반환 값  
 에 대 한 포인터를 반환 합니다.는 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) 구조입니다.  
  
##  <a name="lookupprivilege"></a>  CTokenPrivileges::LookupPrivilege  
 지정 된 권한 이름과 연결 된 특성을 검색 합니다.  
  
```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 `pszPrivilege`  
 WINNT에 정의 된 대로 권한의 이름을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. H 헤더 파일입니다. 예를 들어이 매개 변수 se_security_name 권한, 상수 또는 "SeSecurityPrivilege"는 해당 문자열을 지정할 수 있습니다.  
  
 `pdwAttributes`  
 특성을 수신 하는 변수에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 그렇지 않은 경우이 특성은이 고, false 성공적으로 검색 된 경우 true를 반환 합니다.  
  
##  <a name="operator_eq"></a>  CTokenPrivileges::operator =  
 대입 연산자입니다.  
  
```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);  
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 `rPrivileges`  
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) 구조에 할당 하는 `CTokenPrivileges` 개체입니다.  
  
 `rhs`  
 `CTokenPrivileges` 개체에 할당 하는 개체입니다.  
  
### <a name="return-value"></a>반환 값  
 업데이트 된 반환 `CTokenPrivileges` 개체입니다.  
  
##  <a name="operator_const_token_privileges__star"></a>  CTokenPrivileges::operator const TOKEN_PRIVILEGES *  
 값에 대 한 포인터에 캐스팅은 **TOKEN_PRIVILEGES** 구조입니다.  
  
```  
operator const TOKEN_PRIVILEGES *() const throw(...);
```  
  
### <a name="remarks"></a>설명  
 값에 대 한 포인터에 캐스팅은 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) 구조입니다.  
  
## <a name="see-also"></a>참고 항목  
 [Security 샘플](../../visual-cpp-samples.md)   
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)   
 [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)   
 [LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)   
 [클래스 개요](../../atl/atl-class-overview.md)   
 [보안 전역 함수](../../atl/reference/security-global-functions.md)
