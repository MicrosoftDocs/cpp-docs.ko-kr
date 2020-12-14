---
description: 자세히 알아보기:/Yc (미리 컴파일된 헤더 파일 만들기)
title: /Yc(미리 컴파일된 헤더 파일 만들기)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
ms.openlocfilehash: eba045c3148d0caceee3ca6f9d5352ea61726757
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243652"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc(미리 컴파일된 헤더 파일 만들기)

특정 지점에서 컴파일 상태를 나타내는 미리 컴파일된 헤더 (.pch) 파일을 만들도록 컴파일러에 지시 합니다.

## <a name="syntax"></a>Syntax

> __/Yc__\
> __/Yc__*파일 이름*

## <a name="arguments"></a>인수

*filename*<br/>
헤더 파일 (.h)을 지정 합니다. 이 인수를 사용 하는 경우 컴파일러는 .h 파일을 포함 하 여 모든 코드를 컴파일합니다.

## <a name="remarks"></a>설명

**/Yc** 가 인수 없이 지정 된 경우 컴파일러는 모든 코드를 기본 소스 파일의 끝까지 또는 [hdrstop](../../preprocessor/hdrstop.md) 지시문이 발생 하는 기본 파일의 지점까지 컴파일합니다. **Hdrstop** pragma 또는 **/fp** 옵션을 사용 하 여 다른 파일 이름을 지정 하지 않는 한, 결과 .pch 파일은 기본 소스 파일과 동일한 기본 이름을 갖습니다.

미리 컴파일된 코드는 **/yc** 옵션과 .pch 확장명을 사용 하 여 지정 된 파일의 기본 이름에서 만든 이름으로 파일에 저장 됩니다. 또한 [/fp (Name)를 사용할 수 있습니다. Pch 파일)](fp-name-dot-pch-file.md) 옵션을 선택 하 여 미리 컴파일된 헤더 파일의 이름을 지정할 수 있습니다.

__/Yc__*filename* 을 사용 하는 경우 컴파일러는 나중에 [/Yu (미리 컴파일된 헤더 파일 사용)](yu-use-precompiled-header-file.md) 옵션을 사용 하기 위해 지정 된 파일을 포함 하 여 모든 코드를 컴파일합니다.

동일한 명령줄에서 __/yc__*filename* 및 __/yu__*filename* 옵션을 사용 하는 경우 동일한 파일 이름 및 __/yc__*filename* 이 우선 합니다. 이 기능은 메이크파일 작성을 간소화 합니다.

미리 컴파일된 헤더에 대 한 자세한 내용은 다음을 참조 하세요.

- [/Y (미리 컴파일된 헤더)](y-precompiled-headers.md)

- [미리 컴파일된 헤더 파일](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. .Cpp 파일을 선택 합니다. .Cpp 파일은 미리 컴파일된 헤더 정보를 포함 하는 .h 파일을 #include 해야 합니다. 프로젝트의 **/yc** 설정은 파일 수준에서 재정의할 수 있습니다.

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**, **C/c + +**, **미리 컴파일된 헤더** 속성 페이지를 엽니다.

1. **미리 컴파일된 헤더** 속성을 수정 합니다.

1. 파일 이름을 설정 하려면 **미리 컴파일된 헤더 파일** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>를 확인합니다.

## <a name="example"></a>예제

다음 코드를 생각해 봅시다.

```cpp
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
// ...
```

명령을 사용 하 여이 코드를 컴파일하면 `CL /YcMYAPP.H PROG.CPP` 컴파일러가 afxwin.h, resource.h 및 myapp에 대 한 모든 전처리를 myapp 라는 미리 컴파일된 헤더 파일에 저장 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)<br/>
[미리 컴파일된 헤더 파일](../creating-precompiled-header-files.md)
