---
description: '자세히 알아보기: CComObjectGlobal 클래스'
title: CComObjectGlobal 클래스
ms.date: 11/04/2016
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
ms.openlocfilehash: 0f79acb0fdbb43f9456e08f26875d45eec9904c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151985"
---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal 클래스

이 클래스는 개체를 포함 하는 모듈에 대 한 참조 횟수를 관리 `Base` 합니다.

## <a name="syntax"></a>구문

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>매개 변수

*하단*<br/>
[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 또는 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)에서 파생 된 클래스와 개체에서 지원 하려는 다른 모든 인터페이스에서 파생 됩니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|생성자입니다.|
|[CComObjectGlobal:: ~ CComObjectGlobal](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComObjectGlobal:: AddRef](#addref)|전역을 구현 `AddRef` 합니다.|
|[CComObjectGlobal:: QueryInterface](#queryinterface)|전역을 구현 `QueryInterface` 합니다.|
|[CComObjectGlobal:: Release](#release)|전역을 구현 `Release` 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CComObjectGlobal:: m_hResFinalConstruct](#m_hresfinalconstruct)|개체를 생성 하는 동안 반환 된 HRESULT를 포함 `CComObjectGlobal` 합니다.|

## <a name="remarks"></a>설명

`CComObjectGlobal` 개체를 포함 하는 모듈에 대 한 참조 횟수를 관리 `Base` 합니다. `CComObjectGlobal` 모듈이 해제 되지 않는 한 개체가 삭제 되지 않도록 합니다. 전체 모듈의 참조 횟수가 0이 될 때만 개체가 제거 됩니다.

예를 들어를 사용 하 `CComObjectGlobal` 는 경우 클래스 팩터리는 모든 클라이언트에서 공유 하는 공통 전역 개체를 보유할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomobjectglobaladdref"></a><a name="addref"></a> CComObjectGlobal:: AddRef

개체의 참조 횟수를 1 씩 증가 시킵니다.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>반환 값

진단 및 테스트에 유용할 수 있는 값입니다.

### <a name="remarks"></a>설명

기본적으로 `AddRef` `_Module::Lock` 는를 호출 `_Module` 합니다. 여기서는 [CComModule](../../atl/reference/ccommodule-class.md) 의 전역 인스턴스이거나 여기에서 파생 된 클래스입니다.

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="ccomobjectglobal"></a> CComObjectGlobal::CComObjectGlobal

생성자입니다. 를 호출한 `FinalConstruct` 다음에서 반환 하는에 [m_hResFinalConstruct](#m_hresfinalconstruct) 을 설정 `HRESULT` `FinalConstruct` 합니다.

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>설명

[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)에서 기본 클래스를 파생 하지 않은 경우 고유한 메서드를 제공 해야 합니다 `FinalConstruct` . 이 소멸자는 `FinalRelease`을 호출합니다.

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="dtor"></a> CComObjectGlobal:: ~ CComObjectGlobal

소멸자입니다.

```
CComObjectGlobal();
```

### <a name="remarks"></a>설명

할당 된 모든 리소스를 해제 하 고, 전체 [릴리스](ccomobjectrootex-class.md#finalrelease)를 호출 합니다.

## <a name="ccomobjectglobalm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a> CComObjectGlobal:: m_hResFinalConstruct

개체를 생성 하는 동안를 호출 하는 HRESULT를 포함 `FinalConstruct` `CComObjectGlobal` 합니다.

```
HRESULT m_hResFinalConstruct;
```

## <a name="ccomobjectglobalqueryinterface"></a><a name="queryinterface"></a> CComObjectGlobal:: QueryInterface

요청 된 인터페이스 포인터에 대 한 포인터를 검색 합니다.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 요청 되는 인터페이스의 GUID입니다.

*ppvObject*<br/>
제한이 Iid로 식별 되는 인터페이스 포인터에 대 한 포인터 이거나, 인터페이스를 찾을 수 없는 경우 NULL입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

`QueryInterface`에서는 COM 맵 테이블의 인터페이스만 처리됩니다.

## <a name="ccomobjectglobalrelease"></a><a name="release"></a> CComObjectGlobal:: Release

개체의 참조 횟수를 1 씩 감소 시킵니다.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>반환 값

디버그 빌드에서는 `Release` 진단 및 테스트에 유용할 수 있는 값을 반환 합니다. 디버그가 아닌 빌드에서는 `Release` 항상 0을 반환 합니다.

### <a name="remarks"></a>설명

기본적으로 `Release` `_Module::Unlock` 는를 호출 `_Module` 합니다. 여기서는 [CComModule](../../atl/reference/ccommodule-class.md) 의 전역 인스턴스이거나 여기에서 파생 된 클래스입니다.

## <a name="see-also"></a>참고 항목

[CComObjectStack 클래스](../../atl/reference/ccomobjectstack-class.md)<br/>
[CComAggObject 클래스](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 클래스](../../atl/reference/ccomobject-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
