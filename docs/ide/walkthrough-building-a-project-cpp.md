---
description: '자세한 정보: 연습: 프로젝트 빌드(C++)'
title: '연습: 프로젝트 빌드(C++)'
ms.date: 04/25/2019
helpviewer_keywords:
- building projects [C++]
- projects [C++], building
- project building [C++]
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
ms.openlocfilehash: f606a0ead796916fa41f7669852e67d58ae3b17c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222543"
---
# <a name="walkthrough-building-a-project-c"></a>연습: 프로젝트 빌드(C++)

이 연습에서는 의도적으로 코드에 C++ 구문 오류를 도입하여 어떠한 컴파일 오류가 발생하는지 확인하고 이를 수정하는 방법에 대해 살펴봅니다. 프로젝트를 컴파일하면 어디에 어떠한 문제가 있는지 표시하는 오류 메시지가 나타납니다.

## <a name="prerequisites"></a>사전 요구 사항

- 이 연습에서는 사용자가 C++ 언어의 기본적인 사항을 알고 있는 것으로 가정합니다.

- 또한 [Visual Studio IDE를 사용하여 C++ 데스크톱 개발](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)에 나열된 이전 관련 연습을 완료했다고 가정합니다.

### <a name="to-fix-compilation-errors"></a>컴파일 오류를 수정하려면

1. Game.cpp에서 마지막 줄의 세미콜론을 삭제하여 다음 문과 같이 만듭니다.

   `return 0`

1. 메뉴 모음에서 **빌드** > **솔루션 빌드** 를 선택합니다.

1. **오류 목록** 창의 메시지에 프로젝트 빌드에 오류가 있는 것으로 표시되어 있습니다. 설명은 다음 오류 메시지와 같이 나타납니다.

   `error C2143: syntax error: missing ';' before '}'`

   이 오류에 대한 도움말 정보를 보려면 **오류 목록** 창에서 오류를 강조 표시한 후 **F1** 키를 선택합니다.

1. 구문 오류가 발생한 줄의 끝에 세미콜론을 다시 추가합니다.

   `return 0;`

1. 메뉴 모음에서 **빌드** > **솔루션 빌드** 를 선택합니다.

   프로젝트가 성공적으로 컴파일되었다는 메시지가 **출력** 창에 표시됩니다.

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>Game.cpp
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

## <a name="next-steps"></a>다음 단계

**이전:** [연습: 프로젝트 및 솔루션 작업(C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)<br/>
**다음:** [연습: 프로젝트 테스트(C++)](../ide/walkthrough-testing-a-project-cpp.md)

## <a name="see-also"></a>참조

[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[프로젝트 및 빌드 시스템](../build/projects-and-build-systems-cpp.md)<br/>
