---
title: /fp(부동 소수점 동작 지정)
ms.date: 11/09/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
ms.openlocfilehash: 7a8ae885bbbf00ae916505bf5df646b32268a17a
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040914"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp(부동 소수점 동작 지정)

컴파일러가 부동 소수점 식, 최적화 및 예외를 처리 하는 방법을 지정 합니다. **/Fp** 옵션은 생성 된 코드에서 부동 소수점 환경에서 반올림 모드, 예외 마스크 및 subnormal 동작을 변경할 수 있는지 여부와 부동 소수점 상태 검사에서 현재의 정확한 결과를 반환할지 여부를 지정 합니다. 이 클래스는 컴파일러가 소스 작업 및 식 순서를 유지 관리 하 고 NaN 전파를 위한 표준을 준수 하는 코드를 생성할지 여부를 제어 하거나, 작업의 순서를 변경 하거나 결합 하 고 표준에서 허용 되지 않는 대 수 변환을 간소화 하는 데 사용할 수 있는 보다 효율적인 코드를 생성 합니다.

## <a name="syntax"></a>구문

> **/fp:**[**정확한**  |  **strict**  |  **fast**  |  **except**([ **-** ]] 제외)

### <a name="arguments"></a>인수

#### <a name="precise"></a>set

기본적으로 컴파일러는 동작을 사용 `/fp:precise` 합니다.

`/fp:precise`컴파일러는 대상 컴퓨터에 대 한 개체 코드를 생성 하 고 최적화할 때 부동 소수점 코드의 소스 식 순서 및 반올림 속성을 유지 합니다. 컴파일러는 식 계산 중 네 개의 특정 지점에서 소스 코드 전체 자릿수로 반올림 합니다. 즉, 대입문에서 부동 소수점 인수가 함수 호출에 전달 되 면이 고, 함수 호출에서 부동 소수점 값이 반환 될 때 발생 합니다. 중간 계산은 컴퓨터 전체 자릿수에서 수행할 수 있습니다. 대입문를 사용 하 여 중간 계산을 명시적으로 반올림할 수 있습니다.

변환이 비트 동일한 결과를 생성 하는 것이 보장 되지 않는 한, 컴파일러는 다시 연결 또는 대 수 같은 부동 소수점 식에 대 한 변환을 수행 하지 않습니다.
특수 값 (NaN, + infinity,-infinity,-0.0)을 포함 하는 식은 IEEE 754 사양에 따라 처리 됩니다. 예를 들어 `x != x` **`true`** 는 x가 NaN 인 경우로 평가 됩니다. 부동 소수점 *축약*, 즉 부동 소수점 작업을 결합 하는 컴퓨터 명령은에서 생성할 수 있습니다 `/fp:precise` .

