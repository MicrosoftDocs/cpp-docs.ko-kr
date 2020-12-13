---
description: '자세히 알아보기: CComObject 클래스'
title: CComObject 클래스
ms.date: 11/04/2016
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
ms.openlocfilehash: 086383172d5bb239bbac8ed90e9118838aea1254
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146525"
---
# <a name="ccomobject-class"></a>CComObject 클래스

이 클래스는 집계할 때를 구현 하지 않는 `IUnknown` 개체에 대해를 구현 합니다.

## <a name="syntax"></a>구문

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>매개 변수

*하단*<br/>
[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 또는 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)에서 파생 된 클래스 및 개체에서 지원 하려는 다른 모든 인터페이스에서 파생 됩니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComObject:: CComObject](#ccomobject)|생성자입니다.|
|[CComObject:: ~ CComObject](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComObject:: AddRef](#addref)|개체의 참조 횟수를 증가 시킵니다.|
|[CComObject:: CreateInstance](#createinstance)|정적인 새 개체를 만듭니다 `CComObject` .|
|[CComObject:: QueryInterface](#queryinterface)|요청된 인터페이스에 대한 포인터를 검색합니다.|
|[CComObject:: Release](#release)|개체의 참조 횟수를 감소 시킵니다.|

## <a name="remarks"></a>설명

`CComObject` 집계할 때가 아닌 개체에 대해 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 을 구현 합니다. 그러나, 및에 대 한 호출은 `QueryInterface` `AddRef` `Release` 에 위임 됩니다 `CComObjectRootEx` .

를 사용 하는 방법에 대 한 자세한 내용은 `CComObject` [ATL COM 개체의 기본 사항](../../atl/fundamentals-of-atl-com-objects.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Base`

`CComObject`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomobjectaddref"></a><a name="addref"></a> CComObject:: AddRef

개체의 참조 횟수를 증가 시킵니다.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>반환 값

이 함수는 개체에 대 한 새 증가 된 참조 횟수를 반환 합니다. 이 값은 진단 또는 테스트에 유용할 수 있습니다.

## <a name="ccomobjectccomobject"></a><a name="ccomobject"></a> CComObject:: CComObject

생성자는 모듈 잠금 횟수를 증가 시킵니다.

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>매개 변수

<em>void\*</em><br/>
진행 이 명명 되지 않은 매개 변수는 사용 되지 않습니다. 다른 생성자와의 대칭을 위해 존재 `CComXXXObjectXXX` 합니다.

### <a name="remarks"></a>설명

소멸자는이를 감소 시킵니다.

연산자를 `CComObject` 사용 하 여 파생 개체가 성공적으로 생성 되 면 **`new`** 초기 참조 수는 0입니다. 참조 횟수를 적절 한 값 (1)으로 설정 하려면 [AddRef](#addref) 함수를 호출 합니다.

## <a name="ccomobjectccomobject"></a><a name="dtor"></a> CComObject:: ~ CComObject

소멸자입니다.

```
CComObject();
```

### <a name="remarks"></a>설명

할당 된 모든 리소스를 해제 하 고, 전체 [릴리스](ccomobjectrootex-class.md#finalrelease)를 호출 하 고, 모듈 잠금 횟수를 감소 시킵니다.

## <a name="ccomobjectcreateinstance"></a><a name="createinstance"></a> CComObject:: CreateInstance

이 정적 함수를 사용 하면  `Base` **>** [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)의 오버 헤드 없이 새 CComObject<개체를 만들 수 있습니다.

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>매개 변수

*페이지*<br/>
제한이 **CComObject<** 포인터에 대 한 포인터 `Base` **>** 입니다. `CreateInstance`가 실패 하면 *PP* 가 NULL로 설정 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

반환 된 개체의 참조 횟수는 0 이므로 `AddRef` 즉시 호출한 다음를 사용 하 여 `Release` 작업이 완료 되 면 개체 포인터에 대 한 참조를 해제 합니다.

개체에 직접 액세스할 필요가 없지만의 오버 헤드 없이 새 개체를 만들려면 `CoCreateInstance` [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) 를 대신 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

## <a name="ccomobjectqueryinterface"></a><a name="queryinterface"></a> CComObject:: QueryInterface

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

## <a name="ccomobjectrelease"></a><a name="release"></a> CComObject:: Release

개체의 참조 횟수를 감소 시킵니다.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>반환 값

이 함수는 개체에 대 한 새 감소 된 참조 횟수를 반환 합니다. 디버그 빌드에서 반환 값은 진단 또는 테스트에 유용할 수 있습니다. 디버그가 아닌 빌드에서는 `Release` 항상 0을 반환 합니다.

## <a name="see-also"></a>참고 항목

[CComAggObject 클래스](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPolyObject 클래스](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
