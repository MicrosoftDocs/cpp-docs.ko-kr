---
description: '자세히 알아보기: 포함 된 Monthcalendar 컨트롤 액세스'
title: 포함된 MonthCalendar 컨트롤 액세스
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], accessing month calendar
- CDateTimeCtrl class [MFC], accessing embedded control
- month calendar controls [MFC], embedded in date/time picker
- CMonthCalCtrl class [MFC], changing the font
- month calendar controls [MFC], changing the font
- DateTimePicker control [MFC]
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
ms.openlocfilehash: 35c715cdd84bd7921883db530c8cf36e8e5cf07e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169452"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>포함된 MonthCalendar 컨트롤 액세스

포함 된 month calendar 컨트롤 개체는 `CDateTimeCtrl` [Getmonthcalctrl](reference/cdatetimectrl-class.md#getmonthcalctrl) 멤버 함수를 호출 하 여 개체에서 액세스할 수 있습니다.

> [!NOTE]
> 포함 된 month calendar 컨트롤은 날짜 및 시간 선택 컨트롤에 **DTS_UPDOWN** 스타일이 설정 되어 있지 않은 경우에만 사용 됩니다.

이는 포함 된 컨트롤이 표시 되기 전에 특정 특성을 수정 하려는 경우에 유용 합니다. 이 작업을 수행 하려면 **DTN_DROPDOWN** 알림을 처리 하 고 month calendar 컨트롤 ( [CDateTimeCtrl:: getmonthcalctrl](reference/cdatetimectrl-class.md#getmonthcalctrl)사용)을 검색 한 후 수정 합니다. 그러나 month calendar 컨트롤은 영구적이 지 않습니다.

즉, 사용자가 month calendar 컨트롤의 표시를 요청 하면 새 month calendar 컨트롤이 생성 됩니다 ( **DTN_DROPDOWN** 알림 이전). 사용자가 해제할 때 컨트롤이 제거 됩니다 ( **DTN_CLOSEUP** 알림 이후). 즉, 포함 된 컨트롤이 표시 되기 전에 수정 하는 모든 특성은 포함 된 컨트롤이 해제 될 때 손실 됩니다.

다음 예제에서는 **DTN_DROPDOWN** 알림에 대 한 처리기를 사용 하 여이 절차를 보여 줍니다. 이 코드는 [Setmonthcalcolor](reference/cdatetimectrl-class.md#setmonthcalcolor)에 대 한 호출을 사용 하 여 month calendar 컨트롤의 배경색을 회색으로 변경 합니다. 코드는 다음과 같습니다.

[!code-cpp[NVC_MFCControlLadenDialog#5](codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

앞에서 설명한 것 처럼 month calendar 컨트롤의 속성에 대 한 모든 수정 사항은 포함 된 컨트롤을 해제할 때 두 가지 예외를 제외 하 고 손실 됩니다. Month calendar 컨트롤의 색에 대 한 첫 번째 예외는 이미 설명 되어 있습니다. 두 번째 예외는 month calendar 컨트롤에서 사용 하는 글꼴입니다. 기존 글꼴의 핸들을 전달 하 여 [CDateTimeCtrl:: SetMonthCalFont](reference/cdatetimectrl-class.md#setmonthcalfont)를 호출 하 여 기본 글꼴을 수정할 수 있습니다. 다음 예제 (여기서 `m_dtPicker` 는 날짜 및 시간 컨트롤 개체)는 가능한 한 가지 방법을 보여 줍니다.

[!code-cpp[NVC_MFCControlLadenDialog#6](codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

을 호출 하 여 글꼴이 변경 되 면 `CDateTimeCtrl::SetMonthCalFont` 새 글꼴이 저장 되 고 다음에 월 달력이 표시 될 때 사용 됩니다.

## <a name="see-also"></a>참고 항목

[CDateTimeCtrl 사용](using-cdatetimectrl.md)<br/>
[컨트롤](controls-mfc.md)
