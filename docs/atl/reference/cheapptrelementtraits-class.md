---
description: '자세히 알아보기: CHeapPtrElementTraits 클래스'
title: CHeapPtrElementTraits 클래스
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
ms.openlocfilehash: 7ca3d194a284f06e6b5baa0530cb49bc93d8510a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141611"
---
# <a name="cheapptrelementtraits-class"></a>CHeapPtrElementTraits 클래스

이 클래스는 힙 포인터의 컬렉션을 만들 때 유용한 메서드, 정적 함수 및 typedef를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<typename T, class Allocator = ATL::CCRTAllocator>
class CHeapPtrElementTraits :
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
컬렉션 클래스에 저장 되는 개체 형식입니다.

*할당자*<br/>
사용할 메모리 할당 클래스입니다. 기본값은 [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CHeapPtrElementTraits:: INARGTYPE](#inargtype)|컬렉션 클래스 개체에 요소를 추가 하는 데 사용할 데이터 형식입니다.|
|[CHeapPtrElementTraits:: OUTARGTYPE](#outargtype)|컬렉션 클래스 개체에서 요소를 검색 하는 데 사용할 데이터 형식입니다.|

## <a name="remarks"></a>설명

이 클래스는 힙 포인터를 포함 하는 컬렉션 클래스 개체의 생성을 구체적 하기 위한 메서드, 정적 함수 및 형식 정의를 제공 합니다. 클래스는 `CHeapPtrList` 에서 파생 `CHeapPtrElementTraits` 됩니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CHeapPtrElementTraits`

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="cheapptrelementtraitsinargtype"></a><a name="inargtype"></a> CHeapPtrElementTraits:: INARGTYPE

컬렉션 클래스 개체에 요소를 추가 하는 데 사용할 데이터 형식입니다.

```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```

## <a name="cheapptrelementtraitsoutargtype"></a><a name="outargtype"></a> CHeapPtrElementTraits:: OUTARGTYPE

컬렉션 클래스 개체에서 요소를 검색 하는 데 사용할 데이터 형식입니다.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>참고 항목

[Cdefaul서 용 Ement특성 클래스](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CComHeapPtr 클래스](../../atl/reference/ccomheapptr-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
