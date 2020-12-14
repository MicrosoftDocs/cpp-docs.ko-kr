---
description: 자세한 정보:/F (스택 크기 설정)
title: /F(스택 크기 설정)
ms.date: 11/04/2016
f1_keywords:
- /f
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
ms.openlocfilehash: 5bf8b0855c65fc39caf8935b06a877c62a4e0df0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200782"
---
# <a name="f-set-stack-size"></a>/F(스택 크기 설정)

프로그램 스택 크기 (바이트)를 설정 합니다.

## <a name="syntax"></a>Syntax

> **/F** *번호*

## <a name="arguments"></a>인수

*number*<br/>
스택 크기 (바이트)입니다.

## <a name="remarks"></a>설명

이 옵션을 사용 하지 않으면 스택 크기의 기본값은 1mb입니다. *Number* 인수는 Decimal 또는 C 언어 표기법으로 지정할 수 있습니다. 인수는 1에서 링커가 허용 하는 최대 스택 크기의 범위를 지정할 수 있습니다. 링커에서는 지정 된 값을 가장 가까운 4 바이트로 반올림 합니다. **/F** 와 *number* 사이의 공백은 선택 사항입니다.

프로그램에서 스택 오버플로 메시지를 가져오는 경우 스택 크기를 늘려야 할 수 있습니다.

다음을 기준으로 스택 크기를 설정할 수도 있습니다.

- **/STACK** 링커 옵션을 사용 합니다. 자세한 내용은 [/STACK](stack.md)를 참조 하세요.

- .Exe 파일에 EDITBIN을 사용 합니다. 자세한 내용은 [EDITBIN Reference](editbin-reference.md)를 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
