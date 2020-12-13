---
description: '자세히 알아보기: CDefaultCompareTraits 클래스'
title: CDefaultCompareTraits 클래스
ms.date: 11/04/2016
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
ms.openlocfilehash: dcb366cdcd99a6eed2b641be290ccc4913a81476
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141910"
---
# <a name="cdefaultcomparetraits-class"></a>CDefaultCompareTraits 클래스

이 클래스는 기본 요소 비교 함수를 제공 합니다.

## <a name="syntax"></a>구문

```
template<typename T>
class CDefaultCompareTraits
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
컬렉션에 저장 되는 데이터의 형식입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDefaultCompareTraits:: CompareElements](#compareelements)|정적인 두 요소가 같은지 비교 하려면이 함수를 호출 합니다.|
|[CDefaultCompareTraits:: CompareElementsOrdered](#compareelementsordered)|정적인 이 함수를 호출 하 여 더 크고 더 작은 요소를 확인 합니다.|

## <a name="remarks"></a>설명

이 클래스에는 컬렉션 클래스 개체에 저장 된 요소를 비교 하기 위한 두 개의 정적 함수가 포함 되어 있습니다. 이 클래스는 [Cdefaul지 수 Ement특성 클래스](../../atl/reference/cdefaultelementtraits-class.md)에서 활용 됩니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="cdefaultcomparetraitscompareelements"></a><a name="compareelements"></a> CDefaultCompareTraits:: CompareElements

두 요소가 같은지 비교 하려면이 함수를 호출 합니다.

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>매개 변수

*element1*<br/>
첫 번째 요소입니다.

*element2*<br/>
두 번째 요소입니다.

### <a name="return-value"></a>반환 값

요소가 같으면 true, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현은 같음 ( **==** ) 연산자입니다. 단순 데이터 형식이 아닌 개체의 경우에는이 함수를 재정의 해야 할 수 있습니다.

## <a name="cdefaultcomparetraitscompareelementsordered"></a><a name="compareelementsordered"></a> CDefaultCompareTraits:: CompareElementsOrdered

이 함수를 호출 하 여 더 크고 더 작은 요소를 확인 합니다.

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>매개 변수

*element1*<br/>
첫 번째 요소입니다.

*element2*<br/>
두 번째 요소입니다.

### <a name="return-value"></a>반환 값

다음 테이블을 기반으로 정수를 반환 합니다.

|조건|반환 값|
|---------------|------------------|
|*element1*  <  *element2*|<0|
|*element1*  ==  *element2*|0|
|*element1*  >  *element2*|>0|

### <a name="remarks"></a>설명

이 함수의 기본 구현에서는, 연산자를 사용 합니다 **==** **\<**, and **>** . 단순 데이터 형식이 아닌 개체의 경우에는이 함수를 재정의 해야 할 수 있습니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
