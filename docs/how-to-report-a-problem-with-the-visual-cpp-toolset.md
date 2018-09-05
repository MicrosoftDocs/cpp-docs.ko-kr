---
title: Visual C++ 도구 집합의 문제를 보고하는 방법 | Microsoft Docs
ms.date: 06/21/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 359c9d3f72ffa87abf49c6e3ca90743ad0fc80a3
ms.sourcegitcommit: 9be4b66efa45dc132cef06eb3b258c2252ea23a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/16/2018
ms.locfileid: "42583897"
---
# <a name="how-to-report-a-problem-with-the-visual-c-toolset-or-documentation"></a>Visual C++ 도구 집합 또는 설명서의 문제를 보고하는 방법

Microsoft Visual C++ 컴파일러, 링커 또는 기타 도구 및 라이브러리에 문제가 발생하는 경우 문제를 파악하고자 합니다. 문제가 설명서에 있으면 해당 내용도 알고 싶습니다.

## <a name="how-to-report-a-c-toolset-issue"></a>C++ 도구 집합 문제를 보고하는 방법

문제를 알리는 가장 좋은 방법은 발생한 문제에 대한 설명, 프로그램 빌드 방법에 대한 세부 정보 및 다른 컴퓨터에서 문제를 재현하는 데 사용할 수 있는 완전한 테스트 사례인 *재현*을 보내는 것입니다. 이 정보를 통해 문제가 코드에 있고 사용자 환경에서만 발생하는 문제가 아님을 빠르게 확인할 수 있으며, 다른 버전의 컴파일러에 영향을 주는지 여부를 확인하고 원인을 진단할 수 있습니다.

아래 섹션에서는 좋은 보고서를 만드는 방법, 발견한 문제 유형에 대한 재현을 생성하는 방법 및 제품 팀에 보고서를 보내는 방법에 대해 살펴보겠습니다. 보고서는 Microsoft와 다른 개발자에게 중요합니다. Visual C++ 개선에 도움 주셔서 감사합니다!

## <a name="how-to-prepare-your-report"></a>보고서를 준비하는 방법

완전한 정보가 없으면 발생한 문제를 다른 컴퓨터에서 재현하는 것이 매우 어렵기 때문에 고품질 보고서를 만드는 것이 중요합니다. 보고서가 향상될수록 더 효과적으로 문제를 재현하고 진단할 수 있습니다.

보고서에는 최소한 다음 정보가 포함되어야 합니다.

- 사용 중인 도구 집합의 전체 버전 정보

- 코드를 빌드하는 데 사용된 전체 cl.exe 명령줄

- 발생한 문제에 대한 자세한 설명

- 재현: 문제를 보여주는 완전하고 간소화된 자체 포함 소스 코드 예제입니다.

필요한 특정 정보와 해당 정보를 찾을 수 있는 위치 그리고 좋은 재현을 만드는 방법에 대해 자세히 읽어보세요.

### <a name="the-toolset-version"></a>도구 집합 버전

다른 컴퓨터에서 동일한 도구 집합을 대상으로 재현을 테스트할 수 있도록 문제의 원인이 될 수 있는 도구 집합의 전체 버전 정보 및 대상 아키텍처가 필요합니다. 문제를 재현할 수 있는 경우 이 정보는 동일한 문제가 발생하는 다른 도구 집합 버전을 조사하는 시작점을 제공하기도 합니다.

#### <a name="to-report-the-full-version-of-the-compiler-youre-using"></a>사용 중인 컴파일러의 전체 버전을 보고하려면

