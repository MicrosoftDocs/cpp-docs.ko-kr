---
description: '자세히 알아보기: CSimpleMapEqualHelperFalse 클래스'
title: CSimpleMapEqualHelperFalse 클래스
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
ms.openlocfilehash: 5bad8232dc1a96fc743a3526acdb86b839601d9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140584"
---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse 클래스

이 클래스는 [Csimplemap](../../atl/reference/csimplemap-class.md) 클래스에 대 한 도우미입니다.

## <a name="syntax"></a>구문

```
template <class TKey, class TVal>
class CSimpleMapEqualHelperFalse
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|정적인 두 키가 같은지 테스트 합니다.|
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|정적인 False를 반환 합니다.|

## <a name="remarks"></a>설명

이 특성 클래스는 클래스에 대 한 추가 자료입니다 `CSimpleMap` . 이 클래스는 개체에 포함 된 두 요소 `CSimpleMap` , 특히 두 개의 값 요소 또는 두 개의 키 요소를 비교 하는 메서드를 제공 합니다.

값 비교는 항상 false를 반환 하 고, `ATLASSERT` 참조 되는 경우에는 false의 인수를 사용 하 여를 호출 합니다. 같음 테스트가 충분히 정의 되지 않은 경우에는이 클래스를 사용 하 여 키/값 쌍이 포함 된 맵이 대부분의 메서드에 대해 제대로 작동 하지만 [Csimplemap](../../atl/reference/csimplemap-class.md#findval)의 비교에 의존 하는 메서드에 대해 잘 정의 된 방식으로 실패 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** atlsimpcoll

## <a name="csimplemapequalhelperfalseisequalkey"></a><a name="isequalkey"></a> CSimpleMapEqualHelperFalse::IsEqualKey

두 키가 같은지 테스트 합니다.

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>매개 변수

*k1*<br/>
첫 번째 키입니다.

*k2*<br/>
두 번째 키입니다.

### <a name="return-value"></a>반환 값

키가 같으면 true, 그렇지 않으면 false를 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)을 호출 합니다.

## <a name="csimplemapequalhelperfalseisequalvalue"></a><a name="isequalvalue"></a> CSimpleMapEqualHelperFalse::IsEqualValue

false를 반환합니다.

```
static bool IsEqualValue(const TVal&, const TVal&);
```

### <a name="return-value"></a>반환 값

false를 반환합니다.

### <a name="remarks"></a>설명

이 메서드는 항상 false를 반환 하 고, `ATLASSERT` 참조 되는 경우 false의 인수를 사용 하 여를 호출 합니다. 의 목적은 `CSimpleMapEqualHelperFalse::IsEqualValue` 같음 테스트가 적절 하 게 정의 되지 않은 경우에는 비교를 사용 하 여 잘 정의 된 방식으로 메서드를 강제로 사용 하 여 실패 합니다.

## <a name="see-also"></a>참고 항목

[CSimpleMapEqualHelper 클래스](../../atl/reference/csimplemapequalhelper-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
