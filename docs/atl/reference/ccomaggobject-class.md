---
description: '자세히 알아보기: CComAggObject 클래스'
title: CComAggObject 클래스
ms.date: 11/04/2016
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
ms.openlocfilehash: 84af79678221ae74a151a4821039ff1d7a743cc5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152362"
---
# <a name="ccomaggobject-class"></a>CComAggObject 클래스

이 클래스는 집계 된 개체에 대 한 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 인터페이스를 구현 합니다. 정의에 따라 집계 된 개체는 외부 개체에 포함 됩니다. `CComAggObject`클래스는 외부 클라이언트에서 직접 액세스할 수 있는 인터페이스를 노출 한다는 점을 제외 하 고는 [CComObject 클래스](../../atl/reference/ccomobject-class.md)와 유사 합니다.

## <a name="syntax"></a>구문

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>매개 변수

*있어*<br/>
[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 또는 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)에서 파생 된 클래스 및 개체에서 지원 하려는 다른 모든 인터페이스에서 파생 됩니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComAggObject::CComAggObject](#ccomaggobject)|생성자입니다.|
|[CComAggObject:: ~ CComAggObject](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComAggObject:: AddRef](#addref)|집계 된 개체의 참조 횟수를 증가 시킵니다.|
|[CComAggObject:: CreateInstance](#createinstance)|이 정적 함수를 사용 하면  `contained` **>** [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)의 오버 헤드 없이 새 CComAggObject<개체를 만들 수 있습니다.|
|[CComAggObject::FinalConstruct](#finalconstruct)|의 최종 초기화를 수행 `m_contained` 합니다.|
|[CComAggObject::FinalRelease](#finalrelease)|의 최종 소멸을 수행 `m_contained` 합니다.|
|[CComAggObject:: QueryInterface](#queryinterface)|요청된 인터페이스에 대한 포인터를 검색합니다.|
|[CComAggObject:: Release](#release)|집계 된 개체의 참조 횟수를 감소 시킵니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComAggObject::m_contained](#m_contained)|`IUnknown`외부 알려지지 않은에 대 한 호출을 위임 합니다.|

## <a name="remarks"></a>설명

`CComAggObject` 집계 된 개체에 대해 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 을 구현 합니다. `CComAggObject` 에는 `IUnknown` 외부 개체의 인터페이스와는 별개의 인터페이스가 `IUnknown` 있고 자체 참조 횟수를 유지 관리 합니다.

집계에 대 한 자세한 내용은 [ATL COM 개체의 기본 사항](../../atl/fundamentals-of-atl-com-objects.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomaggobjectaddref"></a><a name="addref"></a> CComAggObject:: AddRef

집계 된 개체의 참조 횟수를 증가 시킵니다.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>반환 값

진단 또는 테스트에 유용할 수 있는 값입니다.

## <a name="ccomaggobjectccomaggobject"></a><a name="ccomaggobject"></a> CComAggObject:: CComAggObject

생성자입니다.

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>매개 변수

*pv*<br/>
진행 외부 알려지지 않은입니다.

### <a name="remarks"></a>설명

`CComContainedObject`[M_contained](#m_contained) 멤버를 초기화하고 모듈 잠금 수를 늘립니다.

소멸자는 모듈 잠금 횟수를 감소 시킵니다.

## <a name="ccomaggobjectccomaggobject"></a><a name="dtor"></a> CComAggObject:: ~ CComAggObject

소멸자입니다.

```
~CComAggObject();
```

### <a name="remarks"></a>설명

할당 된 모든 리소스를 해제 하 고, 전체 [릴리스](#finalrelease)를 호출 하 고, 모듈 잠금 횟수를 감소 시킵니다.

## <a name="ccomaggobjectcreateinstance"></a><a name="createinstance"></a> CComAggObject:: CreateInstance

이 정적 함수를 사용 하면  `contained` **>** [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)의 오버 헤드 없이 새 CComAggObject<개체를 만들 수 있습니다.

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>매개 변수

*페이지*<br/>
제한이> * * 포인터 **를 \<**<em> 포함 </em>** 하는 CComAggObject에 대 한 포인터입니다. `CreateInstance`가 실패 하면 *PP* 가 NULL로 설정 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

반환 된 개체의 참조 횟수는 0 이므로 `AddRef` 즉시 호출한 다음를 사용 하 여 `Release` 작업이 완료 되 면 개체 포인터에 대 한 참조를 해제 합니다.

개체에 직접 액세스할 필요가 없지만의 오버 헤드 없이 새 개체를 만들려면 `CoCreateInstance` [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) 를 대신 사용 합니다.

## <a name="ccomaggobjectfinalconstruct"></a><a name="finalconstruct"></a> CComAggObject:: 구문

개체 생성의 최종 단계 중에 호출 되는이 메서드는 [m_contained](#m_contained) 멤버에 대 한 최종 초기화를 수행 합니다.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="ccomaggobjectfinalrelease"></a><a name="finalrelease"></a> CComAggObject:: 버전 릴리스

개체 소멸 중에 호출 되는이 메서드는 [m_contained](#m_contained) 멤버를 해제 합니다.

```cpp
void FinalRelease();
```

## <a name="ccomaggobjectm_contained"></a><a name="m_contained"></a> CComAggObject:: m_contained

클래스에서 파생 된 [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) 개체입니다.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>매개 변수

*있어*<br/>
진행 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 또는 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)에서 파생 된 클래스 및 개체에서 지원 하려는 다른 모든 인터페이스에서 파생 됩니다.

### <a name="remarks"></a>설명

`IUnknown`를 통한 모든 호출은 `m_contained` 외부에서 알 수 없는 외부에 위임 됩니다.

## <a name="ccomaggobjectqueryinterface"></a><a name="queryinterface"></a> CComAggObject:: QueryInterface

요청된 인터페이스에 대한 포인터를 검색합니다.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 요청 되는 인터페이스의 식별자입니다.

*ppvObject*<br/>
제한이 *Iid* 로 식별 되는 인터페이스 포인터에 대 한 포인터입니다. 개체가이 인터페이스를 지원 하지 않으면 *Ppvobject* 가 NULL로 설정 됩니다.

*페이지*<br/>
제한이 형식으로 식별 되는 인터페이스 포인터에 대 한 포인터 `Q` 입니다. 개체가이 인터페이스를 지원 하지 않는 경우 *pp* 가 NULL로 설정 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

요청 된 인터페이스가 인 경우 `IUnknown` 는 `QueryInterface` 집계 된 개체의 자체에 대 한 포인터를 반환 하 `IUnknown` 고 참조 횟수를 증가 시킵니다. 그렇지 않으면이 메서드는 `CComContainedObject` [m_contained](#m_contained)멤버를 통해 인터페이스를 쿼리 합니다.

## <a name="ccomaggobjectrelease"></a><a name="release"></a> CComAggObject:: Release

집계 된 개체의 참조 횟수를 감소 시킵니다.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>반환 값

디버그 빌드에서는 `Release` 진단 또는 테스트에 유용할 수 있는 값을 반환 합니다. 디버그가 아닌 빌드에서는 `Release` 항상 0을 반환 합니다.

## <a name="see-also"></a>참고 항목

[CComObject 클래스](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 클래스](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
