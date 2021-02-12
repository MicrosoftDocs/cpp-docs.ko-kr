---
title: C++에서 콘솔 계산기 만들기
description: Visual C++에서 Hello World 콘솔 앱 및 계산기 앱 만들기
ms.custom: mvc
ms.date: 08/19/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 2a0f605d6b415e1b827bd2d983b087bc110eddd8
ms.sourcegitcommit: 77235bff6a7b2621c501938e30d93cb15f5733cb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2021
ms.locfileid: "100254418"
---
# <a name="create-a-console-calculator-in-c"></a>C++에서 콘솔 계산기 만들기

::: moniker range=">=msvc-160"

C++ 프로그래머의 일반적인 시작점은 명령줄에서 실행되는 "Hello, world!" 애플리케이션입니다. 이 문서를 통해 Visual Studio에서 이 애플리케이션을 먼저 만든 후에 좀 더 어려운 계산기 앱을 만들겠습니다.

## <a name="prerequisites"></a>사전 요구 사항

- 컴퓨터에서 설치되고 실행 중인 **C++ 워크로드를 사용하여 데스크톱 개발** 을 위해 Visual Studio를 설치합니다. 아직 설치되지 않은 경우 [Visual Studio에서 C++ 지원 설치](../build/vscpp-step-0-installation.md)를 참조하세요.

## <a name="create-your-app-project"></a>앱 프로젝트 만들기

Visual Studio는 ‘프로젝트’를 사용하여 앱에 대한 코드를 구성하고 ‘솔루션’을 사용하여 프로젝트를 구성합니다. 프로젝트에는 앱을 빌드하는 데 사용되는 모든 옵션, 구성 및 규칙이 포함됩니다. 또한 프로젝트의 모든 파일과 외부 파일 간의 관계를 관리합니다. 앱을 만들려면 먼저 새 프로젝트 및 솔루션을 만듭니다.

1. Visual Studio를 방금 시작한 경우 Visual Studio 2019 대화 상자가 표시됩니다. **새 프로젝트 만들기** 를 선택하여 시작합니다.

   ![Visual Studio 2019 첫 번째 대화 상자](./media/calc-vs2019-initial-dialog.png "Visual Studio 2019 첫 번째 대화 상자")

   그렇지 않으면, Visual Studio의 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다. **새 프로젝트 만들기** 창이 열립니다.

1. 프로젝트 템플릿 목록에서 **콘솔 앱** 을 선택한 후, **다음** 을 선택합니다.

   ![콘솔 앱 템플릿 선택](./media/calc-vs2019-choose-console-app.png "콘솔 앱 템플릿 선택")

   > [!Important]
   > **콘솔 앱** 템플릿의 C++ 버전을 선택해야 합니다. **C++** , **Windows** 및 **콘솔** 태그가 있으며, 아이콘은 모서리에 "++"가 있습니다.

1. **새 프로젝트 구성** 대화 상자에서 **프로젝트 이름** 편집 상자를 선택하고, 새 프로젝트의 이름을 *CalculatorTutorial* 로 지정한 다음, **만들기** 를 선택합니다.

   ![새 프로젝트 구성 대화 상자에서 프로젝트에 이름 지정](./media/calc-vs2019-name-your-project.png "새 프로젝트 구성 대화 상자에서 프로젝트에 이름 지정")

   비어 있는 C++ Windows 콘솔 애플리케이션이 생성됩니다. 콘솔 애플리케이션은 Windows 콘솔 창을 사용하여 출력을 표시하고 사용자 입력을 허용합니다. Visual Studio에서 편집기 창이 열리고 생성된 코드를 보여 줍니다.

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n";
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>새 앱이 빌드되고 실행되는지 확인

새 Windows 콘솔 애플리케이션의 템플릿은 간단한 C++ "Hello World" 앱을 생성합니다. 이 시점에서는 Visual Studio가 IDE에서 직접 만든 앱을 빌드하고 실행하는 방법을 확인할 수 있습니다.

1. 프로젝트를 빌드하려면 **빌드** 메뉴에서 **솔루션 빌드** 를 선택합니다. **출력** 창은 빌드 프로세스의 결과를 보여줍니다.

   ![빌드 프로세스의 결과를 보여 주는 출력 창이 있는 Visual Studio 2019의 스크린샷](./media/calc-vs2019-build-your-project.png "프로젝트 빌드")

1. 코드를 실행하려면 메뉴 모음에서 **디버그**, **디버깅하지 않고 시작** 을 선택합니다.

   ![코드가 성공적으로 실행되었음을 보여 주는 Visual Studio 2019 Microsoft Visual Studio 디버그 콘솔의 스크린샷](./media/calc-vs2019-hello-world-console.png "프로젝트 시작")

   콘솔 창이 열린 다음, 앱을 실행합니다. Visual Studio에서 콘솔 앱을 시작하면 코드를 실행한 다음, "이 창을 닫으려면 아무 키나 누르세요. 을 선택합니다. "를 표시하여 출력을 볼 수 있도록 합니다. 지금까지 Visual Studio에서 첫 번째 "Hello, world!" 콘솔 앱을 만들었습니다.

1. 키를 눌러서 콘솔 창을 닫고 Visual Studio로 돌아갑니다.

이제 예상한 대로 코드가 계속 작동하는지 확인하기 위해 앱을 변경할 때마다 빌드하고 실행할 도구가 설치되었습니다. 그렇지 않은 경우 디버그하는 방법을 나중에 보여드리겠습니다.

## <a name="edit-the-code"></a>코드 편집

이제 이 템플릿의 코드를 계산기 앱으로 바꾸겠습니다.

1. *CalculatorTutorial.cpp* 파일에서 이 예제와 일치하도록 코드를 편집합니다.

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > 코드 이해:
   >
   > - `#include` 문을 통해 다른 파일에 있는 코드를 참조할 수 있습니다. 경우에 따라 파일 이름이 꺾쇠 괄호( **\<\>** )로 묶여서 표시될 수 있습니다. 아니면 따옴표( **“ ”** )로 묶일 수 있습니다. 일반적으로, C++ 표준 라이브러리를 참조할 때 꺾쇠 괄호를 사용하는 반면 다른 파일의 경우 따옴표를 사용합니다.
   > - `using namespace std;` 줄은 이 파일에 사용할 C++ 표준 라이브러리의 항목을 가져오도록 컴파일러에 지시합니다. 이 줄이 없으면 라이브러리의 각 키워드에서는 해당 범위를 나타내는 `std::`가 앞에 와야 합니다. 예를 들어 해당 줄이 없으면 `cout`에 대한 참조는 각각 `std::cout`와 같이 작성되어야 합니다. 코드를 정리하기 위해 **`using`** 문을 추가합니다.
   > - C++인 표준 출력으로 인쇄하기 위해 `cout` 키워드를 사용합니다. **\<\<** 연산자는 어떤 항목이든지 표준 출력에 보내도록 컴파일러에 지시합니다.
   > - **endl** 키워드는 Enter 키와 같이 줄을 종료하고 커서를 다음 줄로 이동시킵니다. ""에 포함된 문자열 내에 `\n`을 배치하여 동일한 작업을 수행하는 것이 좋습니다. `endl`이 항상 버퍼를 플러시하고 프로그램의 성능을 저하시킬 수 있지만 매우 작은 앱이므로 가독성을 위해 대신 `endl`을 사용합니다.
   > - C++ 문은 항상 세미콜론으로 끝나야 하며, C++ 애플리케이션에는 항상 `main()` 함수가 포함되어야 합니다. 이 함수는 시작 시 프로그램이 실행하는 내용입니다. 코드를 사용하기 위해 `main()`에서 액세스할 수 있어야 합니다.

