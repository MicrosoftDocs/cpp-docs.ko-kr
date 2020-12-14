---
description: '다음에 대 한 자세한 정보: 바로 가기 키 Thread-Specific'
title: 스레드 관련 바로 가기 키
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 352d39b801d7e6dcecfbf27d841d6977d3666138
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216121"
---
# <a name="thread-specific-hot-keys"></a>스레드 관련 바로 가기 키

응용 프로그램은 Windows 함수를 사용 하 여 스레드 관련 바로 가기 키 ([Chotkeyctrl](../mfc/reference/chotkeyctrl-class.md))를 설정 합니다 `RegisterHotKey` . 사용자가 스레드별 바로 가기 키를 누르면 Windows에서 특정 스레드의 메시지 큐의 시작 부분에 [WM_HOTKEY](/windows/win32/inputdev/wm-hotkey) 메시지를 게시 합니다. WM_HOTKEY 메시지는 누른 특정 바로 가기 키의 가상 키 코드, 이동 상태 및 사용자 정의 ID를 포함 합니다. 표준 가상 키 코드의 목록은 Winuser.h를 참조 하세요. 이 메서드에 대 한 자세한 내용은 [Registerhotkey](/windows/win32/api/winuser/nf-winuser-registerhotkey)를 참조 하세요.

호출에 사용 된 이동 상태 플래그는 `RegisterHotKey` [Gethotkey](../mfc/reference/chotkeyctrl-class.md#gethotkey) 멤버 함수에서 반환 하는 것과 같지 않습니다 .를 호출 하기 전에 이러한 플래그를 변환 해야 `RegisterHotKey` 합니다.

## <a name="see-also"></a>참고 항목

[CHotKeyCtrl 사용](../mfc/using-chotkeyctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
