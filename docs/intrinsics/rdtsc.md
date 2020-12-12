---
description: '다음에 대 한 자세한 정보: __rdtsc'
title: __rdtsc
ms.date: 09/02/2019
f1_keywords:
- __rdtsc
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
ms.openlocfilehash: 930c8fbd0ae762c8674a85e379899bc4fe4d3394
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257513"
---
# <a name="__rdtsc"></a>__rdtsc

**Microsoft 전용**

`rdtsc`프로세서 타임 스탬프를 반환 하는 명령을 생성 합니다. 프로세서 타임 스탬프는 마지막 다시 설정 이후의 클록 주기 수를 기록 합니다.

## <a name="syntax"></a>구문

```C
unsigned __int64 __rdtsc();
```

## <a name="return-value"></a>반환 값

틱 수를 나타내는 64 비트 부호 없는 정수입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__rdtsc`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 루틴은 내장 함수로만 사용할 수 있습니다.

이후 하드웨어 세대에서 TSC 값의 해석은 이전 버전의 x64와는 다릅니다. 자세한 내용은 하드웨어 설명서를 참조 하세요.

## <a name="example"></a>예제

```cpp
// rdtsc.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__rdtsc)

int main()
{
    unsigned __int64 i;
    i = __rdtsc();
    printf_s("%I64d ticks\n", i);
}
```

```Output
3363423610155519 ticks
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
