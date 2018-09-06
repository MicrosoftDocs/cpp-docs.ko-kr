---
title: CComObjectGlobal 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
dev_langs:
- C++
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4198e08a4c126a180006a088d4fc1509643824f6
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764932"
---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal 클래스

이 클래스는 포함 하는 모듈에서 참조 횟수를 관리 하 `Base` 개체입니다.

## <a name="syntax"></a>구문

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>매개 변수

*자료*  
파생 된 클래스 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 하거나 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)처럼 개체에서 지원 하려는 다른 모든 인터페이스 에서도 잘 합니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|생성자입니다.|
|[CComObjectGlobal:: ~ CComObjectGlobal](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComObjectGlobal::AddRef](#addref)|전역 구현 `AddRef`합니다.|
|[CComObjectGlobal::QueryInterface](#queryinterface)|전역 구현 `QueryInterface`합니다.|
|[CComObjectGlobal::Release](#release)|전역 구현 `Release`합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|이름|설명|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|생성 중 반환 된 HRESULT를 포함 합니다 `CComObjectGlobal` 개체입니다.|

## <a name="remarks"></a>설명

`CComObjectGlobal` 포함 하는 모듈에서 참조 횟수를 관리 하 여 `Base` 개체입니다. `CComObjectGlobal` 모듈은 릴리스되지으로 개체가 삭제 되지 않습니다 보장 합니다. 개체는 전체 모듈에 대 한 참조 횟수가 0이 되는 경우에 제거 됩니다.

예를 들어,를 사용 하 여 `CComObjectGlobal`, 클래스 팩터리는 모든 클라이언트에 의해 공유 되는 일반적인 전역 개체를 포함할 수 있습니다.

## <a name="inheritance-hierarchy"></a>상속 계층

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>요구 사항

**헤더:** atlcom.h

##  <a name="addref"></a>  CComObjectGlobal::AddRef

개체의 참조 개수 1 씩 증가 합니다.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>반환 값

진단에 유용 하 고 테스트 될 수 있는 값입니다.

### <a name="remarks"></a>설명

기본적으로 `AddRef` 호출 `_Module::Lock`, 여기서 `_Module` 의 인스턴스인 전역 [CComModule](../../atl/reference/ccommodule-class.md) 클래스에서 파생 된 또는 합니다.

##  <a name="ccomobjectglobal"></a>  CComObjectGlobal::CComObjectGlobal

생성자입니다. 호출 `FinalConstruct` 설정한 [m_hResFinalConstruct](#m_hresfinalconstruct) 에 `HRESULT` 반환한 `FinalConstruct`합니다.

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>설명

기본 클래스에서 파생 되지 않은 하는 경우 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)를 직접 제공 해야 `FinalConstruct` 메서드. 이 소멸자는 `FinalRelease`을 호출합니다.

##  <a name="dtor"></a>  CComObjectGlobal:: ~ CComObjectGlobal

소멸자입니다.

```
CComObjectGlobal();
```

### <a name="remarks"></a>설명

할당 된 모든 리소스 및 호출을 해제 [FinalRelease](ccomobjectrootex-class.md#finalrelease)합니다.

##  <a name="m_hresfinalconstruct"></a>  CComObjectGlobal::m_hResFinalConstruct

호출에서 hresult `FinalConstruct` 생성 하는 동안는 `CComObjectGlobal` 개체입니다.

```
HRESULT m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectGlobal::QueryInterface

요청 된 인터페이스 포인터에 대 한 포인터를 검색합니다.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>매개 변수

*iid*  
[in] 요청 된 인터페이스의 GUID입니다.

*ppvObject*  
[out] 인터페이스를 찾을 수 없으면 iid 또는 NULL로 식별 되는 인터페이스 포인터에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

`QueryInterface`에서는 COM 맵 테이블의 인터페이스만 처리됩니다.

##  <a name="release"></a>  CComObjectGlobal::Release

1 씩 개체의 참조 횟수를 감소 시킵니다.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>반환 값

디버그 빌드에서 `Release` 진단에 유용 하 고 테스트 될 수 있는 값을 반환 합니다. 디버그가 아닌 빌드에서 `Release` 항상 0을 반환 합니다.

### <a name="remarks"></a>설명

기본적으로 `Release` 호출 `_Module::Unlock`, 여기서 `_Module` 의 인스턴스인 전역 [CComModule](../../atl/reference/ccommodule-class.md) 클래스에서 파생 된 또는 합니다.

## <a name="see-also"></a>참고 항목

[CComObjectStack 클래스](../../atl/reference/ccomobjectstack-class.md)   
[CComAggObject 클래스](../../atl/reference/ccomaggobject-class.md)   
[CComObject 클래스](../../atl/reference/ccomobject-class.md)   
[클래스 개요](../../atl/atl-class-overview.md)
