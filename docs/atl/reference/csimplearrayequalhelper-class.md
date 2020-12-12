---
description: '자세히 알아보기: CSimpleArrayEqualHelper 클래스'
title: CSimpleArrayEqualHelper 클래스
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
ms.openlocfilehash: e1a5fd3eea5fd6ef7563febc662c5a7a1bc639c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140766"
---
# <a name="csimplearrayequalhelper-class"></a>CSimpleArrayEqualHelper 클래스

이 클래스는 [CSimpleArray](../../atl/reference/csimplearray-class.md) 클래스에 대 한 도우미입니다.

## <a name="syntax"></a>구문

```
template <class T>
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
파생 클래스입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSimpleArrayEqualHelper:: IsEqual](#isequal)|정적인 두 `CSimpleArray` 개체 요소가 같은지 테스트 합니다.|

## <a name="remarks"></a>설명

이 특성 클래스는 클래스에 대 한 추가 자료입니다 `CSimpleArray` . 개체에 저장 된 두 요소를 비교 하는 메서드를 제공 `CSimpleArray` 합니다. 기본적으로 요소는 **operator = ()** 를 사용 하 여 비교 되지만 배열에 고유한 같음 연산자가 없는 복합 데이터 형식이 포함 된 경우에는이 클래스를 재정의 해야 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** atlsimpcoll

## <a name="csimplearrayequalhelperisequal"></a><a name="isequal"></a> CSimpleArrayEqualHelper:: IsEqual

두 `CSimpleArray` 개체 요소가 같은지 테스트 합니다.

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>매개 변수

*들은*<br/>
T 형식의 개체입니다.

*t*<br/>
T 형식의 개체입니다.

### <a name="return-value"></a>반환 값

요소가 같으면 true, 그렇지 않으면 false를 반환 합니다.

## <a name="see-also"></a>참고 항목

[CSimpleArray 클래스](../../atl/reference/csimplearray-class.md)<br/>
[CSimpleArrayEqualHelperFalse 클래스](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
