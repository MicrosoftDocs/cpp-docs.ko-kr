---
description: 자세히 알아보기:/doc (문서 주석 처리) (C/c + +)
title: /doc(문서 주석 처리)(C/C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
ms.openlocfilehash: ed811edff544c4b5b28baa67ed216fa09ea51092
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192878"
---
# <a name="doc-process-documentation-comments-cc"></a>/doc(문서 주석 처리)(C/C++)

컴파일러가 소스 코드 파일의 문서 주석을 처리 하 고 문서 주석을 포함 하는 각 소스 코드 파일에 대해 .xdc 파일을 만들도록 합니다.

## <a name="syntax"></a>Syntax

> **/doc**[*name*]

## <a name="arguments"></a>인수

*name*<br/>
컴파일러가 만들 .xdc 파일의 이름입니다. 단일 .cpp 파일이 컴파일에서 전달 되는 경우에만 유효 합니다.

## <a name="remarks"></a>설명

.Xdc 파일은 xdcmake.exe를 사용 하 여 .xml 파일로 처리 됩니다. 자세한 내용은 [XDCMake Reference](xdcmake-reference.md)를 참조 하세요.

소스 코드 파일에 문서 주석을 추가할 수 있습니다. 자세한 내용은 [문서 주석에 대한 권장 태그](recommended-tags-for-documentation-comments-visual-cpp.md)를 참조하세요.

IntelliSense에서 생성 된 .xml 파일을 사용 하려면 .xml 파일의 파일 이름을 지원 하려는 어셈블리와 동일 하 게 설정 하 고 .xml 파일이 어셈블리와 동일한 디렉터리에 배치 합니다. Visual Studio 프로젝트에서 어셈블리를 참조 하는 경우 .xml 파일도 찾을 수 있습니다. 자세한 내용은 [IntelliSense 사용](/visualstudio/ide/using-intellisense) 및 [XML 코드 주석 제공](/visualstudio/ide/supplying-xml-code-comments)을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **출력 파일** 속성 페이지를 선택 합니다.

1. **XML 문서 파일 생성** 속성을 수정 합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
