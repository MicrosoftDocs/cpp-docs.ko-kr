---
description: '자세한 정보: 연습: 프로젝트 및 솔루션 작업(C++)'
title: '연습: 프로젝트 및 솔루션 작업(C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: f96c531a7a47e961b7e7da15ad455e3feefc6925
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345279"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>연습: 프로젝트 및 솔루션 작업(C++)

Visual Studio에서 C++ 프로젝트를 만들고 코드를 추가한 다음 프로젝트를 빌드하여 실행하는 방법은 다음과 같습니다. 이 연습에 나오는 프로젝트는 얼마나 많은 플레이어가 서로 다른 카드 게임을 플레이하고 있는지를 추적하는 프로그램입니다.

Visual Studio에서는 프로젝트와 솔루션으로 작업을 구성합니다. 솔루션에는 DLL 및 이 DLL을 참조하는 실행 파일과 같은 둘 이상의 프로젝트가 포함될 수 있습니다. 자세한 내용은 [솔루션 및 프로젝트](/visualstudio/ide/solutions-and-projects-in-visual-studio)를 참조하세요.

## <a name="before-you-start"></a>시작하기 전에

이 연습을 완료하려면 Visual Studio 2017 이상이 필요합니다. 복사본이 필요한 경우 다음과 같은 간단한 가이드를 참조하세요. [Visual Studio에서 C++ 지원을 설치합니다](../build/vscpp-step-0-installation.md). 아직 설치하지 않았다면 "Hello, World" 자습서를 통해 설치한 후, 다음 단계를 수행하여 C++ 구성 요소가 올바르게 설치되고 모두 작동하는지 확인합니다.

C++ 언어의 기본적인 사항을 이해하고 컴파일러, 링커 및 디버거가 사용되는 용도를 파악하면 도움이 됩니다. 이 자습서에서는 Windows 및 메뉴, 대화 상자를 사용하는 방법에 익숙하다고 가정합니다.

## <a name="create-a-project"></a>프로젝트 만들기

프로젝트를 만들려면 먼저 프로젝트 형식 템플릿을 선택합니다. 각 프로젝트 형식에 대해 Visual Studio에서는 컴파일러 설정을 지정하고 형식에 따라 시작 코드를 생성합니다. 이 시작 코드는 나중에 수정할 수 있습니다. 다음 단계는 사용 중인 Visual Studio 버전에 따라 다릅니다. 기본 설정된 버전의 Visual Studio에 대한 설명서를 보려면 **버전** 선택기 컨트롤을 사용하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker range="msvc-160"

### <a name="to-create-a-project-in-visual-studio-2019"></a>Visual Studio 2019에서 프로젝트를 만들려면

1. 주 메뉴에서 **파일** > **새로 만들기** > **프로젝트** 를 선택하여 **새 프로젝트 만들기** 대화 상자를 엽니다.

1. 대화 상자 맨 위에서 **언어** 를 **C++** 로 설정하고 **플랫폼** 을 **Windows** 로 설정하고 **프로젝트 형식** 을 **콘솔** 로 설정합니다.

1. 필터링된 프로젝트 형식 목록에서 **콘솔 앱** 을 선택한 후 **다음** 을 선택합니다. 다음 페이지에서 *게임* 을 프로젝트 이름으로 입력합니다.

   **위치** 드롭다운 목록에서 기본 위치를 적용하거나 다른 위치를 입력하거나 **찾아보기** 단추를 선택하여 프로젝트를 저장할 디렉터리를 찾아볼 수 있습니다.

   프로젝트를 만들면 Visual Studio에서 해당 프로젝트가 솔루션에 추가됩니다. 기본적으로 솔루션의 이름은 프로젝트 이름과 같습니다. **솔루션 이름** 상자에서 이름을 변경할 수 있지만 이 예제에서는 기본 이름을 유지합니다.

1. **만들기** 단추를 선택하여 프로젝트를 만듭니다.

   Visual Studio는 새 솔루션 및 프로젝트 파일을 만들고 생성된 Game.cpp 소스 코드 파일의 편집기를 엽니다.

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-project-in-visual-studio-2017"></a>Visual Studio 2017에서 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

1. **새 프로젝트** 대화 상자의 왼쪽 창에서 **설치됨** 을 확장하고, 아직 열려 있지 않은 경우 **Visual C++** 를 선택합니다.

1. 가운데 창의 설치된 템플릿 목록에서 **Windows 콘솔 애플리케이션** 을 선택합니다.

