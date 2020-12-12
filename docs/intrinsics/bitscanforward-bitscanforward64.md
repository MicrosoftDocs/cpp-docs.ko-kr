---
description: '자세히 알아보기: _BitScanForward, _BitScanForward64'
title: _BitScanForward, _BitScanForward64
ms.date: 09/02/2019
f1_keywords:
- _BitScanForward
- _BitScanForward_cpp
- _BitScanForward64_cpp
- _BitScanForward64
helpviewer_keywords:
- _BitScanForward intrinsic
- bsf instruction
- BitScanForward intrinsic
ms.assetid: 405e60fb-0815-42a7-9b02-6fc035122203
ms.openlocfilehash: 182f22b5350fcad7c3da9a0d6f6df36c0871a3e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337221"
---
# <a name="_bitscanforward-_bitscanforward64"></a>_BitScanForward, _BitScanForward64

**Microsoft 전용**

LSB(최하위 비트)에서 MSB(최상위 비트)로의 마스크 데이터에서 설정 비트(1)를 검색합니다.

## <a name="syntax"></a>구문

```C
unsigned char _BitScanForward(
   unsigned long * Index,
   unsigned long Mask
);
unsigned char _BitScanForward64(
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

마스크가 0이면 0이고 그렇지 않으면 0이 아닙니다.

## <a name="remarks"></a>설명

설정 비트가 발견되면 첫 번째로 발견된 설정 비트의 비트 위치가 첫 번째 매개 변수에서 반환됩니다. 설정 비트가 발견되지 않으면 0이 반환되고 그렇지 않으면 1이 반환됩니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`_BitScanForward`|x86, ARM, x64, ARM64|
|`_BitScanForward64`|ARM64, x64|

**헤더 파일** \<intrin.h>

## <a name="example"></a>예제

```cpp
// BitScanForward.cpp
// compile with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_BitScanForward)

int main()
{
   unsigned long mask = 0x1000;
   unsigned long index;
   unsigned char isNonzero;

   cout << "Enter a positive integer as the mask: " << flush;
   cin >> mask;
   isNonzero = _BitScanForward(&index, mask);
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
Mask: 12 Index: 2
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
