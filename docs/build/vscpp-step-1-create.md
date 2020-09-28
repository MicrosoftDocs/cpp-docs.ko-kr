---
title: C++ 콘솔 앱 프로젝트 만들기
description: Visual Studio에서 Microsoft C++를 사용하여 Hello World 콘솔 앱을 만듭니다.
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 333bb6ce1f3ea0db6b07d70ddd60d4a4be337abd
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686511"
---
# <a name="create-a-c-console-app-project"></a>C++ 콘솔 앱 프로젝트 만들기

C++ 프로그래머의 일반적인 시작점은 명령줄에서 실행되는 "Hello, world!" 애플리케이션입니다. 이 단계에서는 Visual Studio에서 이 애플리케이션을 만들 것입니다.

## <a name="prerequisites"></a>사전 요구 사항

- 컴퓨터에서 설치되고 실행 중인 C++ 워크로드를 사용하여 데스크톱 개발을 위해 Visual Studio를 설치합니다. 아직 설치되지 않은 경우 [Visual Studio에서 C++ 지원 설치](vscpp-step-0-installation.md)를 참조하세요.

## <a name="create-your-app-project"></a>앱 프로젝트 만들기

Visual Studio는 ‘프로젝트’를 사용하여 앱에 대한 코드를 구성하고 ‘솔루션’을 사용하여 프로젝트를 구성합니다.   프로젝트에는 앱을 빌드하는 데 사용되는 모든 옵션, 구성 및 규칙이 포함됩니다. 프로젝트는 모든 프로젝트의 파일과 외부 파일 간의 관계를 관리합니다. 앱을 만들려면 먼저 새 프로젝트 및 솔루션을 만듭니다.

::: moniker range=">=vs-2019"

1. Visual Studio에서 **파일** 메뉴를 열고 **새로 만들기 > 프로젝트**를 선택하여 **새 프로젝트 만들기** 대화 상자를 엽니다. **C++** , **Windows** 및 **콘솔** 태그가 있는 **콘솔 앱** 템플릿을 선택한 다음, **다음**을 선택합니다.

   ![새 프로젝트 만들기](media/vs2019-choose-console-app.png "새 프로젝트 만들기 대화 상자 열기")

1. **새 프로젝트 구성** 대화 상자에서 **프로젝트 이름** 편집 상자에 *HelloWorld*를 입력합니다. **만들기**를 선택하여 프로젝트를 만듭니다.

   ![프로젝트 이름 텍스트 필드에 Hello World가 입력된 새 프로젝트 구성 대화 상자의 스크린샷](media/vs2019-configure-new-project-hello-world.png "새 프로젝트 이름 지정 및 만들기")

   Visual Studio가 새 프로젝트를 만듭니다. 소스 코드를 추가하고 편집할 준비가 완료되었습니다. 기본적으로 콘솔 앱 템플릿은 다음과 같이 "Hello World" 앱을 사용하여 소스 코드를 채웁니다.

   ![IDE의 Hello World 프로젝트](media/vs2019-hello-world-code.png "IDE의 Hello World 프로젝트")

   편집기에 다음과 같이 코드가 표시되면 다음 단계로 이동하여 앱을 빌드할 준비가 된 것입니다.

