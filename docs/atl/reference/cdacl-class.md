---
description: '다음에 대 한 자세한 정보: CDacl 클래스'
title: CDacl 클래스
ms.date: 11/04/2016
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
ms.openlocfilehash: 0f071cbf426fe9cf89752defa19ff7f212e142d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142001"
---
# <a name="cdacl-class"></a>CDacl 클래스

이 클래스는 DACL (임의 액세스 제어 목록) 구조체에 대 한 래퍼입니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CDacl : public CAcl
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDacl:: CDacl](#cdacl)|생성자입니다.|
|[CDacl:: ~ CDacl](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDacl:: AddAllowedAce](#addallowedace)|개체에 허용 된 ACE (액세스 제어 항목)를 추가 `CDacl` 합니다.|
|[CDacl:: AddDeniedAce](#adddeniedace)|거부 된 ACE를 개체에 추가 `CDacl` 합니다.|
|[CDacl:: GetAceCount](#getacecount)|개체의 Ace (액세스 제어 항목) 수를 반환 합니다 `CDacl` .|
|[CDacl:: RemoveAce](#removeace)|개체에서 특정 ACE (액세스 제어 항목)를 제거 합니다 `CDacl` .|
|[CDacl:: RemoveAllAces](#removeallaces)|개체에 포함 된 모든 Ace를 제거 합니다 `CDacl` .|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CDacl:: operator =](#operator_eq)|대입 연산자입니다.|

## <a name="remarks"></a>설명

개체의 보안 설명자에는 DACL이 포함 될 수 있습니다. DACL에는 개체에 액세스할 수 있는 사용자 및 그룹을 식별 하는 Ace (액세스 제어 항목)가 0 개 이상 포함 되어 있습니다. DACL이 비어 있는 경우 (즉, Ace에 0이 포함 된 경우) 액세스 권한이 명시적으로 부여 되지 않으므로 액세스가 암시적으로 거부 됩니다. 그러나 개체의 보안 설명자에 DACL이 없는 경우 개체는 보호 되지 않으며 모든 사용자에 게는 완전 한 액세스 권한이 있습니다.

개체의 DACL을 검색 하려면 개체의 소유자 이거나 개체에 대 한 READ_CONTROL 액세스 권한이 있어야 합니다. 개체의 DACL을 변경 하려면 개체에 대 한 WRITE_DAC 액세스 권한이 있어야 합니다.

제공 된 클래스 메서드를 사용 하 여 개체에서 Ace를 만들고 추가, 제거 및 삭제할 수 `CDacl` 있습니다. 또한, [Atlgetdacl](security-global-functions.md#atlgetdacl) 및 [atlsetdacl](security-global-functions.md#atlsetdacl)을 참조 하세요.

Windows의 액세스 제어 모델에 대 한 소개는 Windows SDK [Access Control](/windows/win32/SecAuthZ/access-control) 를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="cdacladdallowedace"></a><a name="addallowedace"></a> CDacl:: AddAllowedAce

개체에 허용 된 ACE (액세스 제어 항목)를 추가 `CDacl` 합니다.

```
bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>매개 변수

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md) 개체입니다.

*AccessMask*<br/>
지정 된 개체에 대해 허용 되는 액세스 권한의 마스크를 지정 합니다 `CSid` .

*AceFlags*<br/>
ACE 상속을 제어 하는 비트 플래그 집합입니다.

*pObjectType*<br/>
개체 형식입니다.

*pInheritedObjectType*<br/>
상속 된 개체 유형입니다.

### <a name="return-value"></a>반환 값

ACE가 개체에 추가 되 면 TRUE `CDacl` 를 반환 하 고, 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

개체에는 `CDacl` 개체에 액세스할 수 있는 사용자 및 그룹을 식별 하는 ace (액세스 제어 항목)가 0 개 이상 포함 되어 있습니다. 이 메서드는 개체에 대 한 액세스를 허용 하는 ACE를 추가 `CDacl` 합니다.

매개 변수에 설정할 수 있는 다양 한 플래그에 대 한 설명은 [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) 를 참조 하세요 `AceFlags` .

## <a name="cdacladddeniedace"></a><a name="adddeniedace"></a> CDacl:: AddDeniedAce

거부 된 ACE (액세스 제어 항목)를 개체에 추가 `CDacl` 합니다.

```
bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>매개 변수

*rSid*<br/>
`CSid` 개체입니다.

*AccessMask*<br/>
지정 된 개체에 대해 거부할 액세스 권한의 마스크를 지정 합니다 `CSid` .

*AceFlags*<br/>
ACE 상속을 제어 하는 비트 플래그 집합입니다. 메서드의 첫 번째 폼에서 기본값은 0입니다.

*pObjectType*<br/>
개체 형식입니다.

*pInheritedObjectType*<br/>
상속 된 개체 유형입니다.

### <a name="return-value"></a>반환 값

ACE가 개체에 추가 되 면 TRUE `CDacl` 를 반환 하 고, 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

개체에는 `CDacl` 개체에 액세스할 수 있는 사용자 및 그룹을 식별 하는 ace (액세스 제어 항목)가 0 개 이상 포함 되어 있습니다. 이 메서드는 개체에 대 한 액세스를 거부 하는 ACE를 추가 `CDacl` 합니다.

매개 변수에 설정할 수 있는 다양 한 플래그에 대 한 설명은 [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) 를 참조 하세요 `AceFlags` .

## <a name="cdaclcdacl"></a><a name="cdacl"></a> CDacl:: CDacl

생성자입니다.

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>매개 변수

*rhs*<br/>
기존 `ACL` (액세스 제어 목록) 구조입니다.

### <a name="remarks"></a>설명

`CDacl`필요에 따라 기존 구조를 사용 하 여 개체를 만들 수 있습니다 `ACL` . SACL (시스템 액세스 제어 목록)이 아닌 DACL (임의 액세스 제어 목록)만이 매개 변수로 전달 되어야 합니다. 디버그 빌드에서 SACL을 전달 하면 어설션이 발생 합니다. 릴리스 빌드에서 SACL을 전달 하면 ACL의 Ace (액세스 제어 항목)가 무시 되 고 오류가 발생 하지 않습니다.

## <a name="cdaclcdacl"></a><a name="dtor"></a> CDacl:: ~ CDacl

소멸자입니다.

```
~CDacl () throw();
```

### <a name="remarks"></a>설명

소멸자는 [Cdacl:: RemoveAllAces](#removeallaces)를 사용 하 여 모든 ace (액세스 제어 항목)를 비롯 하 여 개체에서 획득 한 모든 리소스를 해제 합니다.

## <a name="cdaclgetacecount"></a><a name="getacecount"></a> CDacl:: GetAceCount

개체의 Ace (액세스 제어 항목) 수를 반환 합니다 `CDacl` .

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>반환 값

개체에 포함 된 Ace의 수를 반환 합니다 `CDacl` .

## <a name="cdacloperator-"></a><a name="operator_eq"></a> CDacl:: operator =

대입 연산자입니다.

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>매개 변수

*rhs*<br/>
기존 개체에 할당할 ACL (액세스 제어 목록)입니다.

### <a name="return-value"></a>반환 값

업데이트 된 개체에 대 한 참조를 반환 `CDacl` 합니다.

### <a name="remarks"></a>설명

이 함수에는 DACL (임의 액세스 제어 목록)만 전달 해야 합니다. SACL (시스템 액세스 제어 목록)을이 함수에 전달 하면 디버그 빌드에서 어설션이 발생 하지만 릴리스 빌드에서 오류가 발생 하지 않습니다.

## <a name="cdaclremoveace"></a><a name="removeace"></a> CDacl:: RemoveAce

개체에서 특정 ACE (액세스 제어 항목)를 제거 합니다 `CDacl` .

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
제거할 ACE 항목의 인덱스입니다.

### <a name="remarks"></a>설명

이 메서드는 [CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat)에서 파생 됩니다.

## <a name="cdaclremoveallaces"></a><a name="removeallaces"></a> CDacl:: RemoveAllAces

개체에 포함 된 모든 Ace (액세스 제어 항목)를 제거 합니다 `CDacl` .

```cpp
void RemoveAllAces() throw();
```

### <a name="remarks"></a>설명

`ACE`개체의 모든 (액세스 제어 항목) 구조 (있는 경우)를 제거 `CDacl` 합니다.

## <a name="see-also"></a>참고 항목

[보안 샘플](../../overview/visual-cpp-samples.md)<br/>
[CAcl 클래스](../../atl/reference/cacl-class.md)<br/>
[ACL](/windows/win32/SecAuthZ/access-control-lists)<br/>
[에이스](/windows/win32/SecAuthZ/access-control-entries)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[보안 전역 함수](../../atl/reference/security-global-functions.md)
