---
description: '자세히 알아보기: CStatusBarCtrl에 대 한 설정'
title: CStatusBarCtrl에 대한 설정
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: 24790d387dde0ef5f452045cfe91ad2d39d48b35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217096"
---
# <a name="settings-for-the-cstatusbarctrl"></a>CStatusBarCtrl에 대한 설정

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) 상태 창의 기본 위치는 부모 창의 아래쪽에 있지만 부모 창의 클라이언트 영역 맨 위에 표시 되도록 CCS_TOP 스타일을 지정할 수 있습니다.

상태 창의 오른쪽 끝에 크기 조정 그립을 포함 하도록 SBARS_SIZEGRIP 스타일을 지정할 수 있습니다 `CStatusBarCtrl` . 크기 조정 그립은 크기 조정 테두리와 유사 합니다. 사용자가 클릭 하 고 끌어서 부모 창의 크기를 조정할 수 있는 사각형 영역입니다.

> [!NOTE]
> CCS_TOP 및 SBARS_SIZEGRIP 스타일을 결합 하는 경우 시스템에서 상태 창에 그리는 경우에도 결과 크기 조정 그립은 작동 하지 않습니다.

상태 창의 창 프로시저는 컨트롤 창의 처음 크기와 위치를 자동으로 설정 합니다. 너비는 부모 창의 클라이언트 영역에 있는 것과 동일 합니다. 높이는 상태 창의 장치 컨텍스트 및 창의 테두리 너비에 현재 선택 된 글꼴의 메트릭을 기반으로 합니다.

창 프로시저는 WM_SIZE 메시지를 받을 때마다 상태 창의 크기를 자동으로 조정 합니다. 일반적으로 부모 창의 크기가 변경 되 면 부모는 상태 창에 WM_SIZE 메시지를 보냅니다.

최소 높이 (픽셀)를 지정 하 여 [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)를 호출 하 여 상태 창의 그리기 영역에 대 한 최소 높이를 설정할 수 있습니다. 그리기 영역에는 창의 테두리가 포함 되지 않습니다.

[Getborders](../mfc/reference/cstatusbarctrl-class.md#getborders)를 호출 하 여 상태 창의 테두리 너비를 검색 합니다. 이 멤버 함수는 가로 테두리의 너비, 세로 테두리 및 사각형 사이의 테두리를 받는 3 개 요소 배열에 대 한 포인터를 포함 합니다.

## <a name="see-also"></a>참고 항목

[CStatusBarCtrl 사용](../mfc/using-cstatusbarctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