컴파일러는 [기본 부동 소수점 환경](#the-default-floating-point-environment) 에서 실행 되도록 작성 된 코드를 생성 하 고 런타임에 부동 소수점 환경에 액세스 하거나 수정 하지 않는 것으로 가정 합니다. 즉, 코드에서 부동 소수점 예외를 마스크 해제 하거나, 부동 소수점 상태 레지스터를 읽거나 쓰거나, 반올림 모드를 변경 하지 않는 것으로 가정 합니다.

부동 소수점 코드가 부동 소수점 문의 연산과 식 순서에 의존 하지 않는 경우 (예:가 또는로 계산 되었는지 여부를 고려 하지 않는 경우)에는 `a * b + a * c` `(b + c) * a` `2 * a` `a + a` [/fp: fast](#fast) 옵션을 고려 하 여 보다 빠르고 효율적인 코드를 생성할 수 있습니다. 코드가 작업 및 식의 순서에 따라 달라 지 고 부동 소수점 환경에 액세스 하거나 변경 하는 경우 (예: 반올림 모드 변경 또는 부동 소수점 예외 트래핑) [/fp: strict](#strict)를 사용 합니다.

#### <a name="strict"></a>strict

`/fp:strict` 는와 유사 `/fp:precise` 합니다. 즉, 컴파일러는 대상 컴퓨터에 대 한 개체 코드를 생성 하 고 최적화 하 고 특수 값을 처리할 때 표준을 관찰 하는 부동 소수점 코드의 소스 순서 및 반올림 속성을 유지 합니다. 또한 프로그램은 런타임에 부동 소수점 환경에 안전 하 게 액세스 하거나 수정할 수 있습니다.

에서 `/fp:strict` 컴파일러는 프로그램에서 부동 소수점 예외를 안전 하 게 마스크 해제 하거나, 부동 소수점 상태 레지스터를 읽거나 쓰거나, 반올림 모드를 변경할 수 있도록 하는 코드를 생성 합니다. 식 계산 중에 대입문에서 부동 소수점 인수가 함수 호출에 전달 될 때 및 함수 호출에서 부동 소수점 값이 반환 될 때 식 계산 중 네 개의 특정 지점에서 소스 코드 전체 자릿수를 반올림 합니다. 중간 계산은 컴퓨터 전체 자릿수에서 수행할 수 있습니다. 대입문를 사용 하 여 중간 계산을 명시적으로 반올림할 수 있습니다. 변환이 비트 동일한 결과를 생성 하는 것이 보장 되지 않는 한, 컴파일러는 다시 연결 또는 대 수 같은 부동 소수점 식에 대 한 변환을 수행 하지 않습니다. 특수 값 (NaN, + infinity,-infinity,-0.0)을 포함 하는 식은 IEEE 754 사양에 따라 처리 됩니다. 예를 들어 `x != x` **`true`** 는 x가 NaN 인 경우로 평가 됩니다. 부동 소수점 축약은에서 생성 되지 않습니다 `/fp:strict` .

`/fp:strict` 는 `/fp:precise` 컴파일러에서 예외를 트래핑 하는 추가 명령을 삽입 해야 하 고 런타임에 프로그램에서 부동 소수점 환경에 액세스 하거나 수정할 수 있도록 하는 것 보다 계산 비용이 더 많이 듭니다. 코드에서이 기능을 사용 하지 않고 소스 코드 순서 지정 및 반올림이 필요 하거나 특수 값을 사용 하는 경우를 사용 `/fp:precise` 합니다. 그렇지 않으면 `/fp:fast` 더 빠르고 작은 코드를 생성할 수 있는를 사용 하는 것이 좋습니다.

#### <a name="fast"></a>빠르지

`/fp:fast`옵션을 사용 하면 컴파일러에서 부동 소수점 작업의 순서를 변경 하거나 결합 하거나 단순화 하 여 속도 및 공간에 대해 부동 소수점 코드를 최적화할 수 있습니다. 컴파일러는 할당 문, 대입문 또는 함수 호출에서 반올림을 생략할 수 있습니다. 예를 들어, 결합성을 사용 하 여 작업 순서를 변경 하거나 대 수 변환을 수행할 수 있습니다. 예를 들어, 이러한 변환으로 인해 다른 반올림 동작이 띄는 경우에도 마찬가지입니다. 이러한 향상 된 최적화로 인해 일부 부동 소수점 계산의 결과는 다른 옵션에 의해 생성 된 것과 다를 수 있습니다 `/fp` . 특수 값 (NaN, + infinity,-infinity,-0.0)은 IEEE-754 표준에 따라 완전히 전파 되거나 동작 하지 않을 수 있습니다. 에서 부동 소수점 축약 생성 될 수 있습니다 `/fp:fast` . 컴파일러는의 기본 아키텍처에 의해 계속 바인딩되어 `/fp:fast` 있으므로 [/arch](arch-minimum-cpu-architecture.md) 옵션을 사용 하 여 추가 최적화를 사용할 수 있습니다.

에서 `/fp:fast` 컴파일러는 기본 부동 소수점 환경에서 실행 하기 위한 코드를 생성 하 고 런타임에 부동 소수점 환경이 액세스 또는 수정 되지 않는다고 가정 합니다. 즉, 코드에서 부동 소수점 예외를 마스크 해제 하거나, 부동 소수점 상태 레지스터를 읽거나 쓰거나, 반올림 모드를 변경 하지 않는 것으로 가정 합니다.

`/fp:fast` 는 엄격한 소스 코드 순서 지정 및 부동 소수점 식의 반올림이 필요 하지 않으며 NaN과 같은 특수 한 값을 처리 하기 위한 표준 규칙을 사용 하지 않는 프로그램을 위한 것입니다. 부동 소수점 코드에서 소스 코드 순서 지정 및 반올림을 유지 해야 하거나 특수 값의 표준 동작에 의존 하는 경우에는 [/fp: precise](#precise)를 사용 합니다. 코드에서 부동 소수점 환경을 액세스 하거나 수정 하 여 반올림 모드를 변경 하거나 부동 소수점 예외의 마스크를 해제 하거나 부동 소수점 상태를 확인 하는 경우 [/fp: strict](#strict)를 사용 합니다.

#### <a name="except"></a>except

옵션은 마스크 되지 않은 `/fp:except` 부동 소수점 예외가 발생 한 정확한 지점에서 발생 하 고 추가 부동 소수점 예외가 발생 하지 않도록 하는 코드를 생성 합니다. 기본적으로이 `/fp:strict` 옵션은을 사용 하도록 설정 하 `/fp:except` 고는 `/fp:precise` 지원 하지 않습니다. `/fp:except`옵션은와 호환 되지 않습니다 `/fp:fast` . 이 옵션은에서 명시적으로 사용 하지 않도록 설정할 수 있습니다 `/fp:except-` .

에서 `/fp:except` 부동 소수점 예외를 단독으로 사용 하도록 설정 하지는 않지만 프로그램에서 부동 소수점 예외를 사용 하도록 설정 해야 합니다. 부동 소수점 예외를 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 를 참조 하세요.

## <a name="remarks"></a>설명

`/fp`동일한 컴파일러 명령줄에서 여러 옵션을 지정할 수 있습니다. `/fp:strict`, 및 옵션 중 하나만 한 `/fp:fast` 번에 `/fp:precise` 적용 될 수 있습니다. 명령줄에 이러한 옵션을 두 개 이상 지정 하면 이후 옵션이 우선적으로 적용 되 고 컴파일러에서 경고를 생성 합니다. `/fp:strict`및 `/fp:except` 옵션은와 호환 되지 않습니다 `/clr` .

[/Za](za-ze-disable-language-extensions.md) (ANSI 호환성) 옵션은와 호환 되지 않습니다 `/fp` .

### <a name="using-compiler-directives-to-control-floating-point-behavior"></a>컴파일러 지시문을 사용 하 여 부동 소수점 동작 제어

컴파일러는 명령줄에 지정 된 부동 소수점 동작 [float_control](../../preprocessor/float-control.md), [fenv_access](../../preprocessor/fenv-access.md)및 [fp_contract](../../preprocessor/fp-contract.md)를 재정의 하는 세 가지 pragma 지시문을 제공 합니다. 이러한 지시문을 사용 하 여 함수 내에서가 아니라 함수 수준에서 부동 소수점 동작을 제어할 수 있습니다. 이러한 지시문은 옵션과 직접 일치 하지 않습니다 `/fp` . 다음 표에서는 `/fp` options 및 pragma 지시문이 서로 매핑되는 방법을 보여 줍니다. 자세한 내용은 개별 옵션 및 pragma 지시문에 대 한 설명서를 참조 하세요.

| 옵션 | float_control (정확한) | float_control (제외) | fenv_access | fp_contract |
|-|-|-|-|-|
|`/fp:fast`|끄기|끄기|끄기|On|
|`/fp:precise`|on|끄기|끄기|On|
|`/fp:strict`|On|On|on|끄기|

### <a name="the-default-floating-point-environment"></a>기본 부동 소수점 환경

프로세스가 초기화 되 면 *기본 부동 소수점 환경이* 설정 됩니다. 이 환경은 모든 부동 소수점 예외를 마스킹 하 고, 반올림 모드를 가장 가까이 ()로 설정 하 고,, `FE_TONEAREST` 및 값에 대 한 significand (가 수)의 기본 전체 자릿수 (denormal)를 사용 하며, 지원 되는 경우 **`float`** **`double`** **`long double`** infinity 컨트롤을 기본 상관 모드로 설정 합니다.

### <a name="floating-point-environment-access-and-modification"></a>부동 소수점 환경 액세스 및 수정

Microsoft Visual C++ 런타임은 부동 소수점 환경에 액세스 하 고 수정 하는 여러 함수를 제공 합니다. 여기에는 [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md), [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)및 [_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md) 와 해당 변형이 포함 됩니다. 코드가 부동 소수점 환경을 액세스 하거나 수정 하는 경우 올바른 프로그램 동작을 보장 하려면를 사용 `fenv_access` 하거나 pragma를 사용 하 여 `/fp:strict` `fenv_access` 이러한 함수에 영향을 주지 않도록 해야 합니다. `fenv_access`을 사용 하도록 설정 하지 않으면 부동 소수점 환경에 대 한 액세스 또는 수정으로 인해 예기치 않은 프로그램 동작이 발생할 수 있습니다. 코드에서 부동 소수점 환경에 대 한 요청 된 변경 내용을 인식 하지 못할 수 있습니다. 부동 소수점 상태 레지스터는 예상 또는 현재 결과를 보고 하지 않을 수 있으며, 예기치 않은 부동 소수점 예외가 발생 하거나 예상 된 부동 소수점 예외가 발생 하지 않을 수 있습니다.

코드가 부동 소수점 환경을 액세스 하거나 수정 하는 경우를 사용 하도록 설정 `fenv_access` 하지 않은 코드를 사용 하도록 설정 하는 코드를 결합할 때 주의 해야 합니다 `fenv_access` . `fenv_access`가 사용 하도록 설정 되지 않은 코드에서 컴파일러는 플랫폼 기본 부동 소수점 환경이 적용 되 고 있고 부동 소수점 상태가 액세스 또는 수정 되지 않는다고 가정 합니다. 컨트롤이 사용 하도록 설정 되지 않은 함수로 전송 되기 전에 로컬 부동 소수점 환경을 기본 상태로 저장 하 고 복원 하는 것이 좋습니다 `fenv_access` . 이 예제에서는 pragma를 `float_control` 설정 하 고 복원 하는 방법을 보여 줍니다.

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>부동 소수점 반올림 모드

및 둘 다에서 `/fp:precise` `/fp:fast` 컴파일러는 기본 부동 소수점 환경에서 실행 되도록 작성 된 코드를 생성 하 고, 런타임에 환경을 액세스 하거나 수정 하지 않는 것으로 가정 합니다. 즉, 코드에서 부동 소수점 예외를 마스크 해제 하거나, 부동 소수점 상태 레지스터를 읽거나 쓰거나, 반올림 모드를 변경 하지 않는 것으로 가정 합니다.  그러나 일부 프로그램은 부동 소수점 환경을 변경 해야 합니다. 예를 들어이 샘플에서는 부동 소수점 반올림 모드를 변경 하 여 부동 소수점 곱셈의 오류 경계를 계산 합니다.

```cpp
// fp_error_bounds.cpp
#include <iostream>
#include <limits>
using namespace std;

int main(void)
{
    float a = std::<float>::max();
    float b = -1.1;
    float cLower = 0.0;
    float cUpper = 0.0;
    unsigned int control_word = 0;
    int err = 0;

    // compute lower error bound.
    // set rounding mode to -infinity.
    err = _controlfp_s(&control_word, _RC_DOWN, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_DOWN, _MCW_RC) failed with error:" << err << endl;
    }  
    cLower = a * b;

    // compute upper error bound.
    // set rounding mode to +infinity.
    err = _controlfp_s(&control_word, _RC_UP, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_UP, _MCW_RC) failed with error:" << err << endl;
    }
    cUpper = a * b;

    // restore default rounding mode.
    err = _controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC) failed with error:" << err << endl;
    }
    // display error bounds.
    cout << "cLower = " << cLower << endl;
    cout << "cUpper = " << cUpper << endl;
    return 0;
}
```

컴파일러가에서 기본 부동 소수점 환경을 사용 한다고 가정 하므로 `/fp:fast` `/fp:precise` 에 대 한 호출을 무시할 수 `_controlfp_s` 있습니다. 예를 들어 x86 아키텍처에 대해 및를 모두 사용 하 여 컴파일하면 `/O2` `/fp:precise` 범위가 계산 되지 않으며 샘플 프로그램은 다음을 출력 합니다.

```Output
cLower = -inf
cUpper = -inf
```

X86 아키텍처에 대해 및를 모두 사용 하 여 컴파일하면 `/O2` `/fp:strict` 샘플 프로그램이 다음을 출력 합니다.

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>부동 소수점 특수 값

`/fp:precise`및 `/fp:strict` 에서는 특수 값 (NaN, + infinity,-infinity,-0.0)이 포함 된 식이 IEEE 754 사양에 따라 동작 합니다. 에서 `/fp:fast` 이러한 특수 값의 동작은 IEEE-754와 일치 하지 않을 수 있습니다.

이 샘플에서는, 및에서 특수 값의 다른 동작을 보여 줍니다 `/fp:precise` `/fp:strict` `/fp:fast` .

```cpp
// fp_special_values.cpp
#include <stdio.h>
#include <cmath>

float gf0 = -0.0;

int main()
{
    float f1 = INFINITY;
    float f2 = NAN;
    float f3 = -INFINITY;
    bool a, b;
    float c, d, e;
    a = (f1 == f1);
    b = (f2 == f2);
    c = (f1 - f1);
    d = (f2 - f2);
    printf("INFINITY == INFINITY : %d\n", a);
    printf("NAN == NAN           : %d\n", b);
    printf("INFINITY - INFINITY  : %f\n", c);
    printf("NAN - NAN            : %f\n", d);

    e = gf0 / abs(f3);
    printf("std::signbit(-0.0/-INFINITY): %d\n", std::signbit(c));
    return 0;
}
```

또는 x 86 아키텍처를 사용 하 여 컴파일할 때 `/O2` `/fp:precise` `/O2` `/fp:strict` 출력은 IEEE-754 사양과 일치 합니다.

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

`/O2` `/fp:fast` X86 아키텍처용으로 컴파일하면 출력이 IEEE-754와 일치 하지 않습니다.

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>부동 소수점 대 수 변환

`/fp:precise`및에서 `/fp:strict` 컴파일러가 비트 동일한 결과를 생성 하는 것이 보장 되지 않는 한 수학적 변환을 수행 하지 않습니다. 컴파일러는에서 이러한 변환을 수행할 수 있습니다 `/fp:fast` . 예를 들어 `a * b + a * c` 샘플 함수의 식은 `algebraic_transformation` 에서로 컴파일될 수 있습니다 `a * (b + c)` `/fp:fast` . 이러한 변환은 또는에서 수행 `/fp:precise` 되지 `/fp:strict` 않으며 컴파일러는을 생성 `a * b + a * c` 합니다.

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>부동 소수점 명시적 캐스팅 지점

`/fp:precise`및 `/fp:strict` 에서는 컴파일러가 식 계산 중 네 개의 특정 지점에서 소스 코드 전체 자릿수로 반올림 합니다. 즉, 대입문에서 부동 소수점 인수가 함수 호출에 전달 되 고 함수 호출에서 부동 소수점 값이 반환 될 때 발생 합니다. 대입문를 사용 하 여 중간 계산을 명시적으로 반올림할 수 있습니다. 에서 `/fp:fast` 컴파일러는 소스 코드 전체 자릿수를 보장 하기 위해 이러한 지점에서 명시적 캐스팅을 생성 하지 않습니다. 이 샘플에서는 다음과 같은 다양 한 옵션의 동작을 보여 줍니다 `/fp` .

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

또는를 사용 하 여 컴파일한 경우 `/O2` `/fp:precise` `/O2` `/fp:strict` 형식 캐스팅 및 x64 아키텍처에 대해 생성 된 코드의 함수 반환 지점에 명시적 형식 캐스팅이 삽입 된 것을 볼 수 있습니다.

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

`/O2` `/fp:fast` 모든 형식 캐스팅이 최적화 되기 때문에 생성 된 코드 아래에서 단순화 됩니다.

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **코드 생성** 속성 페이지를 선택 합니다.

1. 부동 소수점 **모델** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)<br/>
