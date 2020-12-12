---
description: 자세한 정보:/arch (x64)
title: /arch(x64)
ms.date: 10/01/2019
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: 1e9670cdea49c06eda6575fe2cea872072a4e332
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183076"
---
# <a name="arch-x64"></a>/arch(x64)

x64에서 코드 생성 아키텍처를 지정합니다. [(x86) /arch](arch-x86.md)과 [/arch (ARM)](arch-arm.md)도 참조합니다.

## <a name="syntax"></a>구문

```
/arch:[AVX|AVX2|AVX512]
```

## <a name="arguments"></a>인수

**/arch:AVX**<br/>
Intel Advanced Vector Extensions 명령을 사용하도록 설정합니다.

**/arch:AVX2**<br/>
Intel 고급 벡터 확장명 2 명령을 사용하도록 설정합니다.

**/arch: AVX512**<br/>
Intel Advanced Vector Extensions 512 지침을 사용할 수 있습니다.

## <a name="remarks"></a>설명

**/Arch** 옵션을 사용 하면 INTEL 및 AMD의 프로세서에서 사용할 수 있는 특정 명령 집합 확장 (특히 벡터 계산의 경우)을 사용할 수 있습니다. 일반적으로 가장 최근에 도입된 프로세서는 이전 프로세서에서 지원하는 것 보다 더 많은 확장을 지원할 수 있습니다. 그러나 특정 프로세서에 대한 설명서를 참조하거나 [__cpuid](../../intrinsics/cpuid-cpuidex.md)을 사용하여 명령 집합 확장을 지원하는지 테스트해야 합니다.

**/arch** 는 네이티브 함수의 코드 생성에만 영향을 줍니다. [/Clr](clr-common-language-runtime-compilation.md) 을 사용 하 여 컴파일하는 경우 **/arch** 는 관리 되는 함수의 코드 생성에 영향을 주지 않습니다.

프로세서 확장에는 다음과 같은 특징이 있습니다.

- 기본 모드에서는 스칼라 부동 소수점 및 벡터 계산에 대 한 SSE2 명령을 사용 합니다. 이러한 지침을 통해 단일 전체 자릿수, 배정밀도 및 1, 2, 4 또는 8 바이트 정수 값의 128 비트 벡터로 단일 전체 자릿수 및 배정밀도 스칼라 부동 소수점 값을 계산할 수 있습니다.

- **AVX** 에는 128 비트 또는 256 비트의 벡터를 허용 하는 벡터 및 부동 소수점 스칼라 명령에 대 한 대체 명령 인코딩이 도입 되었으며 모든 벡터 결과가 전체 벡터 크기로 0으로 확장 됩니다. 레거시 호환성을 위해 SSE 스타일 벡터 지침은 비트 127 이외의 모든 비트를 유지 합니다. 대부분의 부동 소수점 연산은 256 비트로 확장 됩니다.

- **AVX2** 는 대부분의 정수 작업을 256 비트 벡터로 확장 하 고 Fma (퓨즈 Multiply-Add) 명령을 사용할 수 있도록 합니다.

- **AVX-512** 에는 512 비트 벡터와 기타 선택적 기능을 허용 하는 또 다른 명령 인코딩 형식이 도입 되었습니다. 추가 작업에 대 한 지침도 추가 되었습니다.

각 **/arch** 옵션은 해당 옵션과 관련 된 다른 벡터가 아닌 명령을 사용 하도록 설정할 수도 있습니다. 예를 들어 **/arch: AVX2** 가 지정 된 경우 특정 BMI 명령을 사용 하는 경우를 들 수 있습니다.

`__AVX__`전처리기 기호는 **/ARCH: AVX**, **/arch: AVX2** 또는 **/arch: AVX512** 컴파일러 옵션이 지정 된 경우에 정의 됩니다. `__AVX2__`전처리기 기호는 **/ARCH: AVX2** 또는 **/arch: AVX512** 컴파일러 옵션이 지정 된 경우에 정의 됩니다. `__AVX512F__`,, `__AVX512CD__` `__AVX512BW__` `__AVX512DQ__` 및 `__AVX512VL__` 전처리기 기호는 **/arch: AVX512** 컴파일러 옵션이 지정 된 경우에 정의 됩니다. 자세한 내용은 [Predefined Macros](../../preprocessor/predefined-macros.md)을 참조하세요. **/Arch: AVX2** 옵션은 업데이트 2, 버전 12.0.34567.1 Visual Studio 2013에서 도입 되었습니다. **/Arch: AVX512** 에 대 한 제한 된 지원은 visual studio 2017에 추가 되었으며 visual studio 2019에서 확장 되었습니다.

### <a name="to-set-the-archavx-archavx2-or-archavx512-compiler-option-in-visual-studio"></a>Visual Studio에서/arch: AVX,/arch: AVX2 또는/arch: AVX512 컴파일러 옵션을 설정 하려면

1. 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**, **C/C++** 폴더를 선택합니다.

1. **코드 생성** 속성 페이지를 선택합니다.

1. 향상 된 **명령 집합 사용** 드롭다운 상자에서 **고급 벡터 확장 (/arch: AVX)**, **고급 벡터 확장 2 (/Arch: AVX2)** 또는 **고급 벡터 확장 512 (/arch: AVX512)** 을 선택 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/arch (최소 CPU 아키텍처)](arch-minimum-cpu-architecture.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
