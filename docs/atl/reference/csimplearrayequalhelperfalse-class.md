---
description: '자세히 알아보기: CSimpleArrayEqualHelperFalse 클래스'
title: CSimpleArrayEqualHelperFalse 클래스
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
ms.openlocfilehash: 196f7873f72799408a629bc784cb343966801d79
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140727"
---
# <a name="csimplearrayequalhelperfalse-class"></a>CSimpleArrayEqualHelperFalse 클래스

이 클래스는 [CSimpleArray](../../atl/reference/csimplearray-class.md) 클래스에 대 한 도우미입니다.

## <a name="syntax"></a>구문

```
template <class T>
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
파생 클래스입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSimpleArrayEqualHelperFalse:: IsEqual](#isequal)|정적인 False를 반환 합니다.|

## <a name="remarks"></a>설명

이 특성 클래스는 클래스에 대 한 보수입니다 `CSimpleArray` . 항상 false를 반환 하 고, `ATLASSERT` 참조 되는 경우에는 false의 인수를 사용 하 여를 호출 합니다. 같음 테스트가 충분히 정의 되지 않은 경우이 클래스를 사용 하면 요소가 포함 된 배열이 대부분의 메서드에 대해 제대로 작동 하지만 [CSimpleArray:: Find](../../atl/reference/csimplearray-class.md#find)와 같은 비교에 의존 하는 메서드에 대해 잘 정의 된 방식으로 실패 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** atlsimpcoll

## <a name="csimplearrayequalhelperfalseisequal"></a><a name="isequal"></a> CSimpleArrayEqualHelperFalse:: IsEqual

false를 반환합니다.

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>반환 값

false를 반환합니다.

### <a name="remarks"></a>설명

이 메서드는 항상 false를 반환 하 고, `ATLASSERT` 참조 되는 경우 false의 인수를 사용 하 여를 호출 합니다. 의 목적은 `CSimpleArrayEqualHelperFalse::IsEqual` 같음 테스트가 적절 하 게 정의 되지 않은 경우에는 비교를 사용 하 여 잘 정의 된 방식으로 메서드를 강제로 사용 하 여 실패 합니다.

## <a name="see-also"></a>참고 항목

[CSimpleArrayEqualHelper 클래스](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
