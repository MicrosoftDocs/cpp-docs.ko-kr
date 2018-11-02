---
title: 도구 설명을 만드는 방법
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
ms.openlocfilehash: 80c826b3c9a4f9e24ebd201eaa9d775f9ad9f8cf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663816"
---
# <a name="methods-of-creating-tool-tips"></a>도구 설명을 만드는 방법

MFC는 세 가지 클래스를 만들고 관리 도구 설명 컨트롤을 제공 합니다. [CWnd](../mfc/reference/cwnd-class.md), [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)합니다 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) 및 [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md). 이러한 클래스의 도구 팁 멤버 함수는 Windows 공용 컨트롤을 API를 래핑합니다. 클래스 `CToolBarCtrl` 및 클래스 `CToolTipCtrl` 클래스에서 파생 된 `CWnd`합니다.

`CWnd` 4 개의 멤버 함수 만들기 및 관리 도구를 제공 합니다. [EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips), [CancelToolTips](../mfc/reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](../mfc/reference/cwnd-class.md#filtertooltipmessage), 및 [OnToolHitTest ](../mfc/reference/cwnd-class.md#ontoolhittest). 도구 팁을 구현 하는 방법에 대 한 자세한 내용은 이러한 개별 멤버 함수를 참조 하세요.

사용 하 여 도구 모음을 만드는 경우 `CToolBarCtrl`, 다음 구성원 함수를 사용 하 여 직접 해당 도구 모음에 대 한 도구 팁을 구현할 수 있습니다: [GetToolTips](../mfc/reference/ctoolbarctrl-class.md#gettooltips) 하 고 [SetToolTips](../mfc/reference/ctoolbarctrl-class.md#settooltips)합니다. 이러한 개별 멤버 함수를 참조 하 고 [도구 팁 알림 처리](../mfc/handling-tool-tip-notifications.md) 도구 팁을 구현 하는 방법에 대 한 자세한 내용은 합니다.

`CToolTipCtrl` 클래스 Windows 일반적인 도구 설명 컨트롤의 기능을 제공 합니다. 단일 도구 설명 컨트롤 둘 이상의 도구에 대 한 정보를 제공할 수 있습니다. 도구는 창의 클라이언트 영역 내에서 응용 프로그램 정의 된 사각형 영역을 자식 창 또는 컨트롤 등을 창 중 하나입니다. [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md) 클래스에서 파생 되며 `CToolTipCtrl` 추가 비주얼 스타일 및 기능을 제공 합니다.

## <a name="see-also"></a>참고 항목

[CToolTipCtrl 사용](../mfc/using-ctooltipctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)

