---
description: '다음에 대 한 자세한 정보: __mulh'
title: __mulh
ms.date: 09/02/2019
f1_keywords:
- __mulh
helpviewer_keywords:
- __mulh intrinsic
ms.assetid: cd2ab093-9ef6-404d-ac34-0bee033882f3
ms.openlocfilehash: 0cee31b6a9e1088d76200cd46482fd4aaf80474b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118942"
---
# <a name="__mulh"></a>__mulh

**Microsoft 전용**

2 64 비트 부호 있는 정수 제품의 상위 64 비트를 반환 합니다.

## <a name="syntax"></a>구문

```C
__int64 __mulh(
   __int64 a,
   __int64 b
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
|`__mulh`|X64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
// mulh.cpp
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__mulh)

int main()
{
    __int64 a = 0x0fffffffffffffffI64;
    __int64 b = 0xf0000000I64;

    __int64 result = __mulh(a, b); // the high 64 bits
    __int64 result2 = a * b; // the low 64 bits

    printf_s(" %#I64x * %#I64x = %#I64x%I64x\n",
             a, b, result, result2);
}
```

```Output
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
