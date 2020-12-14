---
description: '자세히 알아보기: _mm_insert_si64, _mm_inserti_si64'
title: _mm_insert_si64, _mm_inserti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
ms.openlocfilehash: 96ddf9a8836dcb927a09a51e0b2818b2a040c9d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345266"
---
# <a name="_mm_insert_si64-_mm_inserti_si64"></a>_mm_insert_si64, _mm_inserti_si64

**Microsoft 전용**

`insertq`두 번째 피연산자의 비트를 첫 번째 피연산자로 삽입 하는 명령을 생성 합니다.

## <a name="syntax"></a>구문

```C
__m128i _mm_insert_si64(
   __m128i Source1,
   __m128i Source2
);
__m128i _mm_inserti_si64(
   __m128i Source1,
   __m128i Source2
   int Length,
   int Index
);
```

### <a name="parameters"></a>매개 변수

*Source1*\
진행 하위 64 비트의 입력 데이터가 있는 128 비트 필드로, 필드가 삽입 됩니다.

*소스 2*\
진행 하위 비트에 삽입할 데이터가 있는 128 비트 필드입니다.  의 `_mm_insert_si64` 경우에는 상위 비트의 필드 설명자도 포함 됩니다.

*길이*\
진행 삽입할 필드의 길이를 지정 하는 정수 상수입니다.

*인덱싱할*\
진행 데이터가 삽입 될 필드의 최하위 비트 인덱스를 지정 하는 정수 상수입니다.

## <a name="return-value"></a>반환 값

128 비트 필드로, 하위 64 비트에는 *Source1* 의 원래 low 64 비트가 포함 되 고, 지정 된 비트 필드는 *소스 2* 의 하위 비트로 교체 됩니다. 반환 값의 상위 64 비트는 정의 되지 않습니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이러한 내장 함수는 `insertq` *소스 2* 에서 *Source1* 로 비트를 삽입 하는 명령을 생성 합니다. 에는 두 가지 버전이 있습니다 .는이 고,는 바로 버전이 며,는 버전이 더 `_mm_inserti_si64` `_mm_insert_si64` 이상 버전이 아닙니다. 각 버전은 소스 2에서 지정 된 길이의 비트 필드를 추출 하 여 Source1에 삽입 합니다.  추출 된 비트는 소스 2의 최하위 비트입니다.  이러한 비트가 삽입 되는 필드 Source1는 최하위 비트의 길이 및 인덱스에 따라 정의 됩니다.  길이 및 인덱스 값은 mod 64로 간주 되므로-1과 127은 모두 63로 해석 됩니다. (감소) 비트 인덱스 및 (축소) 필드 길이의 합계가 64 보다 큰 경우 결과가 정의 되지 않습니다. 필드 길이 값이 0 이면 64로 해석 됩니다. 필드 길이와 비트 인덱스가 모두 0 이면 *소스 2* 의 비트 63:0이 *Source1* 에 삽입 됩니다. 필드 길이가 0 이지만 비트 인덱스가 0이 아닌 경우 결과가 정의 되지 않습니다.

_Mm_insert_si64에 대 한 호출에서 필드 길이는 소스 2의 비트 77:72 및 비트 69:64의 인덱스에 포함 됩니다.

`_mm_inserti_si64`컴파일러가 정수 상수로 확인할 수 없는 인수를 사용 하 여를 호출 하는 경우 컴파일러는 이러한 값을 XMM 레지스터에 압축 하 고를 호출 하는 코드를 생성 `_mm_insert_si64` 합니다.

명령에 대 한 하드웨어 지원을 확인 하려면를 사용 하 여 `insertq` 내장 함수를 호출 하 `__cpuid` `InfoType=0x80000001` 고의 6 비트를 확인 `CPUInfo[2] (ECX)` 합니다. 명령이 지원 되는 경우이 비트는 1이 고, 그렇지 않으면 0입니다. 명령을 지원 하지 않는 하드웨어에서 내장 함수를 사용 하는 코드를 실행 하는 경우 `insertq` 결과를 예측할 수 없습니다.

## <a name="example"></a>예제

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source1, source2, source3, result1, result2, result3;

int
main()
{

    __int64 mask;

    source1.ui64[0] = 0xffffffffffffffffll;
    source2.ui64[0] = 0xfedcba9876543210ll;
    source2.ui64[1] = 0xc10;
    source3.ui64[0] = source2.ui64[0];

    result1.m = _mm_insert_si64 (source1.m, source2.m);
    result2.m = _mm_inserti_si64(source1.m, source3.m, 16, 12);
    mask = 0xffff << 12;
    mask = ~mask;
    result3.ui64[0] = (source1.ui64[0] & mask) |
                      ((source2.ui64[0] & 0xffff) << 12);

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;

}
```

```Output
result1 = 0xfffffffff3210fff
result2 = 0xfffffffff3210fff
result3 = 0xfffffffff3210fff
```

**Microsoft 전용 종료**

Advanced 마이크로 장치, i n c .의 저작권 2007 부분 All rights reserved. 고급 마이크로 장치, i n c .의 권한으로 재현 합니다.

## <a name="see-also"></a>참고 항목

[_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
