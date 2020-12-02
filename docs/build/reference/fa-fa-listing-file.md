---
title: /FA, /Fa(목록 파일)
description: Microsoft c + +/FA 및/Fa (목록 파일) 컴파일러 옵션에 대 한 참조 가이드입니다.
ms.date: 11/21/2020
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.openlocfilehash: 7e8e39fea55bb69eaa0ae914eeabcafef4ac7849
ms.sourcegitcommit: 432c24dde31c400437c4320e8432b1ddb232f844
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440240"
---
# <a name="fa-fa-listing-file"></a>`/FA`, `/Fa` (목록 파일)

어셈블러 코드를 포함 하는 목록 파일을 만듭니다.

## <a name="syntax"></a>구문

> **`/FA`**[**`c`**\][**`s`**\][**`u`**]\
> **`/Fa`**_아니라_

## <a name="remarks"></a>설명

**`/FA`** 컴파일러 옵션은 일반적으로 C 또는 c + + 소스 파일에 해당 하는 컴파일의 각 변환 단위에 대 한 어셈블러 목록 파일을 생성 합니다. 기본적으로는 어셈블러만 ANSI로 인코딩된 목록 파일에 포함 되어 있습니다. **`c`** **`s`** **`u`** **`/FA`** 컴퓨터 코드 또는 소스 코드가 어셈블러 목록과 함께 출력 되는지 여부와 목록이 u t f-8로 인코딩 되는지 여부를 제어 하는 선택적, 및 인수입니다.

기본적으로 각 목록 파일은 소스 파일과 동일한 기본 이름을 가져오며 확장명을 갖습니다 *`.asm`* . 옵션을 사용 하 여 컴퓨터 코드를 포함 하는 경우 **`c`** 목록 파일에는 *`.cod`* 확장명이 있습니다. 옵션을 사용 하 여 목록 파일 및 해당 파일을 만든 디렉터리의 이름과 확장명을 변경할 수 있습니다 **`/Fa`** .

### <a name="fa-arguments"></a>`/FA` 인수

없음을
어셈블러 언어만 목록에 포함 됩니다.

**`c`**\
선택 사항입니다. 목록에 시스템 코드를 포함 합니다.

**`s`**\
선택 사항입니다. 목록에 소스 코드를 포함 합니다.

**`u`**\
선택 사항입니다. 목록 파일을 UTF-8 형식으로 인코딩하고 바이트 순서 표식을 포함 합니다. 기본적으로이 파일은 ANSI로 인코딩됩니다. **`u`** 를 사용 하 여 시스템에 올바르게 표시 되는 목록 파일을 만들거나 유니코드 소스 코드 파일을 컴파일러에 대 한 입력으로 사용 하는 경우를 사용 합니다.

및를 **`s`** 모두 **`u`** 지정 하 고 소스 코드 파일에서 u t f-8이 아닌 유니코드 인코딩을 사용 하는 경우 파일의 코드 줄이 *`.asm`* 올바르게 표시 되지 않을 수 있습니다.

### <a name="fa-argument"></a>`/Fa` 인수

없음을
컴파일의 각 소스 코드 파일에 대해 하나의 *소스 .asm* 파일이 생성 됩니다.

*이름도*\
컴파일러는 현재 디렉터리에 *이름이 filename*.asm 인 목록 파일을 배치 합니다. 이 인수 형식은 단일 소스 코드 파일을 컴파일하는 경우에만 유효 합니다.

*파일 이름. 확장명*\
컴파일러는 현재 디렉터리에 *filename 확장명* 이라는 목록 파일을 배치 합니다. 이 인수 형식은 단일 소스 코드 파일을 컴파일하는 경우에만 유효 합니다.

*디렉터리나*__\\__\
컴파일러는 컴파일의 각 소스 코드 파일에 대해 하나의 *source_file .asm* 파일을 만듭니다. 지정 된 *디렉터리* 에 배치 됩니다. 후행 백슬래시가 필요 합니다. 현재 디스크의 경로만 허용 됩니다.

*디렉터리* __\\__ *파일 이름*\
*Filename* 파일 이름이 지정 된 *디렉터리* 에 배치 됩니다. 이 인수 형식은 단일 소스 코드 파일을 컴파일하는 경우에만 유효 합니다.

*디렉터리* __\\__ *파일 이름. 확장명*\
파일 *이름 확장명이 확장명이* 지정 된 *디렉터리* 에 배치 됩니다. 이 인수 형식은 단일 소스 코드 파일을 컴파일하는 경우에만 유효 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **출력 파일** 속성 페이지를 선택 합니다.

1. 어셈블러 **출력** 속성을 수정 하 여 어셈블러, 컴퓨터 및 소스 코드에 대 한 **/FAc** 및 **/FAs** 옵션을 설정 합니다. **어셈블러 목록에 유니코드 사용** 속성을 수정 하 여 **`/FAu`** ANSI 또는 utf-8 출력에 대 한 옵션을 설정 합니다. **ASM 목록 위치** 를 수정 하 여 **`/Fa`** 파일 이름 및 위치를 나열 하는 옵션을 설정 합니다.

어셈블러 **출력** 을 설정 하 고 **어셈블러에 유니코드를 사용** 하는 경우 [명령줄 경고 D9025](../../error-messages/tool-errors/command-line-warning-d9025.md)이 발생할 수 있습니다. IDE에서 이러한 옵션을 결합 하려면 대신 **명령줄** 속성 페이지에서 **추가 옵션** 필드를 사용 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> 또는 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>을 참조하십시오. **/FAu** 를 지정 하려면을 참조 하십시오 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> .

## <a name="example"></a>예제

다음 명령줄은 라는 결합 된 소스와 기계어 코드 목록을 생성 합니다 *`HELLO.cod`* .

```cmd
CL /FAcs HELLO.CPP
```

## <a name="see-also"></a>참고 항목

[출력 파일 (/F) 옵션](output-file-f-options.md)\
[MSVC 컴파일러 옵션](compiler-options.md)\
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)\
[경로 이름 지정](specifying-the-pathname.md)
