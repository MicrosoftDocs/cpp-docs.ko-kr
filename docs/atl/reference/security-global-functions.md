---
title: 보안 전역 함수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 053e7adb5a0f5d6c65f599ae694525853bd221a7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211793"
---
# <a name="security-global-functions"></a>보안 전역 함수
이러한 함수는 SID 및 ACL 개체를 수정 하기 위한 지원을 제공 합니다.  
  
> [!IMPORTANT]
>  다음 표에 나열 된 함수를 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
|||  
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
 **헤더:** atlsecurity.h 

##  <a name="atlgetdacl"></a>  AtlGetDacl  
 지정된 개체의 DACL(임의 액세스 제어 목록) 정보를 검색하려면 이 함수를 호출합니다.  
  
> [!IMPORTANT]
>  이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```  
  
### <a name="parameters"></a>매개 변수  
 *hObject*  
 보안 정보를 검색 하는 개체에 대 한 핸들입니다.  
  
 *ObjectType*  
 값을 지정 합니다 [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) 식별 되는 개체의 형식을 나타내는 열거형입니다 합니다 *hObject* 매개 변수입니다.  
  
 *pDacl*  
 검색된 된 보안 정보를 포함 하는 DACL 개체에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 true를 반환하고, 실패하면 false를 반환합니다.  
  
### <a name="remarks"></a>설명  
 디버그 빌드에서 경우 어설션 오류가 발생 합니다 *hObject* 하거나 *pDacl* 올바르지 않습니다.  
  
##  <a name="atlsetdacl"></a>  AtlSetDacl  
 지정된 개체의 DACL(임의 액세스 제어 목록) 정보를 설정하려면 이 함수를 호출합니다.  
  
> [!IMPORTANT]
>  이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 *hObject*  
 보안 정보를 설정 하는 개체에 대 한 핸들입니다.  
  
 *ObjectType*  
 값을 지정 합니다 [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) 식별 되는 개체의 형식을 나타내는 열거형입니다 합니다 *hObject* 매개 변수입니다.  
  
 *rDacl*  
 새 보안 정보를 포함 하는 DACL입니다.  
  
 *dwInheritanceFlowControl*  
 상속 흐름 제어 합니다. 이 값은 0 (기본값), PROTECTED_DACL_SECURITY_INFORMATION 또는 UNPROTECTED_DACL_SECURITY_INFORMATION 수 있습니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 true를 반환하고, 실패하면 false를 반환합니다.  
  
### <a name="remarks"></a>설명  
 디버그 빌드에서 어설션 오류가 발생 하는 경우 *hObject* 유효 하지 않은 경우 *dwInheritanceFlowControl* 허용 되는 세 가지 값 중 하나가 아닙니다.  
### <a name="requirements"></a>요구 사항  
 **헤더:** atlsecurity.h 

##  <a name="atlgetgroupsid"></a>  AtlGetGroupSid  
 개체의 그룹 보안 식별자(SID)를 검색하려면 이 함수를 호출합니다.  
  
> [!IMPORTANT]
>  이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 *hObject*  
 보안 정보를 검색 하는 개체에 대 한 핸들입니다.  
  
 *ObjectType*  
 값을 지정 합니다 [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) 식별 되는 개체의 형식을 나타내는 열거형입니다 합니다 *hObject* 매개 변수입니다.  
  
 *pSid*  
 에 대 한 포인터를 `CSid` 개체는 새 보안 정보가 포함 됩니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 true를 반환하고, 실패하면 false를 반환합니다.  

### <a name="requirements"></a>요구 사항  
 **헤더:** atlsecurity.h 

##  <a name="atlsetgroupsid"></a>  AtlSetGroupSid  
 개체의 그룹 보안 식별자(SID)를 설정하려면 이 함수를 호출합니다.  
  
> [!IMPORTANT]
>  이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 *hObject*  
 보안 정보를 설정 하는 개체에 대 한 핸들입니다.  
  
 *ObjectType*  
 값을 지정 합니다 [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) 식별 되는 개체의 형식을 나타내는 열거형입니다 합니다 *hObject* 매개 변수입니다.  
  
 *rSid*  
 `CSid` 새 보안 정보를 포함 하는 개체입니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 true를 반환하고, 실패하면 false를 반환합니다.  

### <a name="requirements"></a>요구 사항  
 **헤더:** atlsecurity.h 

##  <a name="atlgetownersid"></a>  AtlGetOwnerSid  
 개체의 소유자 보안 식별자(SID)를 검색하려면 이 함수를 호출합니다.  
  
> [!IMPORTANT]
>  이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 *hObject*  
 보안 정보를 검색 하는 개체에 대 한 핸들입니다.  
  
 *ObjectType*  
 값을 지정 합니다 [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) 식별 되는 개체의 형식을 나타내는 열거형입니다 합니다 *hObject* 매개 변수입니다.  
  
 *pSid*  
 에 대 한 포인터를 `CSid` 개체는 새 보안 정보가 포함 됩니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 true를 반환하고, 실패하면 false를 반환합니다.  

### <a name="requirements"></a>요구 사항  
 **헤더:** atlsecurity.h 

##  <a name="atlsetownersid"></a>  AtlSetOwnerSid  
 개체의 소유자 보안 식별자(SID)를 설정하려면 이 함수를 호출합니다.  
  
> [!IMPORTANT]
>  이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 *hObject*  
 보안 정보를 설정 하는 개체에 대 한 핸들입니다.  
  
 *ObjectType*  
 값을 지정 합니다 [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) 식별 되는 개체의 형식을 나타내는 열거형입니다 합니다 *hObject* 매개 변수입니다.  
  
 *rSid*  
 `CSid` 새 보안 정보를 포함 하는 개체입니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 true를 반환하고, 실패하면 false를 반환합니다.  

### <a name="requirements"></a>요구 사항  
 **헤더:** atlsecurity.h 

##  <a name="atlgetsacl"></a>  AtlGetSacl  
 지정된 개체의 SACL(시스템 액세스 제어 목록) 정보를 검색하려면 이 함수를 호출합니다.  
  
> [!IMPORTANT]
>  이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 *hObject*  
 보안 정보를 검색 하는 개체에 대 한 핸들입니다.  
  
 *ObjectType*  
 값을 지정 합니다 [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) 식별 되는 개체의 형식을 나타내는 열거형입니다 합니다 *hObject* 매개 변수입니다.  
  
 *pSacl*  
 검색된 된 보안 정보를 포함할 SACL 개체에 대 한 포인터입니다.  
  
 *bRequestNeededPrivileges*  
 True 이면 함수는 SE_SECURITY_NAME 권한을 설정 하 고 완료 되 면 복원 하려고 합니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 true를 반환하고, 실패하면 false를 반환합니다.  
  
### <a name="remarks"></a>설명  
 하는 경우 `AtlGetSacl` 많은 다른 개체를 여러 번 호출 되는 것은 SE_SECURITY_NAME 사용 하 여 함수를 호출 하기 전에 한 번 설정 하는 것이 효율적 *bRequestNeededPrivileges* false로 설정 합니다.  

### <a name="requirements"></a>요구 사항  
 **헤더:** atlsecurity.h 

##  <a name="atlsetsacl"></a>  AtlSetSacl  
 지정된 개체의 SACL(시스템 액세스 제어 목록) 정보를 설정하려면 이 함수를 호출합니다.  
  
> [!IMPORTANT]
>  이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 *hObject*  
 보안 정보를 설정 하는 개체에 대 한 핸들입니다.  
  
 *ObjectType*  
 값을 지정 합니다 [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) 식별 되는 개체의 형식을 나타내는 열거형입니다 합니다 *hObject* 매개 변수입니다.  
  
 *rSacl*  
 새 보안 정보를 포함 하는 SACL입니다.  
  
 *dwInheritanceFlowControl*  
 상속 흐름 제어 합니다. 이 값은 0 (기본값), PROTECTED_SACL_SECURITY_INFORMATION 또는 UNPROTECTED_SACL_SECURITY_INFORMATION 수 있습니다.  
  
 *bRequestNeededPrivileges*  
 True 이면 함수는 SE_SECURITY_NAME 권한을 설정 하 고 완료 되 면 복원 하려고 합니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 true를 반환하고, 실패하면 false를 반환합니다.  
  
### <a name="remarks"></a>설명  
 디버그 빌드에서 어설션 오류가 발생 하는 경우 *hObject* 유효 하지 않은 경우 *dwInheritanceFlowControl* 허용 되는 세 가지 값 중 하나가 아닙니다.  
  
 하는 경우 `AtlSetSacl` 많은 다른 개체를 여러 번 호출 되는 것은 SE_SECURITY_NAME 사용 하 여 함수를 호출 하기 전에 한 번 설정 하는 것이 효율적 *bRequestNeededPrivileges* false로 설정 합니다.  

### <a name="requirements"></a>요구 사항  
 **헤더:** atlsecurity.h 

##  <a name="atlgetsecuritydescriptor"></a>  AtlGetSecurityDescriptor  
 지정된 개체의 보안 설명자를 검색하려면 이 함수를 호출합니다.  
  
> [!IMPORTANT]
>  이 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
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
 *pszObjectName*  
 보안 정보를 검색할 개체의 이름을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다.  
  
 *ObjectType*  
 값을 지정 합니다 [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) 식별 되는 개체의 형식을 나타내는 열거형입니다 합니다 *pszObjectName* 매개 변수입니다.  
  
 *pSecurityDescriptor*  
 요청 된 보안 설명자를 수신 하는 개체입니다.  
  
 *requestedInfo*  
 집합이 [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) 비트 보안 정보를 검색 하 형식을 나타내는 플래그입니다. 이 매개 변수는 다음 값의 조합일 수 있습니다.  
  
 *bRequestNeededPrivileges*  
 True 이면 함수는 SE_SECURITY_NAME 권한을 설정 하 고 완료 되 면 복원 하려고 합니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 true를 반환하고, 실패하면 false를 반환합니다.  
  
### <a name="remarks"></a>설명  
 하는 경우 `AtlGetSecurityDescriptor` 많은 다른 개체를 여러 번 호출 되는 것은 SE_SECURITY_NAME 사용 하 여 함수를 호출 하기 전에 한 번 설정 하는 것이 효율적 *bRequestNeededPrivileges* false로 설정 합니다.  

### <a name="requirements"></a>요구 사항  
 **헤더:** atlsecurity.h 
   
## <a name="see-also"></a>참고 항목  
 [함수](../../atl/reference/atl-functions.md)
