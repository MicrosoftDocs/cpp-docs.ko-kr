---
description: '자세히 알아보기: _mm_extract_si64, _mm_extracti_si64'
title: _mm_extract_si64, _mm_extracti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
ms.openlocfilehash: 39a07c7310727de8d752c060c3d38481469ff1a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322869"
---
# <a name="_mm_extract_si64-_mm_extracti_si64"></a>_mm_extract_si64, _mm_extracti_si64

**Microsoft 전용**

`extrq`첫 번째 인수의 하위 64 비트에서 지정 된 비트를 추출 하는 명령을 생성 합니다.

## <a name="syntax"></a>구문

```C
__m128i _mm_extract_si64(
   __m128i Source,
   __m128i Descriptor
);
__m128i _mm_extracti_si64(
   __m128i Source,
   int Length,
   int Index
);
```

### <a name="parameters"></a>매개 변수

*원본*\
진행 하위 64 비트의 입력 데이터가 있는 128 비트 필드입니다.

*설명자*\
진행 추출할 비트 필드를 설명 하는 128 비트 필드입니다.

*길이*\
진행 추출할 필드의 길이를 지정 하는 정수입니다.

*인덱싱할*\
진행 추출할 필드의 인덱스를 지정 하는 정수입니다.

## <a name="return-value"></a>반환 값

최하위 비트에서 추출 된 필드가 있는 128 비트 필드입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`_mm_extract_si64`|SSE4a|
|`_mm_extracti_si64`|SSE4a|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이러한 내장 함수는 `extrq` *소스* 에서 비트를 추출 하는 명령을 생성 합니다. 에는 두 가지 버전이 있습니다. `_mm_extracti_si64` 는 바로 버전이 고는 버전이 더 `_mm_extract_si64` 이상 버전이 아닙니다. 각 버전은 *원본* 에서 추출 된 비트 필드의 길이와 최하위 비트의 인덱스를 추출 합니다. 길이 및 인덱스 값은 mod 64로 간주 되므로-1과 127은 모두 63로 해석 됩니다. (축소) 인덱스 및 (축소) 필드 길이의 합계가 64 보다 큰 경우 결과가 정의 되지 않습니다. 필드 길이 값이 0 이면 64로 해석 됩니다. 필드 길이와 비트 인덱스가 모두 0 이면 *원본의* 비트 63:0이 추출 됩니다. 필드 길이가 0이 고 비트 인덱스가 0이 아닌 경우 결과가 정의 되지 않습니다.

에 대 한 호출에서 `_mm_extract_si64` *설명자* 는 비트 13:8의 인덱스와 비트 5:0에서 추출할 데이터의 필드 길이를 포함 합니다.

`_mm_extracti_si64`컴파일러가 정수 상수로 확인할 수 없는 인수를 사용 하 여를 호출 하는 경우 컴파일러는 이러한 값을 XMM 레지스터 (*설명자*)로 압축 하 고를 호출 하는 코드를 생성 `_mm_extract_si64` 합니다.

명령에 대 한 하드웨어 지원을 확인 하려면를 사용 하 여 `extrq` 내장 함수를 호출 하 `__cpuid` `InfoType=0x80000001` 고의 6 비트를 확인 `CPUInfo[2] (ECX)` 합니다. 명령이 지원 되는 경우이 비트는 1이 고, 그렇지 않으면 0입니다. 명령을 지원 하지 않는이 내장 하드웨어를 사용 하는 코드를 실행 하는 경우 `extrq` 결과를 예측할 수 없습니다.

## <a name="example"></a>예제

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source, descriptor, result1, result2, result3;

int
main()
{
    source.ui64[0] =     0xfedcba9876543210ll;
    descriptor.ui64[0] = 0x0000000000000b1bll;

    result1.m = _mm_extract_si64 (source.m, descriptor.m);
    result2.m = _mm_extracti_si64(source.m, 27, 11);
    result3.ui64[0] = (source.ui64[0] >> 11) & 0x7ffffff;

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;
}
```

```Output
result1 = 0x30eca86
result2 = 0x30eca86
result3 = 0x30eca86
```

**Microsoft 전용 종료**

Advanced 마이크로 장치, i n c .의 저작권 2007 부분 All rights reserved. 고급 마이크로 장치, i n c .의 권한으로 재현 합니다.

## <a name="see-also"></a>참고 항목

[_mm_insert_si64, _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
