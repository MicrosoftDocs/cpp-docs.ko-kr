---
description: '자세히 알아보기: CElementTraitsBase 클래스'
title: CElementTraitsBase 클래스
ms.date: 11/04/2016
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
ms.openlocfilehash: a200517e378cc3c3ca854ff60e9a49ac8e43d215
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141780"
---
# <a name="celementtraitsbase-class"></a>CElementTraitsBase 클래스

이 클래스는 컬렉션 클래스에 대 한 기본 복사 및 이동 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
template<typename T>
class CElementTraitsBase
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
컬렉션에 저장 되는 데이터의 형식입니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CElementTraitsBase:: INARGTYPE](#inargtype)|컬렉션 클래스 개체에 요소를 추가 하는 데 사용할 데이터 형식입니다.|
|[CElementTraitsBase:: OUTARGTYPE](#outargtype)|컬렉션 클래스 개체에서 요소를 검색 하는 데 사용할 데이터 형식입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CElementTraitsBase:: CopyElements](#copyelements)|컬렉션 클래스 개체에 저장 된 요소를 복사 하려면이 메서드를 호출 합니다.|
|[CElementTraitsBase::RelocateElements](#relocateelements)|컬렉션 클래스 개체에 저장 된 요소를 재배치 하려면이 메서드를 호출 합니다.|

## <a name="remarks"></a>설명

이 기본 클래스는 컬렉션 클래스에서 요소를 복사 하 고 재배치 하기 위한 메서드를 정의 합니다. [CdefaulCStringRefElementTraits Ement특성](../../atl/reference/cdefaultelementtraits-class.md), [](../../atl/reference/cstringrefelementtraits-class.md)및 [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)클래스에서 활용 됩니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="celementtraitsbasecopyelements"></a><a name="copyelements"></a> CElementTraitsBase:: CopyElements

컬렉션 클래스 개체에 저장 된 요소를 복사 하려면이 메서드를 호출 합니다.

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

## <a name="celementtraitsbaseinargtype"></a><a name="inargtype"></a> CElementTraitsBase:: INARGTYPE

컬렉션에 요소를 추가 하는 데 사용할 데이터 형식입니다.

```
typedef const T& INARGTYPE;
```

## <a name="celementtraitsbaseoutargtype"></a><a name="outargtype"></a> CElementTraitsBase:: OUTARGTYPE

컬렉션에서 요소를 검색 하는 데 사용할 데이터 형식입니다.

```
typedef T& OUTARGTYPE;
```

## <a name="celementtraitsbaserelocateelements"></a><a name="relocateelements"></a> CElementTraitsBase::RelocateElements

컬렉션 클래스 개체에 저장 된 요소를 재배치 하려면이 메서드를 호출 합니다.

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

이 메서드는 대부분의 데이터 형식에 충분 한 [memmove](../../c-runtime-library/reference/memmove-wmemmove.md)를 호출 합니다. 이동 하는 개체에 해당 멤버에 대 한 포인터가 포함 되어 있는 경우이 메서드를 재정의 해야 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