1. 파일을 저장하려면 **Ctrl+S** 를 선택하거나 IDE의 위쪽 가까이에서 **저장** 아이콘, 메뉴 모음의 도구 모음에서 플로피 디스크 아이콘을 선택하세요.

1. 애플리케이션을 실행하려면 **Ctrl+F5** 키를 누르거나 **디버그** 메뉴로 이동하고 **디버깅하지 않고 시작** 을 선택하세요. 코드에서 지정된 텍스트가 표시되는 콘솔 창이 나타납니다.

1. 작업이 완료되면 콘솔 창을 닫습니다.

## <a name="add-code-to-do-some-math"></a>일부 계산을 수행하는 코드 추가

일부 수학 논리를 추가할 차례입니다.

### <a name="to-add-a-calculator-class"></a>계산기 클래스를 추가하려면

1. **프로젝트** 메뉴로 이동하고, **클래스 추가** 를 선택합니다. **클래스 이름** 편집 상자에 *계산기* 를 입력합니다. **확인** 을 선택합니다. 2개의 새 파일이 프로젝트에 추가됩니다. 변경된 파일을 모두 한 번에 저장하려면 **Ctrl+Shift+S** 키를 누르세요. **파일** > **모두 저장** 의 바로 가기 키입니다. **저장** 단추 옆에 있는 두 개의 플로피 디스크 아이콘인 **모두 저장** 에 대한 도구 모음 단추이기도 합니다. 일반적으로, **모두 저장** 을 자주 수행하는 것이 좋습니다. 그러면 파일을 저장할 때 누락하지 않게 됩니다.

   ![클래스 이름 텍스트 상자에 Calculator가 입력된 클래스 추가 대화 상자의 스크린샷](./media/calc-vs2019-create-calculator-class.png "계산기 클래스 만들기")

   클래스는 특정 작업을 수행하는 개체의 청사진과 비슷합니다. 이 경우에는 계산기 및 계산기의 작동 방식을 정의합니다. 위에서 사용한 **클래스 추가** 마법사는 클래스와 동일한 이름을 가진 .h 및 .cpp 파일을 만들었습니다. IDE의 측면에 표시되는 **솔루션 탐색기** 창에서 프로젝트 파일의 전체 목록을 볼 수 있습니다. 창이 표시되지 않으면 메뉴 모음에서 **보기** > **솔루션 탐색기** 를 선택하여 열 수 있습니다.

   ![Calculator Tutorial 프로젝트가 표시된 Visual Studio 2019 솔루션 탐색기 창의 스크린샷](./media/calc-vs2019-solution-explorer.png "솔루션 탐색기")

   이제 편집기에는 다음과 같은 세 가지 탭이 열려 있습니다. *CalculatorTutorial.cpp*, *Calculator.h* 및 *Calculator.cpp* 실수로 그중 하나를 닫은 경우 **솔루션 탐색기** 창에서 두 번 클릭하여 다시 열 수 있습니다.

1. 생성된 `Calculator();` 및 `~Calculator();` 줄이 필요하지 않으므로 **Calculator.h** 에서 제거하세요. 다음으로, 다음과 같은 코드 줄을 추가하면 파일은 이제 다음과 같습니다.

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > 코드 이해
   >
   > - 추가한 줄은 `Calculate`라는 새 함수를 선언합니다. 더하기, 빼기, 곱하기 및 나누기 등 수학 작업을 실행하는 데 이 함수를 사용합니다.
   > - C++ 코드는 *헤더*(.h) 파일 및 *원본*(.cpp) 파일로 구성됩니다. 다른 여러 파일 확장명은 다양한 컴파일러에서 지원되지만 이러한 확장명이 알아야 할 주요 항목입니다. 함수 및 변수는 일반적으로 *선언* 됩니다. 즉, 헤더 파일에서 이름 및 형식이 지정되고 *구현* 되거나 원본 파일에서 정의가 지정됩니다. 다른 파일에 정의된 코드에 액세스하려면 `#include "filename.h"`를 사용하면 됩니다. 여기서 'filename.h'는 사용할 변수 또는 함수를 선언하는 파일의 이름입니다.
   > - 삭제된 두 줄은 클래스의 *생성자* 및 *소멸자* 를 정의했습니다. 이와 같은 간단한 클래스의 경우 컴파일러가 해당 항목을 만듭니다. 사용법은 이 자습서에서 다루지 않습니다.
   > - 나중에 필요한 코드를 찾기 쉽도록 코드 내용에 따라 해당 코드를 다른 파일로 구성하는 것이 좋습니다. 이 경우에는 `main()` 함수를 포함하는 파일에서 개별적으로 `Calculator` 클래스를 정의하지만 `main()`에서 `Calculator` 클래스를 참조하려고 합니다.

1. 녹색 오류 표시선이 `Calculate`에 나타납니다. .cpp 파일에서 `Calculate` 함수를 정의하지 않았기 때문입니다. 단어를 마우스로 가리키고, 팝업된 전구(이 경우에 스크루드라이버)를 클릭하고, **Calculator.cpp에서 'Calculate'의 정의 만들기** 를 선택합니다.

   ![강조 표시된 Calculator CPP 옵션의 Calculate 정의 만들기를 보여 주는 Visual Studio 2019의 스크린샷](./media/calc-vs2019-create-definition.png "Calculate의 정의 만들기")

   다른 파일에서 이루어진 코드 변경 내용의 피킹을 제공하는 팝업이 나타납니다. 코드를 *Calculator.cpp* 에 추가했습니다.

   ![Calculate의 정의가 표시된 팝업 항목](./media/calc-vs2019-pop-up-definition.png "Calculate의 정의가 표시된 팝업 항목")

   현재, 0.0만 반환합니다. 이를 변경해봅시다. **Esc** 키를 눌러 팝업을 닫습니다.

