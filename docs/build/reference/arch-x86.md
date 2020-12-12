---
description: 자세히 알아보기:/arch (x86)
title: /arch(x86)
ms.date: 10/01/2019
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
ms.openlocfilehash: a37f0b5cfe1907108bdd5fb71de774a84f585676
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183063"
---
# <a name="arch-x86"></a>/arch(x86)

x86에서 코드 생성 아키텍처를 지정합니다. [(x64) /arch](arch-x64.md)과 [/arch (ARM)](arch-arm.md)도 참조합니다.

## <a name="syntax"></a>구문

```
/arch:[IA32|SSE|SSE2|AVX|AVX2|AVX512]
```

## <a name="arguments"></a>인수

**/arch:IA32**<br/>
고급 명령을 지정하지 않는 반면 부동 소수점 계산을 위해 x87도 지정합니다.

**/arch:SSE**<br/>
SSE 명령을 사용하도록 설정합니다.

**/arch:SSE2**<br/>
SSE2 명령을 사용하도록 설정합니다. 이는 **/arch** 옵션이 지정 되지 않은 경우 x86 플랫폼의 기본 명령입니다.

**/arch:AVX**<br/>
Intel Advanced Vector Extensions 명령을 사용하도록 설정합니다.

**/arch:AVX2**<br/>
Intel 고급 벡터 확장명 2 명령을 사용하도록 설정합니다.

**/arch: AVX512**<br/>
Intel Advanced Vector Extensions 512 지침을 사용할 수 있습니다.

## <a name="remarks"></a>설명

**/Arch** 옵션을 사용 하거나 사용 하지 않도록 설정 합니다. 특히 벡터 계산의 경우 INTEL 및 AMD의 프로세서에서 사용할 수 있습니다. 일반적으로 가장 최근에 도입된 프로세서는 이전 프로세서에서 지원하는 것 보다 더 많은 확장을 지원할 수 있습니다. 그러나 특정 프로세서에 대한 설명서를 참조하거나 [__cpuid](../../intrinsics/cpuid-cpuidex.md)을 사용하여 명령 집합 확장을 지원하는지 테스트해야 합니다.

**/arch** 는 네이티브 함수의 코드 생성에만 영향을 줍니다. [/Clr](clr-common-language-runtime-compilation.md) 을 사용 하 여 컴파일하는 경우 **/arch** 는 관리 되는 함수의 코드 생성에 영향을 주지 않습니다.

**/Arch** options는 다음과 같은 특징을 가진 명령 집합 확장을 참조 합니다.

- **IA32** 는 벡터 작업 없이는 레거시 32 비트 x86 명령 집합으로 부동 소수점 계산에는 x87을 사용 합니다.

- **SSE** 를 사용 하면 최대 4 개의 단 정밀도 부동 소수점 값의 벡터로 계산을 수행할 수 있습니다. 해당 스칼라 부동 소수점 명령도 추가 되었습니다.

- **SSE2** 는 단일 전체 자릿수, 배정밀도 및 1, 2, 4 또는 8 바이트 정수 값의 128 비트 벡터를 사용 하 여 계산을 수행할 수 있습니다. 배정밀도 스칼라 명령도 추가 되었습니다.

- **AVX** 에는 128 비트 또는 256 비트의 벡터를 허용 하는 벡터 및 부동 소수점 스칼라 명령에 대 한 대체 명령 인코딩이 도입 되었으며 모든 벡터 결과가 전체 벡터 크기로 0으로 확장 됩니다. 레거시 호환성을 위해 SSE 스타일 벡터 지침은 비트 127 이외의 모든 비트를 유지 합니다. 대부분의 부동 소수점 연산은 256 비트로 확장 됩니다.

- **AVX2** 는 대부분의 정수 작업을 256 비트 벡터로 확장 하 고 Fma (퓨즈 Multiply-Add) 명령을 사용할 수 있도록 합니다.

- **AVX512** 에는 512 비트 벡터와 기타 선택적 기능을 허용 하는 또 다른 명령 인코딩 형식이 도입 되었습니다. 추가 작업에 대 한 지침도 추가 되었습니다.

