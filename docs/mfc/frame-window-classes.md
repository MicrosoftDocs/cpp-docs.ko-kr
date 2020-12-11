---
description: Frame-Window 클래스에 대해 자세히 알아보세요.
title: 프레임 창 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], about frame window classes
- frame window classes [MFC]
- windows [MFC], MDI
- document frame windows [MFC], classes
- single document interface (SDI), frame windows
- window classes [MFC], frame
- MFC, frame windows
- MDI [MFC], frame windows
- classes [MFC], window
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
ms.openlocfilehash: 888fae71bef2dd2e30e10c645e78ab981a30c6af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154957"
---
# <a name="frame-window-classes"></a>프레임 창 클래스

각 응용 프로그램에는 일반적으로 응용 프로그램 이름을 캡션에 포함 하는 바탕 화면 창의 "주 프레임 창"이 있습니다. 각 문서에는 일반적으로 "문서 프레임 창"이 하나 있습니다. 문서 프레임 창에는 문서의 데이터를 표시 하는 뷰가 하나 이상 포함 되어 있습니다.

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>SDI 및 MDI 응용 프로그램의 프레임 창

SDI 응용 프로그램의 경우 [CFrameWnd](reference/cframewnd-class.md)클래스에서 파생 된 하나의 프레임 창이 있습니다. 이 창은 주 프레임 창과 문서 프레임 창입니다. MDI 응용 프로그램의 경우 주 프레임 창은 [CMDIFrameWnd](reference/cmdiframewnd-class.md)클래스에서 파생 되 고 문서 프레임 창 (mdi 자식 창)은 [CMDIChildWnd](reference/cmdichildwnd-class.md)클래스에서 파생 됩니다.

## <a name="use-the-frame-window-class-or-derive-from-it"></a>Frame-Window 클래스를 사용 하거나 클래스에서 파생 합니다.

이러한 클래스는 응용 프로그램에 필요한 대부분의 프레임 창 기능을 제공 합니다. 정상적인 경우에는 제공 하는 기본 동작 및 모양이 요구에 맞게 표시 됩니다. 추가 기능이 필요한 경우 이러한 클래스에서 파생 합니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [응용 프로그램 마법사에서 만든 프레임 창 클래스](frame-window-classes-created-by-the-application-wizard.md)

- [프레임 창 스타일](frame-window-styles-cpp.md)

- [MFC에서 만든 창 스타일 변경](changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>참고 항목

[프레임 창](frame-windows.md)
