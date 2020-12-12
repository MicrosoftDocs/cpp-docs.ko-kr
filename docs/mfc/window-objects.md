---
description: '자세히 알아보기: 창 개체'
title: 창 개체
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], window
- Windows window [MFC]
- MFC, windows
- frame windows [MFC], C++ window objects
- window objects [MFC]
- windows [MFC], C++ window objects
- window messages [MFC]
- HWND
- messages [MFC], Windows
- Visual C++, window objects [MFC]
- HWND, window objects [MFC]
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
ms.openlocfilehash: 5a7755dfecc8205279785a6452b04c3f8dc429d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214496"
---
# <a name="window-objects"></a>창 개체

MFC는 창의 핸들을 캡슐화 하는 [CWnd](../mfc/reference/cwnd-class.md) 클래스를 제공 `HWND` 합니다. `CWnd` 개체는 Windows 창을 나타내는 `HWND`와 다른 C++ 창 개체이지만 이를 포함합니다. `CWnd`를 사용하여 고유한 자식 창 클래스를 파생시키거나 `CWnd`에서 파생된 여러 MFC 클래스 중 하나를 사용합니다. `CWnd` 클래스는 프레임 창, 대화 상자, 자식 창, 컨트롤 및 컨트롤 막대(예: 도구 모음)를 포함하는 모든 창에 대한 기본 클래스입니다. [C + + 창 개체와 HWND 간의 관계](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md) 를 이해 하는 것은 MFC를 사용 하 여 효과적으로 프로그래밍 하는 데 매우 중요 합니다.

MFC에서는 몇 가지 기본 기능 및 창 관리를 제공하지만 `CWnd`에서 고유한 클래스를 파생시킬 수 있고 해당 멤버 함수를 사용하여 제공된 기능을 사용자 지정할 수 있습니다. 개체를 생성 `CWnd` 하 고 해당 [create](../mfc/reference/cwnd-class.md#create) member 함수를 호출한 다음 멤버 함수를 사용 하 여 자식 창을 사용자 지정 하 여 자식 창을 만들 수 있습니다 `CWnd` . [CView](../mfc/reference/cview-class.md)에서 파생 된 개체 (예: 폼 보기 또는 트리 뷰)를 프레임 창에 포함할 수 있습니다. [CSplitterWnd](../mfc/reference/csplitterwnd-class.md)클래스에서 제공 하는 분할자 창을 통해 문서에 대 한 여러 뷰를 지원할 수 있습니다.

`CWnd` 클래스에서 파생된 각 개체에는 Windows 메시지 또는 명령 ID를 고유한 처리기에 매핑할 수 있는 메시지 맵이 포함됩니다.

Windows 프로그래밍에 대한 일반 문서는 `CWnd` API를 캡슐화하는 `HWND` 멤버 함수를 사용하는 방법을 학습하기 위한 좋은 리소스입니다.

## <a name="functions-for-operating-on-a-cwnd"></a>CWnd에서 작동하는 함수

`CWnd` 및 해당 [파생 창 클래스](../mfc/derived-window-classes.md) 는 생성자, 소멸자 및 멤버 함수를 제공 하 여 개체를 초기화 하 고, 기본 Windows 구조체를 만들고, 캡슐화 된에 액세스 합니다 `HWND` . `CWnd`는 메시지 전송, 창 상태에 액세스, 좌표 변환, 업데이트, 스크롤, 클립보드에 액세스 및 기타 여러 작업을 위해 Windows API를 캡슐화하는 멤버 함수도 제공합니다. `HWND` 인수를 사용하는 대부분의 Windows 창 관리 API는 `CWnd` 멤버 함수로 캡슐화됩니다. 함수와 매개 변수 이름은 `CWnd` 멤버 함수에서 유지됩니다. 로 캡슐화 된 Windows Api에 대 한 자세한 `CWnd` 내용은 [CWnd](../mfc/reference/cwnd-class.md)클래스를 참조 하세요.

## <a name="cwnd-and-windows-messages"></a>CWnd 및 Windows 메시지

의 주요 용도 중 하나 `CWnd` 는 WM_PAINT 또는 WM_MOUSEMOVE와 같은 Windows 메시지를 처리 하기 위한 인터페이스를 제공 하는 것입니다. 의 멤버 함수 대부분은 `CWnd` 표준 메시지에 대 한 처리기입니다 .이는 식별자 **afx_msg** 로 시작 하 고 및와 같은 접두사 "On"으로 시작 `OnPaint` `OnMouseMove` 합니다. 메시지 [처리 및 매핑은](../mfc/message-handling-and-mapping.md) 메시지와 메시지 처리에 대해 자세히 설명 합니다. 프레임워크의 창과 특수 목적을 위해 사용자가 직접 만든 창에 정보가 동일하게 적용됩니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [C++ 창 개체와 HWND 간 관계](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)

- [파생된 창 클래스](../mfc/derived-window-classes.md)

- [창 만들기](../mfc/creating-windows.md)

- [창 개체 소멸](../mfc/destroying-window-objects.md)

- [CWnd를 해당 HWND에서 분리](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [창 개체 작업](../mfc/working-with-window-objects.md)

- [장치 컨텍스트](../mfc/device-contexts.md): Windows 그리기 장치를 독립적으로 만드는 개체

- [그래픽 개체](../mfc/graphic-objects.md): 펜, 브러시, 글꼴, 비트맵, 색상표, 영역

## <a name="see-also"></a>참고 항목

[Windows](../mfc/windows.md)
