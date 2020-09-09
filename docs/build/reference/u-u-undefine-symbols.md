---
title: /U, /u(기호 정의 해제)
description: Microsoft C/c + + 컴파일러/U 및/u 옵션을 사용 하 여 전처리기 기호를 정의 하지 않습니다.
ms.date: 09/03/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
ms.openlocfilehash: 78effabba2fa72e5ab7f2dfc6ef91f22383b063f
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609196"
---
# <a name="u-u-undefine-symbols"></a>/U, /u(기호 정의 해제)

**`/U`** 컴파일러 옵션은 지정 된 전처리기 기호를 해제 합니다. **`/u`** 컴파일러 옵션은 컴파일러에서 정의 하는 Microsoft 관련 기호의 정의를 해제 합니다.

## <a name="syntax"></a>구문

> **`/U`**\[ ]*기호*\
> **`/u`**

## <a name="arguments"></a>인수

*화살표*<br/>
정의 해제할 전처리기 기호입니다.

## <a name="remarks"></a>설명

**`/U`** 및 옵션은 모두 **`/u`** 지시문을 사용 하 여 만든 기호를 정의 해제할 수 **`#define`** 없습니다.

옵션은 **`/U`** 옵션을 사용 하 여 이전에 정의한 기호의 정의를 해제할 수 있습니다 **`/D`** .

기본적으로 컴파일러는 많은 수의 Microsoft 관련 기호를 정의할 수 있습니다. 몇 가지 일반적인 방법은 다음과 같습니다.

| Symbol | 기능 |
|--|--|
| `_CHAR_UNSIGNED` | 기본 문자 형식은 부호가 없습니다. 옵션이 지정 된 경우에 정의 됩니다 [`/J`](j-default-char-type-is-unsigned.md) . |
| `_CPPRTTI` | 옵션으로 컴파일된 코드에 대해 정의 [`/GR`](gr-enable-run-time-type-information.md) 됩니다. |
| `_CPPUNWIND` | 옵션으로 컴파일된 코드에 대해 정의 [`/EHsc`](eh-exception-handling-model.md) 됩니다. |
| `_DLL` | 옵션이 지정 된 경우에 정의 됩니다 [`/MD`](md-mt-ld-use-run-time-library.md) . |
| `_M_IX86` | 기본적으로 x86 대상에 대해 600로 정의 됩니다. |
| `_MSC_VER` | 각 컴파일러 버전에 대 한 고유한 정수 값으로 정의 됩니다. 자세한 내용은 [미리 정의 된 매크로](../../preprocessor/predefined-macros.md)를 참조 하세요. |
| `_WIN32` | WIN32 응용 프로그램에 대해 정의 됩니다. 항상 정의되어 있습니다. |
| `_MT` | [`/MD`](md-mt-ld-use-run-time-library.md)또는 [`/MT`](md-mt-ld-use-run-time-library.md) 옵션을 지정할 때 정의 됩니다. |

Microsoft 전용 미리 정의 된 매크로의 전체 목록은 [미리 정의 된 매크로](../../preprocessor/predefined-macros.md)를 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **고급** 속성 페이지를 선택 합니다.

1. **전처리기 정의** 해제 또는 **모든 전처리기 정의** 정의 해제 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A> 또는 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>을 참조하십시오.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)<br/>
[**`/J`** (부호 없는 기본 문자 형식)](j-default-char-type-is-unsigned.md)<br/>
[**`/GR`** (런타임 형식 정보 사용)](gr-enable-run-time-type-information.md)<br/>
[**`/EH`** (예외 처리 모델)](eh-exception-handling-model.md)<br/>
[**`/MD`**, **`/MT`** , **`/LD`** (런타임 라이브러리 사용)](md-mt-ld-use-run-time-library.md)
