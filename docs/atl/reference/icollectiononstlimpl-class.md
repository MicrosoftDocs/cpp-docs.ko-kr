---
description: '자세히 알아보기: ICollectionOnSTLImpl 클래스'
title: ICollectionOnSTLImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl::get__NewEnum
- ATLCOM/ATL::ICollectionOnSTLImpl::getcount
- ATLCOM/ATL::ICollectionOnSTLImpl::get_Item
- ATLCOM/ATL::ICollectionOnSTLImpl::m_coll
helpviewer_keywords:
- ICollectionOnSTLImpl class
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
ms.openlocfilehash: 089fc0fbd8f410d740646e2a653b076d32448647
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139609"
---
# <a name="icollectiononstlimpl-class"></a>ICollectionOnSTLImpl 클래스

이 클래스는 컬렉션 클래스에서 사용 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
COM 컬렉션 인터페이스입니다.

*CollType*<br/>
C + + 표준 라이브러리 컨테이너 클래스입니다.

*ItemType*<br/>
컨테이너 인터페이스에 의해 노출 되는 항목의 형식입니다.

*CopyItem*<br/>
[복사 정책 클래스](../../atl/atl-copy-policy-classes.md)입니다.

*EnumType*<br/>
[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)호환 되는 열거자 클래스입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[ICollectionOnSTLImpl:: get__NewEnum](#newenum)|컬렉션에 대 한 열거자 개체를 반환 합니다.|
|[ICollectionOnSTLImpl:: getcount](#get_count)|컬렉션의 요소 수를 반환 합니다.|
|[ICollectionOnSTLImpl:: get_Item](#get_item)|컬렉션에서 요청 된 항목을 반환 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[ICollectionOnSTLImpl:: m_coll](#m_coll)|컬렉션입니다.|

## <a name="remarks"></a>설명

이 클래스는 컬렉션 인터페이스의 세 가지 메서드인 [getcount](#get_count), [get_Item](#get_item)및 [get__NewEnum](#newenum)에 대 한 구현을 제공 합니다.

이 클래스를 사용 하려면 다음을 수행 합니다.

- 구현 하려는 컬렉션 인터페이스를 정의 (또는 빌려) 합니다.

- `ICollectionOnSTLImpl`이 컬렉션 인터페이스를 기반으로 하는의 특수화에서 클래스를 파생 시킵니다.

- 파생 클래스를 사용 하 여에서 처리 하지 않는 컬렉션 인터페이스에서 메서드를 구현 `ICollectionOnSTLImpl` 합니다.

> [!NOTE]
> 컬렉션 인터페이스가 이중 인터페이스인 경우 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md)에서 클래스를 파생 하 여 `ICollectionOnSTLImpl` ATL이 메서드의 구현을 제공 하 게 하려면 첫 번째 템플릿 매개 변수로 특수화를 전달 합니다 `IDispatch` .

- [M_coll](#m_coll) 멤버에 항목을 추가 하 여 컬렉션을 채웁니다.

자세한 내용 및 예제는 [ATL 컬렉션 및 열거자](../../atl/atl-collections-and-enumerators.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="icollectiononstlimplgetcount"></a><a name="get_count"></a> ICollectionOnSTLImpl:: getcount

이 메서드는 컬렉션의 항목 수를 반환 합니다.

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>매개 변수

*pcount*<br/>
제한이 컬렉션의 요소 수입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

## <a name="icollectiononstlimplget_item"></a><a name="get_item"></a> ICollectionOnSTLImpl:: get_Item

이 메서드는 컬렉션에서 지정 된 항목을 반환 합니다.

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>매개 변수

*Index*<br/>
진행 컬렉션에 있는 항목의 인덱스 (1부터 기반)입니다.

*pvar*<br/>
제한이 *인덱스* 에 해당 하는 항목입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

항목은 특수화에서 템플릿 인수로 전달 된 [복사 정책 클래스](../../atl/atl-copy-policy-classes.md) 의 copy 메서드를 사용 하 여 [m_coll](#m_coll) 의 지정 된 위치에 있는 데이터를 복사 하 여 가져옵니다 `ICollectionOnSTLImpl` .

## <a name="icollectiononstlimplget__newenum"></a><a name="newenum"></a> ICollectionOnSTLImpl:: get__NewEnum

컬렉션에 대 한 열거자 개체를 반환 합니다.

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>매개 변수

*ppUnk*<br/>
제한이 새로 만든 열거자 개체의 **IUnknown** 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

새로 만든 열거자는 원래 컬렉션에 대 한 반복기를 유지 관리 합니다 `m_coll` (복사는 수행 되지 않음). 컬렉션 개체에 대 한 COM 참조를 보유 하 여 처리 중인 열거자가 있는 동안 컬렉션이 활성 상태로 유지 되도록 합니다.

## <a name="icollectiononstlimplm_coll"></a><a name="m_coll"></a> ICollectionOnSTLImpl:: m_coll

이 멤버는 컬렉션으로 표시 되는 항목을 포함 합니다.

```
CollType m_coll;
```

## <a name="see-also"></a>참고 항목

[이 컬렉션 샘플](../../overview/visual-cpp-samples.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
