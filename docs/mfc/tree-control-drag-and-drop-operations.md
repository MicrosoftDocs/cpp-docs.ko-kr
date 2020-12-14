---
description: '자세한 정보: 트리 컨트롤 끌어서 놓기 작업'
title: 트리 컨트롤 끌어서 놓기 작업
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: 000255ad4aa6801cbe27676603a3f42d0abbef30
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264182"
---
# <a name="tree-control-drag-and-drop-operations"></a>트리 컨트롤 끌어서 놓기 작업

트리 컨트롤 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))은 사용자가 항목을 끌기 시작 하면 알림을 보냅니다. 사용자가 마우스 왼쪽 [TVN_BEGINRDRAG](/windows/win32/Controls/tvn-beginrdrag) 단추를 사용 하 여 항목을 끌기 시작 하면 사용자가 오른쪽 단추를 사용 하 여 끌기를 시작할 때 컨트롤에서 [TVN_BEGINDRAG](/windows/win32/Controls/tvn-begindrag) 알림 메시지를 보냅니다. 트리 컨트롤에서 TVS_DISABLEDRAGDROP 스타일을 지정 하 여 트리 컨트롤에서 이러한 알림을 보내지 않도록 할 수 있습니다.

[CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) 멤버 함수를 호출 하 여 끌기 작업 중에 표시할 이미지를 가져옵니다. 트리 컨트롤은 끌고 있는 항목의 레이블을 기반으로 하 여 끌기 비트맵을 만듭니다. 그런 다음 트리 컨트롤에서 이미지 목록을 만들어 비트맵을 추가 하 고 [CImageList](../mfc/reference/cimagelist-class.md) 개체에 대 한 포인터를 반환 합니다.

실제로 항목을 끄는 코드를 제공 해야 합니다. 일반적으로 이미지 목록 함수의 끌기 기능을 사용 하 고 [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) 를 처리 하 고 끌기 작업이 시작 된 후 전송 된 [WM_LBUTTONUP](/windows/win32/inputdev/wm-lbuttonup) (또는 [WM_RBUTTONUP](/windows/win32/inputdev/wm-rbuttonup)) 메시지를 처리 해야 합니다. 이미지 목록 함수에 대 한 자세한 내용은 Windows SDK의 *MFC 참조* 및 [이미지 목록](/windows/win32/controls/image-lists) 에서 [CImageList](../mfc/reference/cimagelist-class.md) 를 참조 하세요. 트리 컨트롤 항목을 끄는 방법에 대 한 자세한 내용은 Windows SDK [트리 뷰 항목 끌기](/windows/win32/Controls/tree-view-controls)를 참조 하세요.

트리 컨트롤의 항목이 끌어서 놓기 작업의 대상이 되는 경우 마우스 커서가 대상 항목에 있을 때 알아야 합니다. [System.windows.media.visualtreehelper.hittest](../mfc/reference/ctreectrl-class.md#hittest) 멤버 함수를 호출 하 여 찾을 수 있습니다. 포인트와 정수 또는 마우스 커서의 현재 좌표를 포함 하는 [TVHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tvhittestinfo) 구조체의 주소를 지정 합니다. 함수가 반환 될 때 정수 또는 구조에는 트리 컨트롤을 기준으로 마우스 커서의 위치를 나타내는 플래그가 포함 됩니다. 커서가 트리 컨트롤의 항목 위에 있으면 구조에도 항목의 핸들이 포함 됩니다.

[SetItem](../mfc/reference/ctreectrl-class.md#setitem) 멤버 함수를 호출 하 여 상태를 값으로 설정 하 여 항목이 끌어서 놓기 작업의 대상 임을 나타낼 수 있습니다 `TVIS_DROPHILITED` . 이 상태가 있는 항목은 끌어서 놓기 대상을 나타내는 데 사용 되는 스타일로 그려집니다.

## <a name="see-also"></a>참고 항목

[CTreeCtrl 사용](../mfc/using-ctreectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
