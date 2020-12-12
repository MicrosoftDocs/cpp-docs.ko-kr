---
description: '자세히 알아보기: 힌트 파일'
title: 힌트 파일
ms.date: 02/26/2019
f1_keywords:
- cpp.hint
- vc.hint.file
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
ms.openlocfilehash: b9dc4655bde832011afcf03aa7f9a5be34807420
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191656"
---
# <a name="hint-files"></a>힌트 파일

*힌트 파일* 에는 C++ 검색 데이터베이스 파서가 코드 영역을 건너뛰도록 하는 매크로가 포함됩니다. Visual Studio C++ 프로젝트를 열면 파서가 프로젝트의 각 소스 파일에 있는 코드를 분석하고 모든 식별자에 대한 정보로 데이터베이스를 빌드합니다. IDE는 해당 정보를 사용하여 **클래스 뷰** 브라우저 및 **탐색 모음** 과 같은 코드 검색 기능을 지원합니다.

C++ 검색 데이터베이스 파서는 짧은 시간 내에 많은 양의 코드를 구문 분석할 수 있는 유사 파서입니다. 이 파서는 블록의 내용을 건너뛰기 때문에 빠릅니다. 예를 들어 함수의 매개 변수와 위치만 기록하고 그 내용은 무시합니다. 일부 매크로는 블록의 시작과 끝을 확인하는 데 사용된 추론에 대한 문제를 일으킬 수 있습니다. 이러한 문제로 인해 코드 영역이 잘못 기록됩니다.

이렇게 건너뛴 영역은 여러 방법으로 나타낼 수 있습니다.

- **클래스 뷰**, **이동** 및 **탐색 모음** 에서 누락된 형식 및 함수

- **탐색 모음** 에서 잘못된 범위

- 이미 정의된 함수에 대한 **선언/정의 만들기** 제안

힌트 파일에는 C/C++ 매크로 정의와 동일한 구문이 있는 사용자 지정 가능 힌트가 포함되어 있습니다. Visual C++는 대부분의 프로젝트에 충분한 기본 제공 힌트 파일을 포함합니다. 그러나 특별히 자신의 프로젝트에 맞게 파서를 개선하기 위해 사용자 고유의 힌트 파일을 만들 수 있습니다.

> [!IMPORTANT]
> 힌트 파일을 수정 또는 추가하는 경우 변경 내용을 적용하려면 추가 단계를 수행해야 합니다.
>
> - Visual Studio 2017 버전 15.6 이전 버전에서: 모든 변경 내용에 대해 솔루션에서 .sdf 파일 및/또는 VC db 파일을 삭제 합니다.
> - Visual Studio 2017 버전 15.6 이상: 새 힌트 파일을 추가한 후 솔루션을 닫았다가 다시 엽니다.

## <a name="scenario"></a>시나리오

```cpp
#define NOEXCEPT noexcept
void Function() NOEXCEPT
{
}
```

힌트 파일이 없으면 `Function`은 **클래스 뷰**, **이동** 또는 **탐색 모음** 에 표시되지 않습니다. 이 매크로 정의와 함께 힌트 파일을 추가하면 파서가 이를 이해하고 `NOEXCEPT` 매크로를 대체하여 함수를 올바르게 구문 분석할 수 있습니다.

```cpp.hint
#define NOEXCEPT
```

## <a name="disruptive-macros"></a>방해가 되는 매크로

파서를 방해하는 두 가지 범주의 매크로가 있습니다.

- 함수를 표시하는 키워드를 캡슐화하는 매크로

   ```cpp
   #define NOEXCEPT noexcept
   #define STDMETHODCALLTYPE __stdcall
   ```

   이러한 유형의 매크로는 힌트 파일에 매크로 이름만 필요합니다.

   ```cpp.hint
   #define NOEXCEPT
   #define STDMETHODCALLTYPE
   ```

- 짝이 맞지 않는 대괄호를 포함하는 매크로

   ```cpp
   #define BEGIN {
   ```

   이러한 유형의 매크로는 힌트 파일에 매크로 이름과 해당 내용이 필요합니다.

   ```cpp.hint
   #define BEGIN {
   ```

## <a name="editor-support"></a>편집기 지원

