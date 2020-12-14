---
description: '자세한 정보: Tree 컨트롤 스타일'
title: 트리 컨트롤 스타일
ms.date: 11/04/2016
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
helpviewer_keywords:
- TVS_LINESATROOT [MFC]
- styles [MFC], CTreeCtrl
- styles [MFC], tree control
- TVS_HASLINES
- TVS_SINGLEEXPAND
- CTreeCtrl class [MFC], styles
- TVS_EDITLABELS [MFC]
- TVS_NOTOOLTIPS [MFC]
- TVS_HASBUTTONS [MFC]
- tree controls [MFC], styles
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
ms.openlocfilehash: a0e6f88c6dfcae906c5b5f1ef1f5f7cafa582b02
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263922"
---
# <a name="tree-control-styles"></a>트리 컨트롤 스타일

트리 컨트롤 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 스타일은 트리 컨트롤의 모양에 대 한 다양 한 측면을 제어 합니다. 트리 컨트롤을 만들 때 초기 스타일을 설정 합니다. [Getwindowlong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) 및 [setwindowlong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) Windows 함수를 사용 하 여 *n 인덱스* 매개 변수에 대 한 **GWL_STYLE** 를 지정 하 여 트리 컨트롤을 만든 후 스타일을 검색 하 고 변경할 수 있습니다. 스타일의 전체 목록은 Windows SDK의 [트리 뷰 컨트롤 창 스타일](/windows/win32/Controls/tree-view-control-window-styles) 을 참조 하세요.

**TVS_HASLINES** 스타일은 자식 항목을 해당 부모 항목에 연결 하는 선을 그려 트리 컨트롤의 계층 구조에 대 한 그래픽 표현을 향상 시킵니다. 이 스타일은 계층의 루트에 있는 항목을 연결 하지 않습니다. 이렇게 하려면 **TVS_HASLINES** 및 **TVS_LINESATROOT** 스타일을 결합 해야 합니다.

사용자는 부모 항목을 두 번 클릭 하 여 부모 항목의 자식 항목 목록을 확장 하거나 축소할 수 있습니다. **TVS_SINGLEEXPAND** 스타일이 있는 트리 컨트롤은 선택 되는 항목을 확장 하 고 축소 하기 위해 항목을 선택 취소 합니다. 마우스를 사용 하 여 선택한 항목을 한 번 클릭 하면 해당 항목이 닫히고 확장 됩니다. 선택한 항목을 열 때 한 번 클릭 하면 축소 됩니다.

**TVS_HASBUTTONS** 스타일이 있는 트리 컨트롤은 각 부모 항목의 왼쪽에 단추를 추가 합니다. 사용자는 부모 항목을 두 번 클릭 하는 대신 단추를 클릭 하 여 자식 항목을 확장 하거나 축소할 수 있습니다. **TVS_HASBUTTONS** 는 계층의 루트에 있는 항목에 단추를 추가 하지 않습니다. 이렇게 하려면 **TVS_HASLINES**, **TVS_LINESATROOT** 및 **TVS_HASBUTTONS** 를 결합 해야 합니다.

**TVS_EDITLABELS** 스타일을 사용 하면 사용자가 트리 컨트롤 항목의 레이블을 편집할 수 있습니다. 레이블 편집에 대 한 자세한 내용은이 항목의 뒷부분에 나오는 [트리 컨트롤 레이블 편집](../mfc/tree-control-label-editing.md) 을 참조 하세요.

**TVS_NOTOOLTIPS** 스타일은 tree view 컨트롤의 자동 도구 설명 기능을 사용 하지 않도록 설정 합니다. 이 기능은 전체 제목이 현재 표시 되지 않는 경우 마우스 커서 아래에 있는 항목의 제목을 포함 하는 도구 설명을 자동으로 표시 합니다.

## <a name="see-also"></a>참고 항목

[CTreeCtrl 사용](../mfc/using-ctreectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
