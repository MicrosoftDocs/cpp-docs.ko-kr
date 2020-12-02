---
title: Visual Studio에서 C++ 코드 읽기 및 이해
description: Visual Studio의 C++ 코드 편집기를 사용하여 코드를 서식 지정하고, 이해합니다.
ms.date: 05/28/2019
ms.openlocfilehash: cd152ffbbd106c6a31a21da35d08b53555047209
ms.sourcegitcommit: 6284bca6549e7b4f199d4560c30df6c1278bd4a0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96188902"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Visual Studio에서 C++ 코드 읽기 및 이해

C++ 코드 편집기 및 Visual Studio IDE에서는 많은 코딩 보조 기능을 제공합니다. 일부는 C++에 고유하고, 일부는 기본적으로 모든 Visual Studio 언어에서 동일합니다. 공유 기능에 대한 자세한 내용은 [코드 및 텍스트 편집기에서 코드 작성](/visualstudio/ide/writing-code-in-the-code-and-text-editor)을 참조하세요.  

## <a name="colorization"></a>색 지정

Visual Studio는 구문 요소에 색을 지정하여 언어 키워드, 형식 이름, 변수 이름, 함수 매개 변수, 문자열 리터럴 등과 같은 기호의 형식을 구분합니다.

![코드 색 지정](../ide/media/code-outline-colorization.png "C++ 색 지정")

