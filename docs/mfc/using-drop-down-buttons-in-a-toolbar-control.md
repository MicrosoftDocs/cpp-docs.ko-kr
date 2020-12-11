---
description: '자세히 알아보기: Toolbar 컨트롤에서 Drop-Down 단추 사용'
title: 도구 모음 컨트롤에서 드롭다운 단추 사용
ms.date: 11/04/2016
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
ms.openlocfilehash: a37f39397f6b6f66bed1ad1d2fbd9530b55f3d7b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154463"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>도구 모음 컨트롤에서 드롭다운 단추 사용

표준 푸시 단추 외에도 도구 모음에는 드롭다운 단추가 있을 수 있습니다. 드롭다운 단추는 일반적으로 연결 된 아래쪽 화살표가 있음을 나타냅니다.

> [!NOTE]
> 연결 된 아래쪽 화살표는 TBSTYLE_EX_DRAWDDARROWS 확장 스타일이 설정 된 경우에만 표시 됩니다.

사용자가이 화살표를 클릭 하거나 (화살표를 표시 하지 않는 경우) 도구 모음 컨트롤의 부모에 TBN_DROPDOWN 알림 메시지가 전송 됩니다. 그런 다음이 알림을 처리 하 고 팝업 메뉴를 표시할 수 있습니다. Internet Explorer의 동작과 유사 합니다.

다음 절차에서는 팝업 메뉴를 사용 하 여 드롭다운 도구 모음 단추를 구현 하는 방법을 보여 줍니다.

### <a name="to-implement-a-drop-down-button"></a>드롭다운 단추를 구현 하려면

1. 개체를 만든 후에는 `CToolBarCtrl` 다음 코드를 사용 하 여 TBSTYLE_EX_DRAWDDARROWS 스타일을 설정 합니다.

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. 드롭다운 단추가 될 새 ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) 또는 [addbuttons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) 또는 기존 ([setbuttoninfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) 단추에 대 한 TBSTYLE_DROPDOWN 스타일을 설정 합니다. 다음 예제에서는 개체의 기존 단추를 수정 하는 방법을 보여 줍니다 `CToolBarCtrl` .

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. 도구 모음 개체의 부모 클래스에 TBN_DROPDOWN 처리기를 추가 합니다.

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. 새 처리기에서 적절 한 팝업 메뉴를 표시 합니다. 다음 코드에서는 하나의 메서드를 보여 줍니다.

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>참고 항목

[CToolBarCtrl 사용](../mfc/using-ctoolbarctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
