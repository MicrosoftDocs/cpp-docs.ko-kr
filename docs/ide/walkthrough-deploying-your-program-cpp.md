---
description: '자세한 정보: 연습: 프로그램 배포(C++)'
title: '연습: 프로그램 배포(C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: 7d3b35cfbf2c5398e153f038adfb49f1b95b442d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334778"
---
# <a name="walkthrough-deploying-your-program-c"></a>연습: 프로그램 배포(C++)

초기 관련 연습을 수행하여 애플리케이션을 만들었으므로 마지막 단계는 사용자가 컴퓨터에 프로그램을 설치할 수 있도록 설치 관리자를 만드는 것입니다. 설치 관리자의 경우 기존 솔루션에 새 프로젝트를 추가합니다. 이 새 프로젝트에서 다른 컴퓨터에 응용 프로그램을 설치하는 setup.exe 파일이 생성됩니다.

이 연습에서는 Windows Installer를 사용하여 애플리케이션을 배포하는 방법을 보여 줍니다. ClickOnce를 사용하여 애플리케이션을 배포할 수도 있습니다. 자세한 내용은 [ClickOnce Deployment for Visual C++ Applications](../windows/clickonce-deployment-for-visual-cpp-applications.md)를 참조하세요. 배포에 대한 일반적인 자세한 내용은 [애플리케이션, 서비스 및 구성 요소 배포](/visualstudio/deployment/deploying-applications-services-and-components)를 참조하세요.

## <a name="prerequisites"></a>필수 조건

- 이 연습에서는 사용자가 C++ 언어의 기본적인 사항을 알고 있는 것으로 가정합니다.

- 또한 [Visual Studio IDE를 사용하여 C++ 데스크톱 개발](using-the-visual-studio-ide-for-cpp-desktop-development.md)에 나열된 이전 관련 연습을 완료했다고 가정합니다.

- Visual Studio Express 버전에서는 연습을 수행할 수 없습니다.

## <a name="install-the-visual-studio-setup-and-deployment-project-template"></a>Visual Studio 설치 및 배포 프로젝트 템플릿 설치

이 섹션의 단계는 설치한 Visual Studio 버전에 따라 다릅니다. 기본 설정된 버전의 Visual Studio에 대한 설명서를 보려면 **버전** 선택기 컨트롤을 사용하세요. 이 페이지의 목차 맨 위에 있습니다.

<!-- markdownlint-disable MD034 -->

::: moniker range="msvc-160"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2019"></a>Visual Studio 2019용 설치 및 배포 프로젝트 템플릿을 설치하려면

1. 아직 다운로드하지 않은 경우 Microsoft Visual Studio 설치 관리자 프로젝트 확장을 다운로드합니다. 확장은 Visual Studio 개발자를 위한 무료 버전이며 설치 및 배포 프로젝트 템플릿 기능을 Visual Studio에 추가합니다. 인터넷에 연결되면 Visual Studio에서 **확장** > **확장 관리** 를 선택합니다. **확장 및 업데이트** 대화 상자에서 **온라인** 탭을 선택하고 검색 상자에 ‘Microsoft Visual Studio 설치 관리자 프로젝트’를 입력합니다. **Enter** 키를 누르고, **Microsoft Visual Studio \<version> 설치 관리자 프로젝트** 를 선택한 후 **다운로드** 를 클릭합니다. 확장을 선택하여 실행하고 설치한 후 Visual Studio를 다시 시작합니다.

1. Visual Studio 메뉴 모음에서 **파일** > **최근에 사용한 프로젝트 및 솔루션** 을 선택한 다음, 프로젝트를 선택하여 다시 엽니다.

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택하여 **새 프로젝트 만들기** 대화 상자를 엽니다. 검색 상자에 "Setup"을 입력하고 결과 목록에서 **설치 프로젝트** 를 선택합니다.

1. **이름** 상자에 설치 프로젝트의 이름을 입력합니다. **솔루션** 드롭다운 목록에서 **솔루션에 추가** 를 선택합니다. **확인** 단추를 선택하여 설치 프로젝트를 만듭니다. 편집기 창에 **파일 도우미(ProjectName)** 탭이 열립니다.

1. **애플리케이션 폴더** 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **프로젝트 출력** 을 선택하여 **프로젝트 출력 그룹 추가** 대화 상자를 엽니다.

1. 대화 상자에서 **기본 출력** 을 선택하고 **확인** 을 클릭합니다. **Game의 기본 출력(활성)** 이라는 새 항목이 표시됩니다.

1. **의 기본 출력(활성)** 항목을 선택하고, **의 기본 출력(활성) 바로 가기 만들기** 를 마우스 오른쪽 단추로 클릭하여 선택합니다. **Game의 기본 출력(활성) 바로 가기** 라는 새 항목이 표시됩니다.

1. *Game* 바로 가기 항목의 이름을 바꾸고 창의 왼쪽에 있는 **사용자 프로그램 메뉴** 노드로 항목을 끌어서 놓을 수 있습니다.

1. **솔루션 탐색기** 에서 **Game Installer** 프로젝트를 선택하고 **보기** > **속성 창** 을 선택하거나 **F4** 키를 눌러 **속성** 창을 엽니다.

1. 설치 관리자에 표시할 추가 세부 정보를 지정합니다.  예를 들어 **제조업체** 에 *Contoso* 를 사용하고, **제품 이름** 에 *Game Installer* 를 사용하고, **SupportUrl** 에 *https\://www.contoso.com* 을 사용합니다.

