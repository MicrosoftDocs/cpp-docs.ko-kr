---
description: '자세한 정보: 날짜 및 시간 선택 컨트롤에서 알림 메시지 처리'
title: 날짜 및 시간 선택 컨트롤의 알림 메시지 처리
ms.date: 11/04/2016
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
ms.openlocfilehash: 07ac9c4c8ba58c833591409b1f5ab405cd05ebc3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154827"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>날짜 및 시간 선택 컨트롤의 알림 메시지 처리

사용자가 날짜 및 시간 선택 컨트롤과 상호 작용할 때 컨트롤 ()은 `CDateTimeCtrl` 일반적으로 뷰 또는 대화 개체의 부모 창에 알림 메시지를 보냅니다. 이에 대한 응답으로 작업을 수행하려는 경우 이러한 메시지를 처리합니다. 예를 들어 사용자가 날짜 및 시간 선택을 열어 포함 된 month calendar 컨트롤을 표시 하면 DTN_DROPDOWN 알림이 전송 됩니다.

[클래스 마법사](reference/mfc-class-wizard.md) 를 사용 하 여 구현 하려는 메시지의 부모 클래스에 알림 처리기를 추가 합니다.

다음 목록에서는 날짜 및 시간 선택 컨트롤에 의해 전송 되는 다양 한 알림에 대해 설명 합니다.

- DTN_DROPDOWN는 포함 된 monthcalendar 컨트롤의 표시를 부모에 게 알립니다. 이 알림은 DTS_UPDOWN 스타일이 설정 되지 않은 경우에만 전송 됩니다. 이 알림에 대 한 자세한 내용은 포함 된 [Monthcalendar 컨트롤 액세스](accessing-the-embedded-month-calendar-control.md)를 참조 하세요.

- DTN_CLOSEUP는 포함 된 month calendar 컨트롤을 닫을지를 부모에 게 알립니다. 이 알림은 DTS_UPDOWN 스타일이 설정 되지 않은 경우에만 전송 됩니다.

- DTN_DATETIMECHANGE 컨트롤에서 변경이 발생 했음을 부모에 게 알립니다.

- DTN_FORMAT은 콜백 필드에 텍스트가 표시 되어야 함을 부모에 게 알립니다. 이 알림 및 콜백 필드에 대 한 자세한 내용은 [날짜 및 시간 선택 컨트롤에서 콜백 필드 사용](using-callback-fields-in-a-date-and-time-picker-control.md)을 참조 하세요.

- DTN_FORMATQUERY는 부모를 요청 하 여 콜백 필드에 표시 될 문자열의 최대 허용 크기를 제공 합니다. 이 알림을 처리 하면 컨트롤이 항상 출력을 제대로 표시 하 여 컨트롤의 표시 내에서 깜빡임을 줄일 수 있습니다. 이 알림에 대 한 자세한 내용은 [날짜 및 시간 선택 컨트롤에서 콜백 필드 사용](using-callback-fields-in-a-date-and-time-picker-control.md)을 참조 하세요.

- DTN_USERSTRING는 사용자가 날짜 및 시간 선택 컨트롤의 내용 편집을 완료 했음을 부모에 게 알립니다. 이 알림은 DTS_APPCANPARSE 스타일이 설정 된 경우에만 전송 됩니다.

- DTN_WMKEYDOWN 사용자가 콜백 필드를 입력 하면 부모에 게 알립니다. 날짜 및 시간 선택 컨트롤에서 비 콜백 필드에 대해 지원 되는 것과 동일한 키보드 응답을 에뮬레이트 하려면이 알림을 처리 합니다. 이 알림에 대 한 자세한 내용은 Windows SDK에서 [DTP 컨트롤의 콜백 필드 지원](/windows/win32/Controls/date-and-time-picker-controls) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CDateTimeCtrl 사용](using-cdatetimectrl.md)<br/>
[컨트롤](controls-mfc.md)
