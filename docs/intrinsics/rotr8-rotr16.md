---
description: '자세히 알아보기: _rotr8, _rotr16'
title: _rotr8, _rotr16
ms.date: 09/02/2019
f1_keywords:
- _rotr16
- _rotr8
helpviewer_keywords:
- _rotr8 intrinsic
- _rotr16 intrinsic
ms.assetid: dfbd2c82-82b4-427a-ad52-51609027ebff
ms.openlocfilehash: 95908956fe34b654c3602f27b495eb58a0b8f8c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307043"
---
# <a name="_rotr8-_rotr16"></a>_rotr8, _rotr16

**Microsoft 전용**

입력 값을 지정된 비트 위치 수만큼 LSB(최하위 비트) 오른쪽으로 회전합니다.

## <a name="syntax"></a>구문

```C
unsigned char _rotr8(
   unsigned char value,
   unsigned char shift
);
unsigned short _rotr16(
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
|`_rotr8`|x86, ARM, x64, ARM64|
|`_rotr16`|x86, ARM, x64, ARM64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

오른쪽 시프트 작업과 달리, 오른쪽 회전을 실행 하는 경우 낮은 끝을 벗어나는 하위 비트가 상위 비트 위치로 이동 됩니다.

## <a name="example"></a>예제

```cpp
// rotr.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_rotr8, _rotr16)

int main()
{
    unsigned char c = 'A', c1, c2;

    for (int i = 0; i < 8; i++)
    {
       printf_s("Rotating 0x%x right by %d bits gives 0x%x\n", c,
                i, _rotr8(c, i));
    }

    unsigned short s = 0x12;
    int nBit = 10;

    printf_s("Rotating unsigned short 0x%x right by %d bits "
             "gives 0x%x\n",
            s, nBit, _rotr16(s, nBit));
}
```

```Output
Rotating 0x41 right by 0 bits gives 0x41
Rotating 0x41 right by 1 bits gives 0xa0
Rotating 0x41 right by 2 bits gives 0x50
Rotating 0x41 right by 3 bits gives 0x28
Rotating 0x41 right by 4 bits gives 0x14
Rotating 0x41 right by 5 bits gives 0xa
Rotating 0x41 right by 6 bits gives 0x5
Rotating 0x41 right by 7 bits gives 0x82
Rotating unsigned short 0x12 right by 10 bits gives 0x480
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_rotl8, _rotl16](../intrinsics/rotl8-rotl16.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
