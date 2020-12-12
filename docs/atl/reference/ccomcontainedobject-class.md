---
description: '자세히 알아보기: CComContainedObject 클래스'
title: CComContainedObject 클래스
ms.date: 11/04/2016
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
ms.openlocfilehash: 9c0993d5ce71a557b71939f60a7019d3c062bac3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152206"
---
# <a name="ccomcontainedobject-class"></a>CComContainedObject 클래스

이 클래스는 소유자 개체의 `IUnknown`에 위임하여 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)을 구현합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>매개 변수

*하단*<br/>
[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 또는 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)에서 파생 된 클래스입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|생성자입니다. 소유자 개체의에 대 한 멤버 포인터를 초기화 합니다 `IUnknown` .|
|[CComContainedObject:: ~ CComContainedObject](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|Owner 개체의 참조 횟수를 증가 시킵니다.|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|소유자 개체의를 검색 합니다 `IUnknown` .|
|[CComContainedObject::QueryInterface](#queryinterface)|소유자 개체에서 요청 된 인터페이스에 대 한 포인터를 검색 합니다.|
|[CComContainedObject::Release](#release)|Owner 개체의 참조 횟수를 감소 시킵니다.|

## <a name="remarks"></a>설명

ATL은 `CComContainedObject` [CComAggObject](../../atl/reference/ccomaggobject-class.md), [ccompolyobject](../../atl/reference/ccompolyobject-class.md)및 [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)클래스에서 사용 됩니다. `CComContainedObject`소유자 개체의 `IUnknown`를 위임하여 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)을 구현합니다. (소유자는 집계의 외부 개체 또는 분리 인터페이스가 생성 되는 개체입니다.) `CComContainedObject` `CComObjectRootEx` `OuterQueryInterface` , `OuterAddRef` 및 `OuterRelease` 를 호출 합니다. 모두를 통해 상속 `Base` 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Base`

`CComContainedObject`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomcontainedobjectaddref"></a><a name="addref"></a> CComContainedObject:: AddRef

Owner 개체의 참조 횟수를 증가 시킵니다.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>반환 값

진단 또는 테스트에 유용할 수 있는 값입니다.

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="ccomcontainedobject"></a> CComContainedObject::CComContainedObject

생성자입니다.

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>매개 변수

*pv*<br/>
진행 소유자 개체의 `IUnknown` 입니다.

### <a name="remarks"></a>설명

클래스를 `m_pOuterUnknown` 통해 상속 된 멤버 포인터를 `Base` *pv* 로 설정 합니다.

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="dtor"></a> CComContainedObject:: ~ CComContainedObject

소멸자입니다.

```
~CComContainedObject();
```

### <a name="remarks"></a>설명

할당 된 리소스를 모두 해제 합니다.

## <a name="ccomcontainedobjectgetcontrollingunknown"></a><a name="getcontrollingunknown"></a> CComContainedObject::GetControllingUnknown

`m_pOuterUnknown`소유자 개체의를 보유 하는 멤버 포인터 ( *기본* 클래스를 통해 상속 됨)를 반환 합니다 `IUnknown` .

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>반환 값

소유자 개체의 `IUnknown` 입니다.

### <a name="remarks"></a>설명

`Base`가 [DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) 매크로를 선언한 경우 이 메서드는 virtual 일 수 있습니다.

## <a name="ccomcontainedobjectqueryinterface"></a><a name="queryinterface"></a> CComContainedObject:: QueryInterface

소유자 개체에서 요청 된 인터페이스에 대 한 포인터를 검색 합니다.

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

## <a name="ccomcontainedobjectrelease"></a><a name="release"></a> CComContainedObject:: Release

Owner 개체의 참조 횟수를 감소 시킵니다.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>반환 값

디버그 빌드에서는 `Release` 진단 또는 테스트에 유용할 수 있는 값을 반환 합니다. 디버그가 아닌 빌드에서는 `Release` 항상 0을 반환 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
