---
title: float_control pragma
description: Float_control 지시문의 사용법과 효과를 설명 합니다 pragma . Float_control 지시문은 런타임에 부동 소수점 정확한 의미 체계 및 예외 의미 체계의 상태를 제어 합니다.
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragma, float_control
no-loc:
- pragma
ms.openlocfilehash: 98695c15424395a9b4e008a5cb1133824e1e7054
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98712767"
---
# <a name="float_control-no-locpragma"></a>`float_control` pragma

함수의 부동 소수점 동작을 지정합니다.

## <a name="syntax"></a>구문

> **`#pragma float_control`**\
> **`#pragma float_control( precise,`** { **`on`** | **`off`** } [ **`, push`** ] **`)`**\
> **`#pragma float_control( except,`** { **`on`** | **`off`** } [ **`, push`** ] **`)`**\
> **`#pragma float_control(`** { **`push`** | **`pop`** } **`)`**

## <a name="options"></a>옵션

**`precise`**, **`on`** | **`off`**, **`push`**\
**`on`** 정확한 부동 소수점 의미 체계를 사용 () 또는 사용 하지 않을 지 () 지정 합니다 **`off`** . 컴파일러 옵션의 차이점에 대 한 자세한 내용은 **`/fp:precise`** 설명 부분을 참조 하세요. 선택적 **`push`** 토큰은 내부 컴파일러 스택에 대 한 현재 설정을 푸시합니다 **`float_control`** .

**`except`**, **`on`** | **`off`**, **`push`**\
**`on`** 부동 소수점 예외 의미 체계를 사용 () 또는 사용 하지 않도록 () 지정 합니다 **`off`** . 선택적 **`push`** 토큰은 내부 컴파일러 스택에 대 한 현재 설정을 푸시합니다 **`float_control`** .

**`except`****`on`** **`precise`** 가로 설정 된 경우에만를로 설정할 수 있습니다 **`on`** .

**`push`**\
현재 **`float_control`** 설정을 내부 컴파일러 스택에 푸시합니다.

**`pop`**\
**`float_control`** 내부 컴파일러 스택 맨 위에서 설정을 제거 하 고 새 **`float_control`** 설정을 만듭니다.

## <a name="remarks"></a>설명

는 **`float_control`** pragma 컴파일러 옵션과 동일한 동작을 포함 하지 않습니다 [`/fp`](../build/reference/fp-specify-floating-point-behavior.md) . 는 **`float_control`** pragma 부동 소수점 동작의 일부를 제어 합니다. [`fp_contract`](../preprocessor/fp-contract.md) [`fenv_access`](../preprocessor/fenv-access.md) pragma 컴파일러 옵션을 다시 만들려면 및 지시문을 함께 사용 해야 합니다 **`/fp`** . 다음 표에서는 pragma 각 컴파일러 옵션에 해당 하는 설정을 보여 줍니다.

| 옵션 | `float_control(precise, *)` | `float_control(except, *)` | `fp_contract(*)` | `fenv_access(*)` |
|-|-|-|-|-|
| `/fp:strict`             | `on`  | `on`  | `off` | `on`  |
| `/fp:precise`            | `on`  | `off` | `on`  | `off` |
| `/fp:fast`               | `off` | `off` | `on`  | `off` |

즉, pragma **`/fp:fast`** **`/fp:precise`** 및 명령줄 옵션을 에뮬레이션 하기 위해 여러 지시문을 조합 하 여 사용 해야 할 수 있습니다 **`/fp:strict`** .

및 부동 소수점 지시문을 조합 하 여 사용할 수 있는 방법에는 다음과 같은 제한 사항이 있습니다 **`float_control`** **`fenv_access`** pragma .

- 정확한 의미 체계를 사용 하도록 설정한 **`float_control`** 경우에만를로 설정할 수 있습니다 **`except`** **`on`** . 에서 **`float_control`** pragma **`/fp:precise`** 또는 컴파일러 옵션을 사용 하 여 정확한 의미 체계를 사용 하도록 설정할 수 있습니다 **`/fp:strict`** .

- **`float_control`** **`precise`** **`float_control`** pragma 또는 컴파일러 옵션에 따라 예외 의미 체계가 사용 되는 경우를 사용 하 여을 해제할 수 없습니다 **`/fp:except`** .

- 또는 컴파일러 옵션을 사용 하 **`fenv_access`** 여 정확한 의미 체계를 사용 하도록 설정 하지 않은 경우에는를 사용할 수 없습니다 **`float_control`** pragma .

- **`float_control`** **`precise`** 가 설정 된 경우를 사용 하 여을 해제할 수 없습니다 **`fenv_access`** .

이러한 제한 사항은 일부 부동 소수점 지시문의 순서가 중요 함을 의미 pragma 합니다. 지시문을 사용 하 여 빠른 모델에서 엄격한 모델로 이동 하려면 pragma 다음 코드를 사용 합니다.

```cpp
#pragma float_control(precise, on)  // enable precise semantics
#pragma fenv_access(on)             // enable environment sensitivity
#pragma float_control(except, on)   // enable exception semantics
#pragma fp_contract(off)            // disable contractions
```

를 사용 하 여 엄격한 모델에서 빠른 모델로 이동 하려면 **`float_control`** pragma 다음 코드를 사용 합니다.

```cpp
#pragma float_control(except, off)  // disable exception semantics
#pragma fenv_access(off)            // disable environment sensitivity
#pragma float_control(precise, off) // disable precise semantics
#pragma fp_contract(on)             // enable contractions
```

옵션을 지정 하지 않으면는 **`float_control`** 영향을 주지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는를 사용 하 여 오버플로 부동 소수점 예외를 catch 하는 방법을 보여 줍니다 pragma **`float_control`** .

```cpp
// pragma_directive_float_control.cpp
// compile with: /EHa
#include <stdio.h>
#include <float.h>

double func( ) {
   return 1.1e75;
}

#pragma float_control (except, on)

int main( ) {
   float u[1];
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);
   if (err != 0)
      printf_s("_controlfp_s failed!\n");

   try  {
      u[0] = func();
      printf_s ("Fail");
      return(1);
   }

   catch (...)  {
      printf_s ("Pass");
      return(0);
   }
}
```

```Output
Pass
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)\
[`fenv_access` pragma](../preprocessor/fenv-access.md)\
[`fp_contract` pragma](../preprocessor/fp-contract.md)
