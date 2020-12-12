---
description: 'WM_ 메시지: S에 대해 자세히 알아보세요.'
title: 'WM_ 메시지: S'
ms.date: 11/04/2016
f1_keywords:
- ON_WM_SYSDEADCHAR
- ON_WM_SYSKEYDOWN
- ON_WM_STYLECHANGING
- ON_WM_STYLECHANGED
- ON_WM_SPOOLERSTATUS
- ON_WM_SYSCHAR
- ON_WM_SETFOCUS
- ON_WM_SIZE
- ON_WM_SIZING
- ON_WM_SETCURSOR
- ON_WM_SYSCOMMAND
- ON_WM_SETTINGCHANGE
- ON_WM_SHOWWINDOW
- ON_WM_SYSKEYUP
- ON_WM_SIZECLIPBOARD
- ON_WM_SYSCOLORCHANGE
helpviewer_keywords:
- ON_WM_SIZE [MFC]
- ON_WM_SETFOCUS [MFC]
- ON_WM_SIZING [MFC]
- ON_WM_SYSCHAR [MFC]
- ON_WM_SETTINGCHANGE [MFC]
- ON_WM_SYSDEADCHAR [MFC]
- ON_WM_SHOWWINDOW [MFC]
- ON_WM_STYLECHANGING [MFC]
- ON_WM_SYSCOMMAND [MFC]
- ON_WM_STYLECHANGED [MFC]
- ON_WM_SPOOLERSTATUS [MFC]
- ON_WM_SYSCOLORCHANGE [MFC]
- ON_WM_SETCURSOR [MFC]
- ON_WM_SIZECLIPBOARD [MFC]
- ON_WM_SYSKEYUP [MFC]
- ON_WM_SYSKEYDOWN [MFC]
- WM_ messages
ms.assetid: 4b9aec79-a98f-4aa0-a3d9-110941b6dcbc
ms.openlocfilehash: 6fc1f193569d912e438b19646cd1bb4573855346
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218292"
---
# <a name="wm_-messages-s"></a>WM_ 메시지: S

함수 프로토타입에 해당 하는 맵 항목은 다음과 같습니다.

|맵 항목|함수 프로토타입|
|---------------|------------------------|
|ON_WM_SETCURSOR ()|afx_msg BOOL [Onsetcursor](../../mfc/reference/cwnd-class.md#onsetcursor)(CWnd *, UINT, uint);|
|ON_WM_SETFOCUS ()|afx_msg void [Onsetfocus](../../mfc/reference/cwnd-class.md#onsetfocus)(CWnd *);|
|ON_WM_SETTINGCHANGE ()|afx_msg void [Onsettingchange](../../mfc/reference/cwnd-class.md#onsettingchange)(UINT uflags, LPCTSTR lpszSection);|
|ON_WM_SHOWWINDOW ()|afx_msg void [OnShowWindow](../../mfc/reference/cwnd-class.md#onshowwindow)(BOOL, UINT);|
|ON_WM_SIZE ()|afx_msg void [Onsize](../../mfc/reference/cwnd-class.md#onsize)(UINT, int, int);|
|ON_WM_SIZECLIPBOARD ()|afx_msg void [OnSizeClipboard](../../mfc/reference/cwnd-class.md#onsizeclipboard)(CWnd *, HANDLE);|
|ON_WM_SIZING ()|afx_msg void [Onsizing](../../mfc/reference/cwnd-class.md#onsizing)(UINT, LPRECT);|
|ON_WM_SPOOLERSTATUS ()|afx_msg void [OnSpoolerStatus](../../mfc/reference/cwnd-class.md#onspoolerstatus)(UINT, uint);|
|ON_WM_STYLECHANGED ()|afx_msg void [OnStyleChanged](../../mfc/reference/cwnd-class.md#onstylechanged)(INT, LPSTYLESTRUCT);|
|ON_WM_STYLECHANGING ()|afx_msg void [OnStyleChanging](../../mfc/reference/cwnd-class.md#onstylechanging)(INT, LPSTYLESTRUCT);|
|ON_WM_SYSCHAR ()|afx_msg void [OnSysChar](../../mfc/reference/cwnd-class.md#onsyschar)(UINT, UINT, uint);|
|ON_WM_SYSCOLORCHANGE ()|afx_msg void [Onsyscolorchange](../../mfc/reference/cwnd-class.md#onsyscolorchange)();|
|ON_WM_SYSCOMMAND ()|afx_msg void [Onsyscommand](../../mfc/reference/cwnd-class.md#onsyscommand)(UINT, LONG);|
|ON_WM_SYSDEADCHAR ()|afx_msg void [OnSysDeadChar](../../mfc/reference/cwnd-class.md#onsysdeadchar)(UINT, UINT, uint);|
|ON_WM_SYSKEYDOWN ()|afx_msg void [Onsyskeydown](../../mfc/reference/cwnd-class.md#onsyskeydown)(UINT, UINT, uint);|
|ON_WM_SYSKEYUP ()|afx_msg void [Onsyskeyup](../../mfc/reference/cwnd-class.md#onsyskeyup)(UINT, UINT, uint);|

## <a name="see-also"></a>참고 항목

[메시지 맵](../../mfc/reference/message-maps-mfc.md)<br/>
[WM_ 메시지에 대 한 처리기](../../mfc/reference/handlers-for-wm-messages.md)
