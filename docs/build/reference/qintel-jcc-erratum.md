---
title: /QIntel-jcc-erratum
description: Microsoft C/c + + 컴파일러 (MSVC)/QIntel-jcc-erratum 옵션에 대해 설명 합니다.
ms.date: 01/07/2020
f1_keywords:
- QIntel-jcc-erratum
helpviewer_keywords:
- /QIntel-jcc-erratum
- -QIntel-jcc-erratum
ms.openlocfilehash: c66dd4bb25647ce193bce4db5dc4ebb1268277c0
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921375"
---
# <a name="qintel-jcc-erratum"></a>/QIntel-jcc-erratum

::: moniker range="<=msvc-150"

**/QIntel-jcc-erratum** 옵션은 Visual Studio 2019 버전 16.5 이상에서 사용할 수 있습니다.

::: moniker-end

::: moniker range=">=msvc-160"

특정 Intel 프로세서에서 Intel JCC (점프 조건부 코드) erratum 마이크로코드 업데이트로 인 한 성능 영향을 완화 하기 위해 컴파일러에서 명령을 생성 하도록 지정 합니다.

## <a name="syntax"></a>구문

> **/QIntel-jcc-erratum**

## <a name="remarks"></a>설명

**/QIntel-jcc-erratum** 에서는 컴파일러가 32 바이트 경계에서 교차 하거나 종료 하는 점프 및 매크로-퓨즈 점프 명령을 검색 합니다. 경계에 이러한 지침을 맞춥니다. 이러한 변경으로 특정 Intel 프로세서에서 JCC erratum을 방지 하는 마이크로코드 업데이트의 성능 영향을 완화할 수 있습니다. Erratum에 대 한 자세한 내용은 Intel 웹 사이트의 [점프 조건부 코드 Erratum 완화](https://www.intel.com/content/dam/support/us/en/documents/processors/mitigations-jump-conditional-code-erratum.pdf) 를 참조 하세요.

**/QIntel-jcc-erratum** 옵션은 Visual Studio 2019 버전 16.5 이상에서 사용할 수 있습니다. 이 옵션은 x86 및 x 64를 대상으로 하는 컴파일러 에서만 사용할 수 있습니다. ARM 프로세서를 대상으로 하는 컴파일러에서는이 옵션을 사용할 수 없습니다.

**/QIntel-jcc-erratum** 옵션은 기본적으로 해제 되어 있으며 최적화 된 빌드에서만 작동 합니다. 이 옵션은 코드 크기를 늘릴 수 있습니다.

**/QIntel-jcc-erratum** 는 [/clr](clr-common-language-runtime-compilation.md)과 호환 되지 않습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** > **C/c + +** > **코드 생성** 속성 페이지를 선택 합니다.

1. **Intel JCC Erratum 완화 속성 사용** 에 대 한 값을 선택 합니다. **확인** 을 선택하여 변경 내용을 적용합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/Q 옵션 (하위 수준 작업)](q-options-low-level-operations.md)\
[MSVC 컴파일러 옵션](compiler-options.md)\
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)

::: moniker-end
