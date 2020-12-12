---
description: '다음에 대 한 자세한 정보: fp_contract pragma'
title: fp_contract pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
ms.openlocfilehash: cefcf0519f08b3fd68a0f8b464938ea7cdbda6d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261179"
---
# <a name="fp_contract-pragma"></a>fp_contract pragma

부동 소수점 축약 발생 하는지 여부를 확인 합니다. 부동 소수점 축약은 별도의 두 부동 소수점 연산을 단일 명령으로 결합 하는 FMA (퓨즈-곱하기-더하기)와 같은 명령입니다. 이러한 지침을 사용 하면 각 작업 후에 반올림 하는 대신 프로세서가 두 작업 후에 한 번만 반올림할 수 있으므로 부동 소수점 정밀도에 영향을 줄 수 있습니다.

## <a name="syntax"></a>Syntax

> **#pragma fp_contract (** { **on**  |  **off** } **)**

## <a name="remarks"></a>설명

기본적으로 **fp_contract** 는 **설정** 되어 있습니다. 이렇게 하면 가능한 경우 부동 소수점 축약 명령을 사용 하도록 컴파일러에 지시 합니다. 개별 부동 소수점 명령을 유지 하려면 **fp_contract** 을 **off** 로 설정 합니다.

부동 소수점 동작에 대 한 자세한 내용은 [/fp (Floating-Point 동작 지정)](../build/reference/fp-specify-floating-point-behavior.md)를 참조 하세요.

다른 부동 소수점 pragma는 다음과 같습니다.

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>예제

이 샘플에서 생성 된 코드는 대상 프로세서에서 사용할 수 있는 경우에도 퓨즈-곱하기-추가 명령을 사용 하지 않습니다. 주석 처리 하는 경우 `#pragma fp_contract (off)` 생성 된 코드에서 사용할 수 있는 경우에는 퓨즈-곱하기-추가 명령을 사용할 수 있습니다.

```cpp
// pragma_directive_fp_contract.cpp
// on x86 and x64 compile with: /O2 /fp:fast /arch:AVX2
// other platforms compile with: /O2

#include <stdio.h>

// remove the following line to enable FP contractions
#pragma fp_contract (off)

int main() {
   double z, b, t;

   for (int i = 0; i < 10; i++) {
      b = i * 5.5;
      t = i * 56.025;

      z = t * i + b;
      printf("out = %.15e\n", z);
   }
}
```

```Output
out = 0.000000000000000e+00
out = 6.152500000000000e+01
out = 2.351000000000000e+02
out = 5.207249999999999e+02
out = 9.184000000000000e+02
out = 1.428125000000000e+03
out = 2.049900000000000e+03
out = 2.783725000000000e+03
out = 3.629600000000000e+03
out = 4.587525000000000e+03
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
