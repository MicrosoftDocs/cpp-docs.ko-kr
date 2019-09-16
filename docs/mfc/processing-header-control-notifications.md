---
title: 헤더 컨트롤 알림 처리
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
ms.openlocfilehash: bc811763fe3f4717b8baaeb4a23df1ae59bb1979
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908131"
---
# <a name="processing-header-control-notifications"></a>헤더 컨트롤 알림 처리

보기 또는 대화 상자 클래스에서 [클래스 마법사](reference/mfc-class-wizard.md) 를 사용 하 여 처리 하려는[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)(헤더 컨트롤) 알림 메시지에 대 한 switch 문을 사용 하 여 [onchildnotify](../mfc/reference/cwnd-class.md#onchildnotify) 처리기 함수를 만듭니다 (메시지 매핑 참조). [ 함수](../mfc/reference/mapping-messages-to-functions.md)). 사용자가 머리글 항목을 클릭 하거나 두 번 클릭 하 고 항목 사이에 구분선을 끌어와 같이 알림이 부모 창으로 전송 됩니다.

헤더 컨트롤과 연결 된 알림 메시지는 Windows SDK의 [헤더 컨트롤 참조](/windows/win32/controls/header-control-reference) 에 나열 됩니다.

## <a name="see-also"></a>참고자료

[CHeaderCtrl 사용](../mfc/using-cheaderctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
