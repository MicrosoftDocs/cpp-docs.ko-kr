---
title: C + + 코드를 업그레이드 하기 위한 Visual Studio IDE 도구
description: Visual Studio의 c + + 코드 편집기 및 코드 분석 도구를 통해 c + + 코드 베이스를 현대화 수 있습니다.
ms.date: 11/13/2019
ms.topic: conceptual
ms.openlocfilehash: d6368445d16232ff968b7116b0f0313e97aa144c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503767"
---
# <a name="visual-studio-ide-tools-for-upgrading-c-code"></a>C + + 코드를 업그레이드 하기 위한 Visual Studio IDE 도구

Visual Studio는 컴파일러 옵션, 코드 분석 경고 및 빠른 수정, 요약 정보 및 향상 된 스크롤 막대와 같은 편집기 기능을 사용 하 여 레거시 c + + 코드를 업그레이드 하는 데 도움이 됩니다. "레거시 코드" 라는 용어는 다음 범주 중 하나를 의미 합니다.

- 이전에는 Microsoft c + + 컴파일러 (MSVC)에서 허용 하지만 c + + 표준에는 영향을 받지 않은 코드입니다.

   호환 되지 않는 이전 MSVC 코드를 업그레이드 하려면 [/permissive-](../build/reference/permissive-standards-conformance.md) 컴파일러 옵션을 설정 합니다. 호환 되지 않는 사용의 모든 인스턴스에는 코드 편집기에서 빨간색 물결선 밑줄이 그어집니다. **오류 목록** 창의 오류 메시지에는 오류를 해결 하는 방법에 대 한 권장 사항이 포함 되어 있습니다. 오류 코드를 클릭 하 여 설명서의 도움말 페이지로 이동 합니다. 모든 오류를 한 번에 수정 하는 것이 적합 하지 않은 경우에는 **허용** 옵션을 설정 하 고 일부 오류를 수정한 다음 옵션을 해제 하 여 단계에서 비준수 코드를 업그레이드할 수 있습니다. 새로운 향상 된 기능을 사용 하 여 코드를 컴파일하고 나중에 다시 이동 하 여 나머지 문제를 수정할 수 있습니다. 비준수 MSVC 코드의 예는 [/permissive-](../build/reference/permissive-standards-conformance.md) 페이지를 참조 하세요.

- 이전 버전의 c + + 표준에서 허용 되었지만 이후 버전에서는 더 이상 사용 되지 않거나 제거 된 코드입니다.

   최신 언어 표준으로 업그레이드 하려면 [c + + 언어 표준](../build/reference/std-specify-language-standard-version.md) 옵션을 원하는 표준으로 설정 하 고 발생 하는 컴파일 오류를 수정 합니다. 일반적으로 언어 표준을 [/std: c + + 17](../build/reference/std-specify-language-standard-version.md)로 설정 하는 것이 좋습니다. 새 표준으로 업그레이드할 때 발생 하는 오류는 **허용** 옵션을 사용할 때 발생 하는 오류와 관련이 없습니다.

- 모든 버전의 표준을 준수 하지만 최신 c + +에서는 더 이상 모범 사례로 간주 되지 않는 코드입니다.

   변경이 권장 되는 코드를 식별 하려면 [코드 분석](../code-quality/code-analysis-for-c-cpp-overview.md)을 실행 합니다.

## <a name="open-and-convert-a-legacy-project"></a>레거시 프로젝트 열기 및 변환

레거시 프로젝트가 이전 버전의 Visual Studio를 기반으로 하는 경우 visual Studio 2017 또는 Visual Studio 2019에서 열 수 있습니다. Visual Studio는 모든 최신 컴파일러 및 IDE 기능을 지원 하 여 자동으로 현재 프로젝트 스키마로 변환 합니다.

![프로젝트 업그레이드](media/upgrade-dialog-v142.png "프로젝트 업그레이드")

자세한 내용은 [이전 버전의 Visual Studio에서 c + + 프로젝트 업그레이드](upgrading-projects-from-earlier-versions-of-visual-cpp.md)를 참조 하세요.

## <a name="search-the-code-base"></a>코드 베이스 검색

코드 베이스를 업그레이드 하는 경우에는 여러 파일을 검색 해야 하는 경우가 많습니다. 코드 베이스에서 항목을 검색 하려면 **ctrl + T** 를 눌러 모든 검색으로 **이동** 상자를 엽니다.

![전체로 이동](media/go-to-all.png "전체로 이동")

검색 범위를 좁히려면 1 자 필터 중 하나를 입력 하 고 그 뒤에 공백을 입력 한 다음 원하는 항목을 입력 합니다.

## <a name="error-list"></a>오류 목록

원하는 c + + 언어 표준 및 기타 컴파일러 옵션 (**프로젝트**  >  **속성**  >  **일반**)을 설정한 후 **ctrl + Shift + B** 를 눌러 프로젝트를 컴파일합니다. 코드의 다양 한 위치에서 몇 가지 오류와 경고가 빨간색 물결선 형식으로 표시 될 수 있습니다. 오류는 **오류 목록**에도 표시 됩니다. 특정 오류에 대 한 자세한 내용을 보려면 오류 코드를 클릭 하 여 설명서의 도움말 페이지로 이동 하십시오. "C"로 시작 하는 오류 코드는 컴파일러 오류입니다. "MSB"로 시작 하는 코드는 프로젝트 구성에 문제가 있음을 나타내는 MSBuild 오류입니다.

![오류 목록 컴파일러 및 MSBuild 오류](media/compiler-error-list.png "오류 목록 컴파일러 및 MSBuild 오류")

## <a name="document-health-indicator"></a>문서 상태 표시기

