---
description: 자세히 알아보기:/nologo (시작 배너 표시 안 함) (C/c + +)
title: /nologo(시작 배너 표시 안 함)(C/C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.SuppressStartupBanner
- VC.Project.VCCLCompilerTool.SuppressStartupBanner
helpviewer_keywords:
- -nologo compiler option [C++]
- /nologo compiler option [C++]
- nologo compiler option [C++]
- banners, suppressing startup
ms.assetid: 75930d8b-b11c-4db8-99e5-b52f97da0693
ms.openlocfilehash: a924eaf18a772b9495e1a493855fd72e9b79dd83
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196609"
---
# <a name="nologo-suppress-startup-banner-cc"></a>/nologo(시작 배너 표시 안 함)(C/C++)

컴파일러가 시작 될 때 저작권 배너를 표시 하지 않으며 컴파일하는 동안 정보 메시지를 표시 합니다.

## <a name="syntax"></a>구문

```
/nologo
```

## <a name="remarks"></a>설명

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **일반** 속성 페이지를 클릭 합니다.

1. **시작 배너 표시 안 함** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SuppressStartupBanner%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
