---
description: '자세한 정보: Visual C++ 응용 프로그램의 종속성 이해'
title: Visual C++ 애플리케이션의 종속성 이해
ms.date: 11/04/2016
helpviewer_keywords:
- application deployment [C++], dependencies
- Dependency Walker
- dependencies [C++], application deployment and
- deploying applications [C++], dependencies
- DUMPBIN utility
- DLLs [C++], dependencies
- depends.exe
- libraries [C++], application deployment issues
ms.assetid: 62a44c95-c389-4c5f-82fd-07d7ef09dbf9
ms.openlocfilehash: ff18d594edf6d35541655075de6f6e951ea42b88
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336558"
---
# <a name="understanding-the-dependencies-of-a-visual-c-application"></a>Visual C++ 애플리케이션의 종속성 이해

애플리케이션이 종속된 Visual C++ 라이브러리를 확인하려면 프로젝트 속성을 보면 됩니다. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 하 여 **속성 페이지** 대화 상자를 엽니다. Windows 8 및 이전 버전에서는 종속성에 대 한 보다 포괄적인 그림을 제공 하는 종속성 Walker (depends.exe)를 사용할 수도 있습니다. 최신 버전의 Windows에서는 [lucasg/종속성](https://github.com/lucasg/Dependencies) 도구에서 유사한 기능을 제공 합니다 .이 도구는 Microsoft에서 보장 하지 않는 타사 도구입니다.

**속성 페이지** 대화 상자에서 **구성 속성** 의 다양한 페이지를 검사하여 종속성을 확인할 수 있습니다. 예를 들어 프로젝트에서 MFC 라이브러리를 사용 하 고 MFC를 **사용** 하는 경우 **구성 속성**, **일반** 페이지의 **공유 DLL에서 mfc를 사용** 하 고 런타임에 응용 프로그램은 mfc dll과 같은 mfc dll에 종속 \<version> 됩니다. 애플리케이션에서 MFC를 사용하지 않더라도 **다중 스레드 디버그 DLL(/MDd)** 의 **런타임 라이브러리** 값 또는 **구성 속성**, **C/C++**, **코드 생성** 페이지의 **다중 스레드 DLL(/MD)** 을 선택하면 CRT 라이브러리에 종속될 수 있습니다.

depends.exe를 사용하여 로드 시 애플리케이션에 연결되는 DLL 목록과 지연 로드되는 DLL 목록을 확인할 수 있습니다. 런타임에 동적으로 로드되는 DLL의 전체 목록을 가져오려면 depends.exe의 프로파일링 기능을 사용하여 모든 코드 경로를 사용할 때까지 애플리케이션을 테스트할 수 있습니다. 프로파일링 세션을 종료하면 depends.exe에서 런타임에 동적으로 로드된 DLL을 표시합니다.

depends.exe를 사용하여 종속성을 확인할 때 DLL이 다른 DLL이나 특정 DLL 버전에 대해 종속성을 가질 수도 있다는 점에 유의해야 합니다. depends.exe는 개발 컴퓨터 또는 대상 컴퓨터에서 사용할 수 있습니다. 개발 컴퓨터에서 depends.exe를 실행하면 애플리케이션을 지원하는 데 필요한 DLL 목록이 표시됩니다. 대상 컴퓨터에서 실행할 애플리케이션을 가져오는 데 문제가 있으면 depends.exe를 컴퓨터에 복사한 다음 도구에서 애플리케이션을 열어 누락되거나 올바르지 않은 필수 DLL이 있는지 확인할 수 있습니다.

애플리케이션이 종속된 DLL을 확인하면 애플리케이션을 다른 컴퓨터에 배포할 때 이 애플리케이션과 함께 재배포할 DLL을 이 목록 중에서 확인할 수 있습니다. 대부분의 경우 시스템 DLL은 재배포할 필요가 없지만 Visual C++ 라이브러리용 DLL은 다시 배포해야 할 수 있습니다. 자세한 내용은 [재배포할 DLL 확인](determining-which-dlls-to-redistribute.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[데스크톱 애플리케이션 배포](deploying-native-desktop-applications-visual-cpp.md)
