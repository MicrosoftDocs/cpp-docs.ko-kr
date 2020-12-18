---
description: '자세한 정보: Visual Studio에서 C++ 코딩 기본 설정 지정'
title: Visual Studio에서 C++ 코딩 기본 설정 지정
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: 9a82c0771c097bb1246737f748077bbc303ac9f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240912"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Visual Studio에서 C++ 코딩 기본 설정 지정

Visual Studio를 개인 설정하여 C++ 코딩 환경을 더 편리하고 생산적이고 즐거운 방식으로 만들 수 있습니다. 다음과 같습니다.

- 메뉴 및 도구 모음 사용자 지정
- 창 레이아웃 조정
- 색 테마 설정
- 여러 스타일의 ClangFormat을 포함하여 C++ 서식 지정 규칙 지정
- 사용자 지정 바로 가기 키 만들기

여러 컴퓨터에서 기본 설정을 동기화할 수 있으며, 기본 설정 집합을 여러 개 만들어 저장하고 동료와 공유할 수 있습니다. Visual Studio Marketplace에서 확장을 설치하여 동작을 사용자 지정하는 추가 옵션을 사용할 수 있습니다. 자세한 내용은 [Visual Studio IDE 개인 설정](/visualstudio/ide/personalizing-the-visual-studio-ide)을 참조하세요.

## <a name="arrange-window-layout"></a>창 레이아웃 조정

Visual Studio 창 내에서 공간은 주 메뉴, 도구 모음, 코드 편집기(또는 문서 창), 도구 창(예: 솔루션 탐색기 및 오류 목록)으로 구분됩니다. 일부 창은 동일한 위치에서 서로 겹칩니다. 예를 들어 솔루션 탐색기, 클래스 뷰, 리소스 뷰, 소스 제어 탐색기는 모두 동일한 기본 위치를 공유합니다. 프레임 아래쪽의 탭을 선택하여 창 사이를 전환합니다. 이러한 창을 두 개 이상 동시에 표시하려면 창을 제목 표시줄로 끌어 새 위치에 놓으면 됩니다. 창을 Visual Studio 주 창 테두리 중 하나에 도킹하거나 움직일 수 있습니다.

다음 스크린샷에서는 **팀 탐색기** 창을 기본 위치에서 코드 편집기 왼쪽에 도킹된 새 위치로 끄는 모습을 보여 줍니다. 파란색 음영 영역은 마우스 단추를 놓을 때 창이 배치되는 위치입니다.

![레이아웃 변화가 강조 표시된 Visual Studio 팀 탐색기 창의 스크린샷](media/window-layout-move-team-explorer.png)

문서 창에서 열려 있는 파일은 모두 탭 프레임에 포함되어 있습니다. 도구 창과 마찬가지로 이러한 탭을 고정하거나 움직일 수 있습니다. 자세한 내용은 [Visual Studio에서 창 레이아웃 사용자 지정](/visualstudio/ide/customizing-window-layouts-in-visual-studio)을 참조하세요.

모든 도구 창을 숨기고 코드 편집기 창을 최대화하려면 **Alt** + **Shift** + **Enter** 를 눌러 *전체 화면 모드* 로 전환합니다.

## <a name="set-c-coding-styles-and-formatting"></a>C++ 코딩 스타일 및 서식 설정

들여쓰기 및 중괄호 위치와 같은 여러 개별 코드 서식 옵션을 지정할 수 있습니다. 이렇게 하려면 **도구** > **옵션** > **텍스트 편집기** > **C/C++**  > **서식** 으로 이동(또는 **Ctrl + Q** 를 입력한 다음 "서식"을 검색)합니다. 또는 [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) 스타일(또는 사용자 지정 ClangFormat 스타일) 중 하나를 지정할 수 있습니다.

![ClangFormat 옵션의 스크린샷](media/clang-format-ide.png)

모든 서식 옵션에 대한 자세한 내용은 [옵션, 텍스트 편집기, C/ C++, 서식](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting)을 참조하세요.

## <a name="set-the-color-theme"></a>색 테마 설정

밝은 배경 또는 어두운 배경을 설정하려면 **Ctrl + Q** 를 입력하고 "색 테마"를 검색합니다. **도구** > **옵션** > **환경** 으로 이동하고 **색 테마** 를 선택하여 찾을 수도 있습니다.

![색 테마의 스크린샷](media/tools-options-color-theme.png)

예를 들어 다음은 어두운 테마입니다.

