---
description: '자세히 알아보기: 프레임 창'
title: 프레임 창
ms.date: 11/19/2018
helpviewer_keywords:
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame windows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
ms.openlocfilehash: ee993b7f8314c28dba38c9ca607366f6fb93da1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193502"
---
# <a name="frame-windows"></a>프레임 창

Windows에서 응용 프로그램을 실행 하는 경우 사용자는 프레임 창에 표시 된 문서와 상호 작용 합니다. 문서 프레임 창에는 프레임 및 프레임에 포함 되는 내용의 두 가지 주요 구성 요소가 있습니다. 문서 프레임 창은 SDI ( [단일 문서 인터페이스](sdi-and-mdi.md) ) 프레임 창 또는 MDI ( [다중 문서 인터페이스](sdi-and-mdi.md) ) 자식 창이 될 수 있습니다. Windows는 창 이동 및 크기 조정, 닫기, 최소화 및 최대화 등의 작업을 수행 하 여 대부분의 사용자 조작을 프레임 창과 함께 관리 합니다. 프레임 내에서 콘텐츠를 관리 합니다.

## <a name="frame-windows-and-views"></a>프레임 창 및 뷰

MFC 프레임 워크는 프레임 창을 사용 하 여 뷰를 포함 합니다. 두 가지 구성 요소 (프레임 및 내용)는 MFC의 서로 다른 두 클래스에 의해 표시 되 고 관리 됩니다. 프레임 창 클래스는 프레임을 관리 하 고 뷰 클래스는 콘텐츠를 관리 합니다. 뷰 창은 프레임 창의 자식입니다. 문서와의 그리기 및 기타 사용자 조작이 프레임 창의 클라이언트 영역이 아니라 뷰의 클라이언트 영역에서 발생 합니다. 프레임 창은 뷰 주위에 표시 되는 프레임을 제공 하 고, 캡션 표시줄 및 표준 창 컨트롤 (예: 컨트롤 메뉴), 창을 최소화 하 고 최대화 하는 단추, 창의 크기를 조정 하는 컨트롤을 제공 합니다. "내용"은 자식 창이 완전히 차지 하는 창의 클라이언트 영역으로 구성 됩니다. 다음 그림은 프레임 창과 뷰 간의 관계를 보여 줍니다.

![프레임 창 보기](../mfc/media/vc37fx1.gif "프레임 창 보기") <br/>
프레임 창 및 뷰

## <a name="frame-windows-and-splitter-windows"></a>프레임 창 및 분할자 창

또 다른 일반적인 정렬은 일반적으로 [분할자 창을](multiple-document-types-views-and-frame-windows.md)사용 하는 여러 뷰를 프레임 창에 배치 하는 것입니다. 분할자 창에서 프레임 창의 클라이언트 영역은 분할자 창에 사용 되며,이 창에는 뷰 인 창 이라는 여러 자식 창이 있습니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

**일반 프레임 창 항목**

- [창 개체](window-objects.md)

- [프레임 창 클래스](frame-window-classes.md)

- [응용 프로그램 마법사에서 만든 Frame-Window 클래스](frame-window-classes-created-by-the-application-wizard.md)

- [프레임 창 스타일](frame-window-styles-cpp.md)

- [프레임 창의 기능](what-frame-windows-do.md)

**프레임 창 사용에 대 한 항목**

- [프레임 창 사용](using-frame-windows.md)

- [문서 프레임 창 만들기](creating-document-frame-windows.md)

- [프레임 창 제거](destroying-frame-windows.md)

- [MDI 자식 창 관리](managing-mdi-child-windows.md)

- 둘 이상의 보기가 포함 된 프레임 창에서 [현재 뷰 관리](managing-the-current-view.md)

- [메뉴, 컨트롤 막대 및 액셀러레이터 관리 (프레임 창 공간을 공유 하는 다른 개체)](managing-menus-control-bars-and-accelerators.md)

**특수 프레임 창 기능에 대 한 항목**

- 파일 탐색기 또는 파일 관리자에서 프레임 창으로 [파일 끌어서 놓기](dragging-and-dropping-files-in-a-frame-window.md)

- [DDE (동적 데이터 교환)에 응답](responding-to-dynamic-data-exchange-dde.md)

- [Semimodal states: 상황에 맞는 Windows 도움말 (오케스트레이션 기타 창 작업)](orchestrating-other-window-actions.md)

- [Semimodal 상태: 인쇄 및 인쇄 미리 보기 (오케스트레이션 기타 창 작업)](orchestrating-other-window-actions.md)

**다른 종류의 창에 대 한 항목**

- [뷰 사용](using-views.md)

- [대화 상자](dialog-boxes.md)

- [컨트롤](controls-mfc.md)

## <a name="see-also"></a>참고 항목

[Windows](windows.md)
