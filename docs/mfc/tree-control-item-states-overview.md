---
description: '자세한 정보: 트리 컨트롤 항목 상태 개요'
title: 트리 컨트롤 항목 상태 개요
ms.date: 11/04/2016
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
ms.openlocfilehash: bfc8f7783fdaafcb66e29040a316028d96bd86c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264026"
---
# <a name="tree-control-item-states-overview"></a>트리 컨트롤 항목 상태 개요

트리 컨트롤 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))의 각 항목에는 현재 상태가 있습니다. 예를 들어 항목을 선택 하 고, 사용 하지 않도록 설정 하 고, 확장할 수 있습니다. 대부분의 경우 tree 컨트롤은 항목의 선택 등 사용자 동작을 반영 하도록 항목의 상태를 자동으로 설정 합니다. 그러나 [Setitemstate](../mfc/reference/ctreectrl-class.md#setitemstate) 멤버 함수를 사용 하 여 항목의 상태를 설정 하 고 [getitemstate](../mfc/reference/ctreectrl-class.md#getitemstate) 멤버 함수를 사용 하 여 항목의 현재 상태를 검색할 수도 있습니다. 항목 상태의 전체 목록은 Windows SDK의 [트리 뷰 컨트롤 상수](/windows/win32/Controls/tree-view-control-item-states) 를 참조 하십시오.

항목의 현재 상태는 *nstate* 매개 변수에 의해 지정 됩니다. 트리 컨트롤에서 항목을 선택 하거나 항목에 포커스를 설정 하는 등의 사용자 작업을 반영 하도록 항목의 상태를 변경할 수 있습니다. 또한 응용 프로그램에서 항목의 상태를 변경 하 여 항목을 사용 하지 않도록 설정 하거나 숨기고 오버레이 이미지 또는 상태 이미지를 지정할 수 있습니다.

항목의 상태를 지정 하거나 변경 하는 경우 *nStateMask* 매개 변수는 설정할 상태 비트를 지정 하 고 *nstate* 매개 변수에는 해당 비트의 새 값이 포함 됩니다. 예를 들어 다음 예제에서는 개체의 *Hparentitem* 으로 지정 된 부모 항목의 현재 상태를로 변경 합니다 `CTreeCtrl` ( `m_treeCtrl` ) `TVIS_EXPANDPARTIAL` .

[!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]

상태를 변경 하는 또 다른 예는 항목의 오버레이 이미지를 설정 하는 것입니다. 이를 수행 하려면 *nStateMask* 에 `TVIS_OVERLAYMASK` 값을 포함 해야 하며, *nstate* 는 [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) 매크로를 사용 하 여 왼쪽 8 비트로 이동 된 오버레이 이미지의 1부터 기반 하는 인덱스를 포함 해야 합니다. 오버레이 이미지를 지정 하지 않도록 인덱스는 0이 될 수 있습니다. [CImageList:: SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) 함수를 이전에 호출 하 여 오버레이 이미지를 트리 컨트롤의 오버레이 이미지 목록에 추가 해야 합니다. 함수는 추가할 이미지의 인덱스 (1부터 사용)를 지정 합니다. INDEXTOOVERLAYMASK 매크로에 사용 되는 인덱스입니다. 트리 컨트롤에는 오버레이 이미지를 최대 4 개까지 포함할 수 있습니다.

항목의 상태 이미지를 설정 하려면 *nStateMask* 은 `TVIS_STATEIMAGEMASK` 값을 포함 해야 하며, *nstate* 는 [INDEXTOSTATEIMAGEMASK](/windows/win32/api/commctrl/nf-commctrl-indextostateimagemask) 매크로를 사용 하 여 왼쪽 12 비트로 이동 된 상태 이미지의 1부터 기반 인덱스를 포함 해야 합니다. 인덱스는 상태 이미지를 지정 하지 않을 경우 0이 될 수 있습니다. 오버레이 및 상태 이미지에 대 한 자세한 내용은 [트리 컨트롤 이미지 목록](../mfc/tree-control-image-lists.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CTreeCtrl 사용](../mfc/using-ctreectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
