---
description: '자세한 정보: CWnd 개체를 초기화 하는 경우'
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
ms.openlocfilehash: 89d40b826507574fddd41364ac6cecc526663519
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142768"
---
# <a name="when-to-initialize-cwnd-objects"></a>CWnd 개체 초기화 시점

사용자 고유의 자식 창을 만들거나 파생 개체의 생성자에서 Windows API 함수를 호출할 수 없습니다 `CWnd` . 이는 `HWND` 개체에 대 한가 아직 만들어지지 않았기 때문입니다 `CWnd` . 자식 창 추가와 같은 대부분의 Windows 관련 초기화는 [OnCreate](../mfc/reference/cwnd-class.md#oncreate) 메시지 처리기에서 수행 해야 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [문서 프레임 창 만들기](../mfc/creating-document-frame-windows.md)

- [문서/뷰 만들기](../mfc/document-view-creation.md)

## <a name="see-also"></a>참고 항목

[프레임 창 사용](../mfc/using-frame-windows.md)
