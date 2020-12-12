---
description: '다음에 대 한 자세한 정보: WM_ 메시지 처리기: N-O'
title: 'WM_ 메시지 처리기: N - O'
ms.date: 11/04/2016
f1_keywords:
- ON_WM_NCHITTEST
- ON_WM_NCLBUTTONDOWN
- ON_WM_NCCALCSIZE
- ON_WM_NCLBUTTONUP
- ON_WM_NCPAINT
- ON_WM_NCMBUTTONUP
- ON_WM_NCCREATE
- ON_WM_NCACTIVATE
- ON_WM_NCMOUSEMOVE
- ON_WM_NCRBUTTONDBLCLK
- ON_WM_NCLBUTTONDBLCLK
- ON_WM_NCDESTROY
- ON_WM_NCMBUTTONDBLCLK
- ON_WM_NCRBUTTONDOWN
- ON_WM_NCRBUTTONUP
- ON_WM_NCMBUTTONDOWN
helpviewer_keywords:
- ON_WM_NCCALCSIZE [MFC]
- ON_WM_NCMBUTTONDOWN [MFC]
- ON_WM_NCRBUTTONDBLCLK [MFC]
- ON_WM_NCMBUTTONDBLCLK [MFC]
- ON_WM_NCLBUTTONDBLCLK [MFC]
- ON_WM_NCDESTROY [MFC]
- ON_WM_NCRBUTTONDOWN [MFC]
- ON_WM_NCLBUTTONDOWN [MFC]
- ON_WM_NCCREATE [MFC]
- ON_WM_NCRBUTTONUP [MFC]
- ON_WM_NCLBUTTONUP [MFC]
- ON_WM_NCPAINT [MFC]
- ON_WM_NCACTIVATE [MFC]
- ON_WM_NCHITTEST [MFC]
- ON_WM_NCMOUSEMOVE [MFC]
- ON_WM_NCMBUTTONUP [MFC]
- WM_ messages
ms.assetid: 4efd1cda-b642-4e8b-89e8-73255fa70d77
ms.openlocfilehash: 2f70bd0d019b4cdc9557c87c3ae0bb51e330723f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218318"
---
# <a name="wm_-message-handlers-n---o"></a>WM_ 메시지 처리기: N - O

왼쪽에 있는 다음 맵 항목은 오른쪽에 있는 함수 프로토타입과 일치합니다.

|맵 항목|함수 프로토타입|
|---------------|------------------------|
|ON_WM_NCACTIVATE ()|afx_msg BOOL [OnNcActivate](../../mfc/reference/cwnd-class.md#onncactivate)(bool);|
|ON_WM_NCCALCSIZE ()|afx_msg void [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)(BOOL, NCCALCSIZE_PARAMS FAR *);|
|ON_WM_NCCREATE ()|afx_msg BOOL [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)(lpcreatestruct);|
|ON_WM_NCDESTROY ()|afx_msg void [OnNcDestroy](../../mfc/reference/cwnd-class.md#onncdestroy)();|
|ON_WM_NCHITTEST ()|afx_msg LRESULT [Onnchittest](../../mfc/reference/cwnd-class.md#onnchittest)(cpoint);|
|ON_WM_NCLBUTTONDBLCLK ()|afx_msg void [OnNcLButtonDblClk](../../mfc/reference/cwnd-class.md#onnclbuttondblclk)(UINT, cpoint);|
|ON_WM_NCLBUTTONDOWN ()|afx_msg void [Onnclbuttondown](../../mfc/reference/cwnd-class.md#onnclbuttondown)(UINT, cpoint);|
|ON_WM_NCLBUTTONUP ()|afx_msg void [Onnclbuttonup](../../mfc/reference/cwnd-class.md#onnclbuttonup)(UINT, cpoint);|
|ON_WM_NCMBUTTONDBLCLK ()|afx_msg void [OnNcMButtonDblClk](../../mfc/reference/cwnd-class.md#onncmbuttondblclk)(UINT, cpoint);|
|ON_WM_NCMBUTTONDOWN ()|afx_msg void [Onncmbuttondown](../../mfc/reference/cwnd-class.md#onncmbuttondown)(UINT, cpoint);|
|ON_WM_NCMBUTTONUP ()|afx_msg void [Onncmbuttonup](../../mfc/reference/cwnd-class.md#onncmbuttonup)(UINT, cpoint);|
|ON_WM_NCMOUSEHOVER ()|afx_msg void [Onncmousehover](../../mfc/reference/cwnd-class.md#onncmousehover)(UINT, cpoint);|
|ON_WM_NCMOUSELEAVE ()|afx_msg void [OnNcMouseLeave](../../mfc/reference/cwnd-class.md#onncmouseleave)();|
|ON_WM_NCMOUSEMOVE ()|afx_msg void [Onncmousemove](../../mfc/reference/cwnd-class.md#onncmousemove)(UINT, cpoint);|
|ON_WM_NCPAINT ()|afx_msg void [OnNcPaint](../../mfc/reference/cwnd-class.md#onncpaint)();|
|ON_WM_NCRBUTTONDBLCLK ()|afx_msg void [OnNcRButtonDblClk](../../mfc/reference/cwnd-class.md#onncrbuttondblclk)(UINT, cpoint);|
|ON_WM_NCRBUTTONDOWN ()|afx_msg void [Onncrbuttondown](../../mfc/reference/cwnd-class.md#onncrbuttondown)(UINT, cpoint);|
|ON_WM_NCRBUTTONUP ()|afx_msg void [Onncrbuttonup](../../mfc/reference/cwnd-class.md#onncrbuttonup)(UINT, cpoint);|
|ON_WM_NCXBUTTONDBLCLK ()|void [OnNcXButtonDblClk](../../mfc/reference/cwnd-class.md#onncxbuttondblclk)(SHORT, UINT, cpoint);|
|ON_WM_NCXBUTTONDOWN ()|afx_msg void [OnNcXButtonDown](../../mfc/reference/cwnd-class.md#onncxbuttondown)(SHORT, UINT, cpoint);|
|ON_WM_NCXBUTTONUP ()|afx_msg void [OnNcXButtonUp](../../mfc/reference/cwnd-class.md#onncxbuttonup)(SHORT, UINT, cpoint);|
|ON_WM_NEXTMENU ()|afx_msg void [OnNextMenu](../../mfc/reference/cwnd-class.md#onnextmenu)(UINT, LPMDINEXTMENU);|
|ON_WM_NOTIFYFORMAT ()|afx_msg UINT [OnNotifyFormat](../../mfc/reference/cwnd-class.md#onnotifyformat)(CWnd *, UINT);|

## <a name="see-also"></a>참고 항목

[메시지 맵](../../mfc/reference/message-maps-mfc.md)<br/>
[WM_ 메시지에 대 한 처리기](../../mfc/reference/handlers-for-wm-messages.md)