최적화 프로그램은 지정 된 **/arch** 에 따라 벡터 지침을 사용 하는 시기 및 방법을 선택 합니다. 사용 가능한 경우 SSE 또는 AVX 명령을 사용 하 여 스칼라 부동 소수점 계산을 수행 합니다. 일부 호출 규칙은 x87 스택에 부동 소수점 인수를 전달 하도록 지정 합니다. 따라서 코드에서 부동 소수점 계산에는 x87 및 SSE/AVX 명령을 함께 사용할 수 있습니다. 정수 벡터 지침은 사용 가능한 경우 일부 64 비트 정수 연산에도 사용할 수 있습니다.

벡터 및 부동 소수점 스칼라 명령 외에도 각 **/arch** 옵션은 해당 옵션과 관련 된 다른 벡터가 아닌 명령을 사용 하도록 설정할 수 있습니다. 예를 들어 Intel Pentium Pro 프로세서에 처음 표시 된 CMOVcc 명령 패밀리가 있습니다. SSE 명령은 후속 Intel Pentium III 프로세서에서 도입 되었기 때문에 **/arch: IA32** 가 지정 된 경우를 제외 하 고 cmovcc 명령이 생성 될 수 있습니다.

부동 소수점 연산은 일반적으로 x87 코드에서 배정밀도 (64 비트)로 반올림 되지만를 사용 `_controlfp` 하 여 전체 자릿수 (80 비트) 또는 단 정밀도 (32 비트)로 전체 자릿수 제어를 설정 하는 것을 포함 하 여 FP 제어 단어를 수정할 수 있습니다. 자세한 내용은 [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)를 참조하세요. SSE 및 AVX에는 각 작업에 대 한 단 정밀도 및 배정밀도 명령이 별도로 포함 되어 있으므로 SSE/AVX 코드에 해당 하는 것은 없습니다. 부동 소수점 연산의 결과가 사용자 변수에 할당 되는 대신 추가 계산에서 직접 사용 되는 경우 결과가 반올림 되는 방식을 변경할 수 있습니다. 다음을 살펴보세요.

```cpp
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.
```

명시적 할당을 사용 하는 경우:

```cpp
t = f1 * f2;   // Do f1 * f2, round to the type of t.
r = t + d;     // This should produce the same overall result
               // whether x87 stack is used or SSE/SSE2 is used.
```

**/arch** 및 [/qifist](qifist-suppress-ftol.md) 는 동일한 compiland에서 사용할 수 없습니다. **/Qifist** 옵션은 부동 소수점의 반올림 동작을 정수 변환으로 변경 합니다. 기본 동작은 truncate (0으로 반올림) 하는 반면 **/qifist** 옵션은 부동 소수점 환경 반올림 모드의 사용을 지정 합니다. 이는 모든 부동 소수점의 동작을 정수 변환으로 변경 하기 때문에이 플래그는 더 이상 사용 되지 않습니다. SSE 또는 AVX를 컴파일하는 경우에는 내장 함수 시퀀스를 사용 하 여 부동 소수점 환경 반올림 모드를 사용 하 여 부동 소수점 값을 정수로 반올림할 수 있습니다.

```cpp
int convert_float_to_int(float x) {
    return _mm_cvtss_si32(_mm_set_ss(x));
}

int convert_double_to_int(double x) {
    return _mm_cvtsd_si32(_mm_set_sd(x));
}
```

,,,,, `_M_IX86_FP` `__AVX__` `__AVX2__` 및 매크로는 ( `__AVX512F__` `__AVX512CD__` `__AVX512BW__` `__AVX512DQ__` `__AVX512VL__` 있는 경우) 및 사용 된 **/arch** 컴파일러 옵션을 표시 합니다. 자세한 내용은 [Predefined Macros](../../preprocessor/predefined-macros.md)을 참조하세요. **/Arch: AVX2** 옵션과 매크로는 `__AVX2__` Visual Studio 2013 업데이트 2, 버전 12.0.34567.1에서 도입 되었습니다. **/Arch: AVX512** 에 대 한 제한 된 지원은 visual studio 2017에 추가 되었으며 visual studio 2019에서 확장 되었습니다.

### <a name="to-set-this-compiler-option-for-avx-avx2-avx512-ia32-sse-or-sse2-in-visual-studio"></a>Visual Studio에서 AVX, AVX2, AVX512, IA32, SSE 또는 SSE2에 대해이 컴파일러 옵션을 설정 하려면

1. 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**, **C/C++** 폴더를 선택합니다.

1. **코드 생성** 속성 페이지를 선택합니다.

1. **고급 명령 집합 사용** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/arch (최소 CPU 아키텍처)](arch-minimum-cpu-architecture.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
