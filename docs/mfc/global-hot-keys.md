---
title: 전역 바로 가기 키
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: 59918648ea24fd1e2a86ca786de3081cd6cca2df
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508560"
---
# <a name="global-hot-keys"></a>전역 바로 가기 키

전역 바로 가기 키는 특정 비 자식 창에 연결 됩니다. 이를 통해 사용자는 시스템의 모든 부분에서 창을 활성화할 수 있습니다. 응용 프로그램은 해당 창에 [WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey) 메시지를 전송 하 여 특정 창에 대 한 전역 바로 키를 설정 합니다. 예를 들어가 `m_HotKeyCtrl` [chotkeyctrl](../mfc/reference/chotkeyctrl-class.md) 개체이 고 `pMainWnd` 바로 가기 키를 누를 때 활성화 될 창에 대 한 포인터인 경우 다음 코드를 사용 하 여 컨트롤에 지정 된 바로 가기 키를가 가리키는 창에 연결할 수 있습니다. `pMainWnd`.

[!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]

사용자가 전역 바로 가기 키를 누를 때마다 지정 된 창에서 **SC_HOTKEY** 를 명령 유형으로 지정 하는 [WM_SYSCOMMAND](/windows/win32/menurc/wm-syscommand) 메시지를 받습니다. 이 메시지는 또한이 메시지를 수신 하는 창을 활성화 합니다. 이 메시지에는 누른 정확한 키에 대 한 정보가 포함 되어 있지 않기 때문에이 방법을 사용 하면 동일한 창에 연결 될 수 있는 다른 핫 키를 구분할 수 없습니다. **WM_SETHOTKEY** 을 보낸 응용 프로그램이 종료 될 때까지 핫 키는 유효한 상태로 유지 됩니다.

## <a name="see-also"></a>참고자료

[CHotKeyCtrl 사용](../mfc/using-chotkeyctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
