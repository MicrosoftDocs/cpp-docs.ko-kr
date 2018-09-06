---
title: ICollectionOnSTLImpl 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl::get__NewEnum
- ATLCOM/ATL::ICollectionOnSTLImpl::getcount
- ATLCOM/ATL::ICollectionOnSTLImpl::get_Item
- ATLCOM/ATL::ICollectionOnSTLImpl::m_coll
dev_langs:
- C++
helpviewer_keywords:
- ICollectionOnSTLImpl class
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6bbfb34d34f6bd920744621042f5f3e09143e896
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751321"
---
# <a name="icollectiononstlimpl-class"></a>ICollectionOnSTLImpl 클래스

이 클래스는 컬렉션 클래스에 의해 사용 되는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>  
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>매개 변수

*T*  
COM 컬렉션 인터페이스입니다.

*CollType*  
C + + 표준 라이브러리 컨테이너 클래스입니다.

*ItemType*  
컨테이너 인터페이스에 의해 노출 되는 항목의 형식입니다.

*CopyItem*  
A [복사 정책 클래스](../../atl/atl-copy-policy-classes.md)합니다.

*EnumType*  
A [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)-호환 열거자 클래스입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[ICollectionOnSTLImpl::get__NewEnum](#newenum)|컬렉션에 대 한 열거자 개체를 반환합니다.|
|[ICollectionOnSTLImpl::getcount](#get_count)|컬렉션의 요소 수를 반환합니다.|
|[ICollectionOnSTLImpl::get_Item](#get_item)|컬렉션에서 요청된 된 항목을 반환합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|이름|설명|
|----------|-----------------|
|[ICollectionOnSTLImpl::m_coll](#m_coll)|컬렉션입니다.|

## <a name="remarks"></a>설명

이 클래스는 컬렉션 인터페이스의 세 가지 방법에 대 한 구현을 제공 합니다. [getcount](#get_count)를 [get_Item](#get_item), 및 [get__NewEnum](#newenum)합니다.

이 클래스를 사용 합니다.

- 컬렉션 인터페이스를 구현 정의 (또는 차용) 합니다.

- 특수화에서 클래스를 파생 `ICollectionOnSTLImpl` 이 컬렉션 인터페이스를 기반으로 합니다.

- 파생된 클래스에서 처리 되지 않은 컬렉션 인터페이스에서 메서드를 구현 하는 데 `ICollectionOnSTLImpl`합니다.

> [!NOTE]
>  컬렉션 인터페이스 이면 이중 인터페이스에서 클래스를 파생 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md)전달 된 `ICollectionOnSTLImpl` ATL의 구현을 제공 하도록 하려는 경우 첫 번째 템플릿 매개 변수로 특수화는 `IDispatch` 메서드입니다.

- 항목을 추가 합니다 [m_coll](#m_coll) 컬렉션을 채우는 데는 멤버입니다.

자세한 내용 및 예제를 참조 하세요 [ATL 컬렉션 및 열거자](../../atl/atl-collections-and-enumerators.md)합니다.

## <a name="inheritance-hierarchy"></a>상속 계층

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>요구 사항

**헤더:** atlcom.h

##  <a name="get_count"></a>  ICollectionOnSTLImpl::getcount

이 메서드는 컬렉션의 항목 수를 반환합니다.

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>매개 변수

*pcount*  
[out] 컬렉션의 요소 수입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

##  <a name="get_item"></a>  ICollectionOnSTLImpl::get_Item

이 메서드는 컬렉션에서 지정된 된 항목을 반환합니다.

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>매개 변수

*Index*  
[in] 컬렉션에 있는 항목의 인덱스 1부터 시작 합니다.

*pvar*  
[out] 에 해당 하는 항목 *인덱스*합니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

항목의 지정한 위치에서 데이터를 복사 하 여 가져온 [m_coll](#m_coll) 복사 메서드를 사용 하는 [복사 정책 클래스](../../atl/atl-copy-policy-classes.md) 의 템플릿 인수로 전달 되는 `ICollectionOnSTLImpl` 특수화 합니다.

##  <a name="newenum"></a>  ICollectionOnSTLImpl::get__NewEnum

컬렉션에 대 한 열거자 개체를 반환합니다.

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>매개 변수

*ppUnk*  
[out] 합니다 **IUnknown** 새로 만든된 열거자 개체의 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

원래 컬렉션에 반복기를 유지 하는 새로 만든된 열거자 `m_coll`(따라서 복사본이 생성 됨), 컬렉션 처리 되지 않은 열거자 있기는 활성 상태로 유지 하기 위해 컬렉션 개체에 대 한 COM 참조를 보유 하 고 있습니다.

##  <a name="m_coll"></a>  ICollectionOnSTLImpl::m_coll

이 멤버는 컬렉션을 나타내는 항목을 보유 합니다.

```
CollType m_coll;
```

## <a name="see-also"></a>참고 항목

[ATLCollections 샘플](../../visual-cpp-samples.md)   
[클래스 개요](../../atl/atl-class-overview.md)
