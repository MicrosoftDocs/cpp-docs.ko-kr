---
description: '자세한 정보: 트리 컨트롤 항목 선택'
title: 트리 컨트롤 항목 선택
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: 46e1256eea3e8175b996a1b6bdfdd7c1de2739d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264039"
---
# <a name="tree-control-item-selection"></a>트리 컨트롤 항목 선택

한 항목에서 다른 항목으로 선택이 변경 되 면 트리 컨트롤 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))이 [TVN_SELCHANGING](/windows/win32/Controls/tvn-selchanging) 및 [TVN_SELCHANGED](/windows/win32/Controls/tvn-selchanged) 알림 메시지를 보냅니다. 두 알림에는 변경 내용이 마우스 클릭 또는 키 입력의 결과 인지 여부를 지정 하는 값이 포함 됩니다. 또한 알림은 선택 항목을 가져오는 항목과 선택 항목을 손실 하는 항목에 대 한 정보를 포함 합니다. 이 정보를 사용 하 여 항목의 선택 상태에 종속 된 항목 특성을 설정할 수 있습니다. 에 대 한 응답으로 **TRUE** 를 반환 하면 `TVN_SELCHANGING` 선택이 변경 되지 않습니다. **false** 를 반환 하면 변경 내용이 허용 됩니다.

응용 프로그램은 [Selectitem](../mfc/reference/ctreectrl-class.md#selectitem) 멤버 함수를 호출 하 여 선택 항목을 변경할 수 있습니다.

## <a name="see-also"></a>참고 항목

[CTreeCtrl 사용](../mfc/using-ctreectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
