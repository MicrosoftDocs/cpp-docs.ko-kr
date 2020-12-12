---
description: __Lzcnt16, __lzcnt, __lzcnt64에 대해 자세히 알아보세요.
title: __lzcnt16, __lzcnt, __lzcnt64
ms.date: 09/02/2019
f1_keywords:
- __lzcnt64
- __lzcnt16
- __lzcnt
helpviewer_keywords:
- __lzcnt intrinsic
- lzcnt instruction
- lzcnt16 intrinsic
- lzcnt intrinsic
- __lzcnt16 intrinsic
- lzcnt64 intrinsic
- __lzcnt64 intrinsic
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
ms.openlocfilehash: 75e2c105d05cfe4620f558a4f44c8ae8b9cd6f8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167736"
---
# <a name="__lzcnt16-__lzcnt-__lzcnt64"></a>__lzcnt16, __lzcnt, __lzcnt64

**Microsoft 전용**

16, 32 또는 64 비트 정수에서 앞에 오는 0의 수를 계산 합니다.

## <a name="syntax"></a>구문

```C
unsigned short __lzcnt16(
   unsigned short value
);
unsigned int __lzcnt(
   unsigned int value
);
unsigned __int64 __lzcnt64(
   unsigned __int64 value
);
```

### <a name="parameters"></a>매개 변수

*기본값*\
진행 앞에 오는 0을 검색할 16, 32 또는 64 비트 부호 없는 정수입니다.

## <a name="return-value"></a>반환 값

매개 변수에서 앞에 오는 0 비트의 수입니다 `value` . `value`가 0 이면 반환 값은 입력 피연산자의 크기 (16, 32 또는 64)입니다. 의 가장 중요 한 비트가 1 인 경우 `value` 반환 값은 0입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__lzcnt16`|AMD: 고급 비트 조작 (ABM)<br /><br /> Intel: Haswell|
|`__lzcnt`|AMD: 고급 비트 조작 (ABM)<br /><br /> Intel: Haswell|
|`__lzcnt64`|AMD: 64 비트 모드의 ABM (고급 비트 조작).<br /><br /> Intel: Haswell|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

각 내장 함수는 명령을 생성 합니다 `lzcnt` .  명령이 반환 하는 값의 크기는 `lzcnt` 인수의 크기와 동일 합니다.  32 비트 모드에서는 64 비트 범용 레지스터가 없으므로 64 비트가 `lzcnt` 지원 되지 않습니다.

명령에 대 한 하드웨어 지원을 확인 하려면를 사용 하 여 `lzcnt` 내장 함수를 호출 하 `__cpuid` `InfoType=0x80000001` 고의 비트 5를 확인 `CPUInfo[2] (ECX)` 합니다. 명령이 지원 되는 경우이 비트는 1이 고, 그렇지 않으면 0입니다. 명령을 지원 하지 않는 하드웨어에서 내장 함수를 사용 하는 코드를 실행 하는 경우 `lzcnt` 결과를 예측할 수 없습니다.

명령을 지원 하지 않는 Intel 프로세서에서는 `lzcnt` 명령 바이트 인코딩이 `bsr` (비트 검사 역방향)로 실행 됩니다. 코드 이식성이 중요 한 경우에는 내장 함수를 대신 사용 하는 것이 좋습니다 `_BitScanReverse` . 자세한 내용은 [_BitScanReverse, _BitScanReverse64을](../intrinsics/bitscanreverse-bitscanreverse64.md)참조 하세요.

## <a name="example"></a>예제

```cpp
// Compile this test with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
  unsigned short us[3] = {0, 0xFF, 0xFFFF};
  unsigned short usr;
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};
  unsigned int   uir;

  for (int i=0; i<3; i++) {
    usr = __lzcnt16(us[i]);
    cout << "__lzcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __lzcnt(ui[i]);
    cout << "__lzcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__lzcnt16(0x0) = 16
__lzcnt16(0xff) = 8
__lzcnt16(0xffff) = 0
__lzcnt(0x0) = 32
__lzcnt(0xff) = 24
__lzcnt(0xffff) = 16
__lzcnt(0xffffffff) = 0
```

**Microsoft 전용 종료**

이 콘텐츠의 일부는 Advanced 마이크로 장치, i n c .의 저작권 2007입니다. All rights reserved. 고급 마이크로 장치, i n c .의 권한으로 재현 합니다.

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
