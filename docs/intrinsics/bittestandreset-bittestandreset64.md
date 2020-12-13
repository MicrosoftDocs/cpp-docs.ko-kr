---
description: '자세히 알아보기: _bittestandreset, _bittestandreset64'
title: _bittestandreset, _bittestandreset64
ms.date: 09/02/2019
f1_keywords:
- _bittestandreset64_cpp
- _bittestandreset
- _bittestandreset_cpp
- _bittestandreset64
helpviewer_keywords:
- btr instruction
- _bittestandreset intrinsic
- _bittestandreset64 intrinsic
ms.assetid: 8dad63bb-a051-4cd7-a793-3357537dfeaf
ms.openlocfilehash: 5d0b6133b981a7008bbe4979ee123cebd5ef99fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337168"
---
# <a name="_bittestandreset-_bittestandreset64"></a>_bittestandreset, _bittestandreset64

**Microsoft 전용**

주소의 비트를 검사 하 고 `b` `a` 현재 값을 반환 하 고 비트를 0으로 다시 설정 하는 명령을 생성 합니다.

## <a name="syntax"></a>구문

```C
unsigned char _bittestandreset(
   long *a,
   long b
);
unsigned char _bittestandreset64(
   __int64 *a,
   __int64 b
);
```

### <a name="parameters"></a>매개 변수

*은*\
[in, out] 검사할 메모리에 대 한 포인터입니다.

*b*\
진행 테스트할 비트 위치입니다.

## <a name="return-value"></a>반환 값

지정한 위치에 있는 비트입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`_bittestandreset`|x86, ARM, x64, ARM64|
|`_bittestandreset64`|x64, ARM64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
// bittestandreset.cpp
// processor: x86, IPF, x64
#include <stdio.h>
#include <limits.h>
#include <intrin.h>

#pragma intrinsic(_bittestandreset)

// Check the sign bit and reset to 0 (taking the absolute value)
// Returns 0 if the number is positive or zero
// Returns 1 if the number is negative
unsigned char absolute_value(long* p)
{
   const int SIGN_BIT = 31;
   return _bittestandreset(p, SIGN_BIT);
}

int main()
{
    long i = -112;
    unsigned char result;

    // Check the sign bit and reset to 0 (taking the absolute value)

    result = absolute_value(&i);
    if (result == 1)
        printf_s("The number was negative.\n");
}
```

```Output
The number was negative.
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
