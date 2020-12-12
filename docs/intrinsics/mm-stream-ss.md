---
description: '다음에 대 한 자세한 정보: _mm_stream_ss'
title: _mm_stream_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 3af79ee38c09f08ab8e1e5300800846c866972a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133209"
---
# <a name="_mm_stream_ss"></a>_mm_stream_ss

**Microsoft 전용**

캐시를 polluting 않고 메모리 위치에 32 비트 데이터를 씁니다.

## <a name="syntax"></a>구문

```C
void _mm_stream_ss(
   float * Destination,
   __m128 Source
);
```

### <a name="parameters"></a>매개 변수

*대상이*\
제한이 원본 데이터가 기록 되는 위치에 대 한 포인터입니다.

*원본*\
진행 아래쪽 32 비트에 쓸 값을 포함 하는 128 비트 숫자 **`float`** 입니다.

## <a name="return-value"></a>반환 값

없음

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

내장 함수는 명령을 생성 합니다 `movntss` . 이 명령에 대 한 하드웨어 지원을 확인 하려면를 사용 하 여 내장 함수를 호출 하 `__cpuid` `InfoType=0x80000001` 고의 6 비트를 확인 `CPUInfo[2] (ECX)` 합니다. 이 비트는 명령이 지원 되 면 1이 고, 그렇지 않으면 0입니다.

명령을 지원 하지 않는 하드웨어에서 내장 함수를 사용 하는 코드를 실행 하는 경우 `_mm_stream_ss` `movntss` 결과를 예측할 수 없습니다.

## <a name="example"></a>예제

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128 vals;
    float f[4];

    f[0] = -1.;
    f[1] = -2.;
    f[2] = -3.;
    f[3] = -4.;
    vals.m128_f32[0] = 0.;
    vals.m128_f32[1] = 1.;
    vals.m128_f32[2] = 2.;
    vals.m128_f32[3] = 3.;
    _mm_stream_ss(&f[3], vals);
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;
}
```

```Output
f[0] = -1, f[1] = -2
f[2] = -3, f[3] = 3
```

**Microsoft 전용 종료**

Advanced 마이크로 장치, i n c .의 저작권 2007 부분 All rights reserved. 고급 마이크로 장치, i n c .의 권한으로 재현 합니다.

## <a name="see-also"></a>참고 항목

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)\
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)\
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
