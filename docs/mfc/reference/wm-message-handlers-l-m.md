---
description: '자세한 내용은 WM_ 메시지 처리기: L-M'
title: 'WM_ 메시지 처리기: L - M'
ms.date: 11/04/2016
f1_keywords:
- ON_WM_MENUSELECT
- ON_WM_MBUTTONDBLCLK
- ON_WM_MOUSEACTIVATE
- ON_WM_MOUSEMOVE
- ON_WM_MOVING
- ON_WM_LBUTTONUP
- ON_WM_LBUTTONDBLCLK
- ON_WM_MEASUREITEM
- ON_WM_MDIACTIVATE
- ON_WM_MOVE
- ON_WM_LBUTTONDOWN
- ON_WM_MBUTTONDOWN
- ON_WM_MENUCHAR
- ON_WM_MBUTTONUP
helpviewer_keywords:
- ON_WM_MENUSELECT [MFC]
- ON_WM_MBUTTONDBLCLK [MFC]
- ON_WM_MOVE [MFC]
- ON_WM_MOUSEACTIVATE [MFC]
- ON_WM_MBUTTONUP [MFC]
- ON_WM_MOUSEMOVE [MFC]
- ON_WM_MENUCHAR [MFC]
- ON_WM_MBUTTONDOWN [MFC]
- ON_WM_MEASUREITEM [MFC]
- ON_WM_MOVING [MFC]
- ON_WM_LBUTTONDOWN [MFC]
- ON_WM_MDIACTIVATE [MFC]
- ON_WM_LBUTTONDBLCLK [MFC]
- ON_WM_LBUTTONUP [MFC]
- WM_ messages
ms.assetid: 96ecaaf1-6d13-4e12-a454-535635967489
ms.openlocfilehash: 2044f8eeb74c75f92f42c6e0199820528f7c10c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218331"
---
# <a name="wm_-message-handlers-l---m"></a>WM_ 메시지 처리기: L - M

왼쪽에 있는 다음 맵 항목은 오른쪽에 있는 함수 프로토타입과 일치합니다.

|맵 항목|함수 프로토타입|
|---------------|------------------------|
|ON_WM_LBUTTONDBLCLK ()|afx_msg void [OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)(UINT, cpoint);|
|ON_WM_LBUTTONDOWN ()|afx_msg void [Onlbuttondown](../../mfc/reference/cwnd-class.md#onlbuttondown)(UINT, cpoint);|
|ON_WM_LBUTTONUP ()|afx_msg void [Onlbuttonup](../../mfc/reference/cwnd-class.md#onlbuttonup)(UINT, cpoint);|
|ON_WM_MBUTTONDBLCLK ()|afx_msg void [OnMButtonDblClk](../../mfc/reference/cwnd-class.md#onmbuttondblclk)(UINT, cpoint);|
|ON_WM_MBUTTONDOWN ()|afx_msg void [Onmbuttondown](../../mfc/reference/cwnd-class.md#onmbuttondown)(UINT, cpoint);|
|ON_WM_MBUTTONUP ()|afx_msg void [Onmbuttonup](../../mfc/reference/cwnd-class.md#onmbuttonup)(UINT, cpoint);|
|ON_WM_MDIACTIVATE ()|afx_msg void [OnMDIActivate](../../mfc/reference/cwnd-class.md#onmdiactivate)(BOOL, cwnd \* , cwnd \* );|
|ON_WM_MEASUREITEM ()|afx_msg void [OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)(LPMEASUREITEMSTRUCT);|
|ON_WM_MENUCHAR ()|afx_msg LONG [Onmenuchar](../../mfc/reference/cwnd-class.md#onmenuchar)(UINT, Uint, CMenu \* );|
|ON_WM_MENUDRAG ()|afx_msg UINT [Onmenudrag](../../mfc/reference/cwnd-class.md#onmenudrag)(Uint, CMenu \* );|
|ON_WM_MENUGETOBJECT ()|afx_msg UINT [Onmenugetobject](../../mfc/reference/cwnd-class.md#onmenugetobject)(MENUGETOBJECTINFO \* );|
|ON_WM_MENURBUTTONUP ()|afx_msg void [Onmenurbuttonup](../../mfc/reference/cwnd-class.md#onmenurbuttonup)(UINT, CMenu \* );|
|ON_WM_MENUSELECT ()|afx_msg void [OnMenuSelect](../../mfc/reference/cwnd-class.md#onmenuselect)(UINT, UINT, HMENU);|
|ON_WM_MOUSEACTIVATE ()|afx_msg int [Onmouseactivate](../../mfc/reference/cwnd-class.md#onmouseactivate)(CWnd \* , uint, uint);|
|ON_WM_MOUSEHOVER ()|afx_msg void [OnMouseHover](../../mfc/reference/cwnd-class.md#onmousehover)(UINT, cpoint);|
|ON_WM_MOUSEHWHEEL ()|afx_msg void [Onmousehwheel](../../mfc/reference/cwnd-class.md#onmousehwheel)(UINT, Short, cpoint);|
|ON_WM_MOUSELEAVE ()|afx_msg void [OnMouseLeave](../../mfc/reference/cwnd-class.md#onmouseleave)();|
|ON_WM_MOUSEMOVE ()|afx_msg void [OnMouseMove](../../mfc/reference/cwnd-class.md#onmousemove)(UINT, cpoint);|
|ON_WM_MOUSEWHEEL ()|afx_msg BOOL [Onmousewheel](../../mfc/reference/cwnd-class.md#onmousewheel)(UINT, Short, cpoint);|
|ON_WM_MOVE ()|afx_msg void [Onmove](../../mfc/reference/cwnd-class.md#onmove)(int, int);|
|ON_WM_MOVING ()|afx_msg void [Onmoving](../../mfc/reference/cwnd-class.md#onmoving)(UINT, LPRECT);|

## <a name="see-also"></a>참고 항목

[메시지 맵](../../mfc/reference/message-maps-mfc.md)<br/>
[WM_ 메시지에 대 한 처리기](../../mfc/reference/handlers-for-wm-messages.md)
