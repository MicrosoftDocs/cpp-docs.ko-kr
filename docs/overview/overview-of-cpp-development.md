---
title: Visual Studio의 C++ 개발 개요
description: Visual Studio IDE는 코드 편집기, 디버거, 테스트 프레임워크, 정적 분석기 및 기타 프로그래밍 도구를 사용하여 Windows, Linux, Android 및 iOS에서 C++ 개발을 수행하도록 지원합니다.
ms.date: 12/02/2019
helpviewer_keywords:
- Visual C++, development tools
author: corob-msft
ms.author: corob
ms.openlocfilehash: 5a03590074d8de05153b2d9442da8b916e6eba82
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500280"
---
# <a name="overview-of-c-development-in-visual-studio"></a>Visual Studio의 C++ 개발 개요

Visual Studio IDE(통합 개발 환경)의 일부인 Microsoft C++(MSVC)는 다른 언어와 공통된 다양한 창과 도구를 공유합니다. **솔루션 탐색기**, 코드 편집기 및 디버거를 비롯한 이러한 창과 도구에 대해서는 [Visual Studio IDE](/visualstudio/get-started/visual-studio-ide)에서 설명합니다. 흔히 공유 도구 또는 창은 다른 언어와는 약간 다른 C++용 기능 세트를 가지고 있습니다. 일부 창이나 도구는 Visual Studio Professional 또는 Visual Studio Enterprise 버전에서만 사용할 수 있습니다.

Visual Studio IDE에 있는 공유 도구 외에도, MSVC에는 네이티브 코드 개발 전용으로 사용되는 여러 도구가 있습니다. 이러한 도구의 목록도 이 문서에서 제공합니다. Visual Studio의 각 버전에서 사용할 수 있는 도구 목록은 [Visual Studio 버전의 C++ 도구 및 기능](visual-cpp-tools-and-features-in-visual-studio-editions.md)을 참조하세요.

## <a name="create-projects"></a>프로젝트 만들기

*프로젝트*는 기본적으로 실행 가능한 프로그램이나 라이브러리에 빌드된 이미지 또는 데이터 파일과 같은 소스 코드 파일 및 리소스 집합입니다.

Visual Studio는 IntelliSense, 검색 및 디버깅을 완벽하게 지원하여 사용하려는 모든 프로젝트 시스템 또는 사용자 지정 빌드 도구를 지원합니다.

- **MSBuild**는 Visual Studio용 네이티브 프로젝트 시스템입니다. 주 메뉴에서 **파일** > **새로 만들기** > **프로젝트**를 선택하면 다양한 종류의 C++ 애플리케이션 개발을 빠르게 시작하기 위한 많은 유형의 MSBuild ‘프로젝트 템플릿’이 표시됩니다. 

   ::: moniker range="vs-2019"

   ![새 프로젝트 템플릿](../build/media/mathclient-project-name-2019.png "Visual Studio 2019 새 프로젝트 대화 상자")

   ::: moniker-end

   ::: moniker range="<=vs-2017"

   ![프로젝트 템플릿](media/vs2017-new-project.png "Visual Studio 2017 새 프로젝트 대화 상자")

   ::: moniker-end

   일반적으로 기존 CMake 프로젝트를 사용하거나 다른 프로젝트 시스템을 사용하지 않는 한 이러한 템플릿을 새 프로젝트에 사용해야 합니다. 자세한 내용은 [MSBuild 기반 프로젝트 만들기 및 관리](../build/creating-and-managing-visual-cpp-projects.md)를 참조하세요.

- **CMake**는 C++ 워크로드로 데스크톱 개발을 설치할 때, Visual Studio IDE에 통합되는 플랫폼 간 빌드 시스템입니다. 새 프로젝트에 대한 CMake 프로젝트 템플릿을 사용하거나 CMakeLists.txt 파일이 있는 폴더를 열면 됩니다. 자세한 내용은 [Visual Studio의 CMake 프로젝트](../build/cmake-projects-in-visual-studio.md)를 참조하세요.

- 느슨한 파일 컬렉션을 포함한 다른 모든 C++ 빌드 시스템은 **폴더 열기** 기능을 통해 지원됩니다. 간단한 JSON 파일을 생성하여 빌드 프로그램을 호출하고 디버깅 세션을 구성합니다. 자세한 내용은 [C++용 폴더 열기 프로젝트](../build/open-folder-projects-cpp.md)를 참조하세요.

## <a name="add-to-source-control"></a>소스 제어에 추가