1. 프로젝트를 빌드하는 데 사용된 Visual Studio 버전 및 구성 아키텍처와 일치하는 **개발자 명령 프롬프트**를 엽니다. 예를 들어 x64 대상에 x64 Visual Studio 2017을 사용하여 빌드하는 경우 **VS 2017용 x64 Native Tools 명령 프롬프트**를 선택합니다. 자세한 내용은 [개발자 명령 프롬프트 바로 가기](build/building-on-the-command-line.md#developer-command-prompt-shortcuts)를 참조하세요.

1. 개발자 명령 프롬프트 콘솔 창에서 **cl /Bv** 명령을 입력합니다.

다음과 유사한 출력이 표시됩니다.

```Output
C:\Users\username\Source>cl /Bv
Microsoft (R) C/C++ Optimizing Compiler Version 19.14.26428.1 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

Compiler Passes:
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\cl.exe:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1xx.dll:      Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c2.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\link.exe:      Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\mspdb140.dll:  Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\1033\clui.dll: Version 19.14.26428.1

cl : Command line error D8003 : missing source filename
```

전체 출력을 복사하여 보고서에 붙여넣습니다.

### <a name="the-command-line"></a>명령줄

다른 컴퓨터에서 동일한 방식으로 빌드하기 위해 코드를 빌드하는 데 사용된 정확한 명령줄(cl.exe 및 모든 인수)이 필요합니다. 발생한 문제가 특정 인수 또는 인수 조합을 사용하여 빌드하는 경우에만 나타날 수도 있기 때문에 이 정보는 중요합니다.

이 정보를 찾을 수 있는 최상의 위치는 문제가 발생한 직후의 빌드 로그입니다. 이렇게 하면 문제를 초래하는 동일한 인수가 명령줄에 정확히 포함됩니다.

#### <a name="to-report-the-contents-of-the-command-line"></a>명령줄의 내용을 보고하려면

1. **CL.command.1.tlog** 파일을 찾아서 엽니다. 기본적으로 이 파일은 \\Visual Studio *버전*\\Projects\\*SolutionName*\\*ProjectName*\\*Configuration*\\*ProjectName*.tlog\\CL.command.1.tlog의 Documents 폴더에, 또는 \\Source\\Repos\\*SolutionName*\\*ProjectName*\\*Configuration*\\*ProjectName*.tlog\\CL.command.1.tlog의 User 폴더에 있습니다. 다른 빌드 시스템을 사용하거나 프로젝트의 기본 위치를 변경한 경우 이 파일이 다른 위치에 있을 수도 있습니다.

   이 파일 내에서 소스 코드 파일의 이름과 각 파일을 컴파일하는 데 사용된 명령줄 인수를 각 줄에 하나씩 찾을 수 있습니다.

1. 문제가 발생하는 소스 코드 파일의 이름을 포함하는 줄을 찾습니다. 그 아래 줄에는 해당 cl.exe 명령 인수가 포함되어 있습니다.

전체 명령줄을 복사하여 보고서에 붙여넣습니다.

### <a name="a-description-of-the-problem"></a>문제에 대한 설명

다른 컴퓨터에서도 동일한 결과가 표시되는지 확인할 수 있도록 발생한 문제에 대한 자세한 설명이 필요합니다. 이 정보는 수행하려던 작업과 예상한 동작을 파악하는 데에도 유용할 수 있습니다.

도구 집합에서 표시한 **정확한 오류 메시지** 또는 정확한 런타임 동작을 알려주세요. 문제를 올바르게 재현했는지 확인하려면 이 정보가 필요합니다. 마지막 오류 메시지뿐 아니라 **모든** 컴파일러 출력을 포함해주세요. 보고하신 문제를 초래한 모든 항목을 살펴보아야 합니다. 명령줄 컴파일러를 사용하여 문제를 복제할 수 있는 경우 해당 컴파일러 출력을 보내주시는 것이 가장 좋으며, IDE 및 다른 빌드 시스템은 표시되는 오류 메시지를 필터링하거나 오류 메시지의 첫 번째 줄만 캡처할 수 있습니다.

컴파일러가 잘못된 코드를 수락하고 진단을 생성하지 않는 문제인 경우 보고서에 해당 내용을 기록해 주세요.

런타임 동작 문제를 보고하려는 경우 프로그램에서 출력하는 내용의 **정확한 복사본**과 보려고 하는 내용을 포함시킵니다. 출력 문에 포함하는 것이 가장 좋습니다(예: `printf("This should be 5: %d\n", actual_result);`). 프로그램이 충돌하거나 중단되는 경우 그 내용도 기록해 주세요.

시도해 보신 해결 방법처럼 발생한 문제를 진단하는 데 도움이 될 만한 다른 정보도 추가해 주세요. 보고서에 같은 정보를 반복해서 포함하지 마세요.

### <a name="the-repro"></a>재현

재현은 발생한 문제를 재현하여 보여주는 완전한 자체 포함된 소스 코드 예제입니다(따라서 이름). 저희가 사용하는 컴퓨터에서 오류를 재현하려면 재현이 필요합니다. 코드는 그 자체만으로도 컴파일 및 실행되는 또는 발생한 문제에 사용하지 않는 경우 컴파일 및 실행되는 간단한 실행 파일을 만들기에 충분해야 합니다. 재현은 코드 조각이 아닙니다. 완전한 함수 및 클래스가 있어야 하며 표준 헤더에 대해서도 필요한 모든 #include 지시문을 포함하고 있어야 합니다.

#### <a name="what-makes-a-good-repro"></a>좋은 재현의 조건

좋은 재현의 조건은 다음과 같습니다.

- **최소**. 재현은 발생한 문제를 정확하게 보여 주면서도 최대한 작아야 합니다. 재현은 복잡하거나 현실적일 필요가 없습니다. 표준 또는 문서화된 컴파일러 구현을 따르는 코드 또는 진단이 누락된 경우 따르지 않은 코드를 보여주기만 하면 됩니다. 간단하게 말해서, 문제를 보여주는 데 필요한 만큼만 코드를 포함하는 재현이 가장 좋습니다. 코드를 제거 또는 간소화하면서도 준수 상태를 유지하고 문제를 변경되지 않은 상태로 유지할 수 있는 경우 그렇게 해주세요. 작동하는 카운터 코드 예제는 필요 없습니다.

- **자체 포함**. 재현에서 불필요한 종속성을 피해야 합니다. 가능한 한, 타사 라이브러리 없이 문제를 재현할 수 있도록 합니다. 간단한 출력 문 이외의 라이브러리 코드 없이 문제를 재현할 수 있는 경우(예: `puts("this shouldn't compile");`, `std::cout << value;`, 및 `printf("%d\n", value);`는 상관 없음) 그렇게 해주세요. 사용자 헤더에 대한 참조 없이 예제를 단일 소스 코드 파일로 요약할 수 있다면 가장 좋습니다. 가능한 문제 원인으로 고려해야 하는 코드 양을 줄이면 도움이 됩니다.

- **최신 컴파일러 버전 사용**. 재현에는 최신 버전 도구 집합의 최신 업데이트 또는 가능하다면 다음 업데이트 또는 다음 주요 릴리스의 최신 시험판 버전을 사용해야 합니다. 이전 버전의 도구 집합에서 발생하는 문제가 최신 버전에서 수정된 경우가 많습니다. 픽스는 예외적인 경우에만 이전 버전으로 백포팅됩니다.

- 관련된 경우 **다른 컴파일러에서 확인**하세요. 포팅 가능한 C++ 코드를 포함하는 재현은 가능한 경우 다른 컴파일러에서 동작을 확인해야 합니다. Standard는 궁극적으로 프로그램 정확성을 결정하며 어떤 컴파일러도 완벽하지는 않습니다. 그러나 Clang 및 GCC는 진단 없이 코드를 수락하고 MSVC는 수락하지 않으면 컴파일러에 버그가 있을 가능성이 높습니다. (그 외의 가능성으로 Unix와 Windows의 동작이 서로 다르거나 C++ 표준 구현의 수준이 다를 수 있습니다.) 반면, 모든 컴파일러에서 코드를 거부하는 경우 코드가 잘못되었을 가능성이 높습니다. 여러 오류 메시지를 보면 직접 문제를 진단하는 데 도움이 될 수 있습니다.

   ISO C++ 웹 사이트의 [온라인 C++ 컴파일러](https://isocpp.org/blog/2013/01/online-c-compilers)에서 또는 GitHub의 엄선된 [온라인 C++ 컴파일러 목록](https://arnemertz.github.io/online-compilers/)에서 코드를 테스트할 온라인 컴파일러 목록을 찾을 수 있습니다. 몇 가지 구체적인 예제로 [Wandbox](https://wandbox.org/), [컴파일러 탐색기](https://godbolt.org/) 및 [Coliru](http://coliru.stacked-crooked.com/)가 포함됩니다.

   > [!NOTE]
   > 온라인 컴파일러 웹 사이트는 Microsoft와 관련이 없습니다. 많은 온라인 컴파일러 웹 사이트가 개인 프로젝트로 실행되며 이러한 사이트 중에는 현재 사용할 수 없는 곳도 있을 것입니다. 하지만 검색을 통해 사용 가능한 다른 사이트를 찾을 수 있습니다.

컴파일러, 링커 및 라이브러리의 문제는 특정 방식으로 드러나는 경향이 있습니다. 발생한 문제 종류에 따라 보고서에 포함해야 하는 재현 종류가 결정됩니다. 적절한 재현이 없으면 아무것도 조사할 수 없습니다. 다음은 여러분이 목격할 수 있는 몇 가지 종류의 문제와 각 문제 유형을 보고할 때 사용할 재현을 생성하는 방법에 대한 지침입니다.

#### <a name="frontend-parser-crash"></a>프런트 엔드(파서) 충돌

프런트 엔드 충돌은 컴파일러의 구문 분석 단계 중에 발생합니다. 일반적으로 컴파일러는 [심각한 오류 C1001](error-messages/compiler-errors-1/fatal-error-c1001.md)을 내보내고 오류가 발생한 소스 코드 파일 및 줄 번호를 참조합니다. msc1.cpp 파일을 언급하는 경우도 많지만 이 세부 정보는 무시해도 됩니다.

이러한 종류의 충돌을 보고하려면 [전처리 재현](#preprocessed-repros)을 제공하세요.

이러한 종류의 충돌에 대한 컴파일러 출력 예는 다음과 같습니다.

```Output
SandBoxHost.cpp
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        fatal error C1001: An internal error has occurred in the compiler.
(compiler file 'msc1.cpp', line 1369)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        note: This diagnostic occurred in the compiler generated function
        'void Microsoft::Ceres::Common::Tools::Sandbox::SandBoxedProcess::Dispose(bool)'
Internal Compiler Error in d:\o\dev\otools\bin\x64\cl.exe.  You will be prompted
        to send an error report to Microsoft later.
INTERNAL COMPILER ERROR in 'd:\o\dev\otools\bin\x64\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

#### <a name="backend-code-generation-crash"></a>백 엔드(코드 생성) 충돌

백 엔드 충돌은 컴파일러의 코드 생성 단계 중에 발생합니다. 일반적으로 컴파일러는 [심각한 오류 C1001](error-messages/compiler-errors-1/fatal-error-c1001.md)을 내보내며, 문제와 관련된 소스 코드 파일 및 줄 번호를 참조하지 않을 수도 있습니다. compiler\\utc\\src\\p2\\main.c 파일을 언급하는 경우도 많지만 이 세부 정보는 무시해도 됩니다.

이러한 종류의 충돌을 보고하려면 LTCG(링크 타임 코드 생성)를 사용하는 경우(cl.exe에 대한 **/GL** 명령줄 인수를 사용하여 설정) [링크 재현](#link-repros)을 제공해 주세요. 사용하지 않는 경우 그 대신 [전처리 재현](#preprocessed-repros)을 제공해 주세요.

다음은 LTCG가 사용되지 않는 백 엔드 충돌에 대한 컴파일러 출력 예제입니다. 컴파일러 출력이 이렇게 표시되는 경우 [전처리 재현](#preprocessed-repros)을 제공해야 합니다.

```Output
repro.cpp
\\officefile\public\tadg\vc14\comperror\repro.cpp(13) : fatal error C1001:
        An internal error has occurred in the compiler.
(compiler file 'f:\dd\vctools\compiler\utc\src\p2\main.c', line 230)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
INTERNAL COMPILER ERROR in
        'C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\BIN\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

**INTERNAL COMPILER ERROR**로 시작하는 줄에서 cl.exe 대신 link.exe가 언급되는 경우 LTCG가 사용된 것이며 [링크 재현](#link-repros)을 제공해야 합니다. 컴파일러 오류 메시지에서 LTCG 사용 여부가 확실하지 않은 경우 이전 단계에서 빌드 로그를 통해 복사한 명령줄 인수에서 **/GL** 명령줄 인수를 검사해야 할 수도 있습니다.

#### <a name="linker-crash"></a>링커 충돌

링커 충돌은 컴파일러가 실행된 후 연결 단계 중에 발생합니다. 일반적으로 링커는 [링커 도구 오류 LNK1000](error-messages/tool-errors/linker-tools-error-lnk1000.md)을 내보냅니다.

> [!NOTE]
> 출력에서 C1001이 언급되거나 링크 타임 코드 생성이 포함된 경우 대신 [백 엔드(코드 생성) 충돌](#backend-code-generation-crash)에서 자세한 내용을 참조하세요.

이러한 종류의 충돌을 보고하려면 [링크 재현](#link-repros)을 제공하세요.

이러한 종류의 충돌에 대한 컴파일러 출력 예는 다음과 같습니다.

```Output
z:\foo.obj : error LNK1000: Internal error during IMAGE::Pass2

  Version 14.00.22816.0

  ExceptionCode            = C0000005
  ExceptionFlags           = 00000000
  ExceptionAddress         = 00007FF73C9ED0E6 (00007FF73C9E0000)
        "z:\tools\bin\x64\link.exe"
  NumberParameters         = 00000002
  ExceptionInformation[ 0] = 0000000000000000
  ExceptionInformation[ 1] = FFFFFFFFFFFFFFFF

CONTEXT:

  Rax    = 0000000000000400  R8     = 0000000000000000
  Rbx    = 000000655DF82580  R9     = 00007FF840D2E490
  Rcx    = 005C006B006F006F  R10    = 000000655F97E690
  Rdx    = 000000655F97E270  R11    = 0000000000000400
  Rsp    = 000000655F97E248  R12    = 0000000000000000
  Rbp    = 000000655F97EFB0  E13    = 0000000000000000
  Rsi    = 000000655DF82580  R14    = 000000655F97F390
  Rdi    = 0000000000000000  R15    = 0000000000000000
  Rip    = 00007FF73C9ED0E6  EFlags = 0000000000010206
  SegCs  = 0000000000000033  SegDs  = 000000000000002B
  SegSs  = 000000000000002B  SegEs  = 000000000000002B
  SegFs  = 0000000000000053  SegGs  = 000000000000002B
  Dr0    = 0000000000000000  Dr3    = 0000000000000000
  Dr1    = 0000000000000000  Dr6    = 0000000000000000
  Dr2    = 0000000000000000  Dr7    = 0000000000000000
```

증분 연결이 사용되고 초기 연결이 성공한 후에만(즉, 후속 증분 연결의 기준이 되는 첫 번째 전체 연결 후에만) 충돌이 발생한 경우 초기 연결이 완료된 후 수정한 소스 파일에 해당하는 개체(.obj) 및 라이브러리(.lib) 파일의 복사본도 제공해 주세요.

#### <a name="bad-code-generation"></a>잘못된 코드 생성

잘못된 코드 생성은 드물지만 컴파일러에서 실수로 잘못된 코드가 생성되고 응용 프로그램이 컴파일 시간에 이 문제를 검색하지 못하고 런타임에 충돌하는 경우에 발생합니다. 발생하는 문제로 인해 잘못된 코드가 생성된다고 의심하는 경우 보고서를 [백 엔드(코드 생성) 충돌](#backend-code-generation-crash)과 동일하게 처리하세요.

이러한 종류의 충돌을 보고하려면 LTCG(링크 타임 코드 생성)를 사용하는 경우(cl.exe에 대한 **/GL** 명령줄 인수를 사용하여 설정) [링크 재현](#link-repros)을 제공해 주세요. 사용하지 않는 경우 [전처리 재현](#preprocessed-repros)을 제공해 주세요.

## <a name="how-to-generate-a-repro"></a>재현 생성 방법

문제의 원인을 추적하려면 [좋은 재현](#what-makes-a-good-repro)이 중요합니다. 특정 종류의 재현에 대해 아래에 설명된 단계를 수행하기 전에 문제를 보여주는 코드를 최대한 압축합니다. 종속성, 필요한 헤더 및 라이브러리를 제거 또는 최소화하고, 가능하다면 사용되는 컴파일러 옵션 및 전처리기 정의를 제한합니다.

다음은 각기 다른 종류의 문제를 보고하는 데 사용할 다양한 종류의 재현을 생성하기 위한 지침입니다.

### <a name="preprocessed-repros"></a>전처리 재현

*전처리 재현*은 문제를 보여 주고 원래 재현 소스 파일에서 **/P** 컴파일러 옵션을 사용하여 C 전처리기의 출력에서 생성되는 단일 소스 파일입니다. 포함된 헤더를 인라인으로 처리하여 추가 소스 및 헤더 파일에 대한 종속성을 제거하며 매크로, #ifdef 및 로컬 환경에 종속될 수 있는 다른 전처리기 명령도 확인합니다.

> [!NOTE]
> 진행 중인 최신 구현을 대체하여 이미 문제가 해결되었는지 확인하는 경우가 많기 때문에, 전처리 재현은 표준 라이브러리 구현에 있는 버그의 결과로 나타날 수 있는 문제를 해결하기에는 유용하지 않습니다. 이 경우 재현을 전처리하지 말고, 문제를 단일 소스 파일로 줄일 수 없는 경우 코드를 .zip 파일 등으로 패키징하거나 IDE 프로젝트 재현을 사용하는 것이 좋습니다. 자세한 내용은 [기타 재현](#other-repros)을 참조하세요.

#### <a name="to-preprocess-a-source-code-file"></a>소스 코드 파일을 전처리하려면

1. [명령줄의 내용을 보고하려면](#to-report-the-contents-of-the-command-line)에 설명된 대로 재현을 빌드하는 데 사용된 명령줄 인수를 캡처합니다.

1. 프로젝트를 빌드하는 데 사용된 Visual Studio 버전 및 구성 아키텍처와 일치하는 **개발자 명령 프롬프트**를 엽니다.

1. 재현 프로젝트가 포함된 디렉터리로 변경합니다.

1. 개발자 명령 프롬프트 콘솔 창에서 **cl /P** *arguments* *filename.cpp* 명령을 입력합니다. 여기서 *arguments*는 위에서 캡처된 인수 목록이고 *filename.cpp*는 재현 소스 파일의 이름입니다. 이 명령은 재현에 사용된 명령줄을 복제하지만, 전처리기 패스 후 컴파일을 중지하고 전처리된 소스 코드를 *filename*.i로 출력합니다.

C++/CX 소스 코드 파일을 전처리하거나 C++ 모듈 기능을 사용하는 경우 몇 가지 추가 단계가 필요합니다. 자세한 내용은 아래 섹션을 참조하세요.

전처리된 파일을 생성한 후에는 전처리된 파일을 사용하여 여전히 문제가 재현되는지 확인하는 것이 좋습니다.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>전처리된 파일에서도 오류가 재현되는지 확인하려면

1. 개발자 명령 프롬프트 콘솔 창에서 **cl** *arguments* **/TP** *filename*.i 명령을 입력하여 cl.exe에 전처리된 파일을 C++ 소스 파일로 컴파일하라고 알립니다. 여기서 *arguments*는 위에서 캡처된 인수 목록이고(하지만 **/D** 및 **/I** 인수는 이미 전처리된 파일에 포함되었으므로 제거), *filename*.i는 전처리된 파일의 이름입니다.

1. 문제가 재현되는지 확인합니다.

마지막으로 전처리된 재현 *filename*.i를 보고서에 첨부합니다.

### <a name="preprocessed-ccx-winrtuwp-code-repros"></a>전처리된 C++/CX WinRT/UWP 코드 재현

실행 파일을 빌드하기 위해 C++/CX를 사용하는 경우 전처리된 재현을 만들고 유효성을 검사하는 데 필요한 몇 가지 추가 단계가 있습니다.

#### <a name="to-preprocess-ccx-source-code"></a>C++/CX 소스 코드를 전처리하려면

1. [소스 코드 파일을 전처리하려면](#to-preprocess-a-source-code-file)에서 설명된 대로 전처리된 소스 파일을 만듭니다.

1. 생성된 _filename_.i 파일에서 **#using** 지시문을 검색합니다.

1. 참조된 모든 파일의 목록을 만듭니다. Windows\*.winmd 파일, platform.winmd 파일 및 mscorlib.dll은 그대로 둡니다.

전처리된 파일이 여전히 문제를 일으키는지 검증할 준비를 하려면,

1. 전처리된 파일에 대한 새 디렉터리를 만들어 새 디렉터리에 복사합니다.

1. **#using** 목록의 .winmd 파일을 새 디렉터리로 복사합니다.

1. 새 디렉터리에서 빈 vccorlib.h 파일을 만듭니다.

1. 전처리된 파일을 편집하여 mscorlib.dll에 대한 **#using** 지시문을 제거합니다.

1. 전처리된 파일을 편집하여 절대 경로를 복사된 .winmd 파일의 기본 파일 이름으로 변경합니다.

위와 같이 전처리된 파일이 여전히 문제를 일으키는지 확인합니다.

### <a name="preprocessed-c-modules-repros"></a>전처리된 C++ 모듈 재현

C++ 컴파일러의 모듈 기능을 사용하는 경우 전처리된 재현을 만들고 유효성을 검사하는 데 필요한 몇 가지 단계가 있습니다.

#### <a name="to-preprocess-a-source-code-file-that-uses-a-module"></a>모듈을 사용하는 소스 코드 파일을 전처리하려면

1. [명령줄의 내용을 보고하려면](#to-report-the-contents-of-the-command-line)에 설명된 대로 재현을 빌드하는 데 사용된 명령줄 인수를 캡처합니다.

1. 프로젝트를 빌드하는 데 사용된 Visual Studio 버전 및 구성 아키텍처와 일치하는 **개발자 명령 프롬프트**를 엽니다.

1. 재현 프로젝트가 포함된 디렉터리로 변경합니다.

1. 개발자 명령 프롬프트 콘솔 창에서 **cl /P** *arguments* *filename.cpp* 명령을 입력합니다. 여기서 *arguments*는 위에서 캡처된 인수 목록이고 *filename.cpp*는 모듈을 사용하는 소스 파일의 이름입니다.

1. 모듈 인터페이스(.ifc 출력)를 빌드한 재현 프로젝트를 포함하는 디렉터리로 변경합니다.

1. 모듈 인터페이스를 빌드하는 데 사용된 명령줄 인수를 캡처합니다.

1. 개발자 명령 프롬프트 콘솔 창에서 **cl /P** *arguments* *modulename.ixx* 명령을 입력합니다. 여기서 *arguments*는 위에서 캡처된 인수 목록이고 *modulename.ixx*는 모듈 인터페이스를 만드는 소스 파일의 이름입니다.

전처리된 파일을 생성한 후에는 전처리된 파일을 사용하여 여전히 문제가 재현되는지 확인하는 것이 좋습니다.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>전처리된 파일에서도 오류가 재현되는지 확인하려면

1. 개발자 콘솔 창에서 재현 프로젝트가 포함된 디렉터리로 다시 변경합니다.

1. 위와 같이 **cl** *arguments* **/TP** *filename*.i를 입력하여 전처리된 파일을 C++ 소스 파일처럼 컴파일합니다.

1. 전처리된 파일이 여전히 문제를 일으키는지 확인합니다.

마지막으로 .ifc 출력과 함께 전처리된 재현 파일(*filename*.i 및 *modulename*.i)을 보고서에 첨부합니다.

### <a name="link-repros"></a>링크 재현

*링크 재현*은 **link\_repro** 환경 변수를 통해 지정되는 디렉터리의 링커 생성 콘텐츠입니다. LTCG(링크 타임 코드 생성)를 포함한 백 엔드 충돌 또는 링커 충돌처럼 링크 타임에 발생하는 문제를 전체적으로 보여주는 빌드 아티팩트를 포함하고 있습니다. 이러한 빌드 아티팩트는 문제를 재현할 수 있도록 링커 입력으로 필요합니다. 이 환경 변수를 사용하여 링커의 기본 재현 생성 기능을 사용하면 손쉽게 링크 재현을 만들 수 있습니다.

#### <a name="to-generate-a-link-repro"></a>링크 재현을 생성하려면

1. [명령줄의 내용을 보고하려면](#to-report-the-contents-of-the-command-line)에 설명된 대로 재현을 빌드하는 데 사용된 명령줄 인수를 캡처합니다.

1. 프로젝트를 빌드하는 데 사용된 Visual Studio 버전 및 구성 아키텍처와 일치하는 **개발자 명령 프롬프트**를 엽니다.

1. 개발자 명령 프롬프트 콘솔 창에서 재현 프로젝트가 포함된 디렉터리로 변경합니다.

1. **mkdir linkrepro**를 입력하여 링크 재현을 위한 디렉터리를 만듭니다.

1. **set link\_repro=linkrepro** 명령을 입력하여 **link\_repro** 환경 변수를 방금 만든 디렉터리로 설정합니다. 다른 디렉터리에서 빌드가 실행된 경우 더 복잡한 프로젝트와 마찬가지로 대신 **link\_repro**를 linkrepro 디렉터리 전체 경로로 설정합니다.

1. Visual Studio에서 재현 프로젝트를 빌드하려면 개발자 명령 프롬프트 콘솔 창에서 **devenv** 명령을 입력합니다. 이렇게 하면 **link\_repro** 환경 변수의 값이 Visual Studio에 표시됩니다. 명령줄에서 프로젝트를 빌드하려면 위에서 캡처한 명령줄 인수를 사용하여 재현 빌드를 복제합니다.

1. 재현 프로젝트를 빌드하고 예상한 문제가 발생하는지 확인합니다.

1. Visual Studio를 사용하여 빌드를 수행한 경우 Visual Studio를 닫습니다.

1. 개발자 명령 프롬프트 콘솔 창에서 **set link\_repro=** 명령을 입력하여 **link\_repro** 환경 변수를 지웁니다.

마지막으로, 전체 linkrepro 디렉터리를 .zip 파일 등으로 압축하여 재현을 패키징하고 보고서에 첨부합니다.

### <a name="other-repros"></a>기타 재현

문제를 단일 소스 파일이나 전처리 재현으로 줄일 수 없고 문제에 링크 재현이 필요하지 않은 경우 IDE 프로젝트를 조사할 수 있습니다. 좋은 재현을 만드는 방법에 대한 모든 지침이 여전히 적용됩니다. 코드는 크기를 최소화하고 자체 포함되어야 하며, 가장 최신 도구에서 문제가 발생해야 하며, 관련이 있는 경우 다른 컴파일러에서 문제가 보이면 안 됩니다.

재현을 최소 IDE 프로젝트로 만든 다음 전체 디렉터리 구조를 .zip 파일 등으로 압축하여 패키징하고 보고서에 첨부합니다.

## <a name="ways-to-send-your-report"></a>보고서를 보내는 방법

몇 가지 좋은 방법으로 보고서를 보낼 수 있습니다. Visual Studio의 기본 제공 [문제 도구 보고](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) 또는 [Visual Studio 개발자 커뮤니티](https://developercommunity.visualstudio.com/) 페이지를 사용할 수 있습니다. 이 페이지의 아래쪽에 있는 **제품 피드백** 단추를 선택하여 개발자 커뮤니티 페이지로 직접 이동할 수도 있습니다. 스크린 샷을 캡처하여 개발자 커뮤니티 페이지에 게시하기 위해 보고서를 구성하기 위해 IDE에 내장된 도구를 사용할지 여부 또는 웹 사이트를 직접 사용하려는 경우에 따라 선택이 달라집니다.

> [!NOTE]
> 보고서를 제출하는 방법에 관계없이 Microsoft는 사용자의 개인 정보를 보호합니다. Microsoft는 모든 데이터 프라이버시 법률 및 규정을 준수할 것을 약속합니다. Microsoft에서 사용자가 보낸 데이터를 처리하는 방법에 대한 자세한 내용은 [Microsoft 개인정보처리방침](https://privacy.microsoft.com/privacystatement)을 참조하세요.

### <a name="use-the-report-a-problem-tool"></a>문제 보고 도구 사용

Visual Studio의 **문제 보고** 도구는 Visual Studio 사용자가 마우스만 몇 번 클릭하여 다양한 문제를 보고할 수 있는 방법입니다. IDE를 벗어나지 않고 발생한 문제에 대한 자세한 정보를 지정한 다음 보고서를 제출하는 데 사용할 수 있는 간단한 양식을 제공합니다.

**문제 보고** 도구를 통한 문제 보고는 IDE에서 쉽고 간편하게 수행할 수 있습니다. **빠른 시작** 검색 상자 옆에 있는 **사용자 의견 보내기** 아이콘을 선택하여 제목 표시줄에서 액세스하거나 메뉴 표시줄의 **도움말** > **사용자 의견 보내기** > **문제 보고**에서 해당 메뉴를 찾을 수 있습니다.

문제를 보고하려는 경우 개발자 커뮤니티에서 유사한 문제를 검색합니다. 이전에 문제가 보고된 적이 있다면 항목에 찬성하고 추가 세부 정보가 포함된 댓글을 추가하세요. 유사한 문제가 표시되지 않는다면 Visual Studio 피드백 대화 상자의 **새로운 문제 보고** 단추를 선택하고 단계에 따라 문제를 보고합니다.

### <a name="use-the-visual-studio-developer-community-pages"></a>Visual Studio 개발자 커뮤니티 페이지 사용

Visual Studio 개발자 커뮤니티 페이지는 C++ 컴파일러, 도구 및 라이브러리에 대한 문제를 보고하고 해결 방법을 찾을 수 있는 또 다른 편리한 방법입니다. [Visual Studio 질문](https://developercommunity.visualstudio.com/spaces/8/index.html) 페이지에는 IDE 또는 설치 관련 문제를 보고합니다. C++ 컴파일러, 링커, 기타 도구 및 라이브러리와 관련된 문제의 경우 [C++ 질문](https://developercommunity.visualstudio.com/spaces/62/index.html) 페이지를 사용합니다.

개발자 커뮤니티에서 각 페이지의 맨 위 부근에 있는 배너는 자신의 문제와 유사한 문제를 보고하는 게시물이나 항목을 찾는 데 사용할 수 있는 검색 상자입니다. 자신의 문제와 관련된 해결 방법이나 기타 유용한 정보가 기존 항목에 이미 있을 수 있습니다. 누군가가 이전에 동일한 문제를 보고한 경우 새 문제 보고서를 만드는 대신 해당 항목에 찬성하고 댓글을 다세요.

문제가 이전에 보고된 적이 없다면 개발자 커뮤니티 페이지의 검색 상자 옆에 있는 **문제 보고** 단추를 선택하세요. Visual Studio 계정에 로그인하고 개발자 커뮤니티 앱의 프로필 액세스에 동의할지 묻는 메시지가 표시될 수 있습니다. 로그인하면 문제를 보고할 수 있는 페이지로 바로 이동합니다. 재현 코드 및 명령줄, 스크린샷, 관련 토론에 대한 링크 및 자신이 관련성 있고 유용하다고 생각하는 기타 정보를 포함할 수 있습니다.

> [!TIP]
> Visual Studio에서 발생할 수 있고 도구 집합과 관련이 없는 다른 종류의 문제(예: UI 문제, 손상된 IDE 기능 또는 일반 충돌)의 경우 스크린샷 기능 및 발생한 문제를 유발하는 UI 작업 기록 기능 때문에 **문제 보고 도구**가 특히 유용할 수 있습니다. 또한 이러한 종류의 오류는 [개발자 커뮤니티](https://developercommunity.visualstudio.com/) 사이트에서도 보고할 수 있습니다.

### <a name="reports-and-privacy"></a>보고서 및 개인 정보

기본적으로 **보고서의 모든 정보와 모든 의견 및 댓글이 공개됩니다**. 일반적으로 다른 사용자가 발견한 문제점, 솔루션 및 해결 방법을 전체 커뮤니티가 볼 수 있기 때문에 이는 장점이 됩니다. 그러나 개인 정보 또는 지적 재산권을 이유로 데이터 또는 신원 공개가 우려되는 경우 이에 대한 옵션이 있습니다.

신원 노출이 우려되는 경우 자신의 세부 정보를 공개하지 않는 [새로운 Microsoft 계정을 만듭니다.](https://signup.live.com/) 이 계정을 사용하여 보고서를 만듭니다. 

**공개된 초기 보고서의 제목이나 내용에 비공개 내용을 넣지 마십시오.** 대신 별도의 주석으로 개인 세부 정보를 보냅니다. 보고서가 적합한 사람들에게 전달되도록 하려면 문제 보고서의 주제 목록에 **cppcompiler**를 포함시킵니다. 문제 보고서가 작성되면 이제 회신과 첨부 파일을 볼 수 있는 사용자를 지정할 수 있습니다.

#### <a name="to-create-a-problem-report-for-private-information"></a>개인 정보에 대한 문제 보고서를 작성하려면

1. 작성한 보고서에서 **메모 추가**를 선택하여 문제에 대한 개인 설명을 작성합니다.

1. 회신 편집기에서 **제출** 및 **취소** 단추 아래의 드롭다운 컨트롤을 사용하여 회신 대상을 지정합니다. 지정한 사람만이 비공개 회신과 그 안에 포함된 이미지, 링크 또는 코드를 볼 수 있습니다. **중재자 및 원래 게시자가 볼 수 있음**을 선택하여 Microsoft 직원과 본인만 볼 수 있도록 제한합니다.

1. 재현에 필요한 설명 및 기타 정보, 이미지 및 첨부 파일을 추가합니다. **제출** 단추를 선택하여 이 정보를 비공개로 보냅니다.

   첨부 파일은 2GB까지 최대 10개로 제한됩니다. 이보다 큰 파일을 업로드하는 경우 비공개 주석으로 업로드 URL을 요청하십시오.

이 주석 아래의 댓글에는 귀하가 지정한 것과 동일한 공개 설정 제한이 있습니다. 이는 회신의 드롭다운 컨트롤이 공개 제한 상태를 올바르게 표시되지 않는 경우에도 마찬가지입니다.

개인 정보를 보호하고 중요한 정보를 공개하지 않으려면 이 제한적 주석에 따라 회신함으로써 Microsoft와의 모든 상호 작용을 유지하세요. 기타 다른 주석에 대한 회신은 실수로 중요한 정보가 누설될 수 있습니다.

## <a name="how-to-report-a-c-documentation-issue"></a>C++ 설명서 문제를 보고하는 방법

GitHub 문제를 사용하여 설명서에 보고된 문제를 추적합니다. 이제 작성자 및 제품 팀과 훨씬 더 다양한 방식으로 상호 작용할 수 있는 콘텐츠 페이지에서 직접 GitHub 문제를 만들 수 있습니다. 문서, 잘못된 코드 샘플, 혼란스러운 설명, 중요한 누락 또는 오타가 있는 문제가 있으면 편안하게 알려주세요. 페이지 아래쪽으로 스크롤하고 **로그인을 선택하여 설명서 피드백을 제공**합니다. 아직 GitHub 계정이 없는 경우 해당 계정을 만들어야 하지만, 일단 계정이 만들어졌으면 보고된 문제에 대한 변경 내용이 있을 경우 설명서 문제와 해당 상태를 모두 확인하고 알림을 받을 수 있습니다. 자세한 내용은 [새로운 피드백 시스템이 docs.microsoft.com에 제공됩니다](/teamblog/a-new-feedback-system-is-coming-to-docs)를 참조하세요.

설명서 피드백 단추를 사용하여 GitHub에 설명서 문제를 만들면, 문제를 만든 페이지에 대한 일부 정보가 해당 문제에 자동으로 채워져 문제가 있는 위치를 알 수 있습니다. 이 정보는 편집하지 마세요. 잘못된 항목 및 원하는 경우 제안된 해결 방법에 대한 세부 정보를 추가하기만 하면 됩니다. [설명서는 오픈 소스](https://github.com/MicrosoftDocs/cpp-docs/)이므로 실제로 수정하고 직접 제안하려는 경우 그렇게 할 수 있습니다. 설명서에 기여할 수 있는 방법에 대한 자세한 내용은 GitHub의 [기여 가이드](https://github.com/MicrosoftDocs/cpp-docs/blob/master/CONTRIBUTING.md)를 참조하세요.

