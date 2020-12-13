---
description: '자세한 정보: CComPolyObject 클래스'
title: CComPolyObject 클래스
ms.date: 11/04/2016
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
ms.openlocfilehash: 1584fd03882b0eb0618bd20b54134317efd17ba8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142404"
---
# <a name="ccompolyobject-class"></a>CComPolyObject 클래스

이 클래스 `IUnknown` 는 집계 되거나 집계 되지 않은 개체에 대해를 구현 합니다.

## <a name="syntax"></a>구문

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>매개 변수

*있어*<br/>
[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 또는 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)에서 파생 된 클래스 및 개체에서 지원 하려는 다른 모든 인터페이스에서 파생 됩니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComPolyObject:: CComPolyObject](#ccompolyobject)|생성자입니다.|
|[CComPolyObject:: ~ CComPolyObject](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComPolyObject:: AddRef](#addref)|개체의 참조 횟수를 증가 시킵니다.|
|[CComPolyObject:: CreateInstance](#createinstance)|정적인 는  `contained` **>** [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)의 오버 헤드 없이 새 ccompolyobject<개체를 만들 수 있습니다.|
|[CComPolyObject::. 개 구문](#finalconstruct)|의 최종 초기화를 수행 `m_contained` 합니다.|
|[CComPolyObject::FinalRelease](#finalrelease)|의 최종 소멸을 수행 `m_contained` 합니다.|
|[CComPolyObject:: QueryInterface](#queryinterface)|요청된 인터페이스에 대한 포인터를 검색합니다.|
|[CComPolyObject::Release](#release)|개체의 참조 횟수를 감소 시킵니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|개체가 집계 `IUnknown` 되 고 있지 않은 경우 외부에서 알 수 없는 호출을 위임 `IUnknown` 합니다.|

## <a name="remarks"></a>설명

`CComPolyObject` 집계 된 개체 또는 집계할 때가 아닌 개체에 대해 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 을 구현 합니다.

인스턴스를 만들 때 `CComPolyObject` 알 수 없는 외부 값이 확인 됩니다. NULL 인 경우 `IUnknown` 는 집계할 수 없는 개체에 대해 구현 됩니다. 외부 unknown이 NULL이 아닌 경우는 `IUnknown` 집계 된 개체에 대해 구현 됩니다.

를 사용 하는 경우의 장점은 `CComPolyObject` 집계 된 사례와 집계할 수 없는 사례를 처리 하기 위해 모듈에 [CComAggObject](../../atl/reference/ccomaggobject-class.md) 및 [CComObject](../../atl/reference/ccomobject-class.md) 를 둘 다 포함 하지 않도록 하는 것입니다. 단일 `CComPolyObject` 개체는 두 경우를 모두 처리 합니다. 즉, 모듈에는 vtable의 복사본 하 나와 함수의 복사본이 하나만 있습니다. Vtable이 큰 경우 모듈 크기를 크게 줄일 수 있습니다. 그러나 vtable이 작은 경우를 사용 하면 `CComPolyObject` 집계 된 개체 또는 집계할 수 없는 개체에 대해 최적화 되지 않으므로를 사용 하 여 모듈 크기가 약간 커질 수 있습니다 `CComAggObject` `CComObject` .

개체의 클래스 정의에 DECLARE_POLY_AGGREGATABLE 매크로가 지정 된 경우는 개체를 `CComPolyObject` 만드는 데 사용 됩니다. ATL 프로젝트 마법사를 사용 하 여 모든 컨트롤이 나 Internet Explorer 컨트롤을 만드는 경우에는 DECLARE_POLY_AGGREGATABLE 자동으로 선언 됩니다.

집계 되는 경우 `CComPolyObject` 개체는 `IUnknown` 외부 개체와는 다른 자체를 포함 `IUnknown` 하 고 자체 참조 횟수를 유지 관리 합니다. `CComPolyObject`[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) 를 사용 하 여 알 수 없는 외부에 위임 합니다.

집계에 대 한 자세한 내용은 [ATL COM 개체의 기본 사항](../../atl/fundamentals-of-atl-com-objects.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccompolyobjectaddref"></a><a name="addref"></a> CComPolyObject:: AddRef

개체의 참조 횟수를 증가 시킵니다.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>반환 값

진단 또는 테스트에 유용할 수 있는 값입니다.

## <a name="ccompolyobjectccompolyobject"></a><a name="ccompolyobject"></a> CComPolyObject:: CComPolyObject

생성자입니다.

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>매개 변수

*pv*<br/>
진행 개체를 집계할 경우 외부 unknown에 대 한 포인터이 고, 개체가 집계 되지 않은 경우에는 NULL입니다.

### <a name="remarks"></a>설명

[M_contained](#m_contained)`CComContainedObject`데이터 멤버를 초기화하고 모듈 잠금 수를 늘립니다.

소멸자는 모듈 잠금 횟수를 감소 시킵니다.

## <a name="ccompolyobjectccompolyobject"></a><a name="dtor"></a> CComPolyObject:: ~ CComPolyObject

소멸자입니다.

```
~CComPolyObject();
```

### <a name="remarks"></a>설명

할당 된 모든 리소스를 해제 하 고, 전체 [릴리스](#finalrelease)를 호출 하 고, 모듈 잠금 횟수를 감소 시킵니다.

## <a name="ccompolyobjectcreateinstance"></a><a name="createinstance"></a> CComPolyObject:: CreateInstance

는  `contained` **>** [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)의 오버 헤드 없이 새 ccompolyobject<개체를 만들 수 있습니다.

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>매개 변수

*페이지*<br/>
제한이 **Ccompolyobject<** 포인터에 대 한 포인터 `contained` **>** 입니다. `CreateInstance`가 실패 하면 *PP* 가 NULL로 설정 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

반환 된 개체의 참조 횟수는 0 이므로 `AddRef` 즉시 호출한 다음를 사용 하 여 `Release` 작업이 완료 되 면 개체 포인터에 대 한 참조를 해제 합니다.

개체에 직접 액세스할 필요가 없지만의 오버 헤드 없이 새 개체를 만들려면 `CoCreateInstance` [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) 를 대신 사용 합니다.

## <a name="ccompolyobjectfinalconstruct"></a><a name="finalconstruct"></a> CComPolyObject::. 개 구문

개체 생성의 최종 단계 중에 호출 되는이 메서드는 [m_contained](#m_contained) 데이터 멤버에 대 한 최종 초기화를 수행 합니다.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="ccompolyobjectfinalrelease"></a><a name="finalrelease"></a> CComPolyObject:: 버전 릴리스

개체 소멸 중에 호출 되는이 메서드는 [m_contained](#m_contained) 데이터 멤버를 해제 합니다.

```cpp
void FinalRelease();
```

## <a name="ccompolyobjectm_contained"></a><a name="m_contained"></a> CComPolyObject:: m_contained

클래스에서 파생 된 [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) 개체입니다.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>매개 변수

*있어*<br/>
진행 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 또는 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)에서 파생 된 클래스 및 개체에서 지원 하려는 다른 모든 인터페이스에서 파생 됩니다.

### <a name="remarks"></a>설명

`IUnknown``m_contained`개체가 집계 된 경우에는 외부 unknown에 위임 되 고, `IUnknown` 개체가 집계 되지 않은 경우에는이 개체의로 호출 됩니다.

## <a name="ccompolyobjectqueryinterface"></a><a name="queryinterface"></a> CComPolyObject:: QueryInterface

요청된 인터페이스에 대한 포인터를 검색합니다.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>매개 변수

*Q*<br/>
COM 인터페이스입니다.

*iid*<br/>
진행 요청 되는 인터페이스의 식별자입니다.

*ppvObject*<br/>
제한이 *Iid* 로 식별 되는 인터페이스 포인터에 대 한 포인터입니다. 개체가이 인터페이스를 지원 하지 않으면 *Ppvobject* 가 NULL로 설정 됩니다.

*페이지*<br/>
제한이 로 식별 되는 인터페이스에 대 한 포인터 `__uuidof(Q)` 입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

집계 된 개체의 경우 요청 된 인터페이스가 이면는 `IUnknown` `QueryInterface` 집계 된 개체의 자체에 대 한 포인터를 반환 하 `IUnknown` 고 참조 횟수를 증가 시킵니다. 그렇지 않으면이 메서드는 `CComContainedObject` [m_contained](#m_contained)데이터 멤버를 통해 인터페이스를 쿼리 합니다.

## <a name="ccompolyobjectrelease"></a><a name="release"></a> CComPolyObject:: Release

개체의 참조 횟수를 감소 시킵니다.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>반환 값

디버그 빌드에서는 `Release` 진단 또는 테스트에 유용할 수 있는 값을 반환 합니다. Nondebug 빌드에서는 `Release` 항상 0을 반환 합니다.

## <a name="see-also"></a>참고 항목

[CComObjectRootEx 클래스](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
