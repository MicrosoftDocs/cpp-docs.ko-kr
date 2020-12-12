---
description: '자세히 알아보기: Toolbar 컨트롤 사용'
title: ToolBar 컨트롤 사용
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: bb5b14b35deeff515468a16c82a606704300a395
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197467"
---
# <a name="working-with-the-toolbar-control"></a>ToolBar 컨트롤 사용

이 문서에서는 [CToolBar](../mfc/reference/ctoolbar-class.md) 의 기반이 되는 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 개체에 액세스 하 여 도구 모음에 대 한 제어를 강화 하는 방법을 설명 합니다. 이는 고급 항목입니다.

## <a name="procedures"></a>프로시저

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>CToolBar 개체의 기본 도구 모음 공용 컨트롤에 액세스 하려면

1. [CToolBar:: GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)를 호출 합니다.

`GetToolBarCtrl`[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 개체에 대 한 참조를 반환 합니다. 참조를 사용 하 여 toolbar 컨트롤 클래스의 멤버 함수를 호출할 수 있습니다.

> [!CAUTION]
> Get 함수를 호출 하는 `CToolBarCtrl`  것은 안전 하지만 **Set** 함수를 호출 하는 경우 주의 해야 합니다. 이는 고급 항목입니다. 일반적으로 기본 도구 모음 컨트롤에 액세스할 필요가 없습니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [컨트롤 (Windows 공용 컨트롤)](../mfc/controls-mfc.md)

- [도구 모음 기본 사항](../mfc/toolbar-fundamentals.md)

- [도구 모음 고정 및 고정 해제](../mfc/docking-and-floating-toolbars.md)

- [동적으로 도구 모음 크기 조정](../mfc/docking-and-floating-toolbars.md)

- [도구 모음 도구 설명](../mfc/toolbar-tool-tips.md)

- [Flyby 상태 표시줄 업데이트](../mfc/toolbar-tool-tips.md)

- [도구 설명 알림 처리](../mfc/handling-tool-tip-notifications.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md) 및 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 클래스

- [사용자 지정 알림 처리](../mfc/handling-customization-notifications.md)

- [여러 도구 모음](../mfc/toolbar-fundamentals.md)

- [이전 도구 모음 사용](../mfc/using-your-old-toolbars.md)

- [컨트롤 막대](../mfc/control-bars.md)

Windows 공용 컨트롤 사용에 대 한 일반적인 내용은 [공용 컨트롤](/windows/win32/Controls/common-controls-intro)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 도구 모음 구현](../mfc/mfc-toolbar-implementation.md)
