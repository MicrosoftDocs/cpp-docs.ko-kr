---
description: '자세히 알아보기: 목록 컨트롤 및 목록 뷰'
title: 목록 컨트롤 및 목록 뷰
ms.date: 11/04/2016
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
ms.openlocfilehash: 582957cb59bc28797849d45f56fc2be95b8cc2b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336814"
---
# <a name="list-control-and-list-view"></a>목록 컨트롤 및 목록 뷰

편의상 MFC는 두 가지 방법으로 목록 컨트롤을 캡슐화 합니다. List 컨트롤을 사용할 수 있습니다.

- [CListCtrl](reference/clistctrl-class.md) 개체를 대화 상자 클래스에 포함 하 여 직접.

- 클래스 [CListView](reference/clistview-class.md)를 사용 하 여 간접적으로

`CListView` 를 사용 하면 list 컨트롤과 MFC 문서/뷰 아키텍처를 쉽게 통합할 수 있으므로 [Ceditview](reference/ceditview-class.md) 가 편집 컨트롤을 캡슐화 하는 만큼 컨트롤을 캡슐화 합니다. 컨트롤이 mfc 뷰의 전체 노출 영역을 채웁니다. 뷰는로 캐스팅 되는 컨트롤 *입니다* `CListView` .

`CListView`개체는 [CCtrlView](reference/cctrlview-class.md) 및 해당 기본 클래스에서 상속 되며 멤버 함수를 추가 하 여 기본 목록 컨트롤을 검색 합니다. 뷰 멤버를 사용 하 여 뷰로 작업할 수 있습니다. [Getlistctrl](reference/clistview-class.md#getlistctrl) 멤버 함수를 사용 하 여 목록 컨트롤의 멤버 함수에 대 한 액세스 권한을 얻습니다. 이러한 멤버를 사용 하 여 다음을 수행 합니다.

- 목록에서 "항목"을 추가, 삭제 또는 조작 합니다.

- 목록 컨트롤 특성을 설정 하거나 가져옵니다.

기본에 대 한 참조를 가져오려면 `CListCtrl` `CListView` `GetListCtrl` 목록 뷰 클래스에서를 호출 합니다.

[!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]

이 항목에서는 목록 컨트롤을 사용 하는 두 가지 방법에 대해 설명 합니다.

## <a name="see-also"></a>참고 항목

[CListCtrl 사용](using-clistctrl.md)<br/>
[컨트롤](controls-mfc.md)
