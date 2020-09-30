---
title: 심각한 오류 C1083
ms.date: 09/01/2017
f1_keywords:
- C1083
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
ms.openlocfilehash: 57ae8f2d0b7f02732032151f86617498e5201c61
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509749"
---
# <a name="fatal-error-c1083"></a>심각한 오류 C1083

> *Filetype* 파일을 열 수 없습니다. '*file*': *message*

필요한 파일을 찾을 수 없는 경우 컴파일러에서 C1083 오류를 생성 합니다. 이 오류의 원인은 다양합니다. 잘못 된 포함 검색 경로 이거나 누락 된 헤더 파일이 나 misnamed 헤더 파일이 가장 일반적인 원인 이지만 다른 파일 형식 및 문제로 인해 C1083 발생할 수도 있습니다. 컴파일러에서이 오류를 생성 하는 일반적인 이유는 다음과 같습니다.

## <a name="the-specified-file-name-is-wrong"></a>지정한 파일 이름이 잘못됨

파일 이름이 잘못 입력될 수 있습니다. 예를 들면 다음과 같습니다.

`#include <algorithm.h>`

원하는 파일을 찾을 수 없습니다. 대부분의 c + + 표준 라이브러리 헤더 파일에는 .h 파일 이름 확장명이 없습니다. \<algorithm>이 지시문은 헤더를 찾을 수 없습니다 `#include` . 이 문제를 해결 하려면 다음 예제와 같이 올바른 파일 이름을 입력 했는지 확인 합니다.

`#include <algorithm>`

특정 C 런타임 라이브러리 헤더는 표준 포함 디렉터리의 하위 디렉터리에 있습니다. 예를 들어를 포함 하려면 *`sys/types.h`* *`sys`* 지시문에 하위 디렉터리 이름을 포함 해야 합니다 `#include` .

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>파일이 포함 검색 경로에 포함 되어 있지 않습니다.

컴파일러가 `#include` 또는 `#import` 지시문으로 표시되는 검색 규칙을 사용하여 파일을 찾을 수 없습니다. 예를 들어 헤더 파일 이름을 따옴표로 묶으면

`#include "myincludefile.h"`

이렇게 하면 컴파일러가 소스 파일을 먼저 포함 하는 동일한 디렉터리에서 파일을 찾은 다음 빌드 환경에서 지정 된 다른 위치를 찾습니다. 따옴표에 절대 경로가 포함되어 있는 경우 컴파일러는 해당 위치에서만 파일을 찾습니다. 따옴표에 상대 경로가 포함되어 있는 경우 컴파일러는 소스 디렉터리에 관련된 디렉터리에서 파일을 찾습니다.

이름이 꺾쇠 괄호로 묶여 있으면이 고,

`#include <stdio.h>`