[문제가 발생했습니다.](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. Visual Studio에서 **파일** 메뉴를 열고 **새로 만들기 > 프로젝트**를 선택하여 **새 프로젝트** 대화 상자를 엽니다.

   ![새 프로젝트 대화 상자 열기](media/vscpp-file-new-project.gif "새 프로젝트 대화 상자 열기")

1. 아직 선택하지 않은 경우 **새 프로젝트** 대화 상자에서 **설치됨 > Visual C++** 를 선택한 다음, **빈 프로젝트** 템플릿을 선택합니다. **이름** 필드에 *HelloWorld*를 입력합니다. **확인**을 선택하여 프로젝트를 만듭니다.

   ![설치됨 > Visual C++가 선택 및 호출되고 빈 프로젝트 옵션이 호출되었으며 이름 텍스트 상자에 Hello World가 입력된 새 프로젝트 대화 상자의 스크린샷](media/vscpp-concierge-project-name-callouts.png "새 프로젝트 이름 지정 및 만들기")

Visual Studio가 빈 새 프로젝트를 만듭니다. 만들려는 앱의 종류에 대해 특수화하고 소스 코드 파일을 추가할 준비가 되었습니다. 이 작업은 다음에 수행합니다.

[문제가 발생했습니다.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>프로젝트를 콘솔 앱으로 만들기

Visual Studio는 Windows 및 기타 플랫폼용으로 모든 종류의 앱과 구성 요소를 만들 수 있습니다. **빈 프로젝트** 템플릿은 Visual Studio가 만드는 앱의 종류와는 관련이 없습니다. *콘솔 앱*은 콘솔 또는 명령 프롬프트 창에서 실행되는 것입니다. 이 앱을 만들려면 콘솔 하위 시스템을 사용할 앱을 빌드하도록 Visual Studio에 지시해야 합니다.

1. Visual Studio에서 **프로젝트** 메뉴를 열고 **속성**을 선택하여 **HelloWorld 속성 페이지** 대화 상자를 엽니다.

1. **속성 페이지** 대화 상자에서 **구성 속성 > 링커 > 시스템**을 선택한 다음, **하위 시스템** 속성 옆의 편집 상자를 선택합니다. 표시되는 드롭다운 메뉴에서 **콘솔(/SUBSYSTEM:CONSOLE)** 을 선택합니다. **확인**을 선택하여 변경 내용을 저장합니다.

   ![속성 페이지 대화 상자 열기](media/vscpp-properties-linker-subsystem.gif "속성 페이지 대화 상자 열기")

이제 Visual Studio는 콘솔 창에서 실행할 프로젝트를 빌드해야 함을 알고 있습니다. 다음에는 소스 코드 파일을 추가하고 앱에 대한 코드를 입력합니다.

[문제가 발생했습니다.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>소스 코드 파일 추가

1. **솔루션 탐색기**에서 HelloWorld 프로젝트를 선택합니다. 메뉴 모음에서 **프로젝트**, **새 항목 추가**를 선택하여 **새 항목 추가** 대화 상자를 엽니다.

1. 아직 선택하지 않은 경우 **새 항목 추가** 대화 상자의 **설치됨**에서 **Visual C++** 를 선택합니다. 가운데 창에서 **C++ 파일(.cpp)** 을 선택합니다. **이름**을 *HelloWorld.cpp*로 변경합니다. **추가**를 선택하여 대화 상자를 닫고 파일을 만듭니다.

   ![HelloWorld.cpp용 원본 파일 추가](media/vscpp-add-new-item.gif "HelloWorld.cpp용 원본 파일 추가")

Visual Studio는 비어 있는 새 소스 코드 파일을 만들어 편집기 창에서 엽니다. 이로써 소스 코드를 입력할 준비를 완료합니다.

[문제가 발생했습니다.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>소스 파일의 경로 추가

1. 이 코드를 HelloWorld.cpp 편집기 창에 복사합니다.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   코드는 편집기 창에서 다음과 같이 표시됩니다.

   ![편집기의 Hello World 코드](media/vscpp-hello-world-editor.png "편집기의 Hello World 코드")

편집기에 다음과 같이 코드가 표시되면 다음 단계로 이동하여 앱을 빌드할 준비가 된 것입니다.

[문제가 발생했습니다.](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [C++ 프로젝트 빌드 및 실행](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>문제 해결 가이드

첫 번째 C++ 프로젝트를 만들 때 발생하는 일반적인 문제에 대한 해결 방법을 제공합니다.

### <a name="create-your-app-project-issues"></a>앱 프로젝트 만들기: 문제

::: moniker range="vs-2019"

**새 프로젝트** 대화 상자에는 **C++** , **Windows** 및 **콘솔** 태그가 있는 **콘솔 앱** 템플릿이 표시되어야 합니다. 표시되지 않는다면 두 가지 원인이 있을 수 있습니다. 목록에서 필터링되거나 설치되지 않았을 수 있습니다. 먼저 템플릿 목록 맨 위에 있는 필터 드롭다운을 확인하여 **C++** , **Windows** 및 **콘솔**로 설정합니다. C++ **콘솔 앱** 템플릿이 표시됩니다. 그러지 않는 경우 **C++를 사용한 Windows 데스크톱 개발** 워크로드가 설치되어 있지 않은 것입니다.

**C++를 사용한 데스크톱 개발**을 설치하려면 **새 프로젝트** 대화 상자에서 바로 설치 관리자를 실행할 수 있습니다. 템플릿 목록 맨 아래에 있는 **추가 도구 및 기능 설치** 링크를 선택하여 설치 관리자를 시작합니다. **사용자 계정 컨트롤** 대화 상자에서 권한을 요청하는 경우 **예**를 선택합니다. 설치 관리자에서 **C++를 사용한 데스크톱 개발** 워크로드를 선택해야 합니다. 그런 다음, **수정**을 선택하여 Visual Studio 설치를 업데이트합니다.

같은 이름을 가진 다른 프로젝트가 이미 있는 경우 프로젝트에 대해 다른 이름을 선택합니다. 또는 기존 프로젝트를 삭제한 후 다시 시도합니다. 기존 프로젝트를 삭제하려면 파일 탐색기에서 솔루션 폴더(*helloworld.sln* 파일을 포함하는 폴더)를 삭제합니다.

[뒤로 이동](#create-your-app-project).

::: moniker-end

::: moniker range="vs-2017"

**새 프로젝트** 대화 상자의 **설치됨**에 **Visual C++** 항목이 표시되지 않는 경우 Visual Studio의 복사본에 **C++를 사용한 데스크톱 개발** 워크로드가 설치되지 않은 것일 수 있습니다. **새 프로젝트** 대화 상자에서 설치 관리자를 바로 실행할 수 있습니다. **Visual Studio 설치 관리자 열기** 링크를 선택하여 설치 관리자를 다시 시작합니다. **사용자 계정 컨트롤** 대화 상자에서 권한을 요청하는 경우 **예**를 선택합니다. 필요한 경우 설치 관리자를 업데이트합니다. 설치 관리자에서 **C++를 사용한 데스크톱 개발** 워크로드가 선택되었는지 확인하고 **확인**을 선택하여 Visual Studio 설치를 업데이트합니다.

::: moniker-end

::: moniker range="<=vs-2017"

같은 이름을 가진 다른 프로젝트가 이미 있는 경우 프로젝트에 대해 다른 이름을 선택합니다. 또는 기존 프로젝트를 삭제한 후 다시 시도합니다. 기존 프로젝트를 삭제하려면 파일 탐색기에서 솔루션 폴더(*helloworld.sln* 파일을 포함하는 폴더)를 삭제합니다.

[뒤로 이동](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>프로젝트를 콘솔 앱으로 만들기: 문제

**구성 속성**에 **링커**가 나열되어 있지 않은 경우 **취소**를 선택하여 **속성 페이지** 대화 상자를 닫습니다. 다시 시도하기 전에 **솔루션 탐색기**에서 **HelloWorld** 프로젝트를 선택했는지 확인합니다. **솔루션 탐색기**에서 **HelloWorld** 솔루션이나 다른 항목을 선택하지 마세요.

속성을 선택하기 전에는 드롭다운 컨트롤이 **하위 시스템** 속성 편집 상자에 표시되지 않습니다. 편집 상자를 클릭하여 선택합니다. 또는 **탭**을 눌러 **하위 시스템**이 강조 표시될 때까지 대화 상자 컨트롤을 순환할 수 있습니다. 드롭다운 컨트롤을 선택하거나 **Alt+Down**을 눌러 엽니다.

[뒤로 이동](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>소스 코드 파일 추가: 문제

소스 코드 파일에 다른 이름을 지정해도 됩니다. 그러나 동일한 코드를 포함하는 둘 이상의 파일을 프로젝트에 추가하지 마세요.

헤더 파일 등 잘못된 파일 형식을 프로젝트에 추가한 경우 삭제하고 다시 시도하세요. 파일을 삭제하려면 **솔루션 탐색기**에서 해당 파일을 선택하세요. 그런 다음, **삭제** 키를 누릅니다.

[뒤로 이동](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>소스 파일의 경로 추가: 문제

소스 코드 파일 편집기 창을 실수로 닫은 경우 쉽게 다시 열 수 있습니다. 창을 열려면 **솔루션 탐색기** 창에서 HelloWorld.cpp를 두 번 클릭합니다.

소스 코드 편집기에서 빨간색 오류 표시선이 모든 항목 아래에 표시되는 경우 코드가 철자, 문장 부호 및 대/소문자의 예제와 일치하는지 확인하세요. C++ 코드에서는 대/소문자가 중요합니다.

[뒤로 이동](#add-code-to-the-source-file).

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
