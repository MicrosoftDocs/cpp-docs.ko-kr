---
description: '자세한 정보: 트리 컨트롤 레이블 편집'
title: 트리 컨트롤 레이블 편집
ms.date: 11/04/2016
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
ms.openlocfilehash: b471b2ce9773ec86b1e4f94e766d3428fef456fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264013"
---
# <a name="tree-control-label-editing"></a>트리 컨트롤 레이블 편집

사용자는 **TVS_EDITLABELS** 스타일이 있는 트리 컨트롤 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))의 항목 레이블을 직접 편집할 수 있습니다. 사용자는 포커스가 있는 항목의 레이블을 클릭 하 여 편집을 시작 합니다. 응용 프로그램은 [Editlabel](../mfc/reference/ctreectrl-class.md#editlabel) 멤버 함수를 사용 하 여 편집을 시작 합니다. 트리 컨트롤은 편집이 시작 될 때와 취소 되거나 완료 될 때 알림을 보냅니다. 편집이 완료 되 면 해당 하는 경우 항목의 레이블을 업데이트 해야 합니다.

레이블 편집이 시작 되 면 트리 컨트롤이 [TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit) 알림 메시지를 보냅니다. 이 알림을 처리 하면 일부 레이블의 편집을 허용 하 고 다른 레이블의 편집을 방지할 수 있습니다. 0을 반환 하면 편집이 허용 되 고 0이 아닌 값이 반환 됩니다.

레이블 편집이 취소 되거나 완료 되 면 트리 컨트롤이 [TVN_ENDLABELEDIT](/windows/win32/Controls/tvn-endlabeledit) 알림 메시지를 보냅니다. *LParam* 매개 변수는 [NMTVDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmtvdispinfow) 구조체의 주소입니다. **항목** 멤버는 항목을 식별 하 고 편집 된 텍스트를 포함 하는 [tvitem](/windows/win32/api/commctrl/ns-commctrl-tvitemw) 구조입니다. 편집 된 문자열의 유효성을 검사 한 후 해당 하는 경우 항목의 레이블을 업데이트 해야 합니다.  `TV_ITEM` 편집이 취소 된 경우의 pszText 멤버는 0입니다.

일반적으로 [TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit) 알림 메시지에 대 한 응답으로 레이블 편집 중에 [geteditcontrol](../mfc/reference/ctreectrl-class.md#geteditcontrol) 멤버 함수를 사용 하 여 레이블 편집에 사용 되는 편집 컨트롤에 대 한 포인터를 가져올 수 있습니다. 편집 컨트롤의 [Setlimit 텍스트](../mfc/reference/cedit-class.md#setlimittext) 멤버 함수를 호출 하 여 사용자가 입력 하거나, 편집 컨트롤의 서브 클래스를 사용 하 여 잘못 된 문자를 가로채 고 삭제할 수 있는 텍스트의 양을 제한할 수 있습니다. 그러나 편집 컨트롤은 **TVN_BEGINLABELEDIT** 를 보낸 *후* 에만 표시 됩니다.

## <a name="see-also"></a>참고 항목

[CTreeCtrl 사용](../mfc/using-ctreectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
