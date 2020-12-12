---
description: 자세히 알아보기:/Oi (내장 함수 생성)
title: /Oi(내장 함수 만들기)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
ms.openlocfilehash: fc08ff495391092115197fe70e8c3673b77f32e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214281"
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi(내장 함수 만들기)

일부 함수 호출을 내장 함수 호출로 바꾸거나 응용 프로그램이 더 빠르게 실행 하는 데 도움이 되는 특수 한 형태의 함수를 대체 합니다.

## <a name="syntax"></a>구문

```
/Oi[-]
```

## <a name="remarks"></a>설명

내장 함수를 사용 하는 프로그램은 함수 호출의 오버 헤드를 갖지 않지만 추가 코드로 인해 더 커질 수 있기 때문에 속도가 더 빠릅니다.

내장 폼이 있는 함수에 대 한 자세한 내용은 [내장](../../preprocessor/intrinsic.md) 함수를 참조 하세요.

**/Oi** 는 일부 함수 호출을 내장 함수로 바꾸기 위해 컴파일러에 대 한 요청입니다. 컴파일러가 성능을 향상 시키는 경우 함수를 호출 하 고 함수 호출을 내장 함수로 바꾸지 않을 수 있습니다.

**x86 전용**

내장 부동 소수점 함수는 입력 값에 대 한 특별 한 검사를 수행 하지 않으므로 제한 된 입력 범위에서 작동 하며 동일한 이름의 라이브러리 루틴에 대 한 예외 처리 및 경계 조건이 서로 다릅니다. 진정한 내장 폼을 사용 하면 IEEE 예외 처리의 손실과 및 기능이 손실 됩니다 `_matherr` . `errno` 후자는 ANSI 규칙의 손실을 의미 합니다. 그러나 내장 폼을 사용 하면 부동 소수점 집약적 프로그램의 속도를 크게 높일 수 있으며, 많은 프로그램에서 규칙 문제는 실질적으로 가치가 낮습니다.

[Za](za-ze-disable-language-extensions.md) 컴파일러 옵션을 사용 하 여 실제 내장 부동 소수점 옵션의 생성을 재정의할 수 있습니다. 이 경우에는 함수가 인수를 프로그램 스택으로 푸시하는 대신 부동 소수점 칩으로 직접 전달하는 라이브러리 루틴으로 생성됩니다.

**X86 특정 종료**

내장 함수를 만들거나 함수 [(c/c + +)](../../preprocessor/function-c-cpp.md) 를 사용 하 여 함수 호출을 명시적으로 강제 적용 하는 데도 [내장](../../preprocessor/intrinsic.md) 함수를 사용 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **최적화** 속성 페이지를 클릭 합니다.

1. **내장 함수 사용** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/O 옵션 (코드 최적화)](o-options-optimize-code.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[컴파일러 내장 함수](../../intrinsics/compiler-intrinsics.md)
