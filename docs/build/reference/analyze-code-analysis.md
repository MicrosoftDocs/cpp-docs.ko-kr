---
title: /analyze(코드 분석)
description: Microsoft c + + 컴파일러/analyze 옵션 구문 및 사용법입니다.
ms.date: 07/27/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
ms.openlocfilehash: e970872e89132aed52190b8688f2cdaccab5ea6f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500087"
---
# <a name="analyze-code-analysis"></a>`/analyze` (코드 분석)

코드 분석 및 제어 옵션을 사용합니다.

## <a name="syntax"></a>구문

::: moniker range=">=vs-2017"

> **`/analyze`**\
> **`/analyze-`**\
> **`/analyze:autolog`**\
> **`/analyze:autolog-`**\
> **`/analyze:autolog:ext`***확장*\
> **`/analyze:log`***파일 이름*\
> **`/analyze:max_paths`***number*\
> **`/analyze:only`**\
> **`/analyze:plugin`***플러그 인-dll*\
> **`/analyze:quiet`**\
> **`/analyze:ruleset`***규칙 집합*\
> **`/analyze:stacksize`***number*\
> **`/analyze:WX-`**

::: moniker-end
::: moniker range="vs-2015"

> **`/analyze`**\
> **`/analyze-`**\
> **`/analyze:autolog`**\
> **`/analyze:autolog-`**\
> **`/analyze:autolog:ext`***확장*\
> **`/analyze:log`***파일 이름*\
> **`/analyze:max_paths`***number*\
> **`/analyze:only`**\
> **`/analyze:plugin`***플러그 인-dll*\
> **`/analyze:quiet`**\
> **`/analyze:stacksize`***number*\
> **`/analyze:WX-`**

::: moniker-end

## <a name="arguments"></a>인수

**`/analyze`**\
기본 모드에서 분석을 설정합니다. 분석 출력은 콘솔 또는 다른 오류 메시지와 같은 Visual Studio **출력** 창으로 이동 합니다. **`/analyze-`** 분석을 명시적으로 해제 하려면를 사용 합니다.

**`/analyze:autolog`**\
자세한 분석기 결과는 원본 파일과 동일한 기본 이름 및 확장명을 가진 파일에 XML로 작성 됩니다 *`.pftlog`* . **`/analyze:autolog-`** 이 로그 파일을 사용 하지 않도록 설정 합니다.

**`/analyze:autolog:ext`***확장*\
자세한 분석기 결과는 원본 파일과 동일한 기본 이름 및 *확장명*확장명을 가진 파일에 XML로 작성 됩니다.

**`/analyze:log`***파일 이름*\
자세한 분석기 결과는 파일 *이름*으로 지정 된 파일에 XML로 기록 됩니다.

**`/analyze:max_paths`***number*\
이 옵션에 사용 되는 *숫자* 매개 변수는 분석할 코드 경로의 최대 수를 지정 합니다. 이 매개 변수를 지정 하지 않으면 기본적으로 256이 표시 됩니다. 값이 클수록 더 철저 하 게 확인할 수 있지만 분석에 시간이 더 오래 걸릴 수 있습니다.

**`/analyze:only`**\
일반적으로 컴파일러는 코드를 생성하고 분석기를 실행한 후에 추가 구문 검사를 실시합니다. **`/analyze:only`** 옵션은이 코드 생성 패스를 해제 합니다. 분석을 더 빠르게 수행 하지만 컴파일러의 코드 생성 통과에서 찾을 수 있는 컴파일러 오류 및 경고는 내보내지 않습니다. 프로그램에 코드 생성 오류가 없는 경우 분석 결과가 불안정 해질 수 있습니다. 코드가 이미 오류 없이 코드 생성 구문 검사를 통과 한 경우에만이 옵션을 사용 하는 것이 좋습니다.

**`/analyze:plugin`***플러그 인-dll*\
코드 분석 실행의 일부로 지정 된 PREfast 플러그 인을 사용 하도록 설정 합니다.

::: moniker range="<=vs-2017"

LocalEspC.dll는 C261XX 경고 범위에서 동시성 관련 코드 분석 검사를 구현 하는 플러그 인입니다. 예: [26100](../../code-quality/c26100.md), [C26101](../../code-quality/c26101.md), ...,  [C26167](../../code-quality/c26167.md).

LocalEspC.dll를 실행 하려면 다음 컴파일러 옵션을 사용 합니다. **`/analyze:plugin LocalEspC.dll`**

::: moniker-end
::: moniker range=">=vs-2019"

ConcurrencyCheck.dll는 C261XX 경고 범위에서 동시성 관련 코드 분석 검사를 구현 합니다. 예: [26100](../../code-quality/c26100.md), [C26101](../../code-quality/c26101.md), ...,  [C26167](../../code-quality/c26167.md).

ConcurrencyCheck.dll를 실행 하려면 먼저 개발자 명령 프롬프트에서 다음 명령을 실행 합니다.

```cmd
set Esp.Extensions=ConcurrencyCheck.dll
```

그런 다음이 컴파일러 옵션을 사용 **`/analyze:plugin EspXEngine.dll`** 합니다.

CppCoreCheck.dll를 실행 하려면 먼저 개발자 명령 프롬프트에서 다음 명령을 실행 합니다.

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

그런 다음이 컴파일러 옵션을 사용 **`/analyze:plugin EspXEngine.dll`** 합니다.

::: moniker-end

**`/analyze:quiet`**\
콘솔 또는 Visual Studio **출력** 창에 대 한 분석기 출력을 끕니다.

::: moniker range=">=vs-2017"

**`/analyze:ruleset`***file_path. 규칙 집합*\
사용자가 직접 만들 수 있는 사용자 지정 규칙 집합을 포함 하 여 분석할 규칙 집합을 지정할 수 있습니다. 이 스위치가 설정 되 면 규칙 엔진이 실행 되기 전에 지정 된 규칙 집합의 멤버가 아닌 멤버를 제외 하기 때문에 더 효율적입니다. 그렇지 않으면 엔진이 모든 규칙을 검사 합니다.

Visual Studio와 함께 제공 되는 규칙 집합은에 있습니다 *`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`* .

다음 샘플 사용자 지정 규칙 집합은 C6001 및 C26494를 확인 하도록 규칙 엔진에 지시 합니다. 이 파일은 확장명이 있는 한 모든 위치에 저장할 수 *`.ruleset`* 있으며 인수의 전체 경로를 제공 합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description="New rules to apply." ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

**`/analyze:stacksize`***number*\
이 옵션에 사용 되는 *숫자* 매개 변수는 경고 [C6262](../../code-quality/c6262.md) 생성 되는 스택 프레임의 크기 (바이트)를 지정 합니다. *Number* 앞의 공백은 선택 사항입니다. 이 매개 변수를 지정 하지 않으면 기본적으로 스택 프레임 크기가 16KB 됩니다.

**`/analyze:WX-`**\
코드 분석 경고는를 사용 하 여 컴파일할 때 오류로 처리 되지 않습니다 **`/WX`** . 자세한 내용은 [ `/WX` (경고 수준)](compiler-option-warning-level.md)를 참조 하세요.

## <a name="remarks"></a>설명

자세한 내용은 c/c [+ + 용 코드 분석 개요](../../code-quality/code-analysis-for-c-cpp-overview.md) 및 [c/c + + 경고에 대 한 코드 분석](../../code-quality/code-analysis-for-c-cpp-warnings.md)을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **코드 분석**  >  **일반** 속성 페이지를 선택 합니다.

1. 하나 이상의 **코드 분석** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)\
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)
