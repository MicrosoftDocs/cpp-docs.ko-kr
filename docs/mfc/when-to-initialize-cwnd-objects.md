---
title: CWnd 개체 초기화 시점
ms.date: 11/04/2016
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
ms.openlocfilehash: c75745547846fbf6c7e01ecf473d4d6f366bd264
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548553"
---
# <a name="when-to-initialize-cwnd-objects"></a>CWnd 개체 초기화 시점

생성자에서 모든 Windows API 함수를 호출 하거나 고유한 자식 창을 만들 수 없습니다는 `CWnd`-파생 개체입니다. 왜냐하면 합니다 `HWND` 에 대 한는 `CWnd` 개체에 아직 만들어지지 않았습니다. 자식 창에 추가 하는 등 대부분의 Windows 관련 초기화를 수행 해야 합니다는 [OnCreate](../mfc/reference/cwnd-class.md#oncreate) 메시지 처리기입니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아보려는 항목

- [문서 프레임 창 만들기](../mfc/creating-document-frame-windows.md)

- [문서/뷰 만들기](../mfc/document-view-creation.md)

## <a name="see-also"></a>참고 항목

[프레임 창 사용](../mfc/using-frame-windows.md)

