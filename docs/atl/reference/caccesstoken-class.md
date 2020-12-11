---
description: '자세히 알아보기: CAccessToken 클래스'
title: CAccessToken 클래스
ms.date: 07/02/2019
f1_keywords:
- CAccessToken
- ATLSECURITY/ATL::CAccessToken
- ATLSECURITY/ATL::CAccessToken::Attach
- ATLSECURITY/ATL::CAccessToken::CheckTokenMembership
- ATLSECURITY/ATL::CAccessToken::CreateImpersonationToken
- ATLSECURITY/ATL::CAccessToken::CreatePrimaryToken
- ATLSECURITY/ATL::CAccessToken::CreateProcessAsUser
- ATLSECURITY/ATL::CAccessToken::CreateRestrictedToken
- ATLSECURITY/ATL::CAccessToken::Detach
- ATLSECURITY/ATL::CAccessToken::DisablePrivilege
- ATLSECURITY/ATL::CAccessToken::DisablePrivileges
- ATLSECURITY/ATL::CAccessToken::EnablePrivilege
- ATLSECURITY/ATL::CAccessToken::EnablePrivileges
- ATLSECURITY/ATL::CAccessToken::GetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::GetEffectiveToken
- ATLSECURITY/ATL::CAccessToken::GetGroups
- ATLSECURITY/ATL::CAccessToken::GetHandle
- ATLSECURITY/ATL::CAccessToken::GetImpersonationLevel
- ATLSECURITY/ATL::CAccessToken::GetLogonSessionId
- ATLSECURITY/ATL::CAccessToken::GetLogonSid
- ATLSECURITY/ATL::CAccessToken::GetOwner
- ATLSECURITY/ATL::CAccessToken::GetPrimaryGroup
- ATLSECURITY/ATL::CAccessToken::GetPrivileges
- ATLSECURITY/ATL::CAccessToken::GetProcessToken
- ATLSECURITY/ATL::CAccessToken::GetProfile
- ATLSECURITY/ATL::CAccessToken::GetSource
- ATLSECURITY/ATL::CAccessToken::GetStatistics
- ATLSECURITY/ATL::CAccessToken::GetTerminalServicesSessionId
- ATLSECURITY/ATL::CAccessToken::GetThreadToken
- ATLSECURITY/ATL::CAccessToken::GetTokenId
- ATLSECURITY/ATL::CAccessToken::GetType
- ATLSECURITY/ATL::CAccessToken::GetUser
- ATLSECURITY/ATL::CAccessToken::HKeyCurrentUser
- ATLSECURITY/ATL::CAccessToken::Impersonate
- ATLSECURITY/ATL::CAccessToken::ImpersonateLoggedOnUser
- ATLSECURITY/ATL::CAccessToken::IsTokenRestricted
- ATLSECURITY/ATL::CAccessToken::LoadUserProfile
- ATLSECURITY/ATL::CAccessToken::LogonUser
- ATLSECURITY/ATL::CAccessToken::OpenCOMClientToken
- ATLSECURITY/ATL::CAccessToken::OpenNamedPipeClientToken
- ATLSECURITY/ATL::CAccessToken::OpenRPCClientToken
- ATLSECURITY/ATL::CAccessToken::OpenThreadToken
- ATLSECURITY/ATL::CAccessToken::PrivilegeCheck
- ATLSECURITY/ATL::CAccessToken::Revert
- ATLSECURITY/ATL::CAccessToken::SetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::SetOwner
- ATLSECURITY/ATL::CAccessToken::SetPrimaryGroup
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
ms.openlocfilehash: fdcef40948a19c5ffb69aa32b18566280d048697
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158545"
---
# <a name="caccesstoken-class"></a>CAccessToken 클래스

