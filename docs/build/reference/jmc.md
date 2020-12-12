---
description: 자세히 알아보기:/JMC (내 코드만 디버깅)
title: /JMC(내 코드만 디버깅)
ms.date: 08/20/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SupportJustMyCode
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: 03a4cbc9bb9a992f2ed53e4f1239532923b32d0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199690"
---
# <a name="jmc-just-my-code-debugging"></a>/JMC(내 코드만 디버깅)

Visual Studio 디버거에서 네이티브 *내 코드만* 디버깅에 대 한 컴파일러 지원을 지정 합니다. 이 옵션은 Visual Studio에서 시스템, 프레임 워크, 라이브러리 및 기타 비 사용자 호출을 단계별로 실행 하 고 호출 스택 창에서 해당 호출을 축소 하는 데 사용할 수 있는 사용자 설정을 지원 합니다. **/JMC** 컴파일러 옵션은 Visual Studio 2017 버전 15.8부터 사용할 수 있습니다.

## <a name="syntax"></a>Syntax

> **/JMC** \[ **-** ]

## <a name="remarks"></a>설명

Visual Studio [내 코드만](/visualstudio/debugger/just-my-code) 설정은 visual studio 디버거가 시스템, 프레임 워크, 라이브러리 및 기타 비 사용자 호출을 단계별로 수행할지 여부를 지정 합니다. **/JMC** 컴파일러 옵션을 사용 하면 네이티브 c + + 코드에서 내 코드만 디버깅을 지원할 수 있습니다. **/JMC** 를 사용 하는 경우 컴파일러는 함수 프롤로그에서 도우미 함수에 대 한 호출을 삽입 합니다 `__CheckForDebuggerJustMyCode` . 도우미 함수는 Visual Studio 디버거 내 코드만 단계 작업을 지 원하는 후크를 제공 합니다. Visual Studio 디버거에서 내 코드만를 사용 하도록 설정 하려면 메뉴 모음에서 **도구**  >  **옵션** 을 선택 하 고 **디버깅**  >  **일반**  >  **사용 내 코드만** 에서 옵션을 설정 합니다.

**/JMC** 옵션을 사용 하려면 코드가 도우미 함수를 제공 하는 CRT (C 런타임 라이브러리)에 연결 되어야 합니다 `__CheckForDebuggerJustMyCode` . 프로젝트에서 CRT에 연결 하지 않으면 링커 오류 **LNK2019: 확인 되지 않은 외부 기호 __CheckForDebuggerJustMyCode** 표시 될 수 있습니다. 이 오류를 해결 하려면 CRT에 연결 하거나 **/JMC** 옵션을 사용 하지 않도록 설정 합니다.

기본적으로 **/JMC** 컴파일러 옵션은 해제 되어 있습니다. 그러나 Visual Studio 2017 버전 15.8부터이 옵션은 대부분의 Visual Studio 프로젝트 템플릿에서 사용할 수 있습니다. 이 옵션을 명시적으로 사용 하지 않도록 설정 하려면 명령줄에서 **/JMC-** 옵션을 사용 합니다. Visual Studio에서 프로젝트 속성 페이지 대화 상자를 열고 **구성 속성** C/c   >  **+ +**  >  **일반** 속성 페이지의 지원 내 코드만 디버깅 속성을 **아니요** 로 변경 합니다.

자세한 내용은 [visual studio에서 내 코드만를 사용 하 여 사용자 코드만 디버그할 지 여부 지정](/visualstudio/debugger/just-my-code)에서 [c + + 내 코드만](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code) 를 참조 하 고, [Visual studio에서 c + + 내 코드만 단계별 실행을 발표](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/)하는 Visual C++ 팀 블로그 게시물을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** > **C/C++**  > **일반** 속성 페이지를 선택합니다.

1. **지원 내 코드만 디버깅** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
