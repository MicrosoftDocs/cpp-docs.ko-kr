---
description: '다음에 대 한 자세한 정보: _mm_cvttss_si64x'
title: _mm_cvttss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: a4af7b726d0f15099586bc94348ab4ba7ebf5b8e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167632"
---
# <a name="_mm_cvttss_si64x"></a>_mm_cvttss_si64x

**Microsoft 전용**

Convert의 x64 확장 버전을 Single-Precision Floating-Point Number를 64 비트 정수 ( `cvttss2si` ) 명령으로 내보냅니다.

## <a name="syntax"></a>구문

```C
__int64 _mm_cvttss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>매개 변수

*기본값*\
진행 **`__m128`** 단 정밀도 부동 소수점 값을 포함 하는 구조체입니다.

## <a name="return-value"></a>반환 값

첫 번째 부동 소수점 값을 64 비트 정수로 변환한 결과입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`_mm_cvttss_si64x`|X64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

내장 함수는와 `_mm_cvtss_si64x` 는 달리 부정확 한 변환은 0으로 잘립니다. 구조는 **`__m128`** xmm 레지스터를 나타내므로 생성 된 명령은 xmm 레지스터에서 시스템 메모리로 데이터를 이동 합니다.

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
// _mm_cvttss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvttss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] = { 101.5, 200.75,
                                          300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvttss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__m128](../cpp/m128.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
