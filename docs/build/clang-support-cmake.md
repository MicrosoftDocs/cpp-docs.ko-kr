---
title: Visual Studio CMake 프로젝트의 Clang/LLVM 지원
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: e23da02a0c3af624ddb30cec8dbb5afda55660c9
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919581"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Visual Studio CMake 프로젝트의 Clang/LLVM 지원

::: moniker range="<=msvc-150"

Clang 지원은 Visual Studio 2019에서 사용할 수 있습니다.

::: moniker-end

::: moniker range="msvc-160"

Clang과 함께 Visual Studio를 사용하여 Windows 또는 Linux를 대상으로 하는 C++ CMake 프로젝트를 편집하고 디버그할 수 있습니다.

**Windows** : Visual Studio 2019 버전 16.1에는 Windows를 대상으로 하는 CMake 프로젝트에서 Clang/LLVM으로 편집, 빌드 및 디버깅하는 기능에 대한 지원이 포함되어 있습니다.

**Linux** : Linux CMake 프로젝트의 경우 특별한 Visual Studio 지원이 필요 없습니다. 배포판의 패키지 관리자를 사용하여 Clang을 설치하고, CMakeLists.txt 파일에서 적절한 명령을 추가할 수 있습니다.

## <a name="install"></a>설치

Visual Studio에서 최상으로 IDE를 지원하려면 Windows용 최신 Clang 컴파일러 도구를 사용하는 것이 좋습니다. 이 도구가 아직 없는 경우 Visual Studio 설치 관리자를 열고 선택적 구성 요소인 **C++를 사용한 데스크톱 개발** 아래에서 **Windows용 C++ Clang 컴파일러** 를 선택하여 설치할 수 있습니다. 사용자 지정 Clang 설치를 사용하는 경우 **v142 빌드 도구용 C++ Clang-cl** 구성 요소를 확인하세요.

![Clang 구성 요소 설치](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>새 구성 만들기

CMake 프로젝트에 새 Clang 구성을 추가하려면 다음을 수행합니다.

1. **솔루션 탐색기** 에서 CMakeLists.txt 파일을 마우스 오른쪽 단추로 클릭하고 **프로젝트에 대한 CMake 설정** 을 선택합니다.

1. 다음과 같이 **구성** 에서 **구성 추가** 단추를 누릅니다.

   ![구성 추가](media/cmake-add-config-icon.png)

1. 원하는 Clang 구성(Windows 및 Linux에 대해 별도의 Clang 구성이 제공됨)을 선택하고 **선택** 을 누릅니다.

   ![CMake Clang 구성](media/cmake-clang-configuration.png)

1. 이 구성을 수정하려면 **CMake 설정 편집기** 를 사용하세요. 자세한 내용은 [Visual Studio에서 CMake 빌드 설정 사용자 지정](customize-cmake-settings.md)을 참조하세요.

## <a name="modify-an-existing-configuration-to-use-clang"></a>Clang을 사용하도록 기존 구성 수정

Clang를 사용하도록 기존 구성을 수정하려면 다음 단계를 따르세요.

1. **솔루션 탐색기** 에서 CMakeLists.txt 파일을 마우스 오른쪽 단추로 클릭하고 **프로젝트에 대한 CMake 설정** 을 선택합니다.

1. **일반** 에서 **도구 집합** 드롭다운을 선택하고 원하는 Clang 도구 집합을 선택합니다.

   ![도구 집합이 선택되고 clang cl x86이 강조 표시된 일반 대화 상자의 스크린샷](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>사용자 지정 Clang 위치

기본적으로 Visual Studio는 다음 두 위치에서 Clang을 찾습니다.

- (Windows) Visual Studio 설치 관리자와 함께 제공되는 Clang/LLVM의 내부 설치 복사본입니다.
- (Windows 및 Linux) PATH 환경 변수입니다.

다음과 같이 **CMake 설정** 에서 **CMAKE_C_COMPILER** 및 **CMAKE_CXX_COMPILER** CMake 변수를 설정하여 다른 위치를 지정할 수 있습니다.

![CMake CXX Compiler가 강조 표시된 CMake 설정 대화 상자의 스크린샷](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Clang 호환성 모드

Windows 구성의 경우 CMake는 기본적으로 [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) 모드에서 Clang을 호출하고 표준 라이브러리의 Microsoft 구현과 연결됩니다. 기본적으로 **clang-cl.exe** 는 `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`에 있습니다.

**CMake 변수 및 캐시** 의 **CMake 설정** 에서 이 값을 수정할 수 있습니다. **고급 변수 표시** 를 클릭합니다. 아래로 스크롤하여 **CMAKE_CXX_COMPILER** 를 찾은 다음, **찾아보기** 단추를 클릭하여 다른 컴파일러 경로를 지정합니다.

## <a name="edit-build-and-debug"></a>편집, 빌드 및 디버그

Clang 구성을 설정한 후 프로젝트를 빌드하고 디버그할 수 있습니다. Visual Studio는 Clang 컴파일러를 사용 중임을 감지하고 IntelliSense, 강조 표시, 탐색 및 기타 편집 기능을 제공합니다. 오류 및 경고는 **출력 창** 에 표시됩니다.

디버깅하는 경우 중단점, 메모리 및 데이터 시각화, 그리고 대부분의 다른 디버깅 기능을 사용할 수 있습니다. ‘편집’, ‘계속’과 같은 일부 컴파일러 종속 기능은 Clang 구성에 사용할 수 없습니다.

![CMake Clang 디버깅](media/clang-debug-visualize.png)

::: moniker-end
