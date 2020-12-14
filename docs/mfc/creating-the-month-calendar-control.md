---
description: '자세히 알아보기: Month Calendar 컨트롤 만들기'
title: MonthCalendar 컨트롤 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: 98c707e16f05a8f5e4d3b42e3c9504f74e4aca29
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309526"
---
# <a name="creating-the-month-calendar-control"></a>MonthCalendar 컨트롤 만들기

달력 컨트롤을 만드는 방법은 대화 상자에서 컨트롤을 사용 중인지 또는 비모달 창에서 만드는지에 따라 달라집니다.

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>대화 상자에서 CMonthCalCtrl을 직접 사용하려면

1. 대화 상자 편집기에서 달력 컨트롤을 대화 상자 템플릿 리소스에 추가합니다. 해당 컨트롤 ID를 지정합니다.

1. 달력 컨트롤의 속성 대화 상자를 사용해서 필요한 스타일을 지정합니다.

1. [멤버 변수 추가 마법사](../ide/adding-a-member-variable-visual-cpp.md) 를 사용 하 여 컨트롤 속성으로 [Cmonthcalctrl](reference/cmonthcalctrl-class.md) 형식의 멤버 변수를 추가 합니다. 이 멤버를 사용하여 `CMonthCalCtrl` 멤버 함수를 호출할 수 있습니다.

1. [클래스 마법사](reference/mfc-class-wizard.md) 를 사용 하 여 처리 해야 하는 월 달력 컨트롤 알림 메시지에 대 한 대화 상자 클래스의 처리기 함수를 매핑할 수 있습니다 ( [메시지를 함수에 매핑](reference/mapping-messages-to-functions.md)참조).

1. [OnInitDialog](reference/cdialog-class.md#oninitdialog)에서 개체에 대 한 추가 스타일을 설정 `CMonthCalCtrl` 합니다.

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>비모달 창에서 CMonthCalCtrl을 사용하려면

1. 뷰 또는 창 클래스에서 컨트롤을 정의합니다.

1. 부모 창의 [OnCreate](reference/cwnd-class.md#oncreate) handler 함수 (컨트롤을 서브클래싱 하는 경우)의 초기에는 [oninitialupdate](reference/cview-class.md#oninitialupdate)에서 컨트롤의 [Create](reference/cmonthcalctrl-class.md#create) 멤버 함수를 호출 합니다. 컨트롤의 스타일을 설정합니다.

## <a name="see-also"></a>참고 항목

[CMonthCalCtrl 사용](using-cmonthcalctrl.md)<br/>
[컨트롤](controls-mfc.md)
