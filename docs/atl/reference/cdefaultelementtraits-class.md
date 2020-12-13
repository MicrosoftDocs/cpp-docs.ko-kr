---
description: '다음에 대 한 자세한 정보: Cdefaul서 용 Ement특성 클래스'
title: Cdefaul서 용 Ement특성 클래스
ms.date: 11/04/2016
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
ms.openlocfilehash: f4dd1bae67ef626ef793ecee946d88879a07f194
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141897"
---
# <a name="cdefaultelementtraits-class"></a>Cdefaul서 용 Ement특성 클래스

이 클래스는 컬렉션 클래스에 대 한 기본 메서드 및 함수를 제공 합니다.

## <a name="syntax"></a>구문

```
template <typename T>
class CDefaultElementTraits : public CElementTraitsBase<T>,
    public CDefaultHashTraits<T>,
    public CDefaultCompareTraits<T>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
컬렉션에 저장 되는 데이터의 형식입니다.

## <a name="remarks"></a>설명

이 클래스는 컬렉션 클래스 개체에 저장 된 요소를 이동, 복사, 비교 및 해시 하기 위한 기본 정적 함수 및 메서드를 제공 합니다. 이 클래스는 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md), [cdefaulthashtraits](../../atl/reference/cdefaulthashtraits-class.md)및 [cdefaultcompare특성](../../atl/reference/cdefaultcomparetraits-class.md)의 함수 및 메서드를 파생 시키고 [CElementTraits](../../atl/reference/celementtraits-class.md), [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)및 [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)에서 활용 합니다.

자세한 내용은 [ATL 컬렉션 클래스](../../atl/atl-collection-classes.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** atlcoll

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
