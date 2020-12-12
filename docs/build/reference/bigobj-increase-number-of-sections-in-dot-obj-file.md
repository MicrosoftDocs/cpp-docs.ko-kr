---
description: 자세히 알아보기:/bigobj (의 섹션 수 늘리기 Obj 파일)
title: /bigobj(.Obj 파일의 섹션 수 늘리기)
ms.date: 03/26/2019
f1_keywords:
- /bigobj
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
ms.openlocfilehash: 4e820211ec46ad2a2d125552f95fb8a82c6f57ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182699"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj(.Obj 파일의 섹션 수 늘리기)

**/bigobj** 는 개체 파일에 포함 될 수 있는 섹션의 수를 늘립니다.

## <a name="syntax"></a>Syntax

> **/bigobj**

## <a name="remarks"></a>설명

기본적으로 개체 파일은 최대 65279 개 (거의 2 ^ 16)의 주소 지정 가능 섹션을 보유할 수 있습니다. 이 제한은 지정 된 대상 플랫폼에 관계 없이 적용 됩니다. **/bigobj** 는 해당 주소 용량을 4294967296 (2 ^ 32)로 늘립니다.

대부분의 모듈은 65279 개 이상의 섹션이 포함 된 .obj 파일을 생성 하지 않습니다. 그러나 컴퓨터에서 생성 된 코드 또는 템플릿 라이브러리를 많이 사용 하는 코드의 경우 더 많은 섹션을 보유할 수 있는 .obj 파일이 필요할 수 있습니다. **/bigobj** 는 컴퓨터 생성 XAML 코드에 많은 수의 헤더가 포함 되어 있으므로 UWP (유니버설 Windows 플랫폼) 프로젝트에서 기본적으로 사용 하도록 설정 되어 있습니다. UWP 앱 프로젝트에서이 옵션을 사용 하지 않도록 설정 하면 코드에서 컴파일러 오류 C1128 생성 될 수 있습니다.

PE-COFF 개체 파일 형식에 대 한 자세한 내용은 Windows 설명서의 [Pe 형식](/windows/win32/debug/pe-format) 을 참조 하십시오.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에 **/bigobj** 컴파일러 옵션을 입력 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
