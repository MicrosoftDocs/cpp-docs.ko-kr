---
description: '자세한 정보: Visual Studio 프로젝트 - C++'
title: Visual Studio 프로젝트 - C++
ms.date: 10/25/2019
helpviewer_keywords:
- ATL projects, creating
- Visual Studio C++ projects, creating
- projects [C++], creating
- Visual Studio C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: 07c7c0394c7b1a49bd4b8861540e540b095fae5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156816"
---
# <a name="visual-studio-projects---c"></a>Visual Studio 프로젝트 - C++

*Visual Studio 프로젝트* 프로젝트를 MSBuild 빌드 시스템에 기반합니다. MSBuild는 Visual Studio용 기본 빌드 시스템이며 일반적으로 Windows 관련 프로그램에 사용하기에 가장 좋은 빌드 시스템입니다. MSBuild는 Visual Studio와 긴밀하게 통합되어 있지만, 명령줄에서도 사용할 수도 있습니다. 플랫폼 간 프로젝트 또는 오픈 소스 라이브러리를 사용하는 프로젝트의 경우 Visual Studio 2017 이상에서 [Visual Studio CMake 프로젝트](cmake-projects-in-visual-studio.md)를 사용하는 것이 좋습니다. 이전 버전의 Visual Studio에서 MSBuild 프로젝트를 업그레이드하는 방법에 대한 자세한 `내용은 [Microsoft C++ 이식 및 업그레이드 가이드](../porting/visual-cpp-porting-and-upgrading-guide.md)를 참조하세요.

## <a name="create-a-project"></a>프로젝트 만들기

::: moniker range="msvc-160"

**파일** > **새로 만들기** > **프로젝트** 를 선택한 다음, **언어** 를 C++로 설정하여 C++ 프로젝트를 만들 수 있습니다. 결과 목록에는 **플랫폼** 또는 **프로젝트 형식** 을 설정하고 검색 상자에 키워드를 입력하여 필터링할 수 있는 프로젝트 템플릿 목록이 표시됩니다.

   ![Visual Studio 2019 프로젝트 템플릿](../build/media/vs2019-choose-console-app.png "Visual Studio 2019 새 프로젝트 대화 상자")

::: moniker-end

::: moniker range="msvc-150"

**파일** > **새로 만들기** > **프로젝트** 를 선택한 다음, 왼쪽 창에서 Visual C++를 선택하여 C++ 프로젝트를 만들 수 있습니다. 가운데 창에 프로젝트 템플릿 목록이 표시됩니다.

   ![프로젝트 템플릿](../overview/media/vs2017-new-project.png "Visual Studio 2017 새 프로젝트 대화 상자")

::: moniker-end

Visual Studio에 포함된 모든 기본 프로젝트 템플릿에 대한 자세한 정보는 [Visual Studio의 C++ 프로젝트 템플릿](reference/visual-cpp-project-types.md)을 참조하세요. 자체 프로젝트 템플릿을 만들 수 있습니다. 자세한 내용은 [방법: 프로젝트 템플릿 만들기](/visualstudio/ide/how-to-create-project-templates)를 참조하세요.

프로젝트를 만든 후에는 [솔루션 탐색기](/visualstudio/ide/solutions-and-projects-in-visual-studio) 창에 표시됩니다.

   ![솔루션 탐색기](media/mathlibrary-solution-explorer-153.png)

새 프로젝트를 만들면 솔루션 파일(.sln)도 만들어집니다. **솔루션 탐색기** 안에서 해당 항목을 마우스 오른쪽 단추로 클릭하여 다른 프로젝트를 솔루션에 추가할 수 있습니다. 솔루션 파일은 여러 관련 프로젝트가 있을 때 빌드 종속성을 조정하는 데 사용되며 그 이상의 의미는 없습니다. 모든 컴파일러 옵션은 프로젝트 수준에서 설정됩니다.

## <a name="add-items"></a>항목 추가

**솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가 > 새로 만들기** 또는 **추가 > 기존** 을 선택하여 원본 코드 파일, 아이콘 또는 기타 항목을 프로젝트에 추가합니다.

## <a name="add-third-party-libraries"></a>타사 라이브러리 추가

타사 라이브러리를 추가하려면 [vcpkg](vcpkg.md) 패키지 관리자를 사용합니다. Visual Studio 통합 단계를 실행하여 모든 Visual Studio 프로젝트에서 참조할 때 해당 라이브러리에 대한 경로를 설정합니다.

## <a name="set-compiler-options-and-other-build-properties"></a>컴파일러 옵션 및 기타 빌드 속성 설정

프로젝트에 대한 빌드 속성을 구성하려면 **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택합니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](working-with-project-properties.md)을 참조하세요.

## <a name="compile-and-run"></a>컴파일 및 실행

새 프로젝트를 컴파일하여 실행하려면 **F5** 를 누르거나 기본 도구 모음에 녹색 화살표가 있는 *디버그 드롭다운* 을 클릭합니다. *구성 드롭다운* 에서는 빌드 *디버그* 또는 *릴리스* 를 수행할지 선택합니다(또는 기타 사용자 지정 구성).

새 프로젝트가 오류 없이 컴파일됩니다. 자체 코드를 추가할 때 경우에 따라 오류가 발생하거나 경고가 트리거될 수 있습니다. 오류가 발생하면 빌드가 완료되지 않으나 경고는 그렇지 않습니다. 모든 오류 및 경고는 프로젝트를 빌드할 때 출력 창과 오류 목록에 모두 표시됩니다.

   ![출력 창과 오류 목록](../overview/media/vs2017-output-error-list.png)

오류 목록에 강조 표시된 오류에서 **F1** 을 눌러 해당 설명서 항목으로 이동할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용

[Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](working-with-project-properties.md)<br/>
속성 페이지 및 속성 시트를 사용하여 프로젝트 설정을 지정하는 방법

[빌드 시 참조 라이브러리 및 구성 요소](adding-references-in-visual-cpp-projects.md)<br/>
프로젝트에 lib, DLL, COM 및 .NET 구성 요소를 포함하는 방법

[프로젝트 출력 파일 구성](how-to-organize-project-output-files-for-builds.md)<br/>
빌드 프로세스에서 만든 실행 파일의 위치를 사용자 지정하는 방법

[사용자 지정 빌드 단계 및 빌드 이벤트](understanding-custom-build-steps-and-build-events.md)<br/>
특정 지점에서 프로세스에 대한 임의의 명령을 추가하는 방법

[기존 코드로 프로젝트 만들기](how-to-create-a-cpp-project-from-existing-code.md)<br/>
대강의 원본 파일 컬렉션에서 새 Visual Studio 프로젝트를 만드는 방법

## <a name="see-also"></a>참조

[프로젝트 및 빌드 시스템](projects-and-build-systems-cpp.md)<br>
[Microsoft C++ 이식 및 업그레이드 가이드](../porting/visual-cpp-porting-and-upgrading-guide.md)
