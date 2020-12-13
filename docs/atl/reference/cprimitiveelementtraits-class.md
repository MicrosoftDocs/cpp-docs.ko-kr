---
description: '자세히 알아보기: CPrimitiveElementTraits 클래스'
title: CPrimitiveElementTraits 클래스
ms.date: 11/04/2016
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
ms.openlocfilehash: a9a47d9e6268ee6cc858d85e9236b00c270e8841
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141078"
---
# <a name="cprimitiveelementtraits-class"></a>CPrimitiveElementTraits 클래스

이 클래스는 기본 데이터 형식으로 구성 된 컬렉션 클래스에 대 한 기본 메서드 및 함수를 제공 합니다.

## <a name="syntax"></a>구문

```
template <typename T>
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
컬렉션 클래스 개체에 저장 되는 데이터의 형식입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CPrimitiveElementTraits:: INARGTYPE](#inargtype)|컬렉션 클래스 개체에 요소를 추가 하는 데 사용할 데이터 형식입니다.|
|[CPrimitiveElementTraits:: OUTARGTYPE](#outargtype)|컬렉션 클래스 개체에서 요소를 검색 하는 데 사용할 데이터 형식입니다.|

## <a name="remarks"></a>설명

이 클래스는 컬렉션 클래스 개체에 저장 된 기본 데이터 형식 요소를 이동, 복사, 비교 및 해시 하기 위한 기본 정적 함수 및 메서드를 제공 합니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CPrimitiveElementTraits`

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="cprimitiveelementtraitsinargtype"></a><a name="inargtype"></a> CPrimitiveElementTraits:: INARGTYPE

컬렉션 클래스 개체에 요소를 추가 하는 데 사용할 데이터 형식입니다.

```
typedef T INARGTYPE;
```

## <a name="cprimitiveelementtraitsoutargtype"></a><a name="outargtype"></a> CPrimitiveElementTraits:: OUTARGTYPE

컬렉션 클래스 개체에서 요소를 검색 하는 데 사용할 데이터 형식입니다.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>참고 항목

[Cdefaul서 용 Ement특성 클래스](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
