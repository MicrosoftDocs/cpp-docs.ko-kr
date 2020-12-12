---
description: __Popcnt16, __popcnt, __popcnt64에 대해 자세히 알아보세요.
title: __popcnt16, __popcnt, __popcnt64
ms.date: 09/02/2019
f1_keywords:
- __popcnt64
- __popcnt
- __popcnt16
helpviewer_keywords:
- popcnt instruction
- __popcnt16
- __popcnt64
- __popcnt
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
ms.openlocfilehash: cb95ff09d589cfd9a9cfc438d0334cf68f073825
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257526"
---
# <a name="__popcnt16-__popcnt-__popcnt64"></a>__popcnt16, __popcnt, __popcnt64

**Microsoft 전용**

`1`16, 32 또는 64 비트 부호 없는 정수에서 비트 수 (모집단 수)를 계산 합니다.

## <a name="syntax"></a>구문

```C
unsigned short __popcnt16(
   unsigned short value
);
unsigned int __popcnt(
   unsigned int value
);
unsigned __int64 __popcnt64(
   unsigned __int64 value
);
```

### <a name="parameters"></a>매개 변수

*기본값*\
진행 모집단 개수를 원하는 16, 32 또는 64 비트의 부호 없는 정수입니다.

## <a name="return-value"></a>반환 값

`1` *값* 매개 변수의 비트 수입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__popcnt16`|고급 비트 조작|
|`__popcnt`|고급 비트 조작|
|`__popcnt64`|64 비트 모드의 고급 비트 조작입니다.|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

각 내장 함수는 명령을 생성 합니다 `popcnt` . 32 비트 모드에서는 64 비트 범용 레지스터가 없으므로 64 비트가 `popcnt` 지원 되지 않습니다.

명령에 대 한 하드웨어 지원을 확인 하려면를 사용 하 여 `popcnt` 내장 함수를 호출 하 `__cpuid` `InfoType=0x00000001` 고 비트 23을 확인 `CPUInfo[2] (ECX)` 합니다. 명령이 지원 되는 경우이 비트는 1이 고, 그렇지 않으면 0입니다. 명령을 지원 하지 않는 하드웨어에서 이러한 내장 함수를 사용 하는 코드를 실행 하는 경우 `popcnt` 결과를 예측할 수 없습니다.

## <a name="example"></a>예제

```cpp
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
    usr = __popcnt16(us[i]);
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __popcnt(ui[i]);
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__popcnt16(0x0) = 0
__popcnt16(0xff) = 8
__popcnt16(0xffff) = 16
__popcnt(0x0) = 0
__popcnt(0xff) = 8
__popcnt(0xffff) = 16
__popcnt(0xffffffff) = 32
```

**Microsoft 전용 종료**

Advanced 마이크로 장치, i n c .의 저작권 2007 부분 All rights reserved. 고급 마이크로 장치, i n c .의 권한으로 재현 합니다.

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
