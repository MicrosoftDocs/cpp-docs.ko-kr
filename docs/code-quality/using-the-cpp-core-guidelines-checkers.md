---
title: C++ Core Guidelines 사용
description: C++ Core Guidelines에 대 한 Microsoft c + + 코드 분석 규칙을 설정 하 고 사용 하는 방법입니다.
ms.date: 12/16/2020
ms.topic: conceptual
dev_langs:
- CPP
ms.openlocfilehash: 93b69839bc9e5ffd45a08da12e84028eea10aef4
ms.sourcegitcommit: 387ce22a3b0137f99cbb856a772b5a910c9eba99
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97645165"
---
# <a name="use-the-c-core-guidelines-checkers"></a>C++ Core Guidelines 검사기 사용

C++ Core Guidelines은 c + + 전문가 및 디자이너에서 만든 c + +의 코딩에 대 한 지침, 규칙 및 모범 사례 집합입니다. Visual Studio는 현재 c + + 용 코드 분석 도구의 일부로 이러한 규칙의 하위 집합을 지원 합니다. 핵심 지침 체커는 Visual Studio 2017 및 Visual Studio 2019에서 기본적으로 설치 됩니다. [Visual Studio 2015에 대 한 NuGet 패키지로 제공](#vs2015_corecheck)됩니다.

## <a name="the-c-core-guidelines-project"></a>C++ Core Guidelines 프로젝트

Bjarne Stroustrup 및 기타 사용자가 만든 C++ Core Guidelines은 최신 c + +를 안전 하 고 효과적으로 사용 하는 방법에 대 한 지침입니다. 지침은 정적 형식 안전성 및 리소스 안전성을 강조 합니다. 언어의 오류가 발생 하기 쉬운 대부분의 부분을 제거 하거나 최소화 하는 방법을 식별 합니다. 또한 코드를 더 간단 하 고 안정적 이며 성능을 향상 시키는 방법을 제안 합니다. 이러한 지침은 표준 c + + Foundation에 의해 유지 관리 됩니다. 자세한 내용은 [GitHub](https://github.com/isocpp/CppCoreGuidelines)에서 설명서, [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)및 C++ Core Guidelines 설명서 프로젝트 파일 액세스를 참조 하세요.

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>코드 분석에서 C++ Core Check 지침 사용

::: moniker range="<=msvc-150"

C++ Core Check 규칙의 하위 집합은 Microsoft Native 권장 규칙 집합에 포함 되어 있습니다. 코드 분석을 사용 하도록 설정한 경우 기본적으로 실행 되는 규칙 집합입니다.

### <a name="to-enable-code-analysis-on-your-project"></a>프로젝트에서 코드 분석을 사용 하도록 설정 하려면

1. 프로젝트에 대 한  **속성 페이지** 대화 상자를 엽니다.

1. **구성 속성** > **코드 분석** 속성 페이지를 선택 합니다.

1. **빌드 시 코드 분석 사용** 확인란을 선택 합니다.

![코드 분석 일반 설정의 속성 페이지](media/cppcorecheck_codeanalysis_general.png)

추가 핵심 검사 규칙을 사용 하도록 설정 하려면 드롭다운 목록을 열고 포함 하려는 규칙 집합을 선택 합니다.

![추가 C++ Core Check 규칙 집합 드롭다운](media/cppcorecheck_codeanalysis_extensions.png)

::: moniker-end
::: moniker range=">=msvc-160"

C++ Core Check 규칙의 하위 집합은 Microsoft Native 권장 규칙 집합에 포함 되어 있습니다. Microsoft 코드 분석이 사용 하도록 설정 된 경우 기본적으로 실행 되는 규칙 집합입니다.

### <a name="to-enable-code-analysis-on-your-project"></a>프로젝트에서 코드 분석을 사용 하도록 설정 하려면 다음을 수행 합니다.

1. 프로젝트에 대 한  **속성 페이지** 대화 상자를 엽니다.

1. **구성 속성** > **코드 분석** 속성 페이지를 선택 합니다.

1. **빌드 시 코드 분석 사용** 및 **Microsoft 코드 분석** 사용 속성을 설정 합니다.

지원 되는 모든 C++ Core Check 규칙을 실행 하거나 실행할 사용자 고유의 하위 집합을 선택할 수도 있습니다.

### <a name="to-enable-additional-core-check-rules"></a>추가 핵심 검사 규칙을 사용 하도록 설정 하려면

1. 프로젝트에 대 한  **속성 페이지** 대화 상자를 엽니다.

1. **구성 속성** > **코드 분석** > **Microsoft** 속성 페이지를 선택 합니다.

1. **활성 규칙** 드롭다운 목록을 열고 **여러 규칙 집합 선택** 을 선택 합니다.

1. **규칙 집합 추가 또는 제거** 대화 상자에서 포함 하려는 규칙 집합을 선택 합니다.

::: moniker-end

## <a name="examples"></a>예

C++ Core Check 규칙에서 찾을 수 있는 몇 가지 문제의 예는 다음과 같습니다.

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

이 예제에서는 C++ Core Check 규칙에서 찾을 수 있는 몇 가지 경고를 보여 줍니다.

- C26494은 규칙 유형입니다. 5: 항상 개체를 초기화 합니다.

- C26485는 규칙 범위입니다. 3: 배열-포인터 감소 하지 않습니다.

- C26481는 규칙 범위입니다. 1: 포인터 산술 연산을 사용 하지 않습니다. 대신 `span`를 사용하세요.

C++ Core Check 코드 분석 규칙 집합을 설치 하 고 사용 하도록 설정한 다음이 코드를 컴파일합니다. 코드 분석은 처음 두 경고를 출력 하 고 세 번째 경고를 표시 하지 않습니다. 다음은 Visual Studio 2015의 예제 코드에 대 한 빌드 출력입니다.

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

C++ Core Guidelines는 더 빠르고 안전한 코드를 작성 하는 데 도움이 됩니다. 그러나 규칙이 나 프로필을 적용 하지 않아야 하는 인스턴스를 찾을 수 있습니다. 코드에서 직접 표시 하지 않는 것이 쉽습니다. 특성을 사용 `[[gsl::suppress]]` 하 여 다음 코드 블록에서 규칙 위반을 검색 하 고 보고할 수 C++ Core Check 유지할 수 있습니다. 개별 문을 표시 하 여 특정 규칙을 표시 하지 않을 수 있습니다. `[[gsl::suppress(bounds)]]`특정 규칙 번호를 포함 하지 않고 작성 하 여 전체 범위 프로필을 표시 하지 않을 수도 있습니다.

## <a name="supported-rule-sets"></a>지원 되는 규칙 집합

C++ Core Guidelines 검사기에 새 규칙을 추가 하면 기존 코드에 대해 생성 되는 경고 수가 늘어날 수 있습니다. 미리 정의 된 규칙 집합을 사용 하 여 사용할 규칙의 종류를 필터링 할 수 있습니다. [Visual Studio C++ Core Check 참조](code-analysis-for-cpp-corecheck.md)에서 대부분의 규칙에 대 한 참조 문서를 찾을 수 있습니다.

- **산술 규칙**: 산술 [오버플로](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow), [부호 없는](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned)서명 된 작업 및 [비트 조작을](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative)검색 하는 규칙입니다. <sup>15.6</sup>

- **범위 규칙**: [C++ Core Guidelines의 범위 프로필](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)을 적용 합니다. <sup>15.3</sup>

- **클래스 규칙**: 특수 멤버 함수 및 가상 사양의 적절 한 사용에 초점을 맞춘 몇 가지 규칙입니다. [클래스 및 클래스 계층 구조](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class)에 대해 권장 하는 검사의 하위 집합입니다. <sup>15.5</sup>

- **동시성 규칙**: 잘못 된 가드 개체 선언을 catch 하는 단일 규칙입니다. 자세한 내용은 [concurrency와 관련 된 지침](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency)을 참조 하세요. <sup>15.5</sup>

- **Const 규칙**: [C++ Core Guidelines에서 const 관련 검사를](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability)적용 합니다. <sup>15.3</sup>

- **선언 규칙**: 전역 변수를 선언 하는 방법에 초점을 맞춘 [인터페이스 지침](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) 의 몇 가지 규칙입니다. <sup>15.5</sup>

- **열거형 규칙**: 이러한 규칙 [은 C++ Core Guidelines에서 열거형 관련 검사를](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-enum)적용 합니다. <sup>16.3</sup>

- **실험적 규칙** 이러한 규칙은 유용 하지만 일상적으로 사용할 준비가 되지 않은 실험적 C++ Core Check 규칙입니다. 사용해 보고 피드백을 [제공](https://aka.ms/feedback/suggest?space=62)하세요. <sup>16.0</sup>

- **함수 규칙**: 지정자를 도입 하는 데 도움이 되는 두 가지 검사입니다 **`noexcept`** . [Clear 함수 디자인 및 구현](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions)에 대 한 지침의 일부입니다. <sup>15.5</sup>

- **Gsl 규칙**: 이러한 규칙은 [C++ Core Guidelines에서 지침 지원 라이브러리](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-gsl)와 관련 된 검사를 적용 합니다. <sup>15.7</sup>

- **수명 규칙**: 이러한 규칙은 [C++ Core Guidelines의 수명 프로필](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prolifetime-lifetime-safety-profile)을 적용 합니다. <sup>15.7</sup>

- **소유자 포인터 규칙**: [ \<T> C++ Core Guidelines 소유자 관련 리소스 관리 검사를](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)적용 합니다.<sup> 15.3</sup>

- **원시 포인터 규칙**: [C++ Core Guidelines에서 원시 포인터 관련 리소스 관리 검사를](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)적용 합니다. <sup>15.3</sup>

- **공유 포인터 규칙**: [리소스 관리](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) 지침 적용의 일부입니다. <sup>15.5</sup> 공유 포인터가 함수로 전달 되거나 로컬로 사용 되는 방법과 관련 된 몇 가지 규칙을 추가 했습니다.

- **Stl 규칙**: 이러한 규칙 [은 C++ Core Guidelines에서 c + + 표준 라이브러리 (STL)](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-stdlib)와 관련 된 검사를 적용 합니다. <sup>15.7</sup>

- **스타일 규칙**: [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto)를 사용 하는 차단을는 간단 하지만 중요 한 검사입니다. <sup>15.5</sup> c + +에서 코딩 스타일과 식 및 문의 사용을 개선 하는 첫 번째 단계입니다.

- **형식 규칙**: [C++ Core Guidelines의 형식 프로필](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile)을 적용 합니다. <sup>15.3</sup>

- **고유 포인터 규칙**: [C++ Core Guidelines의 고유 포인터 의미 체계를 사용 하 여 형식과 관련 된 리소스 관리 검사를](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)적용 합니다. <sup>15.3</sup>

- **C++ Core Check 규칙**:이 규칙 집합은 실험적 규칙을 제외 하 고 [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-core-guidelines)에서 현재 구현 된 모든 검사를 포함 합니다.

<sup>15.3</sup> 이러한 규칙은 Visual Studio 2017 버전 15.3 \에 먼저 나타났습니다.
<sup>15.5</sup> 이러한 규칙은 Visual Studio 2017 버전 15.5 \에 먼저 나타났습니다.
<sup>15.6</sup> 이러한 규칙은 Visual Studio 2017 버전 15.6 \에 먼저 나타났습니다.
<sup>15.7</sup> 이러한 규칙은 Visual Studio 2017 버전 15.7 \에 먼저 나타났습니다.
<sup>16.0</sup> 이러한 규칙은 Visual Studio 2019 버전 16.0 \에 먼저 나타났습니다.
<sup>16.3</sup> 이러한 규칙은 Visual Studio 2019 버전 16.3에 처음 나타났습니다.

경고를 하나 또는 몇 개의 그룹 으로만 제한 하도록 선택할 수 있습니다. **기본 최소** 및 **기본 권장** 규칙 집합에는 C++ Core Check 규칙 및 기타 PREfast 검사가 포함 됩니다.

::: moniker range="<=msvc-150"

사용 가능한 규칙 집합을 보려면 **프로젝트 속성** 대화 상자를 엽니다. **속성 페이지** 대화 상자에서 **구성 속성**  >  **코드 분석**  >  **일반** 속성 페이지를 선택 합니다. 그런 다음 **규칙 집합** 콤보 상자에서 드롭다운을 열어 사용 가능한 규칙 집합을 표시 합니다. 규칙 집합의 사용자 지정 조합을 작성 하려면 **여러 규칙 집합 선택** 을 선택 합니다. **규칙 집합 추가 또는 제거** 대화 상자에서 선택할 수 있는 규칙을 나열 합니다. Visual Studio에서 규칙 집합을 사용 하는 방법에 대 한 자세한 내용은 [규칙 집합을 사용 하 여 실행할 c + + 규칙 지정을](using-rule-sets-to-specify-the-cpp-rules-to-run.md)참조 하세요.

::: moniker-end
::: moniker range=">=msvc-160"

사용 가능한 규칙 집합을 보려면 **프로젝트 속성** 대화 상자를 엽니다. **속성 페이지** 대화 상자에서 **구성 속성**  >  **코드 분석**  >  **Microsoft** 속성 페이지를 선택 합니다. 그런 다음 **활성 규칙** 콤보 상자에서 드롭다운을 열어 사용 가능한 규칙 집합을 표시 합니다. 규칙 집합의 사용자 지정 조합을 작성 하려면 **여러 규칙 집합 선택** 을 선택 합니다. **규칙 집합 추가 또는 제거** 대화 상자에서 선택할 수 있는 규칙을 나열 합니다. Visual Studio에서 규칙 집합을 사용 하는 방법에 대 한 자세한 내용은 [규칙 집합을 사용 하 여 실행할 c + + 규칙 지정을](using-rule-sets-to-specify-the-cpp-rules-to-run.md)참조 하세요.

::: moniker-end

## <a name="macros"></a>Macros

C++ Core Guidelines 검사기는 코드에서 전체 경고 범주를 더 쉽게 표시 하지 않도록 하는 매크로를 정의 하는 헤더 파일을 제공 합니다.

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

이러한 매크로는 규칙 집합에 해당 하며 공백으로 구분 된 경고 번호 목록으로 확장 됩니다. 적절 한 pragma 구문을 사용 하 여 프로젝트 또는 코드 섹션에 대 한 유용한 규칙 집합을 구성할 수 있습니다. 다음 예제에서 코드 분석은 누락 된 상수 한정자에 대해서만 경고를 표시 합니다.

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>특성

Microsoft c + + 컴파일러는 특성을 제한적으로 지원 합니다 `[[gsl::suppress]]` . 함수 내에서 식 및 블록 문에 대 한 경고를 표시 하지 않는 데 사용할 수 있습니다.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppress-analysis-by-using-command-line-options"></a>명령줄 옵션을 사용 하 여 분석 표시 안 함

#Pragmas 대신 파일의 속성 페이지에서 명령줄 옵션을 사용 하 여 프로젝트 또는 단일 파일에 대 한 경고를 표시 하지 않을 수 있습니다. 예를 들어 파일에 대 한 경고 C26400를 사용 하지 않도록 설정 하려면 다음을 수행 합니다.

1. **솔루션 탐색기** 에서 파일을 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다.

1. **속성 페이지** 대화 상자에서 **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 편집 상자에서을 추가 *`/wd26400`* 합니다.

명령줄 옵션을 사용 하 여를 지정 하 여 파일에 대 한 모든 코드 분석을 일시적으로 사용 하지 않도록 설정할 수 있습니다 **`/analyze-`** . 나중에 코드 분석을 다시 사용 하도록 설정 하는 데 도움이 되는 ' */analyze-'로 '/analyze '를 재정의* 하는 경고 D9025 표시 됩니다.

## <a name="enable-the-c-core-guidelines-checker-on-specific-project-files"></a><a name="corecheck_per_file"></a> 특정 프로젝트 파일에 대 한 C++ Core Guidelines 검사기 사용

때로는 포커스가 있는 코드 분석을 수행 하 고 Visual Studio IDE를 계속 사용 하는 것이 유용한 경우가 있습니다. 규모가 많은 프로젝트에 대해 다음 샘플 시나리오를 수행해 보세요. 빌드 시간을 절약 하 고 결과를 더 쉽게 필터링 할 수 있습니다.

1. 명령 셸에서 `esp.extension` 및 `esp.annotationbuildlevel` 환경 변수를 설정 합니다.

1. 이러한 변수를 상속 하려면 명령 셸에서 Visual Studio를 엽니다.

1. 프로젝트를 로드 하 고 해당 속성을 엽니다.

1. 코드 분석을 사용 하도록 설정 하 고, 적절 한 규칙 집합을 선택 하지만 코드 분석 확장을 사용 하지 않습니다.

1. C++ Core Guidelines 검사기를 사용 하 여 분석 하려는 파일로 이동 하 여 해당 속성을 엽니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄**  >  **추가 옵션** 을 선택 하 고 추가 합니다.*`/analyze:plugin EspXEngine.dll`*

1. 미리 컴파일된 헤더를 사용 하지 않도록 설정 합니다 (**구성 속성**  >  **C/c + +**  >  **미리 컴파일된 헤더**). 확장 엔진이 미리 컴파일된 헤더 (PCH)에서 내부 정보를 읽으려고 할 수 있기 때문에이 작업이 필요 합니다. PCH가 기본 프로젝트 옵션을 사용 하 여 컴파일된 경우에는 호환 되지 않습니다.

1. 프로젝트를 다시 빌드합니다. 모든 파일에서 일반적인 PREFast 검사를 실행 해야 합니다. C++ Core Guidelines 검사기는 기본적으로 사용 하도록 설정 되어 있지 않으므로이를 사용 하도록 구성 된 파일 에서만 실행 해야 합니다.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Visual Studio 외부에서 C++ Core Guidelines 검사기를 사용 하는 방법

자동화 된 빌드에서 C++ Core Guidelines 체크를 사용할 수 있습니다.

### <a name="msbuild"></a>MSBuild

네이티브 코드 분석 검사기 (PREfast)는 사용자 지정 대상 파일을 통해 MSBuild 환경에 통합 됩니다. 프로젝트 속성을 사용 하 여 사용 하도록 설정 하 고 PREfast을 기반으로 하는 C++ Core Guidelines 검사기를 추가할 수 있습니다.

```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

파일을 가져오기 전에 이러한 속성을 추가 해야 *`Microsoft.Cpp.targets`* 합니다. 특정 규칙 집합을 선택 하거나 사용자 지정 규칙 집합을 만들 수 있습니다. 또는 다른 PREfast 검사를 포함 하는 기본 규칙 집합을 사용 합니다.

지정 된 파일 에서만 c + + Core 검사기를 실행할 수 있습니다. [앞에서 설명한](#corecheck_per_file)것과 동일한 방법을 사용 하지만 MSBuild 파일을 사용 합니다. 다음 항목을 사용 하 여 환경 변수를 설정할 수 있습니다 `BuildMacro` .

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

프로젝트 파일을 수정 하지 않으려는 경우 명령줄에서 속성을 전달할 수 있습니다.

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>비 MSBuild 프로젝트

MSBuild를 사용 하지 않는 빌드 시스템을 사용 하는 경우에도 검사기를 실행할 수 있습니다. 이를 사용 하려면 코드 분석 엔진 구성의 일부 내부에 대해 잘 알고 있어야 합니다. 이후 버전의 Visual Studio에서는 이러한 내부 지원을 보장 하지 않습니다.

코드 분석에는 몇 가지 환경 변수와 컴파일러 명령줄 옵션이 필요 합니다. 컴파일러에 대 한 특정 경로, 포함 디렉터리 등을 검색할 필요가 없도록 **Native Tools 명령 프롬프트** 환경을 사용 하는 것이 좋습니다.

- **환경 변수**
  - `set esp.extensions=cppcorecheck.dll` 그러면 엔진에 C++ Core Guidelines 모듈을 로드 하 라는 메시지가 나타납니다.
  - `set esp.annotationbuildlevel=ignore` 이렇게 하면 SAL 주석을 처리 하는 논리를 사용할 수 없습니다. 주석은 C++ Core Guidelines 검사기의 코드 분석에 영향을 주지 않지만 처리 시간이 오래 걸릴 수도 있습니다. 이 설정은 선택 사항 이지만 매우 권장 됩니다.
  - `set caexcludepath=%include%` 표준 헤더에서 발생 하는 경고를 사용 하지 않도록 설정 하는 것이 좋습니다. 여기에 경로를 더 추가할 수 있습니다. 예를 들어 프로젝트의 공용 헤더에 대 한 경로를 추가할 수 있습니다.

- **명령줄 옵션**
  - **`/analyze`**  코드 분석을 사용 하도록 설정 합니다 (및도 사용 **`/analyze:only`** **`/analyze:quiet`** ).
  - **`/analyze:plugin EspXEngine.dll`** 이 옵션은 PREfast 코드 분석 확장 엔진을 로드 합니다. 이 엔진은 C++ Core Guidelines 검사기를 차례로 로드 합니다.

## <a name="use-the-guideline-support-library"></a>지침 지원 라이브러리 사용

GSL (지침 지원 라이브러리)은 핵심 지침을 따르는 데 도움이 되도록 설계 되었습니다. GSL에는 오류가 발생 하기 쉬운 구문을 보다 안전한 대체 항목으로 바꿀 수 있는 정의가 포함 되어 있습니다. 예를 들어 `T*, length` 매개 변수 쌍을 형식으로 바꿀 수 있습니다 `span<T>` . GSL 프로젝트는 GitHub에서 사용할 수 있습니다 [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) . 라이브러리는 오픈 소스 이므로 소스를 보거나 의견을 올리거나 참가할 수 있습니다. [Vcpkg](../build/vcpkg.md) 패키지 관리자를 사용 하 여 라이브러리를 로컬로 다운로드 하 고 설치할 수도 있습니다.

::: moniker range="msvc-140"

## <a name="use-the-c-core-check-guidelines-in-visual-studio-2015-projects"></a><a name="vs2015_corecheck"></a> Visual Studio 2015 프로젝트의 C++ Core Check 지침 사용

Visual Studio 2015을 사용 하는 경우 C++ Core Check 코드 분석 규칙 집합은 기본적으로 설치 되지 않습니다. Visual Studio 2015에서 C++ Core Check 코드 분석 도구를 사용 하도록 설정 하기 전에 추가 단계가 필요 합니다. Microsoft에서는 NuGet 패키지를 사용 하 여 Visual Studio 2015 프로젝트에 대 한 지원을 제공 합니다. 패키지 이름은 CppCoreCheck입니다 .이 패키지는에서 사용할 수 있습니다 [http://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck) . 이 패키지에는 Visual Studio 2015 이상 업데이트 1이 설치 되어 있어야 합니다.

또한 패키지는 다른 패키지를 종속성으로 설치 합니다. GSL (헤더 전용 지침 지원 라이브러리). GSL는 GitHub 에서도 사용할 수 있습니다 [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .

Visual Studio 2015 내에서 코드 분석 규칙이 로드 되는 방식 때문에 `Microsoft.CppCoreCheck` 확인 하려는 각 c + + 프로젝트에 NuGet 패키지를 설치 해야 합니다.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Visual Studio 2015에서 프로젝트에 CppCoreCheck 패키지를 추가 하려면

1. **솔루션 탐색기** 에서 패키지를 추가 하려는 솔루션의 프로젝트에 대 한 상황에 맞는 메뉴를 마우스 오른쪽 단추로 클릭 하 여 엽니다. Nuget 패키지 **관리** 를 선택 하 여 **nuget 패키지 관리자** 를 엽니다.

1. **NuGet 패키지 관리자** 창에서 CppCoreCheck를 검색 합니다.

    ![Nuget 패키지 관리자 창에 CppCoreCheck 패키지 표시](../code-quality/media/cppcorecheck_nuget_window.png)

1. CppCoreCheck 패키지를 선택한 후 **설치** 단추를 선택 하 여 프로젝트에 규칙을 추가 합니다.

   NuGet 패키지는 *`.targets`* 프로젝트에 대해 코드 분석을 사용 하도록 설정할 때 호출 되는 추가 MSBuild 파일을 프로젝트에 추가 합니다. 이 *`.targets`* 파일은 Visual Studio code analysis tool의 추가 확장으로 C++ Core Check 규칙을 추가 합니다. 패키지가 설치 될 때 속성 페이지 대화 상자를 사용 하 여 해제 된 및 실험적 규칙을 사용 하거나 사용 하지 않도록 설정할 수 있습니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

- [Visual Studio C++ Core Check 참조](code-analysis-for-cpp-corecheck.md)
