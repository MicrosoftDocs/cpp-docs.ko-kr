---
description: '자세히 알아보기: CComQIPtrElementTraits 클래스'
title: CComQIPtrElementTraits 클래스
ms.date: 11/04/2016
f1_keywords:
- CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits::INARGTYPE
helpviewer_keywords:
- CComQIPtrElementTraits class
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
ms.openlocfilehash: 9aa96c5b926263d6ed58125a28f5d0a12d8107d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142339"
---
# <a name="ccomqiptrelementtraits-class"></a>CComQIPtrElementTraits 클래스

이 클래스는 COM 인터페이스 포인터의 컬렉션을 만들 때 유용한 메서드, 정적 함수 및 typedef를 제공 합니다.

## <a name="syntax"></a>구문

```
template<typename I, const IID* piid=& __uuidof(I)>
class CComQIPtrElementTraits :
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```

#### <a name="parameters"></a>매개 변수

*I*<br/>
저장할 포인터의 형식을 지정 하는 COM 인터페이스입니다.

*piid*<br/>
*I* 의 IID에 대 한 포인터입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CComQIPtrElementTraits:: INARGTYPE](#inargtype)|컬렉션 클래스 개체에 요소를 추가 하는 데 사용할 데이터 형식입니다.|

## <a name="remarks"></a>설명

이 클래스는 메서드를 파생 시키고 [CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM 인터페이스 포인터 개체의 컬렉션 클래스를 만들 때 유용한 typedef를 제공 합니다. 이 클래스는 [Cinterfacearray](../../atl/reference/cinterfacearray-class.md) 와 [cinterfacearray](../../atl/reference/cinterfacelist-class.md) 클래스 모두에서 활용 됩니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CComQIPtrElementTraits`

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="ccomqiptrelementtraitsinargtype"></a><a name="inargtype"></a> CComQIPtrElementTraits:: INARGTYPE

컬렉션 클래스 개체에 요소를 추가 하는 데 사용할 데이터 형식입니다.

```
typedef I* INARGTYPE;
```

## <a name="see-also"></a>참고 항목

[Cdefaul서 용 Ement특성 클래스](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
