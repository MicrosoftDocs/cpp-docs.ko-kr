---
description: '자세한 정보: 도구 설명 컨트롤 조작'
title: 도구 설명 컨트롤 조작
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
ms.openlocfilehash: f04a2a9fe7d9b32d4b0fab1c6fea0d82f48cbf1a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281069"
---
# <a name="manipulating-the-tool-tip-control"></a>도구 설명 컨트롤 조작

클래스는 `CToolTipCtrl` `CToolTipCtrl` 개체와 도구 설명 창의 다양 한 특성을 제어 하는 멤버 함수 그룹을 제공 합니다.

[Getdelaytime](reference/ctooltipctrl-class.md#getdelaytime) 및 [setdelaytime](reference/ctooltipctrl-class.md#setdelaytime)에 대 한 호출을 사용 하 여 도구 설명 창의 초기, 팝업 및 검색 기간을 설정 하 고 검색할 수 있습니다.

다음 함수를 사용 하 여 도구 설명 창의 모양을 변경 합니다.

- [Getmargin](reference/ctooltipctrl-class.md#getmargin) 및 [setmargin](reference/ctooltipctrl-class.md#setmargin) 은 도구 설명 테두리와 도구 설명 텍스트 사이의 너비를 검색 하 고 설정 합니다.

- [GetMaxTipWidth](reference/ctooltipctrl-class.md#getmaxtipwidth) 및 [SetMaxTipWidth](reference/ctooltipctrl-class.md#setmaxtipwidth) 는 도구 설명 창의 최대 너비를 검색 하 고 설정 합니다.

- [Gettipbkcolor](reference/ctooltipctrl-class.md#gettipbkcolor) 및 [settipbkcolor](reference/ctooltipctrl-class.md#settipbkcolor) 는 도구 설명 창의 배경색을 검색 하 고 설정 합니다.

- [GetTipTextColor](reference/ctooltipctrl-class.md#gettiptextcolor) 및 [SetTipTextColor](reference/ctooltipctrl-class.md#settiptextcolor) 는 도구 설명 창의 텍스트 색을 검색 하 고 설정 합니다.

도구 설명 컨트롤에 WM_LBUTTONXXX 메시지와 같은 중요 한 메시지에 대 한 알림이 표시 되도록 하려면 메시지를 도구 설명 컨트롤에 릴레이 해야 합니다. 이 릴레이의 가장 좋은 방법은 소유자 창의 함수에서 [CToolTipCtrl:: RelayEvent](reference/ctooltipctrl-class.md#relayevent)를 호출 하는 것입니다 `PreTranslateMessage` . 다음 예제에서는 도구 설명 컨트롤이 호출 된 것으로 가정 하 여 가능한 메서드를 보여 줍니다 `m_ToolTip` .

[!code-cpp[NVC_MFCControlLadenDialog#41](codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]

도구 설명 창을 즉시 제거 하려면 [Pop](reference/ctooltipctrl-class.md#pop) 멤버 함수를 호출 합니다.

## <a name="see-also"></a>참고 항목

[CToolTipCtrl 사용](using-ctooltipctrl.md)<br/>
[컨트롤](controls-mfc.md)
