---
description: '자세히 알아보기: CElementTraits 클래스'
title: CElementTraits 클래스
ms.date: 11/04/2016
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
helpviewer_keywords:
- CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
ms.openlocfilehash: 1bcb6c9da2bca733efe68b634eebd7f379ba0d10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141806"
---
# <a name="celementtraits-class"></a>CElementTraits 클래스

이 클래스는 컬렉션 클래스에서 이동, 복사, 비교 및 해시 작업을 위한 메서드와 함수를 제공 하는 데 사용 됩니다.

## <a name="syntax"></a>구문

```
template<typename T>
class CElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
컬렉션에 저장 되는 데이터의 형식입니다.

## <a name="remarks"></a>설명

이 클래스는 컬렉션 클래스 개체에 저장 된 요소를 이동, 복사, 비교 및 해시 하기 위한 기본 정적 함수 및 메서드를 제공 합니다. `CElementTraits` 는 컬렉션 클래스 [CAtlArray](../../atl/reference/catlarray-class.md), [catllist](../../atl/reference/catllist-class.md), [Crbmap](../../atl/reference/crbmap-class.md), [CRBMultiMap](../../atl/reference/crbmultimap-class.md)및 [CRBTree](../../atl/reference/crbtree-class.md)에 의해 이러한 작업의 기본 공급자로 지정 됩니다.

기본 구현은 단순한 데이터 형식에는 충분 하지만 컬렉션 클래스를 사용 하 여 더 복잡 한 개체를 저장 하는 경우에는 사용자가 제공한 구현에서 함수 및 메서드를 재정의 해야 합니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="see-also"></a>참고 항목

[Cdefaul서 용 Ement특성 클래스](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
