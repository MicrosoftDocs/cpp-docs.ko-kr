---
description: '자세한 정보: 트리 컨트롤 부모 및 자식 항목'
title: 트리 컨트롤 부모 및 자식 항목
ms.date: 11/04/2016
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
ms.openlocfilehash: b1af78bf8a22c46b45e1fd8952944249c41bd5e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263961"
---
# <a name="tree-control-parent-and-child-items"></a>트리 컨트롤 부모 및 자식 항목

트리 컨트롤 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))의 모든 항목에는 자식 항목 이라고 하는 하위 항목의 목록이 연결 되어 있을 수 있습니다. 하나 이상의 자식 항목을 포함 하는 항목을 부모 항목 이라고 합니다. 자식 항목이 부모 항목 아래에 표시 되 고 부모 항목에 하위 항목이 있음을 나타내기 위해 들여씁니다. 부모가 없는 항목은 계층의 맨 위에 있고 루트 항목 이라고 합니다.

지정 된 시간에 부모 항목의 자식 항목 목록 상태는 확장 하거나 축소할 수 있습니다. 상태를 확장 하면 자식 항목이 부모 항목 아래에 표시 됩니다. 축소 된 경우에는 자식 항목이 표시 되지 않습니다. 사용자가 부모 항목을 두 번 클릭 하거나 부모 항목에 연결 된 단추를 클릭할 때 부모 항목에 **TVS_HASBUTTONS** 스타일이 있으면 목록에서 확장 된 상태와 축소 된 상태 사이를 자동으로 전환 합니다. 응용 프로그램은 [expand](../mfc/reference/ctreectrl-class.md#expand) 멤버 함수를 사용 하 여 자식 항목을 확장 하거나 축소할 수 있습니다.

[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) 멤버 함수를 호출 하 여 트리 컨트롤에 항목을 추가 합니다. 이 함수는 항목을 고유 하 게 식별 하는 **HTREEITEM** 형식의 핸들을 반환 합니다. 항목을 추가할 때 새 항목의 부모 항목에 대 한 핸들을 지정 해야 합니다. [Tvinsertstruct](/windows/win32/api/commctrl/ns-commctrl-tvinsertstructw) 구조 또는 *hparent* 매개 변수에서 부모 항목 핸들 대신 **NULL** 또는 **TVI_ROOT** 값을 지정 하면 항목이 루트 항목으로 추가 됩니다.

부모 항목의 자식 항목 목록을 확장 하거나 축소할 때 트리 컨트롤에서 [TVN_ITEMEXPANDING](/windows/win32/Controls/tvn-itemexpanding) 알림 메시지를 보냅니다. 이 알림은 변경을 방지 하거나 자식 항목 목록의 상태에 종속 된 부모 항목의 특성을 설정할 수 있는 기회를 제공 합니다. 목록 상태를 변경한 후에는 트리 컨트롤이 [TVN_ITEMEXPANDED](/windows/win32/Controls/tvn-itemexpanded) 알림 메시지를 보냅니다.

자식 항목의 목록이 확장 되 면 부모 항목을 기준으로 들여씁니다. [Setindent](../mfc/reference/ctreectrl-class.md#setindent) 멤버 함수를 사용 하 여 들여쓰기 크기를 설정 하거나 [getindent](../mfc/reference/ctreectrl-class.md#getindent) 멤버 함수를 사용 하 여 현재 크기를 검색할 수 있습니다.

## <a name="see-also"></a>참고 항목

[CTreeCtrl 사용](../mfc/using-ctreectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
