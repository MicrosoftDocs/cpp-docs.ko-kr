---
description: '자세히 알아보기: CTokenGroups 클래스'
title: CTokenGroups 클래스
ms.date: 11/04/2016
f1_keywords:
- CTokenGroups
- ATLSECURITY/ATL::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::Add
- ATLSECURITY/ATL::CTokenGroups::Delete
- ATLSECURITY/ATL::CTokenGroups::DeleteAll
- ATLSECURITY/ATL::CTokenGroups::GetCount
- ATLSECURITY/ATL::CTokenGroups::GetLength
- ATLSECURITY/ATL::CTokenGroups::GetPTOKEN_GROUPS
- ATLSECURITY/ATL::CTokenGroups::GetSidsAndAttributes
- ATLSECURITY/ATL::CTokenGroups::LookupSid
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
ms.openlocfilehash: 3d6633afbd649aa175196f1fae8e62afdf784f99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140350"
---
# <a name="ctokengroups-class"></a>CTokenGroups 클래스

이 클래스는 구조체에 대 한 래퍼입니다 `TOKEN_GROUPS` .

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CTokenGroups
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|생성자입니다.|
|[CTokenGroups:: ~ CTokenGroups](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CTokenGroups:: Add](#add)|`CSid`개체에 또는 기존 `TOKEN_GROUPS` 구조체를 추가 `CTokenGroups` 합니다.|
|[CTokenGroups::D e)](#delete)|`CSid`개체에서 및 관련 특성을 삭제 `CTokenGroups` 합니다.|
|[CTokenGroups::D eleteAll](#deleteall)|`CSid`개체에서 모든 개체 및 관련 특성을 삭제 `CTokenGroups` 합니다.|
|[CTokenGroups:: GetCount](#getcount)|`CSid`개체에 포함 된 개체 및 관련 특성의 수를 반환 합니다 `CTokenGroups` .|
|[CTokenGroups:: GetLength](#getlength)|개체의 크기를 반환 합니다 `CTokenGroups` .|
|[CTokenGroups:: GetPTOKEN_GROUPS](#getptoken_groups)|구조체에 대 한 포인터를 검색 `TOKEN_GROUPS` 합니다.|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|`CSid`개체에 속하는 개체 및 특성을 검색 `CTokenGroups` 합니다.|
|[CTokenGroups:: LookupSid](#lookupsid)|개체와 연결 된 특성을 검색 `CSid` 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CTokenGroups:: operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|개체를 `CTokenGroups` 구조체에 대 한 포인터로 캐스팅 `TOKEN_GROUPS` 합니다.|
|[CTokenGroups:: operator =](#operator_eq)|대입 연산자입니다.|

## <a name="remarks"></a>설명

[액세스 토큰](/windows/win32/SecAuthZ/access-tokens) 은 프로세스나 스레드의 보안 컨텍스트를 설명 하 고 Windows 시스템에 로그온 한 각 사용자에 게 할당 되는 개체입니다.

`CTokenGroups`클래스는 액세스 토큰의 그룹 sid (보안 식별자)에 대 한 정보를 포함 하는 [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) 구조체의 래퍼입니다.

Windows의 액세스 제어 모델에 대 한 소개는 Windows SDK [Access Control](/windows/win32/SecAuthZ/access-control) 를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="ctokengroupsadd"></a><a name="add"></a> CTokenGroups:: Add

`CSid`개체에 또는 기존 `TOKEN_GROUPS` 구조체를 추가 `CTokenGroups` 합니다.

```cpp
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>매개 변수

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md) 개체입니다.

*dwAttributes*<br/>
개체에 연결할 특성 `CSid` 입니다.

*rTokenGroups*<br/>
[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) 구조체입니다.

### <a name="remarks"></a>설명

이러한 메서드는 `CSid` 개체와 개체에 연결 된 특성을 하나 이상 추가 `CTokenGroups` 합니다.

## <a name="ctokengroupsctokengroups"></a><a name="ctokengroups"></a> CTokenGroups::CTokenGroups

생성자입니다.

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>매개 변수

*rhs*<br/>
`CTokenGroups`개체를 생성 하는 데 사용할 개체 또는 [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) 구조 `CTokenGroups` 입니다.

### <a name="remarks"></a>설명

`CTokenGroups`필요에 따라 `TOKEN_GROUPS` 구조체 또는 이전에 정의 된 개체를 사용 하 여 개체를 만들 수 있습니다 `CTokenGroups` .

## <a name="ctokengroupsctokengroups"></a><a name="dtor"></a> CTokenGroups:: ~ CTokenGroups

소멸자입니다.

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>설명

소멸자는 할당 된 리소스를 모두 해제 합니다.

## <a name="ctokengroupsdelete"></a><a name="delete"></a> CTokenGroups::D e)

`CSid`개체에서 및 관련 특성을 삭제 `CTokenGroups` 합니다.

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>매개 변수

*rSid*<br/>
SID (보안 식별자) 및 특성을 제거할 [CSid](../../atl/reference/csid-class.md) 개체입니다.

### <a name="return-value"></a>반환 값

`CSid`이 제거 되 면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

## <a name="ctokengroupsdeleteall"></a><a name="deleteall"></a> CTokenGroups::D eleteAll

`CSid`개체에서 모든 개체 및 관련 특성을 삭제 `CTokenGroups` 합니다.

```cpp
void DeleteAll() throw();
```

## <a name="ctokengroupsgetcount"></a><a name="getcount"></a> CTokenGroups:: GetCount

에 포함 된 개체 수를 반환 합니다 `CSid` `CTokenGroups` .

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>반환 값

개체에 포함 된 [CSid](../../atl/reference/csid-class.md) 개체 및 관련 특성의 수를 반환 합니다 `CTokenGroups` .

## <a name="ctokengroupsgetlength"></a><a name="getlength"></a> CTokenGroups:: GetLength

개체의 크기를 반환 합니다 `CTokenGroup` .

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>설명

개체의 총 크기 (바이트)를 반환 합니다 `CTokenGroup` .

## <a name="ctokengroupsgetptoken_groups"></a><a name="getptoken_groups"></a> CTokenGroups:: GetPTOKEN_GROUPS

구조체에 대 한 포인터를 검색 `TOKEN_GROUPS` 합니다.

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>반환 값

액세스 토큰 개체에 속하는 [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) 구조체에 대 한 포인터를 검색 `CTokenGroups` 합니다.

## <a name="ctokengroupsgetsidsandattributes"></a><a name="getsidsandattributes"></a> CTokenGroups::GetSidsAndAttributes

개체를 검색 하 `CSid` 고 선택적으로 개체에 속한 특성을 검색 합니다 `CTokenGroups` .

```cpp
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>매개 변수

*pSids*<br/>
[CSid](../../atl/reference/csid-class.md) 개체의 배열에 대 한 포인터입니다.

*pAttributes*<br/>
Dword 배열에 대 한 포인터입니다. 이 매개 변수를 생략 하거나 NULL을 지정 하면 특성이 검색 되지 않습니다.

### <a name="remarks"></a>설명

이 메서드는 개체에 포함 된 모든 개체를 열거 하 `CSid` `CTokenGroups` 고 배열 개체에 특성 플래그를 추가 합니다 (선택 사항).

## <a name="ctokengroupslookupsid"></a><a name="lookupsid"></a> CTokenGroups:: LookupSid

개체와 연결 된 특성을 검색 `CSid` 합니다.

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>매개 변수

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md) 개체입니다.

*pdwAttributes*<br/>
개체의 특성을 허용 하는 DWORD에 대 한 포인터입니다 `CSid` . 생략 하거나 NULL 인 경우에는 특성이 검색 되지 않습니다.

### <a name="return-value"></a>반환 값

이 있으면 true `CSid` 를 반환 하 고, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

*Pdwattributes* 를 NULL로 설정 하면 특성에 액세스 하지 않고의 존재를 확인 하는 방법을 제공 합니다 `CSid` . 이 메서드는 액세스 권한을 확인 하는 데 사용 하면 안 됩니다. 응용 프로그램에서 [CAccessToken:: CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) 메서드를 대신 사용 해야 합니다.

## <a name="ctokengroupsoperator-"></a><a name="operator_eq"></a> CTokenGroups:: operator =

대입 연산자입니다.

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>매개 변수

*rhs*<br/>
`CTokenGroups`개체에 할당할 개체 또는 [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) 구조 `CTokenGroups` 입니다.

### <a name="return-value"></a>반환 값

업데이트 된 개체를 반환 `CTokenGroups` 합니다.

## <a name="ctokengroupsoperator-const-token_groups-"></a><a name="operator_const_token_groups__star"></a> CTokenGroups:: operator const TOKEN_GROUPS *

구조체에 대 한 포인터로 값을 캐스팅 `TOKEN_GROUPS` 합니다.

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>설명

값을 [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) 구조체에 대 한 포인터로 캐스팅 합니다.

## <a name="see-also"></a>참고 항목

[보안 샘플](../../overview/visual-cpp-samples.md)<br/>
[CSid 클래스](../../atl/reference/csid-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[보안 전역 함수](../../atl/reference/security-global-functions.md)
