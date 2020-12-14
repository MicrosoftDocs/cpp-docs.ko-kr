---
description: '에 대 한 자세한 정보: 슬라이더 알림 메시지'
title: 슬라이더 알림 메시지
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], notifications
- slider controls [MFC], notification messages
- messages, notification
- notifications [MFC], CSliderCtrl
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
ms.openlocfilehash: fab8d515e71fd2ca8fd390a41b6d1bf68442c24c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216888"
---
# <a name="slider-notification-messages"></a>슬라이더 알림 메시지

슬라이더 컨트롤은 슬라이더 컨트롤의 방향에 따라 부모 WM_HSCROLL 또는 WM_VSCROLL 메시지를 전송 하 여 사용자 동작의 부모 창에 알립니다. 이러한 메시지를 처리 하려면 WM_HSCROLL에 대 한 처리기를 추가 하 고 부모 창에 메시지 WM_VSCROLL 합니다. [Onhscroll](../mfc/reference/cwnd-class.md#onhscroll) 및 [onhscroll](../mfc/reference/cwnd-class.md#onvscroll) 멤버 함수에는 알림 코드, 슬라이더의 위치 및 [CSliderCtrl](../mfc/reference/csliderctrl-class.md) 개체에 대 한 포인터가 전달 됩니다. 포인터는 `CScrollBar *` 개체를 가리키는 경우에도 형식입니다 `CSliderCtrl` . 슬라이더 컨트롤을 조작 해야 하는 경우이 포인터를 형식 캐스팅 할 수 있습니다.

슬라이더 컨트롤은 스크롤 막대 알림 코드를 사용 하는 대신 다른 알림 코드 집합을 보냅니다. 슬라이더 컨트롤은 사용자가 키보드를 사용 하 여 슬라이더 컨트롤과 상호 작용 하는 경우에만 TB_BOTTOM, TB_LINEDOWN, TB_LINEUP 및 TB_TOP 알림 코드를 보냅니다. TB_THUMBPOSITION 및 TB_THUMBTRACK 알림 메시지는 사용자가 마우스를 사용 하는 경우에만 전송 됩니다. 두 경우 모두 TB_ENDTRACK, TB_PAGEDOWN 및 TB_PAGEUP 알림 코드가 전송 됩니다.

다음 표에서는 알림을 보내는 슬라이더 컨트롤 알림 메시지와 이벤트 (가상 키 코드 또는 마우스 이벤트)를 보여 줍니다. 표준 가상 키 코드 목록은 Winuser.h를 참조 하십시오.

|알림 메시지|알림을 보내도록 유발 하는 이벤트|
|--------------------------|-------------------------------------------|
|TB_BOTTOM|VK_END|
|TB_ENDTRACK|WM_KEYUP (사용자가 관련 가상 키 코드를 보낸 키를 해제 했습니다.)|
|TB_LINEDOWN|VK_RIGHT 또는 VK_DOWN|
|TB_LINEUP|VK_LEFT 또는 VK_UP|
|TB_PAGEDOWN|VK_NEXT (사용자가 아래 채널 또는 슬라이더 오른쪽으로 클릭)|
|TB_PAGEUP|VK_PRIOR (사용자가 슬라이더의 위쪽 이나 왼쪽에 있는 채널을 클릭 함)|
|TB_THUMBPOSITION|TB_THUMBTRACK 알림 메시지를 다음에 WM_LBUTTONUP|
|TB_THUMBTRACK|슬라이더 이동 (사용자가 슬라이더를 끌고)|
|TB_TOP|VK_HOME|

## <a name="see-also"></a>참고 항목

[CSliderCtrl 사용](../mfc/using-csliderctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
