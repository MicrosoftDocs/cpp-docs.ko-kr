---
title: _InterlockedAdd 내장 함수
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAdd64_acq_cpp
- _InterlockedAdd64_acq
- _InterlockedAdd_acq
- _InterlockedAdd_nf
- _InterlockedAdd64_rel
- _InterlockedAdd64
- _InterlockedAdd_cpp
- _InterlockedAdd_rel_cpp
- _InterlockedAdd_rel
- _InterlockedAdd64_rel_cpp
- _InterlockedAdd64_cpp
- _InterlockedAdd_acq_cpp
- _InterlockedAdd64_nf
- _InterlockedAdd
helpviewer_keywords:
- _InterlockedAdd_nf intrinsic
- _InterlockedAdd_rel intrinsic
- _InterlockedAdd intrinsic
- _InterlockedAdd64 intrinsic
- _InterlockedAdd64_acq intrinsic
- _InterlockedAdd64_nf intrinsic
- _InterlockedAdd_acq intrinsic
- _InterlockedAdd64_rel intrinsic
ms.assetid: 3d319603-ea9c-4fdd-ae61-e52430ccc3b1
ms.openlocfilehash: efe1444273f17c8f0544d2c51b98923169032e61
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683899"
---
# <a name="_interlockedadd-intrinsic-functions"></a>_InterlockedAdd 내장 함수

**Microsoft 전용**

이러한 함수는 원자성 추가를 수행 하 여 두 개 이상의 스레드가 공유 변수에 액세스할 수 있는 경우 작업이 성공적으로 완료 되도록 합니다.

## <a name="syntax"></a>구문

```C
long _InterlockedAdd(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_acq(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_nf(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_rel(
   long volatile * Addend,
   long Value
);
__int64 _InterlockedAdd64(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_acq(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_nf (
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_rel(
   __int64 volatile * Addend,
   __int64 Value
);
```

### <a name="parameters"></a>매개 변수

*가 수*\
[in, out] 추가 될 정수에 대 한 포인터입니다. 더하기의 결과로 대체 됩니다.

*Value*\
진행 더할 값입니다.

## <a name="return-value"></a>반환 값

두 함수는 모두 추가의 결과를 반환합니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|아키텍처|
|---------------|------------------|
|`_InterlockedAdd`|ARM, ARM64|
|`_InterlockedAdd_acq`|ARM, ARM64|
|`_InterlockedAdd_nf`|ARM, ARM64|
|`_InterlockedAdd_rel`|ARM, ARM64|
|`_InterlockedAdd64`|ARM, ARM64|
|`_InterlockedAdd64_acq`|ARM, ARM64|
|`_InterlockedAdd64_nf`|ARM, ARM64|
|`_InterlockedAdd64_rel`|ARM, ARM64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

`_acq` 또는 `_rel` 접미사가 포함된 이러한 함수 버전은 획득 또는 해제 의미 체계 후에 연관 추가를 수행합니다. *의미 체계 가져오기* 는 나중에 메모리를 읽고 쓰기 전에 모든 스레드와 프로세서에 작업 결과가 표시 되는 것을 의미 합니다. 취득은 임계 영역을 입력할 때 유용합니다. *릴리스 의미 체계* 는 작업의 결과가 표시 되기 전에 모든 메모리 읽기 및 쓰기가 모든 스레드와 프로세서에 강제로 표시 되도록 합니다. 해제는 임계 영역을 벗어날 때 유용합니다. `_nf`("No fence") 접미사가 포함 된 내장 함수는 메모리 장벽으로 작동 하지 않습니다.

이러한 루틴은 내장 함수로만 사용할 수 있습니다.

## <a name="examples"></a>예제

```cpp
// interlockedadd.cpp
// Compile with: /Oi /EHsc
// processor: ARM
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_InterlockedAdd)

int main()
{
        long data1 = 0xFF00FF00;
        long data2 = 0x00FF0000;
        long retval;
        retval = _InterlockedAdd(&data1, data2);
        printf("0x%x 0x%x 0x%x", data1, data2, retval);
}
```

## <a name="output"></a>출력

```Output
0xffffff00 0xff0000 0xffffff00
```

```cpp
// interlockedadd64.cpp
// compile with: /Oi /EHsc
// processor: ARM
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_InterlockedAdd64)

int main()
{
        __int64 data1 = 0x0000FF0000000000;
        __int64 data2 = 0x00FF0000FFFFFFFF;
        __int64 retval;
        cout << hex << data1 << " + " << data2 << " = " ;
        retval = _InterlockedAdd64(&data1, data2);
        cout << data1 << endl;
        cout << "Return value: " << retval << endl;
}
```

## <a name="output"></a>출력

```Output
ff0000000000 + ff0000ffffffff = ffff00ffffffff
Return value: ffff00ffffffff
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[X86 컴파일러와 충돌](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
