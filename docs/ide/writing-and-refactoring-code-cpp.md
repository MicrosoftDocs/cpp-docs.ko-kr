---
title: Visual Studio에서 C++ 코드 편집 및 리팩터링
description: Visual Studio의 C++ 코드 편집기를 사용하여 코드를 서식 지정, 탐색, 이해 및 리팩터링합니다.
ms.date: 05/31/2019
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.topic: overview
ms.openlocfilehash: bf34bf39bc41841be72c9400ec63c501d7aa56a3
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686334"
---
# <a name="edit-and-refactor-c-code-in-visual-studio"></a>Visual Studio에서 C++ 코드 편집 및 리팩터링

Visual Studio는 코드를 작성, 편집 및 리팩터링할 수 있는 여러 도구를 제공합니다.

## <a name="intellisense"></a>IntelliSense

IntelliSense는 사용자가 입력하면 그에 따라 기호 및 코드 조각을 제안하는 강력한 코드 완성 도구입니다. Visual Studio의 C++ IntelliSense는 실시간으로 실행되며, 사용자가 코드 베이스를 업데이트하면 그것을 분석하여 추천을 제공합니다. 사용자가 더 많은 문자를 입력하면 추천 결과 목록이 좁혀집니다.

![C&#43;&#43; 멤버 목록 드롭다운](../ide/media/cpp-statement-completion.png)

일부 기호는 결과 범위를 좁히기 위해 자동으로 생략됩니다. 예를 들어 클래스 외부에서 클래스 개체의 멤버에 액세스할 때에는 기본적으로 프라이빗 멤버 또는 보호된 멤버(자식 클래스 컨텍스트에 있지 않은 경우)를 볼 수 없습니다. 하단의 단추를 사용하여 필터링을 조정할 수 있습니다.

드롭다운 목록에서 기호를 선택한 후에는 **Tab**, **Enter** 또는 다른 커밋 문자 중 하나로 기호를 자동 완성할 수 있습니다(기본적으로 `{ } [ ] ( ) . , : ; + - * / % & | ^ ! = ? @ # \`). 이 목록에서 문자를 추가 또는 제거하려면 **빠른 실행**(Ctrl + Q)에서 "IntelliSense"를 검색하고 **텍스트 편집기 > C/C++ > 고급** 옵션을 선택합니다. **멤버 목록 커밋 문자** 옵션을 사용하면 목록을 원하는 대로 변경하여 사용자 지정할 수 있습니다.

**멤버 목록 필터 모드** 옵션은 표시할 IntelliSense 자동 완성 제안의 종류를 제어합니다. 기본적으로 **유사 항목**으로 설정됩니다. 유사 항목 검색에서는 *MyAwesomeClass*라는 기호가 있는 경우 "MAC"를 입력하고 자동 완성 제안에서 해당 클래스를 찾을 수 있습니다. 유사 항목 알고리즘은 기호가 목록에 표시되려면 충족해야 하는 최소 임계값을 설정합니다. **스마트** 필터링은 사용자가 입력한 내용과 일치하는 부분 문자열이 포함된 모든 기호를 표시합니다. **접두사** 필터링은 사용자가 입력한 문자로 시작되는 문자열을 검색합니다.

C++ IntelliSense에 대한 자세한 내용은 [Visual C++ IntelliSense](/visualstudio/ide/visual-cpp-intellisense) 및 [IntelliSense에 대한 C++ 프로젝트 구성](/visualstudio/ide/visual-cpp-intellisense-configuration)을 참조하세요.

## <a name="intellicode"></a>IntelliCode

IntelliCode는 AI의 도움을 받을 수 있는 IntelliSense입니다. 완성 목록에 사용될 가능성이 가장 높은 후보입니다. IntelliCode 추천은 각각 100개가 넘는 별을 받은 GitHub의 오픈 소스 프로젝트를 기반으로 합니다. 코드의 컨텍스트와 결합하면 완성 목록을 원하는 대로 구성하여 일반적인 사례의 수준을 높일 수 있습니다.

C++을 작성하는 경우 IntelliCode는 표준 라이브러리처럼 인기 있는 라이브러리를 사용할 때 도움이 됩니다. 코드의 컨텍스트는 무엇보다도 가장 유용한 추천을 제공하기 위해 사용됩니다. 다음 예제의 `size` 멤버 함수는 일반적으로 `sort` 함수와 함께 사용되므로 결과 목록의 맨 위에 표시됩니다.

![C&#43;&#43; IntelliCode](../ide/media/intellicode-cpp.png "C++ IntelliCode")

::: moniker range="vs-2019"

Visual Studio 2019에서는 IntelliCode가 **C++ 데스크톱 개발** 워크로드의 선택적 구성 요소로 제공됩니다. IntelliCode가 C++에 대해 활성화되었는지 확인하려면 **도구** > **옵션** > **IntelliCode** > **일반**으로 이동하여 **C++ 기본 모델**을 **사용**으로 설정합니다.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017에서는 IntelliCode가 Visual Studio Marketplace에 확장으로 제공됩니다.

::: moniker-end

## <a name="predictive-intellisense-experimental"></a>예측 IntelliSense(실험적)

**예측 IntelliSense**는 컨텍스트 인식 기능을 사용하여 IntelliSense 드롭다운 목록에 표시되는 결과의 수를 제한하는 실험적 기능입니다. 이 알고리즘은 형식 일치를 적용하여 예상 형식과 일치하는 결과만 표시합니다. 간단한 예를 들자면, `int x =`을 입력하고 IntelliSense 드롭다운을 호출하면 정수 또는 정수를 반환하는 함수만 표시됩니다. 이 기능은 아직 개발 중이기 때문에 기본적으로 해제되어 있습니다. 이 기능이 가장 잘 작동하는 것은 글로벌 기호이며, 멤버 함수는 아직 지원되지 않습니다. **빠른 실행**에 "예측"을 입력하거나 **도구** > **옵션** > **텍스트 편집기** > **C/C++**  > **실험적** > **예측 IntelliSense 사용**으로 이동하여 이 기능을 켤 수 있습니다.

**예측 IntelliSense**를 재정의하고 더 긴 목록을 표시하려면 **Ctrl + J**를 누릅니다. **예측 IntelliSense**가 켜져 있는 경우 **Ctrl + J**를 누르면 예측 필터가 제거됩니다. **Ctrl + J**를 다시 누르면 관련된 멤버 목록 결과에서 내게 필요한 옵션 필터가 제거됩니다. IntelliSense 드롭다운 목록 아래의 ([+]) 단추는 **Ctrl + J**와 똑같은 방식으로 작동합니다. 마우스 커서를 단추 위로 이동하면 현재 표시되는 항목의 도구 설명 정보를 볼 수 있습니다.

![C&#43;&#43; 예측 IntelliSense](../ide/media/predictive-intellisense-cpp.png "예측 IntelliSense")

이전 스크린샷은 드롭다운 목록 아래에 있는 여러 단추를 보여줍니다. 이러한 단추를 통해 다양한 종류의 결과에 IntelliSense 필터를 사용할 수 있습니다.

- 변수와 상수
- 함수
- 유형
- 매크로
- 열거형
- 네임스페이스

단추는 현재 IntelliSense 세션과 관련이 있는 경우에만 표시됩니다. 일반적으로 일부 단추만 표시됩니다.

## <a name="template-intellisense"></a>템플릿 IntelliSense

템플릿 정의 내에 캐럿이 있는 경우 IntelliSense의 샘플 템플릿 인수를 제공할 수 있는 **템플릿 표시줄**이 나타납니다.

![C&#43;&#43; 템플릿 IntelliSense에서 기존 인스턴스화 표시](../ide/media/template-intellisense-cpp-1.png "템플릿 IntelliSense에서 기존 인스턴스화 표시")

**\<T>** 아이콘을 클릭하면 **템플릿 표시줄**이 확장/축소됩니다. 연필 아이콘을 클릭하거나 **템플릿 표시줄**을 두 번 클릭하면 **편집** 창이 열립니다.

![C&#43;&#43; 템플릿 IntelliSense](../ide/media/template-intellisense-cpp-3.png "템플릿 IntelliSense")

이 창에서 편집하는 내용은 소스 코드에 바로 적용되므로 편집 효과를 실시간으로 확인할 수 있습니다.

템플릿 표시줄은 코드의 인스턴스화에 따라 후보를 자동으로 채울 수 있습니다. **모든 기존 인스턴스화 추가**를 클릭하면 코드 베이스 전체에서 템플릿 인스턴스화에 사용된 모든 구체적 인수 목록을 볼 수 있습니다.

![C&#43;&#43; 템플릿 IntelliSense 결과 목록](../ide/media/template-intellisense-cpp-2.png "템플릿 IntelliSense 결과 목록")

편집기 하단의 창은 각 인스턴스화가 발견된 위치 및 해당 인수를 보여줍니다.

![C&#43;&#43; 템플릿 IntelliSense 인스턴스화 맵](../ide/media/template-intellisense-cpp-4.png "템플릿 IntelliSense 인스턴스화 맵")

**템플릿 표시줄** 정보는 사용자별로 처리됩니다. .vs 폴더에 저장되며 소스 제어에 커밋되지 않습니다.

## <a name="error-squiggles-and-quick-fixes"></a>오류 표시선 및 빠른 수정

편집기는 코드에서 문제를 발견하면 해당 문제 아래에 색이 있는 오류 표시선을 추가합니다. 빨간색 오류 표시선은 컴파일되지 않는 코드를 나타냅니다. 녹색 오류 표시선은 중대한 오류일 수도 있는 다른 종류의 문제를 나타냅니다. **오류 목록** 창을 열면 문제에 대한 자세한 정보를 볼 수 있습니다.

일부 오류와 일반적인 코딩 패턴의 경우 편집기에서 오류 표시선 위로 마우스 커서를 이동하면 전구 모양의 형태로 **빠른 수정**이 제공됩니다. 아래쪽 화살표를 클릭하면 제안 사항을 볼 수 있습니다.

다음 예제에서는 `vector`가 선언되었지만 정의를 찾을 수 없으므로 편집기는 다음과 같은 필요한 헤더 파일을 포함할 것을 제안합니다.

![오류 표시선과 편집기가 제공하는 빠른 수정을 보여 주는 스크린샷](../ide/media/quick-fix-for-header-cpp.png "C++ 빠른 수정")

또한 편집기는 일부 리팩터링 기회에 빠른 픽스를 제공합니다. 예를 들어 헤더 파일에서 클래스를 선언하면 Visual Studio는 별도의 .cpp 파일에 해당 클래스에 대한 정의를 만들 것을 제안합니다.

![channel.cpp 옵션에서 채널의 채널 경로 반복기 정의 만들기가 강조 표시된 빠른 수정을 보여 주는 스크린샷](../ide/media/quick-fix.png "C++ 빠른 수정")

## <a name="change-tracking"></a>Change tracking

사용자가 파일을 변경할 때마다 저장되지 않은 변경 내용이 있음을 나타내는 노란색 표시줄이 왼쪽에 표시됩니다. 파일을 저장하면 표시줄이 녹색으로 바뀝니다. 녹색 및 노란색 표시줄은 문서가 편집기에서 열려 있는 동안 유지됩니다. 이러한 표시줄은 사용자가 마지막으로 문서를 연 이후에 변경한 내용을 나타냅니다.

![C&#43;&#43; 변경 내용 추적](../ide/media/change-tracking-cpp.png "Change tracking")

## <a name="move-code"></a>코드 이동

코드를 선택하고, Alt 키를 누른 상태에서 **위쪽/아래쪽** 화살표 키를 눌러 코드 줄을 위아래로 이동할 수 있습니다.

## <a name="insert-snippets"></a>코드 조각 삽입

코드 조각은 소스 코드의 미리 정의된 조각입니다. 단일 지점이나 선택한 텍스트를 마우스 오른쪽 단추로 클릭하여 코드 조각을 삽입하거나 선택한 텍스트를 코드 조각으로 둘러쌉니다. 다음 그림에서는 선택한 문을 for 루프로 둘러싸는 세 단계를 보여 줍니다. 최종 이미지의 노란색 강조 표시는 tab 키를 사용하여 액세스하는 편집 가능한 필드입니다. 자세한 내용은 [코드 조각](/visualstudio/ide/code-snippets)을 참조하세요.

![C&#43;&#43; 코드 조각 삽입 드롭다운&#45;](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

## <a name="add-class"></a>클래스 추가

**프로젝트** 메뉴 또는 **솔루션 탐색기**의 팝업 메뉴에서 새 클래스를 추가합니다.

![C에 새 클래스 추가&#43;&#43;](../ide/media/vs2017-add-class.png "vs2015_cpp_add_class")

기존 클래스를 수정하거나 검사하려면 클래스 마법사를 사용할 수도 있습니다.

![C&#43;&#43; 클래스 마법사](../ide/media/vs2017-class-wizard.png)

자세한 내용은 [코드 마법사로 기능 추가(C++)](../ide/adding-functionality-with-code-wizards-cpp.md)를 참조하세요.

## <a name="refactoring"></a>리팩터링

리팩터링은 빠른 작업 상황에 맞는 메뉴 아래에서 또는 편집기에서 [전구](/visualstudio/ide/perform-quick-actions-with-light-bulbs)를 클릭하여 사용할 수 있습니다.  일부는 **편집 > 리팩터링** 메뉴에 있습니다.  이러한 기능에는 다음이 포함됩니다.

- [이름 바꾸기](refactoring/rename.md)
- [함수 추출](refactoring/extract-function.md)
- [순수 가상 구현](refactoring/implement-pure-virtuals.md)
- [선언/정의 만들기](refactoring/create-declaration-definition.md)
- [함수 정의 이동](refactoring/move-definition-location.md)
- [원시 문자열 리터럴로 변환](refactoring/convert-to-raw-string-literal.md)
- [시그니처 변경](refactoring/change-signature.md)

## <a name="code-style-enforcement-with-clangformat-and-editorconfig"></a>ClangFormat 및 EditorConfig를 사용하여 코드 스타일 적용

Visual Studio 2017 이상부터는 Clang/LLVM 기반의 인기 있는 C++용 코드 서식 지정 유틸리티인 [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html)을 기본적으로 지원합니다. [빠른 실행](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box)에 "ClangFormat"을 입력하고 다음과 같은 일반 형식 중 하나를 사용하도록 설정합니다.

- LLVM
- Google
- Chromium
- Mozilla
- WebKit
- Visual Studio

동일한 수준 또는 하위 수준에서 모든 코드에 사용자 지정 규칙을 적용하는 사용자 고유의 .clang-format 또는 _clang-format 파일을 제공할 수도 있습니다.

이러한 파일은 소스 제어를 통해 쉽게 공유할 수 있으므로, 개발 팀 전체에 코딩 규칙을 적용할 수 있습니다.

![C&#43;&#43; Clang 형식](../ide/media/clang-format-cpp.png "Clang 형식")

Visual Studio 2017 이상부터는 비슷한 방식으로 작동하는 [EditorConfig](https://editorconfig.org/)도 지원합니다. 하지만 ClangFormat은 C++와 관련된 규칙을 포함하여 EditorConfig보다 많은 스타일 옵션을 제공합니다. **EditorConfig**로 **.editorconfig** 파일을 만들어서 데이터베이스의 여러 폴더에 배치하는 방법으로 해당 폴더와 그 하위 폴더의 코드 스타일을 지정할 수 있습니다. **.editorconfig** 파일은 부모 폴더의 다른 **.editorconfig** 파일을 대체하고 **도구** > **옵션**을 통해 구성된 서식 설정을 덮어씁니다. 탭과 공간, 들여쓰기 크기 등에 대한 규칙을 설정할 수 있습니다. 자세한 내용은 [EditorConfig를 사용하여 휴대용, 사용자 지정 편집기 설정 만들기](/visualstudio/ide/create-portable-custom-editor-options)를 참조하세요.

## <a name="other-formatting-options"></a>다른 서식 지정 옵션

**빠른 실행** 검색 상자는 설정 또는 도구를 찾는 가장 빠른 방법을 제공합니다. 이 방법은 주 메뉴에 있습니다. 입력을 시작하면 자동 완성 목록이 결과를 필터링합니다.

![Visual Studio 빠른 실행](../ide/media/vs2015_cpp_quick_launch.png "빠른 실행")

들여쓰기, 중괄호 완성, 색 지정과 같은 서식 지정 옵션을 설정하려면 **빠른 실행** 창에 "C++ 서식 지정"을 입력합니다.

![C++ 서식 지정 옵션](media/cpp-formatting-options.png)

다른 서식 지정 옵션은 주 메뉴의 **편집** > **고급** 아래에서 찾을 수 있습니다.

![C++ 고급 편집 옵션](media/edit-advanced-cpp.png)

C++ 관련 편집 기능을 사용하고 구성하기 위한 옵션은 **도구** > **옵션** > **텍스트 편집기** > **C/C++** 에 있습니다. 설정하려는 옵션을 선택한 후 대화 상자에 초점이 맞춰져 있을 때 **F1** 키를 누르면 추가 도움말을 확인할 수 있습니다. 일반적인 코드 서식 지정 옵션은 **빠른 실행**에 `Editor C++`을 입력합니다.

![Visual Studio Tools > 옵션](../ide/media/tools-options.png "편집기 옵션")

향후 버전의 Visual Studio에 포함될 수도 포함되지 않을 수 있는 실험적 기능은 [텍스트 편집기 C++ 실험적](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental) 대화 상자에 있습니다. Visual Studio 2017 이상에서는 이 대화 상자에서 **예측 IntelliSense**를 사용하도록 설정할 수 있습니다.

## <a name="see-also"></a>관련 항목

[C++ 코드 읽기 및 이해](read-and-understand-code-cpp.md)</br>
[Visual Studio에서 C++ 코드 베이스 탐색](navigate-code-cpp.md)</br>
[C++용 Live Share를 사용하여 협업](live-share-cpp.md)
