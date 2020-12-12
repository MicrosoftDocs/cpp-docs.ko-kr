---
description: '자세히 알아보기: 헤더 컨트롤 만들기'
title: 헤더 컨트롤 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
ms.openlocfilehash: b75a21a0d855e557bf02a9144fc3712b5bb2ee35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309695"
---
# <a name="creating-the-header-control"></a>헤더 컨트롤 만들기

헤더 컨트롤을 포함 하는 목록 컨트롤을 추가할 수 있지만 헤더 컨트롤은 대화 상자 편집기에서 직접 사용할 수 없습니다.

### <a name="to-put-a-header-control-in-a-dialog-box"></a>대화 상자에서 헤더 컨트롤을 배치 하려면

1. [CHeaderCtrl](reference/cheaderctrl-class.md) 형식의 멤버 변수를 대화 상자 클래스에 수동으로 포함 합니다.

1. [OnInitDialog](reference/cdialog-class.md#oninitdialog)에서의 스타일을 만들고 설정 하 고, `CHeaderCtrl` 위치를 표시 하 고, 표시 합니다.

1. 헤더 컨트롤에 항목을 추가 합니다.

1. [클래스 마법사](reference/mfc-class-wizard.md) 를 사용 하 여 처리 해야 하는 헤더 제어 알림 메시지에 대 한 대화 상자 클래스의 처리기 함수를 매핑할 수 있습니다 ( [메시지를 함수에 매핑](reference/mapping-messages-to-functions.md)참조).

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>뷰에 헤더 컨트롤을 배치 하려면 (CListView 아님)

1. 뷰 클래스에 [CHeaderCtrl](reference/cheaderctrl-class.md) 개체를 포함 합니다.

1. 보기의 [Oninitialupdate](reference/cview-class.md#oninitialupdate) 멤버 함수에서 헤더 컨트롤 창의 스타일을 만들고 위치를 표시 하 고 표시 합니다.

1. 헤더 컨트롤에 항목을 추가 합니다.

1. [클래스 마법사](reference/mfc-class-wizard.md) 를 사용 하 여 처리 해야 하는 헤더 제어 알림 메시지에 대 한 뷰 클래스의 처리기 함수를 매핑할 수 있습니다 ( [메시지를 함수에 매핑](reference/mapping-messages-to-functions.md)참조).

두 경우 모두 뷰 또는 대화 상자 개체를 만들 때 포함 된 컨트롤 개체가 만들어집니다. 그런 다음 [CHeaderCtrl:: create](reference/cheaderctrl-class.md#create) 를 호출 하 여 컨트롤 창을 만들어야 합니다. 컨트롤을 배치 하려면 [CHeaderCtrl:: Layout](reference/cheaderctrl-class.md#layout) 을 호출 하 여 컨트롤의 초기 크기와 위치를 결정 하 고 [setwindowpos](reference/cwnd-class.md#setwindowpos) 를 설정 하 여 원하는 위치를 설정 합니다. 그런 다음 [헤더 컨트롤에 항목 추가](adding-items-to-the-header-control.md)에 설명 된 대로 항목을 추가 합니다.

자세한 내용은 Windows SDK에서 [헤더 컨트롤 만들기](/windows/win32/Controls/header-controls) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CHeaderCtrl 사용](using-cheaderctrl.md)<br/>
[컨트롤](controls-mfc.md)
