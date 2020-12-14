---
description: '자세히 알아보기: `/Yu` (미리 컴파일된 헤더 파일 사용)'
title: /Yu(미리 컴파일된 헤더 파일 사용)
ms.date: 07/31/2020
f1_keywords:
- /Yu
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
ms.openlocfilehash: 7076a3a4dd9183a3a0072fa6211acbb0b95a4865
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229965"
---
# <a name="yu-use-precompiled-header-file"></a>`/Yu` (미리 컴파일된 헤더 파일 사용)

컴파일러가 현재 컴파일에서 기존의 미리 컴파일된 헤더 () 파일을 사용 하도록 지시 *`.pch`* 합니다.

## <a name="syntax"></a>Syntax

> **`/Yu`**\[*파일 이름*]

## <a name="arguments"></a>인수

*filename*<br/>
전처리기 지시문을 사용 하 여 소스 파일에 포함 된 헤더 파일의 이름입니다 `#include` .

## <a name="remarks"></a>설명

포함 파일의 이름은 **`/Yc`** 미리 컴파일된 헤더를 만드는 옵션과 **`/Yu`** 미리 컴파일된 헤더 사용을 나타내는 이후 옵션 모두에서 동일 해야 합니다.

의 **`/Yc`** 경우 *filename* 은 미리 컴파일을 중지 하는 지점을 지정 합니다. 컴파일러는 모든 코드를 *파일 이름* 으로 미리 컴파일하고 포함 파일의 기본 이름과의 확장명을 사용 하 여 결과 미리 컴파일된 헤더의 이름을 지정 합니다 *`.pch`* .

를 *`.pch`* 사용 하 여 파일을 만들어야 합니다 **`/Yc`** .

컴파일러는 .h 파일 이전에 발생 하는 모든 코드를 미리 컴파일된 것으로 처리 합니다. 이 `#include` 지시문은 파일에 연결 된 지시문 바로 다음에 *`.h`* 파일에 포함 된 코드를 사용 하 *`.pch`* 고 파일 *이름* 뒤에 모든 코드를 컴파일하는 것으로 건너뜁니다.

명령줄에서 **`/Yu`** 및 *파일 이름* 사이에는 공백이 허용 되지 않습니다.

파일 이름 없이 옵션을 지정 하는 경우 **`/Yu`** 소스 프로그램에는 [`#pragma hdrstop`](../../preprocessor/hdrstop.md) 미리 컴파일된 헤더 파일의 파일 이름을 지정 하는 pragma가 포함 되어 있어야 합니다 *`.pch`* . 이 경우 컴파일러는에 의해 이름이 지정 된 미리 컴파일된 헤더 (파일)를 사용 합니다 *`.pch`* [`/Fp (Name .pch file)`](fp-name-dot-pch-file.md) . 컴파일러가 해당 pragma의 위치로 건너뛰고 지정 된 미리 컴파일된 헤더 파일에서 컴파일된 상태를 복원 합니다. 그런 다음 pragma 다음에 오는 코드만 컴파일합니다. `#pragma hdrstop`에서 파일 이름을 지정 하지 않은 경우 컴파일러는 확장명이 인 소스 파일의 기본 이름에서 파생 된 이름을 사용 하 여 파일을 찾습니다 *`.pch`* . 옵션을 사용 하 여 **`/Fp`** 다른 파일을 지정할 수도 있습니다 *`.pch`* .

**`/Yu`** 파일 이름 없이 옵션을 지정 하 고 pragma를 지정 하지 않으면 `hdrstop` 오류 메시지가 생성 되 고 컴파일이 실패 합니다.

**`/Yc`**  **`/Yu`** 같은 명령줄에서 파일 이름 및 _파일_ 이름 옵션을 사용 하 고 둘 다 동일한 파일 이름을 참조 하는 경우 파일 이름에 우선 순위를 지정 하 여 명명 된 파일을 포함 하 여 **`/Yc`**  모든 코드를 미리 컴파일하는 것입니다. 이 기능은 메이크파일 작성을 간소화 합니다.

파일에는 *`.pch`* 컴퓨터 환경 및 프로그램에 대 한 메모리 주소 정보에 대 한 정보가 포함 되어 있으므로 파일을 만든 컴퓨터 에서만 파일을 사용 해야 합니다 *`.pch`* .

미리 컴파일된 헤더에 대 한 자세한 내용은 다음을 참조 하세요.

- [`/Y` (미리 컴파일된 헤더)](y-precompiled-headers.md)

- [미리 컴파일된 헤더 파일](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 .cpp 파일에 [ `/Yc` (미리 컴파일된 헤더 파일 만들기)](yc-create-precompiled-header-file.md) 를 지정 합니다.

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **미리 컴파일된 헤더** 속성 페이지를 선택 합니다.

1. **미리 컴파일된 헤더** 속성, **CREATE/Use PCH to File** 속성 또는 **Create/use 미리 컴파일된 헤더** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>를 확인합니다.

## <a name="example"></a>예제

다음 코드는 다음과 같습니다.

```cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
...
```

는 명령줄을 사용 하 여 컴파일되며 `CL /YuMYAPP.H PROG.CPP` 컴파일러는 세 개의 include 문을 처리 하지 않습니다. 대신에서 미리 컴파일된 코드를 사용 합니다 .이 코드는 *`MYAPP.pch`* 세 파일 (및 포함 될 수 있는 모든 파일)을 전처리 하는 데 소요 되는 시간을 절약 합니다.

[`/Fp (Name .pch file)`](fp-name-dot-pch-file.md)다음 예제와 같이 옵션을 옵션과 함께 사용 하 여 **`/Yu`** *`.pch`* 이름이 *filename* 인수 **`/Yc`** 또는 원본 파일의 기본 이름과 다른 경우 파일 이름을 지정할 수 있습니다.

```cmd
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP
```

이 명령은 이라는 미리 컴파일된 헤더 파일을 지정 합니다 *`MYPCH.pch`* . 컴파일러는 해당 콘텐츠를 사용 하 여 모든 헤더 파일의 미리 컴파일된 상태를까지 복원 *`MYAPP.h`* 합니다. 그런 다음 컴파일러는 * 지시문 후에 발생 하는 코드를 컴파일합니다 `#include "MYAPP.h"` .

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)
