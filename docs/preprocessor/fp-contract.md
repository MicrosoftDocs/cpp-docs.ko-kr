---
title: fp_contract | Microsoft Docs
ms.custom: ''
ms.date: 03/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95f23fa132a263970047a480ccde37382b6d03de
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052166"
---
# <a name="fpcontract"></a>fp_contract

부동 소수점 축약 발생 여부를 결정 합니다. 부동 소수점 축약은 별도 단일 명령으로 부동 두 지점 작업을 결합 하는 FMA (Fused-곱셈-덧셈)와 같은 명령입니다. 이러한 명령을 사용 하 여 각 작업이 끝난 후 반올림 하는 대신 프로세서 반올림할 수 한 번만 모두 작업 후 때문에 부동 소수점 정밀도만을 달라질 수 있습니다.

## <a name="syntax"></a>구문

> **#pragma fp_contract (** {0} **온** | **해제** } **)**

## <a name="remarks"></a>설명

기본적으로 **fp_contract** 됩니다 **에서**합니다. 이 가능한 경우 부동 소수점 축약 지침을 사용 하도록 컴파일러에 지시 합니다. 설정할 **fp_contract** 하 **해제** 개별 부동 소수점 명령을 유지 하려면.

부동 소수점 동작에 대 한 자세한 내용은 참조 하세요. [/fp (부동 소수점 동작 지정)](../build/reference/fp-specify-floating-point-behavior.md)합니다.

다른 부동 소수점 pragma는 다음과 같습니다.

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>예제

이 샘플에서 생성 된 코드는 대상 프로세서에서 사용할 수 있는 경우에 fused-곱셈-덧셈 지침을 사용 하지 않습니다. 주석으로 처리 하는 경우 `#pragma fp_contract (off)`, 생성된 된 코드는 사용 가능한 경우 fused-곱셈-덧셈 명령을 사용할 수 있습니다.

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

## <a name="see-also"></a>참고자료

[Pragma 지시문 및 __Pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
