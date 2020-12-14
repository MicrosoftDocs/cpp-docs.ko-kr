---
description: '다음에 대 한 자세한 정보:/FU (강제 #using 파일 이름)'
title: '/FU(강제 #using 파일 이름 지정)'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
ms.openlocfilehash: 458369e7ff1322d2d2fa2fb37e8915c5a39c8446
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200379"
---
# <a name="fu-name-forced-using-file"></a>/FU(강제 #using 파일 이름 지정)

소스 코드에서 파일 이름을 [#using 지시문](../../preprocessor/hash-using-directive-cpp.md) 에 전달 하는 대신 사용할 수 있는 컴파일러 옵션입니다.

## <a name="syntax"></a>Syntax

> **/FU** *파일*

## <a name="arguments"></a>인수

*file*<br/>
이 컴파일에서 참조할 메타 데이터 파일을 지정 합니다.

## <a name="remarks"></a>설명

/FU 스위치는 파일 이름을 하나만 사용합니다. 여러 파일을 지정하려면 각 항목에 대해 /FU를 사용합니다.

C + +/CLI를 사용 하 고 있으며 [Friend 어셈블리](../../dotnet/friend-assemblies-cpp.md) 기능을 사용 하는 메타 데이터를 참조 하는 경우 **/fu** 를 사용할 수 없습니다. `#using` 특성과 함께 `[as friend]`을 사용해서 코드에서 메타데이터를 참조해야 합니다. Friend 어셈블리는 Visual C++ 구성 요소 확장 c + +/CX에서 지원 되지 않습니다.

CLR (공용 언어 런타임)에 대 한 어셈블리 또는 모듈을 만드는 방법에 대 한 자세한 내용은 [/clr (공용 언어 런타임 컴파일)](clr-common-language-runtime-compilation.md)을 참조 하세요. C + +/CX로 빌드하는 방법에 대 한 자세한 내용은 [앱 및 라이브러리 빌드](../../cppcx/building-apps-and-libraries-c-cx.md)를 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **고급** 속성 페이지를 선택 합니다.

1. **Force #using** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[출력 파일 (/F) 옵션](output-file-f-options.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
