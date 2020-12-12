---
description: '자세히 알아보기: CFrameWnd에서 파생 되지 않은 Windows의 도구 설명'
title: CFrameWnd에서 파생되지 않은 창의 도구 설명
ms.date: 11/04/2016
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
ms.openlocfilehash: 1d5d2ba744800424a9dce325f9d4341956bc22ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264429"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>CFrameWnd에서 파생되지 않은 창의 도구 설명

이 문서 제품군에서는 [CFrameWnd](../mfc/reference/cframewnd-class.md)에서 파생 되지 않은 창에 포함 된 컨트롤에 대 한 도구 설명을 사용 하도록 설정 하는 방법을 설명 합니다. 도구 [모음 도구 설명](../mfc/toolbar-tool-tips.md) 에서는의 컨트롤에 대 한 도구 설명 정보를 제공 합니다 `CFrameWnd` .

이 문서 제품군에서 다루는 항목은 다음과 같습니다.

- [도구 설명 사용](../mfc/enabling-tool-tips.md)

- [도구 설명에 대 한 TTN_NEEDTEXT 알림 처리](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [TOOLTIPTEXT 구조체](../mfc/tooltiptext-structure.md)

도구 설명은에서 파생 된 부모 창에 포함 된 단추 및 기타 컨트롤에 대해 자동으로 표시 됩니다 `CFrameWnd` . 에는 `CFrameWnd` 컨트롤과 연결 된 도구 설명 컨트롤의 알림을 **TTN_NEEDTEXT** 처리 하는 [TTN_GETDISPINFO](/windows/win32/Controls/ttn-getdispinfo) 알림에 대 한 기본 처리기가 있기 때문입니다.

그러나  `CFrameWnd` 대화 상자 또는 폼 뷰의 컨트롤과 같이가 아닌 창의 컨트롤과 연결 된 도구 설명 컨트롤에서 TTN_NEEDTEXT 알림을 보내는 경우에는이 기본 처리기가 호출 되지 않습니다. 따라서 자식 컨트롤에 대 한 도구 설명을 표시 하기 위해 **TTN_NEEDTEXT** 알림 메시지에 대 한 처리기 함수를 제공 해야 합니다.

[CWnd:: Enabletoololtool](../mfc/reference/cwnd-class.md#enabletooltips) 에 의해 제공 되는 windows 용 기본 도구 설명에는 연결 된 텍스트가 없습니다. 도구 설명에 표시할 텍스트를 검색 하기 위해 도구 설명 창이 표시 되기 직전에 **TTN_NEEDTEXT** 알림이 도구 설명 컨트롤의 부모 창으로 전송 됩니다. **TOOLTIPTEXT** 구조의 *pszText* 멤버에 일부 값을 할당 하기 위한이 메시지에 대 한 처리기가 없는 경우 도구 설명에 대 한 텍스트가 표시 되지 않습니다.

## <a name="see-also"></a>참고 항목

[도구 설명](../mfc/tool-tips.md)
