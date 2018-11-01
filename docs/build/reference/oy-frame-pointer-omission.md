---
title: /Oy(프레임 포인터 생략)
ms.date: 09/22/2017
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
ms.openlocfilehash: d6d896079c08ed2cf595b95ed41045885c83b5bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431735"
---
# <a name="oy-frame-pointer-omission"></a>/Oy(프레임 포인터 생략)

호출 스택에서 프레임 포인터를 생성하지 않습니다.

## <a name="syntax"></a>구문

> /Oy [-]

## <a name="remarks"></a>설명

프레임 포인터를 설정하고 제거할 필요가 없기 때문에 이 옵션을 사용하면 함수 호출 속도가 빨라집니다. 또한 일반 용도 레지스터 하나를 해제합니다.

**/Oy** 프레임 포인터 생략을 사용 하도록 설정 하 고 **/Oy-** 생략을 사용 하지 않도록 설정 합니다. **/Oy** x86 에서만 사용할 수 있습니다 컴파일러.

경우 코드에 EBP 기반 주소 지정 요구를 지정할 수 있습니다 합니다 **/Oy-** 후 옵션을 **/Ox** 옵션 또는 사용 하 여 [최적화](../../preprocessor/optimize.md) 사용 하 여는 "**y**" 및 **해제** EBP 기반 주소 지정을 최대로 최적화할에 대 한 인수입니다. 컴파일러가 EBP 기반 주소 지정이 필요한 상황을 대부분 인식합니다. 예를 들어, `_alloca` 및 `setjmp` 함수와 구조적 예외 처리가 있는 경우에 EBP 기반 주소 지정이 필요합니다.

합니다 [/Ox (사용 가장 속도 최적화)](../../build/reference/ox-full-optimization.md) 하 고 [/o1, / o2 (크기 최소화, 속도 최대화)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 옵션 의미 **/Oy**합니다. 지정 **/Oy-** 후 합니다 **/Ox**를 **/o1**, 또는 **/o2** 옵션이 비활성화 **/Oy**인지, 명시적 또는 암시적입니다.

합니다 **/Oy** 컴파일러 옵션을 사용 하면 컴파일러 프레임 포인터 정보가 제한 되므로 더 어렵게 디버거를 사용 합니다. 디버그 컴파일러 옵션을 지정 하면 ([/z7, /Zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md))를 지정 하는 것이 좋습니다는 **/Oy-** 다른 최적화 컴파일러 옵션 뒤 옵션입니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. **C/C++** 폴더를 클릭합니다.

1. 클릭 합니다 **최적화** 속성 페이지.

1. 수정 된 **프레임 포인터 생략** 속성입니다. 이 속성을 추가 또는 제거 합니다 **/Oy** 옵션입니다. 추가 하려는 경우는 **/Oy-** 옵션을 클릭 **명령줄** 수정 **추가 옵션**합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/O 옵션(코드 최적화)](../../build/reference/o-options-optimize-code.md)

[컴파일러 옵션](../../build/reference/compiler-options.md)

[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)
