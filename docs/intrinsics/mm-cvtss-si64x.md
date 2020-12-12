---
description: '다음에 대 한 자세한 정보: _mm_cvtss_si64x'
title: _mm_cvtss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtss_si64x
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
ms.openlocfilehash: 5b62b373305899920d5206b16c19f9b557f30bba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167697"
---
# <a name="_mm_cvtss_si64x"></a>_mm_cvtss_si64x

**Microsoft 전용**

스칼라 단일 정밀도 부동 소수점 숫자를 64 비트 정수 () 명령으로 변환 하는 x64 확장 버전을 생성 합니다 `cvtss2si` .

## <a name="syntax"></a>구문

```C
__int64 _mm_cvtss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>매개 변수

*기본값*\
진행 **`__m128`** 부동 소수점 값을 포함 하는 구조체입니다.

## <a name="return-value"></a>반환 값

첫 번째 부동 소수점 값을 정수로 변환한 결과인 64 비트 정수입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`_mm_cvtss_si64x`|X64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

구조체 값의 첫 번째 요소는 정수로 변환 되 고 반환 됩니다. MXCSR의 반올림 제어 비트는 반올림 동작을 결정 하는 데 사용 됩니다. 기본 반올림 모드는 가장 가까운 값으로 반올림 됩니다. 소수 부분이 0.5 이면 짝수로 반올림 됩니다. 구조체는 **`__m128`** xmm 레지스터를 나타내므로 내장 함수는 xmm 레지스터의 값을 사용 하 여 시스템 메모리에 씁니다.

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
// _mm_cvtss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] =
                           { 101.25, 200.75, 300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvtss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__m128d](../cpp/m128d.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