![어두운 색 테마가 있는 Visual Studio의 스크린샷](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>코드 색 지정 사용자 지정

Visual Studio 2019에서는 미리 정의된 세 가지 색 구성표에서 선택할 수 있습니다. 이들은 편집기에서 코드 요소의 색을 지정하는 방법을 지정합니다. 테마를 선택하려면 **도구** > **옵션** > **텍스트 편집기** > **C/C++**  > **보기** 로 이동하고 **색 구성표** 를 선택합니다.

![고급이 강조 표시된 C++ 색 구성표 옵션의 스크린샷](media/color-schemes.png)

**Visual Studio 2017** 이라는 색 구성표에서는 대부분의 코드 요소가 단순하게 검정색입니다. **고급** 색 구성표에는 함수, 지역 변수, 매크로 및 기타 요소에 대한 색이 지정되어 있습니다. **고급(전역 및 멤버)** 구성표에서는 전역 함수 및 변수와 클래스 멤버가 대조되는 색으로 지정됩니다. 기본 모드는 **고급** 이며 다음과 같습니다.

![고급 색 구성표의 스크린샷](media/color-scheme-enhanced.png)

설정된 테마 또는 색 구성표에 관계없이 개별 코드 요소의 글꼴 및 색을 사용자 지정할 수 있습니다. 이렇게 하려면 **도구** > **옵션** > **환경** > **글꼴 및 색** 로 이동(또는 **Ctrl + Q** 를 입력하고 "글꼴"을 검색)합니다. C++ 옵션이 표시될 때까지 표시 항목 목록을 아래로 스크롤합니다.

![C++ 글꼴 및 색 옵션의 스크린샷](media/tools-options-cpp-colors.png)

여기서 설정한 색은 색 구성표에 정의된 값을 재정의합니다. 색 구성표의 기본 색으로 돌아가려면 색을 다시 **기본값** 으로 설정합니다.

## <a name="customize-the-toolbars"></a>도구 모음 사용자 지정

도구 모음은 메뉴 또는 바로 가기 키를 사용하는 대신 한 번의 클릭으로 명령을 실행하는 편리한 방법을 제공합니다. Visual Studio에는 표준 도구 모음 집합이 포함되어 있습니다. 표준 C++ 개발의 경우 가장 유용한 도구 모음은 표준, 텍스트 편집기, 빌드, 디버그, 소스 제어 및 파일 비교입니다. Windows 개발의 경우 대화 상자 편집기 및 이미지 편집기가 대화 상자를 배치하고 아이콘을 편집하는 데 유용합니다.

도구 모음에 있는 아이콘을 마우스로 가리키면 해당 아이콘이 나타내는 명령이 표시됩니다.

![마우스로 가리키면 표시되는 명령 정보의 예를 보여 주는 도구 모음 아이콘의 스크린샷](media/toolbar-mouse-hover.png)

아래쪽 화살표를 선택하여 명령을 추가 또는 제거하거나 사용자 지정 도구 모음을 만들 수 있습니다. 도구 모음을 새 위치로 이동하려면 왼쪽의 점선 막대로 끕니다.

![아래쪽 화살표 및 점선 막대가 강조 표시된 도구 모음의 스크린샷](media/toolbar-move-edit.png).

자세한 내용은 [방법: Visual Studio에서 메뉴 및 도구 모음 사용자 지정](/visualstudio/ide/how-to-customize-menus-and-toolbars-in-visual-studio)을 참조하세요.

## <a name="show-or-hide-line-numbers"></a>줄 번호 표시 또는 숨기기

줄 번호가 편집기 창의 왼쪽에 표시되는지 여부를 지정할 수 있습니다. **옵션** 의 **C/C++** 에서 **일반** 을 선택합니다. **설정** 섹션에서 선호에 따라 **줄 번호** 를 선택하거나 선택 취소합니다.

![줄 번호가 강조 표시된 일반 옵션의 스크린샷](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>바로 가기 키 만들기

Visual Studio의 많은 명령에는 키와 Ctrl, Alt 또는 Shift 키가 조합된 바로 가기 키가 있습니다. Visual Studio에서 이러한 바로 가기 키를 수정하거나 새로 만들 수 있습니다. **도구** > **옵션** > **환경** > **키보드** 로 이동(또는 **Ctrl + Q** 를 입력하고 "바로 가기"를 검색)합니다. 자세한 내용은 [Visual Studio의 바로 가기 키 식별 및 사용자 지정](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)을 참조하세요.
