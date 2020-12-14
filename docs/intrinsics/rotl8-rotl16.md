---
description: '자세히 알아보기: _rotl8, _rotl16'
title: _rotl8, _rotl16
ms.date: 09/02/2019
f1_keywords:
- _rotl8
- _rotl16
helpviewer_keywords:
- _rotl8 intrinsic
- _rotl16 intrinsic
ms.assetid: 8c519ab6-aef9-4f07-a387-daee8408368f
ms.openlocfilehash: 71ef10bb6af750fc08955fbdf82975b1ed32fa94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211910"
---
# <a name="_rotl8-_rotl16"></a>_rotl8, _rotl16

**Microsoft 전용**

입력 값을 지정된 비트 위치 수만큼 MSB(최상위 비트) 왼쪽으로 회전합니다.

## <a name="syntax"></a>구문

```C
unsigned char _rotl8(
   unsigned char value,
   unsigned char shift
);
unsigned short _rotl16(
   unsigned short value,
   unsigned char shift
);
```

### <a name="parameters"></a>매개 변수

*기본값*\
진행 회전할 값입니다.

*교대조*\
진행 회전할 비트 수입니다.

## <a name="return-value"></a>반환 값

순환된 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`_rotl8`|x86, ARM, x64, ARM64|
|`_rotl16`|x86, ARM, x64, ARM64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

왼쪽 시프트 작업과 달리 왼쪽 회전을 실행 하면 높은 끝을 벗어나는 상위 비트가 최하위 비트 위치로 이동 합니다.

## <a name="example"></a>예제

```cpp
// rotl.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_rotl8, _rotl16)

int main()
{
    unsigned char c = 'A', c1, c2;

    for (int i = 0; i < 8; i++)
    {
       printf_s("Rotating 0x%x left by %d bits gives 0x%x\n", c,
               i, _rotl8(c, i));
    }

    unsigned short s = 0x12;
    int nBit = 10;

    printf_s("Rotating unsigned short 0x%x left by %d bits gives 0x%x\n",
            s, nBit, _rotl16(s, nBit));
}
```

```Output
Rotating 0x41 left by 0 bits gives 0x41
Rotating 0x41 left by 1 bits gives 0x82
Rotating 0x41 left by 2 bits gives 0x5
Rotating 0x41 left by 3 bits gives 0xa
Rotating 0x41 left by 4 bits gives 0x14
Rotating 0x41 left by 5 bits gives 0x28
Rotating 0x41 left by 6 bits gives 0x50
Rotating 0x41 left by 7 bits gives 0xa0
Rotating unsigned short 0x12 left by 10 bits gives 0x4800
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_rotr8, _rotr16](../intrinsics/rotr8-rotr16.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
