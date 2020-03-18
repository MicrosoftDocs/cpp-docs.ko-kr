---
title: CStatusBarCtrl 개체에서 도구 설명 사용
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: a607a5fb8c9470df42d12c771865b924891b2dac
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442547"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>CStatusBarCtrl 개체에서 도구 설명 사용

상태 표시줄 컨트롤에 대 한 도구 설명을 사용 하도록 설정 하려면 SBT_TOOLTIPS 스타일을 사용 하 여 `CStatusBarCtrl` 개체를 만듭니다.

> [!NOTE]
>  `CStatusBar` 개체를 사용 하 여 상태 표시줄을 구현 하는 경우 `CStatusBar::CreateEx` 함수를 사용 합니다. 포함 된 `CStatusBarCtrl` 개체에 대 한 추가 스타일을 지정할 수 있습니다.

`CStatusBarCtrl` 개체가 성공적으로 만들어지면 [CStatusBarCtrl:: SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) 및 [CStatusBarCtrl:: GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) 를 사용 하 여 특정 창에 대 한 팁 텍스트를 설정 하 고 검색 합니다.

도구 설명이 설정 되 면 파트에 텍스트가 없거나 모든 텍스트를 파트 안에 표시할 수 없는 경우에만 표시 됩니다. 도구 설명은 단순 모드에서 지원 되지 않습니다.

## <a name="see-also"></a>참고 항목

[CStatusBarCtrl 사용](../mfc/using-cstatusbarctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
