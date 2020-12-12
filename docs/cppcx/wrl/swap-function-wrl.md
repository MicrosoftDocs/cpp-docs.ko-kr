---
description: '자세히 알아보기: Swap 함수 (WRL)'
title: Swap 함수 (WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Swap
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
ms.openlocfilehash: e81c9e332c6c6a69f475f53132689dc99fffdfee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186196"
---
# <a name="swap-function-wrl"></a>Swap 함수 (WRL)

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
WRL_NOTHROW inline void Swap(
   _Inout_ T& left,
   _Inout_ T& right
);
```

### <a name="parameters"></a>매개 변수

*비어*<br/>
첫 번째 인수입니다.

*오른쪽*<br/>
두 번째 인수입니다.

## <a name="return-value"></a>반환 값

## <a name="remarks"></a>설명

지정 된 두 인수 값을 교환 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** internal. h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL::D etails 네임 스페이스](microsoft-wrl-details-namespace.md)
