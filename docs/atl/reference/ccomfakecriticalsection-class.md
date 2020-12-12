---
description: '자세히 알아보기: CComFakeCriticalSection 클래스'
title: CComFakeCriticalSection 클래스
ms.date: 11/04/2016
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
ms.openlocfilehash: 7280a47daa7464b24246ca8baa0aa7f5eaefa87a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152063"
---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalSection 클래스

이 클래스는 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 와 동일한 메서드를 제공 하지만 임계 영역을 제공 하지 않습니다.

## <a name="syntax"></a>구문

```
class CComFakeCriticalSection
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComFakeCriticalSection:: Init](#init)|중요 한 섹션이 없기 때문에 아무 작업도 수행 하지 않습니다.|
|[CComFakeCriticalSection:: Lock](#lock)|중요 한 섹션이 없기 때문에 아무 작업도 수행 하지 않습니다.|
|[CComFakeCriticalSection:: Term](#term)|중요 한 섹션이 없기 때문에 아무 작업도 수행 하지 않습니다.|
|[CComFakeCriticalSection:: Unlock](#unlock)|중요 한 섹션이 없기 때문에 아무 작업도 수행 하지 않습니다.|

## <a name="remarks"></a>설명

`CComFakeCriticalSection`[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)에 있는 메서드를 미러링합니다. 그러나는 `CComFakeCriticalSection` 임계 영역을 제공 하지 않으므로 해당 메서드는 아무 작업도 수행 하지 않습니다.

일반적으로 또는의 `CComFakeCriticalSection` 이름을 통해를 사용 **`typedef`** `AutoCriticalSection` `CriticalSection` 합니다. [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) 또는 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)를 사용 하는 경우이 두 **`typedef`** 이름이 모두 참조 `CComFakeCriticalSection` 됩니다. [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)를 사용 하는 경우 각각 [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) 및 `CComCriticalSection` 를 참조 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomfakecriticalsectioninit"></a><a name="init"></a> CComFakeCriticalSection:: Init

중요 한 섹션이 없기 때문에 아무 작업도 수행 하지 않습니다.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

## <a name="ccomfakecriticalsectionlock"></a><a name="lock"></a> CComFakeCriticalSection:: Lock

중요 한 섹션이 없기 때문에 아무 작업도 수행 하지 않습니다.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

## <a name="ccomfakecriticalsectionterm"></a><a name="term"></a> CComFakeCriticalSection:: Term

중요 한 섹션이 없기 때문에 아무 작업도 수행 하지 않습니다.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

## <a name="ccomfakecriticalsectionunlock"></a><a name="unlock"></a> CComFakeCriticalSection:: Unlock

중요 한 섹션이 없기 때문에 아무 작업도 수행 하지 않습니다.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
