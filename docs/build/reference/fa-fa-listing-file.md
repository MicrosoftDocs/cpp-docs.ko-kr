---
title: /FA, /Fa(목록 파일)
ms.date: 11/04/2016
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
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
ms.openlocfilehash: 6bb5e18c5a174c9e48b253031daad195e6132375
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507304"
---
# <a name="fa-fa-listing-file"></a>/FA, /Fa(목록 파일)

어셈블러 코드가 포함 된 목록 파일을 만듭니다.

## <a name="syntax"></a>구문

> **/FA**[**c**\][**s**\][**u**] **/Fa**_경로 이름_

## <a name="remarks"></a>설명

합니다 **/FA** 컴파일러 옵션 컴파일할 때 일반적으로 C 또는 c + + 소스 파일에 해당 하는 각 변환 단위에 대 한 어셈블러 목록 파일을 생성 합니다. 기본적으로 어셈블러 ANSI로 인코딩 되는 목록 파일에 포함 되어 있습니다. 선택적 **c**를 **s**, 및 **u** 인수 **/FA** 여부 기계어 코드를 제어 하거나 소스 코드는 어셈블러와 함께 출력 목록은 목록 u t F-8로 인코딩 되는 여부 및 합니다.

기본적으로 각 목록 파일 소스 파일과 동일한 기본 이름을 가져오고.asm 확장명이 합니다. 기계어 코드를 사용 하 여 포함 된 경우는 **c** .cod 확장명이 옵션을 나열 합니다. 이름 및 확장명이 목록 파일 및 디렉터리를 사용 하 여 만들어지는 위치를 변경할 수 있습니다 합니다 **/Fa** 옵션입니다.

### <a name="fa-arguments"></a>/FA 인수

없음<br/>
어셈블러 언어만 목록에 포함 됩니다.

**c**<br/>
선택 사항입니다. 목록에서 컴퓨터 코드를 포함합니다.

**s**<br/>
선택 사항입니다. 목록에서 소스 코드를 포함합니다.

**u**<br/>
선택 사항입니다. 목록 파일에 utf-8 형식으로 인코딩하고 바이트 순서 마커를 포함 합니다. 기본적으로 파일 ANSI로 인코딩됩니다. 사용 하 여 `u` 모든 시스템에 올바르게 표시 하는 한 목록 파일을 만들려면 컴파일러에 대 한 입력으로 유니코드를 사용 하는 경우 또는 소스 코드 파일.

둘 다 **s** 하 고 **u** 를 지정 하 고 소스 코드 파일 경우 u t F-8을.asm 파일에 코드 줄을 올바르게 표시 되지 않을 이외의 유니코드 인코딩을 사용 합니다.

### <a name="fa-argument"></a>/Fa 인수

없음<br/>
하나의 *원본*.asm 파일을 컴파일할 때 각 소스 코드 파일에 대 한 만들어집니다.

*filename*<br/>
목록 파일인 *filename*.asm은 현재 디렉터리에 배치 합니다. 이 단일 소스 코드 파일을 컴파일할 때에 유효 합니다.

*filename.extension*<br/>
목록 파일인 *filename.extension* 현재 디렉터리에 배치 됩니다. 이 단일 소스 코드 파일을 컴파일할 때에 유효 합니다.

*디렉터리*__\\__<br/>
하나의 *source_file*.asm 파일을 만들고 지정 된 배치 *directory* 컴파일할 때 각 소스 코드 파일에 대 한 합니다. 필요한 후행 백슬래시를 note 합니다. 현재 디스크에 대 한 경로만 허용 됩니다.

*디렉터리*__\\__*파일 이름*<br/>
목록 파일 이름이 *filename*.asm 위치한 지정 된 *디렉터리*합니다. 이 단일 소스 코드 파일을 컴파일할 때에 유효 합니다.

*디렉터리*__\\__*filename.extension*<br/>
목록 파일 이름이 *filename.extension* 위치한 지정 된 *directory*합니다. 이 단일 소스 코드 파일을 컴파일할 때에 유효 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. 선택 된 **구성 속성** > **C/c + +** > **출력 파일** 속성 페이지.

1. 수정 합니다 **어셈블러 출력** 속성을 설정 합니다 **/FAc** 및 **/FAs** assembler, 컴퓨터 및 소스 코드에 대 한 옵션입니다. 수정 합니다 **어셈블러 목록에 대 한 사용 하 여 유니코드** 속성을 설정 합니다 **하려면 /FAu** ANSI 또는 u t F-8 출력에 대 한 옵션입니다. 수정 합니다 **ASM 목록 위치** 설정 하는 **/Fa** 파일 이름과 위치를 나열 하기 위한 옵션입니다.

모두 설정 **어셈블러 출력** 하 고 **어셈블러 목록에 대 한 사용 하 여 유니코드** 속성에서 발생할 수 있습니다 [명령줄 경고 D9025](../../error-messages/tool-errors/command-line-warning-d9025.md)합니다. IDE에서 이러한 옵션을 결합 하려면 사용 합니다 **추가 옵션** 필드에 **명령줄** 속성 페이지 대신 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> 또는 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>을 참조하십시오. 지정할 **하려면 /FAu**를 참조 하세요 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>합니다.

## <a name="example"></a>예제

다음 명령줄을 결합 된 소스를 생성 하 고 기계어 코드로 hello.cod:

```cmd
CL /FAcs HELLO.CPP
```

## <a name="see-also"></a>참고 항목

[출력 파일(/F) 옵션](../../build/reference/output-file-f-options.md)<br/>
[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)<br/>
[경로 이름 지정](../../build/reference/specifying-the-pathname.md)
