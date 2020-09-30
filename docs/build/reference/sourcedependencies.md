---
title: /sourceDependencies (소스 레벨 종속성 보고)
description: Microsoft c + +의/sourceDependencies 컴파일러 옵션에 대 한 참조 가이드입니다.
ms.date: 07/29/2020
f1_keywords:
- /sourceDependencies
helpviewer_keywords:
- /sourceDependencies compiler option
- /sourceDependencies
ms.openlocfilehash: 0c1866812435c777f6f1fd7ed7f9db788a8cf031
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502842"
---
# <a name="sourcedependencies-report-source-level-dependencies"></a>`/sourceDependencies` (보고서 원본 수준 종속성)

컴파일하는 동안 사용 된 소스 수준 종속성을 자세히 설명 하는 JSON 파일을 생성 하도록 컴파일러에 지시 합니다.

JSON 파일에는 다음을 포함 하는 소스 종속성 목록이 포함 되어 있습니다.

- 헤더 파일 (전이적이 고 직접 포함 된 헤더).
- 사용 되는 PCH **`/Yu`** 입니다 (가 지정 된 경우).
- 가져온 모듈 및 가져온 헤더 단위 (전이적이 고 직접 가져온 모듈/헤더 단위).

## <a name="syntax"></a>구문

> **`/sourceDependencies`***파일 이름*\
> **`/sourceDependencies`***디렉터리*

## <a name="arguments"></a>인수

*이름도*\
컴파일러는 지정 된 파일 이름에 상대 또는 절대 경로를 포함할 수 있는 소스 종속성 출력을 씁니다.

*디렉터리나*\
인수가 디렉터리인 경우 컴파일러는 지정 된 디렉터리에 소스 종속성 파일을 생성 합니다. 출력 파일 이름은 입력 파일의 전체 이름을 기반으로 하며 추가 된 확장명을 사용 합니다 *`.json`* . 예를 들어, 컴파일러에 제공 된 파일이 인 경우 *`main.cpp`* 생성 된 출력 파일 이름은 *`main.cpp.json`* 입니다.

## <a name="remarks"></a>설명

**`/sourceDependencies`** 컴파일러 옵션은 Visual Studio 2019 버전 16.7부터 사용할 수 있습니다. 기본적으로 사용 하도록 설정 되어 있지 않습니다.

컴파일러 옵션을 지정 하는 경우 **`/MP`** 디렉터리 인수와 함께를 사용 하는 것이 좋습니다 **`/sourceDependencies`** . 단일 파일 이름 인수를 제공 하는 경우 컴파일러의 두 인스턴스는 출력 파일을 동시에 열려고 시도 하 여 오류를 발생 시킬 수 있습니다. 에 대 한 자세한 내용은 **`/MP`** [ `/MP` (여러 프로세스로 빌드)](mp-build-with-multiple-processes.md)를 참조 하세요.

심각 하지 않은 컴파일러 오류가 발생 하는 경우 종속성 정보는 여전히 출력 파일에 기록 됩니다.

모든 파일 경로는 출력에서 절대 경로로 표시 됩니다.

### <a name="examples"></a>예

다음 샘플 코드를 제공 합니다.

```cpp
// main.cpp
#include "header.h"
import m;
import "other.h";

int main() { }
```

**`/sourceDependencies`** 나머지 컴파일러 옵션과 함께를 사용할 수 있습니다.

> `cl ... /sourceDependencies output.json ... main.cpp`

여기서는 `...` 다른 컴파일러 옵션을 나타냅니다. 이 명령줄은 *`output.json`* 다음과 같은 내용이 포함 된 JSON 파일을 생성 합니다.

```JSON
{
    "Version": "1.0",
    "Data": {
        "Source": "C:\\...\\main.cpp",
        "PCH": "C:\\...\\pch.pch",
        "Includes": [
            "C:\\...\\header.h"
        ],
        "Modules": [
            "C:\\...\\m.ifc",
            "C:\\...\\other.h.ifc"
        ]
    }
}
```

`...`보고 된 경로의 약어를 사용 하 여 보고서에 절대 경로가 포함 되어 있습니다. 보고 된 경로는 컴파일러가 종속성을 찾는 위치에 따라 달라 집니다. 예기치 않은 결과가 발생 하는 경우 프로젝트의 포함 경로 설정을 확인 하는 것이 좋습니다.

### <a name="to-set-the-sourcedependencies-compiler-option-in-visual-studio"></a>Visual Studio에서/sourceDependencies 컴파일러 옵션을 설정 하려면

1. 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에서을 추가 하 *`/sourceDependencies: <filename>`* 고 **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- 이 옵션에는 프로그래밍 방식으로 해당 하는 항목이 없습니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)<br/>
