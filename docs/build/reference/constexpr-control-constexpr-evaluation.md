---
description: 다음에 대 한 자세한 정보:/hconstexpr (컨트롤 constexpr 평가)
title: /constexpr(컨트롤 constexpr 평가)
ms.date: 08/15/2017
f1_keywords:
- /constexpr
- -constexpr
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
ms.openlocfilehash: a9274321933fb0fbcf965943b0168db85c8a8d5c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205345"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr(컨트롤 constexpr 평가)

컴파일 시간에 계산에 대 한 매개 변수를 제어 하려면 **/sers** 컴파일러 옵션을 사용 **`constexpr`** 합니다.

## <a name="syntax"></a>Syntax

> **/cerx: 깊이**<em>N</em>\
> **/constexpr: backtrace**<em>N</em>\
> **/constexpr:**<em>N</em> 단계

## <a name="arguments"></a>인수

**깊이**<em>n</em> 재귀 함수 호출의 깊이 **`constexpr`** 를 *n* 수준으로 제한 합니다. 기본값은 512입니다.

**backtrace**<em>n</em> 진단에서 최대 *n* 개의 평가를 표시 **`constexpr`** 합니다. 기본값은 10입니다.

<em></em> n 단계 **`constexpr`** 를 완료 한  후 n 단계를 종료 합니다. 기본값은 10만입니다.

## <a name="remarks"></a>설명

**/Sers** 컴파일러 옵션은 식의 컴파일 타임 계산을 제어 합니다 **`constexpr`** . 평가 단계, 재귀 수준 및 backtrace 깊이가 계산에 너무 많은 시간을 소비 하는 것을 방지 하기 위해 제어 됩니다 **`constexpr`** . 언어 요소에 대 한 자세한 내용은 **`constexpr`** [Constexpr (c + +)](../../cpp/constexpr-cpp.md)을 참조 하세요.

**/Oere** 옵션은 Visual Studio 2015부터 사용할 수 있습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다.

2. **구성 속성** 에서 **C/c + +** 폴더를 확장 하 고 **명령줄** 속성 페이지를 선택 합니다.

3. **추가 옵션** 상자에/cererers 옵션을 입력 합니다.  **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
