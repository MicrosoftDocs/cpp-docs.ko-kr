---
title: 설치 프로젝트를 사용하여 Visual C++ 응용 프로그램 배포 | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 058bbcd1128d8dfa5d546385d5684a927447902e
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234621"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>연습: 설치 프로젝트를 사용하여 Visual C++ 응용 프로그램 배포

설치 프로젝트를 사용하여 Visual C++ 응용 프로그램을 배포하는 방법을 설명합니다.

## <a name="prerequisites"></a>전제 조건

이 연습을 완료하려면 다음 구성 요소가 필요합니다.  
  
- Visual Studio를 설치한 컴퓨터.  
  
- Visual C++ 라이브러리가 없는 추가 컴퓨터.  
  
### <a name="to-deploy-an-application-by-using-a-setup-project"></a>설치 프로젝트를 사용하여 응용 프로그램을 배포하려면  

1. 새 프로젝트를 만듭니다. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다. 
  
1. **MFC ApplicationWizard**를 사용하여 새 Visual Studio 솔루션을 만듭니다. 마법사를 찾으려면 **새 프로젝트** 대화 상자에서 **Visual C++** 노드를 확장하고, **MFC**를 선택하고, **MFC 응용 프로그램**을 선택하고, 프로젝트의 이름을 입력한 다음, **확인**을 클릭합니다. **마침**을 클릭합니다.

   > [!NOTE]
   > **MFC 응용 프로그램** 종류가 없는 경우:<br/>
   > **Visual Studio 2017**: **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual Studio 설치 관리자 열기**를 선택합니다. **선택적** 구성 요소 섹션의 **C++를 사용한 데스크톱 개발** 아래에 있는 옵션인 **x86 및 x64용 Visual C++ MFC**를 설치합니다.<br/>
   > **Visual Studio 2015**: Windows 시작 단추를 클릭하고 **프로그램 추가/제거**를 입력합니다. 결과 목록에서 프로그램을 열고 설치된 프로그램 목록에서 Microsoft Visual Studio 2015 설치를 찾습니다. 이를 두 번 클릭한 후 **수정**을 선택하고 **Visual C++** 에서 **Microsoft Foundation Classes** 구성 요소를 선택합니다.
  
1. 활성 솔루션 구성을 **릴리스**로 변경합니다. **빌드** 메뉴에서 **Configuration Manger**를 선택합니다. **Configuration Manager** 대화 상자의 **활성 솔루션 구성** 드롭다운 상자 목록에서 **릴리스**를 선택합니다. **닫기**를 클릭합니다.
  
1. **Ctrl**+**Shift**+**B**를 눌러 응용 프로그램을 빌드합니다. 또는 **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다. 응용 프로그램을 빌드하면 설치 프로젝트가 이 MFC 응용 프로그램 프로젝트의 출력을 사용할 수 있습니다.   

1. 아직 다운로드하지 않은 경우 Microsoft Visual Studio 설치 관리자 프로젝트 확장을 다운로드합니다. 확장은 Visual Studio 개발자를 위한 무료 버전이며 설치 및 배포 프로젝트 템플릿 기능을 Visual Studio에 추가합니다. 인터넷에 연결되어 있으면 Visual Studio에서 **도구** >  **확장 및 업데이트**를 선택합니다. **확장 및 업데이트** 대화 상자에서 **온라인** 탭을 선택하고 검색 상자에 ‘Microsoft Visual Studio 설치 관리자 프로젝트’를 입력합니다. **Enter** 키를 누르고, **Microsoft Visual Studio \<버전> 설치 관리자 프로젝트**를 선택한 후, **다운로드**를 클릭합니다. 확장을 선택하여 실행하고 설치한 후 Visual Studio를 다시 시작합니다. 
  
1. 메뉴 모음에서 **파일** > **최근에 사용한 프로젝트 및 솔루션**을 선택한 후 프로젝트를 선택하여 다시 엽니다.   
  
1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택하여 **새 프로젝트** 대화 상자를 엽니다. 그런 다음, 대화 상자의 왼쪽 창에서 **설치됨** > **기타 프로젝트 형식** 노드를 확장하고 **Visual Studio 설치 관리자**를 선택합니다. 가운데 창에서 **설치 프로젝트**를 선택합니다.  
  
1. **이름** 상자에 설치 프로젝트의 이름을 입력합니다. **솔루션** 드롭다운 목록에서 **솔루션에 추가**를 선택합니다. **확인** 단추를 선택하여 설치 프로젝트를 만듭니다. 편집기 창에 **파일 도우미(ProjectName)** 탭이 열립니다.  

1. **응용 프로그램 폴더** 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **프로젝트 출력**을 선택하여 **프로젝트 출력 그룹 추가** 대화 상자를 엽니다. 대화 상자에서 **기본 출력**을 선택하고 **확인**을 클릭합니다. **ProjectName의 기본 출력(활성)** 이라는 새 항목이 표시됩니다.

1. **응용 프로그램 폴더** 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **어셈블리**를 선택하여 **구성 요소 선택** 대화 상자를 엽니다. [재배포할 DLL 확인](determining-which-dlls-to-redistribute.md) 문서의 설명대로 프로그램에 필요한 모든 DLL를 선택하고 추가합니다. 

1. **ProjectName의 기본 출력(활성)** 항목을 선택하고, **ProjectName의 기본 출력(활성) 바로 가기 만들기**를 마우스 오른쪽 단추로 클릭하여 선택합니다. **ProjectName의 기본 출력(활성) 바로 가기**라는 새 항목이 표시됩니다. 바로 가기 항목의 이름을 바꾸고 창의 왼쪽에 있는 **사용자 프로그램 메뉴** 노드로 항목을 끌어서 놓을 수 있습니다.

1. 메뉴 모음에서 **빌드** > **구성 관리자**를 선택합니다. **프로젝트** 테이블의 **빌드** 열 아래에서 배포 프로젝트의 확인란을 선택합니다. **닫기**를 클릭합니다.
  
1. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택하여 MFC 프로젝트와 배포 프로젝트를 빌드합니다.  
  
1. 솔루션 폴더에서, 배포 프로젝트에서 빌드된 setup.exe 프로그램을 찾습니다. 이 파일(및 .msi 파일)을 복사하여 다른 컴퓨터에 응용 프로그램 및 기타 필요한 라이브러리 파일을 설치할 수 있습니다. Visual C++ 라이브러리가 없는 두 번째 컴퓨터에서 설치 프로그램을 실행합니다.
  
## <a name="see-also"></a>참고 항목  

[배포 예제](deployment-examples.md)<br/>
