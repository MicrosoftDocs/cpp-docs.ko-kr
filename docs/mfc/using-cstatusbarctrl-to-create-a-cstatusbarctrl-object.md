---
description: '자세히 알아보기: CStatusBarCtrl를 사용 하 여 CStatusBarCtrl 개체 만들기'
title: CStatusBarCtrl을 사용하여 CStatusBarCtrl 개체 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
ms.openlocfilehash: 0b76065ce4e90600bdec7e4f4a89ee2c5bb14085
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202381"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>CStatusBarCtrl을 사용하여 CStatusBarCtrl 개체 만들기

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)를 사용 하는 일반적인 예는 다음과 같습니다.

### <a name="to-use-a-status-bar-control-with-parts"></a>파트에 상태 표시줄 컨트롤을 사용 하려면

1. `CStatusBarCtrl` 개체를 생성합니다.

1. 상태 표시줄 컨트롤의 그리기 영역에 대 한 최소 높이를 설정 하려면 [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) 를 호출 합니다.

1. [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) 를 호출 하 여 상태 표시줄 컨트롤의 배경색을 설정 합니다.

1. [Setparts](../mfc/reference/cstatusbarctrl-class.md#setparts) 를 호출 하 여 상태 표시줄 컨트롤의 파트 수와 각 파트의 오른쪽 가장자리 좌표를 설정 합니다.

1. [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) 를 호출 하 여 상태 표시줄 컨트롤의 지정 된 부분에 텍스트를 설정 합니다. 이 메시지는 컨트롤이 다음에 WM_PAINT 메시지를 받을 때 새 텍스트를 표시 하도록 변경 된 컨트롤 부분을 무효화 합니다.

상태 표시줄에 텍스트 줄만 표시 해야 하는 경우도 있습니다. 이 경우 [Setsimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)에 대 한 호출을 수행 합니다. 그러면 상태 표시줄 컨트롤이 한 줄의 텍스트를 표시 하는 "simple" 모드로 전환 됩니다.

## <a name="see-also"></a>참고 항목

[CStatusBarCtrl 사용](../mfc/using-cstatusbarctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
