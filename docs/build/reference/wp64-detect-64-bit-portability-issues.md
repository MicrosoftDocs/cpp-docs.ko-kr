---
description: 자세히 알아보기:/Wp64 (64 비트 이식성 문제 검색)
title: /Wp64(64비트 이식성 문제 검색)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
ms.openlocfilehash: d1ee441089531c4ebe222c73f6cec16b59fa7583
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261088"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64(64비트 이식성 문제 검색)

이 컴파일러 옵션은 더 이상 사용되지 않습니다. Visual Studio 2013 이전 버전에서는 [__w64](../../cpp/w64.md) 키워드로도 표시된 형식에서 64비트 이식성 문제를 검색합니다.

## <a name="syntax"></a>구문

```
/Wp64
```

## <a name="remarks"></a>설명

기본적으로 Visual Studio 2013 하기 전에 Visual Studio 버전에서 **/Wp64** 컴파일러 옵션은 32 비트 x86 코드를 빌드하는 MSVC 컴파일러와 64 비트 x64 코드를 빌드하는 MSVC 컴파일러에서 해제 되어 있습니다.

> [!IMPORTANT]
> [/Wp64](wp64-detect-64-bit-portability-issues.md) 컴파일러 옵션 및 [__w64](../../cpp/w64.md) 키워드는 Visual Studio 2010 및 Visual Studio 2012에서 더 이상 사용되지 않으며 Visual Studio 2013부터는 지원되지 않습니다. 이 스위치를 사용하는 프로젝트를 변환하면 변환 중에 스위치가 마이그레이션되지 않습니다. Visual Studio 2010 또는 Visual Studio 2012에서 이 옵션을 사용하려면 프로젝트 속성의 **명령줄** 섹션에서 **추가 옵션** 아래에 컴파일러 스위치를 입력해야 합니다. 명령줄에서 **/Wp64** 컴파일러 옵션을 사용하면 컴파일러에서 명령줄 경고 D9002를 표시합니다. 64 비트 이식성 문제를 검색 하기 위해이 옵션과 키워드를 사용 하는 대신 64 비트 플랫폼을 대상으로 하는 MSVC 컴파일러를 사용 하 고 [/W4](compiler-option-warning-level.md) 옵션을 지정 합니다. 자세한 내용은 [64 비트, x64 대상에 대 한 c + + 프로젝트 구성을](../configuring-programs-for-64-bit-visual-cpp.md)참조 하세요.

다음 유형의 변수는 64비트 운영 체제에서 사용되는 것처럼 32비트 운영 체제에서 테스트됩니다.

- int

- long

- 포인터(pointer)

64 비트의 x64 코드를 작성 하는 컴파일러를 사용 하 여 응용 프로그램을 정기적으로 컴파일하는 경우 64 비트 컴파일러에서 모든 문제를 검색 하기 때문에 32 비트 컴파일에서 **/Wp64** 를 사용 하지 않도록 설정할 수 있습니다. Windows 64 비트 운영 체제를 대상으로 지정 하는 방법에 대 한 자세한 내용은 [64 비트, x64 대상에 대 한 c + + 프로젝트 구성](../configuring-programs-for-64-bit-visual-cpp.md)을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다.

   자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **/Wp64** 를 포함하도록 **추가 옵션** 상자의 내용을 수정합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[64비트, x64 대상에 대한 C++ 프로젝트 구성](../configuring-programs-for-64-bit-visual-cpp.md)
