---
title: 창 소멸 시퀀스
ms.date: 11/04/2016
helpviewer_keywords:
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
ms.openlocfilehash: 07312d6c7bba219cebcfa2c73a8d66c9c97ec08e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571355"
---
# <a name="window-destruction-sequence"></a>창 소멸 시퀀스

MFC 프레임 워크를 사용자가 창의 기본 프레임 창을 닫으면 [OnClose](../mfc/reference/cwnd-class.md#onclose) 처리기 호출 [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)합니다. Windows 창을 소멸 될 때 호출 되는 마지막 멤버 함수는 [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), 일부 정리를 수행 하는 호출을 [기본](../mfc/reference/cwnd-class.md#default) 멤버 Windows 정리를 수행 하도록 함수를 마지막으로 호출 합니다 가상 멤버 함수 [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)합니다. 합니다 [CFrameWnd](../mfc/reference/cframewnd-class.md) 구현의 `PostNcDestroy` c + + 창 개체를 삭제 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아보려는 항목

- [할당 및 창 메모리 할당 취소](../mfc/allocating-and-deallocating-window-memory.md)

- [해당 HWND에서에서 CWnd 분리](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>참고 항목

[창 개체 제거](../mfc/destroying-window-objects.md)

