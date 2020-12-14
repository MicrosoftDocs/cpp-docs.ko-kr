---
description: 자세히 알아보기:/Oy (프레임 포인터 생략)
title: /Oy(프레임 포인터 생략)
ms.date: 11/19/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.OmitFramePointers
- /oy
helpviewer_keywords:
- omit frame pointer
- Oy compiler option [C++]
- stack frame pointer compiler option [C++]
- -Oy compiler option [C++]
- frame pointer omission compiler option [C++]
- suppress frame pointer creation
- /Oy compiler option [C++]
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
ms.openlocfilehash: dc0f9272bce5ad36840eac9ccdfc7e2465f7e3c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226300"
---
# <a name="oy-frame-pointer-omission"></a>/Oy(프레임 포인터 생략)

호출 스택에서 프레임 포인터를 생성하지 않습니다.

## <a name="syntax"></a>Syntax

> /Oy [-]

## <a name="remarks"></a>설명

프레임 포인터를 설정하고 제거할 필요가 없기 때문에 이 옵션을 사용하면 함수 호출 속도가 빨라집니다. 또한 일반적인 사용을 위해 하나 이상의 등록을 해제 합니다.

**/Oy** 는 프레임 포인터를 생략 하 고 **/Oy-** 생략을 사용 하지 않도록 설정 합니다. X64 컴파일러에서는 **/oy** 및 **/Oy-** 를 사용할 수 없습니다.

코드에 프레임 기반 주소 지정이 필요한 경우 **/ox** 옵션 뒤에 **/Oy-** 옵션을 지정 하거나 "**y**" 및 **off** 인수를 사용 하 여 [최적화](../../preprocessor/optimize.md) 를 사용 하 여 프레임 기반 주소 지정에 대 한 최대 최적화를 얻을 수 있습니다. 컴파일러는 프레임 기반 주소 지정이 필요한 대부분의 경우 (예를 들어 `_alloca` 및 `setjmp` 함수와 구조적 예외 처리를 사용 하 여)를 검색 합니다.

[/Ox (최대 속도 최적화 사용)](ox-full-optimization.md) 및 [/O1,/O1 (크기 최소화, 속도 최대화)](o1-o2-minimize-size-maximize-speed.md) 옵션은 **/oy** 를 의미 합니다. **/Ox**, **/O1** 또는 **/O1** 옵션 다음에 **/Oy-** 를 지정 하면 명시적이 든 묵시적이 든 간에 **/oy** 사용 하지 않도록 설정 됩니다.

**/Oy** 컴파일러 옵션을 사용 하면 컴파일러에서 프레임 포인터 정보를 표시 하지 않기 때문에 디버거를 더 어렵게 만들 수 있습니다. 디버그 컴파일러 옵션 ([/Z7,/zi,/zi](z7-zi-zi-debug-information-format.md))을 지정 하는 경우 다른 최적화 컴파일러 옵션 뒤에 **/Oy-** 옵션을 지정 하는 것이 좋습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **최적화** 속성 페이지를 선택 합니다.

1. **생략 프레임 포인터** 속성을 수정 합니다. 이 속성은 **/oy** 옵션만 추가 하거나 제거 합니다. **/Oy-** 옵션을 추가 하려면 **명령줄** 속성 페이지를 선택 하 고 **추가 옵션** 을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/O 옵션 (코드 최적화)](o-options-optimize-code.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
