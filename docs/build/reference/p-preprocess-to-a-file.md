---
description: 자세한 정보:/P (파일로 전처리)
title: /P(파일 전처리)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
ms.openlocfilehash: 20bca03694c866baa0575445271fc4f587268096
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226196"
---
# <a name="p-preprocess-to-a-file"></a>/P(파일 전처리)

C 및 c + + 소스 파일을 전처리 하 고 전처리 된 출력을 파일에 씁니다.

## <a name="syntax"></a>구문

```
/P
```

## <a name="remarks"></a>설명

이 파일의 기본 이름은 소스 파일과 같으며 확장명이입니다. 이 프로세스에서는 모든 전처리기 지시문이 수행 되 고 매크로 확장이 수행 되며 주석이 제거 됩니다. 전처리 된 출력에서 주석을 유지 하려면 **/p** 와 함께 [/C (전처리 중에 주석 유지)](c-preserve-comments-during-preprocessing.md) 옵션을 사용 합니다.

**/P** `#line` 는 포함 된 각 파일의 시작과 끝에 및 조건부 컴파일의 전처리기 지시문에 의해 제거 되는 줄에 지시문을 출력에 추가 합니다. 이러한 지시문은 전처리 된 파일의 줄 번호를 다시 매깁니다. 따라서 이후 처리 단계 중에 생성 된 오류는 전처리 된 파일의 줄이 아니라 원래 소스 파일의 줄 번호를 나타냅니다. 지시문을 생성 하지 않으려면 `#line` [/ep (#line 지시문 없이 Stdout으로 전처리)](ep-preprocess-to-stdout-without-hash-line-directives.md) 및 **/p** 를 사용 합니다.

**/P** 옵션은 컴파일을 표시 하지 않습니다. [/Fo (개체 파일 이름)](fo-object-file-name.md)를 사용 하더라도 .obj 파일은 생성 되지 않습니다. 컴파일을 위해 전처리 된 파일을 다시 전송 해야 합니다. **/P** 는 또한 **/fa**, **/fa** 및 **/fm** 옵션에서 출력 파일을 표시 하지 않습니다. 자세한 내용은 [/fa,/fa (목록 파일)](fa-fa-listing-file.md) 및 [/fm (맵 파일 이름)](fm-name-mapfile.md)을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **전처리기** 속성 페이지를 클릭 합니다.

1. 전처리 된 **파일 생성** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>을 참조하세요.

## <a name="example"></a>예제

다음 명령줄은 전처리 하 고, `ADD.C` 주석을 유지 하 `#line` 고, 지시문을 추가 하 고, 결과를 파일에 씁니다 `ADD.I` .

```
CL /P /C ADD.C
```

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[/Fi (출력 파일 이름 전처리)](fi-preprocess-output-file-name.md)
