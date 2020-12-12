---
description: 자세한 정보:/Gs (스택 검사 호출 제어)
title: /Gs(스택 검사 호출 제어)
ms.date: 10/25/2018
f1_keywords:
- /GS
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
ms.openlocfilehash: 128a5ad4dbcba15dfc5b76313b8576ce1448ec68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200166"
---
# <a name="gs-control-stack-checking-calls"></a>/Gs(스택 검사 호출 제어)

스택 프로브에 대 한 임계값을 제어 합니다.

## <a name="syntax"></a>Syntax

> **/Gs**[*size*]

## <a name="arguments"></a>인수

*size*<br/>
(옵션) 스택 프로브가 초기화되기 전에 지역 변수가 차지할 수 있는 바이트 수 입니다. **/Gs** 와 *size* 사이에는 공백이 허용 되지 않습니다.

## <a name="remarks"></a>설명

*스택 프로브* 는 컴파일러에서 함수 호출의 시작 부분에 삽입 하는 일련의 코드입니다. 초기화되면 스택 프로브는 함수의 지역 변수를 저장하는 데 필요한 메모리 공간에 원활하게 도달합니다. 이렇게 하면 나머지 함수를 실행 하기 전에 필요한 경우 운영 체제에서 추가 스택 메모리를 투명 하 게 페이지에 추가 합니다.

기본적으로 컴파일러에서는 함수에 스택 공간이 2페이지 이상 필요한 경우 스택 프로브를 초기화하는 코드를 생성합니다. 이는 x86, x64, ARM 및 ARM64 플랫폼용 **/Gs4096** 의 컴파일러 옵션과 동일 합니다. 이 값은 애플리케이션 및 Windows 메모리 관리자가 런타임 시 프로그램 스택으로 동적으로 커밋되는 메모리 양을 늘리도록 합니다.

> [!NOTE]
> **/Gs4096** 의 기본값은 Windows 용 응용 프로그램의 프로그램 스택이 런타임에 올바르게 확장 될 수 있도록 합니다. 변경해야 할 확실한 이유가 없는 경우에는 이 기본값을 변경하지 마세요.

가상 디바이스 드라이버와 같은 일부 프로그램에는 이러한 기본 스택 증가 메커니즘이 필요하지 않습니다. 이러한 경우 스택 프로브는 필요 하지 않으며, *크기* 를 지역 변수 저장소에 필요한 함수 보다 큰 값으로 설정 하 여 컴파일러에서이를 생성 하지 않도록 할 수 있습니다.

**/Gs0** 은 지역 변수를 저장 해야 하는 모든 함수 호출에 대 한 스택 프로브를 시작 합니다. 이는 성능을 저하시킬 수 있습니다.

X64 대상의 경우 **/gs** 옵션이 *크기* 인수 없이 지정 된 경우 **/gs0** 과 동일 합니다. *Size* 인수가 1에서 9 인 경우 경고 D9014을 내보내고 영향은 **/gs0** 을 지정 하는 것과 같습니다.

X86, ARM 및 ARM64 대상의 경우 *크기* 인수가 없는 **/Gs** 옵션은 **/gs4096** 과 동일 합니다. *Size* 인수가 1에서 9 인 경우 경고 D9014을 내보내고 영향은 **/Gs4096** 을 지정 하는 것과 같습니다.

모든 대상에 대해 10에서 2147485647 사이의 *크기* 인수는 지정 된 값에 대 한 임계값을 설정 합니다. 2147485648 이상의 *크기* 를 설정 하면 심각한 오류 C1049 발생 합니다.

[Check_stack](../../preprocessor/check-stack.md) 지시어를 사용 하 여 스택 프로브를 설정 하거나 해제할 수 있습니다. **/Gs** 및 `check_stack` Pragma는 표준 C 라이브러리 루틴에는 영향을 주지 않으며 컴파일하는 함수에만 영향을 줍니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 에서 **/gs** 컴파일러 옵션 및 선택적 크기를 입력 합니다. **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