Visual Studio 2017 버전 15.8부터 방해가 되는 매크로를 식별할 수 있는 여러 가지 기능이 제공됩니다.

- 파서가 건너뛴 영역 내부의 매크로는 강조 표시됩니다.

- 빠른 작업을 통해 강조 표시된 매크로를 포함하는 힌트 파일을 만들거나 기존 힌트 파일이 있는 경우 해당 매크로를 힌트 파일에 추가합니다.

![강조 표시 된 매크로.](media/hint-squiggle-and-actions.png "힌트 물결선 및 빠른 작업")

빠른 작업 중 하나를 실행하면 파서가 힌트 파일에 의해 영향을 받는 파일을 다시 구문 분석합니다.

기본적으로 문제 매크로는 제안으로 강조 표시됩니다. 강조 표시는 빨간색 또는 녹색 오류 표시선처럼 보다 눈에 띄는 것으로 변경할 수 있습니다. **도구** > **옵션** > **텍스트 편집기** > **C/C++** > **보기** 아래 **코드 오류 표시선** 섹션에서 **Macros in Skipped Browsing Regions**(건너뛴 검색 영역의 매크로) 옵션을 사용합니다.

![건너뛴 검색 영역 옵션의 매크로](media/skipped-regions-squiggle-option.png "건너뛴 영역 물결선 옵션입니다.")

## <a name="display-browsing-database-errors"></a>검색 데이터베이스 오류 표시

**프로젝트**  >  **표시 검색 데이터베이스 오류** 메뉴 명령은 **오류 목록** 구문 분석에 실패 한 모든 지역을 표시 합니다. 이 명령은 초기 힌트 파일의 작성을 간소화하기 위해 것입니다. 그러나 파서는 문제의 원인이 방해가 되는 매크로인지 알릴 수 없으므로 사용자가 각 오류를 평가해야 합니다. **검색 데이터베이스 오류 표시** 명령을 실행하고 각 오류로 이동하여 편집기에서 영향을 받는 파일을 로드합니다. 파일이 로드된 후에는 매크로가 영역 내에 있는 경우 강조 표시됩니다. 빠른 작업을 호출하여 매크로를 힌트 파일에 추가할 수 있습니다. 힌트 파일을 업데이트하면 오류 목록이 자동으로 업데이트됩니다. 또는, 힌트 파일을 수동으로 수정하는 경우 **솔루션 다시 검색** 명령을 사용하여 업데이트를 트리거할 수 있습니다.

## <a name="architecture"></a>Architecture

힌트 파일은 **솔루션 탐색기** 에 표시된 논리 디렉터리가 아니라 실제 디렉터리와 관련됩니다. 힌트 파일을 적용하기 위해 프로젝트에 힌트 파일을 추가할 필요가 없습니다. 구문 분석 시스템은 소스 파일을 구문 분석할 때만 힌트 파일을 사용합니다.

모든 힌트 파일의 이름은 **cpp.hint** 입니다. 많은 디렉터리에 힌트 파일이 포함될 수 있지만, 특정 디렉터리에는 하나의 힌트 파일만 있을 수 있습니다.

프로젝트는 0개 이상의 힌트 파일의 영향을 받을 수 있습니다. 힌트 파일이 없으면 구문 분석 시스템에서 오류 복구 기술을 사용하여 해독할 수 없는 소스 코드를 무시합니다. 그렇지 않으면 구문 분석 시스템에서 다음 전략을 사용하여 힌트를 찾고 수집합니다.

### <a name="search-order"></a>검색 순서

구문 분석 시스템에서 다음 순서로 디렉터리를 검색하여 힌트 파일을 찾습니다.

- Visual C++용 설치 패키지(**vcpackages**)가 있는 디렉터리입니다. 이 디렉터리에는 자주 사용되는 시스템 파일의 기호를 설명하는 기본 제공 힌트 파일(예: **windows.h**)이 포함되어 있습니다. 따라서 프로젝트에서 필요한 대부분의 힌트를 자동으로 상속받습니다.

