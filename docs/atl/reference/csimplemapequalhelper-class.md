---
description: '자세히 알아보기: CSimpleMapEqualHelper 클래스'
title: CSimpleMapEqualHelper 클래스
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: 2b8ff742bf24b6c6c4354cef652e3fc697ffb1d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140610"
---
# <a name="csimplemapequalhelper-class"></a>CSimpleMapEqualHelper 클래스

이 클래스는 [Csimplemap](../../atl/reference/csimplemap-class.md) 클래스에 대 한 도우미입니다.

## <a name="syntax"></a>구문

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>매개 변수

*TKey*<br/>
키 요소입니다.

*TVal*<br/>
값 요소입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|정적인 두 키가 같은지 테스트 합니다.|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|정적인 두 값이 같은지 테스트 합니다.|

## <a name="remarks"></a>설명

이 특성 클래스는 클래스에 대 한 추가 자료입니다 `CSimpleMap` . 두 `CSimpleMap` 개체 요소 (특히 키 및 값 구성 요소)가 같은지 비교 하는 메서드를 제공 합니다. 기본적으로 키와 값은 **operator = = ()** 를 사용 하 여 비교 되지만 맵에 고유한 같음 연산자가 없는 복합 데이터 형식이 포함 된 경우이 클래스를 재정의 하 여 필요한 추가 기능을 제공할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:** atlsimpcoll

## <a name="csimplemapequalhelperisequalkey"></a><a name="isequalkey"></a> CSimpleMapEqualHelper::IsEqualKey

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

## <a name="csimplemapequalhelperisequalvalue"></a><a name="isequalvalue"></a> CSimpleMapEqualHelper::IsEqualValue

두 값이 같은지 테스트 합니다.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>매개 변수

*v1*<br/>
첫 번째 값입니다.

*v2*<br/>
두 번째 값입니다.

### <a name="return-value"></a>반환 값

값이 같으면 true, 그렇지 않으면 false를 반환 합니다.

## <a name="see-also"></a>참고 항목

[CSimpleMapEqualHelperFalse 클래스](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