소스 제어를 사용하면 여러 개발자 간 작업을 조정하고, 진행 중인 작업을 프로덕션 코드에서 분리하고, 소스 코드를 백업할 수 있습니다. Visual Studio에서는 해당 **팀 탐색기** 창을 통해 Git 및 [TFVC\(Team Foundation 버전 제어\)](/azure/devops/repos/tfvc/)를 지원합니다.

::: moniker range="vs-2019"

![Visual Studio 2019 팀 탐색기 창의 스크린샷](media/vs2019-team-explorer.png "Visual Studio 2017 팀 탐색기")

::: moniker-end

::: moniker range="<=vs-2017"

![Visual Studio 2017 팀 탐색기 창의 스크린샷](media/vs2017-team-explorer.png "Visual Studio 2017 팀 탐색기")

::: moniker-end

Azure의 리포지토리와의 Git 통합에 대한 자세한 내용은 [Visual Studio 2017 및 Azure 리포지토리 Git과 코드 공유](/azure/devops/repos/git/share-your-code-in-git-vs-2017)를 참조하세요. GitHub와의 Git 통합에 대한 자세한 내용은 [Visual Studio용 GitHub 확장](https://visualstudio.github.com/)을 참조하세요.

## <a name="obtain-libraries"></a>라이브러리 가져오기

타사 라이브러리를 가져와 설치하려면 [vcpkg](../build/vcpkg.md) 패키지 관리자를 사용합니다. 900개가 넘는 오픈 소스 라이브러리가 현재 카탈로그에서 제공되고 있습니다.

## <a name="create-user-interfaces-with-designers"></a>디자이너를 사용하여 사용자 인터페이스 만들기

프로그램에 사용자 인터페이스가 있는 경우 디자이너를 사용하여 단추, 목록 상자 등의 컨트롤로 빠르게 채울 수 있습니다. 도구 상자 창의 컨트롤을 끌어 디자인 화면에 놓으면 Visual Studio에서 모든 작업을 수행하는 데 필요한 리소스 및 코드를 생성합니다. 그런 다음, 코드를 작성하여 모양 및 동작을 사용자 지정합니다.

![디자이너 및 도구 상자](media/vs2017-toolbox-designer.png "Visual Studio 2017 도구 상자 및 디자이너")

유니버설 Windows 플랫폼 앱의 사용자 인터페이스 디자인에 대한 자세한 내용은 [디자인 및 UI](https://developer.microsoft.com/windows/design)를 참조하세요.

MFC 애플리케이션의 사용자 인터페이스 만들기에 대한 자세한 내용은 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)을 참조하세요. Win32 Windows 프로그램에 대한 자세한 내용은 [Windows 데스크톱 애플리케이션](../windows/desktop-applications-visual-cpp.md)을 참조하세요.

## <a name="write-code"></a>코드 작성

프로젝트를 만든 후에는 모든 프로젝트 파일이 **솔루션 탐색기** 창에 표시됩니다. (*솔루션*은 하나 이상의 관련 프로젝트의 논리적 컨테이너입니다.) **솔루션 탐색기**에서 .h 또는 .cpp 파일을 클릭하면 파일이 코드 편집기에서 열립니다.

![솔루션 탐색기 및 코드 편집기](media/vs2017-solution-explorer-code-editor.png "Visual Studio 2017 솔루션 탐색기 및 코드 편집기")

코드 편집기는 C++ 소스 코드용 특수 워드 프로세서입니다. 언어 키워드, 메서드 및 변수 이름, 기타 코드 요소 등을 색으로 구분하여 코드를 더 쉽게 읽고 이해할 수 있도록 해 줍니다. 또한 코드 리팩터링, 서로 다른 파일 간 이동 및 코드가 구성되는 방식을 이해하기 위한 도구를 제공합니다. 자세한 내용은 [코드 작성 및 리팩터링](../ide/writing-and-refactoring-code-cpp.md)을 참조하세요.

## <a name="add-and-edit-resources"></a>리소스 추가 및 편집

Windows 프로그램 또는 DLL에는 일반적으로 대화 상자, 아이콘, 이미지, 지역화 가능 문자열, 시작 화면, 데이터베이스 연결 문자열 또는 임의 데이터와 같은 일부 *리소스*가 포함되어 있습니다. Visual Studio에는 리소스를 추가하고 편집하기 위한 도구가 포함되어 있습니다. 자세한 내용은 [리소스 파일을 사용하여 작업](../windows/working-with-resource-files.md)을 참조하세요.

## <a name="build-compile-and-link"></a>빌드(컴파일 및 연결)

메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택하거나 **Ctrl+Shift+B** 키 조합을 입력하여 프로젝트를 컴파일하고 연결합니다. 빌드 오류 및 경고는 오류 목록에 보고됩니다(**Ctrl+\\, E**). **출력** 창(**Alt+2**)에는 빌드 프로세스에 대한 정보가 표시됩니다.

![출력 창 및 오류 목록](media/vs2017-output-error-list.png "Visual Studio 2017 출력 창 및 오류 목록")

빌드 구성에 대한 자세한 내용은 [프로젝트 속성 작업](../build/working-with-project-properties.md) 및 [프로젝트 및 빌드 시스템](../build/projects-and-build-systems-cpp.md)을 참조하세요.

컴파일러(cl.exe) 및 다양한 빌드 관련 독립 실행형 도구(예: NMAKE 및 LIB)를 명령줄에서 바로 사용할 수도 있습니다. 자세한 내용은 [명령줄에서 C/C++ 코드 빌드](../build/building-on-the-command-line.md) 및 [C/C++ 빌드 참조](../build/reference/c-cpp-building-reference.md)를 참조하세요.

## <a name="debug"></a>디버그

**F5** 키를 눌러 디버깅을 시작할 수 있습니다. 설정한 모든 중단점에서 실행이 일시 중지됩니다(**F9**를 누를 경우). 한 번에 한 줄씩 코드를 단계별로 진행하며(**F10**) 변수 또는 레지스터의 값을 확인할 수 있고, 일부 사례에서는 코드 변경 후 다시 컴파일하지 않고 디버깅을 계속할 수도 있습니다. 다음 그림에서는 중단점에서 실행이 중지되는 디버깅 세션을 보여 줍니다. 데이터 구조 멤버의 값은 **조사식 창**에 표시됩니다.

![디버깅 세션](media/vs2017-debug-watch.png "Visual Studio 2017 디버깅 세션")

자세한 내용은 [Visual Studio의 디버깅](/visualstudio/debugger/debugging-in-visual-studio)을 참조하세요.

## <a name="test"></a>테스트

Visual Studio에는 Boost.Test, Google Test 및 CTest에 대한 지원뿐만 아니라 C++용 Microsoft Unit Test Framework가 포함되어 있습니다. **테스트 탐색기** 창에서 테스트를 실행합니다.

![테스트 탐색기](media/cpp-test-explorer-passed.png "Visual Studio 2017 테스트 탐색기")

자세한 내용은 [단위 테스트를 사용하여 코드 확인](/visualstudio/test/unit-test-your-code) 및 [Visual Studio에서 C/C++에 대한 단위 테스트 작성](/visualstudio/test/writing-unit-tests-for-c-cpp)을 참조하세요.

## <a name="analyze"></a>분석

Visual Studio에는 소스 코드에서 잠재적인 문제를 감지할 수 있는 정적 코드 분석 도구가 포함되어 있습니다. 이러한 도구에는 [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) 규칙 검사기의 구현이 포함됩니다. 자세한 내용은 [C/C++용 코드 분석 개요](../code-quality/code-analysis-for-c-cpp-overview.md)를 참조하세요.

## <a name="deploy-completed-applications"></a>완성된 애플리케이션 배포

Microsoft Store를 통해 기존 데스크톱 애플리케이션과 UWP 앱을 고객에게 배포할 수 있습니다. CRT 배포는 백그라운드에서 자동으로 처리됩니다. 자세한 내용은 [Windows 앱 및 게임 게시](/windows/uwp/publish/)를 참조하세요.

기본 C++ 데스크톱을 다른 컴퓨터에 배포할 수도 있습니다. 자세한 내용은 [데스크톱 애플리케이션 배포](../windows/deploying-native-desktop-applications-visual-cpp.md)를 참조하세요.

C++/CLI 프로그램의 배포에 대한 자세한 내용은 [개발자를 위한 배포 가이드](/dotnet/framework/deployment/deployment-guide-for-developers)를 참조하세요.

## <a name="next-steps"></a>다음 단계

이러한 소개 아티클 중 하나와 함께 다음을 수행하여 Visual Studio를 추가로 탐색합니다.

> [!div class="nextstepaction"]
> [코드 편집기를 사용하는 방법 알아보기](/visualstudio/get-started/tutorial-editor)

> [!div class="nextstepaction"]
> [프로젝트 및 솔루션에 대한 자세한 정보](/visualstudio/get-started/tutorial-projects-solutions)
