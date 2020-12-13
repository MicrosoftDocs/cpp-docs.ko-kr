---
description: '자세히 알아보기: CComObjectNoLock 클래스'
title: CComObjectNoLock 클래스
ms.date: 11/04/2016
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
ms.openlocfilehash: 97708250ecd9637c52daf5db82f39d1a12565399
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142495"
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock 클래스

이 클래스 `IUnknown` 는 집계 되지 않은 개체에 대해를 구현 하지만 생성자에서 모듈 잠금 수를 증가 시 지 않습니다.

## <a name="syntax"></a>구문

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>매개 변수

*하단*<br/>
[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 또는 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)에서 파생 된 클래스와 개체에서 지원 하려는 다른 모든 인터페이스에서 파생 됩니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|생성자입니다.|
|[CComObjectNoLock:: ~ CComObjectNoLock](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CComObjectNoLock:: AddRef](#addref)|개체의 참조 횟수를 증가 시킵니다.|
|[CComObjectNoLock:: QueryInterface](#queryinterface)|요청 된 인터페이스에 대 한 포인터를 반환 합니다.|
|[CComObjectNoLock:: Release](#release)|개체의 참조 횟수를 감소 시킵니다.|

## <a name="remarks"></a>설명

`CComObjectNoLock`는 집계할 수 없는 개체에 대해 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 을 구현 한다는 점에서 [CComObject](../../atl/reference/ccomobject-class.md) 와 비슷합니다. 그러나는 `CComObjectNoLock` 생성자에서 모듈 잠금 횟수를 증가 시 지 않습니다.

ATL은 `CComObjectNoLock` 클래스 팩터리에 대해 내부적으로를 사용 합니다. 일반적으로이 클래스는 직접 사용 하지 않습니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ccomobjectnolockaddref"></a><a name="addref"></a> CComObjectNoLock:: AddRef

개체의 참조 횟수를 증가 시킵니다.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>반환 값

진단 또는 테스트에 유용할 수 있는 값입니다.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="ccomobjectnolock"></a> CComObjectNoLock::CComObjectNoLock

생성자입니다. [CComObject](../../atl/reference/ccomobject-class.md)와 달리는 모듈 잠금 횟수를 증가 시 지 않습니다.

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>매개 변수

<em>void\*</em><br/>
진행 이 명명 되지 않은 매개 변수는 사용 되지 않습니다. 다른 생성자와의 대칭을 위해 존재 `CComXXXObjectXXX` 합니다.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="dtor"></a> CComObjectNoLock:: ~ CComObjectNoLock

소멸자입니다.

```
~CComObjectNoLock();
```

### <a name="remarks"></a>설명

할당 된 모든 리소스를 해제 하 고, 전체 [릴리스](ccomobjectrootex-class.md#finalrelease)를 호출 합니다.

## <a name="ccomobjectnolockqueryinterface"></a><a name="queryinterface"></a> CComObjectNoLock:: QueryInterface

요청된 인터페이스에 대한 포인터를 검색합니다.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>매개 변수

*iid*<br/>
진행 요청 되는 인터페이스의 식별자입니다.

*ppvObject*<br/>
제한이 *Iid* 로 식별 되는 인터페이스 포인터에 대 한 포인터입니다. 개체가이 인터페이스를 지원 하지 않으면 *Ppvobject* 가 NULL로 설정 됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="ccomobjectnolockrelease"></a><a name="release"></a> CComObjectNoLock:: Release

개체의 참조 횟수를 감소 시킵니다.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>반환 값

디버그 빌드에서는 `Release` 진단 또는 테스트에 유용할 수 있는 값을 반환 합니다. 디버그가 아닌 빌드에서는 `Release` 항상 0을 반환 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
