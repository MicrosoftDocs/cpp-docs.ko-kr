---
description: 다음에 대 한 자세한 정보:/I (추가 포함 디렉터리)
title: /I(추가 포함 디렉터리)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
ms.openlocfilehash: ad44abec28bbb87f91f449765a9ea2f30f2bffa8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191344"
---
# <a name="i-additional-include-directories"></a>/I(추가 포함 디렉터리)

포함 파일을 검색 하는 디렉터리 목록에 디렉터리를 추가 합니다.

## <a name="syntax"></a>Syntax

> **/I**[]*디렉터리*

### <a name="arguments"></a>인수

*디렉터리나*<br/>
포함 파일을 검색할 디렉터리 목록에 추가할 디렉터리입니다.

## <a name="remarks"></a>설명

둘 이상의 디렉터리를 추가 하려면이 옵션을 두 번 이상 사용 합니다. 지정 된 포함 파일을 찾을 때 까지만 디렉터리가 검색 됩니다.

이 옵션은 ([/x (표준 포함 경로 무시)](x-ignore-standard-include-paths.md)) 옵션과 함께 사용할 수 있습니다.

컴파일러는 다음 순서로 디렉터리를 검색 합니다.

1. 큰따옴표 형식의 [#include 지시어](../../preprocessor/hash-include-directive-c-cpp.md) 를 사용 하 여 지정 하는 경우 먼저 로컬 디렉터리를 검색 합니다. 검색은 **#include** 문이 포함 된 파일과 동일한 디렉터리에서 시작 됩니다. 이로 인해 파일이 검색 되지 않으면 현재 열려 있는 포함 파일의 디렉터리를 검색 하는 역순으로 검색 합니다. 검색은 부모 include 파일의 디렉터리에서 시작하여 위쪽의 상위 부모 include 파일 디렉터리로 진행됩니다.

1. 꺾쇠 괄호 형식으로 **#include** 지시어를 사용 하 여 지정 하거나 로컬 디렉터리 검색에 실패 한 경우 **/i** 옵션을 사용 하 여 지정 된 디렉터리를 검색 하는 순서 대로 CL은 명령줄에서 해당 디렉터리를 검색 합니다.

1. **INCLUDE** 환경 변수에 지정 된 디렉터리입니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** > **C/C++**  > **일반** 속성 페이지를 선택합니다.

1. **추가 포함 디렉터리** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>을 참조하세요.

## <a name="example"></a>예제

다음 명령은 MAIN에서 요청한 포함 파일을 다음 순서로 검색 합니다. 첫 번째는 큰따옴표를 사용 하 여 지정 하면 로컬 파일이 검색 됩니다. 다음으로, \INCLUDE 디렉터리에서 검색을 계속 하 고, \MY\INCLUDE 디렉터리에서 마지막으로 INCLUDE 환경 변수에 할당 된 디렉터리를 검색 합니다.

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
