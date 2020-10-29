---
title: '연습: 표준 C++ 프로그램 만들기(C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 778a73e62a834dd73aca1a22bd4dd7f244e7bb4d
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924244"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>연습: 표준 C++ 프로그램 만들기(C++)

Visual Studio를 사용 하 여 표준 c + + 프로그램을 만들 수 있습니다. 이 연습의 단계를 수행 하 여 프로젝트를 만들고, 프로젝트에 새 파일을 추가 하 고, c + + 코드를 추가 하도록 파일을 수정 하 고, Visual Studio를 사용 하 여 프로그램을 컴파일하고 실행할 수 있습니다.

사용자 고유의 c + + 프로그램을 입력 하거나 샘플 프로그램 중 하나를 사용할 수 있습니다. 이 연습의 샘플 프로그램은 콘솔 응용 프로그램입니다. 이 응용 프로그램은 `set` c + + 표준 라이브러리의 컨테이너를 사용 합니다.

> [!NOTE]
> 특정 버전의 c + + 언어 표준 (예: c + + 14 또는 c + + 17)을 준수 해야 하는 경우 `/std:c++14` 또는 `/std:c++17` 컴파일러 옵션을 사용 합니다. (Visual Studio 2017 이상)

## <a name="prerequisites"></a>사전 요구 사항

이 연습을 완료하려면 C++ 언어의 기본적인 사항을 알고 있어야 합니다.

### <a name="to-create-a-project-and-add-a-source-file"></a>프로젝트를 만들고 소스 파일을 추가 하려면

다음 단계는 사용 중인 Visual Studio 버전에 따라 다릅니다. 기본 설정된 버전의 Visual Studio에 대한 설명서를 보려면 **버전** 선택기 컨트롤을 사용하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker range="msvc-160"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Visual Studio 2019에서 c + + 프로젝트를 만들려면

1. 주 메뉴에서 **파일** > **새로 만들기** > **프로젝트** 를 선택하여 **새 프로젝트 만들기** 대화 상자를 엽니다.

1. 대화 상자 맨 위에서 **언어** 를 **C++** 로 설정하고 **플랫폼** 을 **Windows** 로 설정하고 **프로젝트 형식** 을 **콘솔** 로 설정합니다.

1. 필터링된 프로젝트 형식 목록에서 **콘솔 앱** 을 선택한 후 **다음** 을 선택합니다. 다음 페이지에서 프로젝트의 이름을 입력하고 원하는 경우 프로젝트 위치를 지정합니다.

1. **만들기** 단추를 선택하여 프로젝트를 만듭니다.

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Visual Studio 2017에서 c + + 프로젝트를 만들려면

1. **파일** 메뉴에서 **새로 만들기** 를 가리킨 다음 **프로젝트** 를 클릭 하 여 프로젝트를 만듭니다.

1. **Visual C++** 프로젝트 형식 창에서 **windows 바탕 화면** 을 클릭 한 다음 **windows 콘솔 응용 프로그램** 을 클릭 합니다.

1. 프로젝트의 이름을 입력 합니다. 기본적으로 프로젝트를 포함 하는 솔루션의 이름은 프로젝트 이름과 동일 하지만 다른 이름을 입력할 수 있습니다. 프로젝트의 다른 위치를 입력할 수도 있습니다.

1. **확인** 을 클릭하여 프로젝트를 만듭니다.

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Visual Studio 2015에서 c + + 프로젝트를 만들려면

1. **파일** 메뉴에서 **새로 만들기** 를 가리킨 다음 **프로젝트** 를 클릭 하 여 프로젝트를 만듭니다.

1. **Visual C++** 프로젝트 형식 창에서 **windows 바탕 화면** 을 클릭 한 다음 **windows 콘솔 응용 프로그램** 을 클릭 합니다.

1. **새 프로젝트** 대화 상자에서 **설치 된**  >  **템플릿**  >  **Visual C++** 을 확장 하 고 **Win32** 를 선택 합니다. 가운데 창에서 **Win32 콘솔 애플리케이션** 을 선택합니다.

1. 프로젝트의 이름을 입력 합니다. 기본적으로 프로젝트를 포함 하는 솔루션의 이름은 프로젝트 이름과 동일 하지만 다른 이름을 입력할 수 있습니다. 프로젝트의 다른 위치를 입력할 수도 있습니다.

1. **확인** 을 클릭하여 프로젝트를 만듭니다.

1. **Win32 응용 프로그램 마법사** 를 완료 합니다.

1. **다음** 을 클릭 한 다음 **콘솔 응용 프로그램** 이 선택 되어 있는지 확인 하 고 **미리 컴파일된 헤더** 상자의 선택을 취소 합니다.

1. **마침** 을 클릭합니다.

::: moniker-end

## <a name="add-a-new-source-file"></a>새 소스 파일 추가

1. **솔루션 탐색기** 표시 되지 않으면 **보기** 메뉴에서 **솔루션 탐색기** 를 클릭 합니다.

1. 다음과 같이 프로젝트에 새 소스 파일을 추가 합니다.

   1. **솔루션 탐색기** 에서 **소스 파일** 폴더를 마우스 오른쪽 단추로 클릭 하 고 **추가** 를 가리킨 다음 **새 항목** 을 클릭 합니다.

   1. **코드** 노드에서 **c + + 파일 (.cpp)** 을 클릭 하 고 파일 이름을 입력 한 다음 **추가** 를 클릭 합니다.

   .Cpp 파일은 **솔루션 탐색기** 의 **소스 파일** 폴더에 표시 되 고 파일은 Visual Studio 편집기에서 열립니다.

1. 편집기의 파일에 c + + 표준 라이브러리를 사용 하는 올바른 c + + 프로그램을 입력 하거나 샘플 프로그램 중 하나를 복사 하 여 파일에 붙여넣습니다.

1. 파일을 저장합니다.

1. **빌드** 메뉴에서 **솔루션 빌드** 를 클릭합니다.

   **출력** 창에는 빌드 로그의 위치 및 빌드 상태를 나타내는 메시지와 같은 컴파일 진행률에 대 한 정보가 표시 됩니다.

1. **디버그** 메뉴에서 **디버깅 하지 않고 시작** 을 클릭 합니다.

   샘플 프로그램을 사용 하는 경우 명령 창이 표시 되 고 특정 정수가 집합에 있는지 여부를 표시 합니다.

## <a name="next-steps"></a>다음 단계

**이전:** [Visual C++의 콘솔 응용 프로그램](./overview-of-windows-programming-in-cpp.md)<br/>
**다음:** [연습: 명령줄에서 네이티브 c + + 프로그램 컴파일](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>참조

[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[C + + 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)
