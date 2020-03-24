---
title: CompareStringOrdinal 메서드
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
ms.openlocfilehash: 1291084395b02602b7a3de9013df6720d2e237fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214099"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal 메서드

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
inline INT32 CompareStringOrdinal(
   HSTRING lhs,
   HSTRING rhs)
```

### <a name="parameters"></a>매개 변수

*lhs*<br/>
비교할 첫 번째 HSTRING입니다.

*rhs*<br/>
비교할 두 번째 HSTRING입니다.

## <a name="return-value"></a>반환 값

|값|조건|
|-----------|---------------|
|-1|*lhs* 가 *rhs*보다 작은 경우|
|0|*lhs* equals *rhs*.|
|1|*lhs* 가 *rhs*보다 큽니다.|

## <a name="remarks"></a>주의

지정 된 두 HSTRING 개체를 비교 하 고 정렬 순서에서 해당 상대 위치를 나타내는 정수를 반환 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼::D etails

## <a name="see-also"></a>참고 항목

[Microsoft::WRL::Wrappers::Details 네임스페이스](microsoft-wrl-wrappers-details-namespace.md)