- 소스 파일의 루트 디렉터리에서 소스 파일 자체가 포함된 디렉터리로의 경로입니다. 일반적인 Visual Studio C++ 프로젝트의 경우 루트 디렉터리에 솔루션 또는 프로젝트 파일이 포함되어 있습니다.

   이 규칙의 예외는 *중지 파일* 이 소스 파일의 경로에 있는 경우입니다. 중지 파일은 이름이 **cpp.stop** 인 모든 파일입니다. 중지 파일은 검색 순서에 대한 추가 제어를 제공합니다. 구문 분석 시스템은 루트 디렉터리에서 시작하는 대신 중지 파일이 포함된 디렉터리에서 소스 파일이 있는 디렉터리로 검색합니다. 일반적인 프로젝트에서는 중지 파일이 필요하지 않습니다.

### <a name="hint-gathering"></a>힌트 수집

힌트 파일에는 0개 이상의 *힌트* 가 포함되어 있습니다. 힌트는 C/C++ 매크로와 동일하게 정의되거나 삭제됩니다. 즉 `#define` 전처리기 지시문에서 힌트를 만들거나 다시 정의하고, `#undef` 지시문에서 힌트를 삭제합니다.

구문 분석 시스템에서는 앞에서 설명한 검색 순서에 따라 각 힌트 파일을 엽니다. *효과적인 힌트* 집합에 각 파일의 힌트를 누적한 다음, 효과적인 힌트를 사용하여 코드의 식별자를 해석합니다.

구문 분석 시스템에서 힌트를 누적하기 위해 다음과 같은 규칙을 사용합니다.

- 새 힌트에서 아직 정의되지 않은 이름을 지정하는 경우 새 힌트에서 효과적인 힌트에 해당 이름을 추가합니다.

- 새 힌트에서 이미 정의된 이름을 지정하는 경우 새 힌트에서 기존 힌트를 다시 정의합니다.

- 새 힌트가 기존의 효과적인 힌트를 지정하는 `#undef` 지시문인 경우 새 힌트에서 기존 힌트를 삭제합니다.

첫 번째 규칙은 이전에 열었던 힌트 파일에서 효과적인 힌트가 상속된다는 것을 의미합니다. 마지막 두 규칙은 검색 순서에서 나중에 나오는 힌트가 이전의 힌트를 재정의할 수 있다는 것을 의미합니다. 예를 들어 소스 파일이 포함된 디렉터리에 힌트 파일을 만들면 모든 이전 힌트를 재정의할 수 있습니다.

