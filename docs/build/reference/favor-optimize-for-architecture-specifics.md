---
description: 자세히 알아보기:/favor (아키텍처에 맞게 최적화)
title: /favor(아키텍처에 맞게 최적화)
ms.date: 11/04/2016
f1_keywords:
- /favor
helpviewer_keywords:
- -favor compiler option [C++]
- /favor compiler option [C++]
ms.assetid: ad264df2-e30f-4d68-8bd0-10d6bee71a2a
ms.openlocfilehash: 184e81e1007214a09088601b6c579692a0dd20a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192306"
---
# <a name="favor-optimize-for-architecture-specifics"></a>/favor(아키텍처에 맞게 최적화)

**/favor:** `option` 는 특정 아키텍처에 맞게 최적화 된 코드를 생성 하거나 AMD 및 Intel 아키텍처에서 마이크로 아키텍처의 특성을 지정 합니다.

## <a name="syntax"></a>Syntax

> **/favor:**{**blend**  |  **ATOM**  |  **AMD64**  |  **INTEL64**}

## <a name="remarks"></a>설명

**/favor: blend**<br/>
(x86 및 x64)는 AMD 및 Intel 아키텍처에서 마이크로 아키텍처 사양에 맞게 최적화된 코드를 생성합니다. **/Favor: blend** 는 특정 프로세서에서 최고의 성능을 제공 하지 않을 수 있지만 광범위 한 x86 및 x64 프로세서에서 최상의 성능을 제공 하도록 설계 되었습니다. 기본적으로 **/favor: blend** 가 적용 됩니다.

**/favor: ATOM**<br/>
(x86 및 x64)은 Intel Atom 프로세서 및 Intel Centrino Atom 프로세서 기술 사양에 맞게 최적화된 코드를 생성합니다. **/Favor: ATOM** 을 사용 하 여 생성 된 코드는 intel 프로세서에 대 한 intel SSSE3, SSE3, SSE2 및 SSE 명령도 생성할 수 있습니다.

**/favor: AMD64**<br/>
(x64만 해당)는 AMD Opteron 및 64비트 확장을 지원하는 Athlon 프로세서에 대해 생성된 코드를 최적화합니다. 최적화된 코드는 모든 x64 호환 플랫폼에서 실행할 수 있습니다. **/Favor: AMD64** 를 사용 하 여 생성 된 코드는 Intel64를 지 원하는 Intel 프로세서에서 성능이 저하 될 수 있습니다.

**/favor: INTEL64**<br/>
(x64만 해당)는 Intel64를 지원하는 Intel 프로세서에 대해 생성된 코드를 최적화하며 일반적으로 해당 플랫폼에서 더 나은 성능을 제공합니다. 결과 코드는 모든 x64 플랫폼에서 실행할 수 있습니다. **/Favor: INTEL64** 를 사용 하 여 생성 된 코드는 AMD Opteron의 성능이 저하 될 수 있으며 64 비트 확장을 지 원하는 프로세서를 Athlon 수 있습니다.

> [!NOTE]
> Intel64 아키텍처는 이전에 확장 된 메모리 64 기술로 알려져 있고 해당 컴파일러 옵션은 **/favor: EM64T** 였습니다.

X64 아키텍처를 프로그래밍 하는 방법에 대 한 자세한 내용은 [X64 소프트웨어 규칙](../x64-software-conventions.md)을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/c + +** 폴더를 선택 합니다.

1. **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
