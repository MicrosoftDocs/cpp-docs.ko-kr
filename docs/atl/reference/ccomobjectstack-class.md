---
description: '자세히 알아보기: CComObjectStack 클래스'
title: CComObjectStack 클래스
ms.date: 11/04/2016
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
ms.openlocfilehash: 5713601a765ad9ff1c32992d1f9c517dd86affca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142417"
---
# <a name="ccomobjectstack-class"></a>CComObjectStack 클래스

이 클래스는 임시 COM 개체를 만들고의 기초 구현을 제공 `IUnknown` 합니다.

## <a name="syntax"></a>구문

```
template <class  Base>
class CComObjectStack : public Base
```

#### <a name="parameters"></a>매개 변수

*하단*<br/>
[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 또는 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)에서 파생 된 클래스와 개체에서 지원 하려는 다른 모든 인터페이스에서 파생 됩니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|생성자입니다.|
|[CComObjectStack:: ~ CComObjectStack](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComObjectStack:: AddRef](#addref)|0을 반환합니다. 디버그 모드에서를 호출 `_ASSERTE` 합니다.|
|[CComObjectStack:: QueryInterface](#queryinterface)|E_NOINTERFACE를 반환 합니다. 디버그 모드에서를 호출 `_ASSERTE` 합니다.|
|[CComObjectStack:: Release](#release)|0을 반환합니다. 디버그 모드에서를 호출 `_ASSERTE` 합니다. ~|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComObjectStack:: m_hResFinalConstruct](#m_hresfinalconstruct)|개체를 생성 하는 동안 반환 된 HRESULT를 포함 `CComObjectStack` 합니다.|

## <a name="remarks"></a>설명

`CComObjectStack` 는 임시 COM 개체를 만들고 개체에의 기초 구현을 제공 하는 데 사용 됩니다 `IUnknown` . 일반적으로 개체는 한 함수에서 지역 변수로 사용 됩니다. 즉, 스택으로 푸시됩니다. 함수가 완료 되 면 개체가 소멸 되므로 효율성을 높이기 위해 참조 계산이 수행 되지 않습니다.

다음 예제에서는 함수 내에서 사용 되는 COM 개체를 만드는 방법을 보여 줍니다.

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

임시 개체가 `Tempobj` 스택에 푸시되 고 함수가 완료 되 면 자동으로 사라집니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Base`

`CComObjectStack`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomobjectstackaddref"></a><a name="addref"></a> CComObjectStack:: AddRef

0을 반환합니다.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>반환 값

0을 반환합니다.

### <a name="remarks"></a>설명

디버그 모드에서를 호출 `_ASSERTE` 합니다.

## <a name="ccomobjectstackccomobjectstack"></a><a name="ccomobjectstack"></a> CComObjectStack::CComObjectStack

생성자입니다.

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>설명

를 호출한 `FinalConstruct` 다음에서 반환 된 HRESULT로 [m_hResFinalConstruct](#m_hresfinalconstruct) 을 설정 `FinalConstruct` 합니다. [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)에서 기본 클래스를 파생 하지 않은 경우 고유한 메서드를 제공 해야 합니다 `FinalConstruct` . 이 소멸자는 `FinalRelease`을 호출합니다.

## <a name="ccomobjectstackccomobjectstack"></a><a name="dtor"></a> CComObjectStack:: ~ CComObjectStack

소멸자입니다.

```
CComObjectStack();
```

### <a name="remarks"></a>설명

할당 된 모든 리소스를 해제 하 고, 전체 [릴리스](ccomobjectrootex-class.md#finalrelease)를 호출 합니다.

## <a name="ccomobjectstackm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a> CComObjectStack:: m_hResFinalConstruct

개체를 생성 하는 동안 호출에서 반환 된 HRESULT를 포함 `FinalConstruct` `CComObjectStack` 합니다.

```
HRESULT    m_hResFinalConstruct;
```

## <a name="ccomobjectstackqueryinterface"></a><a name="queryinterface"></a> CComObjectStack:: QueryInterface

E_NOINTERFACE를 반환 합니다.

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>반환 값

E_NOINTERFACE를 반환 합니다.

### <a name="remarks"></a>설명

디버그 모드에서를 호출 `_ASSERTE` 합니다.

## <a name="ccomobjectstackrelease"></a><a name="release"></a> CComObjectStack:: Release

0을 반환합니다.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>반환 값

0을 반환합니다.

### <a name="remarks"></a>설명

디버그 모드에서를 호출 `_ASSERTE` 합니다.

## <a name="see-also"></a>참고 항목

[CComAggObject 클래스](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 클래스](../../atl/reference/ccomobject-class.md)<br/>
[CComObjectGlobal 클래스](../../atl/reference/ccomobjectglobal-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
