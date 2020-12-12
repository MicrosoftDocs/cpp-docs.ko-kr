---
description: '자세히 알아보기: Month Calendar 컨트롤의 일 상태 설정'
title: MonthCalendar 컨트롤의 일 상태 설정
ms.date: 11/04/2016
f1_keywords:
- MCN_GETDAYSTATE
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
ms.openlocfilehash: e7fc06516877c54aadaef715c33abd128bbd6994
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217213"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>MonthCalendar 컨트롤의 일 상태 설정

Month calendar 컨트롤의 특성 중 하나는 해당 월의 각 날짜에 대 한 정보를 컨트롤의 일 상태 라고 하는 정보를 저장 하는 기능입니다. 이 정보는 현재 표시 된 달의 특정 날짜를 강조 하는 데 사용 됩니다.

> [!NOTE]
> `CMonthCalCtrl`일 상태 정보를 표시 하려면 개체에 MCS_DAYSTATE 스타일이 있어야 합니다.

일 상태 정보는 32 비트 데이터 형식인 **Monthdaystate** 로 표시 됩니다. **Monthdaystate** 비트 필드의 각 비트 (1-31)는 한 달의 일 상태를 나타냅니다. 비트가 켜져 있으면 해당 날짜가 굵게 표시 됩니다. 그렇지 않으면 강조 표시 되지 않고 표시 됩니다.

Month calendar 컨트롤의 일 상태를 설정 하는 방법에는 [Cmonthcalctrl:: SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) 에 대 한 호출을 사용 하거나 MCN_GETDAYSTATE 알림 메시지를 처리 하는 두 가지 방법이 있습니다.

## <a name="handling-the-mcn_getdaystate-notification-message"></a>MCN_GETDAYSTATE 알림 메시지 처리

표시 되는 월의 일 수를 표시 하는 방법을 결정 하기 위해 컨트롤에서 MCN_GETDAYSTATE 메시지를 보냅니다.

> [!NOTE]
> 이 컨트롤은 표시 된 달에 대해 이전 및 다음 달을 캐시 하므로 새 월을 선택할 때마다이 알림을 받게 됩니다.

이 메시지를 올바르게 처리 하려면 상태 정보를 요청 하는 기간 (일)의 수를 결정 하 고, 적절 한 값을 사용 하 여 **monthdaystate** 구조의 배열을 초기화 하 고, 관련 구조체 멤버를 새 정보로 초기화 해야 합니다. 필요한 단계를 자세히 설명 하는 다음 절차에서는 사용자에 게 `CMonthCalCtrl` *m_monthcal* 라는 개체 및 **Monthdaystate** objects *mdstate* 배열이 있다고 가정 합니다.

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>MCN_GETDAYSTATE 알림 메시지를 처리 하려면

1. [클래스 마법사](reference/mfc-class-wizard.md)를 사용 하 여 MCN_GETDAYSTATE 메시지에 대 한 알림 처리기를 *m_monthcal* 개체에 추가 합니다 ( [메시지를 함수에 매핑](../mfc/reference/mapping-messages-to-functions.md)참조).

1. 처리기의 본문에 다음 코드를 추가 합니다.

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   이 예에서는 *Pnmhdr* 포인터를 적절 한 형식으로 변환한 다음 요청 될 개월 수 ()를 결정 `pDayState->cDayState` 합니다. 매월 현재 비트 필드 ( `pDayState->prgDayState[i]` )가 0으로 초기화 된 다음 필요한 날짜가 설정 됩니다 (이 경우 매월 15 일).

## <a name="see-also"></a>참고 항목

[CMonthCalCtrl 사용](../mfc/using-cmonthcalctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
