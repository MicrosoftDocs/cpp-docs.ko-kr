---
description: '자세히 알아보기: 보안 전역 함수'
title: 보안 전역 함수
ms.date: 11/04/2016
f1_keywords:
- atlsecurity/ATL::AtlGetDacl
- atlsecurity/ATL::AtlSetDacl
- atlsecurity/ATL::AtlGetGroupSid
- atlsecurity/ATL::AtlSetGroupSid
- atlsecurity/ATL::AtlGetOwnerSid
- atlsecurity/ATL::AtlSetOwnerSid
- atlsecurity/ATL::AtlGetSacl
- atlsecurity/ATL::AtlSetSacl
- atlsecurity/ATL::AtlGetSecurityDescriptor
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
ms.openlocfilehash: 10a3a3f358eba3aa1715bd375221f6ec35a56fcf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157791"
---
# <a name="security-global-functions"></a>보안 전역 함수

이러한 함수는 SID 및 ACL 개체를 수정 하는 기능을 제공 합니다.

> [!IMPORTANT]
> 다음 표에 나열 된 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

|Name|설명|
|-|-|
|[AtlGetDacl](#atlgetdacl)|지정된 개체의 DACL(임의 액세스 제어 목록) 정보를 검색하려면 이 함수를 호출합니다.|
|[AtlSetDacl](#atlsetdacl)|지정된 개체의 DACL(임의 액세스 제어 목록) 정보를 설정하려면 이 함수를 호출합니다.|
|[AtlGetGroupSid](#atlgetgroupsid)|개체의 그룹 보안 식별자(SID)를 검색하려면 이 함수를 호출합니다.|
|[AtlSetGroupSid](#atlsetgroupsid)|개체의 그룹 보안 식별자(SID)를 설정하려면 이 함수를 호출합니다.|
|[AtlGetOwnerSid](#atlgetownersid)|개체의 소유자 보안 식별자(SID)를 검색하려면 이 함수를 호출합니다.|
|[AtlSetOwnerSid](#atlsetownersid)|개체의 소유자 보안 식별자(SID)를 설정하려면 이 함수를 호출합니다.|
|[AtlGetSacl](#atlgetsacl)|지정된 개체의 SACL(시스템 액세스 제어 목록) 정보를 검색하려면 이 함수를 호출합니다.|
|[AtlSetSacl](#atlsetsacl)|지정된 개체의 SACL(시스템 액세스 제어 목록) 정보를 설정하려면 이 함수를 호출합니다.|
|[AtlGetSecurityDescriptor](#atlgetsecuritydescriptor)|지정된 개체의 보안 설명자를 검색하려면 이 함수를 호출합니다.|

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="atlgetdacl"></a><a name="atlgetdacl"></a> 서-Getdacl

지정된 개체의 DACL(임의 액세스 제어 목록) 정보를 검색하려면 이 함수를 호출합니다.

> [!IMPORTANT]
> 이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>매개 변수

*hObject*<br/>
보안 정보를 검색할 개체에 대 한 핸들입니다.

*ObjectType*<br/>
*Hobject* 매개 변수로 식별 되는 개체 유형을 나타내는 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 열거형의 값을 지정 합니다.

*Pdce Acl*<br/>
검색 된 보안 정보를 포함 하는 DACL 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="remarks"></a>설명

디버그 빌드에서는 *Hobject* 또는 *pdce acl* 이 잘못 된 경우 어설션 오류가 발생 합니다.

## <a name="atlsetdacl"></a><a name="atlsetdacl"></a> AtlSetDacl

지정된 개체의 DACL(임의 액세스 제어 목록) 정보를 설정하려면 이 함수를 호출합니다.

> [!IMPORTANT]
> 이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>매개 변수

*hObject*<br/>
보안 정보를 설정 하는 개체에 대 한 핸들입니다.

*ObjectType*<br/>
*Hobject* 매개 변수로 식별 되는 개체 유형을 나타내는 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 열거형의 값을 지정 합니다.

*rDacl*<br/>
새 보안 정보를 포함 하는 DACL입니다.

*dwInheritanceFlowControl*<br/>
상속 흐름 제어입니다. 이 값은 0 (기본값), PROTECTED_DACL_SECURITY_INFORMATION 또는 UNPROTECTED_DACL_SECURITY_INFORMATION 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="remarks"></a>설명

디버그 빌드에서는 *Hobject* 가 잘못 되었거나 *dwInheritanceFlowControl* 가 허용 되는 세 값 중 하나가 아닌 경우 어설션 오류가 발생 합니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="atlgetgroupsid"></a><a name="atlgetgroupsid"></a> AtlGetGroupSid

개체의 그룹 보안 식별자(SID)를 검색하려면 이 함수를 호출합니다.

> [!IMPORTANT]
> 이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>매개 변수

*hObject*<br/>
보안 정보를 검색할 개체에 대 한 핸들입니다.

*ObjectType*<br/>
*Hobject* 매개 변수로 식별 되는 개체 유형을 나타내는 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 열거형의 값을 지정 합니다.

*pSid*<br/>
새 보안 정보를 포함 하는 개체에 대 한 포인터 `CSid` 입니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="atlsetgroupsid"></a><a name="atlsetgroupsid"></a> AtlSetGroupSid

개체의 그룹 보안 식별자(SID)를 설정하려면 이 함수를 호출합니다.

> [!IMPORTANT]
> 이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>매개 변수

*hObject*<br/>
보안 정보를 설정 하는 개체에 대 한 핸들입니다.

*ObjectType*<br/>
*Hobject* 매개 변수로 식별 되는 개체 유형을 나타내는 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 열거형의 값을 지정 합니다.

*rSid*<br/>
`CSid`새 보안 정보를 포함 하는 개체입니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="atlgetownersid"></a><a name="atlgetownersid"></a> 는이 Sid

개체의 소유자 보안 식별자(SID)를 검색하려면 이 함수를 호출합니다.

> [!IMPORTANT]
> 이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>매개 변수

*hObject*<br/>
보안 정보를 검색할 개체에 대 한 핸들입니다.

*ObjectType*<br/>
*Hobject* 매개 변수로 식별 되는 개체 유형을 나타내는 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 열거형의 값을 지정 합니다.

*pSid*<br/>
새 보안 정보를 포함 하는 개체에 대 한 포인터 `CSid` 입니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="atlsetownersid"></a><a name="atlsetownersid"></a> AtlSetOwnerSid

개체의 소유자 보안 식별자(SID)를 설정하려면 이 함수를 호출합니다.

> [!IMPORTANT]
> 이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>매개 변수

*hObject*<br/>
보안 정보를 설정 하는 개체에 대 한 핸들입니다.

*ObjectType*<br/>
*Hobject* 매개 변수로 식별 되는 개체 유형을 나타내는 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 열거형의 값을 지정 합니다.

*rSid*<br/>
`CSid`새 보안 정보를 포함 하는 개체입니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="atlgetsacl"></a><a name="atlgetsacl"></a> Atl

지정된 개체의 SACL(시스템 액세스 제어 목록) 정보를 검색하려면 이 함수를 호출합니다.

> [!IMPORTANT]
> 이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>매개 변수

*hObject*<br/>
보안 정보를 검색할 개체에 대 한 핸들입니다.

*ObjectType*<br/>
*Hobject* 매개 변수로 식별 되는 개체 유형을 나타내는 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 열거형의 값을 지정 합니다.

*pSacl*<br/>
검색 된 보안 정보를 포함 하는 SACL 개체에 대 한 포인터입니다.

*Brequestnee이상 권한*<br/>
True 이면 함수가 SE_SECURITY_NAME 권한을 사용 하도록 설정 하 고 완료 될 때 복원 합니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="remarks"></a>설명

여러 `AtlGetSacl` 개체에서를 여러 번 호출 하는 경우에는 *Brequestneededprivileges* false로 설정 된 상태에서 함수를 호출 하기 전에 SE_SECURITY_NAME 권한을 한 번 사용 하도록 설정 하는 것이 더 효율적입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="atlsetsacl"></a><a name="atlsetsacl"></a> AtlSetSacl

지정된 개체의 SACL(시스템 액세스 제어 목록) 정보를 설정하려면 이 함수를 호출합니다.

> [!IMPORTANT]
> 이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>매개 변수

*hObject*<br/>
보안 정보를 설정 하는 개체에 대 한 핸들입니다.

*ObjectType*<br/>
*Hobject* 매개 변수로 식별 되는 개체 유형을 나타내는 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 열거형의 값을 지정 합니다.

*rSacl*<br/>
새 보안 정보를 포함 하는 SACL입니다.

*dwInheritanceFlowControl*<br/>
상속 흐름 제어입니다. 이 값은 0 (기본값), PROTECTED_SACL_SECURITY_INFORMATION 또는 UNPROTECTED_SACL_SECURITY_INFORMATION 수 있습니다.

*Brequestnee이상 권한*<br/>
True 이면 함수가 SE_SECURITY_NAME 권한을 사용 하도록 설정 하 고 완료 될 때 복원 합니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="remarks"></a>설명

디버그 빌드에서는 *Hobject* 가 잘못 되었거나 *dwInheritanceFlowControl* 가 허용 되는 세 값 중 하나가 아닌 경우 어설션 오류가 발생 합니다.

여러 `AtlSetSacl` 개체에서를 여러 번 호출 하는 경우에는 *Brequestneededprivileges* false로 설정 된 상태에서 함수를 호출 하기 전에 SE_SECURITY_NAME 권한을 한 번 사용 하도록 설정 하는 것이 더 효율적입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="atlgetsecuritydescriptor"></a><a name="atlgetsecuritydescriptor"></a> AtlGetSecurityDescriptor

지정된 개체의 보안 설명자를 검색하려면 이 함수를 호출합니다.

> [!IMPORTANT]
> 이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```
inline bool AtlGetSecurityDescriptor(
    LPCTSTR pszObjectName,
    SE_OBJECT_TYPE ObjectType,
    CSecurityDesc* pSecurityDescriptor,
    SECURITY_INFORMATION requestedInfo = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION,
bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>매개 변수

*pszObjectName*<br/>
보안 정보를 검색할 개체의 이름을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*ObjectType*<br/>
*PszObjectName* 매개 변수로 식별 되는 개체의 형식을 나타내는 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 열거형의 값을 지정 합니다.

*pSecurityDescriptor*<br/>
요청 된 보안 설명자를 수신 하는 개체입니다.

*requestedInfo*<br/>
검색할 보안 정보의 형식을 나타내는 [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) 비트 플래그 집합입니다. 이 매개 변수는 다음 값을 조합 하 여 사용할 수 있습니다.

*Brequestnee이상 권한*<br/>
True 이면 함수가 SE_SECURITY_NAME 권한을 사용 하도록 설정 하 고 완료 될 때 복원 합니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="remarks"></a>설명

여러 `AtlGetSecurityDescriptor` 개체에서를 여러 번 호출 하는 경우에는 *Brequestneededprivileges* false로 설정 된 상태에서 함수를 호출 하기 전에 SE_SECURITY_NAME 권한을 한 번 사용 하도록 설정 하는 것이 더 효율적입니다.

### <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="see-also"></a>참조

[함수](../../atl/reference/atl-functions.md)