1. 편집기 창에서 *Calculator.cpp* 파일로 전환합니다. .h 파일에서 수행한 대로 `Calculator()` 및 `~Calculator()` 섹션을 제거하고 다음 코드를 `Calculate()`에 추가합니다.

    ```cpp
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > 코드 이해
   >
   > - `Calculate` 함수는 숫자, 연산자 및 두 번째 숫자를 사용한 다음, 숫자에 대해 요청된 작업을 수행합니다.
   > - 스위치 문은 제공된 연산자를 검사하고, 해당 작업에 해당하는 사례만을 실행합니다. 프로그램이 중단되지 않도록 사용자가 허용되지 않는 연산자를 입력하는 경우에는 기본 사례로 대체됩니다. 일반적으로 더 세련된 방식으로 잘못된 사용자 입력을 처리하는 것이 좋지만 이 자습서에서는 다루지 않습니다.
   > - **`double`** 키워드는 10진수를 지원하는 수 형식을 나타냅니다. 이렇게 하면 계산기는 10진수 수학 및 정수 계산을 모두 처리할 수 있습니다. 코드 시작 부분의 **`double`** 로 인해(이 함수의 반환 형식을 나타냄) 항상 이러한 숫자를 반환하도록 `Calculate` 함수가 필요합니다. 이 때문에 기본 사례에서도 0.0을 반환합니다.
   > - .h 파일은 *프로토타입* 함수를 선언합니다. 해당 함수는 컴파일러에 미리 필요한 매개 변수 및 예상되는 반환 형식을 지시합니다. .cpp 파일에는 함수의 구현 세부 정보가 포함됩니다.

이 시점에서 코드를 빌드하고 실행하는 경우 수행할 작업을 물은 후에 종료됩니다. 다음으로, 몇 가지 계산을 수행하도록 `main` 함수를 수정합니다.

### <a name="to-call-the-calculator-class-member-functions"></a>계산기 클래스 멤버 함수를 호출하려면

1. 이제 *CalculatorTutorial.cpp* 에서 `main` 함수를 업데이트하겠습니다.

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > 코드 이해
   >
   > - C++ 프로그램이 항상 `main()` 함수에서 시작하므로 거기에서 다른 코드를 호출해야 합니다. 따라서 `#include` 문이 필요합니다.
   > - 일부 초기 변수(`x`, `y`, `oper` 및 `result`)를 선언하여 첫 번째 숫자, 두 번째 숫자, 연산자 및 최종 결과를 각각 저장합니다. 정의되지 않은 동작을 방지하려면 몇 가지 초기 값을 입력하는 것이 좋습니다. 여기서는 이를 수행했습니다.
   > - `Calculator c;` 줄은 'c'라는 개체를 `Calculator` 클래스의 인스턴스로 선언합니다. 클래스 자체는 계산기 작동 방식의 청사진입니다. 개체는 계산을 수행하는 특정 계산기입니다.
   > - `while (true)` 문은 루프입니다. `()` 내의 조건이 true인 경우 루프 내부의 코드는 계속 반복해서 실행됩니다. 조건이 단순히 **`true`** 로 나열되므로 항상 true입니다. 따라서 루프가 계속 실행됩니다. 프로그램을 닫으려면 사용자가 수동으로 콘솔 창을 닫아야 합니다. 그렇지 않으면 프로그램은 항상 새 입력을 기다리며 대기합니다.
   > - `cin` 키워드는 사용자로부터 입력을 허용하는 데 사용됩니다. 이 입력 스트림은 사용자 입력이 필수 사양과 일치한다고 가정하기 위해 콘솔 창에 입력된 텍스트 줄을 처리하고, 나열된 변수 각각에 배치할 수 있을 만큼 지능적입니다. 다른 형식의 입력(예: 세 개 이상의 숫자)을 허용하도록 이 줄을 수정할 수 있지만 `Calculate()` 함수가 이를 처리하도록 업데이트되어야 합니다.
   > - `c.Calculate(x, oper, y);` 식은 이전에 정의된 `Calculate` 함수를 호출하고, 입력된 입력 값을 제공합니다. 그러면 함수는 `result`에 저장된 수를 반환합니다.
   > - 마지막으로, `result`가 콘솔에 출력되므로 계산 결과가 사용자에게 표시됩니다.

### <a name="build-and-test-the-code-again"></a>코드 다시 빌드 및 테스트

이제 프로그램을 다시 테스트하여 모든 항목이 제대로 작동하는지 확인하겠습니다.

1. **Ctrl+F5** 키를 눌러 앱을 다시 빌드하고 시작합니다.

1. `5 + 5`를 입력하고 **Enter** 키를 누릅니다. 결과가 10인지 확인합니다.

   ![5+5의 올바른 결과를 보여 주는 Visual Studio 2019 Microsoft Visual Studio 디버그 콘솔의 스크린샷](./media/calc-vs2019-five-plus-five.png "5 + 5의 결과")

## <a name="debug-the-app"></a>앱 디버그

사용자가 콘솔 창에 무엇이든 입력할 수 있으므로 계산기가 예상대로 일부 입력을 처리하는지 확인하겠습니다. 프로그램을 실행하는 대신 디버깅하여 수행 내용을 단계별로 자세히 검사할 수 있습니다.

### <a name="to-run-the-app-in-the-debugger"></a>디버거에서 앱을 실행하려면

1. 사용자가 입력하도록 요청받은 직후 `result = c.Calculate(x, oper, y);` 줄에 중단점을 설정합니다. 중단점을 설정하려면 편집기 창의 왼쪽 가장자리를 따라 있는 회색 세로 막대의 줄 옆을 클릭합니다. 빨간색 점이 나타납니다.

   ![중단점을 나타내는 빨간 점을 보여 주는 Visual Studio 2019의 스크린샷](./media/calc-vs2019-set-breakpoint.png "중단점 설정")

   이제 프로그램을 디버깅할 때 항상 해당 줄에서 실행이 일시 중지됩니다. 프로그램이 간단한 케이스에 대해 작동하는 대략적인 아이디어가 이미 있습니다. 매번 실행을 일시 정지하지 않으므로 조건부로 중단점을 만듭니다.

1. 중단점을 나타내는 빨간색 점을 마우스 오른쪽 단추로 클릭하고, **조건** 을 선택합니다. 조건의 편집 상자에 `(y == 0) && (oper == '/')`를 입력합니다. 완료되면 **닫기** 단추를 선택합니다. 조건이 자동으로 저장됩니다.

   ![중단점 설정 섹션과 true 값에 추가된 조건을 보여 주는 Visual Studio 2019의 스크린샷](./media/calc-vs2019-conditional-breakpoint.png "조건부 중단점 설정")

   이제 0으로 나누기를 시도하는 경우에 특히 중단점에서 실행을 일시 중지합니다.

1. 프로그램을 디버그하려면 **F5** 키를 누르거나 **로컬 Windows 디버거** 녹색 화살표 아이콘이 있는 도구 모음 단추를 선택합니다. 콘솔 앱에서 "5 - 0" 같은 코드를 입력하는 경우 프로그램은 정상적으로 작동하고 계속 실행됩니다. 그러나 "10 / 0"을 입력하면 중단점에서 일시 중지됩니다. 연산자와 숫자 사이에 공백을 배치할 수도 있습니다. `cin`은 입력을 적절하게 구문 분석할 수 있을 만큼 지능적입니다.

   ![조건부 중단점에서 프로그램이 일시 중지되었음을 보여 주는 Visual Studios 2019의 스크린샷](./media/calc-vs2019-debug-breakpoint.png "조건부 중단점에서 일시 중지")

### <a name="useful-windows-in-the-debugger"></a>디버거에서 유용한 창

코드를 디버그할 때마다 몇 개의 새 창이 표시되는 것을 확인할 수 있습니다. 이러한 창은 디버깅 환경을 지원할 수 있습니다. **자동** 창을 살펴보세요. **자동** 창에서는 적어도 3개 줄 이전부터 현재 줄까지 사용된 변수의 현재 값을 보여 줍니다. 해당 함수의 모든 변수를 보려면 **로컬** 창으로 전환합니다. 실제로 해당 항목이 프로그램에 미치는 영향을 확인하도록 디버깅하는 동안 이러한 변수 값을 수정할 수 있습니다. 이 사례에서는 해당 항목을 그대로 둡니다.

   ![Visual Studio 2019의 로컬 창 스크린샷](./media/calc-vs2019-debug-locals.png "로컬 창")

