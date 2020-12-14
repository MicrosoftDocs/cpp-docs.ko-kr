---
description: 자세한 정보:/EP (#line 지시문 없이 stdout으로 전처리)
title: /EP(#line 지시문 없이 stdout로 전처리)
ms.date: 11/04/2016
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
ms.openlocfilehash: cbd36cd6bdafe315a7a6ef01b46857725033bd69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201003"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP(#line 지시문 없이 stdout로 전처리)

C 및 c + + 소스 파일을 전처리 하 고 전처리 된 파일을 표준 출력 장치에 복사 합니다.

## <a name="syntax"></a>구문

```
/EP
```

## <a name="remarks"></a>설명

이 프로세스에서는 모든 전처리기 지시문이 수행 되 고 매크로 확장이 수행 되며 주석이 제거 됩니다. 전처리 된 출력에서 주석을 유지 하려면 **/ep** 를 사용 하 여 [/C (전처리 중에 주석 유지)](c-preserve-comments-during-preprocessing.md) 옵션을 사용 합니다.

**/Ep** 옵션은 컴파일을 표시 하지 않습니다. 컴파일을 위해 전처리 된 파일을 다시 전송 해야 합니다. **/Ep** 는 또한 **/fa**, **/fa** 및 **/fm** 옵션에서 출력 파일을 표시 하지 않습니다. 자세한 내용은 [/fa,/fa (목록 파일)](fa-fa-listing-file.md) 및 [/fm (맵 파일 이름)](fm-name-mapfile.md)을 참조 하세요.

이후 처리 단계에서 생성 된 오류는 원래 소스 파일이 아닌 전처리 된 파일의 줄 번호를 나타냅니다. 줄 번호가 원래 원본 파일을 참조 하도록 하려면 [/e (stdout으로 전처리)](e-preprocess-to-stdout.md) 를 대신 사용 합니다. **/E** 옵션은 `#line` 이 목적을 위해 출력에 지시문을 추가 합니다.

전처리 된 출력, `#line` 지시문을 파일에 보내려면 대신 [/P (파일에 대 한 전처리)](p-preprocess-to-a-file.md) 옵션을 사용 합니다.

지시문을 사용 하 여 전처리 된 출력을 stdout에 보내려면 `#line` **/P** 와 **/ep** 를 함께 사용 합니다.

미리 컴파일된 헤더는 **/ep** 옵션과 함께 사용할 수 없습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **전처리기** 속성 페이지를 클릭 합니다.

1. 전처리 된 **파일 생성** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>을 참조하세요.

## <a name="example"></a>예제

다음 명령줄은 파일을 전처리 하 `ADD.C` 고, 주석을 유지 하 고, 표준 출력 장치에 결과를 표시 합니다.

```
CL /EP /C ADD.C
```

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