1. **이름** 상자에 프로젝트의 이름을 입력합니다. 이 예에서는 *Game* 을 입력합니다.

   **위치** 드롭다운 목록에서 기본 위치를 적용하거나 다른 위치를 입력하거나 **찾아보기** 단추를 선택하여 프로젝트를 저장할 디렉터리를 찾아볼 수 있습니다.

   프로젝트를 만들면 Visual Studio에서 해당 프로젝트가 솔루션에 추가됩니다. 기본적으로 솔루션의 이름은 프로젝트 이름과 같습니다. **솔루션 이름** 상자에서 이름을 변경할 수 있지만 이 예제에서는 기본 이름을 유지합니다.

1. **확인** 단추를 선택하여 프로젝트를 만듭니다.

   Visual Studio는 새 솔루션 및 프로젝트 파일을 만들고 생성된 Game.cpp 소스 코드 파일의 편집기를 엽니다.

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-project-in-visual-studio-2015"></a>Visual Studio 2015에서 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

1. **새 프로젝트** 대화 상자의 왼쪽 창에서 **설치됨** 을 확장하고, 아직 열려 있지 않은 경우 **Visual C++** 를 선택합니다.

1. 가운데 창의 설치된 템플릿 목록에서 **Win32 콘솔 애플리케이션** 을 선택합니다.

1. **이름** 상자에 프로젝트의 이름을 입력합니다. 이 예에서는 *Game* 을 입력합니다.

   **위치** 드롭다운 목록에서 기본 위치를 적용하거나 다른 위치를 입력하거나 **찾아보기** 단추를 선택하여 프로젝트를 저장할 디렉터리를 찾아볼 수 있습니다.

   프로젝트를 만들면 Visual Studio에서 해당 프로젝트가 솔루션에 추가됩니다. 기본적으로 솔루션의 이름은 프로젝트 이름과 같습니다. **솔루션 이름** 상자에서 이름을 변경할 수 있지만 이 예제에서는 기본 이름을 유지합니다.

1. **확인** 단추를 선택하여 프로젝트를 만듭니다.

   Visual Studio는 새 솔루션 및 프로젝트 파일을 만들고 생성된 Game.cpp 소스 코드 파일의 편집기를 엽니다.

::: moniker-end

## <a name="organize-projects-and-files"></a>프로젝트 및 파일 구성

**솔루션 탐색기** 를 사용하여 솔루션의 프로젝트, 파일 및 기타 리소스를 구성하고 관리할 수 있습니다.

이 연습 부분에서는 프로젝트에 클래스를 추가하는 방법을 보여 줍니다. 클래스를 추가하면 Visual Studio에서 해당 .h 및 .cpp 파일을 추가합니다. **솔루션 탐색기** 에서 결과를 볼 수 있습니다.

### <a name="to-add-a-class-to-a-project"></a>프로젝트에 클래스를 추가하려면

1. **솔루션 탐색기** 창이 Visual Studio에 표시되지 않으면 메뉴 모음에서 **보기** > **솔루션 탐색기** 를 선택합니다.

1. **솔루션 탐색기** 에서 **Game** 프로젝트를 선택합니다. 메뉴 모음에서 **프로젝트** > **클래스 추가** 를 선택합니다.

1. **클래스 추가** 대화 상자에서 **클래스 이름** 상자에 *Cardgame* 을 입력합니다. 기본 파일 이름과 설정을 수정하지 마십시오. **확인** 단추를 선택합니다.

   Visual Studio는 새 파일을 만들어 프로젝트에 추가합니다. **솔루션 탐색기** 창에서 해당 항목을 볼 수 있습니다. Cardgame.h 및 Cardgame.cpp 파일이 편집기에서 열립니다.

