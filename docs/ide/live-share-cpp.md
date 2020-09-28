---
title: Visual Studio에서 C++용 Live Share를 사용하여 협업
description: Visual Studio에서 C++용 Live Share를 사용하여 협업하고 실시간으로 코드를 공유합니다.
ms.date: 05/24/2019
ms.openlocfilehash: 60830ad6c6b98f644e1c3ddb2e78fbf7397ae919
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684523"
---
# <a name="collaborate-using-live-share-for-c"></a>C++용 Live Share를 사용하여 협업

Visual Studio 2019 및 Visual Studio Code에서 **Live Share**를 사용하여 실시간으로 C++ 프로젝트를 협업할 수 있습니다. **Live Share**를 사용하여 다른 사용자는 프로젝트 또는 해당 종속성을 설치할 필요 없이 코드를 편집 및 디버깅할 수 있습니다. 발생하는 대로 서로의 편집이 표시되고 각 편집은 편집을 수행한 사람의 이름으로 태그가 지정됩니다.

![C&#43;&#43; Live Share 편집](../ide/media/live-share-edit-cpp.png "C++에서 Live Share 편집")

## <a name="live-share-host-and-guests"></a>Live Share 호스트 및 게스트

Live Share 세션에는 하나의 호스트와 하나 이상의 게스트가 있습니다. 호스트와 게스트 모두 Visual Studio 또는 Visual Studio Code를 사용할 수 있습니다. Windows의 Visual Studio 2019 호스트는 Linux의 Visual Studio Code 게스트와 공유할 수 있습니다.

호스트는 게스트에게 생산성을 높이기 위해 필요한 모든 것을 제공합니다. 게스트는 소스 코드, 컴파일러, 외부 종속성 또는 설치된 동일한 구성 요소를 가질 필요가 없습니다.

호스트 및 게스트는 이러한 IntelliSense 기능을 사용할 수 있습니다.

- 멤버 목록
- 매개 변수 도움말
- 요약 정보
- 디버깅/중단점
- 모든 참조 찾기
- 정의로 이동
- 기호 검색(Ctrl+T)
- 참조 강조 표시
- 진단/오류/오류 표시선

![C&#43;&#43; Live Share 디버깅](../ide/media/live-share-debug-cpp.png "C++에서 Live Share 디버깅")

## <a name="start-and-end-a-live-share-session"></a>Live Share 세션 시작 및 종료

Visual Studio에서 Live Share 세션을 시작하려면 오른쪽 맨 위에서 공유 단추를 클릭하거나 **파일** > **협업 세션 시작**으로 이동합니다. 협력자와 공유할 수 있는 링크를 생성합니다.

![Live Share 단추의 작은 스크린샷](../ide/media/live-share-button-cpp.png "Live Share 단추")

세션을 종료하려면 **공유** 드롭다운에서 ** 세션 종료**를 선택합니다.

![공동 작업 세션 종료 옵션이 강조 표시된 공유 드롭다운 목록의 스크린샷](../ide/media/live-share-end-session-cpp.png "Live Share 단추")

## <a name="for-more-information"></a>참조 항목

Visual Studio에서 **Live Share**에 대한 자세한 내용은 [Visual Studio Live Share란?](/visualstudio/liveshare/)을 참조하세요. Visual Studio Code에서 Live Share에 대한 자세한 내용은 [ Live Share](https://marketplace.visualstudio.com/items?itemName=ms-vsliveshare.vsliveshare)를 참조하세요.

## <a name="see-also"></a>참고 항목

[코드(C++) 편집 및 리팩터링](writing-and-refactoring-code-cpp.md)</br>
[Visual Studio에서 C++ 코드 베이스 탐색](navigate-code-cpp.md)</br>
[C++ 코드 읽기 및 이해](read-and-understand-code-cpp.md)</br>
