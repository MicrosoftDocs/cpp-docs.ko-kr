---
title: '연습: 정적 라이브러리 만들기 및 사용 (C++)'
description: Visual Studio에서 C++를 사용하여 정적 라이브러리(.lib)를 만듭니다.
ms.custom: get-started-article
ms.date: 04/13/2020
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.openlocfilehash: 6cb379baafc506570b1bdc1b286b35c40f8cd0d8
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924379"
---
# <a name="walkthrough-create-and-use-a-static-library"></a>연습: 정적 라이브러리 만들기 및 사용

이 단계별 연습에서는 C++ 앱에 사용할 수 있도록 정적 라이브러리(.lib 파일)를 만드는 방법을 보여 줍니다. 정적 라이브러리를 사용하면 코드를 매우 편리하게 다시 사용할 수 있습니다. 기능이 필요한 모든 애플리케이션에서 동일한 루틴을 다시 구현하는 대신 정적 라이브러리에 한 번만 작성한 다음 애플리케이션에서 루틴을 참조하도록 합니다. 정적 라이브러리에서 연결된 코드는 애플리케이션의 일부가 되므로 코드를 사용하기 위해 다른 파일을 설치할 필요가 없습니다.

이 연습에서는 다음 작업 방법을 배웁니다.

- [정적 라이브러리 프로젝트 만들기](#CreateLibProject)

- [정적 라이브러리에 클래스 추가](#AddClassToLib)

- [정적 라이브러리를 참조하는 C++ 콘솔 앱 만들기](#CreateAppToRefTheLib)

- [앱에서 정적 라이브러리의 기능 사용](#UseLibInApp)

- [앱 실행](#RunApp)

## <a name="prerequisites"></a>사전 요구 사항

C++ 언어의 기본적인 사항을 알고 있어야 합니다.

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a> 정적 라이브러리 프로젝트 만들기

프로젝트를 만드는 방법에 대한 지침은 Visual Studio 버전에 따라 다릅니다. 기본 설정된 버전의 Visual Studio에 대한 설명서를 보려면 **버전** 선택기 컨트롤을 사용하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker range="msvc-160"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>Visual Studio 2019에서 정적 라이브러리 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택하여 **새 프로젝트 만들기** 대화 상자를 엽니다.

1. 대화 상자 맨 위에서 **언어** 를 **C++** 로 설정하고 **플랫폼** 을 **Windows** 로 설정하고 **프로젝트 형식** 을 **라이브러리** 로 설정합니다.

1. 필터링된 프로젝트 형식 목록에서 **Windows 데스크톱 마법사** 를 선택한 후 **다음** 을 선택합니다.

1. **새 프로젝트 구성** 페이지에서 **프로젝트 이름** 상자에 *MathLibrary* 를 입력하여 프로젝트의 이름을 지정합니다. **솔루션 이름** 상자에 *StaticMath* 를 입력합니다. **만들기** 단추를 선택하여 **Windows 데스크톱 프로젝트** 대화 상자를 엽니다.

1. **Windows 데스크톱 프로젝트** 대화 상자의 **애플리케이션 종류** 에서 **정적 라이브러리(.lib)** 를 선택합니다.

1. **추가 옵션** 에서 **미리 컴파일된 헤더** 확인란을 선택 취소합니다(선택된 경우). **빈 프로젝트** 상자를 선택합니다.

1. **확인** 을 클릭하여 프로젝트를 만듭니다.

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>Visual Studio 2017에서 정적 라이브러리 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

1. **새 프로젝트** 대화 상자에서 **설치됨** > **Visual C++**  > **Windows 데스크톱** 을 선택합니다. 가운데 창에서 **Windows 데스크톱 마법사** 를 선택합니다.

1. **이름** 상자에서 프로젝트의 이름(예: *MathLibrary* )을 지정합니다. **솔루션 이름** 상자에서 솔루션 이름(예: *StaticMath* )을 지정합니다. **확인** 단추를 선택합니다.

1. **Windows 데스크톱 프로젝트** 대화 상자의 **애플리케이션 종류** 에서 **정적 라이브러리(.lib)** 를 선택합니다.

1. **추가 옵션** 에서 **미리 컴파일된 헤더** 확인란을 선택 취소합니다(선택된 경우). **빈 프로젝트** 상자를 선택합니다.

1. **확인** 을 클릭하여 프로젝트를 만듭니다.

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>Visual Studio 2015에서 정적 라이브러리 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

1. **새 프로젝트** 대화 상자에서 **설치됨** > **템플릿** > **Visual C++**  > **Win32** 를 선택합니다. 가운데 창에서 **Win32 콘솔 애플리케이션** 을 선택합니다.

1. **이름** 상자에서 프로젝트의 이름(예: *MathLibrary* )을 지정합니다. **솔루션 이름** 상자에서 솔루션 이름(예: *StaticMath* )을 지정합니다. **확인** 단추를 선택합니다.

1. **Win32 애플리케이션 마법사** 에서 **다음** 을 선택합니다.

1. **애플리케이션 설정** 페이지의 **애플리케이션 종류** 아래에서 **정적 라이브러리** 를 선택합니다. **추가 옵션** 에서 **미리 컴파일된 헤더** 확인란을 선택 취소합니다. **마침** 을 선택하여 프로젝트를 만듭니다.

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a> 정적 라이브러리에 클래스 추가

### <a name="to-add-a-class-to-the-static-library"></a>정적 라이브러리에 클래스를 추가하려면

1. 새 클래스에 대한 헤더 파일을 만들려면 **솔루션 탐색기** 에서 마우스 오른쪽 단추를 클릭하여 **MathLibrary** 프로젝트의 바로 가기 메뉴를 연 다음 **추가** > **새 항목** 을 선택합니다.

1. **새 항목 추가** 대화 상자에서 **Visual C++**  > **코드** 를 선택합니다. 가운데 창에서 **헤더 파일 (.h)** 을 선택합니다. 헤더 파일의 이름(예: *MathLibrary.h* )을 지정하고 **추가** 단추를 선택합니다. 거의 빈 헤더 파일이 표시됩니다.

1. 덧셈, 뺄셈, 곱셈, 나눗셈 같은 일반적인 산술 연산을 수행하는 `Arithmetic`라는 클래스에 대한 선언을 추가합니다. 코드는 다음과 비슷합니다.

    ```cpp
    // MathLibrary.h
    #pragma once

    namespace MathLibrary
    {
        class Arithmetic
        {
        public:
            // Returns a + b
            static double Add(double a, double b);

            // Returns a - b
            static double Subtract(double a, double b);

            // Returns a * b
            static double Multiply(double a, double b);

            // Returns a / b
            static double Divide(double a, double b);
        };
    }
    ```

1. 새 클래스에 대한 소스 파일을 만들려면 **솔루션 탐색기** 에서 **MathLibrary** 프로젝트에 대한 바로 가기 메뉴를 연 다음 **추가** > **새 항목** 을 선택합니다.

1. **새 항목 추가** 대화 상자의 가운데 창에서 **C++ 파일(.cpp)** 을 선택합니다. 소스 파일의 이름(예: *MathLibrary.cpp* )을 지정하고 **추가** 단추를 선택합니다. 빈 소스 파일이 표시됩니다.

1. 이 소스 파일을 사용하여 클래스 `Arithmetic`의 기능을 구현합니다. 코드는 다음과 비슷합니다.

    ```cpp
    // MathLibrary.cpp
    // compile with: cl /c /EHsc MathLibrary.cpp
    // post-build command: lib MathLibrary.obj

    #include "MathLibrary.h"

    namespace MathLibrary
    {
        double Arithmetic::Add(double a, double b)
        {
            return a + b;
        }

        double Arithmetic::Subtract(double a, double b)
        {
            return a - b;
        }

        double Arithmetic::Multiply(double a, double b)
        {
            return a * b;
        }

        double Arithmetic::Divide(double a, double b)
        {
            return a / b;
        }
    }
    ```

1. 정적 라이브러리를 빌드하려면 메뉴 모음에서 **빌드** > **솔루션 빌드** 를 선택합니다. 빌드는 다른 프로그램에서 사용할 수 있는 정적 라이브러리 *MathLibrary.lib* 를 만듭니다.

   > [!NOTE]
   > Visual Studio 명령줄에서 빌드하는 경우 프로그램을 빌드하는 데 두 단계를 거쳐야 합니다. 먼저 `cl /c /EHsc MathLibrary.cpp`를 실행하여 코드를 컴파일하고 *MathLibrary.obj* 라는 개체 파일을 만듭니다. `cl` 명령은 Cl.exe 컴파일러를 호출하고, `/c` 옵션은 연결 없는 컴파일을 지정합니다. 자세한 내용은 [/c(링크 없이 컴파일)](../build/reference/c-compile-without-linking.md)을 참조하세요. 두 번째로 `lib MathLibrary.obj`를 실행하여 코드를 연결하고 정적 라이브러리 *MathLibrary.lib* 를 만듭니다. `lib` 명령은 Lib.exe 라이브러리 관리자를 호출합니다. 자세한 내용은 [LIB Reference](../build/reference/lib-reference.md)를 참조하세요.

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a> 정적 라이브러리를 참조하는 C++ 콘솔 앱 만들기

::: moniker range="msvc-160"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>Visual Studio 2019에서 정적 라이브러리를 참조하는 C++ 콘솔 앱을 만들려면

1. **솔루션 탐색기** 에서 맨 위 노드 **솔루션 'StaticMath'** 를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다. **추가** > **새 프로젝트** 를 선택하여 **새 프로젝트 추가** 대화 상자를 엽니다.

1. 대화 상자 맨 위에서 **프로젝트 형식** 필터를 **콘솔** 로 설정합니다.

1. 필터링된 프로젝트 형식 목록에서 **콘솔 앱** 을 선택한 후 **다음** 을 선택합니다. 다음 페이지에서 **이름** 상자에 *MathClient* 를 입력하여 프로젝트의 이름을 지정합니다.

1. **만들기** 단추를 선택하여 클라이언트 프로젝트를 만듭니다.

1. 콘솔 응용 프로그램을 만들면 빈 프로그램이 만들어집니다. 소스 파일의 이름은 앞에서 선택한 이름과 동일하게 설정됩니다. 이 예제에서는 이름이 `MathClient.cpp`입니다.

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>Visual Studio 2017에서 정적 라이브러리를 참조하는 C++ 콘솔 앱을 만들려면

1. **솔루션 탐색기** 에서 맨 위 노드 **솔루션 'StaticMath'** 를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다. **추가** > **새 프로젝트** 를 선택하여 **새 프로젝트 추가** 대화 상자를 엽니다.

1. **새 프로젝트 추가** 대화 상자에서 **설치됨** > **Visual C++**  > **Windows 데스크톱** 을 선택합니다. 가운데 창에서 **Windows 데스크톱 마법사** 를 선택합니다.

1. **이름** 상자에서 프로젝트의 이름(예: *MathClient* )을 지정합니다. **확인** 단추를 선택합니다.

1. **Windows 데스크톱 프로젝트** 대화 상자의 **애플리케이션 종류** 에서 **콘솔 애플리케이션(.exe)** 을 선택합니다.

1. **추가 옵션** 에서 **미리 컴파일된 헤더** 확인란을 선택 취소합니다(선택된 경우).

1. **확인** 을 클릭하여 프로젝트를 만듭니다.

1. 콘솔 응용 프로그램을 만들면 빈 프로그램이 만들어집니다. 소스 파일의 이름은 앞에서 선택한 이름과 동일하게 설정됩니다. 이 예제에서는 이름이 `MathClient.cpp`입니다.

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>Visual Studio 2015에서 정적 라이브러리를 참조하는 C++ 콘솔 앱을 만들려면

1. **솔루션 탐색기** 에서 맨 위 노드 **솔루션 'StaticMath'** 를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다. **추가** > **새 프로젝트** 를 선택하여 **새 프로젝트 추가** 대화 상자를 엽니다.

1. **새 프로젝트 추가** 대화 상자에서 **설치됨** > **Visual C++**  > **Win32** 를 선택합니다. 가운데 창에서 **Win32 콘솔 애플리케이션** 을 선택합니다.

1. **이름** 상자에서 프로젝트의 이름(예: *MathClient* )을 지정합니다. **확인** 단추를 선택합니다.

1. **Win32 애플리케이션 마법사** 대화 상자에서 **다음** 을 선택합니다.

1. **애플리케이션 설정** 페이지의 **애플리케이션 종류** 아래에서 **콘솔 애플리케이션** 이 선택되어 있는지 확인합니다. **추가 옵션** 아래에서 **미리 컴파일된 헤더** 를 선택 취소하고 **빈 프로젝트** 확인란을 선택합니다. **마침** 을 선택하여 프로젝트를 만듭니다.

1. 빈 프로젝트에 소스 파일을 추가하려면 **솔루션 탐색기** 에서 마우스 오른쪽 단추를 클릭하여 **MathClient** 프로젝트의 바로 가기 메뉴를 연 다음 **추가** > **새 항목** 을 선택합니다.

1. **새 항목 추가** 대화 상자에서 **Visual C++**  > **코드** 를 선택합니다. 가운데 창에서 **C++ 파일 (.cpp)** 을 선택합니다. 소스 파일의 이름(예: *MathClient.cpp* )을 지정하고 **추가** 단추를 선택합니다. 빈 소스 파일이 표시됩니다.

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a> 앱에서 정적 라이브러리의 기능 사용

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>앱에서 정적 라이브러리의 기능을 사용하려면

1. 정적 라이브러리에서 수학 루틴을 사용하기 전에 이를 참조해야 합니다. **솔루션 탐색기** 에서 **MathClient** 프로젝트의 바로 가기 메뉴를 연 다음 **추가** > **참조** 를 선택합니다.

1. **참조 추가** 대화 상자에는 참조할 수 있는 라이브러리의 목록이 표시됩니다. **프로젝트** 탭에는 현재 솔루션의 모든 프로젝트와 이들 프로젝트가 참조하는 라이브러리가 나열됩니다. **프로젝트** 탭을 열고 **MathLibrary** 확인란을 선택한 다음 **확인** 단추를 선택합니다.

1. `MathLibrary.h` 헤더 파일을 참조하려면 포함된 디렉터리 경로를 수정해야 합니다. **솔루션 탐색기** 에서 **MathClient** 를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다. **속성** 을 선택하여 **MathClient 속성 페이지** 대화 상자를 엽니다.

1. **MathClient 속성 페이지** 대화 상자에서 **구성** 드롭다운을 **모든 구성** 으로 설정합니다. **플랫폼** 드롭다운을 **모든 플랫폼** 으로 설정합니다.

1. **구성 속성** > **C/C++**  > **일반** 속성 페이지를 선택합니다. **추가 포함 디렉터리** 속성에서 **MathLibrary** 디렉터리의 경로를 지정하거나 해당 경로를 찾습니다.

   디렉터리 경로를 찾으려면

   1. **추가 포함 디렉터리** 속성 값 드롭다운 목록을 열고 **편집** 을 선택합니다.

   1. **추가 포함 디렉터리** 대화 상자에서 텍스트 상자의 상단을 두 번 클릭합니다. 그런 다음 줄의 끝에 있는 줄임표 단추( **...** )를 선택합니다.

   1. **디렉터리 선택** 대화 상자에서 한 수준 위로 이동한 다음 **MathLibrary** 디렉터리를 선택합니다. 그런 다음 **폴더 선택** 단추를 선택하여 선택 내용을 저장합니다.

   1. **추가 포함 디렉터리** 대화 상자에서 **확인** 단추를 선택합니다.

   1. **속성 페이지** 대화 상자에서 **확인** 단추를 선택하여 변경 내용을 프로젝트에 저장합니다.

1. 이제 코드에 `#include "MathLibrary.h"` 헤더를 포함하여 이 앱에서 `Arithmetic` 클래스를 사용할 수 있습니다. `MathClient.cpp`의 내용을 다음 코드로 바꿉니다.

    ```cpp
    // MathClient.cpp
    // compile with: cl /EHsc MathClient.cpp /link MathLibrary.lib

    #include <iostream>
    #include "MathLibrary.h"

    int main()
    {
        double a = 7.4;
        int b = 99;

        std::cout << "a + b = " <<
            MathLibrary::Arithmetic::Add(a, b) << std::endl;
        std::cout << "a - b = " <<
            MathLibrary::Arithmetic::Subtract(a, b) << std::endl;
        std::cout << "a * b = " <<
            MathLibrary::Arithmetic::Multiply(a, b) << std::endl;
        std::cout << "a / b = " <<
            MathLibrary::Arithmetic::Divide(a, b) << std::endl;

        return 0;
    }
    ```

1. 실행 파일을 빌드하려면 메뉴 모음에서 **빌드** > **솔루션 빌드** 를 선택합니다.

## <a name="run-the-app"></a><a name="RunApp"></a> 앱 실행

### <a name="to-run-the-app"></a>앱을 실행하려면

1. **MathClient** 가 기본 프로젝트로 선택되어 있는지 확인합니다. 이를 선택하려면 **솔루션 탐색기** 에서 마우스 오른쪽 단추를 클릭하여 **MathClient** 의 바로 가기 메뉴를 연 다음 **시작 프로젝트로 설정** 을 선택합니다.

1. 프로젝트를 실행하려면 메뉴 모음에서 **디버그** > **디버그하지 않고 시작** 을 선택합니다. 출력은 다음과 비슷합니다.

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>참조

[연습: 동적 연결 라이브러리 만들기 및 사용(C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[데스크톱 애플리케이션(Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
