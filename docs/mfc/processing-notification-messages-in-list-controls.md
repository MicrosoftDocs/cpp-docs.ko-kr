---
description: '자세히 알아보기: 목록 컨트롤에서 알림 메시지 처리'
title: 목록 컨트롤에서 알림 메시지 처리
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: b761f5213a73ce31484a7a252b9b441da2fe154d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154801"
---
# <a name="processing-notification-messages-in-list-controls"></a>목록 컨트롤에서 알림 메시지 처리

사용자가 열 머리글을 클릭 하 고 아이콘을 끌어서 레이블을 편집 하는 등의 방법으로 목록 컨트롤 ([CListCtrl](../mfc/reference/clistctrl-class.md))은 해당 부모 창에 알림 메시지를 보냅니다. 이에 대한 응답으로 작업을 수행하려는 경우 이러한 메시지를 처리합니다. 예를 들어 사용자가 열 머리글을 클릭 하는 경우 Microsoft Outlook에서와 같이 클릭 된 열의 내용을 기준으로 항목을 정렬 하는 것이 좋습니다.

보기 또는 대화 상자 클래스의 목록 컨트롤에서 WM_NOTIFY 메시지를 처리 합니다. [클래스 마법사](reference/mfc-class-wizard.md) 를 사용 하 여 처리 되는 알림 메시지에 따라 switch 문을 사용 하 여 [onchildnotify](../mfc/reference/cwnd-class.md#onchildnotify) 처리기 함수를 만듭니다.

목록 컨트롤이 부모 창에 보낼 수 있는 알림 목록은 Windows SDK의 [목록 뷰 컨트롤 참조](/windows/win32/Controls/list-view-control-reference) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CListCtrl 사용](../mfc/using-clistctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
