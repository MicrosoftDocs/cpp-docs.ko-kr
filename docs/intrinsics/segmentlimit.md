---
description: '다음에 대 한 자세한 정보: __segmentlimit'
title: __segmentlimit
ms.date: 09/02/2019
f1_keywords:
- __segmentlimit
helpviewer_keywords:
- __segmentlimit intrinsic
- lsl instruction
ms.assetid: d0bc3630-90cb-4185-8667-686fd41e23d4
ms.openlocfilehash: 49f8688918e07e143615af7b184a784daa0eaaa1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307004"
---
# <a name="__segmentlimit"></a>__segmentlimit

**Microsoft 전용**

`lsl`(로드 세그먼트 제한) 명령을 생성 합니다.

## <a name="syntax"></a>구문

```C
unsigned long __segmentlimit(
   unsigned long a
);
```

### <a name="parameters"></a>매개 변수

*은*\
진행 세그먼트 선택기를 지정 하는 상수입니다.

## <a name="return-value"></a>반환 값

선택 기가 유효 하 고 현재 사용 권한 수준에서 표시 되는 경우 *에* 의해 지정 된 세그먼트 선택기의 세그먼트 한도입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__segmentlimit`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

세그먼트 제한을 검색할 수 없는 경우에는이 명령이 실패 합니다. 오류가 발생 하면이 명령은 ZF 플래그를 지우고 반환 값이 정의 되지 않습니다.

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
#include <stdio.h>

#ifdef _M_IX86
typedef unsigned int READETYPE;
#else
typedef unsigned __int64 READETYPE;
#endif

#define EFLAGS_ZF      0x00000040
#define KGDT_R3_DATA    0x0020
#define RPL_MASK        0x3

extern "C"
{
unsigned long __segmentlimit (unsigned long);
READETYPE __readeflags();
}

#pragma intrinsic(__readeflags)
#pragma intrinsic(__segmentlimit)

int main(void)
{
   const unsigned long initsl = 0xbaadbabe;
   READETYPE eflags = 0;
   unsigned long sl = initsl;

   printf("Before: segment limit =0x%x eflags =0x%x\n", sl, eflags);
   sl = __segmentlimit(KGDT_R3_DATA + RPL_MASK);

   eflags = __readeflags();

   printf("After: segment limit =0x%x eflags =0x%x eflags.zf = %s\n", sl, eflags, (eflags & EFLAGS_ZF) ? "set" : "clear");

   // If ZF is set, the call to lsl succeeded; if ZF is clear, the call failed.
   printf("%s\n", eflags & EFLAGS_ZF ? "Success!": "Fail!");

   // You can verify the value of sl to make sure that the instruction wrote to it
   printf("sl was %s\n", (sl == initsl) ? "unchanged" : "changed");

   return 0;
}
```

```Output
Before: segment limit =0xbaadbabe eflags =0x0
After: segment limit =0xffffffff eflags =0x256 eflags.zf = set
Success!
sl was changed
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
