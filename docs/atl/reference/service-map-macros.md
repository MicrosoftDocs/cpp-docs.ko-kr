---
description: 서비스 맵 매크로에 대 한 자세한 정보
title: 서비스 맵 매크로
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: 08a26ac4043b62f8377ca9b4728eb262494f1aa1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138829"
---
# <a name="service-map-macros"></a>서비스 맵 매크로

이러한 매크로는 서비스 맵과 항목을 정의 합니다.

|Name|설명|
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|ATL 서비스 맵의 시작을 표시 합니다.|
|[END_SERVICE_MAP](#end_service_map)|ATL 서비스 맵의 끝을 표시 합니다.|
|[SERVICE_ENTRY](#service_entry)|개체가 특정 서비스 ID를 지원함을 나타냅니다.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|지정 된 개체에 연결 하도록 [Iserviceproviderimpl:: QueryService](#queryservice) 에 지시 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="begin_service_map"></a><a name="begin_service_map"></a> BEGIN_SERVICE_MAP

서비스 맵의 시작을 표시 합니다.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
진행 서비스 맵을 포함 하는 클래스를 지정 합니다.

### <a name="remarks"></a>설명

서비스 맵을 사용 하 여 COM 개체에서 서비스 공급자 기능을 구현 합니다. 먼저 [Iserviceproviderimpl](../../atl/reference/iserviceproviderimpl-class.md)클래스를 파생 해야 합니다. 항목에는 다음과 같은 두 가지 유형이 있습니다.

- [SERVICE_ENTRY](#service_entry)   지정 된 SID (서비스 ID)에 대 한 지원을 나타냅니다.

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)   지정 된 다른 개체에 연결 하도록 [Iserviceproviderimpl:: QueryService](#queryservice) 에 지시 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

## <a name="end_service_map"></a><a name="end_service_map"></a> END_SERVICE_MAP

서비스 맵의 끝을 표시 합니다.

```
END_SERVICE_MAP()
```

### <a name="example"></a>예제

[BEGIN_SERVICE_MAP](#begin_service_map)의 예제를 참조 하세요.

## <a name="service_entry"></a><a name="service_entry"></a> SERVICE_ENTRY

개체가 *SID* 로 지정 된 서비스 id를 지원함을 나타냅니다.

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>매개 변수

*SID*<br/>
서비스 ID입니다.

### <a name="example"></a>예제

[BEGIN_SERVICE_MAP](#begin_service_map)의 예제를 참조 하세요.

## <a name="service_entry_chain"></a><a name="service_entry_chain"></a> SERVICE_ENTRY_CHAIN

*Punk* 에 지정 된 개체에 연결 하도록 [Iserviceproviderimpl::](#queryservice) 에 지시 합니다.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>매개 변수

*punk*<br/>
연결할 **IUnknown** 인터페이스에 대 한 포인터입니다.

### <a name="example"></a>예제

[BEGIN_SERVICE_MAP](#begin_service_map)의 예제를 참조 하세요.

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

[매크로](../../atl/reference/atl-macros.md)
