---
title: /constexpr (컨트롤 constexpr 평가)
ms.date: 08/15/2017
f1_keywords:
- /constexpr
- -constexpr
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
ms.openlocfilehash: ea55a2686c2cdd7f4e0a6b558d3cd456fe87cb9d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544250"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (컨트롤 constexpr 평가)

사용 된 **/constexpr** 컴파일러 옵션에 대 한 제어 매개 변수를 **constexpr** 컴파일 시간에 평가 합니다.

## <a name="syntax"></a>구문

> **/constexpr:depth**<em>N</em>
>  **/constexpr:backtrace**<em>N</em>
>  **/constexpr:** <em>N</em>

## <a name="arguments"></a>인수

**깊이**<em>N</em> 재귀 깊이 제한 **constexpr** 함수를 호출 *N* 수준입니다. 기본값은 512입니다.

**backtrace**<em>N</em> 최대 표시 *N* **constexpr** 진단에서 평가 합니다. 기본값은 10입니다.

**단계**<em>N</em> Terminate **constexpr** 후의 계산 *N* 단계입니다. 기본값은 100,000입니다.

## <a name="remarks"></a>설명

합니다 **/constexpr** 컴파일러 옵션 제어의 컴파일 시간 계산이 **constexpr** 식입니다. 평가 단계, 재귀 수준 및 backtrace 깊이 컴파일러에서 너무 많은 시간을 소비 하지 못하도록 제어 됩니다 **constexpr** 평가 합니다. 대 한 자세한 내용은 합니다 **constexpr** 언어 요소를 참조 하세요 [constexpr (c + +)](../../cpp/constexpr-cpp.md)합니다.

합니다 **/constexpr** 옵션은 Visual Studio 2015부터 사용할 수 있습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트를 엽니다 **속성 페이지** 대화 상자.

2. 아래 **구성 속성**를 확장 합니다 **C/c + +** 폴더 선택한를 **명령줄** 속성 페이지.

3. 입력할 **/constexpr** 컴파일러 옵션에 **추가 옵션** 상자입니다. 선택 **확인** 하거나 **적용** 변경 내용을 저장 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)