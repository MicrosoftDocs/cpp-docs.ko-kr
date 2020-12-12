---
description: '자세히 알아보기: CComCriticalSection 클래스'
title: CComCriticalSection 클래스
ms.date: 11/04/2016
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
ms.openlocfilehash: 7a6a3efef68a14cbda513ee60ed3980293514ad6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146733"
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection 클래스

이 클래스는 임계 영역 개체의 소유권을 가져오고 해제 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
class CComCriticalSection
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComCriticalSection:: Init](#init)|임계 영역 개체를 만들고 초기화 합니다.|
|[CComCriticalSection::Lock](#lock)|임계 영역 개체의 소유권을 가져옵니다.|
|[CComCriticalSection::Term](#term)|임계 영역 개체에서 사용 하는 시스템 리소스를 해제 합니다.|
|[CComCriticalSection::Unlock](#unlock)|임계 영역 개체의 소유권을 해제 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|CRITICAL_SECTION 개체입니다.|

## <a name="remarks"></a>설명

`CComCriticalSection` 는 임계 영역을 명시적으로 초기화 하 고 해제 해야 한다는 점을 제외 하 고는 [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)클래스와 유사 합니다.

일반적으로 `CComCriticalSection` CriticalSection 이름을 통해를 **`typedef`** 사용 [](ccommultithreadmodel-class.md#criticalsection)합니다. [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)를 사용하는 경우 이 이름은 `CComCriticalSection`를 참조합니다.

이 클래스를 사용 하는 보다 안전한 방법은 [CComCritSecLock 클래스](../../atl/reference/ccomcritseclock-class.md) 를 참조 `Lock` 하세요 `Unlock` .

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomcriticalsectionccomcriticalsection"></a><a name="ccomcriticalsection"></a> CComCriticalSection::CComCriticalSection

생성자입니다.

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>설명

[M_sec](#m_sec) 데이터 멤버를 NULL로 설정 합니다.

## <a name="ccomcriticalsectioninit"></a><a name="init"></a> CComCriticalSection:: Init

[M_sec](#m_sec) 데이터 멤버에 포함 된 임계 영역 개체를 초기화 하는 Win32 함수 [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection)를 호출 합니다.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK를 반환 하거나, 오류 발생 시 E_FAIL E_OUTOFMEMORY 반환 합니다.

## <a name="ccomcriticalsectionlock"></a><a name="lock"></a> CComCriticalSection:: Lock

는 스레드가 [m_sec](#m_sec) 데이터 멤버에 포함 된 임계 영역 개체의 소유권을 가져올 수 있을 때까지 대기 하는 Win32 함수 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)를 호출 합니다.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK를 반환 하거나, 오류 발생 시 E_FAIL E_OUTOFMEMORY 반환 합니다.

### <a name="remarks"></a>설명

먼저 [Init](#init) 메서드를 호출 하 여 임계 영역 개체를 초기화 해야 합니다. 보호 된 코드의 실행이 완료 되 면 스레드의 [잠금 해제](#unlock) 를 호출 하 여 임계 영역에 대 한 소유권을 해제 해야 합니다.

## <a name="ccomcriticalsectionm_sec"></a><a name="m_sec"></a> CComCriticalSection:: m_sec

모든 메서드에서 사용 하는 임계 영역 개체를 포함 `CComCriticalSection` 합니다.

```
CRITICAL_SECTION m_sec;
```

## <a name="ccomcriticalsectionterm"></a><a name="term"></a> CComCriticalSection:: Term

[M_sec](#m_sec) 데이터 멤버에 포함 된 임계 영역 개체에서 사용 하는 모든 리소스를 해제 하는 Win32 함수 [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection)를 호출 합니다.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

`Term`가 호출 되 면 임계 영역을 더 이상 동기화에 사용할 수 없습니다.

## <a name="ccomcriticalsectionunlock"></a><a name="unlock"></a> CComCriticalSection:: Unlock

[M_sec](#m_sec) 데이터 멤버에 포함 된 임계 영역 개체의 소유권을 해제 하는 Win32 함수 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)를 호출 합니다.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

### <a name="remarks"></a>설명

먼저 소유권을 얻으려면 스레드가 [Lock](#lock) 메서드를 호출 해야 합니다. 에 대 한 각 호출에는 임계 영역에 대 한 `Lock` `Unlock` 소유권을 해제 하기 위해에 대 한 해당 호출이 필요 합니다.

## <a name="see-also"></a>참고 항목

[CComFakeCriticalSection 클래스](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[CComCritSecLock 클래스](../../atl/reference/ccomcritseclock-class.md)