코드 자체에 있는 변수를 마우스로 가리키기만 하면 실행이 현재 일시 중지된 경우 현재 값을 확인할 수도 있습니다. 먼저 클릭하여 편집기 창에 포커스가 맞춰졌는지 확인합니다.

   ![변수의 값을 표시하는 도구 설명을 보여 주는 Visual Studio 2019의 스크린샷](./media/calc-vs2019-hover-tooltip.png "마우스로 가리켜서 현재 변수 값 보기")

### <a name="to-continue-debugging"></a>디버깅을 계속하려면

1. 왼쪽의 노란색 줄은 현재 실행 지점을 보여줍니다. 현재 줄이 `Calculate`을 호출하므로 **F11** 키를 눌러 해당 함수에서 **한 단계씩 코드를 실행** 합니다. `Calculate` 함수의 본문에서 직접 찾아봅니다. **한 단계씩 코드 실행** 에 주의하세요. 코드를 너무 많이 실행하면 많은 시간을 낭비할 수 있습니다. 표준 라이브러리 함수를 포함하여, 현재 줄에서 사용하는 코드로 이동합니다.

1. 이제 실행 지점이 `Calculate` 함수의 시작 부분에 있으므로 **F10** 키를 눌러 프로그램을 실행하는 중에 다음 줄로 이동합니다. **F10** 키는 **프로시저 단위 실행** 이라고도 합니다. **프로시저 단위 실행** 을 사용하여 줄의 각 파트에서 발생한 내용의 세부 정보를 살펴보지 않고 줄을 이동할 수 있습니다. (`Calculate`의 본문에 도달하기 위해 수행한 대로) 다른 곳에서 호출되는 코드에 대해 더 심층적으로 알아보지 않으려면 일반적으로 **한 단계씩 코드 실행** 대신 **프로시저 단위 실행** 을 사용해야 합니다.

1. 다른 파일에서 `main()` 함수로 다시 이동할 때까지 계속 **F10** 키를 사용하여 각 줄을 **프로시저 단위 실행** 하고, `cout` 줄에서 중지합니다.

   프로그램이 예정된 내용을 수행하는 것처럼 보입니다. 첫 번째 숫자를 사용하고 두 번째로 나눕니다. `cout` 줄에서 `result` 변수를 마우스로 가리키거나 **자동** 창에서 `result`를 살펴봅니다. 올바르지 않은 것 같은 “inf”로 값이 등록된 것을 확인하게 됩니다. 해당 값을 수정하세요. `cout` 줄은 `result`에 저장된 모든 값을 출력하므로 **F10** 키를 사용하여 추가로 한 줄을 실행하면 콘솔 창에서는 다음을 표시합니다.

   ![0으로 나누기 결과를 보여 주는 Visual Studio 2019 Microsoft Visual Studio 디버그 콘솔의 스크린샷](./media/calc-vs2019-divide-by-zero-fail.png "0으로 나눈 결과")

   이 결과는 0으로 나누기가 정의되지 않았기 때문에 발생합니다. 따라서 프로그램에는 요청된 작업에 대한 숫자 응답이 포함되지 않습니다.

### <a name="to-fix-the-divide-by-zero-error"></a>"0으로 나누기" 오류를 해결하려면

사용자가 문제를 이해할 수 있도록 0으로 나누기를 더욱 원활하게 처리해 보겠습니다.

1. *CalculatorTutorial.cpp* 를 다음과 같이 변경합니다. (**편집하며 계속하기** 라는 디버거 기능을 통해 편집한 대로 프로그램이 실행되도록 둘 수 있습니다.)

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. 이제 **F5** 키를 한 번 누릅니다. 사용자 입력에 대한 요청을 일시 중지해야 할 때까지 계속 프로그램을 실행합니다. `10 / 0`을 다시 입력하세요. 이제 더 유용한 메시지가 출력됩니다. 사용자에게는 추가 입력 메시지가 표시되고, 프로그램은 계속 정상적으로 실행됩니다.

   ![변경 후 최종 결과를 보여 주는 Visual Studio 2019 Microsoft Visual Studio 디버그 콘솔의 스크린샷](./media/calc-vs2019-final-verification.png "변경 후의 최종 결과")

   > [!Note]
   > 디버깅 모드에서 코드를 편집하면 코드가 부실해질 위험이 있습니다. 이 문제는 디버거가 계속 이전 코드를 실행하고 변경 내용을 사용하여 업데이트하지 않는 경우에 발생합니다. 디버거는 문제가 발생했음을 알려주는 대화 상자를 표시합니다. 경우에 따라 **F5** 키를 눌러 실행 중인 코드를 새로 고쳐야 합니다. 특히 함수를 변경하는 동시에 실행 지점이 해당 함수 내에 있는 경우 함수에서 나간 다음, 다시 들어와서 업데이트된 코드를 가져와야 합니다. 이 방법이 어떤 이유로 작동하지 않고 오류 메시지가 표시되는 경우 IDE의 맨 위에 있는 메뉴 아래의 도구 모음에서 빨간색 사각형을 클릭하여 디버깅을 중지한 다음, **F5** 키를 다시 입력하거나 도구 모음에서 중지 단추 옆에 있는 녹색 "재생" 화살표를 선택하여 디버깅을 시작할 수 있습니다.

   > 실행 및 디버그 바로 가기 이해
   >
   > - **F5** 키(또는 **디버그** > **디버깅 시작**)는 디버깅 세션이 활성 상태가 아닌 경우 디버깅 세션을 시작하고, 중단점에 도달하거나 프로그램에 사용자 입력이 필요할 때까지 프로그램을 실행합니다. 사용자 입력이 필요하지 않고 중단점에 도달할 수 없는 경우 프로그램 실행이 완료되면 프로그램이 종료되고 콘솔 창이 닫힙니다. "Hello World"와 같은 프로그램을 실행한 경우 **F5** 키를 입력하여 창을 열어두기 전에 **Ctrl+F5** 키를 사용하거나 중단점을 설정합니다.
   > - **Ctrl+F5** 키(또는 **디버그** > **디버깅하지 않고 시작**)는 디버그 모드로 전환하지 않고 애플리케이션을 실행합니다. 이 방법이 디버깅보다 약간 빠릅니다. 또한 프로그램 실행이 완료되면 콘솔 창을 열어 둡니다.
   > - **F10** 키(**프로시저 단위 실행** 이라고도 함)를 통해 코드를 한 줄씩 반복하고, 코드를 실행하는 방법 및 실행의 각 단계에서 변수 값을 시각화할 수 있습니다.
   > - **F11** 키(**한 단계씩 코드 실행** 이라고도 함)는 실행 줄에서 호출되는 함수를 한 단계씩 코드 실행한다는 점을 제외하고 **프로시저 단위 실행** 과 유사하게 작동합니다. 예를 들어 실행되는 줄이 함수를 호출하는 경우 **F11** 키를 누르면 함수의 본문에 포인터를 이동시킵니다. 따라서 시작한 줄로 이동하기 전에 실행되는 함수의 코드를 수행할 수 있습니다. **F10** 키를 누르면 함수 호출을 프로시저 단위로 실행하고 다음 줄로 이동합니다. 여전히 함수 호출이 실행되지만 프로그램은 표시되는 내용을 일시 중지하지 않습니다.

