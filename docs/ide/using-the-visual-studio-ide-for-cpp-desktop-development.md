---
description: '자세한 정보: C++ 데스크톱 개발에 Visual Studio IDE 사용'
title: C++ 데스크톱 개발에 Visual Studio IDE 사용
ms.date: 04/25/2019
helpviewer_keywords:
- IDE [C++]
- Visual Studio IDE [C++]
ms.assetid: d985c230-8e81-49d6-92be-2db9cac8d023
ms.openlocfilehash: d82b3717525758810720121f1319c763e3de8f43
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318704"
---
# <a name="using-the-visual-studio-ide-for-c-desktop-development"></a>C++ 데스크톱 개발에 Visual Studio IDE 사용

Visual Studio IDE(통합 개발 환경)는 정적 분석 및 강력한 디버깅 도구를 사용하여 크고 작은 코드 프로젝트를 관리하고, 코드를 작성 및 리팩터링하고, 오류를 감지 및 수정하는 데 도움이 되는 기능 집합을 제공합니다. 이 문서 집합은 프로젝트를 관리하고 코드를 작성, 테스트 및 디버깅한 다음, 다른 컴퓨터에 배포하는 데 필요한 각 단계를 안내하도록 설계되었습니다.

## <a name="prerequisites"></a>필수 구성 요소

아직 Visual Studio를 설치하지 않았다면, 지금이 적기입니다. 다운로드 링크와 빠른 연습은 [Visual Studio에서 C++ 지원 설치](../build/vscpp-step-0-installation.md)를 참조합니다. 일반적으로 Visual Studio 설치 방법 및 문제 해결 팁에 대한 자세한 내용은 [Visual Studio 설치](/visualstudio/install/install-visual-studio)를 참조합니다. 기본적으로 C++ 컴파일러, 도구 및 라이브러리가 설치되어 있지 않으므로 Visual Studio를 설치할 때 이들을 포함하려면 **C++를 사용한 데스크톱 개발** 워크로드를 선택했는지 확인합니다.

이 연습에서는 Windows 데스크톱 개발에 필요한 C++ 구성 요소를 설치했다고 가정합니다. 또한 개발자는 C++ 언어의 기본적인 사항을 이해하고 있다고 가정합니다. C++를 배워야 할 경우, 많은 책과 웹 리소스를 이용할 수 있습니다. 시작하기 좋은 곳 중 하나는 표준 C++ Foundation 웹 사이트의 [시작하기](https://isocpp.org/get-started) 페이지입니다.

아직 Visual Studio를 설치하지 않았다면, 지금이 적기입니다. 일반적으로 Visual Studio 2017 또는 Visual Studio 2015 컴파일러를 사용하여 코드를 컴파일해야 하는 경우에도 Visual Studio 2019를 사용하는 것이 좋습니다. 자세한 내용은 [Visual Studio의 네이티브 멀티 타기팅을 사용하여 이전 프로젝트 빌드](../porting/use-native-multi-targeting.md)를 참조하세요.

**Visual Studio 2019 설치**

Visual Studio 2019를 가져오려면 [Visual Studio 다운로드](https://www.visualstudio.com/downloads/)에서 다운로드하면 됩니다. Visual Studio를 설치할 때 기본적으로 설치되지 않으므로, C++ 개발 도구를 포함해야 합니다. Visual Studio를 설치하는 방법에 대한 자세한 내용은 [Visual Studio 설치](/visualstudio/install/install-visual-studio)를 참조하세요.

**Visual Studio 2017 설치**

Visual Studio 2017을 가져오려면 [Visual Studio의 이전 버전 다운로드](https://www.visualstudio.com/vs/older-downloads/)에서 다운로드하면 됩니다. Visual Studio를 설치할 때 기본적으로 설치되지 않으므로, C++ 개발 도구를 포함해야 합니다. Visual Studio를 설치하는 방법에 대한 자세한 내용은 [Visual Studio 설치](/visualstudio/install/install-visual-studio)를 참조하세요. Visual Studio 2017에 대한 지침을 보려면 Visual Studio **버전** 선택기 제어를 Visual Studio 2017로 설정합니다. 이 페이지의 목차 맨 위에 있습니다.

**Visual Studio 2015 설치**

Visual Studio 2015를 설치하려면 [이전 버전의 Visual Studio 다운로드](https://www.visualstudio.com/vs/older-downloads/)로 이동합니다. 설치 프로그램을 실행하고 **사용자 지정 설치** 를 선택한 다음, C++ 구성 요소를 선택합니다.

Visual Studio 설치가 완료되면 계속 진행할 준비가 된 것입니다.

## <a name="get-started"></a>시작하기

Visual Studio IDE를 사용하여 C++ 앱을 빌드하려면 각 항목을 순서대로 진행합니다. 각 항목은 이전 항목에서 완료한 작업을 기반으로 작성됩니다.

- [연습: 프로젝트 및 솔루션 작업(C++)](walkthrough-working-with-projects-and-solutions-cpp.md)

- [연습: 프로젝트 빌드(C++)](walkthrough-building-a-project-cpp.md)

- [연습: 프로젝트 테스트(C++)](walkthrough-testing-a-project-cpp.md)

- [연습: 프로젝트 디버깅(C++)](walkthrough-debugging-a-project-cpp.md)

- [연습: 프로그램 배포(C++)](walkthrough-deploying-your-program-cpp.md)

## <a name="next-steps"></a>다음 단계

이러한 연습을 완료하면 자신의 프로젝트를 만들기 시작할 준비가 된 것입니다. C++ 개발에 대한 자세한 내용과 리소스는 [Visual Studio의 Visual C++](../overview/visual-cpp-in-visual-studio.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[Visual Studio에서 개발 시작](/visualstudio/ide/get-started-developing-with-visual-studio)