1. Cardgame.h 파일을 편집하고 다음과 같이 변경합니다.

   - 클래스 정의의 여는 중괄호 뒤에 두 개의 전용 데이터 멤버를 추가합니다.
     <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Visual Studio에서 생성된 기본 생성자를 수정합니다. `public:` 액세스 지정자 뒤에서 다음과 같은 줄을 찾습니다.

      `Cardgame();`

      생성자를 수정하여 *players* 라고 명명된 **`int`** 형식의 매개 변수 하나를 사용합니다.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - 기본 소멸자 뒤에 매개 변수를 사용하지 않고 `totalParticipants` 값을 반환하는 *GetParticipants* 라는 `static int` 멤버 함수에 대한 인라인 선언을 추가합니다.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   변경한 후 Cardgame.h 파일은 아래 코드와 유사합니다.

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->

    ```cpp
    #pragma once
    class Cardgame
    {
        int players;
        static int totalParticipants;
    public:
        Cardgame(int players);
        ~Cardgame();
        static int GetParticipants() { return totalParticipants; }
    };
    ```

   `#pragma once` 줄은 컴파일러에 헤더 파일을 한 번만 포함하도록 지시합니다. 자세한 내용은 [once](../preprocessor/once.md)를 참조하세요. 위의 헤더 파일에 포함된 다른 C++ 키워드에 대한 자세한 내용은 [class](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [static](../cpp/storage-classes-cpp.md) 및 [public](../cpp/public-cpp.md)을 참조하세요.

1. 편집 창 맨 위에 있는 **Cardgame.cpp** 탭을 선택하여 편집할 수 있도록 엽니다.

1. 파일에 있는 모든 항목을 삭제하고 다음 코드로 바꿉니다.

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->

    ```cpp
    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    int Cardgame::totalParticipants = 0;

    Cardgame::Cardgame(int players)
        : players(players)
    {
        totalParticipants += players;
        cout << players << " players have started a new game.  There are now "
             << totalParticipants << " players in total." << endl;
    }

    Cardgame::~Cardgame()
    {
    }
    ```

   > [!NOTE]
   > 코드를 입력할 때 자동 완성 기능을 사용할 수 있습니다. 예를 들어 키보드에서 이 코드를 입력한 경우 *pl* 또는 *tot* 를 입력한 다음, **Ctrl**+**스페이스바** 를 누릅니다. 자동 완성 기능이 `players` 또는 `totalParticipants`를 자동으로 입력합니다.

## <a name="add-test-code-to-your-main-function"></a>main 함수에 테스트 코드 추가

새 함수를 테스트하는 일부 코드를 앱에 추가합니다.

### <a name="to-add-test-code-to-the-project"></a>테스트 코드를 프로젝트에 추가하려면

1. **Game.cpp** 편집기 창에서 기존 코드를 다음과 같이 바꿉니다.

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->

    ```cpp
    // Game.cpp : Defines the entry point for the console application.
    //

    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    void PlayGames()
    {
        Cardgame bridge(4);
        Cardgame blackjack(8);
        Cardgame solitaire(1);
        Cardgame poker(5);
    }

    int main()
    {
        PlayGames();
        return 0;
    }
    ```

   이 코드는 소스 코드에 테스트 함수 `PlayGames`를 추가하고, `main`에서 호출합니다.

## <a name="build-and-run-your-app-project"></a>앱 프로젝트 빌드 및 실행

그런 다음, 프로젝트를 빌드하고 앱을 실행합니다.

### <a name="to-build-and-run-the-project"></a>프로젝트를 빌드하여 실행하려면

1. 메뉴 모음에서 **빌드** > **솔루션 빌드** 를 선택합니다.

   빌드의 출력이 **출력** 창에 표시됩니다. 빌드가 성공한 경우 출력은 다음과 같습니다.

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>pch.cpp
    1>Cardgame.cpp
    1>Game.cpp
    1>Generating Code...
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

   빌드 구성에 따라 **출력** 창에 다른 단계가 표시될 수 있지만, 프로젝트 빌드가 성공한 경우 마지막 줄은 표시된 출력과 비슷합니다.

   빌드가 실패한 경우 코드를 이전 단계에서 표시된 코드와 비교합니다.

1. 프로젝트를 실행하려면 메뉴 모음에서 **디버그** > **디버그하지 않고 시작** 을 선택합니다. 콘솔 창이 나타나고 출력은 다음과 같습니다.

    ```Output
    4 players have started a new game.  There are now 4 players in total.
    8 players have started a new game.  There are now 12 players in total.
    1 players have started a new game.  There are now 13 players in total.
    5 players have started a new game.  There are now 18 players in total.
    ```

   콘솔 창을 닫으려면 키를 누릅니다.

축하합니다, 앱 프로젝트와 솔루션을 성공적으로 빌드했습니다. Visual Studio에서 C++ 코드 프로젝트를 빌드하는 방법에 대해 자세히 알아보려면 연습을 계속합니다.

## <a name="next-steps"></a>다음 단계

**이전:** [C++ 데스크톱 개발에 Visual Studio IDE 사용](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**다음:** [연습: 프로젝트 빌드(C++)](../ide/walkthrough-building-a-project-cpp.md)

## <a name="see-also"></a>참조

[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[프로젝트 및 빌드 시스템](../build/projects-and-build-systems-cpp.md)<br/>
