---
description: '자세한 정보: 트리 컨트롤 사용'
title: 트리 컨트롤 사용
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
ms.openlocfilehash: 7b8a10acc3ee256f4b26c9988c4de7df900e1535
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143197"
---
# <a name="using-tree-controls"></a>트리 컨트롤 사용

트리 컨트롤 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))의 일반적인 사용법은 다음 패턴을 따릅니다.

- 컨트롤이 만들어집니다. 컨트롤이 대화 상자 템플릿에서 지정 되거나를 사용 하는 경우 `CTreeView` 에는 대화 상자 또는 뷰를 만들 때 자동으로 생성 됩니다. 트리 컨트롤을 다른 창의 자식 창으로 만들려면 [create](../mfc/reference/ctreectrl-class.md#create) member 함수를 사용 합니다.

- 트리 컨트롤에서 이미지를 사용 하 게 하려면 [Seon Agelist](../mfc/reference/ctreectrl-class.md#setimagelist)를 호출 하 여 이미지 목록을 설정 합니다. 또한 [Setindent](../mfc/reference/ctreectrl-class.md#setindent)를 호출 하 여 들여쓰기를 변경할 수 있습니다. 이 작업을 수행 하는 데 좋은 시간은 [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (대화 상자의 컨트롤) 또는 [oninitialupdate](../mfc/reference/cview-class.md#oninitialupdate) (보기의 경우)입니다.

- `CTreeCtrl`각 데이터 항목에 대해의 [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) 함수를 한 번씩 호출 하 여 데이터를 컨트롤에 배치 합니다. `InsertItem` 자식 항목을 추가할 때 처럼 나중에 참조 하는 데 사용할 수 있는 항목에 대 한 핸들을 반환 합니다. 데이터를 초기화 하는 데 적합 한 시간 `OnInitDialog` (대화 상자의 컨트롤) 또는 `OnInitialUpdate` (뷰의 경우)입니다.

- 사용자가 컨트롤과 상호 작용하여 다양한 알림 메시지가 전송됩니다. 컨트롤 창의 메시지 맵에 ON_NOTIFY_REFLECT 매크로를 추가 하거나 부모 창의 메시지 맵에 ON_NOTIFY 매크로를 추가 하 여 처리 하려는 각 메시지를 처리 하는 함수를 지정할 수 있습니다. 가능한 알림 목록은이 항목의 뒷부분에 나오는 [트리 제어 알림 메시지](../mfc/tree-control-notification-messages.md) 를 참조 하세요.

- 다양한 Set 멤버 함수를 호출하여 컨트롤에 대한 값을 설정합니다. 이렇게 변경 하려면 들여쓰기를 설정 하 고 항목에 연결 된 텍스트, 이미지 또는 데이터를 변경 합니다.

- 다양 한 Get 함수를 사용 하 여 컨트롤의 내용을 검사 합니다. 또한 지정 된 항목의 부모, 자식 및 형제로 핸들을 검색할 수 있도록 하는 함수를 사용 하 여 트리 컨트롤의 내용을 트래버스할 수 있습니다. 특정 노드의 자식을 정렬할 수도 있습니다.

- 컨트롤이 완료 되 면 제대로 소멸 되었는지 확인 합니다. 트리 컨트롤이 대화 상자에 있거나 뷰가 면 해당 컨트롤이 `CTreeCtrl` 자동으로 제거 됩니다. 그렇지 않은 경우 컨트롤 및 `CTreeCtrl` 개체가 모두 제대로 소멸되었는지 확인해야 합니다.

## <a name="see-also"></a>참고 항목

[CTreeCtrl 사용](../mfc/using-ctreectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
