---
description: '자세한 정보: IServiceProviderImpl 클래스'
title: IServiceProviderImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
ms.openlocfilehash: 0cd9fab784fe8bffe420123129aa51c80c187890
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139154"
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl 클래스

이 클래스는 인터페이스의 기본 구현을 제공 합니다 `IServiceProvider` .

## <a name="syntax"></a>구문

```
template <class T>
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IServiceProviderImpl` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IServiceProviderImpl:: QueryService](#queryservice)|지정 된 서비스를 만들거나 액세스 하 고 서비스에 대해 지정 된 인터페이스에 대 한 인터페이스 포인터를 반환 합니다.|

## <a name="remarks"></a>설명

`IServiceProvider`인터페이스는 해당 GUID로 지정 된 서비스를 찾고 서비스에서 요청 된 인터페이스에 대 한 인터페이스 포인터를 반환 합니다. 클래스는 `IServiceProviderImpl` 이 인터페이스의 기본 구현을 제공 합니다.

`IServiceProviderImpl` 지정 된 서비스를 만들거나 액세스 하 고 서비스에 대해 지정 된 인터페이스에 대 한 인터페이스 포인터를 반환 하는 메서드 하나를 지정 합니다. [QueryService](#queryservice).

`IServiceProviderImpl` 는 [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) 부터 시작 하 여 [END_SERVICE_MAP](service-map-macros.md#end_service_map)종료 되는 서비스 맵을 사용 합니다.

서비스 맵에는 개체에서 지 원하는 지정 된 서비스 id (SID)를 나타내는 [SERVICE_ENTRY](service-map-macros.md#service_entry)와 다른 개체에 연결 하기 위해를 호출 하는 [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain)두 개의 항목이 포함 되어 있습니다. `QueryService`

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="iserviceproviderimplqueryservice"></a><a name="queryservice"></a> IServiceProviderImpl:: QueryService

지정 된 서비스를 만들거나 액세스 하 고 서비스에 대해 지정 된 인터페이스에 대 한 인터페이스 포인터를 반환 합니다.

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>매개 변수

*guidService*<br/>
진행 SID (서비스 식별자)에 대 한 포인터입니다.

*riid*<br/>
진행 호출자가 액세스할 수 있는 인터페이스의 식별자입니다.

*ppvObj*<br/>
제한이 요청 된 인터페이스에 대 한 간접 포인터입니다.

### <a name="return-value"></a>반환 값

반환 된 HRESULT 값은 다음 중 하나입니다.

|반환 값|의미|
|------------------|-------------|
|S_OK|서비스를 만들거나 검색 했습니다.|
|E_INVALIDARG|하나 이상의 인수가 잘못된 경우|
|E_OUTOFMEMORY|메모리가 부족 하 여 서비스를 만들 수 없습니다.|
|E_UNEXPECTED|알 수 없는 오류가 발생했습니다.|
|E_NOINTERFACE|요청 된 인터페이스가이 서비스의 일부가 아니거나 서비스를 알 수 없습니다.|

### <a name="remarks"></a>설명

`QueryService` 지정 된 서비스에서 요청 된 인터페이스에 대 한 간접 포인터를 반환 합니다. 호출자는 더 이상 필요 하지 않은 경우이 포인터를 해제 해야 합니다.

를 호출할 때 `QueryService` 서비스 식별자 (*guidService*)와 인터페이스 식별자 (*riid*)를 모두 전달 합니다. *GuidService* 는 액세스 하려는 서비스를 지정 하 고, *riid* 는 서비스의 일부인 인터페이스를 식별 합니다. 반환 시 인터페이스에 대 한 간접 포인터를 받습니다.

인터페이스를 구현 하는 개체는 다른 서비스의 일부인 인터페이스를 구현할 수도 있습니다. 다음을 살펴보세요.

- 이러한 인터페이스 중 일부는 선택 사항이 될 수 있습니다. 서비스 설명에 정의 된 모든 인터페이스는 서비스의 모든 구현 또는 반환 된 모든 개체에 반드시 있어야 하는 것은 아닙니다.

- 호출과 달리 다른 서비스 식별자를 전달 하는 것은 `QueryInterface` 다른 COM (구성 요소 개체 모델) 개체가 반환 되는 것을 의미 하는 것은 아닙니다.

- 반환 된 개체에는 서비스 정의의 일부가 아닌 추가 인터페이스가 있을 수 있습니다.

SID_SMyService 및 SID_SYourService와 같은 두 가지 서비스는 둘 다 동일한 인터페이스를 사용 하도록 지정할 수 있습니다. 단, 인터페이스 구현에는 두 서비스 간에 공통적인 내용이 없을 수 있습니다. `QueryService`(SID_SMyService, IID_IDispatch)에 대 한 호출은 `QueryService` (SID_SYourService, IID_IDispatch)와 다른 개체를 반환할 수 있기 때문에이 작업을 수행 합니다. 다른 서비스 식별자를 지정 하는 경우에는 개체 id를 가정 하지 않습니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
