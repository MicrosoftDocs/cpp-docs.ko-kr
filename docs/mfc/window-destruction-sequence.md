---
description: '자세히 알아보기: 창 소멸 시퀀스'
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
ms.openlocfilehash: 2ba60f1dcd3668a754bbe4384a6c8cf6b4d541d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207685"
---
# <a name="window-destruction-sequence"></a>창 소멸 시퀀스

MFC 프레임 워크에서 사용자가 프레임 창을 닫으면 창의 기본 [OnClose](../mfc/reference/cwnd-class.md#onclose) 처리기는 [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)를 호출 합니다. Windows 창이 제거 될 때 호출 되는 마지막 멤버 함수는 [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy)입니다 .이 함수는 정리를 수행 하 고 [기본](../mfc/reference/cwnd-class.md#default) 멤버 함수를 호출 하 여 windows 정리를 수행 하며, 마지막으로 가상 멤버 함수 [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)를 호출 합니다. 의 [CFrameWnd](../mfc/reference/cframewnd-class.md) 구현은 `PostNcDestroy` c + + 창 개체를 삭제 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [창 메모리 할당 및 할당 취소](../mfc/allocating-and-deallocating-window-memory.md)

- [CWnd를 해당 HWND에서 분리](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>참고 항목

[창 개체 소멸](../mfc/destroying-window-objects.md)
