---
title: Visual Studio에서 C++ 메이크파일 만들기
ms.date: 08/05/2019
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects [C++]
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: 69e6a2ff0d7e82f3bc431a28f57127e8d9a3aa4d
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921531"
---
# <a name="create-a-c-makefile-project"></a>C++ 메이크파일 프로젝트 만들기

‘메이크파일’은 C++ 소스 코드 파일 집합을 컴파일하고 링크(또는 ‘빌드’)하는 방법에 대한 지시를 포함하는 텍스트 파일입니다.  ‘메이크’ 프로그램은 메이크파일을 읽고, 컴파일러, 링커 및 가능한 다른 프로그램을 호출하여 실행 파일을 만듭니다.  ‘메이크’ 프로그램의 Microsoft 구현을 

기존 메이크파일 프로젝트가 있는 경우 Visual Studio IDE에서 코딩 및/또는 디버그할지 선택 사항이 있습니다.

- 기존 메이크파일을 사용하는 Visual Studio에서 메이크파일 프로젝트를 만들어 Visual Studio가 IntelliSense에 사용할 .vcxproj 파일을 구성합니다. (네이티브 MSBuild 프로젝트를 사용 하 여 모든 IDE 기능을 사용할 수 있는 것은 아닙니다.) 아래 [에서 메이크파일 프로젝트를 만들려면를](#create_a_makefile_project) 참조 하세요.
- **기존 코드 파일에서 새 프로젝트 만들기** 마법사를 사용하여 소스 코드에서 기본 MSBuild 프로젝트를 만듭니다. 그러면 원래 메이크파일이 사용되지 않습니다. 자세한 내용은 [방법: 기존 코드로 C++ 프로젝트 만들기](../how-to-create-a-cpp-project-from-existing-code.md)를 참조하세요.
- **Visual Studio 2017 이상** : MSBuild 시스템의 개입 없이 **폴더 열기** 기능을 사용 하 여 메이크파일 프로젝트를 그대로 편집 하 고 빌드합니다. 자세한 내용은 [C++용 폴더 열기 프로젝트](../open-folder-projects-cpp.md)를 참조하세요.
- **Visual Studio 2019 이상** : LINUX 용 UNIX 메이크파일 프로젝트를 만듭니다.

## <a name="a-namecreate_a_makefile_project-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> 메이크파일 프로젝트 템플릿을 사용하여 메이크파일 프로젝트 만들기

Visual Studio 2017 이상에서 메이크파일 프로젝트 템플릿은 C++ 데스크톱 개발 워크로드가 설치되어 있을 때 사용할 수 있습니다.

마법사를 따라 메이크파일에서 사용하는 명령과 환경을 지정합니다. 그런 다음, 이 프로젝트를 사용하여 Visual Studio에서 코드를 빌드합니다.

기본적으로 메이크파일 프로젝트는 솔루션 탐색기에 파일을 표시하지 않습니다. 메이크파일 프로젝트는 프로젝트의 속성 페이지에 반영되는 빌드 설정을 지정합니다.

프로젝트에서 지정하는 출력 파일은 빌드 스크립트가 생성하는 이름에는 영향을 미치지 않으며 의도만 선언합니다. 메이크파일은 여전히 빌드 프로세스를 제어하고 빌드 대상을 지정합니다.

::: moniker range="msvc-160"

### <a name="to-create-a-makefile-project-in-visual-studio-2019"></a>Visual Studio 2019에서 메이크파일 프로젝트를 만들려면

1. Visual Studio 주 메뉴에서 **파일**  >  **새로 만들기**  >  **프로젝트** 를 선택 하 고 검색 상자에 "메이크파일"을 입력 합니다. 또는 **새 프로젝트** 대화 상자에서 **Visual C++** > **일반** (Visual Studio 2015) 또는 **기타** (Visual Studio 2017)를 확장한 다음, 대상이 Windows인지 또는 Linux인지에 따라 두 옵션 중에서 선택합니다.

1. **Windows만** 해당: **디버그 구성 설정** 페이지에서 디버그 및 정품 빌드에 대 한 명령, 출력, 정리 및 다시 빌드 정보를 제공 합니다. 릴리스 구성에 대해 다른 설정을 지정하려면 **다음** 을 클릭합니다.

1. **마침** 을 클릭하여 대화 상자를 닫고, **솔루션 탐색기** 에서 새로 만든 프로젝트를 엽니다.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-create-a-makefile-project-in-visual-studio-2015-or-visual-studio-2017"></a>Visual Studio 2015 또는 Visual Studio 2017에서 메이크파일 프로젝트를 만들려면

1. Visual Studio 시작 페이지에서 **새 프로젝트** 검색 상자에 “메이크파일”을 입력합니다. 또는 **새 프로젝트** 대화 상자에서 **Visual C++** > **일반** (Visual Studio 2015) 또는 **기타** (Visual Studio 2017)를 확장한 다음, [템플릿] 창에서 **메이크파일 프로젝트** 를 선택하여 프로젝트 마법사를 엽니다.

1. **애플리케이션 설정** 페이지에서 디버그 및 일반 정품 빌드에 대한 명령, 출력, 정리 및 다시 빌드 정보를 제공합니다.

1. **마침** 을 클릭하여 마법사를 닫고, **솔루션 탐색기** 에서 새로 만든 프로젝트를 엽니다.

::: moniker-end

속성 페이지에서 프로젝트의 속성을 보고 편집할 수 있습니다. 속성 페이지 표시에 대한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

## <a name="makefile-project-wizard"></a>메이크파일 프로젝트 마법사

메이크파일 프로젝트를 만든 후에 프로젝트의 속성 페이지의 **Nmake** 페이지에서 다음 옵션을 각각 보고 편집할 수 있습니다.

- **빌드 명령줄:** 사용자가 빌드 메뉴에서 빌드를 선택할 때 실행할 명령줄을 지정 합니다. 프로젝트 속성 페이지의 Nmake 페이지에 있는 빌드 명령줄 필드에 표시됩니다.

- **출력:** 명령줄에 대 한 출력을 포함 하는 파일의 이름을 지정 합니다. 기본적으로 이 옵션은 프로젝트 이름을 기반으로 합니다. 프로젝트 속성 페이지의 Nmake 페이지에 있는 출력 필드에 표시됩니다.

- **정리 명령:** 사용자가 빌드 메뉴에서 정리를 선택할 때 실행할 명령줄을 지정 합니다. 프로젝트 속성 페이지의 Nmake 페이지에 있는 정리 명령줄 필드에 표시됩니다.

- **다시 빌드 명령줄:** 사용자가 빌드 메뉴에서 다시 빌드를 선택할 때 실행할 명령줄을 지정 합니다. 프로젝트 속성 페이지의 Nmake 페이지에 있는 모든 다시 빌드 명령줄 필드에 표시됩니다.

## <a name="how-to-enable-intellisense-for-makefile-projects"></a>방법: 메이크파일 프로젝트에 IntelliSense 사용

특정 프로젝트 설정 또는 컴파일러 옵션이 잘못 설정된 경우IntelliSense가 메이크파일 프로젝트에서 실패합니다. IntelliSense가 예상대로 작동할 수 있게 다음 단계에 따라 메이크파일 프로젝트를 구성합니다.

1. **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** 노드를 확장합니다.

1. **NMake** 속성 페이지를 선택한 다음, **IntelliSense** 에서 속성을 적절하게 수정합니다.

   - **전처리기 정의** 속성을 설정하여 메이크파일 프로젝트의 모든 전처리기 기호를 정의합니다. 자세한 내용은 [/D(전처리기 정의)](d-preprocessor-definitions.md)를 참조하세요.

   - **포함 검색 경로** 속성을 설정하여 컴파일러가 메이크파일 프로젝트의 전처리기 지시문에 전달되는 파일 참조를 확인하기 위해 검색할 디렉터리 목록을 지정합니다. 자세한 내용은 [/I(추가 포함 디렉터리)](i-additional-include-directories.md)를 참조하세요.

   - 명령 창에서 CL.EXE를 사용하여 빌드된 프로젝트의 경우, **INCLUDE** 환경 변수를 설정하여 컴파일러가 메이크파일 프로젝트의 전처리기 지시문에 전달되는 파일 참조를 확인하기 위해 검색할 디렉터리를 지정합니다.

   - **강제 포함** 속성을 설정하여 메이크파일 프로젝트를 빌드할 때 처리할 헤더 파일을 지정합니다. 자세한 내용은 [/FI(강제 포함 파일 이름 지정)](fi-name-forced-include-file.md)를 참조하세요.

   - **어셈블리 검색 경로** 속성을 설정하여 프로젝트의 .NET 어셈블리에 대한 참조를 확인하기 위해 컴파일러에서 검색할 디렉터리 목록을 지정합니다. 자세한 내용은 [/AI(메타데이터 디렉터리 지정)](ai-specify-metadata-directories.md)를 참조하세요.

   - **강제 사용 어셈블리** 속성을 설정하여 메이크파일 프로젝트를 빌드할 때 처리할 .NET 어셈블리를 지정합니다. 자세한 내용은 [/FU(강제 #using 파일 이름 지정)](fu-name-forced-hash-using-file.md)를 참조하세요.

   - **추가 옵션** 속성을 설정 하 여 c + + 파일을 구문 분석할 때 IntelliSense에서 사용할 추가 컴파일러 스위치를 지정 합니다.

1. **확인** 을 클릭하여 속성 페이지를 닫습니다.

1. **모두 저장** 명령을 사용하여 수정된 프로젝트 설정을 저장합니다.

다음에 Visual Studio 개발 환경에서 메이크파일 프로젝트를 열 때 메이크파일 프로젝트에서 **솔루션 정리** 명령을 실행한 다음, **솔루션 빌드** 명령을 실행합니다. IntelliSense는 IDE에서 제대로 작동해야 합니다.

## <a name="see-also"></a>참고 항목

[IntelliSense 사용](/visualstudio/ide/using-intellisense)<br>
[NMAKE 참조](nmake-reference.md)<br>
[방법: 기존 코드에서 C++ 프로젝트 만들기](../how-to-create-a-cpp-project-from-existing-code.md)<br>
[메이크파일의 특수 문자](special-characters-in-a-makefile.md)<br/>
[메이크파일의 내용](contents-of-a-makefile.md)<br/>
