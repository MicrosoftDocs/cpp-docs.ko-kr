---
title: '/Zc: forscope (for 강제 규칙 루프 범위) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope
- VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope
- /zc:forScope
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bef68f47fe8fdc430138a6961078139b48030b3d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723595"
---
# <a name="zcforscope-force-conformance-in-for-loop-scope"></a>/Zc:forScope(for 루프 범위의 강제 규칙)

Microsoft 확장( [/Ze](../../cpp/for-statement-cpp.md) )과 함께[for](../../build/reference/za-ze-disable-language-extensions.md)루프의 표준 C++ 동작을 구현하는 데 사용됩니다.

## <a name="syntax"></a>구문

> **/Zc:forScope**[**-**]

## <a name="remarks"></a>설명

표준 동작은 **for** 루프의 이니셜라이저가 **for** 루프 후 범위를 벗어나는 것입니다. **/Zc:forScope-** 및 [/Ze](../../build/reference/za-ze-disable-language-extensions.md)에서 **for** 루프의 이니셜라이저는 로컬 범위가 종료될 때까지 범위 내에 남아 있습니다.

합니다 **/zc: forscope** 옵션이 기본적으로 켜져 있습니다. **/Zc: forscope** 시기에 영향을 받지 않습니다 합니다 [관대 한 /-](permissive-standards-conformance.md) 옵션을 지정 합니다.

**/Zc:forScope-** 옵션은 더 이상 사용되지 않으므로 이후 릴리스에서 제거될 예정입니다. **/Zc:forScope-** 를 사용하면 사용 중단 경고 D9035가 발생합니다.

다음 코드는 **/Za** 가 아니라 **/Ze**에서 컴파일됩니다.

```cpp
// zc_forScope.cpp
// compile by using: cl /Zc:forScope- /Za zc_forScope.cpp
// C2065, D9035 expected
int main() {
    // Compile by using cl /Zc:forScope- zc_forScope.cpp
    // to compile this non-standard code as-is.
    // Uncomment the following line to resolve C2065 for /Za.
    // int i;
    for (int i = 0; i < 1; i++)
        ;
    i = 20;   // i has already gone out of scope under /Za
}
```

**/Zc:forScope-** 를 사용하는 경우 이전 범위에서 만든 선언으로 인해 변수가 범위 내에 있으면 경고 C4288이 발생합니다(기본적으로 설정되어 있지 않음). 이를 증명하려면 예제 코드에서 `//` 문자를 제거하여 `int i`를 선언합니다.

**conform** pragma를 사용하여 [/Zc:forScope](../../preprocessor/conform.md) 의 런타임 동작을 수정할 수 있습니다.

기존 .pch 파일이 있는 프로젝트에서 **/Zc:forScope-** 를 사용하면 **/Zc:forScope-** 가 무시되고 기존 .pch 파일을 사용하여 계속 컴파일합니다. 사용 하 여 생성 된 새.pch 파일을 원하면 [/Yc (미리 컴파일된 헤더 파일 만들기)](../../build/reference/yc-create-precompiled-header-file.md)합니다.

Visual C++의 규칙과 관련된 문제에 대한 자세한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)을 참조하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. 선택 된 **구성 속성** > **C/c + +** > **언어** 속성 페이지.

1. **For 루프 범위 강제 규칙** 속성을 수정합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>을 참조하세요.

## <a name="see-also"></a>참고자료

[/Zc(규칙)](../../build/reference/zc-conformance.md)<br/>
[/Za, /Ze(언어 확장 사용 안 함)](../../build/reference/za-ze-disable-language-extensions.md)<br/>