편집기 아래쪽의 문서 상태 표시기에는 현재 문서에 있는 오류 및 경고 수가 표시 되 고, 경고/오류 중 하나에서 다음으로 직접 이동할 수 있습니다.

![문서 상태 표시기](media/document-health-indicator.png "문서 상태 표시기")

대부분의 경우 Visual Studio 변경 기록 및 규칙 향상에 대 한 설명서에서 특정 오류에 대 한 자세한 정보를 찾을 수 있습니다.

- [C++ 규칙 향상](../overview/cpp-conformance-improvements.md)
- [Visual C++ 변경 기록 2003-2015](visual-cpp-change-history-2003-2015.md)
- [잠재적인 업그레이드 문제 개요](overview-of-potential-upgrade-issues-visual-cpp.md)

## <a name="use-code-analysis-to-modernize-your-code"></a>코드 분석을 사용 하 여 코드 현대화

업그레이드할 때 코드가 최소한 Microsoft 기본 권장 규칙을 따르도록 프로젝트에 대해 코드 분석을 실행 하는 것이 좋습니다. 이러한 규칙은 Microsoft에서 정의한 규칙의 조합 및 [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)하위 집합입니다. 이러한 사항을 준수 하면 버그의 일반적인 소스를 크게 줄이거나 없앨 수 있으며, 동시에 코드를 더 읽기 쉽게 유지 관리할 수 있습니다. Microsoft 네이티브 권장 규칙을 사용 하는 코드 분석은 기본적으로 사용 하도록 설정 되어 있습니다. **프로젝트**  >  **속성**  >  **코드 분석**에서 추가 규칙을 사용 하도록 설정할 수 있습니다. 규칙 중 하나를 위반 하는 코드는 경고로 플래그가 지정 되며 코드 편집기에서 녹색 물결선으로 밑줄이 표시 됩니다. 문제를 설명 하는 **QuickInfo** 도구 설명을 표시 하려면 물결선을 마우스로 가리킵니다.

![코드 분석 도구 설명](media/code-analysis-tooltip.png "코드 분석 경고")

**코드** 열에서 필터 아이콘을 클릭 하 여 표시 되는 경고를 선택 합니다.

![오류 목록의 코드 분석 필터](media/code-analysis-filter.png "오류 목록의 코드 분석 필터")

코드 분석 오류 및 경고도 컴파일러 오류와 마찬가지로 **오류 목록** 에도 표시 됩니다.

![오류 목록에서 코드 분석 경고](media/code-analysis-error-list.png "오류 목록에서 코드 분석 경고")

활성 상태인 규칙을 변경 하 고 사용자 지정 규칙 집합을 만들 수 있습니다. 코드 분석을 사용 하는 방법에 대 한 자세한 내용은 [c/c + + 용 코드 분석 개요](../code-quality/code-analysis-for-c-cpp-overview.md)를 참조 하세요.

## <a name="use-quick-actions-to-modernize-code"></a>빠른 작업을 사용 하 여 코드 현대화

코드 편집기는 몇 가지 일반적인 권장 사항에 대 한 빠른 작업을 제공 합니다. 전구 아이콘이 표시 되 면 클릭 하 여 사용 가능한 빠른 작업을 볼 수 있습니다.

### <a name="convert-macros-to-constexpr-functions"></a>매크로를 constexpr 함수로 변환

다음 그림에서는 기본 의미 체계를 색으로 지정 하는 이라는 매크로를 사용 하는 방법을 보여 줍니다 `AVERAGE` . 또한 이미지는 마우스 커서를 포인터로 가리킬 때 표시 되는 QuickInfo 도구 설명을 보여 줍니다.

![QuickInfo 매크로 확장](media/macro-expansion-quick-info.png "QuickInfo tooltip 매크로 확장")

최신 c + +에서는 매크로를 사용 하지 않는 것이 좋습니다. Visual Studio를 사용 하면 매크로를 쉽게 함수로 변환할 수 있습니다 **`constexpr`** .

1. 를 마우스 오른쪽 단추로 클릭 하 `AVERAGE` 고 **정의로 이동을**선택 합니다.
2. 드라이버 아이콘을 클릭 하 고 **매크로를 constexpr로 변환을** 선택 합니다.

   ![Constexpr에 대 한 빠른 작업 매크로](media/quick-action-macro-to-constexpr.png "Constexpr에 대 한 빠른 작업 매크로")

매크로는 아래와 같이 변환 됩니다.

![constexpr 함수](media/constexpr-function.png "constexpr 함수")

이제에 대 한 호출이 `AVERAGE` 함수 호출로 색으로 표시 되 고 요약 정보 도구 설명는 함수의 추론 된 형식을 표시 합니다.

![constexpr 함수 호출](media/constexpr-function-call.png "constexpr 함수 호출")

### <a name="initialize-variables"></a>변수 초기화

초기화 되지 않은 변수는 심각한 버그로 이어질 수 있는 임의의 값을 포함할 수 있습니다. 코드 분석은 이러한 인스턴스에 플래그를 제공 하 고 편집기는 빠른 작업을 제공 합니다.

![변수 초기화](media/init-variable.png "변수 빠른 작업 초기화")

### <a name="convert-to-raw-string-literal"></a>원시 문자열 리터럴로 변환

원시 문자열 리터럴은 포함 된 이스케이프 문자를 사용 하는 문자열 보다 오류가 발생 하기 쉬우며 더 편리 하 게 사용할 수 있습니다. 문자열을 마우스 오른쪽 단추로 클릭 하 고 **빠른 작업** 을 선택 하 여 원시 문자열 리터럴로 변환 합니다.

![원시 문자열 리터럴](media/raw-string-literal.png "원시 문자열 리터럴")

문자열은로 변환 됩니다 `R"(C:\Users\bjarnes\demo\output.txt)"` .