사용되지 않는 코드(예: #if 0 아래의 코드)는 색에서 희미하게 표시됩니다.

![비활성 코드](../ide/media/inactive-code-cpp.png "C++ 비활성 코드")

**빠른 실행** 에서 "글꼴"을 입력한 다음, **글꼴 및 색** 을 선택하여 색을 사용자 지정할 수 있습니다. **글꼴 및 색** 대화 상자에서 C/C++ 옵션으로 스크롤한 다음, 사용자 지정 글꼴 및/또는 색을 선택합니다.

## <a name="outlining"></a>개요

소스 코드 파일의 아무 곳이나 마우스 오른쪽 단추로 클릭하고 **개요** 를 선택하여 코드 블록 및/또는 사용자 지정 영역을 축소하거나 확장하면 관심 있는 코드만 쉽게 찾을 수 있습니다. 자세한 내용은 [개요](/visualstudio/ide/outlining)를 참조하세요.

![C&#43;&#43; 개요](../ide/media/vs2015_cpp_outlining.png "개요")

커서를 중괄호, '{' 또는 '}' 앞에 배치하면 편집기는 일치하는 항목을 강조 표시합니다.

다른 개요 옵션은 주 메뉴의 **편집** > **개요** 아래에 있습니다.

## <a name="line-numbers"></a>줄 번호

**도구** > **옵션** > **텍스트 편집기** > **모든 언어** > **일반** 으로 이동하거나 **빠른 실행(Ctrl + Q)** 으로 "줄 번호"를 검색하여 프로젝트에 줄 번호를 추가할 수 있습니다. 모든 언어에 대해 또는 C++를 포함하는 특정 언어에 대해서만 줄 번호를 설정할 수 있습니다.

## <a name="scroll-and-zoom"></a>스크롤 및 확대/축소

**Ctrl** 키를 누르고 마우스 휠로 스크롤하여 편집기에서 확대/축소할 수 있습니다. 왼쪽 아래 모퉁이에서 확대/축소 설정을 사용하여 확대/축소할 수도 있습니다.

![C&#43;&#43; 확대/축소 컨트롤](../ide/media/zoom-control.png "확대/축소 컨트롤")

스크롤 막대 **맵 모드** 를 사용하면 현재 위치를 벗어나지 않고 코드 파일을 신속하게 스크롤하여 찾아볼 수 있습니다. 코드 맵의 아무 곳이나 클릭하여 해당 위치로 직접 이동할 수 있습니다.

![C&#43;&#43;의 코드 맵](../ide/media/vs2015-cpp-code-map.png "코드 맵")

**맵 모드** 를 켜려면 주 도구 모음 상자의 **빠른 실행** 검색 상자에 “맵”을 입력하고 **스크롤 맵 모드 사용** 을 선택합니다. 자세한 내용은 [방법: 스크롤 막대를 사용자 지정하여 코드 추적](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar)을 참조하세요.

**맵 모드** 가 꺼진 경우 스크롤 막대는 여전히 파일의 변경 내용을 강조 표시합니다. 녹색은 저장된 변경 내용을 나타내며 노란색은 저장되지 않은 변경 내용을 나타냅니다.

## <a name="quick-info-and-parameter-info"></a>요약 정보 및 매개 변수 정보

모든 변수, 함수 또는 다른 기호를 마우스로 가리켜 선언을 포함한 정보 및 바로 앞에 있는 설명을 가져옵니다.

::: moniker range="msvc-160"

![Visual Studio 2019의 요약 정보 도구 설명을 보여 주는 스크린샷](../ide/media/quick-info-vs2019.png "요약 정보")

**요약 정보** 도구 설명에는 **온라인 검색** 링크가 있습니다. **도구** > **옵션** > **텍스트 편집기** > **C++**  > **보기** 로 이동하여 검색 공급 기업을 지정합니다.

코드에 오류가 있는 경우 마우스로 가리키면 **요약 정보** 가 오류 메시지를 표시합니다. 오류 메시지를 오류 목록 창에서 찾을 수도 있습니다.

![오류에 대한 요약 정보](../ide/media/quickinfo-on-error.png "오류에 대한 요약 정보")

::: moniker-end

::: moniker range="<=msvc-150"

![Visual Studio 2017의 요약 정보 도구 설명을 보여 주는 스크린샷](../ide/media/quick-info.png "요약 정보")

코드에 오류가 있는 경우 마우스로 가리키면 **요약 정보** 가 오류 메시지를 표시합니다. 오류 메시지를 **오류 목록** 창에서 찾을 수도 있습니다.

![오류에 대한 요약 정보](../ide/media/quickinfo-on-error.png "오류에 대한 요약 정보")

::: moniker-end

함수를 호출할 때 **매개 변수 정보** 는 매개 변수의 형식 및 예상되는 순서를 보여 줍니다.

![C&#43;&#43;의 매개 변수 정보](../ide/media/parameter-info.png "매개 변수 정보")

## <a name="peek-definition"></a>정의 피킹(Peeking)

변수 또는 함수 선언을 마우스로 가리키고, 마우스 오른쪽 단추를 클릭한 다음, **정의 피킹(Peeking)** 을 선택하여 현재 위치에서 이동하지 않고 해당 정의의 인라인 뷰를 표시합니다. 자세한 내용은 [정의 피킹(Peeking)(Alt+F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12)을 참조하세요.

![C&#43;&#43; 정의 피킹](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

## <a name="f1-help"></a>F1 도움말

형식, 키워드 또는 함수 위나 바로 뒤에 커서를 놓고 **F1** 키를 눌러 docs.microsoft.com에서 관련된 참조 항목으로 바로 이동합니다. **F1** 키는 많은 대화 상자와 오류 목록의 항목에서도 작동합니다.

## <a name="class-view"></a>클래스 뷰

**클래스 뷰** 는 프로젝트별로 구성된 검색 가능한 모든 코드 기호와 해당 범위 및 부모/자식 계층 구조의 트리 세트를 표시합니다. **클래스 뷰 설정** 에서 **클래스 뷰** 가 표시하는 항목을 구성할 수 있습니다(창의 맨 위에 있는 기어 상자 아이콘 클릭).

![C&#43;&#43;의 클래스 뷰](../ide/media/class-view.png "클래스 뷰")

## <a name="generate-graph-of-include-files"></a>포함 파일의 그래프 생성

프로젝트에서 코드 파일을 마우스 오른쪽 단추로 클릭하고 **포함 파일의 그래프 생성** 을 선택하여 다른 파일에 포함된 파일의 그래프를 표시합니다.

![C&#43;&#43; 포함 파일의 그래프](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>호출 계층 구조 보기

함수 호출을 마우스 오른쪽 단추로 클릭하고 함수가 호출하는 모든 함수와 함수를 호출하는 모든 함수의 재귀적 목록을 표시합니다. 목록의 각 함수를 동일한 방식으로 확장할 수 있습니다. 자세한 내용은 [호출 계층 구조](/visualstudio/ide/reference/call-hierarchy)를 참조하세요.

![C&#43;&#43; 호출 계층 구조](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>참고 항목

[코드(C++) 편집 및 리팩터링](writing-and-refactoring-code-cpp.md)</br>
[Visual Studio에서 C++ 코드 베이스 탐색](navigate-code-cpp.md)</br>
[C++용 Live Share를 사용하여 협업](live-share-cpp.md)
