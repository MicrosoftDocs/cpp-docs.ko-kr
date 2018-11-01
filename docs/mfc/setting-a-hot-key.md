---
title: 바로 가기 키 설정
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: a5dc885767137a4e53d1ea0d066944d5f276c38c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508799"
---
# <a name="setting-a-hot-key"></a>바로 가기 키 설정

응용 프로그램 바로 가기 키를 제공 하는 정보를 사용할 수 있습니다 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md))의 두 가지 방법으로 제어 합니다.

- 전송 하 여 비 자식 창을 활성화 하기 위한 전역 바로 가기 키를 설정 된 [WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) 활성화할 창에 메시지.

- Windows 함수를 호출 하 여 스레드 관련 바로 가기 키를 설정 [RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309)합니다.

## <a name="see-also"></a>참고 항목

[CHotKeyCtrl 사용](../mfc/using-chotkeyctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)

