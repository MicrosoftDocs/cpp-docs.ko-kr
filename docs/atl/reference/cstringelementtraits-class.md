---
description: '자세히 알아보기: CStringElementTraits 클래스'
title: CStringElementTraits 클래스
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits::INARGTYPE
- CSTRINGT/ATL::CStringElementTraits::OUTARGTYPE
- CSTRINGT/ATL::CStringElementTraits::CompareElements
- CSTRINGT/ATL::CStringElementTraits::CompareElementsOrdered
- CSTRINGT/ATL::CStringElementTraits::CopyElements
- CSTRINGT/ATL::CStringElementTraits::Hash
- CSTRINGT/ATL::CStringElementTraits::RelocateElements
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
ms.openlocfilehash: 1e3f6a73e71530250d9dd88408165471028a18e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140493"
---
# <a name="cstringelementtraits-class"></a>CStringElementTraits 클래스

이 클래스는 개체를 저장 하는 컬렉션 클래스에서 사용 하는 정적 함수를 제공 `CString` 합니다.

## <a name="syntax"></a>구문

```
template <typename T>
class CStringElementTraits
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
컬렉션에 저장 되는 데이터의 형식입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CStringElementTraits:: INARGTYPE](#inargtype)|컬렉션 클래스 개체에 요소를 추가 하는 데 사용할 데이터 형식입니다.|
|[CStringElementTraits:: OUTARGTYPE](#outargtype)|컬렉션 클래스 개체에서 요소를 검색 하는 데 사용할 데이터 형식입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CStringElementTraits:: CompareElements](#compareelements)|정적인 두 문자열 요소가 같은지 비교 하려면이 함수를 호출 합니다.|
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|정적인 두 문자열 요소를 비교 하려면이 함수를 호출 합니다.|
|[CStringElementTraits:: CopyElements](#copyelements)|정적인 `CString` 컬렉션 클래스 개체에 저장 된 요소를 복사 하려면이 함수를 호출 합니다.|
|[CStringElementTraits:: Hash](#hash)|정적인 지정 된 문자열 요소에 대 한 해시 값을 계산 하려면이 함수를 호출 합니다.|
|[CStringElementTraits::RelocateElements](#relocateelements)|정적인 `CString` 컬렉션 클래스 개체에 저장 된 요소를 재배치 하려면이 함수를 호출 합니다.|

## <a name="remarks"></a>설명

이 클래스는 문자열을 복사, 이동 및 비교 하 고 해시 값을 만들기 위한 정적 함수를 제공 합니다. 이러한 함수는 컬렉션 클래스를 사용 하 여 문자열 기반 데이터를 저장할 때 유용 합니다. 대/소문자를 구분 하지 않는 비교를 수행 해야 하는 경우 [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) 를 사용 합니다. 문자열 개체를 참조로 처리할 때 [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) 를 사용 합니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** cstringt. h

## <a name="cstringelementtraitscompareelements"></a><a name="compareelements"></a> CStringElementTraits:: CompareElements

두 문자열 요소가 같은지 비교 하려면이 정적 함수를 호출 합니다.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>매개 변수

*str1*<br/>
첫 번째 문자열 요소입니다.

*str2*<br/>
두 번째 문자열 요소입니다.

### <a name="return-value"></a>반환 값

요소가 같으면 true, 그렇지 않으면 false를 반환 합니다.

## <a name="cstringelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a> CStringElementTraits::CompareElementsOrdered

두 문자열 요소를 비교 하려면이 정적 함수를 호출 합니다.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>매개 변수

*str1*<br/>
첫 번째 문자열 요소입니다.

*str2*<br/>
두 번째 문자열 요소입니다.

### <a name="return-value"></a>반환 값

문자열이 동일한 경우 0 <, *str1* 가 > *str2* 보다 작은 경우 0, *str1* 가 *str2* 보다 큰 경우 0입니다. [CStringT:: Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) 메서드는 비교를 수행 하는 데 사용 됩니다.

## <a name="cstringelementtraitscopyelements"></a><a name="copyelements"></a> CStringElementTraits:: CopyElements

`CString`컬렉션 클래스 개체에 저장 된 요소를 복사 하려면이 정적 함수를 호출 합니다.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>매개 변수

*pDest*<br/>
복사한 데이터를 수신 하는 첫 번째 요소에 대 한 포인터입니다.

*.Psrc*<br/>
복사할 첫 번째 요소에 대 한 포인터입니다.

*nElements*<br/>
복사할 요소의 수입니다.

### <a name="remarks"></a>설명

원본 및 대상 요소는 겹칠 수 없습니다.

## <a name="cstringelementtraitshash"></a><a name="hash"></a> CStringElementTraits:: Hash

지정 된 문자열 요소에 대 한 해시 값을 계산 하려면이 정적 함수를 호출 합니다.

```
static ULONG Hash(INARGTYPE str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
문자열 요소입니다.

### <a name="return-value"></a>반환 값

문자열의 내용을 사용 하 여 계산 된 해시 값을 반환 합니다.

## <a name="cstringelementtraitsinargtype"></a><a name="inargtype"></a> CStringElementTraits:: INARGTYPE

컬렉션 클래스 개체에 요소를 추가 하는 데 사용할 데이터 형식입니다.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsoutargtype"></a><a name="outargtype"></a> CStringElementTraits:: OUTARGTYPE

컬렉션 클래스 개체에서 요소를 검색 하는 데 사용할 데이터 형식입니다.

```
typedef T& OUTARGTYPE;
```

## <a name="cstringelementtraitsrelocateelements"></a><a name="relocateelements"></a> CStringElementTraits::RelocateElements

`CString`컬렉션 클래스 개체에 저장 된 요소를 재배치 하려면이 정적 함수를 호출 합니다.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>매개 변수

*pDest*<br/>
재배치 된 데이터를 수신 하는 첫 번째 요소에 대 한 포인터입니다.

*.Psrc*<br/>
재배치할 첫 번째 요소에 대 한 포인터입니다.

*nElements*<br/>
재배치할 요소의 수입니다.

### <a name="remarks"></a>설명

이 정적 함수는 [memmove](../../c-runtime-library/reference/memmove-wmemmove.md)를 호출 하며, 대부분의 데이터 형식에는 충분 합니다. 이동 하는 개체에 해당 멤버에 대 한 포인터가 포함 되어 있으면이 정적 함수를 재정의 해야 합니다.

## <a name="see-also"></a>참고 항목

[CElementTraitsBase 클래스](../../atl/reference/celementtraitsbase-class.md)<br/>
[CStringElementTraitsI 클래스](../../atl/reference/cstringelementtraitsi-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
