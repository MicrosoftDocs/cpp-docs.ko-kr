---
description: '자세히 알아보기: CStringElementTraitsI 클래스'
title: CStringElementTraitsI 클래스
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
ms.openlocfilehash: 0a626677f4a62805933b2effb4811394626374a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140403"
---
# <a name="cstringelementtraitsi-class"></a>CStringElementTraitsI 클래스

이 클래스는 컬렉션 클래스 개체에 저장 된 문자열과 관련 된 정적 함수를 제공 합니다. [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)와 유사 하지만 대/소문자를 구분 하지 않는 비교를 수행 합니다.

## <a name="syntax"></a>구문

```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>
class CStringElementTraitsI : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
컬렉션에 저장 되는 데이터의 형식입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CStringElementTraitsI:: INARGTYPE](#inargtype)|컬렉션 클래스 개체에 요소를 추가 하는 데 사용할 데이터 형식입니다.|
|[CStringElementTraitsI:: OUTARGTYPE](#outargtype)|컬렉션 클래스 개체에서 요소를 검색 하는 데 사용할 데이터 형식입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CStringElementTraitsI:: CompareElements](#compareelements)|대/소문자 차이를 무시 하 고 두 문자열 요소가 같은지 비교 하려면이 정적 함수를 호출 합니다.|
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|대/소문자 차이를 무시 하 고 두 문자열 요소를 비교 하려면이 정적 함수를 호출 합니다.|
|[CStringElementTraitsI:: Hash](#hash)|지정 된 문자열 요소에 대 한 해시 값을 계산 하려면이 정적 함수를 호출 합니다.|

## <a name="remarks"></a>설명

이 클래스는 문자열을 비교 하 고 해시 값을 만들기 위한 정적 함수를 제공 합니다. 이러한 함수는 컬렉션 클래스를 사용 하 여 문자열 기반 데이터를 저장할 때 유용 합니다. 문자열 개체가로 처리 되는 경우 [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) 를 사용 하 여 참조로 처리 합니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="cstringelementtraitsicompareelements"></a><a name="compareelements"></a> CStringElementTraitsI:: CompareElements

대/소문자 차이를 무시 하 고 두 문자열 요소가 같은지 비교 하려면이 정적 함수를 호출 합니다.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>매개 변수

*str1*<br/>
첫 번째 문자열 요소입니다.

*str2*<br/>
두 번째 문자열 요소입니다.

### <a name="return-value"></a>반환 값

요소가 같으면 true, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

비교는 대/소문자를 구분 하지 않습니다.

## <a name="cstringelementtraitsicompareelementsordered"></a><a name="compareelementsordered"></a> CStringElementTraitsI::CompareElementsOrdered

대/소문자 차이를 무시 하 고 두 문자열 요소를 비교 하려면이 정적 함수를 호출 합니다.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>매개 변수

*str1*<br/>
첫 번째 문자열 요소입니다.

*str2*<br/>
두 번째 문자열 요소입니다.

### <a name="return-value"></a>반환 값

문자열이 동일한 경우 0 <, *str1* 가 > *str2* 보다 작은 경우 0, *str1* 가 *str2* 보다 큰 경우 0입니다. [CStringT:: Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) 메서드는 비교를 수행 하는 데 사용 됩니다.

### <a name="remarks"></a>설명

비교는 대/소문자를 구분 하지 않습니다.

## <a name="cstringelementtraitsihash"></a><a name="hash"></a> CStringElementTraitsI:: Hash

지정 된 문자열 요소에 대 한 해시 값을 계산 하려면이 정적 함수를 호출 합니다.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>매개 변수

*str*<br/>
문자열 요소입니다.

### <a name="return-value"></a>반환 값

문자열의 내용을 사용 하 여 계산 된 해시 값을 반환 합니다.

## <a name="cstringelementtraitsiinargtype"></a><a name="inargtype"></a> CStringElementTraitsI:: INARGTYPE

컬렉션 클래스 개체에 요소를 추가 하는 데 사용할 데이터 형식입니다.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsioutargtype"></a><a name="outargtype"></a> CStringElementTraitsI:: OUTARGTYPE

컬렉션 클래스 개체에서 요소를 검색 하는 데 사용할 데이터 형식입니다.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>참고 항목

[CElementTraitsBase 클래스](../../atl/reference/celementtraitsbase-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[CStringElementTraits 클래스](../../atl/reference/cstringelementtraits-class.md)