이 클래스는 액세스 토큰에 대 한 래퍼입니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class CAccessToken
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAccessToken:: ~ CAccessToken](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAccessToken:: Attach](#attach)|지정 된 액세스 토큰 핸들의 소유권을 사용 하려면이 메서드를 호출 합니다.|
|[CAccessToken:: CheckTokenMembership](#checktokenmembership)|지정 된 SID가 개체에서 사용 되는지 확인 하려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: CreateImpersonationToken](#createimpersonationtoken)|새 가장 액세스 토큰을 만들려면이 메서드를 호출 합니다.|
|[CAccessToken:: CreatePrimaryToken](#createprimarytoken)|새 기본 토큰을 만들려면이 메서드를 호출 합니다.|
|[CAccessToken:: CreateProcessAsUser](#createprocessasuser)|개체가 나타내는 사용자의 보안 컨텍스트에서 실행 되는 새 프로세스를 만들려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: CreateRestrictedToken](#createrestrictedtoken)|새 제한 된 개체를 만들려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken::D etach](#detach)|액세스 토큰의 소유권을 해지 하려면이 메서드를 호출 합니다.|
|[CAccessToken::D isablePrivilege](#disableprivilege)|개체에서 권한을 사용 하지 않도록 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken::D isablePrivileges](#disableprivileges)|개체에서 하나 이상의 권한을 사용 하지 않도록 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: EnablePrivilege](#enableprivilege)|개체에서 권한을 사용 하도록 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: EnablePrivileges](#enableprivileges)|개체에서 하나 이상의 권한을 사용 하도록 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: GetDefaultDacl](#getdefaultdacl)|개체의 기본 DACL을 반환 하려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: GetEffectiveToken](#geteffectivetoken)|`CAccessToken`현재 스레드에 적용 되는 액세스 토큰과 같은 개체를 가져오려면이 메서드를 호출 합니다.|
|[CAccessToken:: GetGroups](#getgroups)|개체의 토큰 그룹을 반환 하려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: GetHandle](#gethandle)|액세스 토큰에 대 한 핸들을 검색 하려면이 메서드를 호출 합니다.|
|[CAccessToken:: GetImpersonationLevel](#getimpersonationlevel)|액세스 토큰에서 가장 수준을 가져오려면이 메서드를 호출 합니다.|
|[CAccessToken:: GetLogonSessionId](#getlogonsessionid)|이 메서드를 호출 하 여 개체에 연결 된 로그온 세션 ID를 가져옵니다 `CAccessToken` .|
|[CAccessToken:: GetLogonSid](#getlogonsid)|이 메서드를 호출 하 여 개체에 연결 된 로그온 SID를 가져옵니다 `CAccessToken` .|
|[CAccessToken:: GetOwner](#getowner)|이 메서드를 호출 하 여 개체와 연결 된 소유자를 가져옵니다 `CAccessToken` .|
|[CAccessToken:: GetPrimaryGroup](#getprimarygroup)|이 메서드를 호출 하 여 개체에 연결 된 주 그룹을 가져옵니다 `CAccessToken` .|
|[CAccessToken:: GetPrivileges](#getprivileges)|이 메서드를 호출 하 여 개체와 연결 된 권한을 가져옵니다 `CAccessToken` .|
|[CAccessToken:: GetProcessToken](#getprocesstoken)|지정된 프로세스의 액세스 토큰을 사용해서 `CAccessToken`을 초기화하려면 이 메서드를 호출합니다.|
|[CAccessToken:: GetProfile](#getprofile)|이 메서드를 호출 하 여 개체와 연결 된 사용자 프로필을 가리키는 핸들을 가져옵니다 `CAccessToken` .|
|[CAccessToken:: GetSource](#getsource)|개체의 소스를 가져오려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: GetStatistics](#getstatistics)|개체와 연결 된 정보를 가져오려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: GetTerminalServicesSessionId](#getterminalservicessessionid)|개체와 연결 된 터미널 서비스 세션 ID를 가져오려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: GetThreadToken](#getthreadtoken)|지정 된 스레드의 토큰을 사용 하 여를 초기화 하려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: GetTokenId](#gettokenid)|이 메서드를 호출 하 여 개체에 연결 된 토큰 ID를 가져옵니다 `CAccessToken` .|
|[CAccessToken:: GetType](#gettype)|개체의 토큰 형식을 가져오려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: GetUser](#getuser)|이 메서드를 호출 하 여 개체와 연결 된 사용자를 식별 합니다 `CAccessToken` .|
|[CAccessToken:: HKeyCurrentUser](#hkeycurrentuser)|이 메서드를 호출 하 여 개체와 연결 된 사용자 프로필을 가리키는 핸들을 가져옵니다 `CAccessToken` .|
|[CAccessToken:: Impersonate](#impersonate)|이 메서드를 호출 하 여 스레드에 가장을 할당 `CAccessToken` 합니다.|
|[CAccessToken:: ImpersonateLoggedOnUser](#impersonateloggedonuser)|호출 스레드가 로그온 한 사용자의 보안 컨텍스트를 가장할 수 있도록 하려면이 메서드를 호출 합니다.|
|[CAccessToken:: IsTokenRestricted](#istokenrestricted)|개체가 제한 된 Sid 목록을 포함 하는지 테스트 하려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: Processmodel.loaduserprofile](#loaduserprofile)|이 메서드를 호출 하 여 개체와 연결 된 사용자 프로필을 로드 합니다 `CAccessToken` .|
|[CAccessToken:: LogonUser](#logonuser)|지정 된 자격 증명과 연결 된 사용자에 대 한 로그온 세션을 만들려면이 메서드를 호출 합니다.|
|[CAccessToken:: OpenCOMClientToken](#opencomclienttoken)|클라이언트의 호출을 처리 하는 COM 서버 내에서이 메서드를 호출 하 여 COM 클라이언트의 액세스 토큰을 사용 하 여를 초기화 합니다 `CAccessToken` .|
|[CAccessToken:: OpenNamedPipeClientToken](#opennamedpipeclienttoken)|클라이언트에서 액세스 토큰을 사용 하 여를 초기화 하는 명명 된 파이프에 대 한 요청을 수행 하는 서버 내에서이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: OpenRPCClientToken](#openrpcclienttoken)|RPC 클라이언트의 호출을 처리 하는 서버에서이 메서드를 호출 하 여 클라이언트의 액세스 토큰을 사용 하 여를 초기화 합니다 `CAccessToken` .|
|[CAccessToken:: OpenThreadToken](#openthreadtoken)|가장 수준을 설정 하려면이 메서드를 호출 하 고, 지정 된 스레드의 토큰을 사용 하 여를 초기화 합니다 `CAccessToken` .|
|[CAccessToken::P rivilegeCheck](#privilegecheck)|개체에서 지정 된 권한 집합을 사용할 수 있는지 여부를 확인 하려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: Revert](#revert)|가장 토큰을 사용 하는 스레드를 중지 하려면이 메서드를 호출 합니다.|
|[CAccessToken:: SetDefaultDacl](#setdefaultdacl)|개체의 기본 DACL을 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: SetOwner](#setowner)|개체의 소유자를 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.|
|[CAccessToken:: SetPrimaryGroup](#setprimarygroup)|개체의 주 그룹을 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.|

## <a name="remarks"></a>설명

[액세스 토큰](/windows/win32/SecAuthZ/access-tokens) 은 프로세스나 스레드의 보안 컨텍스트를 설명 하 고 Windows 시스템에 로그온 한 각 사용자에 게 할당 되는 개체입니다.

Windows의 액세스 제어 모델에 대 한 소개는 Windows SDK [Access Control](/windows/win32/SecAuthZ/access-control) 를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="caccesstokenattach"></a><a name="attach"></a> CAccessToken:: Attach

지정 된 액세스 토큰 핸들의 소유권을 사용 하려면이 메서드를 호출 합니다.

```cpp
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>매개 변수

*hToken*<br/>
액세스 토큰에 대 한 핸들입니다.

### <a name="remarks"></a>설명

디버그 빌드에서 `CAccessToken` 개체에 액세스 토큰의 소유권이 이미 있는 경우 어설션 오류가 발생 합니다.

## <a name="caccesstokencaccesstoken"></a><a name="dtor"></a> CAccessToken:: ~ CAccessToken

소멸자입니다.

```cpp
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>설명

할당 된 리소스를 모두 해제 합니다.

## <a name="caccesstokenchecktokenmembership"></a><a name="checktokenmembership"></a> CAccessToken:: CheckTokenMembership

지정 된 SID가 개체에서 사용 되는지 확인 하려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>매개 변수

*rSid*<br/>
[CSid 클래스](../../atl/reference/csid-class.md) 개체에 대 한 참조입니다.

*pbIsMember*<br/>
검사 결과를 받는 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

`CheckTokenMembership`메서드는 액세스 토큰의 사용자 및 그룹 sid에 sid가 있는지 확인 합니다. SID가 있고 SE_GROUP_ENABLED 특성이 있는 경우 *Pbismember* 는 TRUE로 설정 됩니다. 그렇지 않으면 FALSE로 설정 됩니다.

디버그 빌드에서는 *Pbismember* 가 유효한 포인터가 아닌 경우 어설션 오류가 발생 합니다.

> [!NOTE]
> `CAccessToken`개체는 주 토큰이 아닌 가장 토큰 이어야 합니다.

## <a name="caccesstokencreateimpersonationtoken"></a><a name="createimpersonationtoken"></a> CAccessToken:: CreateImpersonationToken

가장 액세스 토큰을 만들려면이 메서드를 호출 합니다.

```cpp
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pImp*<br/>
새 개체에 대 한 포인터 `CAccessToken` 입니다.

*sil*<br/>
새 토큰의 가장 수준을 제공 하는 [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) 열거 형식을 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

`CreateImpersonationToken`[DuplicateToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetoken) 를 호출 하 여 새 가장 토큰을 만듭니다.

## <a name="caccesstokencreateprimarytoken"></a><a name="createprimarytoken"></a> CAccessToken:: CreatePrimaryToken

새 기본 토큰을 만들려면이 메서드를 호출 합니다.

```cpp
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pPri*<br/>
새 개체에 대 한 포인터 `CAccessToken` 입니다.

*dwDesiredAccess*<br/>
새 토큰에 대해 요청 된 액세스 권한을 지정 합니다. 기본 MAXIMUM_ALLOWED는 호출자에 게 유효한 모든 액세스 권한을 요청 합니다. 액세스 권한에 대 한 자세한 내용은 액세스 [권한 및 액세스 마스크](/windows/win32/SecAuthZ/access-rights-and-access-masks) 를 참조 하세요.

*pTokenAttributes*<br/>
새 토큰에 대 한 보안 설명자를 지정 하 고 자식 프로세스가 토큰을 상속할 수 있는지 여부를 결정 하는 [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 구조체에 대 한 포인터입니다. *Ptokenattributes* 가 NULL 인 경우 토큰은 기본 보안 설명자를 가져오며 핸들을 상속할 수 없습니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

`CreatePrimaryToken`[DuplicateTokenEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex) 를 호출 하 여 새 주 토큰을 만듭니다.

## <a name="caccesstokencreateprocessasuser"></a><a name="createprocessasuser"></a> CAccessToken:: CreateProcessAsUser

개체가 나타내는 사용자의 보안 컨텍스트에서 실행 되는 새 프로세스를 만들려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool CreateProcessAsUser(
    LPCTSTR pApplicationName,
    LPTSTR pCommandLine,
    LPPROCESS_INFORMATION pProcessInformation,
    LPSTARTUPINFO pStartupInfo,
    DWORD dwCreationFlags = NORMAL_PRIORITY_CLASS,
    bool bLoadProfile = false,
    const CSecurityAttributes* pProcessAttributes = NULL,
    const CSecurityAttributes* pThreadAttributes = NULL,
    bool bInherit = false,
    LPCTSTR pCurrentDirectory = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*pApplicationName*<br/>
실행할 모듈을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. 이 매개 변수는 NULL 일 수 없습니다.

*pCommandLine*<br/>
실행할 명령줄을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*pProcessInformation*<br/>
새 프로세스에 대 한 식별 정보를 수신 하는 [PROCESS_INFORMATION 구조체](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information) 에 대 한 포인터입니다.

*pStartupInfo*<br/>
새 프로세스의 주 창이 표시 되는 방법을 지정 하는 [Startupinfo](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfow) 구조체에 대 한 포인터입니다.

*dwCreationFlags*<br/>
우선 순위 클래스와 프로세스 생성을 제어 하는 추가 플래그를 지정 합니다. 플래그 목록은 Win32 함수 [Createprocessasuser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) 를 참조 하십시오.

*bLoadProfile*<br/>
TRUE 이면 사용자의 프로필이 [processmodel.loaduserprofile](/windows/win32/api/userenv/nf-userenv-loaduserprofilew)를 사용 하 여 로드 됩니다.

*pProcessAttributes*<br/>
새 프로세스에 대 한 보안 설명자를 지정 하 고 자식 프로세스가 반환 된 핸들을 상속할 수 있는지 여부를 결정 하는 [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 구조체에 대 한 포인터입니다. *Pprocessattributes* 가 NULL 인 경우 프로세스는 기본 보안 설명자를 가져오며 핸들을 상속할 수 없습니다.

*pThreadAttributes*<br/>
새 스레드에 대 한 보안 설명자를 지정 하 고 자식 프로세스가 반환 된 핸들을 상속할 수 있는지 여부를 결정 하는 [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 구조체에 대 한 포인터입니다. *Pthreadattributes* 가 NULL 이면 스레드는 기본 보안 설명자를 가져오며 핸들을 상속할 수 없습니다.

*bInherit*<br/>
새 프로세스가 호출 프로세스에서 핸들을 상속 하는지 여부를 나타냅니다. TRUE 이면 호출 프로세스에서 각각의 상속 가능한 열린 핸들이 새 프로세스에 의해 상속 됩니다. 상속 된 핸들에는 원래 핸들과 동일한 값 및 액세스 권한이 있습니다.

*pCurrentDirectory*<br/>
새 프로세스의 현재 드라이브 및 디렉터리를 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. 문자열은 드라이브 문자를 포함 하는 전체 경로 여야 합니다. 이 매개 변수가 NULL 이면 새 프로세스는 호출 프로세스와 동일한 현재 드라이브 및 디렉터리를 갖게 됩니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

`CreateProcessAsUser` 는 Win32 함수를 사용 하 여 `CreateProcessAsUser` 개체가 나타내는 사용자의 보안 컨텍스트에서 실행 되는 새 프로세스를 만듭니다 `CAccessToken` . 필요한 매개 변수에 대 한 자세한 내용은 [Createprocessasuser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) 함수에 대 한 설명을 참조 하세요.

이 메서드가 성공 하려면 `CAccessToken` 개체가 제한 된 토큰이 아닌 경우 할당 된 Primarytoken을 보유 하 고 IncreaseQuota 권한이 있어야 합니다.

## <a name="caccesstokencreaterestrictedtoken"></a><a name="createrestrictedtoken"></a> CAccessToken:: CreateRestrictedToken

새 제한 된 개체를 만들려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pRestrictedToken*<br/>
제한 된 새 `CAccessToken` 개체입니다.

*SidsToDisable*<br/>
`CTokenGroups`거부 전용 sid를 지정 하는 개체입니다.

*Sid를 엄격 하 게*<br/>
`CTokenGroups`제한 sid를 지정 하는 개체입니다.

*PrivilegesToDelete*<br/>
`CTokenPrivileges`제한 된 토큰에서 삭제할 수 있는 권한을 지정 하는 개체입니다. 기본값은 빈 개체를 만듭니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

`CreateRestrictedToken`[CreateRestrictedToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) Win32 함수를 사용 하 여 `CAccessToken` 제한 사항이 있는 새 개체를 만듭니다.

> [!IMPORTANT]
> 를 사용 하는 경우 `CreateRestrictedToken` 다음을 확인 합니다. 기존 토큰은 유효 하 고 (사용자가 입력 하지 않음), *Sidstodisable* 및 *PrivilegesToDelete* 는 모두 유효 하 고 사용자가 입력 하지 않습니다. 메서드가 FALSE, 거부 기능을 반환 하면입니다.

## <a name="caccesstokendetach"></a><a name="detach"></a> CAccessToken::D etach

액세스 토큰의 소유권을 해지 하려면이 메서드를 호출 합니다.

```cpp
HANDLE Detach() throw();
```

### <a name="return-value"></a>반환 값

분리 된에 대 한 핸들을 반환 합니다 `CAccessToken` .

### <a name="remarks"></a>설명

이 메서드는 `CAccessToken` 액세스 토큰의 소유권을 해지 합니다.

## <a name="caccesstokendisableprivilege"></a><a name="disableprivilege"></a> CAccessToken::D isablePrivilege

개체에서 권한을 사용 하지 않도록 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>매개 변수

*pszPrivilege*<br/>
개체에서 사용 하지 않도록 설정할 권한이 포함 된 문자열에 대 한 포인터 `CAccessToken` 입니다.

*pPreviousState*<br/>
`CTokenPrivileges`이전 권한 상태를 포함 하는 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokendisableprivileges"></a><a name="disableprivileges"></a> CAccessToken::D isablePrivileges

개체에서 하나 이상의 권한을 사용 하지 않도록 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>매개 변수

*rPrivileges*<br/>
개체에서 사용 하지 않도록 설정할 수 있는 권한을 포함 하는 문자열 배열에 대 한 포인터 `CAccessToken` 입니다.

*pPreviousState*<br/>
`CTokenPrivileges`이전 권한 상태를 포함 하는 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokenenableprivilege"></a><a name="enableprivilege"></a> CAccessToken:: EnablePrivilege

개체에서 권한을 사용 하도록 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>매개 변수

*pszPrivilege*<br/>
개체에서 사용할 수 있는 권한을 포함 하는 문자열에 대 한 포인터 `CAccessToken` 입니다.

*pPreviousState*<br/>
`CTokenPrivileges`이전 권한 상태를 포함 하는 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokenenableprivileges"></a><a name="enableprivileges"></a> CAccessToken:: EnablePrivileges

개체에서 하나 이상의 권한을 사용 하도록 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>매개 변수

*rPrivileges*<br/>
개체에서 사용할 수 있는 권한을 포함 하는 문자열 배열에 대 한 포인터 `CAccessToken` 입니다.

*pPreviousState*<br/>
`CTokenPrivileges`이전 권한 상태를 포함 하는 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokengetdefaultdacl"></a><a name="getdefaultdacl"></a> CAccessToken:: GetDefaultDacl

개체의 기본 DACL을 반환 하려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>매개 변수

*Pdce Acl*<br/>
개체의 기본 DACL을 수신 하는 [Cdacl 클래스](../../atl/reference/cdacl-class.md) 개체에 대 한 포인터 `CAccessToken` 입니다.

### <a name="return-value"></a>반환 값

기본 DACL이 복구 되었으면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

## <a name="caccesstokengeteffectivetoken"></a><a name="geteffectivetoken"></a> CAccessToken:: GetEffectiveToken

`CAccessToken`현재 스레드에 적용 되는 액세스 토큰과 같은 개체를 가져오려면이 메서드를 호출 합니다.

```cpp
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>매개 변수

*dwDesiredAccess*<br/>
액세스 토큰에 대해 요청된 액세스 형식을 지정하는 액세스 마스크를 지정합니다. 이러한 요청된 액세스 형식은 토큰의 DACL과 비교하여 액세스가 허용 또는 거부되는 경우를 확인합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokengetgroups"></a><a name="getgroups"></a> CAccessToken:: GetGroups

개체의 토큰 그룹을 반환 하려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pGroups*<br/>
그룹 정보를 수신 하는 [CTokenGroups 클래스](../../atl/reference/ctokengroups-class.md) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokengethandle"></a><a name="gethandle"></a> CAccessToken:: GetHandle

액세스 토큰에 대 한 핸들을 검색 하려면이 메서드를 호출 합니다.

```cpp
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>반환 값

개체의 액세스 토큰에 대 한 핸들을 반환 합니다 `CAccessToken` .

## <a name="caccesstokengetimpersonationlevel"></a><a name="getimpersonationlevel"></a> CAccessToken:: GetImpersonationLevel

액세스 토큰에서 가장 수준을 가져오려면이 메서드를 호출 합니다.

```cpp
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pImpersonationLevel*<br/>
가장 수준 정보를 수신 하는 [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) 열거형 형식에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokengetlogonsessionid"></a><a name="getlogonsessionid"></a> CAccessToken:: GetLogonSessionId

이 메서드를 호출 하 여 개체에 연결 된 로그온 세션 ID를 가져옵니다 `CAccessToken` .

```cpp
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pluid*<br/>
로그온 세션 ID를 받을 [LUID](/windows/win32/api/winnt/ns-winnt-luid) 에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

디버그 빌드에서 *pluid* 이 잘못 된 값인 경우 어설션 오류가 발생 합니다.

## <a name="caccesstokengetlogonsid"></a><a name="getlogonsid"></a> CAccessToken:: GetLogonSid

이 메서드를 호출 하 여 개체에 연결 된 로그온 SID를 가져옵니다 `CAccessToken` .

```cpp
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pSid*<br/>
[CSid 클래스](../../atl/reference/csid-class.md) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

디버그 빌드에서 *Psid* 가 잘못 된 값인 경우 어설션 오류가 발생 합니다.

## <a name="caccesstokengetowner"></a><a name="getowner"></a> CAccessToken:: GetOwner

이 메서드를 호출 하 여 개체와 연결 된 소유자를 가져옵니다 `CAccessToken` .

```cpp
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pSid*<br/>
[CSid 클래스](../../atl/reference/csid-class.md) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

소유자는이 액세스 토큰이 적용 되는 동안 생성 된 모든 개체에서 기본적으로 설정 됩니다.

## <a name="caccesstokengetprimarygroup"></a><a name="getprimarygroup"></a> CAccessToken:: GetPrimaryGroup

이 메서드를 호출 하 여 개체에 연결 된 주 그룹을 가져옵니다 `CAccessToken` .

```cpp
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pSid*<br/>
[CSid 클래스](../../atl/reference/csid-class.md) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

이 액세스 토큰이 적용 되는 동안 생성 된 모든 개체에서 그룹이 기본적으로 설정 됩니다.

## <a name="caccesstokengetprivileges"></a><a name="getprivileges"></a> CAccessToken:: GetPrivileges

이 메서드를 호출 하 여 개체와 연결 된 권한을 가져옵니다 `CAccessToken` .

```cpp
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pPrivileges*<br/>
권한을 수신 하는 [CTokenPrivileges 클래스](../../atl/reference/ctokenprivileges-class.md) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokengetprocesstoken"></a><a name="getprocesstoken"></a> CAccessToken:: GetProcessToken

지정된 프로세스의 액세스 토큰을 사용해서 `CAccessToken`을 초기화하려면 이 메서드를 호출합니다.

```cpp
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*dwDesiredAccess*<br/>
액세스 토큰에 대해 요청된 액세스 형식을 지정하는 액세스 마스크를 지정합니다. 이러한 요청된 액세스 형식은 토큰의 DACL과 비교하여 액세스가 허용 또는 거부되는 경우를 확인합니다.

*hProcess*<br/>
액세스 토큰이 열린 프로세스에 대한 핸들입니다. 기본값인 NULL을 사용 하는 경우 현재 프로세스가 사용 됩니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

[OpenProcessToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) Win32 함수를 호출 합니다.

## <a name="caccesstokengetprofile"></a><a name="getprofile"></a> CAccessToken:: GetProfile

이 메서드를 호출 하 여 개체와 연결 된 사용자 프로필을 가리키는 핸들을 가져옵니다 `CAccessToken` .

```cpp
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>반환 값

사용자 프로필을 가리키는 핸들을 반환 하거나 프로필이 존재 하지 않는 경우 NULL을 반환 합니다.

## <a name="caccesstokengetsource"></a><a name="getsource"></a> CAccessToken:: GetSource

개체의 소스를 가져오려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pSource*<br/>
[TOKEN_SOURCE](/windows/win32/api/winnt/ns-winnt-token_source) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokengetstatistics"></a><a name="getstatistics"></a> CAccessToken:: GetStatistics

개체와 연결 된 정보를 가져오려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pStatistics*<br/>
[TOKEN_STATISTICS](/windows/win32/api/winnt/ns-winnt-token_statistics) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokengetterminalservicessessionid"></a><a name="getterminalservicessessionid"></a> CAccessToken:: GetTerminalServicesSessionId

개체와 연결 된 터미널 서비스 세션 ID를 가져오려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pdwSessionId*<br/>
터미널 서비스 세션 ID입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokengetthreadtoken"></a><a name="getthreadtoken"></a> CAccessToken:: GetThreadToken

지정 된 스레드의 토큰을 사용 하 여를 초기화 하려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>매개 변수

*dwDesiredAccess*<br/>
액세스 토큰에 대해 요청된 액세스 형식을 지정하는 액세스 마스크를 지정합니다. 이러한 요청된 액세스 형식은 토큰의 DACL과 비교하여 액세스가 허용 또는 거부되는 경우를 확인합니다.

*hThread*<br/>
액세스 토큰이 열려 있는 스레드에 대 한 핸들입니다.

*bOpenAsSelf*<br/>
메서드를 호출 하는 스레드의 보안 컨텍스트 `GetThreadToken` 또는 호출 스레드에 대 한 프로세스의 보안 컨텍스트에 대 한 액세스 검사를 수행할지 여부를 나타냅니다.

이 매개 변수가 FALSE 이면 호출 하는 스레드에 대 한 보안 컨텍스트를 사용 하 여 액세스 검사를 수행 합니다. 스레드가 클라이언트를 가장 하는 경우이 보안 컨텍스트는 클라이언트 프로세스의이 될 수 있습니다. 이 매개 변수가 TRUE 이면 호출 하는 스레드에 대 한 프로세스의 보안 컨텍스트를 사용 하 여 액세스 검사를 수행 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokengettokenid"></a><a name="gettokenid"></a> CAccessToken:: GetTokenId

이 메서드를 호출 하 여 개체에 연결 된 토큰 ID를 가져옵니다 `CAccessToken` .

```cpp
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pluid*<br/>
토큰 ID를 받을 [LUID](/windows/win32/api/winnt/ns-winnt-luid) 에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokengettype"></a><a name="gettype"></a> CAccessToken:: GetType

개체의 토큰 형식을 가져오려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pType*<br/>
성공 시 토큰 형식을 받는 [TOKEN_TYPE](/windows/win32/api/winnt/ne-winnt-token_type) 변수의 주소입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

TOKEN_TYPE 열거형 형식에는 주 토큰과 가장 토큰을 구분 하는 값이 포함 되어 있습니다.

## <a name="caccesstokengetuser"></a><a name="getuser"></a> CAccessToken:: GetUser

이 메서드를 호출 하 여 개체와 연결 된 사용자를 식별 합니다 `CAccessToken` .

```cpp
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pSid*<br/>
[CSid 클래스](../../atl/reference/csid-class.md) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="caccesstokenhkeycurrentuser"></a><a name="hkeycurrentuser"></a> CAccessToken:: HKeyCurrentUser

이 메서드를 호출 하 여 개체와 연결 된 사용자 프로필을 가리키는 핸들을 가져옵니다 `CAccessToken` .

```cpp
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>반환 값

사용자 프로필을 가리키는 핸들을 반환 하거나 프로필이 존재 하지 않는 경우 NULL을 반환 합니다.

## <a name="caccesstokenimpersonate"></a><a name="impersonate"></a> CAccessToken:: Impersonate

이 메서드를 호출 하 여 스레드에 가장을 할당 `CAccessToken` 합니다.

```cpp
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>매개 변수

*hThread*<br/>
가장 토큰을 할당할 스레드에 대 한 핸들입니다. 이 핸들은 TOKEN_IMPERSONATE 액세스 권한으로 열어야 합니다. *Hthread* 가 NULL 인 경우 메서드는 스레드가 가장 토큰을 사용 하 여 중지 되도록 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

디버그 빌드에서에 토큰에 대 한 유효한 포인터가 없는 경우 어설션 오류가 발생 `CAccessToken` 합니다.

[CAutoRevertImpersonation 클래스](../../atl/reference/cautorevertimpersonation-class.md) 를 사용 하 여 가장 된 액세스 토큰을 자동으로 되돌릴 수 있습니다.

## <a name="caccesstokenimpersonateloggedonuser"></a><a name="impersonateloggedonuser"></a> CAccessToken:: ImpersonateLoggedOnUser

호출 스레드가 로그온 한 사용자의 보안 컨텍스트를 가장할 수 있도록 하려면이 메서드를 호출 합니다.

```cpp
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

> [!IMPORTANT]
> 어떤 이유로 든 가장 함수에 대 한 호출이 실패 하면 클라이언트는 가장 되지 않으며 호출이 수행 된 프로세스의 보안 컨텍스트에서 클라이언트 요청이 수행 됩니다. 프로세스가 높은 권한 있는 계정으로 실행 되거나 관리 그룹의 구성원으로 실행 되는 경우 사용자는 작업을 수행할 수 있습니다. 그렇지 않으면 사용자가 허용 되지 않을 수도 있습니다. 따라서이 함수의 반환 값을 항상 확인 해야 합니다.

## <a name="caccesstokenistokenrestricted"></a><a name="istokenrestricted"></a> CAccessToken:: IsTokenRestricted

개체가 제한 된 Sid 목록을 포함 하는지 테스트 하려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>반환 값

개체에 제한 된 Sid 목록이 포함 되어 있으면 TRUE를 반환 하 고, 제한 된 Sid가 없거나 메서드가 실패 하는 경우 FALSE를 반환 합니다.

## <a name="caccesstokenloaduserprofile"></a><a name="loaduserprofile"></a> CAccessToken:: Processmodel.loaduserprofile

이 메서드를 호출 하 여 개체와 연결 된 사용자 프로필을 로드 합니다 `CAccessToken` .

```cpp
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

디버그 빌드에서에 `CAccessToken` 유효한 토큰이 포함 되어 있지 않거나 사용자 프로필이 이미 있는 경우 어설션 오류가 발생 합니다.

## <a name="caccesstokenlogonuser"></a><a name="logonuser"></a> CAccessToken:: LogonUser

지정 된 자격 증명과 연결 된 사용자에 대 한 로그온 세션을 만들려면이 메서드를 호출 합니다.

```cpp
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>매개 변수

*pszUserName*<br/>
사용자 이름을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. 로그온 하는 데 사용 되는 사용자 계정의 이름입니다.

*pszDomain*<br/>
계정 데이터베이스에 *pszUserName* 계정이 포함 된 도메인 또는 서버의 이름을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*pszPassword*<br/>
*PszUserName* 로 지정 된 사용자 계정에 대 한 일반 텍스트 암호를 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*dwLogonType*<br/>
수행할 로그온 작업의 유형을 지정 합니다. 자세한 내용은 [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) 를 참조 하세요.

*dwLogonProvider*<br/>
로그온 공급자를 지정 합니다. 자세한 내용은 [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) 를 참조 하세요.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

로그온으로 인해 발생 하는 액세스 토큰은에 연결 됩니다 `CAccessToken` . 이 메서드가 성공 하려면 `CAccessToken` 개체는 신뢰할 수 있는 컴퓨터 기반의 일부로 소유자를 식별 하는 SE_TCB_NAME 권한을 보유 해야 합니다. 필요한 권한에 대 한 자세한 내용은 [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) 를 참조 하십시오.

## <a name="caccesstokenopencomclienttoken"></a><a name="opencomclienttoken"></a> CAccessToken:: OpenCOMClientToken

클라이언트의 호출을 처리 하는 COM 서버 내에서이 메서드를 호출 하 여 COM 클라이언트의 액세스 토큰을 사용 하 여를 초기화 합니다 `CAccessToken` .

```cpp
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>매개 변수

*dwDesiredAccess*<br/>
액세스 토큰에 대해 요청된 액세스 형식을 지정하는 액세스 마스크를 지정합니다. 이러한 요청된 액세스 형식은 토큰의 DACL과 비교하여 액세스가 허용 또는 거부되는 경우를 확인합니다.

*bImpersonate*<br/>
TRUE 이면이 호출이 성공적으로 완료 되 면 현재 스레드에서 호출 하는 COM 클라이언트를 가장 합니다. FALSE 이면 액세스 토큰이 열리고이 호출이 완료 되 면 스레드에 가장 토큰이 없습니다.

*bOpenAsSelf*<br/>
[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) 메서드를 호출 하는 스레드의 보안 컨텍스트 또는 호출 스레드에 대 한 프로세스의 보안 컨텍스트에 대 한 액세스 검사를 수행할지 여부를 나타냅니다.

이 매개 변수가 FALSE 이면 호출 하는 스레드에 대 한 보안 컨텍스트를 사용 하 여 액세스 검사를 수행 합니다. 스레드가 클라이언트를 가장 하는 경우이 보안 컨텍스트는 클라이언트 프로세스의이 될 수 있습니다. 이 매개 변수가 TRUE 이면 호출 하는 스레드에 대 한 프로세스의 보안 컨텍스트를 사용 하 여 액세스 검사를 수행 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

[CAutoRevertImpersonation 클래스](../../atl/reference/cautorevertimpersonation-class.md) 를 사용 하면 *BIMPERSONATE* 플래그를 TRUE로 설정 하 여 만든 가장 된 액세스 토큰을 자동으로 되돌릴 수 있습니다.

## <a name="caccesstokenopennamedpipeclienttoken"></a><a name="opennamedpipeclienttoken"></a> CAccessToken:: OpenNamedPipeClientToken

클라이언트에서 액세스 토큰을 사용 하 여를 초기화 하는 명명 된 파이프에 대 한 요청을 수행 하는 서버 내에서이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>매개 변수

*hPipe*<br/>
명명 된 파이프에 대 한 핸들입니다.

*dwDesiredAccess*<br/>
액세스 토큰에 대해 요청된 액세스 형식을 지정하는 액세스 마스크를 지정합니다. 이러한 요청된 액세스 형식은 토큰의 DACL과 비교하여 액세스가 허용 또는 거부되는 경우를 확인합니다.

*bImpersonate*<br/>
TRUE 이면이 호출이 성공적으로 완료 되 면 현재 스레드에서 호출 파이프 클라이언트를 가장 합니다. FALSE 이면 액세스 토큰이 열리고이 호출이 완료 되 면 스레드에 가장 토큰이 없습니다.

*bOpenAsSelf*<br/>
[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) 메서드를 호출 하는 스레드의 보안 컨텍스트 또는 호출 스레드에 대 한 프로세스의 보안 컨텍스트에 대 한 액세스 검사를 수행할지 여부를 나타냅니다.

이 매개 변수가 FALSE 이면 호출 하는 스레드에 대 한 보안 컨텍스트를 사용 하 여 액세스 검사를 수행 합니다. 스레드가 클라이언트를 가장 하는 경우이 보안 컨텍스트는 클라이언트 프로세스의이 될 수 있습니다. 이 매개 변수가 TRUE 이면 호출 하는 스레드에 대 한 프로세스의 보안 컨텍스트를 사용 하 여 액세스 검사를 수행 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

[CAutoRevertImpersonation 클래스](../../atl/reference/cautorevertimpersonation-class.md) 를 사용 하면 *BIMPERSONATE* 플래그를 TRUE로 설정 하 여 만든 가장 된 액세스 토큰을 자동으로 되돌릴 수 있습니다.

## <a name="caccesstokenopenrpcclienttoken"></a><a name="openrpcclienttoken"></a> CAccessToken:: OpenRPCClientToken

RPC 클라이언트의 호출을 처리 하는 서버에서이 메서드를 호출 하 여 클라이언트의 액세스 토큰을 사용 하 여를 초기화 합니다 `CAccessToken` .

```cpp
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>매개 변수

*BindingHandle*<br/>
클라이언트에 대 한 바인딩을 나타내는 서버에 대 한 바인딩 핸들입니다.

*dwDesiredAccess*<br/>
액세스 토큰에 대해 요청된 액세스 형식을 지정하는 액세스 마스크를 지정합니다. 이러한 요청된 액세스 형식은 토큰의 DACL과 비교하여 액세스가 허용 또는 거부되는 경우를 확인합니다.

*bImpersonate*<br/>
TRUE 이면이 호출이 성공적으로 완료 되 면 현재 스레드에서 호출 하는 RPC 클라이언트를 가장 합니다. FALSE 이면 액세스 토큰이 열리고이 호출이 완료 되 면 스레드에 가장 토큰이 없습니다.

*bOpenAsSelf*<br/>
[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) 메서드를 호출 하는 스레드의 보안 컨텍스트 또는 호출 스레드에 대 한 프로세스의 보안 컨텍스트에 대 한 액세스 검사를 수행할지 여부를 나타냅니다.

이 매개 변수가 FALSE 이면 호출 하는 스레드에 대 한 보안 컨텍스트를 사용 하 여 액세스 검사를 수행 합니다. 스레드가 클라이언트를 가장 하는 경우이 보안 컨텍스트는 클라이언트 프로세스의이 될 수 있습니다. 이 매개 변수가 TRUE 이면 호출 하는 스레드에 대 한 프로세스의 보안 컨텍스트를 사용 하 여 액세스 검사를 수행 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

[CAutoRevertImpersonation 클래스](../../atl/reference/cautorevertimpersonation-class.md) 를 사용 하면 *BIMPERSONATE* 플래그를 TRUE로 설정 하 여 만든 가장 된 액세스 토큰을 자동으로 되돌릴 수 있습니다.

## <a name="caccesstokenopenthreadtoken"></a><a name="openthreadtoken"></a> CAccessToken:: OpenThreadToken

가장 수준을 설정 하려면이 메서드를 호출 하 고, 지정 된 스레드의 토큰을 사용 하 여를 초기화 합니다 `CAccessToken` .

```cpp
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>매개 변수

*dwDesiredAccess*<br/>
액세스 토큰에 대해 요청된 액세스 형식을 지정하는 액세스 마스크를 지정합니다. 이러한 요청된 액세스 형식은 토큰의 DACL과 비교하여 액세스가 허용 또는 거부되는 경우를 확인합니다.

*bImpersonate*<br/>
TRUE 이면이 메서드가 완료 된 후 요청 된 가장 수준에서 스레드를 그대로 유지 합니다. FALSE 이면 스레드가 원래 가장 수준으로 되돌아갑니다.

*bOpenAsSelf*<br/>
[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) 메서드를 호출 하는 스레드의 보안 컨텍스트 또는 호출 스레드에 대 한 프로세스의 보안 컨텍스트에 대 한 액세스 검사를 수행할지 여부를 나타냅니다.

이 매개 변수가 FALSE 이면 호출 하는 스레드에 대 한 보안 컨텍스트를 사용 하 여 액세스 검사를 수행 합니다. 스레드가 클라이언트를 가장 하는 경우이 보안 컨텍스트는 클라이언트 프로세스의이 될 수 있습니다. 이 매개 변수가 TRUE 이면 호출 하는 스레드에 대 한 프로세스의 보안 컨텍스트를 사용 하 여 액세스 검사를 수행 합니다.

*sil*<br/>
토큰의 가장 수준을 제공 하는 [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) 열거 형식을 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

`OpenThreadToken` 는 [CAccessToken:: GetThreadToken](#getthreadtoken)와 유사 하지만 `CAccessToken` 스레드 액세스 토큰에서를 초기화 하기 전에 가장 수준을 설정 합니다.

[CAutoRevertImpersonation 클래스](../../atl/reference/cautorevertimpersonation-class.md) 를 사용 하면 *BIMPERSONATE* 플래그를 TRUE로 설정 하 여 만든 가장 된 액세스 토큰을 자동으로 되돌릴 수 있습니다.

## <a name="caccesstokenprivilegecheck"></a><a name="privilegecheck"></a> CAccessToken::P rivilegeCheck

개체에서 지정 된 권한 집합을 사용할 수 있는지 여부를 확인 하려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>매개 변수

*RequiredPrivileges*<br/>
[PRIVILEGE_SET](/windows/win32/api/winnt/ns-winnt-privilege_set) 구조체에 대 한 포인터입니다.

*Presult*<br/>
개체에서 지정 된 권한 중 일부 또는 모두를 사용할 수 있는지 여부를 나타내는 메서드를 설정 하는 값에 대 한 포인터입니다 `CAccessToken` .

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

가 `PrivilegeCheck` 반환 되 면 `Attributes` 해당 권한이 설정 된 경우 각 [LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes) 구조의 멤버가 SE_PRIVILEGE_USED_FOR_ACCESS로 설정 됩니다. 이 메서드는 [PrivilegeCheck](/windows/win32/api/securitybaseapi/nf-securitybaseapi-privilegecheck) Win32 함수를 호출 합니다.

## <a name="caccesstokenrevert"></a><a name="revert"></a> CAccessToken:: Revert

이 메서드를 호출 하 여 스레드가 가장 토큰을 사용 하지 않도록 합니다.

```cpp
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>매개 변수

*hThread*<br/>
가장에서 되돌릴 스레드에 대 한 핸들입니다. *Hthread* 가 NULL 이면 현재 스레드를 가정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

가장 토큰의 변경할지는 [CAutoRevertImpersonation 클래스](../../atl/reference/cautorevertimpersonation-class.md)를 사용 하 여 자동으로 수행할 수 있습니다.

## <a name="caccesstokensetdefaultdacl"></a><a name="setdefaultdacl"></a> CAccessToken:: SetDefaultDacl

개체의 기본 DACL을 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>매개 변수

*rDacl*<br/>
새 기본 [Cdacl 클래스](../../atl/reference/cdacl-class.md) 정보입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

기본 DACL은이 액세스 토큰을 적용 하 여 새 개체를 만들 때 기본적으로 사용 되는 DACL입니다.

## <a name="caccesstokensetowner"></a><a name="setowner"></a> CAccessToken:: SetOwner

개체의 소유자를 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>매개 변수

*rSid*<br/>
소유자 정보를 포함 하는 [CSid 클래스](../../atl/reference/csid-class.md) 개체입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

소유자는이 액세스 토큰이 적용 되는 동안 생성 된 새 개체에 사용 되는 기본 소유자입니다.

## <a name="caccesstokensetprimarygroup"></a><a name="setprimarygroup"></a> CAccessToken:: SetPrimaryGroup

개체의 주 그룹을 설정 하려면이 메서드를 호출 `CAccessToken` 합니다.

```cpp
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>매개 변수

*rSid*<br/>
주 그룹 정보를 포함 하는 [CSid 클래스](../../atl/reference/csid-class.md) 개체입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

주 그룹은이 액세스 토큰이 적용 되는 동안 생성 된 새 개체에 대 한 기본 그룹입니다.

## <a name="see-also"></a>참고 항목

[보안 되지 않은 보안 샘플](../../overview/visual-cpp-samples.md)<br/>
[액세스 토큰](/windows/win32/SecAuthZ/access-tokens)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
