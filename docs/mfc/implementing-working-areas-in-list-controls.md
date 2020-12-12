---
description: '자세히 알아보기: 목록 컨트롤의 작업 영역 구현'
title: 리스트 컨트롤의 작업 영역 구현
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: 04eb935531dff0ac1ee240dec8690bd7ce1378a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290078"
---
# <a name="implementing-working-areas-in-list-controls"></a>리스트 컨트롤의 작업 영역 구현

기본적으로 목록 컨트롤은 모든 항목을 표준 그리드 방식으로 정렬 합니다. 그러나 다른 방법으로 목록 항목을 사각형 그룹으로 정렬 하는 작업 영역을 지원 합니다. 작업 영역을 구현 하는 목록 컨트롤의 이미지는 Windows SDK에서 List-View 컨트롤 사용을 참조 하세요.

> [!NOTE]
> 작업 영역은 목록 컨트롤이 아이콘 또는 작은 아이콘 모드일 때만 표시 됩니다. 그러나 보기가 보고서 또는 목록 모드로 전환 된 경우에는 현재 작업 영역이 유지 됩니다.

작업 영역을 사용 하 여 빈 테두리 (항목의 왼쪽, 위쪽 및/또는 오른쪽)를 표시 하거나, 일반적으로가 아닌 경우 가로 스크롤 막대가 표시 되도록 할 수 있습니다. 또 다른 일반적인 사용법은 항목을 이동 하거나 삭제할 수 있는 여러 작업 영역을 만드는 것입니다. 이 방법을 사용 하면 의미가 다른 단일 보기에서 영역을 만들 수 있습니다. 그러면 사용자가 항목을 다른 영역에 배치 하 여 분류할 수 있습니다. 이에 대 한 예는 읽기/쓰기 파일의 영역과 읽기 전용 파일의 다른 영역이 있는 파일 시스템의 뷰입니다. 파일 항목이 읽기 전용 영역으로 이동 된 경우 자동으로 읽기 전용이 됩니다. 읽기 전용 영역에서 읽기/쓰기 영역으로 파일을 이동 하면 파일 읽기/쓰기가 가능 합니다.

`CListCtrl` 는 목록 컨트롤에서 작업 영역을 만들고 관리 하기 위한 여러 멤버 함수를 제공 합니다. [Get작업 영역](reference/clistctrl-class.md#getworkareas) 및 [set작업 영역](reference/clistctrl-class.md#setworkareas) `CRect` `RECT` 에서는 목록 컨트롤에 대해 현재 구현 된 작업 영역을 저장 하는 개체 (또는 구조체)의 배열을 검색 하 고 설정 합니다. 또한 [Getnumberof작업 영역](reference/clistctrl-class.md#getnumberofworkareas) 에서는 목록 컨트롤에 대 한 현재 작업 영역 수를 검색 합니다 (기본적으로 0).

## <a name="items-and-working-areas"></a>항목 및 작업 영역

작업 영역을 만들면 작업 영역 내에 있는 항목이 그 멤버가 됩니다. 마찬가지로, 항목을 작업 영역으로 이동 하는 경우 해당 항목은 이동 된 작업 영역의 멤버가 됩니다. 항목이 작업 영역 내에 없으면 자동으로 첫 번째 (인덱스 0) 작업 영역의 멤버가 됩니다. 항목을 만들어 특정 작업 영역 내에 배치 하려면 항목을 만든 다음 [Setitemposition](reference/clistctrl-class.md#setitemposition)을 호출 하 여 원하는 작업 영역으로 이동 해야 합니다. 아래 두 번째 예제에서는이 방법을 보여 줍니다.

다음 예제에서는 `rcWorkAreas` 목록 컨트롤 ()에서 각 작업 영역 주위에 10 픽셀의 테두리가 있는 동일한 크기의 네 가지 작업 영역 ()을 구현 합니다 `m_WorkAreaListCtrl` .

[!code-cpp[NVC_MFCControlLadenDialog#20](codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

[ApproximateViewRect](reference/clistctrl-class.md#approximateviewrect) 에 대 한 호출을 통해 한 지역의 모든 항목을 표시 하는 데 필요한 총 영역의 추정치를 가져옵니다. 그런 다음이 추정치는 네 개의 영역으로 나뉘어 5 픽셀 너비의 테두리로 채워집니다.

다음 예에서는 각 그룹 ()에 기존 목록 항목을 할당 하 `rcWorkAreas` 고 컨트롤 뷰 ()를 새로 고쳐 `m_WorkAreaListCtrl` 효과를 완료 합니다.

[!code-cpp[NVC_MFCControlLadenDialog#21](codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>참고 항목

[CListCtrl 사용](using-clistctrl.md)<br/>
[컨트롤](controls-mfc.md)