힌트가 수집되는 방법을 알아보려면 [예제](#example) 섹션을 참조하세요.

### <a name="syntax"></a>Syntax

매크로를 만들고 삭제하는 전처리기 지시문과 동일한 구문을 사용하여 힌트를 만들고 삭제합니다. 실제로 구문 분석 시스템은 C/C++ 전처리기를 사용하여 힌트를 평가합니다. 전처리기 지시문에 대한 자세한 내용은 [#define 지시문(C/C++)](../../preprocessor/hash-define-directive-c-cpp.md) 및 [#undef 지시문(C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)을 참조하세요.

유일하게 특이한 구문 요소는 `@<`, `@=` 및 `@>` 대체 문자열입니다. 이러한 힌트 파일 특정 대체 문자열은 *맵* 매크로에만 사용됩니다. 맵은 데이터, 함수 또는 이벤트를 다른 데이터, 함수 또는 이벤트 처리기와 관련시키는 일단의 매크로입니다. 예를 들어 `MFC`는 맵을 사용하여 [메시지 맵](../../mfc/reference/message-maps-mfc.md)을 만들고, `ATL`은 맵을 사용하여 [개체 맵](../../atl/reference/object-map-macros.md)을 만듭니다. 힌트 파일 특정 대체 문자열은 맵의 시작, 중간 및 끝 요소를 표시합니다. 맵 매크로의 이름만 중요합니다. 따라서 각 대체 문자열은 의도적으로 매크로의 구현을 숨깁니다.

힌트는 다음 구문을 사용합니다.

|Syntax|의미|
|------------|-------------|
|`#define` *hint-name* *replacement-string*<br /><br /> `#define` *hint-name* `(` *parameter*, ...`)`*replacement-string*|새 힌트를 정의하거나 기존 힌트를 다시 정의하는 전처리기 지시문입니다. 지시문 뒤에 나오는 전처리기에서 소스 코드에 있는 *hint-name* 의 각 항목을 *replacement-string* 으로 바꿉니다.<br /><br /> 두 번째 구문 형식은 함수와 비슷한 힌트를 정의합니다. 소스 코드에서 함수와 비슷한 힌트가 발생하면 전처리기에서 *replacement-string* 의 각 *parameter* 를 소스 코드의 해당 인수로 바꾼 다음, *hint-name* 을 *replacement-string* 으로 바꿉니다.|
|`@<`|맵 요소 집합의 시작을 나타내는 힌트 파일 특정 *replacement-string* 입니다.|
|`@=`|중간 맵 요소를 나타내는 힌트 파일 특정 *replacement-string* 입니다. 맵에는 여러 개의 맵 요소가 있을 수 있습니다.|
|`@>`|맵 요소 집합의 끝을 나타내는 힌트 파일 특정 *replacement-string* 입니다.|
|`#undef` *hint-name*|기존 힌트를 삭제하는 전처리기 지시문입니다. 힌트의 이름은 *hint-name* 식별자로 제공됩니다.|
|`//`*설명*|한 줄 주석문입니다.|
|`/*` *comment* `*/`|여러 줄 주석입니다.|

## <a name="example"></a>예제

이 예제에서는 힌트 파일에서 힌트가 누적되는 방법을 보여 줍니다. 중지 파일은 이 예제에서 사용되지 않습니다.

그림에서는 Visual Studio C++ 프로젝트의 실제 디렉터리 중 일부를 보여 줍니다. `vcpackages`, `Debug`, `A1` 및 `A2` 디렉터리에 힌트 파일이 있습니다.

### <a name="hint-file-directories"></a>힌트 파일 디렉터리

![Common 및 project&#45;특정 힌트 파일 디렉터리입니다.](media/hintfile.png "HintFile")

### <a name="directories-and-hint-file-contents"></a>디렉터리 및 힌트 파일 내용

이 목록에서는 이 프로젝트에서 힌트 파일이 포함된 디렉터리와 해당 힌트 파일의 내용을 보여 줍니다. `vcpackages` 디렉터리 힌트 파일의 많은 힌트 중 일부만 나열됩니다.

- vcpackages

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    ```

- 디버그

    ```cpp.hint
    // Debug
    #undef _In_
    #define OBRACE {
    #define CBRACE }
    #define RAISE_EXCEPTION(x) throw (x)
    #define START_NAMESPACE namespace MyProject {
    #define END_NAMESPACE }
    ```

- A1

    ```cpp.hint
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    ```

- A2

    ```cpp.hint
    // A2
    #undef OBRACE
    #undef CBRACE
    ```

### <a name="effective-hints"></a>효과적인 힌트

이 표에는 이 프로젝트의 소스 파일에 대한 효과적인 힌트가 나와 있습니다.

- 소스 파일: A1_A2_B.cpp

- 효과적인 힌트:

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    // Debug...
    #define RAISE_EXCEPTION(x) throw (x)
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    // ...Debug
    #define END_NAMESPACE }
    ```

위의 목록에 적용되는 참고 사항은 다음과 같습니다.

- 효과적인 힌트는 `vcpackages`, `Debug`, `A1` 및 `A2` 디렉터리에 있습니다.

- `Debug` 힌트 파일의 **#undef** 지시문은 `vcpackages` 디렉터리 힌트 파일에서 `#define _In_` 힌트를 제거했습니다.

- `A1` 디렉터리의 힌트 파일은 `START_NAMESPACE`를 다시 정의합니다.

- `A2` 디렉터리의 `#undef` 힌트에서 `Debug` 디렉터리 힌트 파일의 `OBRACE` 및 `CBRACE`에 대한 힌트를 제거했습니다.

## <a name="see-also"></a>참고 항목

[Visual Studio C++ 프로젝트용으로 만든 파일 형식](file-types-created-for-visual-cpp-projects.md)<br>
[#define 지시문 (C/c + +)](../../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef 지시문 (C/c + +)](../../preprocessor/hash-undef-directive-c-cpp.md)<br>
[SAL 주석](../../c-runtime-library/sal-annotations.md)<br>
