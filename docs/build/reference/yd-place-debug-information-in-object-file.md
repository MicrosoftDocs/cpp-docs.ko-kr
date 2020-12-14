---
description: 자세한 정보:/Yd (개체 파일에 디버그 정보 삽입)
title: /Yd(개체 파일에 디버그 정보 삽입)
ms.date: 11/04/2016
f1_keywords:
- /yd
helpviewer_keywords:
- /Yd compiler option [C++]
- -Yd compiler option [C++]
- debugging [C++], debug information files
- Yd compiler option [C++]
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
ms.openlocfilehash: 7716d5ca1893faefac9186f97e2f7439a3887343
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243590"
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd(개체 파일에 디버그 정보 삽입)

[/Yc](yc-create-precompiled-header-file.md) 및 [/z7](z7-zi-zi-debug-information-format.md) 옵션과 함께 사용 하는 경우 미리 컴파일된 헤더 (.pch) 파일에서 생성 된 모든 개체 파일의 전체 디버깅 정보를 속도로 합니다. 더 이상 사용되지 않습니다.

## <a name="syntax"></a>구문

```
/Yd
```

## <a name="remarks"></a>설명

**/Yd** 는 사용 되지 않습니다. 이제 Visual C++는 단일 .pdb 파일에 쓰는 여러 개체를 지원 합니다. 대신 **/zi** 를 사용 합니다. 사용 되지 않는 컴파일러 옵션의 목록은 [컴파일러 옵션 범주별](compiler-options-listed-by-category.md)목록에서 **사용 되지 않는 컴파일러 옵션** 을 참조 하세요.

디버깅 정보를 포함 하는 라이브러리를 배포 해야 하는 경우가 아니면 **/Z7** 및 **/yd** 대신 [/zi](z7-zi-zi-debug-information-format.md) 옵션을 사용 합니다.

모든 .obj 파일에 전체 디버깅 정보를 저장 하는 것은 디버깅 정보를 포함 하는 라이브러리를 배포 하는 경우에만 필요 합니다. 컴파일 속도가 느려지고 상당한 디스크 공간이 필요 합니다. **/Yc** 와 **/Z7** 이 **/yd** 없이 사용 되 면 컴파일러는 .pch 파일에서 만든 첫 번째 .obj 파일에 일반적인 디버깅 정보를 저장 합니다. 컴파일러는 나중에 .pch 파일에서 만든 .obj 파일에이 정보를 삽입 하지 않습니다. 정보에 대 한 상호 참조를 삽입 합니다. .Pch 파일을 사용 하는 .obj 파일의 수에 관계 없이 하나의 .obj 파일만 일반적인 디버깅 정보를 포함 합니다.

이러한 기본 동작으로 인해 빌드 시간이 단축 되 고 디스크 공간 요구 사항이 감소 하지만, 작은 변경으로 인해 일반적인 디버깅 정보가 포함 된 .obj 파일을 다시 빌드해야 하는 경우에는 바람직하지 않습니다. 이 경우 컴파일러는 원본 .obj 파일에 대 한 상호 참조를 포함 하는 모든 .obj 파일을 다시 작성 해야 합니다. 또한 다른 프로젝트에서 일반적인 .pch 파일을 사용 하는 경우 단일 .obj 파일에 대 한 상호 참조를 사용 하는 것은 어렵습니다.

미리 컴파일된 헤더에 대 한 자세한 내용은 다음을 참조 하세요.

- [/Y (미리 컴파일된 헤더)](y-precompiled-headers.md)

- [미리 컴파일된 헤더 파일](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="examples"></a>예제

각각 다음과 같은 **#include** 문을 포함 하는 두 개의 기본 파일인 F .Cpp와 G .cpp가 있다고 가정 합니다.

```
#include "windows.h"
#include "etc.h"
```

다음 명령은 미리 컴파일된 헤더 파일 (.pch) 및 개체 파일 F. .obj를 만듭니다.

```
CL /YcETC.H /Z7 F.CPP
```

개체 파일의 파일에는 WINDOWS .h 및 기타 .h와 기타 헤더 파일에 대 한 형식 및 기호 정보가 포함 되어 있습니다. 이제 미리 컴파일된 헤더 (.pch)를 사용 하 여 소스 파일을 컴파일할 수 있습니다.

```
CL /YuETC.H /Z7 G.CPP
```

개체 파일 G. .obj는 미리 컴파일된 헤더에 대 한 디버깅 정보를 포함 하지 않지만 F .obj 파일에서 해당 정보를 참조 합니다. 여기서는 F .obj 파일과 연결 해야 합니다.

미리 컴파일된 헤더를 **/z7** 로 컴파일하지 않은 경우에도 **/z7** 을 사용 하 여 나중 컴파일에서 해당 헤더를 사용할 수 있습니다. 그러나 디버깅 정보는 현재 개체 파일에 배치 되 고 미리 컴파일된 헤더에 정의 된 함수 및 형식에 대 한 로컬 기호는 디버거에 사용할 수 없습니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
