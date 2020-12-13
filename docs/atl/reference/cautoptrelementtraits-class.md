---
description: '자세히 알아보기: CAutoPtrElementTraits 클래스'
title: CAutoPtrElementTraits 클래스
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
ms.openlocfilehash: 2478f8251f0094aaa5cabf1c0dcc873c9c526cd8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147136"
---
# <a name="cautoptrelementtraits-class"></a>CAutoPtrElementTraits 클래스

이 클래스는 스마트 포인터의 컬렉션을 만들 때 유용한 메서드, 정적 함수 및 typedef를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<typename T>
class CAutoPtrElementTraits
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
포인터 형식입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CAutoPtrElementTraits:: INARGTYPE](#inargtype)|컬렉션 클래스 개체에 요소를 추가 하는 데 사용할 데이터 형식입니다.|
|[CAutoPtrElementTraits:: OUTARGTYPE](#outargtype)|컬렉션 클래스 개체에서 요소를 검색 하는 데 사용할 데이터 형식입니다.|

## <a name="remarks"></a>설명

이 클래스는 스마트 포인터를 포함 하는 컬렉션 클래스 개체의 생성을 구체적 하기 위한 메서드, 정적 함수 및 형식 정의를 제공 합니다. [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) 및 [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) 클래스는에서 파생 `CAutoPtrElementTraits` 됩니다. Vector new 및 delete 연산자를 필요로 하는 스마트 포인터 컬렉션을 빌드하는 경우 대신 [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) 를 사용 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoPtrElementTraits`

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="cautoptrelementtraitsinargtype"></a><a name="inargtype"></a> CAutoPtrElementTraits:: INARGTYPE

컬렉션 클래스 개체에 요소를 추가 하는 데 사용할 데이터 형식입니다.

```
typedef CAutoPtr<T>& INARGTYPE;
```

## <a name="cautoptrelementtraitsoutargtype"></a><a name="outargtype"></a> CAutoPtrElementTraits:: OUTARGTYPE

컬렉션 클래스 개체에서 요소를 검색 하는 데 사용할 데이터 형식입니다.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>참고 항목

[Cdefaul서 용 Ement특성 클래스](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
