---
description: '다음에 대 한 자세한 정보: __umulh'
title: __umulh
ms.date: 09/02/2019
f1_keywords:
- __umulh
helpviewer_keywords:
- __umulh intrinsic
ms.assetid: d241b53a-e6f7-4af1-9f6e-84e149158f03
ms.openlocfilehash: 1d727d72155bdfb5cd5da1ee56c514af26b5ae89
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333612"
---
# <a name="__umulh"></a>__umulh

**Microsoft 전용**

64비트 부호 없는 두 정수의 곱에서 상위 64비트를 반환합니다.

## <a name="syntax"></a>구문

```C
unsigned __int64 __umulh(
   unsigned __int64 a,
   unsigned __int64 b
);
```

### <a name="parameters"></a>매개 변수

*은*\
[in] 곱할 첫 번째 숫자입니다.

*b*\
[in] 곱할 두 번째 숫자입니다.

## <a name="return-value"></a>반환 값

곱셈의 128비트 결과에서 상위 64비트입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__umulh`|X64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이러한 루틴은 내장 함수로만 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
// umulh.cpp
// processor: X64
#include <cstdio>
#include <intrin.h>

int main()
{
    unsigned __int64 i = 0x10;
    unsigned __int64 j = 0xFEDCBA9876543210;
    unsigned __int64 k = i * j; // k has the low 64 bits
                                // of the product.
    unsigned __int64 result;
    result = __umulh(i, j); // result has the high 64 bits
                            // of the product.
    printf_s("0x%I64x * 0x%I64x = 0x%I64x%I64x \n", i, j, result, k);
    return 0;
}
```

```Output
0x10 * 0xfedcba9876543210 = 0xfedcba98765432100
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
