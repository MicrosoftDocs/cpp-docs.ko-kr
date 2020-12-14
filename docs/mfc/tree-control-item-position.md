---
description: '자세한 정보: 트리 컨트롤 항목 위치'
title: 트리 컨트롤 항목 위치
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
ms.openlocfilehash: 7eeab82c48344f7e16a31b8d6962007024277dfc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264075"
---
# <a name="tree-control-item-position"></a>트리 컨트롤 항목 위치

항목의 초기 위치는 멤버 함수를 사용 하 여 항목이 트리 컨트롤 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))에 추가 될 때 설정 됩니다 `InsertItem` . 멤버 함수 호출은 부모 항목의 핸들과 새 항목을 삽입할 항목의 핸들을 지정 합니다. 두 번째 핸들은 지정 된 부모의 자식 항목이 나 `TVI_FIRST` , 또는 값 중 하나를 식별 해야 합니다. `TVI_LAST` `TVI_SORT`

`TVI_FIRST`또는 `TVI_LAST` 를 지정 하면 트리 컨트롤은 지정 된 부모 항목의 자식 항목 목록 시작 또는 끝에 새 항목을 배치 합니다. `TVI_SORT`을 지정 하면 트리 컨트롤은 항목 레이블의 텍스트를 기준으로 자식 항목 목록에 새 항목을 사전순으로 삽입 합니다.

[Sortchildren](../mfc/reference/ctreectrl-class.md#sortchildren) 멤버 함수를 호출 하 여 부모 항목의 자식 항목 목록을 사전순으로 정렬할 수 있습니다. 이 함수에는 지정 된 부모 항목에서 내림차순으로 모든 자식 항목 수준을 사전순으로 정렬할지 여부를 지정 하는 매개 변수가 포함 되어 있습니다.

[SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb) 멤버 함수를 사용 하면 정의 된 조건에 따라 자식 항목을 정렬할 수 있습니다. 이 함수를 호출 하는 경우 두 자식 항목의 상대 순서를 결정 해야 할 때마다 트리 컨트롤에서 호출할 수 있는 응용 프로그램 정의 콜백 함수를 지정 합니다. 콜백 함수는 비교 되는 항목에 대 한 2 32 비트 응용 프로그램 정의 값과를 호출할 때 사용자가 지정 하는 세 번째 32 비트 값을 받습니다 `SortChildrenCB` .

## <a name="see-also"></a>참고 항목

[CTreeCtrl 사용](../mfc/using-ctreectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
