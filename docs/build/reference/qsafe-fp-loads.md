---
description: 다음에 대 한 자세한 정보:/Qsafe_fp_loads
title: /Qsafe_fp_loads
ms.date: 01/24/2018
ms.openlocfilehash: e569b308d2da982c72775699ff2149daa45a8f2a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225520"
---
# <a name="qsafe_fp_loads"></a>/Qsafe_fp_loads

부동 소수점 값에 대한 정수 이동 명령을 필요로 하고 특정 부동 소수점 부하 최적화를 사용하지 않도록 설정합니다.

## <a name="syntax"></a>Syntax

> **/Qsafe_fp_loads**

## <a name="remarks"></a>설명

**/Qsafe_fp_loads** 은 x 86을 대상으로 하는 컴파일러 에서만 사용할 수 있습니다. x64 또는 ARM을 대상으로 하는 컴파일러에서는 사용할 수 없습니다.

**/Qsafe_fp_loads** 를 사용 하면 컴파일러에서 부동 소수점 이동 명령 대신 정수 이동 명령을 사용 하 여 메모리와 MMX 레지스터 간에 데이터를 이동 합니다. 이 옵션은 또한 로드 시 값(예: NaN 값)이 예외를 일으킬 수 있는 여러 제어 경로에서 로드할 수 있는 부동 소수점 값에 대한 레지스터 로드 최적화를 사용하지 않도록 설정합니다.

이 옵션은 [/fp: except](fp-specify-floating-point-behavior.md)에 의해 재정의 됩니다. **/Qsafe_fp_loads** **/fp: except** 로 지정 된 컴파일러 동작의 하위 집합을 지정 합니다.

**/Qsafe_fp_loads** [/clr](clr-common-language-runtime-compilation.md) 및 [/fp: fast](fp-specify-floating-point-behavior.md)와 호환 되지 않습니다. 부동 소수점 컴파일러 옵션에 대 한 자세한 내용은 [/fp (Floating-Point 동작 지정)](fp-specify-floating-point-behavior.md)를 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력 합니다. **확인** 을 선택하여 변경 내용을 적용합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/Q 옵션 (하위 수준 작업)](q-options-low-level-operations.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