### <a name="close-the-app"></a>앱 닫기

- 계속 실행 중이면 계산기 앱의 콘솔 창을 닫습니다.

## <a name="the-finished-app"></a>완성된 앱

지금까지 계산기 앱의 코드를 완료하고, Visual Studio에서 빌드하고 디버깅했습니다.

## <a name="next-steps"></a>다음 단계

[C++용 Visual Studio에 대한 자세한 정보](https://devblogs.microsoft.com/cppblog/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end

::: moniker range="<msvc-160"

C++ 프로그래머의 일반적인 시작점은 명령줄에서 실행되는 "Hello, world!" 애플리케이션입니다. 이 문서를 통해 Visual Studio를 사용해 좀 더 어려운 문제인 계산기 앱을 개발해 보겠습니다.

## <a name="prerequisites"></a>사전 요구 사항

- 컴퓨터에서 설치되고 실행 중인 **C++ 워크로드를 사용하여 데스크톱 개발** 을 위해 Visual Studio를 설치합니다. 아직 설치되지 않은 경우 [Visual Studio에서 C++ 지원 설치](../build/vscpp-step-0-installation.md)를 참조하세요.

## <a name="create-your-app-project"></a>앱 프로젝트 만들기

Visual Studio는 ‘프로젝트’를 사용하여 앱에 대한 코드를 구성하고 ‘솔루션’을 사용하여 프로젝트를 구성합니다. 프로젝트에는 앱을 빌드하는 데 사용되는 모든 옵션, 구성 및 규칙이 포함됩니다. 또한 프로젝트의 모든 파일과 외부 파일 간의 관계를 관리합니다. 앱을 만들려면 먼저 새 프로젝트 및 솔루션을 만듭니다.

1. Visual Studio의 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다. **새 프로젝트** 창이 열립니다.

2. 왼쪽 세로 막대에서 **Visual C++** 를 선택했는지 확인합니다. 중앙에서 **Windows 콘솔 애플리케이션** 을 선택합니다.

3. 맨 아래에 있는 **이름** 편집 상자에서 새 프로젝트의 이름을 *CalculatorTutorial* 이라고 지정하고, **확인** 을 선택합니다.

   ![새 프로젝트 대화 상자](./media/calculator-new-project-dialog.png "새 프로젝트 대화 상자")

   비어 있는 C++ Windows 콘솔 애플리케이션이 생성됩니다. 콘솔 애플리케이션은 Windows 콘솔 창을 사용하여 출력을 표시하고 사용자 입력을 허용합니다. Visual Studio에서 편집기 창이 열리고 생성된 코드를 보여 줍니다.

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n";
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>새 앱이 빌드되고 실행되는지 확인

새 Windows 콘솔 애플리케이션의 템플릿은 간단한 C++ "Hello World" 앱을 생성합니다. 이 시점에서는 Visual Studio가 IDE에서 직접 만든 앱을 빌드하고 실행하는 방법을 확인할 수 있습니다.

1. 프로젝트를 빌드하려면 **빌드** 메뉴에서 **솔루션 빌드** 를 선택합니다. **출력** 창은 빌드 프로세스의 결과를 보여줍니다.

   ![빌드 프로세스의 결과를 보여 주는 출력 창이 있는 Visual Studio의 스크린샷](./media/calculator-initial-build-output.png "프로젝트 빌드")

1. 코드를 실행하려면 메뉴 모음에서 **디버그**, **디버깅하지 않고 시작** 을 선택합니다.

   ![코드가 성공적으로 실행되었음을 보여 주는 Microsoft Visual Studio 디버그 콘솔의 스크린샷](./media/calculator-hello-world-console.png "프로젝트 시작")

   콘솔 창이 열린 다음, 앱을 실행합니다. Visual Studio에서 콘솔 앱을 시작하면 코드를 실행한 다음, "계속하려면 아무 키나 누르세요. 을 선택합니다. "를 표시하여 출력을 볼 수 있도록 합니다. 지금까지 Visual Studio에서 첫 번째 "Hello, world!" 콘솔 앱을 만들었습니다.

1. 키를 눌러서 콘솔 창을 닫고 Visual Studio로 돌아갑니다.

이제 예상한 대로 코드가 계속 작동하는지 확인하기 위해 앱을 변경할 때마다 빌드하고 실행할 도구가 설치되었습니다. 그렇지 않은 경우 디버그하는 방법을 나중에 보여드리겠습니다.

## <a name="edit-the-code"></a>코드 편집

이제 이 템플릿의 코드를 계산기 앱으로 바꾸겠습니다.

1. *CalculatorTutorial.cpp* 파일에서 이 예제와 일치하도록 코드를 편집합니다.

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > 코드 이해:
   >
   > - `#include` 문을 통해 다른 파일에 있는 코드를 참조할 수 있습니다. 경우에 따라 파일 이름이 꺾쇠 괄호( **\<\>** )로 묶여서 표시될 수 있습니다. 아니면 따옴표( **“ ”** )로 묶일 수 있습니다. 일반적으로, C++ 표준 라이브러리를 참조할 때 꺾쇠 괄호를 사용하는 반면 다른 파일의 경우 따옴표를 사용합니다.
   > - `#include "pch.h"`(또는 Visual Studio 2017 및 이전 버전`#include "stdafx.h"`) 줄은 미리 컴파일된 헤더라는 항목을 참조합니다. 해당 항목은 컴파일 시간을 개선하기 위해 전문 프로그래머에 의해 자주 사용되지만 이 자습서에서 다루지 않습니다.
   > - `using namespace std;` 줄은 이 파일에 사용할 C++ 표준 라이브러리의 항목을 가져오도록 컴파일러에 지시합니다. 이 줄이 없으면 라이브러리의 각 키워드에서는 해당 범위를 나타내는 `std::`가 앞에 와야 합니다. 예를 들어 해당 줄이 없으면 `cout`에 대한 참조는 각각 `std::cout`와 같이 작성되어야 합니다. 코드를 정리하기 위해 **`using`** 문을 추가합니다.
   > - C++인 표준 출력으로 인쇄하기 위해 `cout` 키워드를 사용합니다. **\<\<** 연산자는 어떤 항목이든지 표준 출력에 보내도록 컴파일러에 지시합니다.
   > - **endl** 키워드는 Enter 키와 같이 줄을 종료하고 커서를 다음 줄로 이동시킵니다. ""에 포함된 문자열 내에 `\n`을 배치하여 동일한 작업을 수행하는 것이 좋습니다. `endl`이 항상 버퍼를 플러시하고 프로그램의 성능을 저하시킬 수 있지만 매우 작은 앱이므로 가독성을 위해 대신 `endl`을 사용합니다.
   > - C++ 문은 항상 세미콜론으로 끝나야 하며, C++ 애플리케이션에는 항상 `main()` 함수가 포함되어야 합니다. 이 함수는 시작 시 프로그램이 실행하는 내용입니다. 코드를 사용하기 위해 `main()`에서 액세스할 수 있어야 합니다.

1. 파일을 저장하려면 **Ctrl+S** 를 선택하거나 IDE의 위쪽 가까이에서 **저장** 아이콘, 메뉴 모음의 도구 모음에서 플로피 디스크 아이콘을 선택하세요.

1. 애플리케이션을 실행하려면 **Ctrl+F5** 키를 누르거나 **디버그** 메뉴로 이동하고 **디버깅하지 않고 시작** 을 선택하세요. **이 프로젝트가 만료되었습니다.** 라는 문구의 팝업이 표시되면 **이 대화 상자를 다시 표시 안 함** 을 선택한 다음, **예** 를 선택하여 애플리케이션을 빌드할 수 있습니다. 코드에서 지정된 텍스트가 표시되는 콘솔 창이 나타납니다.

   ![애플리케이션 빌드 시작](./media/calculator-first-launch.gif "애플리케이션 빌드 시작")

1. 작업이 완료되면 콘솔 창을 닫습니다.

## <a name="add-code-to-do-some-math"></a>일부 계산을 수행하는 코드 추가

일부 수학 논리를 추가할 차례입니다.

### <a name="to-add-a-calculator-class"></a>계산기 클래스를 추가하려면

1. **프로젝트** 메뉴로 이동하고, **클래스 추가** 를 선택합니다. **클래스 이름** 편집 상자에 *계산기* 를 입력합니다. **확인** 을 선택합니다. 2개의 새 파일이 프로젝트에 추가됩니다. 변경된 파일을 모두 한 번에 저장하려면 **Ctrl+Shift+S** 키를 누르세요. **파일** > **모두 저장** 의 바로 가기 키입니다. **저장** 단추 옆에 있는 두 개의 플로피 디스크 아이콘인 **모두 저장** 에 대한 도구 모음 단추이기도 합니다. 일반적으로, **모두 저장** 을 자주 수행하는 것이 좋습니다. 그러면 파일을 저장할 때 누락하지 않게 됩니다.

   ![클래스 추가 대화 상자를 열고 클래스 이름 필드에 Calculator를 입력한 후 확인을 선택하는 사용자를 보여 주는 짧은 동영상](./media/calculator-create-class.gif "계산기 클래스 만들기")

   클래스는 특정 작업을 수행하는 개체의 청사진과 비슷합니다. 이 경우에는 계산기 및 계산기의 작동 방식을 정의합니다. 위에서 사용한 **클래스 추가** 마법사는 클래스와 동일한 이름을 가진 .h 및 .cpp 파일을 만들었습니다. IDE의 측면에 표시되는 **솔루션 탐색기** 창에서 프로젝트 파일의 전체 목록을 볼 수 있습니다. 창이 표시되지 않으면 메뉴 모음에서 **보기** > **솔루션 탐색기** 를 선택하여 열 수 있습니다.

   ![Calculator Tutorial 프로젝트가 표시된 솔루션 탐색기 창의 스크린샷](./media/calculator-solution-explorer.png "솔루션 탐색기")

   이제 편집기에는 다음과 같은 세 가지 탭이 열려 있습니다. *CalculatorTutorial.cpp*, *Calculator.h* 및 *Calculator.cpp* 실수로 그중 하나를 닫은 경우 **솔루션 탐색기** 창에서 두 번 클릭하여 다시 열 수 있습니다.

1. 생성된 `Calculator();` 및 `~Calculator();` 줄이 필요하지 않으므로 **Calculator.h** 에서 제거하세요. 다음으로, 다음과 같은 코드 줄을 추가하면 파일은 이제 다음과 같습니다.

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > 코드 이해
   >
   > - 추가한 줄은 `Calculate`라는 새 함수를 선언합니다. 더하기, 빼기, 곱하기 및 나누기 등 수학 작업을 실행하는 데 이 함수를 사용합니다.
   > - C++ 코드는 *헤더*(.h) 파일 및 *원본*(.cpp) 파일로 구성됩니다. 다른 여러 파일 확장명은 다양한 컴파일러에서 지원되지만 이러한 확장명이 알아야 할 주요 항목입니다. 함수 및 변수는 일반적으로 *선언* 됩니다. 즉, 헤더 파일에서 이름 및 형식이 지정되고 *구현* 되거나 원본 파일에서 정의가 지정됩니다. 다른 파일에 정의된 코드에 액세스하려면 `#include "filename.h"`를 사용하면 됩니다. 여기서 'filename.h'는 사용할 변수 또는 함수를 선언하는 파일의 이름입니다.
   > - 삭제된 두 줄은 클래스의 *생성자* 및 *소멸자* 를 정의했습니다. 이와 같은 간단한 클래스의 경우 컴파일러가 해당 항목을 만듭니다. 사용법은 이 자습서에서 다루지 않습니다.
   > - 나중에 필요한 코드를 찾기 쉽도록 코드 내용에 따라 해당 코드를 다른 파일로 구성하는 것이 좋습니다. 이 경우에는 `main()` 함수를 포함하는 파일에서 개별적으로 `Calculator` 클래스를 정의하지만 `main()`에서 `Calculator` 클래스를 참조하려고 합니다.

1. 녹색 오류 표시선이 `Calculate`에 나타납니다. .cpp 파일에서 `Calculate` 함수를 정의하지 않았기 때문입니다. 단어를 마우스로 가리키고, 팝업된 전구를 클릭하고, **Calculator.cpp에서 'Calculate'의 정의 만들기** 를 선택합니다. 다른 파일에서 이루어진 코드 변경 내용의 피킹을 제공하는 팝업이 나타납니다. 코드를 *Calculator.cpp* 에 추가했습니다.

   ![Calculator CPP 옵션에서 Calculate 정의 만들기를 선택하는 사용자를 보여 주는 짧은 동영상](./media/calculator-create-definition.gif "Calculate의 정의 만들기")

   현재, 0.0만 반환합니다. 이를 변경해봅시다. **Esc** 키를 눌러 팝업을 닫습니다.

1. 편집기 창에서 *Calculator.cpp* 파일로 전환합니다. .h 파일에서 수행한 대로 `Calculator()` 및 `~Calculator()` 섹션을 제거하고 다음 코드를 `Calculate()`에 추가합니다.

    ```cpp
    #include "pch.h"
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > 코드 이해
   >
   > - `Calculate` 함수는 숫자, 연산자 및 두 번째 숫자를 사용한 다음, 숫자에 대해 요청된 작업을 수행합니다.
   > - 스위치 문은 제공된 연산자를 검사하고, 해당 작업에 해당하는 사례만을 실행합니다. 프로그램이 중단되지 않도록 사용자가 허용되지 않는 연산자를 입력하는 경우에는 기본 사례로 대체됩니다. 일반적으로 더 세련된 방식으로 잘못된 사용자 입력을 처리하는 것이 좋지만 이 자습서에서는 다루지 않습니다.
   > - **`double`** 키워드는 10진수를 지원하는 수 형식을 나타냅니다. 이렇게 하면 계산기는 10진수 수학 및 정수 계산을 모두 처리할 수 있습니다. 코드 시작 부분의 **`double`** 로 인해(이 함수의 반환 형식을 나타냄) 항상 이러한 숫자를 반환하도록 `Calculate` 함수가 필요합니다. 이 때문에 기본 사례에서도 0.0을 반환합니다.
   > - .h 파일은 *프로토타입* 함수를 선언합니다. 해당 함수는 컴파일러에 미리 필요한 매개 변수 및 예상되는 반환 형식을 지시합니다. .cpp 파일에는 함수의 구현 세부 정보가 포함됩니다.

이 시점에서 코드를 빌드하고 실행하는 경우 수행할 작업을 물은 후에 종료됩니다. 다음으로, 몇 가지 계산을 수행하도록 `main` 함수를 수정합니다.

### <a name="to-call-the-calculator-class-member-functions"></a>계산기 클래스 멤버 함수를 호출하려면

1. 이제 *CalculatorTutorial.cpp* 에서 `main` 함수를 업데이트하겠습니다.

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > 코드 이해
   >
   > - C++ 프로그램이 항상 `main()` 함수에서 시작하므로 거기에서 다른 코드를 호출해야 합니다. 따라서 `#include` 문이 필요합니다.
   > - 일부 초기 변수(`x`, `y`, `oper` 및 `result`)를 선언하여 첫 번째 숫자, 두 번째 숫자, 연산자 및 최종 결과를 각각 저장합니다. 정의되지 않은 동작을 방지하려면 몇 가지 초기 값을 입력하는 것이 좋습니다. 여기서는 이를 수행했습니다.
   > - `Calculator c;` 줄은 'c'라는 개체를 `Calculator` 클래스의 인스턴스로 선언합니다. 클래스 자체는 계산기 작동 방식의 청사진입니다. 개체는 계산을 수행하는 특정 계산기입니다.
   > - `while (true)` 문은 루프입니다. `()` 내의 조건이 true인 경우 루프 내부의 코드는 계속 반복해서 실행됩니다. 조건이 단순히 **`true`** 로 나열되므로 항상 true입니다. 따라서 루프가 계속 실행됩니다. 프로그램을 닫으려면 사용자가 수동으로 콘솔 창을 닫아야 합니다. 그렇지 않으면 프로그램은 항상 새 입력을 기다리며 대기합니다.
   > - `cin` 키워드는 사용자로부터 입력을 허용하는 데 사용됩니다. 이 입력 스트림은 사용자 입력이 필수 사양과 일치한다고 가정하기 위해 콘솔 창에 입력된 텍스트 줄을 처리하고, 나열된 변수 각각에 배치할 수 있을 만큼 지능적입니다. 다른 형식의 입력(예: 세 개 이상의 숫자)을 허용하도록 이 줄을 수정할 수 있지만 `Calculate()` 함수가 이를 처리하도록 업데이트되어야 합니다.
   > - `c.Calculate(x, oper, y);` 식은 이전에 정의된 `Calculate` 함수를 호출하고, 입력된 입력 값을 제공합니다. 그러면 함수는 `result`에 저장된 수를 반환합니다.
   > - 마지막으로, `result`가 콘솔에 출력되므로 계산 결과가 사용자에게 표시됩니다.

### <a name="build-and-test-the-code-again"></a>코드 다시 빌드 및 테스트

이제 프로그램을 다시 테스트하여 모든 항목이 제대로 작동하는지 확인하겠습니다.

1. **Ctrl+F5** 키를 눌러 앱을 다시 빌드하고 시작합니다.

1. `5 + 5`를 입력하고 **Enter** 키를 누릅니다. 결과가 10인지 확인합니다.

   ![5+5의 올바른 결과를 보여 주는 Microsoft Visual Studio 디버그 콘솔의 스크린샷](./media/calculator-five-plus-five.png "5 + 5의 결과")

## <a name="debug-the-app"></a>앱 디버그

사용자가 콘솔 창에 무엇이든 입력할 수 있으므로 계산기가 예상대로 일부 입력을 처리하는지 확인하겠습니다. 프로그램을 실행하는 대신 디버깅하여 수행 내용을 단계별로 자세히 검사할 수 있습니다.

### <a name="to-run-the-app-in-the-debugger"></a>디버거에서 앱을 실행하려면

1. 사용자가 입력하도록 요청받은 직후 `result = c.Calculate(x, oper, y);` 줄에 중단점을 설정합니다. 중단점을 설정하려면 편집기 창의 왼쪽 가장자리를 따라 있는 회색 세로 막대의 줄 옆을 클릭합니다. 빨간색 점이 나타납니다.

   ![중단점을 나타내는 빨간 점을 만드는 사용자를 보여 주는 짧은 Visual Studio 동영상](./media/calculator-set-breakpoint.gif "중단점 설정")

   이제 프로그램을 디버깅할 때 항상 해당 줄에서 실행이 일시 중지됩니다. 프로그램이 간단한 케이스에 대해 작동하는 대략적인 아이디어가 이미 있습니다. 매번 실행을 일시 정지하지 않으므로 조건부로 중단점을 만듭니다.

1. 중단점을 나타내는 빨간색 점을 마우스 오른쪽 단추로 클릭하고, **조건** 을 선택합니다. 조건의 편집 상자에 `(y == 0) && (oper == '/')`를 입력합니다. 완료되면 **닫기** 단추를 선택합니다. 조건이 자동으로 저장됩니다.

   ![중단점 설정 섹션을 열고 조건부 중단점을 설정하는 사용자를 보여 주는 짧은 Visual Studio 2019 동영상](./media/calculator-conditional-breakpoint.gif "조건부 중단점 설정")

   이제 0으로 나누기를 시도하는 경우에 특히 중단점에서 실행을 일시 중지합니다.

1. 프로그램을 디버그하려면 **F5** 키를 누르거나 **로컬 Windows 디버거** 녹색 화살표 아이콘이 있는 도구 모음 단추를 선택합니다. 콘솔 앱에서 "5 - 0" 같은 코드를 입력하는 경우 프로그램은 정상적으로 작동하고 계속 실행됩니다. 그러나 "10 / 0"을 입력하면 중단점에서 일시 중지됩니다. 연산자와 숫자 사이에 공백을 배치할 수도 있습니다. `cin`은 입력을 적절하게 구문 분석할 수 있을 만큼 지능적입니다.

   ![프로그램이 조건부 중단점에서 일시 중지되었음을 보여 주는 짧은 Visual Studios 동영상](./media/calculator-debug-conditional.gif "조건부 중단점에서 일시 중지")

### <a name="useful-windows-in-the-debugger"></a>디버거에서 유용한 창

코드를 디버그할 때마다 몇 개의 새 창이 표시되는 것을 확인할 수 있습니다. 이러한 창은 디버깅 환경을 지원할 수 있습니다. **자동** 창을 살펴보세요. **자동** 창에서는 적어도 3개 줄 이전부터 현재 줄까지 사용된 변수의 현재 값을 보여 줍니다.

   ![자동 창](./media/calculator-autos.png "자동 창")

해당 함수의 모든 변수를 보려면 **로컬** 창으로 전환합니다. 실제로 해당 항목이 프로그램에 미치는 영향을 확인하도록 디버깅하는 동안 이러한 변수 값을 수정할 수 있습니다. 이 사례에서는 해당 항목을 그대로 둡니다.

   ![로컬 창의 스크린샷](./media/calculator-locals.png "로컬 창")

코드 자체에 있는 변수를 마우스로 가리키기만 하면 실행이 현재 일시 중지된 경우 현재 값을 확인할 수도 있습니다. 먼저 클릭하여 편집기 창에 포커스가 맞춰졌는지 확인합니다.

   ![변수의 값을 표시하는 도구 설명을 보여 주는 짧은 동영상](./media/calculator-hover-tooltip.gif "마우스로 가리켜서 현재 변수 값 보기")

### <a name="to-continue-debugging"></a>디버깅을 계속하려면

1. 왼쪽의 노란색 줄은 현재 실행 지점을 보여줍니다. 현재 줄이 `Calculate`을 호출하므로 **F11** 키를 눌러 해당 함수에서 **한 단계씩 코드를 실행** 합니다. `Calculate` 함수의 본문에서 직접 찾아봅니다. **한 단계씩 코드 실행** 에 주의하세요. 코드를 너무 많이 실행하면 많은 시간을 낭비할 수 있습니다. 표준 라이브러리 함수를 포함하여, 현재 줄에서 사용하는 코드로 이동합니다.

1. 이제 실행 지점이 `Calculate` 함수의 시작 부분에 있으므로 **F10** 키를 눌러 프로그램을 실행하는 중에 다음 줄로 이동합니다. **F10** 키는 **프로시저 단위 실행** 이라고도 합니다. **프로시저 단위 실행** 을 사용하여 줄의 각 파트에서 발생한 내용의 세부 정보를 살펴보지 않고 줄을 이동할 수 있습니다. (`Calculate`의 본문에 도달하기 위해 수행한 대로) 다른 곳에서 호출되는 코드에 대해 더 심층적으로 알아보지 않으려면 일반적으로 **한 단계씩 코드 실행** 대신 **프로시저 단위 실행** 을 사용해야 합니다.

1. 다른 파일에서 `main()` 함수로 다시 이동할 때까지 계속 **F10** 키를 사용하여 각 줄을 **프로시저 단위 실행** 하고, `cout` 줄에서 중지합니다.

   ![Calculate에서 나가기 및 결과 확인](./media/calculator-undefined-zero.gif "Calculate에서 나가기 및 결과 확인")

   프로그램이 예정된 내용을 수행하는 것처럼 보입니다. 첫 번째 숫자를 사용하고 두 번째로 나눕니다. `cout` 줄에서 `result` 변수를 마우스로 가리키거나 **자동** 창에서 `result`를 살펴봅니다. 올바르지 않은 것 같은 “inf”로 값이 등록된 것을 확인하게 됩니다. 해당 값을 수정하세요. `cout` 줄은 `result`에 저장된 모든 값을 출력하므로 **F10** 키를 사용하여 추가로 한 줄을 실행하면 콘솔 창에서는 다음을 표시합니다.

   ![0으로 나누기 결과를 보여 주는 Microsoft Visual Studio 디버그 콘솔의 스크린샷](./media/calculator-divide-by-zero-fail.png "0으로 나눈 결과")

   이 결과는 0으로 나누기가 정의되지 않았기 때문에 발생합니다. 따라서 프로그램에는 요청된 작업에 대한 숫자 응답이 포함되지 않습니다.

### <a name="to-fix-the-divide-by-zero-error"></a>"0으로 나누기" 오류를 해결하려면

사용자가 문제를 이해할 수 있도록 0으로 나누기를 더욱 원활하게 처리해 보겠습니다.

1. *CalculatorTutorial.cpp* 를 다음과 같이 변경합니다. (**편집하며 계속하기** 라는 디버거 기능을 통해 편집한 대로 프로그램이 실행되도록 둘 수 있습니다.)

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. 이제 **F5** 키를 한 번 누릅니다. 사용자 입력에 대한 요청을 일시 중지해야 할 때까지 계속 프로그램을 실행합니다. `10 / 0`을 다시 입력하세요. 이제 더 유용한 메시지가 출력됩니다. 사용자에게는 추가 입력 메시지가 표시되고, 프로그램은 계속 정상적으로 실행됩니다.

   ![변경 후 최종 결과를 보여 주는 Microsoft Visual Studio 디버그 콘솔의 짧은 동영상](./media/calculator-final-verification.gif "변경 후의 최종 결과")

   > [!Note]
   > 디버깅 모드에서 코드를 편집하면 코드가 부실해질 위험이 있습니다. 이 문제는 디버거가 계속 이전 코드를 실행하고 변경 내용을 사용하여 업데이트하지 않는 경우에 발생합니다. 디버거는 문제가 발생했음을 알려주는 대화 상자를 표시합니다. 경우에 따라 **F5** 키를 눌러 실행 중인 코드를 새로 고쳐야 합니다. 특히 함수를 변경하는 동시에 실행 지점이 해당 함수 내에 있는 경우 함수에서 나간 다음, 다시 들어와서 업데이트된 코드를 가져와야 합니다. 이 방법이 어떤 이유로 작동하지 않고 오류 메시지가 표시되는 경우 IDE의 맨 위에 있는 메뉴 아래의 도구 모음에서 빨간색 사각형을 클릭하여 디버깅을 중지한 다음, **F5** 키를 다시 입력하거나 도구 모음에서 중지 단추 옆에 있는 녹색 "재생" 화살표를 선택하여 디버깅을 시작할 수 있습니다.

   > 실행 및 디버그 바로 가기 이해
   >
   > - **F5** 키(또는 **디버그** > **디버깅 시작**)는 디버깅 세션이 활성 상태가 아닌 경우 디버깅 세션을 시작하고, 중단점에 도달하거나 프로그램에 사용자 입력이 필요할 때까지 프로그램을 실행합니다. 사용자 입력이 필요하지 않고 중단점에 도달할 수 없는 경우 프로그램 실행이 완료되면 프로그램이 종료되고 콘솔 창이 닫힙니다. "Hello World"와 같은 프로그램을 실행한 경우 **F5** 키를 입력하여 창을 열어두기 전에 **Ctrl+F5** 키를 사용하거나 중단점을 설정합니다.
   > - **Ctrl+F5** 키(또는 **디버그** > **디버깅하지 않고 시작**)는 디버그 모드로 전환하지 않고 애플리케이션을 실행합니다. 이 방법이 디버깅보다 약간 빠릅니다. 또한 프로그램 실행이 완료되면 콘솔 창을 열어 둡니다.
   > - **F10** 키(**프로시저 단위 실행** 이라고도 함)를 통해 코드를 한 줄씩 반복하고, 코드를 실행하는 방법 및 실행의 각 단계에서 변수 값을 시각화할 수 있습니다.
   > - **F11** 키(**한 단계씩 코드 실행** 이라고도 함)는 실행 줄에서 호출되는 함수를 한 단계씩 코드 실행한다는 점을 제외하고 **프로시저 단위 실행** 과 유사하게 작동합니다. 예를 들어 실행되는 줄이 함수를 호출하는 경우 **F11** 키를 누르면 함수의 본문에 포인터를 이동시킵니다. 따라서 시작한 줄로 이동하기 전에 실행되는 함수의 코드를 수행할 수 있습니다. **F10** 키를 누르면 함수 호출을 프로시저 단위로 실행하고 다음 줄로 이동합니다. 여전히 함수 호출이 실행되지만 프로그램은 표시되는 내용을 일시 중지하지 않습니다.

### <a name="close-the-app"></a>앱 닫기

- 계속 실행 중이면 계산기 앱의 콘솔 창을 닫습니다.

## <a name="the-finished-app"></a>완성된 앱

지금까지 계산기 앱의 코드를 완료하고, Visual Studio에서 빌드하고 디버깅했습니다.

## <a name="next-steps"></a>다음 단계

[C++용 Visual Studio에 대한 자세한 정보](https://devblogs.microsoft.com/cppblog/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end
