---
description: 자세히 알아보기:/Ob (인라인 함수 확장)
title: /Ob(인라인 함수 확장)
ms.date: 08/08/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
helpviewer_keywords:
- inline functions, function expansion compiler option [C++]
- -Ob1 compiler option [C++]
- -Ob0 compiler option [C++]
- /Ob0 compiler option [C++]
- /Ob1 compiler option [C++]
- any suitable compiler option [C++]
- Ob2 compiler option [C++]
- Ob1 compiler option [C++]
- /Ob2 compiler option [C++]
- Ob compiler option [C++]
- -Ob2 compiler option [C++]
- disable compiler option [C++]
- -Ob compiler option [C++]
- /Ob compiler option [C++]
- only __inline compiler option [C++]
- Ob0 compiler option [C++]
- inline expansion, compiler option
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
ms.openlocfilehash: 9a003f83d27ca0517b427bab6f7ffda75ff51557
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214343"
---
# <a name="ob-inline-function-expansion"></a>/Ob(인라인 함수 확장)

함수의 인라인 확장을 제어합니다. 기본적으로 최적화할 때 확장은 컴파일러의 판단에 따라 *자동 인라이닝* 이라고 하는 모든 함수에서 발생 합니다.

## <a name="syntax"></a>Syntax

::: moniker range=">=msvc-160"

> **/Ob**{**0** | **1** | **2** | **3**}

::: moniker-end

::: moniker range="<=msvc-150"

> **/Ob**{**0** | **1** | **2**}

::: moniker-end

## <a name="arguments"></a>인수

**0**\
[/Od](od-disable-debug.md)의 기본값입니다. 인라인 확장을 사용하지 않도록 설정합니다.

**1**\
[인라인](../../cpp/inline-functions-cpp.md), [__inline](../../cpp/inline-functions-cpp.md)또는 [__forceinline](../../cpp/inline-functions-cpp.md)표시 된 함수만 확장 하거나 클래스 선언에 정의 된 c + + 멤버 함수를 확장할 수 있습니다.

**2**\
[/O1](o1-o2-minimize-size-maximize-speed.md) 과 [/o1](o1-o2-minimize-size-maximize-speed.md)의 기본값입니다. 컴파일러가 인라이닝 되지 않도록 명시적으로 표시 되지 않은 모든 함수를 확장할 수 있습니다.

::: moniker range=">=msvc-160"

**3**\
이 옵션은 **/Ob2** 보다 더 적극적인 인라인 인라인을 지정 하지만 동일한 제한 사항이 있습니다. **/Ob3** 옵션은 Visual Studio 2019부터 사용할 수 있습니다.

::: moniker-end

## <a name="remarks"></a>설명

컴파일러는 인라인 확장 옵션과 키워드를 제안으로 처리합니다. 모든 함수가 인라인으로 확장 되는 것은 아닙니다. 인라인 확장을 사용 하지 않도록 설정할 수 있지만 키워드를 사용 하는 경우에도 컴파일러가 특정 함수를 인라인 할 수 없습니다 **`__forceinline`** .

인라인 확장의 후보로 고려 하지 않도록 함수를 제외 하려면 [__declspec (noinline)](../../cpp/noinline.md)를 사용 하거나 [#pragma auto_inline (off)](../../preprocessor/auto-inline.md) 지시문으로 표시 된 영역을 사용 하거나 [auto_inline (on)](../../preprocessor/auto-inline.md) 지시문을 #pragma 수 있습니다. 컴파일러에 인라인 힌트를 제공 하는 다른 방법에 대 한 자세한 내용은 [#pragma 내장](../../preprocessor/intrinsic.md) 지시문을 참조 하십시오.

> [!NOTE]
> 프로 파일링 테스트 실행에서 수집 되는 정보는 **/Ob**, **/os** 또는 **/ot** 를 지정 했기 때문에 다르게 적용 되는 최적화를 재정의 합니다. 자세한 내용은 [프로필 기반 최적화](../profile-guided-optimizations.md)를 참조하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **최적화** 속성 페이지를 선택 합니다.

1. **인라인 함수 확장** 속성을 수정 합니다.

::: moniker range=">=msvc-160"

**/Ob3** 옵션은 **인라인 함수 확장** 속성에서 사용할 수 없습니다. **/Sv3** 을 설정 하려면:

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** > **C/C++** > **명령줄** 속성 페이지를 선택합니다.

1. **추가 옵션** 에서 **/ob3** 을 입력 합니다.

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/O 옵션 (코드 최적화)](o-options-optimize-code.md)\
[MSVC 컴파일러 옵션](compiler-options.md)\
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
