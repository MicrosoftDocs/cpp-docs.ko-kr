---
description: 자세히 알아보기:/Za,/Ze (언어 확장 사용 안 함)
title: /Za, /Ze(언어 확장명 사용 안 함)
ms.date: 02/19/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
ms.openlocfilehash: 98b3d3a36a0aaf0731e6fe6ded06844f7f1e4213
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263181"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze(언어 확장명 사용 안 함)

**/Za** 컴파일러 옵션은 ANSI C89/ISO C90와 호환 되지 않는 C에 대 한 Microsoft 확장 오류를 비활성화 하 고 내보냅니다. 사용 되지 않는 **/ze** 컴파일러 옵션은 Microsoft 확장을 사용 하도록 설정 합니다. Microsoft 확장은 기본적으로 사용하도록 설정됩니다.

## <a name="syntax"></a>Syntax

> **/Za**\
> **/Ze**

## <a name="remarks"></a>설명

> [!NOTE]
> 코드를 c + +로 컴파일할 때 **/za** 를 사용 하지 않는 것이 좋습니다. **/Ze** 옵션은 동작이 기본적으로 설정 되어 있기 때문에 사용 되지 않습니다. 사용 되지 않는 컴파일러 옵션의 목록은 [사용 되지 않음 및 제거 된 컴파일러 옵션](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options)을 참조 하세요.

Microsoft C/c + + 컴파일러는 C 코드의 컴파일을 다음과 같은 두 가지 방법으로 지원 합니다.

- 컴파일러는 소스 파일의 확장명이 *.c* 이거나 [/tc](tc-tp-tc-tp-specify-source-file-type.md) 또는 [/tc](tc-tp-tc-tp-specify-source-file-type.md) 옵션이 지정 된 경우 기본적으로 c 컴파일 모드를 사용 합니다. C 컴파일러는 기본적으로 C 언어에 대 한 Microsoft 확장을 사용 하도록 설정 하는 C89/C90 컴파일러입니다. 특정 확장에 대 한 자세한 내용은 [c 및 c + +에 대 한 Microsoft 확장](microsoft-extensions-to-c-and-cpp.md)을 참조 하세요. C 컴파일과 **/za** 옵션이 모두 지정 된 경우 c 컴파일러는 C89/C90 표준을 엄격 하 게 준수 합니다. 컴파일러는 microsoft 확장 키워드를 단순 식별자로 처리 하 고, 다른 microsoft 확장을 사용 하지 않도록 설정 하 고, C 프로그램에 대해 미리 정의 된 [ \_ \_ STDC \_ \_ ](../../preprocessor/predefined-macros.md) 매크로를 자동으로 정의 합니다.

- 컴파일러는 c + + 컴파일 모드에서 C 코드를 컴파일할 수 있습니다. 이 동작은 *.c* 확장명이 없는 소스 파일에 대 한 기본값이 며 [/tp](tc-tp-tc-tp-specify-source-file-type.md) 또는 [/tp](tc-tp-tc-tp-specify-source-file-type.md) 옵션이 지정 된 경우에 해당 합니다. C + + 컴파일 모드에서는 컴파일러가 c + + 표준에 통합 된 ISO C99 및 C11 표준의 해당 부분을 지원 합니다. 거의 모든 C 코드는 유효한 c + + 코드 이기도 합니다. 적은 수의 C 키워드 및 코드 구문은 유효한 c + + 코드가 아니거나 c + +에서 다르게 해석 됩니다. 이 경우 컴파일러는 c + + 표준에 따라 동작 합니다. C + + 컴파일 모드에서는 **/za** 옵션으로 인해 예기치 않은 동작이 발생할 수 있으므로 권장 하지 않습니다.

다른 컴파일러 옵션은 컴파일러가 표준 준수를 보장 하는 방법에 영향을 줄 수 있습니다. 특정 표준 C 및 c + + 동작 설정을 지정 하는 방법은 [/zc](zc-conformance.md) 컴파일러 옵션을 참조 하세요. 추가 c + + 표준 규칙 설정에 대 한 자세한 내용은 [/permissive-](permissive-standards-conformance.md) 및 [/sts](std-specify-language-standard-version.md) 컴파일러 옵션을 참조 하세요.

Visual C++의 규칙 문제에 대 한 자세한 내용은 [비표준 동작](../../cpp/nonstandard-behavior.md)을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. 탐색 창에서 **구성 속성**  >  **C/c + +**  >  **언어** 를 선택 합니다.

1. **언어 확장 사용 안 함** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[컴파일러 옵션](compiler-options.md)<br/>
[/Zc(규칙)](zc-conformance.md)<br/>
[/permissive-(표준 준수)](permissive-standards-conformance.md)<br/>
[/std (언어 표준 버전 지정)](std-specify-language-standard-version.md)<br/>
