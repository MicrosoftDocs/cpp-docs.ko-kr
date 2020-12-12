---
description: '자세한 정보: 도구 설명을 만드는 방법'
title: 도구 설명을 만드는 방법
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
ms.openlocfilehash: fc710f569e78f9698cdc924a071489c03b2975b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203109"
---
# <a name="methods-of-creating-tool-tips"></a>도구 설명을 만드는 방법

MFC는 [CWnd](reference/cwnd-class.md), [CToolBarCtrl](reference/ctoolbarctrl-class.md), [CToolTipCtrl](reference/ctooltipctrl-class.md) 및 [CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md)도구 설명 컨트롤을 만들고 관리 하기 위한 세 가지 클래스를 제공 합니다. 이러한 클래스의 도구 설명 멤버 함수는 Windows 공용 컨트롤 API를 래핑합니다. 클래스 `CToolBarCtrl` 및 클래스 `CToolTipCtrl` 는 클래스에서 파생 됩니다 `CWnd` .

`CWnd` 은 (는) 도구 설명을 만들고 관리 하는 데 필요한 네 가지 멤버 함수 [Enabletooltips](reference/cwnd-class.md#enabletooltips), [canceltooltips](reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](reference/cwnd-class.md#filtertooltipmessage)및 [OnToolHitTest](reference/cwnd-class.md#ontoolhittest)를 제공 합니다. 도구 설명을 구현 하는 방법에 대 한 자세한 내용은 이러한 개별 멤버 함수를 참조 하세요.

를 사용 하 여 도구 모음을 만드는 경우 `CToolBarCtrl` 다음 멤버 함수를 사용 하 여 해당 도구 모음에 대 한 도구 설명을 직접 구현할 수 있습니다. [Gettooltips](reference/ctoolbarctrl-class.md#gettooltips) 및 [settooltips](reference/ctoolbarctrl-class.md#settooltips) 도구 설명을 구현 하는 방법에 대 한 자세한 내용은 이러한 개별 멤버 함수 및 [도구 설명 알림 처리](handling-tool-tip-notifications.md) 를 참조 하세요.

`CToolTipCtrl`클래스는 Windows의 공용 도구 설명 컨트롤의 기능을 제공 합니다. 단일 도구 설명 컨트롤은 둘 이상의 도구에 대 한 정보를 제공할 수 있습니다. 도구는 자식 창이 나 컨트롤과 같은 창 또는 창의 클라이언트 영역에 있는 응용 프로그램 정의 사각형 영역 중 하나입니다. [CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md) 클래스는에서 파생 `CToolTipCtrl` 되며 추가 비주얼 스타일 및 기능을 제공 합니다.

## <a name="see-also"></a>참고 항목

[CToolTipCtrl 사용](using-ctooltipctrl.md)<br/>
[컨트롤](controls-mfc.md)
