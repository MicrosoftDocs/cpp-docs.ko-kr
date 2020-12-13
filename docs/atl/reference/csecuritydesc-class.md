---
description: '자세히 알아보기: CSecurityDesc 클래스'
title: CSecurityDesc 클래스
ms.date: 11/04/2016
f1_keywords:
- CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::FromString
- ATLSECURITY/ATL::CSecurityDesc::GetControl
- ATLSECURITY/ATL::CSecurityDesc::GetDacl
- ATLSECURITY/ATL::CSecurityDesc::GetGroup
- ATLSECURITY/ATL::CSecurityDesc::GetOwner
- ATLSECURITY/ATL::CSecurityDesc::GetPSECURITY_DESCRIPTOR
- ATLSECURITY/ATL::CSecurityDesc::GetSacl
- ATLSECURITY/ATL::CSecurityDesc::IsDaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsDaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsDaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsDaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsGroupDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsOwnerDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsSaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsSaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::MakeAbsolute
- ATLSECURITY/ATL::CSecurityDesc::MakeSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::SetControl
- ATLSECURITY/ATL::CSecurityDesc::SetDacl
- ATLSECURITY/ATL::CSecurityDesc::SetGroup
- ATLSECURITY/ATL::CSecurityDesc::SetOwner
- ATLSECURITY/ATL::CSecurityDesc::SetSacl
- ATLSECURITY/ATL::CSecurityDesc::ToString
helpviewer_keywords:
- CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
ms.openlocfilehash: 66a2229aa4819059a353baf8b3802bb1263da2e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140779"
---
# <a name="csecuritydesc-class"></a>CSecurityDesc 클래스

