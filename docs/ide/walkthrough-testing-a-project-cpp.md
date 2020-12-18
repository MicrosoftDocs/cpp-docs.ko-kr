---
description: '자세한 정보: 연습: 프로젝트 테스트(C++)'
title: '연습: 프로젝트 테스트(C++)'
ms.date: 04/25/2019
helpviewer_keywords:
- project testing [C++]
- testing projects
- projects [C++], testing
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
ms.openlocfilehash: 0469f6c161689d2638cfb206c91c2530b72cd00b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334764"
---
# <a name="walkthrough-testing-a-project-c"></a>연습: 프로젝트 테스트(C++)

디버그 모드로 프로그램을 실행하는 경우 중단점을 사용하여 변수 및 개체의 상태를 검사하기 위해 프로그램을 일시 중지할 수 있습니다.

이 연습에서는 프로그램이 실행될 때 변수 값을 확인하고, 기대한 것과 값이 다른 이유를 추론합니다.

## <a name="prerequisites"></a>사전 요구 사항

- 이 연습에서는 사용자가 C++ 언어의 기본적인 사항을 알고 있는 것으로 가정합니다.

- 또한 [Visual Studio IDE를 사용하여 C++ 데스크톱 개발](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)에 나열된 이전 관련 연습을 완료했다고 가정합니다.

### <a name="to-run-a-program-in-debug-mode"></a>디버그 모드로 프로그램을 실행하려면

1. 편집을 위해 Games.cpp를 엽니다.

1. 다음과 같은 코드 줄을 선택합니다.

   `Cardgame solitaire(1);`

1. 해당 줄에 중단점을 설정하려면 메뉴 모음에서 **디버그** > **중단점 설정/해제** 를 선택하거나 **F9** 키를 선택합니다. 줄의 왼쪽에 빨간색 원이 나타나면 중단점이 설정되었음을 나타냅니다. 중단점을 제거하려면 메뉴 명령이나 **F9** 키를 다시 선택하면 됩니다.

   마우스를 사용하는 경우에도 왼쪽 여백을 클릭하여 중단점을 설정하거나 제거할 수 있습니다.

1. 메뉴 모음에서 **디버그** > **디버깅 시작** 을 선택하거나 **F5** 키를 선택합니다.

   프로그램이 중단점을 포함한 줄에 도달하면 프로그램이 중단 모드이기 때문에 실행이 일시적으로 중지됩니다. 코드 줄의 왼쪽에 있는 노란색 화살표는 실행될 다음 줄을 나타냅니다.

1. `Cardgame::totalParticipants` 변수의 값을 검사하려면 포인터를 `Cardgame` 위로 이동한 다음, 도구 설명 창의 왼쪽에 있는 확장 컨트롤 위로 이동합니다. 변수 이름 `totalParticipants` 및 **12** 라는 해당 값이 표시됩니다.

   `Cardgame::totalParticipants` 변수의 바로 가기 메뉴를 연 다음, **조사식 추가** 를 선택하여 **조사식 1** 창에서 해당 변수를 표시합니다. 또한 변수를 강조 표시하고 **조사식 1** 창으로 끌어올 수 있습니다.

1. 다음 코드 줄로 이동하려면 메뉴 모음에서 **디버그** > **프로시저 단위 실행** 을 선택하거나 **F10** 키를 선택합니다.

   **조사식 1** 창의 `Cardgame::totalParticipants` 값은 이제 **13** 으로 표시됩니다.

1. `return 0;` 문의 바로 가기 메뉴를 연 다음, **커서까지 실행** 을 선택합니다. 코드의 왼쪽에 있는 노란색 화살표는 실행될 다음 문을 가리킵니다.

1. `Cardgame::totalParticipants` 번호는 `Cardgame`이 종료될 때 감소해야 합니다. 이 시점에서 모든 `Cardgame` 인스턴스가 삭제되었으므로 `Cardgame::totalParticipants`는 0과 같아야 하지만 **조사식 1** 창은 `Cardgame::totalparticipants`가 **18** 과 같음을 나타냅니다. 이 차이는 코드에 버그가 있음을 나타냅니다. 이것은 [연습: 프로젝트 디버깅(C++)](../ide/walkthrough-debugging-a-project-cpp.md) 연습을 완료하여 검색하고 수정할 수 있습니다.

1. 프로그램을 중지하려면 메뉴 모음에서 **디버그** > **디버깅 중지** 를 선택하거나 **Shift**+**F5** 바로 가기 키를 선택합니다.

## <a name="next-steps"></a>다음 단계

**이전:** [연습: 프로젝트 빌드(C++)](../ide/walkthrough-building-a-project-cpp.md)<br/>
**다음:** [연습: 프로젝트 디버깅(C++)](../ide/walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>참조

[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[프로젝트 및 빌드 시스템](../build/projects-and-build-systems-cpp.md)<br/>
