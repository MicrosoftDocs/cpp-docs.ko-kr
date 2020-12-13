---
description: '자세히 알아보기: CPrivateObjectSecurityDesc 클래스'
title: CPrivateObjectSecurityDesc 클래스
ms.date: 11/04/2016
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
ms.openlocfilehash: 339105d2a6356150c7a7ce8ccf04bc17d3df4911
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141065"
---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc 클래스

이 클래스는 private 개체 보안 설명자 개체를 나타냅니다.

## <a name="syntax"></a>구문

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|생성자입니다.|
|[CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|이 메서드를 호출 하 여 보안 설명자와 해당 Acl (액세스 제어 목록)을 상속 가능한 Ace (액세스 제어 항목)의 자동 전파를 지 원하는 형식으로 변환 합니다.|
|[CPrivateObjectSecurityDesc:: Create](#create)|호출 하는 리소스 관리자가 만든 전용 개체에 대해 자체 상대 보안 설명자를 할당 하 고 초기화 하려면이 메서드를 호출 합니다.|
|[CPrivateObjectSecurityDesc:: Get](#get)|Private 개체의 보안 설명자에서 정보를 검색 하려면이 메서드를 호출 합니다.|
|[CPrivateObjectSecurityDesc:: Set](#set)|Private 개체의 보안 설명자를 수정 하려면이 메서드를 호출 합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자 =](#operator_eq)|대입 연산자입니다.|

## <a name="remarks"></a>설명

[Csecuritydesc](../../atl/reference/csecuritydesc-class.md)에서 파생 된이 클래스는 전용 개체의 보안 설명자를 만들고 관리 하기 위한 메서드를 제공 합니다.

Windows의 액세스 제어 모델에 대 한 소개는 Windows SDK [Access Control](/windows/win32/SecAuthZ/access-control) 를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="cprivateobjectsecuritydescconverttoautoinherit"></a><a name="converttoautoinherit"></a> CPrivateObjectSecurityDesc::ConvertToAutoInherit

이 메서드를 호출 하 여 보안 설명자와 해당 Acl (액세스 제어 목록)을 상속 가능한 Ace (액세스 제어 항목)의 자동 전파를 지 원하는 형식으로 변환 합니다.

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>매개 변수

*pParent*<br/>
개체의 부모 컨테이너를 참조 하는 [Csecuritydesc](../../atl/reference/csecuritydesc-class.md) 개체에 대 한 포인터입니다. 부모 컨테이너가 없으면이 매개 변수는 NULL입니다.

*ObjectType*<br/>
`GUID`현재 개체와 연결 된 개체의 형식을 식별 하는 구조체에 대 한 포인터입니다. 개체에 GUID가 없는 경우 *ObjectType* 을 NULL로 설정 합니다.

*bIsDirectoryObject*<br/>
새 개체가 다른 개체를 포함할 수 있는지 여부를 지정 합니다. True 값은 새 개체가 컨테이너 임을 나타냅니다. False 값은 새 개체가 컨테이너가 아님을 나타냅니다.

*GenericMapping*<br/>
각 제네릭 오른쪽에서 개체에 대 한 특정 권한으로의 매핑을 지정 하는 [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="remarks"></a>설명

이 메서드는 현재 보안 설명자의 DACL (임의 액세스 제어 목록) 및 SACL (시스템 액세스 제어 목록)에 있는 Ace가 부모 보안 설명자에서 상속 되었는지 여부를 확인 하려고 합니다. [ConvertToAutoInheritPrivateObjectSecurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity) 함수를 호출 합니다.

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="cprivateobjectsecuritydesc"></a> CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

생성자입니다.

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>설명

초기화는 `CPrivateObjectSecurityDesc` 개체입니다.

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="dtor"></a> CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc

소멸자입니다.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>설명

소멸자는 할당 된 모든 리소스를 해제 하 고 전용 개체의 보안 설명자를 삭제 합니다.

## <a name="cprivateobjectsecuritydesccreate"></a><a name="create"></a> CPrivateObjectSecurityDesc:: Create

호출 하는 리소스 관리자가 만든 전용 개체에 대해 자체 상대 보안 설명자를 할당 하 고 초기화 하려면이 메서드를 호출 합니다.

```
bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>매개 변수

*pParent*<br/>
새 개체를 만드는 부모 디렉터리를 참조 하는 [Csecuritydesc](../../atl/reference/csecuritydesc-class.md) 개체에 대 한 포인터입니다. 부모 디렉터리가 없으면 NULL로 설정 합니다.

*pCreator*<br/>
개체 작성자가 제공 하는 보안 설명자에 대 한 포인터입니다. 개체의 작성자가 새 개체에 대 한 보안 정보를 명시적으로 전달 하지 않는 경우이 매개 변수를 NULL로 설정 합니다.

*bIsDirectoryObject*<br/>
새 개체가 다른 개체를 포함할 수 있는지 여부를 지정 합니다. True 값은 새 개체가 컨테이너 임을 나타냅니다. False 값은 새 개체가 컨테이너가 아님을 나타냅니다.

*토큰*<br/>
개체를 만들고 있는 클라이언트 프로세스에 대 한 [CAccessToken](../../atl/reference/caccesstoken-class.md) 개체에 대 한 참조입니다.

*GenericMapping*<br/>
각 제네릭 오른쪽에서 개체에 대 한 특정 권한으로의 매핑을 지정 하는 [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) 구조체에 대 한 포인터입니다.

*ObjectType*<br/>
`GUID`현재 개체와 연결 된 개체의 형식을 식별 하는 구조체에 대 한 포인터입니다. 개체에 GUID가 없는 경우 *ObjectType* 을 NULL로 설정 합니다.

*bIsContainerObject*<br/>
새 개체가 다른 개체를 포함할 수 있는지 여부를 지정 합니다. True 값은 새 개체가 컨테이너 임을 나타냅니다. False 값은 새 개체가 컨테이너가 아님을 나타냅니다.

*AutoInheritFlags*<br/>
Ace (액세스 제어 항목)가 *Pparent* 에서 상속 되는 방식을 제어 하는 비트 플래그 집합입니다. 자세한 내용은 [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) 를 참조 하세요.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="remarks"></a>설명

이 메서드는 [CreatePrivateObjectSercurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) 또는 [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)를 호출 합니다.

두 번째 방법을 사용 하 여 새 개체의 개체 형식 GUID를 지정 하거나 Ace 상속 방식을 제어할 수 있습니다.

> [!NOTE]
> 자체 상대 보안 설명자는 인접 한 메모리 블록에 모든 보안 정보를 저장 하는 보안 설명자입니다.

## <a name="cprivateobjectsecuritydescget"></a><a name="get"></a> CPrivateObjectSecurityDesc:: Get

Private 개체의 보안 설명자에서 정보를 검색 하려면이 메서드를 호출 합니다.

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>매개 변수

*si*<br/>
검색할 보안 설명자의 파트를 나타내는 비트 플래그 집합입니다. 이 값은 [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) 비트 플래그의 조합일 수 있습니다.

*pResult*<br/>
지정 된 보안 설명자에서 요청 된 정보의 복사본을 받는 [Csecuritydesc](../../atl/reference/csecuritydesc-class.md) 개체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="remarks"></a>설명

보안 설명자는 보안 개체에 대 한 보안 정보를 포함 하는 구조 및 연결 된 데이터입니다.

## <a name="cprivateobjectsecuritydescoperator-"></a><a name="operator_eq"></a> CPrivateObjectSecurityDesc:: operator =

대입 연산자입니다.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>매개 변수

*rhs*<br/>
현재 개체에 할당할 `CPrivateObjectSecurityDesc` 개체입니다.

### <a name="return-value"></a>반환 값

업데이트 된 개체를 반환 `CPrivateObjectSecurityDesc` 합니다.

## <a name="cprivateobjectsecuritydescset"></a><a name="set"></a> CPrivateObjectSecurityDesc:: Set

Private 개체의 보안 설명자를 수정 하려면이 메서드를 호출 합니다.

```
bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```

### <a name="parameters"></a>매개 변수

*si*<br/>
설정할 보안 설명자의 부분을 나타내는 비트 플래그 집합입니다. 이 값은 [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) 비트 플래그의 조합일 수 있습니다.

*수정*<br/>
[Csecuritydesc](../../atl/reference/csecuritydesc-class.md) 개체에 대 한 포인터입니다. *Si* 매개 변수로 표시 되는이 보안 설명자 부분은 개체의 보안 설명자에 적용 됩니다.

*GenericMapping*<br/>
각 제네릭 오른쪽에서 개체에 대 한 특정 권한으로의 매핑을 지정 하는 [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) 구조체에 대 한 포인터입니다.

*토큰*<br/>
개체를 만들고 있는 클라이언트 프로세스에 대 한 [CAccessToken](../../atl/reference/caccesstoken-class.md) 개체에 대 한 참조입니다.

*AutoInheritFlags*<br/>
Ace (액세스 제어 항목)가 *Pparent* 에서 상속 되는 방식을 제어 하는 비트 플래그 집합입니다. 자세한 내용은 [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) 를 참조 하세요.

### <a name="return-value"></a>반환 값

성공하면 true를 반환하고 실패하면 false를 반환합니다.

### <a name="remarks"></a>설명

두 번째 방법을 사용 하 여 개체의 개체 형식 GUID를 지정 하거나 Ace 상속 방식을 제어할 수 있습니다.

## <a name="see-also"></a>참고 항목

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[보안 전역 함수](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc 클래스](../../atl/reference/csecuritydesc-class.md)
