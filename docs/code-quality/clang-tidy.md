---
title: Visual Studio에서 Clang-Tidy 사용
description: Microsoft c + + 코드 분석을 위해 Visual Studio에서 Clang-Tidy를 사용 하는 방법입니다.
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
ms.openlocfilehash: 5b2da222caea435bdb24d774b5e93c995e734bb7
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919074"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Visual Studio에서 Clang-Tidy 사용

::: moniker range="<=msvc-150"

Clang-Tidy에 대 한 지원은 Visual Studio 2019 버전 16.4 이상 이어야 합니다. 이 버전에 대한 설명서를 보려면 이 문서의 Visual Studio **버전** 선택기 컨트롤을 Visual Studio 2019로 설정하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker-end

::: moniker range=">=msvc-160"

코드 분석은 Clang 또는 MSVC 도구 집합을 사용 하는지 여부에 관계 없이 MSBuild 및 CMake 프로젝트 모두에 대해 [Clang](https://clang.llvm.org/extra/clang-tidy/) 를 기본적으로 지원 합니다. Clang-Tidy 검사는 백그라운드 코드 분석의 일부로 실행 될 수 있습니다. 편집기 내 경고 (물결선)로 표시 되 고 오류 목록 표시 됩니다.

Clang-Tidy 지원은 Visual Studio 2019 버전 16.4부터 사용할 수 있습니다. Visual Studio 설치 관리자에서 c + + 워크 로드를 선택 하면 자동으로 포함 됩니다.

MSBuild와 CMake 모두에서 사용할 수 있는/clang 도구 집합을 사용 하는 경우 기본 분석 도구입니다. Clang-Tidy MSVC 도구 집합을 사용 하 여 표준 코드 분석 환경을 함께 실행 하거나 바꿀 때이를 구성할 수 있습니다. Clang-cl 도구 집합을 사용 하는 경우 Microsoft 코드 분석을 사용할 수 없습니다.

컴파일이 성공적으로 완료 된 후 Clang-Tidy 실행 됩니다. Clang-Tidy 결과를 얻으려면 소스 코드 오류를 해결 해야 할 수 있습니다.

## <a name="msbuild"></a>MSBuild

프로젝트 속성 창의 **코드 분석**  >  **일반** 페이지에서 코드 분석 및 빌드의 일부로 실행 되도록 Clang-Tidy를 구성할 수 있습니다. 도구를 구성 하는 옵션은 Clang-Tidy 하위 메뉴에서 찾을 수 있습니다.

자세한 내용은 [방법: C/c + + 프로젝트에 대 한 코드 분석 속성 설정](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md)을 참조 하세요.

## <a name="cmake"></a>CMake

CMake 프로젝트에서 내에 Clang-Tidy 검사를 구성할 수 있습니다 `CMakeSettings.json` . 열리고 나면 CMake 프로젝트 설정 편집기의 오른쪽 위 모서리에서 "JSON 편집"을 선택 합니다. 다음 키를 인식할 수 있습니다.

- `enableMicrosoftCodeAnalysis`: Microsoft 코드 분석을 사용 합니다.
- `enableClangTidyCodeAnalysis`: Clang-Tidy 분석을 사용 하도록 설정
- `clangTidyChecks`: 쉼표로 구분 된 목록으로 지정 된 Clang-Tidy 구성 (사용 또는 사용 안 함)

"사용 안 함" 옵션을 지정 하지 않은 경우 Visual Studio는 사용 된 플랫폼 도구 집합과 일치 하는 분석 도구를 선택 합니다.

## <a name="warning-display"></a>경고 표시

Clang-Tidy 실행 하면 오류 목록에 표시 되는 경고와 관련 된 코드 섹션 아래의 편집기 내 물결선로 표시 됩니다. 오류 목록에서 "Category" 열을 사용 하 여 Clang-Tidy 경고를 정렬 하 고 구성 합니다. **도구** 옵션에서 "코드 분석 물결선 사용 안 함" 설정을 전환 하 여 편집기 내 경고를 구성할 수 있습니다  >  **Options** .

## <a name="clang-tidy-configuration"></a>Clang-Tidy 구성

**Clang 검사** 옵션을 통해 Visual Studio 내에서 clang 실행 되는 검사를 구성할 수 있습니다. 이 입력은 도구의 인수에 제공 됩니다 **`--checks`** . 추가 구성은 사용자 지정 파일에 포함 될 수 있습니다 *`.clang-tidy`* . 자세한 내용은 [LLVM.org에 대 한 Clang 설명서](https://clang.llvm.org/extra/clang-tidy/)를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [MSBuild 프로젝트에 대 한 Clang/LLVM 지원](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [CMake 프로젝트에 대 한 Clang/LLVM 지원](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end
