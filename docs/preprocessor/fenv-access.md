---
title: fenv_access pragma
description: Fenv_access 지시문의 사용법과 효과를 설명 합니다 pragma . Fenv_access 지시문은 런타임에 부동 소수점 환경에 대 한 액세스를 제어 합니다.
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragma, fenv_access
- fenv_access pragma
no-loc:
- pragma
ms.openlocfilehash: be33bbf9de381850ec78ece204d117ebc537152b
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713664"
---
# <a name="fenv_access-no-locpragma"></a>`fenv_access` pragma

부동 소수점 **`on`** **`off`** 환경 플래그 테스트 및 모드 변경을 변경할 수 있는 () 또는 () 최적화를 사용 하지 않도록 설정 합니다.

## <a name="syntax"></a>구문

> **`#pragma fenv_access (`** { **`on`** | **`off`** } **`)`**

## <a name="remarks"></a>설명

기본적으로 **`fenv_access`** 는 **`off`** 입니다. 컴파일러는 코드가 부동 소수점 환경을 액세스 하거나 조작 하지 않는다고 가정 합니다. 환경 액세스가 필요 하지 않은 경우 컴파일러는 부동 소수점 코드를 최적화 하기 위해 더 많은 작업을 수행할 수 있습니다.

**`fenv_access`** 코드에서 부동 소수점 상태 플래그, 예외를 테스트 하거나 제어 모드 플래그를 설정 하는 경우 사용 하도록 설정 합니다. 컴파일러가 부동 소수점 최적화를 사용 하지 않도록 설정 하므로 코드가 부동 소수점 환경에 일관 되 게 액세스할 수 있습니다.

[/Fp: strict] 명령줄 옵션은 자동으로 사용 하도록 설정 **`fenv_access`** 합니다. 이 부동 소수점 동작에 대 한 자세한 내용은 [/fp (Floating-Point 동작 지정)](../build/reference/fp-specify-floating-point-behavior.md)를 참조 하세요.

**`fenv_access`** 다른 부동 소수점 설정과 함께를 사용할 수 있는 방법에 대 한 제한 사항이 있습니다 pragma .

- **`fenv_access`** 정확한 의미 체계를 사용 하도록 설정 하지 않으면를 사용 하도록 설정할 수 없습니다. 에서 [`float_control`](float-control.md) pragma [`/fp:precise`](../build/reference/fp-specify-floating-point-behavior.md) 또는 컴파일러 옵션을 사용 하 여 정확한 의미 체계를 사용 하도록 설정할 수 있습니다 [`/fp:strict`](../build/reference/fp-specify-floating-point-behavior.md) . **`/fp:precise`** 다른 부동 소수점 명령줄 옵션이 지정 되지 않은 경우 컴파일러는 기본적으로로 설정 됩니다.

- **`float_control`** 가 설정 된 경우를 사용 하 여 정확한 의미 체계를 비활성화할 수 없습니다 **`fenv_access(on)`** .

에 적용 되는 최적화의 종류는 **`fenv_access`** 다음과 같습니다.

- 전역 공통 하위 식 제거

- 코드 이동

- 상수 정리

다른 부동 소수점 pragma 지시문은 다음과 같습니다.

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>예

이 예제에서는 **`fenv_access`** 를로 설정 **`on`** 하 여 24 비트 전체 자릿수에 대 한 부동 소수점 제어 레지스터를 설정 합니다.

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2 /arch:IA32
// processor: x86
#include <stdio.h>
#include <float.h>
#include <errno.h>
#pragma fenv_access (on)

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=9.999999776482582e-03
```

이전 샘플에서 주석 처리 하는 경우 `#pragma fenv_access (on)` 출력은 다릅니다. 컴파일러는 컴파일 시간 평가를 수행 하므로 컨트롤 모드를 사용 하지 않기 때문입니다.

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2 /arch:IA32
#include <stdio.h>
#include <float.h>

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=1.000000000000000e-02
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
