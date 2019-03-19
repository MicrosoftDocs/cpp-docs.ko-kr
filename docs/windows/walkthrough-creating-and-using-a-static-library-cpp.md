﻿---
title: '연습: 정적 라이브러리 만들기 및 사용(C++)'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.author: corob
ms.openlocfilehash: 506db5ea8e94887d9971b48c06ce8c0d6156dccb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429216"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>연습: 정적 라이브러리 만들기 및 사용(C++)

이 단계별 연습에서는 C++ 앱에 사용할 수 있도록 정적 라이브러리(.lib 파일)를 만드는 방법을 보여 줍니다. 정적 라이브러리를 사용하면 코드를 매우 편리하게 다시 사용할 수 있습니다. 필요한 기능을 작성 하는 모든 앱에서 동일한 루틴을 인해야 하는 대신 정적 라이브러리에서 시간 하 고 앱에서 참조 합니다. 정적 라이브러리에서 연결된 코드는 응용 프로그램의 일부가 되므로 코드를 사용하기 위해 다른 파일을 설치할 필요가 없습니다.

이 연습에서는 다음 작업 방법을 배웁니다.

- [정적 라이브러리 프로젝트 만들기](#CreateLibProject)

- [정적 라이브러리에 클래스 추가](#AddClassToLib)

- [정적 라이브러리를 참조하는 C++ 콘솔 앱 만들기](#CreateAppToRefTheLib)

- [앱에서 정적 라이브러리의 기능 사용](#UseLibInApp)

- [앱 실행](#RunApp)

## <a name="prerequisites"></a>전제 조건

C++ 언어의 기본적인 사항을 알고 있어야 합니다.

##  <a name="CreateLibProject"></a> 정적 라이브러리 프로젝트 만들기

### <a name="to-create-a-static-library-project"></a>정적 라이브러리 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

1. 왼쪽된 창에서 합니다 **새 프로젝트** 대화 상자에서 **설치 됨** > **Visual c + +** 를 선택한 후 **Windows Desktop**. 가운데 창에서 선택 **Windows 데스크톱 마법사**합니다.

   > [!NOTE]
   > Visual Studio 2017 년 보다 오래 된 버전에 **새 프로젝트** 대화 상자에서 **설치 됨** > **템플릿**  >  **Visual c + +** 를 선택한 후 **Win32**합니다. 가운데 창에서 **Win32 콘솔 응용 프로그램**을 선택합니다.

1. *이름*상자에서 프로젝트 이름(예: **MathFuncsLib** )을 지정합니다. *솔루션 이름*상자에서 솔루션 이름(예: **StaticLibrary** )을 지정합니다. **확인** 단추를 선택합니다.

    - Visual Studio 2017의 경우

        1. 아래 **응용 프로그램 종류**를 선택 **정적 라이브러리 (.lib)** 합니다.

        1. 아래 **추가 옵션**의 **미리 컴파일된 헤더** 확인란을 선택 취소 합니다.

        1. 선택할 **확인** 프로젝트를 만듭니다.

    - Visual Studio 2017 년 보다 오래 된 버전

        1. **다음**을 클릭합니다.

        1. 아래 **응용 프로그램 종류**를 선택 **정적 라이브러리**합니다. 다음 확인란 선택을 취소 합니다 **미리 컴파일된 헤더** 확인란을 선택한 **마침**합니다.

##  <a name="AddClassToLib"></a> 정적 라이브러리에 클래스 추가

### <a name="to-add-a-class-to-the-static-library"></a>정적 라이브러리에 클래스를 추가하려면

1. 바로 가기 메뉴를 열고 새 클래스에 대 한 헤더 파일을 만들려면 합니다 **MathFuncsLib** 프로젝트 **솔루션 탐색기**를 선택한 후 **추가**  >   **새 항목**합니다. **새 항목 추가** 대화 상자의 왼쪽 창에 있는 **Visual C++** 에서 **코드**를 선택합니다. 가운데 창에서 **헤더 파일 (.h)** 을 선택합니다. 헤더 파일의 이름(예: *MathFuncsLib.h*)을 지정하고 **추가** 단추를 선택합니다. 빈 헤더 파일이 표시됩니다.

1. 라는 클래스를 추가 `MyMathFuncs` 더하기, 빼기, 곱하기 및 나누기 같은 일반적인 산술 연산을 수행 합니다. 코드는 같아야 합니다.

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]

1. 바로 가기 메뉴를 열고 새 클래스에 대 한 소스 파일을 만들려면 합니다 **MathFuncsLib** 프로젝트 **솔루션 탐색기**를 선택한 후 **추가**  >   **새 항목**합니다. **새 항목 추가** 대화 상자의 왼쪽 창에 있는 **Visual C++** 에서 **코드**를 선택합니다. 가운데 창에서 **C++ 파일 (.cpp)** 을 선택합니다. 소스 파일의 이름(예: *MathFuncsLib.cpp*)을 지정하고 **추가** 단추를 선택합니다. 빈 소스 파일이 표시됩니다.

1. 이 소스 파일을 사용하여 **MyMathFuncs**의 기능을 구현합니다. 코드는 같아야 합니다.

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]

1. 선택 하 여 정적 라이브러리를 컴파일합니다 **빌드합니다** > **솔루션 빌드** 메뉴 모음에서. 컴파일 다른 프로그램에서 사용할 수 있는 정적 라이브러리를 만듭니다.

   > [!NOTE]
   > Visual Studio 명령줄에서 빌드하는 경우 프로그램을 빌드하는 데 두 단계를 거쳐야 합니다. 먼저 실행 `cl /c /EHsc MathFuncsLib.cpp` 라는 개체 파일을 만들고 코드를 컴파일하려면 코드 `MathFuncsLib.obj`합니다. `cl` 명령은 Cl.exe 컴파일러를 호출하고, `/c` 옵션은 연결 없는 컴파일을 지정합니다. 자세한 내용은 [(컴파일 없이 링크 사용)는 /c](../build/reference/c-compile-without-linking.md).) 둘째, 실행 `lib MathFuncsLib.obj` 정적 라이브러리를 만들고 코드를 링크 합니다 `MathFuncsLib.lib`합니다. `lib` 명령은 Lib.exe 라이브러리 관리자를 호출합니다. 자세한 내용은 [LIB Reference](../build/reference/lib-reference.md)를 참조하세요.

##  <a name="CreateAppToRefTheLib"></a> 정적 라이브러리를 참조하는 C++ 콘솔 앱 만들기

### <a name="to-create-a-c-console-app-that-references-the-static-library"></a>정적 라이브러리를 참조하는 C++ 콘솔 앱을 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

1. 왼쪽된 창에서 합니다 **새 프로젝트** 대화 상자에서 **설치 됨** > **Visual c + +** 를 선택한 후 **Windows Desktop**. 가운데 창에서 선택 **Windows 데스크톱 마법사**합니다.

   > [!NOTE]
   > Visual Studio 2017 년 보다 오래 된 버전에 **새 프로젝트** 대화 상자에서 **설치 됨** > **템플릿**  >  **Visual c + +** 를 선택한 후 **Win32**합니다. 가운데 창에서 **Win32 콘솔 응용 프로그램**을 선택합니다.

1. *이름*상자에서 프로젝트 이름(예: **MyExecRefsLib** )을 지정합니다. **솔루션**옆에 있는 드롭다운 목록에서 **솔루션에 추가**를 선택합니다. 이 명령은 정적 라이브러리를 포함 하는 솔루션에 새 프로젝트를 추가 합니다. **확인** 단추를 선택합니다.

    - Visual Studio 2017의 경우

        1. 아래 **응용 프로그램 종류**를 선택 **콘솔 응용 프로그램 (.exe)** 합니다.

        1. 아래 **추가 옵션**의 선택을 취소 합니다 **미리 컴파일된 헤더** 확인란 합니다.

        1. 선택할 **확인** 프로젝트를 만듭니다.

    - Visual Studio 2017 년 보다 오래 된 버전

        1. **다음**을 클릭합니다.

        1. 했는지 **콘솔 응용 프로그램** 을 선택 합니다. 다음 확인 합니다 **빈 프로젝트** 확인란을 선택한 **마침**합니다.

##  <a name="UseLibInApp"></a> 앱에서 정적 라이브러리의 기능 사용

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>앱에서 정적 라이브러리의 기능을 사용하려면

1. 콘솔 응용 프로그램을 만들면 빈 프로그램이 만들어집니다. 소스 파일의 이름은 앞에서 선택한 이름과 동일하게 설정됩니다. 예제에서는 라는 `MyExecRefsLib.cpp`합니다.

1. 정적 라이브러리에서 수학 루틴을 사용하기 전에 이를 참조해야 합니다. 바로 가기 메뉴를 열고 합니다 **MyExecRefsLib** 프로젝트 **솔루션 탐색기**를 선택한 후 **추가** > **참조**.

1. **참조 추가** 대화 상자에는 참조할 수 있는 라이브러리의 목록이 표시됩니다. 합니다 **프로젝트** 탭 현재 솔루션에서 참조 하는 모든 라이브러리 프로젝트를 나열 합니다. **프로젝트** 탭에서 **MathFuncsLib** 확인란을 선택한 다음 **확인** 단추를 선택합니다.

1. 참조는 `MathFuncsLib.h` 헤더 파일에 포함 된 디렉터리 경로 수정 해야 합니다. **MyExecRefsLib** 에 대한 **속성 페이지**대화 상자에서 **구성 속성** 노드, **C/C++** 노드를 차례로 확장한 다음 **일반**을 선택합니다. 옆에 **Additional Include Directories**의 경로 지정 합니다 **MathFuncsLib** 디렉터리 또는 검색에 대 한 합니다.

   디렉터리 경로를 찾으려면 속성 값 드롭다운 목록 상자를 열고 **편집**을 선택합니다. 에 **Additional Include Directories** 대화 상자의 텍스트 상자에서 빈 줄을 선택 하 고 선택한 다음 줄임표 단추 (**...** ) 줄의 끝입니다. **디렉터리 선택** 대화 상자에서 **MathFuncsLib** 디렉터리를 선택하고 **폴더 선택** 단추를 선택하여 선택 내용을 저장한 후 대화 상자를 닫습니다. **추가 포함 디렉터리** 대화 상자에서 **확인** 단추를 선택한 후 **속성 페이지** 대화 상자에서 **확인** 단추를 선택하여 프로젝트에 변경 내용을 저장합니다.

1. 이제 사용할 수 있습니다 합니다 `MyMathFuncs` 클래스를 포함 하 여이 앱에는 `#include "MathFuncsLib.h"` 코드에서 헤더입니다. 내용을 바꿉니다 `MyExecRefsLib.cpp` 이 코드를 사용 하 여:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]

1. 선택 하 여 실행 파일을 빌드합니다 **빌드합니다** > **솔루션 빌드** 메뉴 모음에서.

##  <a name="RunApp"></a> 앱 실행

### <a name="to-run-the-app"></a>앱을 실행하려면

1. **솔루션 탐색기** 에서 **MyExecRefsLib** 의 바로 가기 메뉴를 열고 **시작 프로젝트로 설정**을 선택하여 **MyExecRefsLib**가 기본 프로젝트로 선택되었는지 확인합니다.

1. 프로젝트를 실행하려면 메뉴 모음에서 **디버그** > **디버그하지 않고 시작**을 선택합니다. 출력은 유사 합니다.

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>참고 항목

[연습: 동적 연결 라이브러리 만들기 및 사용(C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[데스크톱 응용 프로그램(Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
