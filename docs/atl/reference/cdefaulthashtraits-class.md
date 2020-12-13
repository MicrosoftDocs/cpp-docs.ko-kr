---
description: '자세한 정보: CDefaultHashTraits 클래스'
title: CDefaultHashTraits 클래스
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: 85cc881466be03931d435d91a48548456d74305b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141884"
---
# <a name="cdefaulthashtraits-class"></a>CDefaultHashTraits 클래스

이 클래스는 해시 값을 계산 하는 정적 함수를 제공 합니다.

## <a name="syntax"></a>구문

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
컬렉션에 저장 되는 데이터의 형식입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDefaultHashTraits:: Hash](#hash)|정적인 지정 된 요소에 대 한 해시 값을 계산 하려면이 함수를 호출 합니다.|

## <a name="remarks"></a>설명

이 클래스에는 지정 된 요소에 대 한 해시 값을 반환 하는 단일 정적 함수가 포함 되어 있습니다. 이 클래스는 [Cdefaul지 수 Ement특성 클래스](../../atl/reference/cdefaultelementtraits-class.md)에서 활용 됩니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="cdefaulthashtraitshash"></a><a name="hash"></a> CDefaultHashTraits:: Hash

지정 된 요소에 대 한 해시 값을 계산 하려면이 함수를 호출 합니다.

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>매개 변수

*요소인*<br/>
요소입니다.

### <a name="return-value"></a>반환 값

해시 값을 반환 합니다.

### <a name="remarks"></a>설명

기본 해시 알고리즘은 매우 간단 합니다. 반환 값은 요소 번호입니다. 더 복잡 한 알고리즘이 필요한 경우이 함수를 재정의 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
