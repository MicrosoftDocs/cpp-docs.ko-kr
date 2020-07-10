---
title: intrinsic pragma
description: MSVC 내장 pragma는 내장 함수로 사용할 지원 되는 내장 함수를 지정 하는 데 사용 됩니다.
ms.date: 07/08/2020
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
ms.openlocfilehash: 31f4ebc2fdd4c5c984160d441b4e0a723c686a46
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180957"
---
# <a name="intrinsic-pragma"></a>`intrinsic` pragma

pragma의 인수 목록에 지정된 함수에 대한 호출을 내장 함수로 지정합니다.

## <a name="syntax"></a>구문

> **`#pragma intrinsic(`** *`function1`* [**`,`** _`function2`_ ... ] **`)`**

## <a name="remarks"></a>설명

**`intrinsic`** Pragma는 함수에 알려진 동작이 있음을 컴파일러에 알립니다. 컴파일러는 함수를 호출할 수 있으며 성능을 개선할 수 있는 경우 함수 호출을 인라인 명령으로 바꾸지 않을 수 있습니다.

아래에 내장 형식의 라이브러리 함수가 나와 있습니다. **`intrinsic`** Pragma가 표시 되 면 지정 된 내장 함수를 포함 하는 첫 번째 함수 정의에서 적용 됩니다. 효과는 소스 파일의 끝 이나 동일한 내장 함수를 지정 하는 pragma의 모양으로 계속 됩니다 `function` . **`intrinsic`** Pragma는 전역 수준에서 함수 정의 외부 에서만 사용할 수 있습니다.

다음 함수에는 내장 형식이 있으며 다음을 지정할 때 내장 형식이 사용 됩니다 [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) .

|  |  |  |  |
|--|--|--|--|
| [`_disable`](../intrinsics/disable.md) | [`_outp`](../c-runtime-library/outp-outpw-outpd.md) | [`fabs`](../c-runtime-library/reference/fabs-fabsf-fabsl.md) | [`strcmp`](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md) |
| [`_enable`](../intrinsics/enable.md) | [`_outpw`](../c-runtime-library/outp-outpw-outpd.md) | [`labs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md) | [`strcpy`](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md) |
| [`_inp`](../c-runtime-library/inp-inpw-inpd.md) | [`_rotl`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md) | [`memcmp`](../c-runtime-library/reference/memcmp-wmemcmp.md) | [`strlen`](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md) |
| [`_inpw`](../c-runtime-library/inp-inpw-inpd.md) | [`_rotr`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md) | [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md) |  |
| [`_lrotl`](../c-runtime-library/reference/lrotl-lrotr.md) | [`_strset`](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md) | [`memset`](../c-runtime-library/reference/memset-wmemset.md) |  |
| [`_lrotr`](../c-runtime-library/reference/lrotl-lrotr.md) | [`abs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md) | [`strcat`](../c-runtime-library/reference/strcat-wcscat-mbscat.md) |  |

내장 함수를 사용 하는 프로그램은 함수 호출의 오버 헤드가 없기 때문에 더 빠릅니다. 그러나 생성 된 추가 코드로 인해 크기가 커질 수 있습니다.

### <a name="x86-specific-example"></a>x86 관련 예제

`_disable`및 `_enable` 내장 함수는 인터럽트를 사용 하거나 사용 하지 않도록 커널 모드 명령을 생성 하며 커널 모드 드라이버에 유용할 수 있습니다.

명령줄에서를 사용 하 여 다음 코드를 컴파일하고를 `cl -c -FAs sample.c` 확인 *`sample.asm`* 하 여 X86 명령 CLI 및 STI로 전환 합니다.

```cpp
// pragma_directive_intrinsic.cpp
// processor: x86
#include <dos.h>   // definitions for _disable, _enable
#pragma intrinsic(_disable)
#pragma intrinsic(_enable)
void f1(void) {
   _disable();
   // do some work here that should not be interrupted
   _enable();
}
int main() {
}
```

### <a name="intrinsic-floating-point-functions"></a>내장 부동 소수점 함수

이러한 부동 소수점 함수는 진정한 내장 형식이 아닙니다. 대신 스택에 인수를 푸시하는 대신 부동 소수점 칩에 직접 인수를 전달 하는 버전이 있습니다.

|  |  |  |  |
|--|--|--|--|
| [`acos`](../c-runtime-library/reference/acos-acosf-acosl.md) | [`cosh`](../c-runtime-library/reference/cosh-coshf-coshl.md) | [`pow`](../c-runtime-library/reference/pow-powf-powl.md) | [`tanh`](../c-runtime-library/reference/tanh-tanhf-tanhl.md) |
| [`asin`](../c-runtime-library/reference/asin-asinf-asinl.md) | [`fmod`](../c-runtime-library/reference/fmod-fmodf.md) | [`sinh`](../c-runtime-library/reference/sinh-sinhf-sinhl.md) |  |

이러한 부동 소수점 함수는 [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) 및 [`/fp:fast`](../build/reference/fp-specify-floating-point-behavior.md) (또는에, 및를 포함 하는 모든 옵션)를 **`/Oi`** [`/Ox`](../build/reference/ox-full-optimization.md) [`/O1`](../build/reference/o1-o2-minimize-size-maximize-speed.md) 지정할 때 진정한 내장 형식이 있습니다 [`/O2`](../build/reference/o1-o2-minimize-size-maximize-speed.md) .

|  |  |  |  |
|--|--|--|--|
| [`atan`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`exp`](../c-runtime-library/reference/exp-expf.md) | [`log10`](../c-runtime-library/reference/log-logf-log10-log10f.md) | [`sqrt`](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md) |
| [`atan2`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [`log`](../c-runtime-library/reference/log-logf-log10-log10f.md) | [`sin`](../c-runtime-library/reference/sin-sinf-sinl.md) | [`tan`](../c-runtime-library/reference/tan-tanf-tanl.md) |
| [`cos`](../c-runtime-library/reference/cos-cosf-cosl.md) |  |  |  |

[`/fp:strict`](../build/reference/fp-specify-floating-point-behavior.md)또는 [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 를 사용 하 여 실제 내장 부동 소수점 옵션의 생성을 재정의할 수 있습니다. 이 경우에는 함수가 인수를 프로그램 스택으로 푸시하는 대신 부동 소수점 칩으로 직접 전달하는 라이브러리 루틴으로 생성됩니다.

[`#pragma function`](../preprocessor/function-c-cpp.md)소스 텍스트 블록에 대해 내장 함수를 사용 하거나 사용 하지 않도록 설정 하는 방법에 대 한 자세한 내용은을 참조 하세요.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
