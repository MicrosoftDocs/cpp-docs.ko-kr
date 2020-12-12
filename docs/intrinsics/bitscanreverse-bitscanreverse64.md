---
description: '자세히 알아보기: _BitScanReverse, _BitScanReverse64'
title: _BitScanReverse, _BitScanReverse64
ms.date: 09/02/2019
f1_keywords:
- _BitScanReverse64
- _BitScanReverse_cpp
- _BitScanReverse
- _BitScanReverse64_cpp
helpviewer_keywords:
- bsr instruction
- _BitScanReverse intrinsic
- BitScanReverse intrinsic
ms.assetid: 2520a207-af8b-4aad-9ae7-831abeadf376
ms.openlocfilehash: 1a535dcc95f9fbf791de3ecd2c2d54eddcc0399c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337215"
---
# <a name="_bitscanreverse-_bitscanreverse64"></a>_BitScanReverse, _BitScanReverse64

**Microsoft 전용**

MSB(최상위 비트)에서 LSB(최하위 비트)로의 마스크 데이터에서 설정 비트(1)를 검색합니다.

## <a name="syntax"></a>구문

```C
unsigned char _BitScanReverse(
   unsigned long * Index,
   unsigned long Mask
);
unsigned char _BitScanReverse64(
   unsigned long * Index,
   unsigned __int64 Mask
);
```

### <a name="parameters"></a>매개 변수

*인덱싱할*\
제한이 첫 번째 설정 비트 (1)의 비트 위치를 사용 하 여 로드 되었습니다.

*마스크할*\
진행 검색할 32 비트 또는 64 비트 값입니다.

## <a name="return-value"></a>반환 값

`Index`가 설정된 경우에는 0이 아니고 설정 비트가 발견되지 않은 경우에는 0입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|헤더|
|---------------|------------------|------------|
|`_BitScanReverse`|x86, ARM, x64, ARM64|\<intrin.h>|
|`_BitScanReverse64`|ARM64, x64|\<intrin.h>|

## <a name="example"></a>예제

```cpp
// BitScanReverse.cpp
// compile with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_BitScanReverse)

int main()
{
   unsigned long mask = 0x1000;
   unsigned long index;
   unsigned char isNonzero;

   cout << "Enter a positive integer as the mask: " << flush;
   cin >> mask;
   isNonzero = _BitScanReverse(&index, mask);
   if (isNonzero)
   {
      cout << "Mask: " << mask << " Index: " << index << endl;
   }
   else
   {
      cout << "No set bits found.  Mask is zero." << endl;
   }
}
```

```Input
12
```

```Output
Enter a positive integer as the mask:
Mask: 12 Index: 3
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