컴파일러는 빌드 환경, **`/I`** 컴파일러 옵션, **`/X`** 컴파일러 옵션 및 **INCLUDE** 환경 변수에서 정의한 검색 경로를 따릅니다. 파일을 찾는 데 사용 되는 검색 순서에 대 한 구체적인 정보를 비롯 한 자세한 내용은 [#include 지시문 (c/c + +)](../../preprocessor/hash-include-directive-c-cpp.md) 및 [#import 지시문](../../preprocessor/hash-import-directive-cpp.md)을 참조 하세요.

포함 파일이 원본 디렉터리를 기준으로 하는 다른 디렉터리에 있고 include 지시문에서 상대 경로를 사용 하는 경우 꺾쇠 괄호 대신 큰따옴표를 사용 해야 합니다. 예를 들어 헤더 파일이 *`myheader.h`* 헤더 라는 프로젝트 소스의 하위 디렉터리에 있는 경우이 예에서는 파일을 찾지 못하고 C1083을 발생 시킵니다.

`#include <headers\myheader.h>`

그러나이 예는 다음과 같습니다.

`#include "headers\myheader.h"`

상대 경로는 포함 검색 경로의 디렉터리와 함께 사용할 수도 있습니다. Visual Studio에서 **include** 환경 변수 또는 **포함 디렉터리** 경로에 디렉터리를 추가 하는 경우 include 지시문에 경로 부분을 추가 하지 마십시오. 예를 들어 헤더가에 있으며 *`\path\example\headers\myheader.h`* *`\path\example\headers\`* Visual Studio에서 **포함 디렉터리** 경로에를 추가 하지만 `#include` 지시문은 파일을

`#include <headers\myheader.h>`

그런 다음 파일을 찾을 수 없습니다. 포함 검색 경로에 지정 된 디렉터리에 상대적인 올바른 경로를 사용 합니다. 이 예에서는 include 검색 경로를로 변경 *`\path\example\`* 하거나 *`headers\`* 지시문에서 경로 세그먼트를 제거할 수 있습니다 `#include` .

## <a name="third-party-library-issues-and-vcpkg"></a>타사 라이브러리 문제 및 vcpkg

빌드의 일부로 타사 라이브러리를 구성 하려고 할 때이 오류가 표시 되는 경우 [`vcpkg`](../../build/vcpkg.md) c + + 패키지 관리자를 사용 하 여 라이브러리를 설치 하 고 작성 하는 것이 좋습니다. vcpkg는 크고 증가 하는 [타사 라이브러리 목록을](https://github.com/Microsoft/vcpkg/tree/master/ports)지원 하 고 프로젝트의 일부로 성공한 빌드에 필요한 모든 구성 속성 및 종속성을 설정 합니다.

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>파일이 프로젝트에 있지만 포함 검색 경로는 아닙니다.

헤더 파일이 프로젝트의 일부로 **솔루션 탐색기** 에 나열 된 경우에도 파일은 `#include` 소스 파일의 또는 지시문에 의해 참조 되 `#import` 고 포함 검색 경로에 있는 컴파일러 에서만 찾을 수 있습니다. 빌드 종류에 따라 다른 검색 경로가 사용될 수도 있습니다. **`/X`** 컴파일러 옵션은 포함 검색 경로에서 디렉터리를 제외 하는 데 사용할 수 있습니다. 이렇게 하면 각 빌드에서 이름은 같지만 다른 디렉터리에 보관되는 다른 포함 파일을 사용할 수 있습니다. 이는 전처리기 명령을 통한 조건부 컴파일의 대체 방법입니다. 컴파일러 옵션에 대 한 자세한 내용은 **`/X`** [ `/X` (표준 포함 경로 무시)](../../build/reference/x-ignore-standard-include-paths.md)를 참조 하세요.

이 문제를 해결하려면 컴파일러가 포함되거나 가져온 파일을 찾는 데 사용하는 경로를 수정합니다. 새 프로젝트는 기본 포함 검색 경로를 사용 합니다. 프로젝트에 대 한 디렉터리를 추가 하려면 포함 검색 경로를 수정 해야 할 수 있습니다. 명령줄에서 컴파일하는 경우 **INCLUDE** 환경 변수에 대 한 경로를 추가 하거나 **`/I`** 컴파일러 옵션을 추가 하 여 파일 경로를 지정 합니다.

Visual Studio에서 포함 디렉터리 경로를 설정 하려면 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 왼쪽 창의 **구성 속성** 에서 **VC + + 디렉터리** 를 선택 하 고 **포함 디렉터리** 속성을 편집 합니다. Visual Studio에서 컴파일러가 검색 하는 사용자별 및 프로젝트별 디렉터리에 대 한 자세한 내용은 [VC + + 디렉터리 속성 페이지](../../build/reference/vcpp-directories-property-page.md)를 참조 하세요. 컴파일러 옵션에 대 한 자세한 내용은 **`/I`** [ `/I` (추가 포함 디렉터리)](../../build/reference/i-additional-include-directories.md)를 참조 하세요.

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>명령줄 INCLUDE 또는 LIB 환경이 설정 되지 않았습니다.

명령줄에서 컴파일러를 호출하는 경우 대체로 환경 변수를 사용하여 검색 경로를 지정합니다. **INCLUDE** 또는 **LIB** 환경 변수에 설명 된 검색 경로가 올바르게 설정 되지 않은 경우 C1083 오류가 발생할 수 있습니다. 개발자 명령 프롬프트 바로 가기를 사용 하 여 명령줄 빌드에 대 한 기본 환경을 설정 하는 것이 좋습니다. 자세한 내용은 [명령줄에서 c/c + + 빌드](../../build/building-on-the-command-line.md)를 참조 하세요. 환경 변수를 사용 하는 방법에 대 한 자세한 내용은 [방법: 빌드 시 환경 변수 사용](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build)을 참조 하세요.

## <a name="the-file-may-be-locked-or-in-use"></a>파일이 잠겼거나 사용 중일 수 있습니다.

다른 프로그램을 사용 하 여 파일을 편집 하거나 액세스 하는 경우 파일이 잠겨 있을 수 있습니다. 다른 프로그램에서 파일을 닫아 보세요. 경우에 따라 병렬 컴파일 옵션을 사용 하는 경우 다른 프로그램은 Visual Studio 자체가 될 수 있습니다. 병렬 빌드 옵션을 off로 설정 하면 오류가 발생 합니다. 다른 병렬 빌드 시스템 에서도이 문제가 발생할 수 있습니다. 빌드 순서가 올바른지 파일 및 프로젝트 종속성을 설정 해야 합니다. 경우에 따라 여러 프로젝트에서 빌드할 수 있는 공용 파일에 대해 빌드 종속성 순서를 적용 하는 중간 프로젝트를 만드는 것이 좋습니다. 바이러스 백신 프로그램에서 최근에 변경 된 파일을 검색 하기 위해 임시로 잠그는 경우가 있습니다. 가능 하면 바이러스 백신 스캐너에서 프로젝트 빌드 디렉터리를 제외 하는 것이 좋습니다.

## <a name="the-wrong-version-of-a-file-name-is-included"></a>잘못된 버전의 파일 이름이 포함됨

C1083 오류가 잘못된 버전의 파일이 포함되었음을 나타낼 수도 있습니다. 예를 들어 빌드에서 사용되지 않는 헤더 파일에 대한 `#include` 지시문이 있는 잘못된 버전의 파일이 빌드에 포함되어 있을 수 있습니다. 예를 들어 특정 파일은 x86 빌드에만 적용 되거나 빌드를 디버그할 수 있습니다. 헤더 파일을 찾을 수 없는 경우 컴파일러에서 C1083 오류가 발생합니다. 이 문제를 해결하려면 올바른 파일을 사용하고 헤더 파일 또는 디렉터리를 빌드에 추가하지 마십시오.

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>미리 컴파일된 헤더가 미리 컴파일되지 않았음

미리 컴파일된 헤더를 사용 하도록 프로젝트를 구성 하는 경우 *`.pch`* 헤더 콘텐츠를 사용 하는 파일을 컴파일할 수 있도록 관련 파일을 만들어야 합니다. 예를 들어 *`pch.cpp`* *`stdafx.cpp`* Visual Studio 2017 및 이전 버전의 파일은 새 프로젝트에 대 한 프로젝트 디렉터리에 자동으로 만들어집니다. 먼저 해당 파일을 컴파일하여 미리 컴파일된 헤더 파일을 만듭니다. 일반적인 빌드 프로세스 디자인에서는이 작업이 자동으로 수행 됩니다. 자세한 내용은 [미리 컴파일된 헤더 파일 만들기](../../build/creating-precompiled-header-files.md)를 참조 하세요.

## <a name="additional-causes"></a>추가 원인

- SDK 또는 타사 라이브러리를 설치 했지만 SDK 또는 라이브러리를 설치한 후에는 새 개발자 명령 프롬프트 창을 열지 않았습니다. SDK 또는 라이브러리에서 파일을 **포함** 경로에 추가 하는 경우 이러한 환경 변수 변경을 선택 하기 위해 새 개발자 명령 프롬프트 창을 열어야 할 수 있습니다.

- 이 파일은 관리 코드를 사용 하지만 컴파일러 옵션은 **`/clr`** 지정 되지 않았습니다. 자세한 내용은 [ `/clr` (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)를 참조 하세요.

- **`/analyze`** 헤더를 미리 컴파일하는 데 사용 되는 것 보다 다른 컴파일러 옵션 설정을 사용 하 여 파일을 컴파일합니다. 프로젝트에 대 한 헤더를 미리 컴파일하는 경우 모두 동일한 설정을 사용 해야 합니다 **`/analyze`** . 자세한 내용은 [ `/analyze` (코드 분석)](../../build/reference/analyze-code-analysis.md)를 참조 하세요.

- Linux 용 Windows 하위 시스템에서 파일 또는 디렉터리를 만들었습니다. 디렉터리 단위 대/소문자 구분을 사용 하도록 설정 하 고 지정 된 경로 또는 파일의 대/소문자가 디스크에 있는 경로 또는 파일의 대/소문자와 일치 하지 않습니다.

- 파일, 디렉터리 또는 디스크가 읽기 전용입니다.

- Visual Studio 또는 명령줄 도구에 파일이 나 디렉터리를 읽을 수 있는 권한이 없습니다. 예를 들어 프로젝트 파일의 소유권이 Visual Studio 또는 명령줄 도구를 실행 하는 프로세스와 다른 경우이 문제가 발생할 수 있습니다. 경우에 따라 Visual Studio 또는 개발자 명령 프롬프트를 관리자 권한으로 실행 하 여이 문제를 해결할 수 있습니다.

- 파일 핸들이 충분하지 않습니다. 일부 애플리케이션을 닫은 후 다시 컴파일하십시오. 이러한 경우는 일반적인 상황에서 거의 발생하지 않습니다. 하지만 실제 메모리가 제한된 컴퓨터에서 큰 프로젝트를 빌드하는 경우 발생할 수 있습니다.

## <a name="example"></a>예제

다음 예에서는 헤더 파일이 `"test.h"` 원본 디렉터리 또는 포함 검색 경로에 없는 경우 C1083 오류를 생성 합니다.

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

IDE 또는 명령줄에서 C/c + + 프로젝트를 빌드하는 방법 및 환경 변수를 설정 하는 방법에 대 한 자세한 내용은 [프로젝트 및 빌드 시스템](../../build/projects-and-build-systems-cpp.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

- [MSBuild 속성](/visualstudio/msbuild/msbuild-properties)
