---
description: '자세한 정보: 트리 컨트롤 알림 메시지'
title: 트리 컨트롤 알림 메시지
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
ms.openlocfilehash: 899b6469a2de9a076dd33e62c5023f502448d45f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263987"
---
# <a name="tree-control-notification-messages"></a>트리 컨트롤 알림 메시지

트리 컨트롤 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))은 WM_NOTIFY 메시지로 다음 알림 메시지를 보냅니다.

|알림 메시지|설명|
|--------------------------|-----------------|
|TVN_BEGINDRAG|끌어서 놓기 작업의 시작을 신호로 보냅니다.|
|TVN_BEGINLABELEDIT|내부 레이블 편집의 시작을 신호로 보냅니다.|
|TVN_BEGINRDRAG|마우스 오른쪽 단추를 사용 하 여 끌어서 놓기 작업을 시작 하도록 신호를 보냅니다.|
|TVN_DELETEITEM|특정 항목을 삭제 하도록 신호를 보냅니다.|
|TVN_ENDLABELEDIT|레이블 편집의 끝을 신호로 보냅니다.|
|TVN_GETDISPINFO|트리 컨트롤에서 항목을 표시 하는 데 필요한 정보를 요청 합니다.|
|TVN_ITEMEXPANDED|부모 항목의 자식 항목 목록이 확장 또는 축소 되었음을 신호로 보냅니다.|
|TVN_ITEMEXPANDING|부모 항목의 자식 항목 목록이 확장 또는 축소 되려고 함을 신호로 보냅니다.|
|TVN_KEYDOWN|키보드 이벤트를 신호로 보냅니다.|
|TVN_SELCHANGED|한 항목에서 다른 항목으로 선택이 변경 되었음을 신호로 보냅니다.|
|TVN_SELCHANGING|한 항목에서 다른 항목으로 선택이 변경 되려고 함을 신호로 보냅니다.|
|TVN_SETDISPINFO|항목에 대해 유지 관리 되는 정보를 업데이트 하는 알림|

## <a name="see-also"></a>참고 항목

[CTreeCtrl 사용](../mfc/using-ctreectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
