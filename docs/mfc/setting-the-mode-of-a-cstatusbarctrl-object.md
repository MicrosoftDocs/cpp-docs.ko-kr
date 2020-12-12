---
description: '자세히 알아보기: CStatusBarCtrl 개체의 모드 설정'
title: CStatusBarCtrl 개체의 모드 설정
ms.date: 11/04/2016
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: 46a87c17c68059e1d12476f4963f159cd2915824
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217109"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>CStatusBarCtrl 개체의 모드 설정

개체에는 `CStatusBarCtrl` 단순 하 고 단순 하지 않은 두 가지 모드가 있습니다. 대부분의 경우 상태 표시줄 컨트롤에는 텍스트, 아이콘 또는 아이콘과 함께 하나 이상의 부분이 있습니다. 이를 단순 모드가 아닌 모드로 부릅니다. 이 모드에 대 한 자세한 내용은 [CStatusBarCtrl 개체의 파트 초기화](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md)를 참조 하세요.

그러나 한 줄의 텍스트를 표시 해야 하는 경우도 있습니다. 이 경우 단순 모드는 요구 사항에 맞게 충분 합니다. 개체의 모드를 간단 하 게 변경 하려면 `CStatusBarCtrl` [setsimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) 멤버 함수를 호출 합니다. 상태 표시줄 컨트롤이 단순 모드 이면 멤버 함수를 호출 하 여 텍스트를 설정 하 `SetText` 고 255을 *npane* 매개 변수의 값으로 전달 합니다.

[Issimple](../mfc/reference/cstatusbarctrl-class.md#issimple) 함수를 사용 하 여 개체가 있는 모드를 확인할 수 있습니다 `CStatusBarCtrl` .

> [!NOTE]
> 상태 표시줄 개체가 단순에서 단순으로 또는 그 반대로 변경 되는 경우 창은 즉시 다시 그려지고, 해당 하는 경우 정의 된 부분은 자동으로 복원 됩니다.

## <a name="see-also"></a>참고 항목

[CStatusBarCtrl 사용](../mfc/using-cstatusbarctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
