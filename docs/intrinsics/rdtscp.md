---
description: '다음에 대 한 자세한 정보: __rdtscp'
title: __rdtscp
ms.date: 09/02/2019
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: 511d0f1001c218fd838d4bb315fe8c95f10eb3bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257495"
---
# <a name="__rdtscp"></a>__rdtscp

**Microsoft 전용**

는 `rdtscp` 메모리에 대 한 명령을 생성 하 고,는 `TSC_AUX[31:0` 64 비트 타임 스탬프 카운터를 반환 합니다 ( `TSC)` 결과).

## <a name="syntax"></a>구문

```C
unsigned __int64 __rdtscp(
   unsigned int * AUX
);
```

### <a name="parameters"></a>매개 변수

*AUX*\
제한이 컴퓨터별 레지스터의 콘텐츠를 포함 하는 위치에 대 한 포인터입니다 `TSC_AUX[31:0]` .

## <a name="return-value"></a>반환 값

64 비트 부호 없는 정수 틱 수입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__rdtscp`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

`__rdtscp`내장 함수는 명령을 생성 합니다 `rdtscp` . 이 명령에 대 한 하드웨어 지원을 확인 하려면를 사용 하 여 내장 함수를 호출 하 `__cpuid` `InfoType=0x80000001` 고 비트 27를 확인 `CPUInfo[3] (EDX)` 합니다. 명령이 지원 되는 경우이 비트는 1이 고, 그렇지 않으면 0입니다.  명령을 지원 하지 않는 하드웨어에서 내장 함수를 사용 하는 코드를 실행 하는 경우 `rdtscp` 결과를 예측할 수 없습니다.

이 명령은 모든 이전 명령이 실행 되 고 모든 이전 로드가 전역적으로 표시 될 때까지 대기 합니다. 그러나 직렬화 명령이 아닙니다. 자세한 내용은 Intel 및 AMD 설명서를 참조 하십시오.

에서 값의 의미는 `TSC_AUX[31:0]` 운영 체제에 따라 달라 집니다.

## <a name="example"></a>예제

```cpp
#include <intrin.h>
#include <stdio.h>
int main()
{
    unsigned __int64 i;
    unsigned int ui;
    i = __rdtscp(&ui);
    printf_s("%I64d ticks\n", i);
    printf_s("TSC_AUX was %x\n", ui);
}
```

```Output
3363423610155519 ticks
TSC_AUX was 0
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__rdtsc](../intrinsics/rdtsc.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
