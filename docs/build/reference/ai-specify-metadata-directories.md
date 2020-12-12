---
description: 자세한 정보:/AI (메타 데이터 디렉터리 지정)
title: /AI(메타데이터 디렉터리 지정)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.AdditionalUsingDirectories
- VC.Project.VCNMakeTool.AssemblySearchPath
- /AI
- VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories
helpviewer_keywords:
- /AI compiler option [C++]
- AI compiler option [C++]
- -AI compiler option [C++]
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
ms.openlocfilehash: e30711b1da2d41204bf56520d56dd5101f3168b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179748"
---
# <a name="ai-specify-metadata-directories"></a>/AI(메타데이터 디렉터리 지정)

`#using` 지시문에 전달된 파일 참조를 확인하기 위해 컴파일러가 검색할 디렉터리를 지정합니다.

## <a name="syntax"></a>Syntax

> **/Ai**_디렉터리_

## <a name="arguments"></a>인수

*디렉터리나*<br/>
검색할 컴파일러의 디렉터리나 경로

## <a name="remarks"></a>설명

하나의 디렉터리만 **/ai** 호출에 전달할 수 있습니다. 컴파일러가 검색할 각 경로에 대해 하나의 **/ai** 옵션을 지정 합니다. 예를 들어 지시문의 컴파일러 검색 경로에 C:\Project\Meta 및 C:\Common\Meta를 둘 다 추가 하려면 `#using` `/AI"C:\Project\Meta" /AI"C:\Common\Meta"` 컴파일러 명령줄에를 추가 하거나 Visual Studio의 **추가 #using 디렉터리** 속성에 각 디렉터리를 추가 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** > **C/C++**  > **일반** 속성 페이지를 선택합니다.

1. **추가 #using 디렉터리** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[#using 지시문](../../preprocessor/hash-using-directive-cpp.md)
