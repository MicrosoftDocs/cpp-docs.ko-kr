---
description: '자세히 알아보기: Month Calendar 컨트롤에서 알림 메시지 처리'
title: MonthCalendar 컨트롤에서 알림 메시지 처리
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
ms.openlocfilehash: 4c527bd2c950277d36164ec14c7c714d82d2c812
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154788"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>MonthCalendar 컨트롤에서 알림 메시지 처리

사용자가 monthcalendar 컨트롤 (날짜 및/또는 다른 월을 선택 하 여 선택)과 상호 작용 하는 경우 컨트롤 ( `CMonthCalCtrl` )은 일반적으로 뷰 또는 대화 개체의 부모 창에 알림 메시지를 보냅니다. 이에 대한 응답으로 작업을 수행하려는 경우 이러한 메시지를 처리합니다. 예를 들어 사용자가 볼 새 월을 선택 하는 경우 강조 표시 해야 하는 날짜 집합을 제공할 수 있습니다.

[클래스 마법사](reference/mfc-class-wizard.md) 를 사용 하 여 구현 하려는 메시지의 부모 클래스에 알림 처리기를 추가 합니다.

다음 목록에서는 month calendar 컨트롤에서 전송 되는 다양 한 알림에 대해 설명 합니다.

- MCN_GETDAYSTATE 굵게 표시 되어야 하는 날짜에 대 한 정보를 요청 합니다. 이 알림을 처리 하는 방법에 대 한 자세한 내용은 [Month Calendar 컨트롤의 일 상태 설정](../mfc/setting-the-day-state-of-a-month-calendar-control.md)을 참조 하십시오.

- MCN_SELCHANGE는 선택한 날짜 또는 날짜 범위가 변경 되었음을 부모에 게 알립니다.

- MCN_SELECT는 명시적 날짜 선택이 수행 되었음을 부모에 게 알립니다.

## <a name="see-also"></a>참고 항목

[CMonthCalCtrl 사용](../mfc/using-cmonthcalctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