이 클래스는 구조체에 대 한 래퍼입니다 `SECURITY_DESCRIPTOR` .

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CSecurityDesc
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSecurityDesc:: CSecurityDesc](#csecuritydesc)|생성자입니다.|
|[CSecurityDesc:: ~ CSecurityDesc](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSecurityDesc:: FromString](#fromstring)|문자열 형식 보안 설명자를 올바른 기능 보안 설명자로 변환 합니다.|
|[CSecurityDesc:: GetControl](#getcontrol)|보안 설명자에서 컨트롤 정보를 검색 합니다.|
|[CSecurityDesc:: GetDacl](#getdacl)|보안 설명자에서 DACL (임의 액세스 제어 목록) 정보를 검색 합니다.|
|[CSecurityDesc:: GetGroup](#getgroup)|보안 설명자에서 주 그룹 정보를 검색 합니다.|
|[CSecurityDesc:: GetOwner](#getowner)|보안 설명자에서 소유자 내용은를 검색 합니다.|
|[CSecurityDesc:: GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|구조체에 대 한 포인터를 반환 합니다 `SECURITY_DESCRIPTOR` .|
|[CSecurityDesc:: GetSacl](#getsacl)|보안 설명자에서 SACL (시스템 액세스 제어 목록) 정보를 검색 합니다.|
|[CSecurityDesc:: IsDaclAutoInherited](#isdaclautoinherited)|DACL이 자동 전파를 지원 하도록 구성 되어 있는지 여부를 확인 합니다.|
|[CSecurityDesc:: IsDaclDefaulted](#isdacldefaulted)|보안 설명자가 기본 DACL로 구성 되어 있는지 여부를 확인 합니다.|
|[CSecurityDesc:: IsDaclPresent](#isdaclpresent)|보안 설명자에 DACL이 포함 되어 있는지 여부를 확인 합니다.|
|[CSecurityDesc:: IsDaclProtected](#isdaclprotected)|DACL이 수정 되지 않도록 구성 되었는지 여부를 확인 합니다.|
|[CSecurityDesc:: IsGroupDefaulted](#isgroupdefaulted)|보안 설명자의 그룹 보안 식별자 (SID)가 기본적으로 설정 되어 있는지 여부를 확인 합니다.|
|[CSecurityDesc:: IsOwnerDefaulted](#isownerdefaulted)|보안 설명자의 소유자 SID가 기본적으로 설정 되어 있는지 여부를 확인 합니다.|
|[CSecurityDesc:: IsSaclAutoInherited](#issaclautoinherited)|SACL이 자동 전파를 지원 하도록 구성 되어 있는지 여부를 확인 합니다.|
|[CSecurityDesc:: IsSaclDefaulted](#issacldefaulted)|보안 설명자가 기본 SACL로 구성 되어 있는지 여부를 확인 합니다.|
|[CSecurityDesc:: IsSaclPresent](#issaclpresent)|보안 설명자에 SACL이 포함 되어 있는지 여부를 확인 합니다.|
|[CSecurityDesc:: IsSaclProtected](#issaclprotected)|SACL이 수정 되지 않도록 구성 되었는지 여부를 확인 합니다.|
|[CSecurityDesc:: IsSelfRelative](#isselfrelative)|보안 설명자가 자체 상대 형식 인지 여부를 확인 합니다.|
|[CSecurityDesc:: MakeAbsolute](#makeabsolute)|보안 설명자를 절대 형식으로 변환 하려면이 메서드를 호출 합니다.|
|[CSecurityDesc:: MakeSelfRelative](#makeselfrelative)|보안 설명자를 자체 상대 형식으로 변환 하려면이 메서드를 호출 합니다.|
|[CSecurityDesc:: SetControl](#setcontrol)|보안 설명자의 제어 비트를 설정합니다.|
|[CSecurityDesc:: SetDacl](#setdacl)|DACL에 정보를 설정 합니다. DACL이 보안 설명자에 이미 있는 경우 대체 됩니다.|
|[CSecurityDesc:: SetGroup](#setgroup)|이미 있는 주 그룹 정보를 대체 하 여 절대 형식 보안 설명자의 주 그룹 정보를 설정 합니다.|
|[CSecurityDesc:: SetOwner](#setowner)|이미 있는 소유자 정보를 대체 하 여 절대 형식 보안 설명자의 소유자 정보를 설정 합니다.|
|[CSecurityDesc:: SetSacl](#setsacl)|SACL의 정보를 설정 합니다. 보안 설명자에 SACL이 이미 있는 경우이를 대체 합니다.|
|[CSecurityDesc:: ToString](#tostring)|보안 설명자를 문자열 형식으로 변환 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CSecurityDesc:: operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|구조체에 대 한 포인터를 반환 합니다 `SECURITY_DESCRIPTOR` .|
|[CSecurityDesc:: operator =](#operator_eq)|대입 연산자입니다.|

## <a name="remarks"></a>설명

구조체에는 `SECURITY_DESCRIPTOR` 개체와 연결 된 보안 정보가 포함 되어 있습니다. 응용 프로그램은이 구조를 사용 하 여 개체의 보안 상태를 설정 하 고 쿼리 합니다. [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor)도 참조 하세요.

응용 프로그램은 구조를 직접 수정 하면 안 `SECURITY_DESCRIPTOR` 되며 제공 된 클래스 메서드를 대신 사용 해야 합니다.

Windows의 액세스 제어 모델에 대 한 소개는 Windows SDK [Access Control](/windows/win32/SecAuthZ/access-control) 를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="csecuritydesccsecuritydesc"></a><a name="csecuritydesc"></a> CSecurityDesc:: CSecurityDesc

생성자입니다.

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>매개 변수

*rhs*<br/>
`CSecurityDesc` `SECURITY_DESCRIPTOR` 새 개체에 할당할 개체 또는 구조체 `CSecurityDesc` 입니다.

### <a name="remarks"></a>설명

`CSecurityDesc`필요에 따라 `SECURITY_DESCRIPTOR` 구조체 또는 이전에 정의 된 개체를 사용 하 여 개체를 만들 수 있습니다 `CSecurityDesc` .

## <a name="csecuritydesccsecuritydesc"></a><a name="dtor"></a> CSecurityDesc:: ~ CSecurityDesc

소멸자입니다.

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>설명

소멸자는 할당 된 리소스를 모두 해제 합니다.

## <a name="csecuritydescfromstring"></a><a name="fromstring"></a> CSecurityDesc:: FromString

문자열 형식 보안 설명자를 올바른 기능 보안 설명자로 변환 합니다.

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>매개 변수

*pstr*<br/>
변환할 [문자열 형식 보안 설명자](/windows/win32/SecAuthZ/security-descriptor-string-format) 를 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 true를 반환 합니다. 실패 한 경우 예외를 throw 합니다.

### <a name="remarks"></a>설명

[Csecuritydesc:: ToString](#tostring)을 사용 하 여 문자열을 만들 수 있습니다. 보안 설명자를 문자열로 변환 하면 저장 및 전송 하기가 더 쉽습니다.

이 메서드는 [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)을 호출 합니다.

## <a name="csecuritydescgetcontrol"></a><a name="getcontrol"></a> CSecurityDesc:: GetControl

보안 설명자에서 컨트롤 정보를 검색 합니다.

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>매개 변수

*psdc*<br/>
`SECURITY_DESCRIPTOR_CONTROL`보안 설명자의 컨트롤 정보를 수신 하는 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 true를 반환 하 고 실패 하면 false를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 [GetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol)을 호출 합니다.

## <a name="csecuritydescgetdacl"></a><a name="getdacl"></a> CSecurityDesc:: GetDacl

보안 설명자에서 DACL (임의 액세스 제어 목록) 정보를 검색 합니다.

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>매개 변수

*Pdce Acl*<br/>
`CDacl`보안 설명자의 DACL 복사본을 저장할 구조에 대 한 포인터입니다. 임의 ACL이 있는 경우 메서드는 해당 acl을 보안 설명자의 임의 ACL *주소로 설정 합니다* . 임의 ACL이 없으면 값이 저장 되지 않습니다.

*Ppresent*<br/>
지정 된 보안 설명자에 임의 ACL이 있는지 여부를 나타내는 값에 대 한 포인터입니다. 보안 설명자에 임의의 ACL이 포함 된 경우이 매개 변수는 true로 설정 됩니다. 보안 설명자에 임의 ACL이 포함 되어 있지 않으면이 매개 변수는 false로 설정 됩니다.

*P기본값*<br/>
`SECURITY_DESCRIPTOR_CONTROL`보안 설명자에 대 한 임의 ACL이 존재 하는 경우 구조체의 SE_DACL_DEFAULTED 플래그 값으로 설정 된 플래그에 대 한 포인터입니다. 이 플래그가 true 이면 임의 ACL이 기본 메커니즘에 의해 검색 된 것입니다. false 이면 사용자가 임의 ACL을 명시적으로 지정 했습니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 true를 반환 하 고 실패 하면 false를 반환 합니다.

## <a name="csecuritydescgetgroup"></a><a name="getgroup"></a> CSecurityDesc:: GetGroup

보안 설명자에서 주 그룹 정보를 검색 합니다.

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pSid*<br/>
CDacl에 저장 된 그룹의 복사본을 받는 [CSid](../../atl/reference/csid-class.md) (보안 식별자)에 대 한 포인터입니다.

*P기본값*<br/>
메서드가 반환 될 때 구조체의 SE_GROUP_DEFAULTED 플래그 값으로 설정 된 플래그에 대 한 포인터입니다 `SECURITY_DESCRIPTOR_CONTROL` .

### <a name="return-value"></a>반환 값

메서드가 성공 하면 true를 반환 하 고 실패 하면 false를 반환 합니다.

## <a name="csecuritydescgetowner"></a><a name="getowner"></a> CSecurityDesc:: GetOwner

보안 설명자에서 소유자 내용은를 검색 합니다.

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pSid*<br/>
CDacl에 저장 된 그룹의 복사본을 받는 [CSid](../../atl/reference/csid-class.md) (보안 식별자)에 대 한 포인터입니다.

*P기본값*<br/>
메서드가 반환 될 때 구조체의 SE_OWNER_DEFAULTED 플래그 값으로 설정 된 플래그에 대 한 포인터입니다 `SECURITY_DESCRIPTOR_CONTROL` .

### <a name="return-value"></a>반환 값

메서드가 성공 하면 true를 반환 하 고 실패 하면 false를 반환 합니다.

## <a name="csecuritydescgetpsecurity_descriptor"></a><a name="getpsecurity_descriptor"></a> CSecurityDesc:: GetPSECURITY_DESCRIPTOR

구조체에 대 한 포인터를 반환 합니다 `SECURITY_DESCRIPTOR` .

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>반환 값

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor) 구조체에 대 한 포인터를 반환 합니다.

## <a name="csecuritydescgetsacl"></a><a name="getsacl"></a> CSecurityDesc:: GetSacl

보안 설명자에서 SACL (시스템 액세스 제어 목록) 정보를 검색 합니다.

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pSacl*<br/>
`CSacl`보안 설명자의 SACL 복사본을 저장할 구조에 대 한 포인터입니다. 시스템 ACL이 있는 경우 메서드는 *Psacl* 을 보안 설명자의 시스템 acl 주소로 설정 합니다. 시스템 ACL이 없으면 값이 저장 되지 않습니다.

*Ppresent*<br/>
지정 된 보안 설명자에 시스템 ACL이 있음을 나타내기 위해 메서드에서 설정 하는 플래그에 대 한 포인터입니다. 보안 설명자에 시스템 ACL이 포함 된 경우이 매개 변수는 true로 설정 됩니다. 보안 설명자에 시스템 ACL이 없는 경우이 매개 변수는 false로 설정 됩니다.

*P기본값*<br/>
`SECURITY_DESCRIPTOR_CONTROL`보안 설명자에 대 한 시스템 ACL이 존재 하는 경우 구조체의 SE_SACL_DEFAULTED 플래그 값으로 설정 된 플래그에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 true를 반환 하 고 실패 하면 false를 반환 합니다.

## <a name="csecuritydescisdaclautoinherited"></a><a name="isdaclautoinherited"></a> CSecurityDesc:: IsDaclAutoInherited

DACL (임의 액세스 제어 목록)이 자동 전파를 지원 하도록 구성 되어 있는지 여부를 확인 합니다.

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>반환 값

보안 설명자에 상속 가능한 Ace (액세스 제어 항목)를 기존 자식 개체에 자동으로 전파 하도록 설정 된 DACL이 포함 되어 있는 경우 true를 반환 합니다. 그렇지 않으면 false를 반환합니다.

### <a name="remarks"></a>설명

시스템은 개체 및 기존 자식 개체에 대해 자동 상속 알고리즘을 수행할 때이 비트를 설정 합니다.

## <a name="csecuritydescisdacldefaulted"></a><a name="isdacldefaulted"></a> CSecurityDesc:: IsDaclDefaulted

보안 설명자가 기본 DACL (임의 액세스 제어 목록)을 사용 하 여 구성 되었는지 여부를 확인 합니다.

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>반환 값

보안 설명자에 기본 DACL이 포함 되어 있으면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

이 플래그는 ACE (액세스 제어 항목) 상속과 관련 하 여 시스템에서 DACL을 처리 하는 방법에 영향을 줄 수 있습니다. 예를 들어 개체의 작성자가 DACL을 지정 하지 않으면 개체는 작성자의 액세스 토큰에서 기본 DACL을 받습니다. SE_DACL_PRESENT 플래그가 설정 되지 않은 경우 시스템에서이 플래그를 무시 합니다.

이 플래그는 개체의 최종 DACL을 계산 하는 방법을 결정 하는 데 사용 되며 보안 개체의 보안 설명자 컨트롤에 물리적으로 저장 되지 않습니다.

이 플래그를 설정 하려면 [Csecuritydesc:: SetDacl](#setdacl) 메서드를 사용 합니다.

## <a name="csecuritydescisdaclpresent"></a><a name="isdaclpresent"></a> CSecurityDesc:: IsDaclPresent

보안 설명자에 DACL (임의 액세스 제어 목록)이 포함 되어 있는지 여부를 확인 합니다.

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>반환 값

보안 설명자에 DACL이 포함 되어 있으면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

이 플래그가 설정 되어 있지 않거나이 플래그가 설정 되 고 DACL이 NULL 인 경우 보안 설명자는 모든 사용자에 게 모든 액세스를 허용 합니다.

이 플래그는 보안 설명자가 보안 개체와 연결 될 때까지 호출자가 지정 하는 보안 정보를 저장 하는 데 사용 됩니다. 보안 설명자가 보안 개체와 연결 되 면 항상 보안 설명자 컨트롤에서 SE_DACL_PRESENT 플래그가 설정 됩니다.

이 플래그를 설정 하려면 [Csecuritydesc:: SetDacl](#setdacl) 메서드를 사용 합니다.

## <a name="csecuritydescisdaclprotected"></a><a name="isdaclprotected"></a> CSecurityDesc:: IsDaclProtected

DACL (임의 액세스 제어 목록)이 수정 되지 않도록 구성 되었는지 여부를 확인 합니다.

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>반환 값

DACL이 상속 가능한 Ace (액세스 제어 항목)에서 보안 설명자를 수정 하지 못하도록 구성 된 경우 true를 반환 합니다. 그렇지 않으면 false를 반환합니다.

### <a name="remarks"></a>설명

이 플래그를 설정 하려면 [Csecuritydesc:: SetDacl](#setdacl) 메서드를 사용 합니다.

이 메서드는 상속 가능한 Ace의 자동 전파를 지원 합니다.

## <a name="csecuritydescisgroupdefaulted"></a><a name="isgroupdefaulted"></a> CSecurityDesc:: IsGroupDefaulted

보안 설명자의 그룹 보안 식별자 (SID)가 기본적으로 설정 되어 있는지 여부를 확인 합니다.

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>반환 값

보안 설명자의 원래 공급자가 아닌 기본 메커니즘이 보안 설명자의 그룹 SID를 제공한 경우 true를 반환 합니다. 그렇지 않으면 false를 반환합니다.

### <a name="remarks"></a>설명

이 플래그를 설정 하려면 [Csecuritydesc:: SetGroup](#setgroup) 메서드를 사용 합니다.

## <a name="csecuritydescisownerdefaulted"></a><a name="isownerdefaulted"></a> CSecurityDesc:: IsOwnerDefaulted

보안 설명자의 소유자 보안 식별자 (SID)가 기본적으로 설정 되어 있는지 여부를 확인 합니다.

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>반환 값

보안 설명자의 원본 공급자가 아닌 기본 메커니즘이 보안 설명자의 소유자 SID를 제공한 경우 true를 반환 합니다. 그렇지 않으면 false를 반환합니다.

### <a name="remarks"></a>설명

이 플래그를 설정 하려면 [Csecuritydesc:: SetOwner](#setowner) 메서드를 사용 합니다.

## <a name="csecuritydescissaclautoinherited"></a><a name="issaclautoinherited"></a> CSecurityDesc:: IsSaclAutoInherited

SACL (시스템 액세스 제어 목록)이 자동 전파를 지원 하도록 구성 되어 있는지 여부를 확인 합니다.

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>반환 값

보안 설명자에 상속 가능한 Ace (액세스 제어 항목)를 기존 자식 개체에 자동으로 전파 하도록 설정 된 SACL이 포함 되어 있는 경우 true를 반환 합니다. 그렇지 않으면 false를 반환합니다.

### <a name="remarks"></a>설명

시스템은 개체 및 기존 자식 개체에 대해 자동 상속 알고리즘을 수행할 때이 비트를 설정 합니다.

## <a name="csecuritydescissacldefaulted"></a><a name="issacldefaulted"></a> CSecurityDesc:: IsSaclDefaulted

보안 설명자가 기본 SACL (시스템 액세스 제어 목록)로 구성 되었는지 여부를 확인 합니다.

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>반환 값

보안 설명자에 기본 SACL이 포함 되어 있으면 true를, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

이 플래그는 ACE (액세스 제어 항목) 상속과 관련 하 여 시스템이 SACL을 처리 하는 방법에 영향을 줄 수 있습니다. SE_SACL_PRESENT 플래그가 설정 되지 않은 경우 시스템에서이 플래그를 무시 합니다.

이 플래그를 설정 하려면 [Csecuritydesc:: SetSacl](#setsacl) 메서드를 사용 합니다.

## <a name="csecuritydescissaclpresent"></a><a name="issaclpresent"></a> CSecurityDesc:: IsSaclPresent

보안 설명자에 SACL (시스템 액세스 제어 목록)이 포함 되어 있는지 여부를 확인 합니다.

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>반환 값

보안 설명자에 SACL이 포함 되어 있으면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

이 플래그를 설정 하려면 [Csecuritydesc:: SetSacl](#setsacl) 메서드를 사용 합니다.

## <a name="csecuritydescissaclprotected"></a><a name="issaclprotected"></a> CSecurityDesc:: IsSaclProtected

SACL (시스템 액세스 제어 목록)이 수정 되지 않도록 구성 되어 있는지 여부를 확인 합니다.

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>반환 값

SACL이 상속 가능한 Ace (액세스 제어 항목)에 의해 보안 설명자가 수정 되지 않도록 구성 된 경우 true를 반환 합니다. 그렇지 않으면 false를 반환합니다.

### <a name="remarks"></a>설명

이 플래그를 설정 하려면 [Csecuritydesc:: SetSacl](#setsacl) 메서드를 사용 합니다.

이 메서드는 상속 가능한 Ace의 자동 전파를 지원 합니다.

## <a name="csecuritydescisselfrelative"></a><a name="isselfrelative"></a> CSecurityDesc:: IsSelfRelative

보안 설명자가 자체 상대 형식 인지 여부를 확인 합니다.

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>반환 값

보안 설명자가 인접 한 메모리 블록에 있는 모든 보안 정보와 함께 자체 상대 형식인 경우 true를 반환 합니다. 보안 설명자가 절대 형식이 면 false를 반환 합니다. 자세한 내용은 [절대 및 Self-Relative 보안 설명자](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)를 참조 하세요.

## <a name="csecuritydescmakeabsolute"></a><a name="makeabsolute"></a> CSecurityDesc:: MakeAbsolute

보안 설명자를 절대 형식으로 변환 하려면이 메서드를 호출 합니다.

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>반환 값

메서드가 성공 하면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

절대 형식의 보안 설명자에는 정보 자체가 아닌 포함 된 정보에 대 한 포인터가 포함 되어 있습니다. 자체 상대 형식의 보안 설명자에는 인접 한 메모리 블록의 정보가 포함 됩니다. 자체 상대 보안 설명자에서 `SECURITY_DESCRIPTOR` 구조는 항상 정보를 시작 하지만 보안 설명자의 다른 구성 요소는 모든 순서로 구조를 따를 수 있습니다. 메모리 주소를 사용 하는 대신 자체 상대 보안 설명자의 구성 요소는 보안 설명자의 시작 부분에서 오프셋으로 식별 됩니다. 이 형식은 보안 설명자를 디스크에 저장 하거나 통신 프로토콜을 통해 전송 해야 하는 경우에 유용 합니다. 자세한 내용은 [절대 및 Self-Relative 보안 설명자](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)를 참조 하세요.

## <a name="csecuritydescmakeselfrelative"></a><a name="makeselfrelative"></a> CSecurityDesc:: MakeSelfRelative

보안 설명자를 자체 상대 형식으로 변환 하려면이 메서드를 호출 합니다.

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>반환 값

메서드가 성공 하면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

절대 형식의 보안 설명자에는 정보 자체를 포함 하는 것이 아니라 포함 된 정보에 대 한 포인터가 포함 되어 있습니다. 자체 상대 형식의 보안 설명자에는 인접 한 메모리 블록의 정보가 포함 됩니다. 자체 상대 보안 설명자에서 `SECURITY_DESCRIPTOR` 구조는 항상 정보를 시작 하지만 보안 설명자의 다른 구성 요소는 모든 순서로 구조를 따를 수 있습니다. 보안 설명자의 구성 요소는 메모리 주소를 사용 하는 대신 보안 설명자의 시작 부분에서 오프셋으로 식별 됩니다. 이 형식은 보안 설명자를 디스크에 저장 하거나 통신 프로토콜을 통해 전송 해야 하는 경우에 유용 합니다. 자세한 내용은 [절대 및 Self-Relative 보안 설명자](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)를 참조 하세요.

## <a name="csecuritydescoperator-"></a><a name="operator_eq"></a> CSecurityDesc:: operator =

대입 연산자입니다.

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>매개 변수

*rhs*<br/>
`SECURITY_DESCRIPTOR` `CSecurityDesc` 개체에 할당할 구조체 또는 개체 `CSecurityDesc` 입니다.

### <a name="return-value"></a>반환 값

업데이트 된 개체를 반환 `CSecurityDesc` 합니다.

## <a name="csecuritydescoperator-const-security_descriptor-"></a><a name="operator_const_security_descriptor__star"></a> CSecurityDesc:: operator const SECURITY_DESCRIPTOR *

구조체에 대 한 포인터로 값을 캐스팅 `SECURITY_DESCRIPTOR` 합니다.

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

## <a name="csecuritydescsetcontrol"></a><a name="setcontrol"></a> CSecurityDesc:: SetControl

보안 설명자의 제어 비트를 설정합니다.

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>매개 변수

*ControlBitsOfInterest*<br/>
설정하려는 제어 비트를 나타내는 SECURITY_DESCRIPTOR_CONTROL 마스크입니다. 설정할 수 있는 플래그 목록은 [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol)를 참조 하세요.

*ControlBitsToSet*<br/>
*ControlBitsOfInterest* mask로 지정 된 컨트롤 비트의 새 값을 나타내는 마스크입니다. SECURITY_DESCRIPTOR_CONTROL 이 매개 변수는 *ControlBitsOfInterest* 매개 변수에 대해 나열 된 플래그의 조합일 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="remarks"></a>설명

이 메서드는 [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol)을 호출 합니다.

## <a name="csecuritydescsetdacl"></a><a name="setdacl"></a> CSecurityDesc:: SetDacl

DACL (임의 액세스 제어 목록)에 정보를 설정 합니다. DACL이 보안 설명자에 이미 있는 경우 대체 됩니다.

```
inline void SetDacl(
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>매개 변수

*Dacl*<br/>
`CDacl`보안 설명자에 대 한 DACL을 지정 하는 개체에 대 한 참조입니다. 이 매개 변수는 NULL이 아니어야 합니다. 보안 설명자에 NULL DACL을 설정 하려면이 메서드의 첫 번째 형태를 false *로 설정 하 여 사용 해야* 합니다.

*bPresent*<br/>
보안 설명자에 DACL이 있는지를 나타내는 플래그를 지정 합니다. 이 매개 변수가 true 이면 메서드는 구조체에 SE_DACL_PRESENT 플래그를 설정 `SECURITY_DESCRIPTOR_CONTROL` 하 고 *DACL* 및 *bdefaulted* 매개 변수의 값을 사용 합니다. False 이면 메서드가 SE_DACL_PRESENT 플래그를 지우고 *Bdefaulted* 은 무시 됩니다.

*bDefaulted*<br/>
DACL의 원본을 나타내는 플래그를 지정 합니다. 이 플래그가 true 이면 DACL이 일부 기본 메커니즘에 의해 검색 된 것입니다. False 이면 사용자가 DACL을 명시적으로 지정 합니다. 메서드는 구조체의 SE_DACL_DEFAULTED 플래그에이 값을 저장 `SECURITY_DESCRIPTOR_CONTROL` 합니다. 이 매개 변수를 지정 하지 않으면 SE_DACL_DEFAULTED 플래그가 지워집니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="remarks"></a>설명

빈 DACL과 존재 하지 않는 DACL 사이에는 중요 한 차이가 있습니다. DACL이 비어 있는 경우 액세스 제어 항목이 포함 되지 않으며 명시적으로 액세스 권한이 부여 되지 않습니다. 따라서 개체에 대 한 액세스가 암시적으로 거부 됩니다. 반면 개체에는 DACL이 없는 경우 개체에 보호가 할당 되지 않으며 모든 액세스 요청이 허용 됩니다.

## <a name="csecuritydescsetgroup"></a><a name="setgroup"></a> CSecurityDesc:: SetGroup

이미 있는 주 그룹 정보를 대체 하 여 절대 형식 보안 설명자의 주 그룹 정보를 설정 합니다.

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>매개 변수

*S*<br/>
보안 설명자의 새 주 그룹에 대 한 [CSid](../../atl/reference/csid-class.md) 개체에 대 한 참조입니다. 이 매개 변수는 NULL이 아니어야 합니다. 보안 설명자는 DACL 또는 SACL을 포함 하지 않는 것으로 표시 될 수 있지만 그룹 및 소유자가 있어야 합니다. 단,이는 NULL SID (특별 한 의미를 가진 기본 제공 SID)입니다.

*bDefaulted*<br/>
기본 그룹 정보가 기본 메커니즘에서 파생 되었는지 여부를 나타냅니다. 이 값이 true 이면 기본 정보이 고, 메서드는 구조체의 SE_GROUP_DEFAULTED 플래그로이 값을 저장 `SECURITY_DESCRIPTOR_CONTROL` 합니다. 이 매개 변수가 0 이면 SE_GROUP_DEFAULTED 플래그가 지워집니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

## <a name="csecuritydescsetowner"></a><a name="setowner"></a> CSecurityDesc:: SetOwner

절대 형식 보안 설명자의 소유자 정보를 설정 합니다. 이미 존재 하는 모든 소유자 정보를 대체 합니다.

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>매개 변수

*S*<br/>
보안 설명자의 새 주 소유자에 대 한 [CSid](../../atl/reference/csid-class.md) 개체입니다. 이 매개 변수는 NULL이 아니어야 합니다.

*bDefaulted*<br/>
소유자 정보가 기본 메커니즘에서 파생 되는지 여부를 나타냅니다. 이 값이 true 이면 기본 정보입니다. 메서드는 구조체에 SE_OWNER_DEFAULTED 플래그로이 값을 저장 `SECURITY_DESCRIPTOR_CONTROL` 합니다. 이 매개 변수가 0 이면 SE_OWNER_DEFAULTED 플래그가 지워집니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

## <a name="csecuritydescsetsacl"></a><a name="setsacl"></a> CSecurityDesc:: SetSacl

SACL (시스템 액세스 제어 목록)에 정보를 설정 합니다. 보안 설명자에 SACL이 이미 있는 경우이를 대체 합니다.

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>매개 변수

*Sacl*<br/>
`CSacl`보안 설명자의 SACL을 지정 하는 개체에 대 한 포인터입니다. 이 매개 변수는 NULL 일 수 없으며 CSacl 개체 여야 합니다. Dacl과 달리 SACL 개체는 액세스 권한을 지정 하지 않고 감사 정보만 지정 하므로 NULL과 빈 SACL 사이에는 차이가 없습니다.

*bDefaulted*<br/>
SACL의 원본을 나타내는 플래그를 지정 합니다. 이 플래그가 true 이면 SACL이 일부 기본 메커니즘에 의해 검색 된 것입니다. False 이면 사용자가 SACL을 명시적으로 지정 합니다. 메서드는 구조체의 SE_SACL_DEFAULTED 플래그에이 값을 저장 `SECURITY_DESCRIPTOR_CONTROL` 합니다. 이 매개 변수를 지정 하지 않으면 SE_SACL_DEFAULTED 플래그가 지워집니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

## <a name="csecuritydesctostring"></a><a name="tostring"></a> CSecurityDesc:: ToString

보안 설명자를 문자열 형식으로 변환 합니다.

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pstr*<br/>
[문자열 형식 보안 설명자](/windows/win32/SecAuthZ/security-descriptor-string-format)를 수신 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*si*<br/>
출력 문자열에 포함할 보안 설명자의 구성 요소를 나타내는 SECURITY_INFORMATION 비트 플래그의 조합을 지정 합니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="remarks"></a>설명

보안 설명자가 문자열 형식인 경우 더 쉽게 저장 하거나 전송할 수 있습니다. 메서드를 사용 `CSecurityDesc::FromString` 하 여 문자열을 다시 보안 설명자로 변환 합니다.

*Si* 매개 변수는 다음 SECURITY_INFORMATION 플래그를 포함할 수 있습니다.

|값|의미|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|소유자를 포함 합니다.|
|GROUP_SECURITY_INFORMATION|주 그룹을 포함 합니다.|
|DACL_SECURITY_INFORMATION|DACL을 포함 합니다.|
|SACL_SECURITY_INFORMATION|SACL을 포함 합니다.|

DACL이 NULL이 고 SE_DACL_PRESENT 컨트롤 비트가 입력 보안 설명자에 설정 된 경우 메서드는 실패 합니다.

DACL이 NULL이 고 SE_DACL_PRESENT 컨트롤 비트가 입력 보안 설명자에 설정 되어 있지 않으면 결과 보안 설명자 문자열에 D: 구성 요소가 없습니다. 자세한 내용은 [보안 설명자 문자열 형식](/windows/win32/SecAuthZ/security-descriptor-string-format) 을 참조 하세요.

이 메서드는 [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)을 호출 합니다.

## <a name="see-also"></a>참고 항목

[보안 샘플](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[보안 전역 함수](../../atl/reference/security-global-functions.md)