1. 메뉴 모음에서 **빌드** > **구성 관리자** 를 선택합니다. **프로젝트** 테이블의 **빌드** 열 아래에서 **Game Installer** 의 확인란을 선택합니다. **닫기** 를 클릭합니다.

1. 메뉴 모음에서 **빌드** > **솔루션 빌드** 를 선택하여 게임 프로젝트와 게임 설치 관리자 프로젝트를 빌드합니다.

1. 솔루션 폴더에서, 게임 설치 프로젝트에 내장된 setup.exe 프로그램을 찾아 실행 게임 애플리케이션을 컴퓨터에 설치합니다. 이 파일(및 GameInstaller.msi)을 복사하여 다른 컴퓨터에 애플리케이션 및 기타 필요한 라이브러리 파일을 설치할 수 있습니다.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2017-and-earlier"></a>Visual Studio 2017 이상용 설치 및 배포 프로젝트 템플릿을 설치하려면

1. 인터넷에 연결되어 있으면 Visual Studio에서 **도구** > **확장 및 업데이트** 를 선택합니다.

1. **확장 및 업데이트** 에서 **온라인** 탭을 선택하고 검색 상자에 ‘Microsoft Visual Studio 설치 관리자 프로젝트’를 입력합니다. **Enter** 키를 누르고, **Microsoft Visual Studio \<version> 설치 관리자 프로젝트** 를 선택한 후 **다운로드** 를 클릭합니다.

1. 확장을 선택하여 설치한 후 Visual Studio를 다시 시작합니다.

1. 메뉴 모음에서 **파일** > **최근에 사용한 프로젝트 및 솔루션** 을 선택한 다음, **게임** 솔루션을 선택하여 다시 엽니다.

### <a name="to-create-a-setup-project-and-install-your-program"></a>설치 프로젝트를 만들고 프로그램을 설치하려면

1. 활성 솔루션 구성을 릴리스로 변경합니다. 메뉴 모음에서 **빌드** > **구성 관리자** 를 선택합니다. **Configuration Manager** 대화 상자의 **활성 솔루션 구성** 드롭다운 상자 목록에서 **릴리스** 를 선택합니다. **닫기** 단추를 선택하여 구성을 저장합니다.

1. 메뉴 모음에서 **파일**, >**새로 만들기**>, **프로젝트** 를 선택하여 **새 프로젝트** 대화 상자를 엽니다.

1. 대화 상자의 왼쪽 창에서 **설치됨** > **기타 프로젝트 형식** 노드를 확장한 후 **Visual Studio 설치 관리자** 를 선택합니다. 가운데 창에서 **설치 프로젝트** 를 선택합니다.

1. **이름** 상자에 설치 프로젝트의 이름을 입력합니다. 이 예에서는 *게임 설치 관리자* 를 입력합니다. **솔루션** 드롭다운 목록에서 **솔루션에 추가** 를 선택합니다. **확인** 단추를 선택하여 설치 프로젝트를 만듭니다. 편집기 창에 **파일 도우미(게임 설치 관리자)** 탭이 열립니다.

1. **애플리케이션 폴더** 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **프로젝트 출력** 을 선택하여 **프로젝트 출력 그룹 추가** 대화 상자를 엽니다.

1. 대화 상자에서 **기본 출력** 을 선택하고 **확인** 을 클릭합니다. **Game의 기본 출력(활성)** 이라는 새 항목이 표시됩니다.

1. **의 기본 출력(활성)** 항목을 선택하고, **의 기본 출력(활성) 바로 가기 만들기** 를 마우스 오른쪽 단추로 클릭하여 선택합니다. **Game의 기본 출력(활성) 바로 가기** 라는 새 항목이 표시됩니다.

1. *Game* 바로 가기 항목의 이름을 바꾸고 창의 왼쪽에 있는 **사용자 프로그램 메뉴** 노드로 항목을 끌어서 놓을 수 있습니다.

1. **솔루션 탐색기** 에서 **Game Installer** 프로젝트를 선택하고 **보기** > **속성 창** 을 선택하거나 **F4** 키를 눌러 **속성** 창을 엽니다.

1. 설치 관리자에 표시할 추가 세부 정보를 지정합니다.  예를 들어 **제조업체** 에 *Contoso* 를 사용하고, **제품 이름** 에 *Game Installer* 를 사용하고, **SupportUrl** 에 *https\://www.contoso.com* 을 사용합니다.

1. 메뉴 모음에서 **빌드** > **구성 관리자** 를 선택합니다. **프로젝트** 테이블의 **빌드** 열 아래에서 **Game Installer** 의 확인란을 선택합니다. **닫기** 를 클릭합니다.

1. 메뉴 모음에서 **빌드** > **솔루션 빌드** 를 선택하여 게임 프로젝트와 게임 설치 관리자 프로젝트를 빌드합니다.

1. 솔루션 폴더에서, 게임 설치 프로젝트에 내장된 setup.exe 프로그램을 찾아 실행 게임 애플리케이션을 컴퓨터에 설치합니다. 이 파일(및 GameInstaller.msi)을 복사하여 다른 컴퓨터에 애플리케이션 및 기타 필요한 라이브러리 파일을 설치할 수 있습니다.

::: moniker-end

## <a name="next-steps"></a>다음 단계

**이전:** [연습: 프로젝트 디버깅(C++)](walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>참조

[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[프로젝트 및 빌드 시스템](../build/projects-and-build-systems-cpp.md)<br/>
[데스크톱 애플리케이션 배포](../windows/deploying-native-desktop-applications-visual-cpp.md)<br/>
