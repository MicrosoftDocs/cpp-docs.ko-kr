---
description: '자세히 알아보기: 이미지 목록 만들기'
title: 이미지 목록 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: f2776902e7be06161bdbcfad23bd21d9188467f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309669"
---
# <a name="creating-the-image-lists"></a>이미지 목록 만들기

[CListView](reference/clistview-class.md) 또는 [CListCtrl](reference/clistctrl-class.md)를 사용 하는지에 관계 없이 이미지 목록을 만드는 것은 동일 합니다.

> [!NOTE]
> 목록 컨트롤이 스타일을 포함 하는 경우에만 이미지 목록이 필요 `LVS_ICON` 합니다.

클래스를 사용 `CImageList` 하 여 전체 크기 아이콘, 작은 아이콘 및 상태에 대 한 하나 이상의 이미지 목록을 만듭니다. [CImageList](reference/cimagelist-class.md)을 참조 하 고 Windows SDK [목록 뷰 이미지 목록](/windows/win32/Controls/using-list-view-controls) 을 참조 하세요.

각 이미지 목록에 대해 [CListCtrl:: Se agelist](reference/clistctrl-class.md#setimagelist) 를 호출 합니다. 적절 한 개체에 포인터를 전달 `CImageList` 합니다.

## <a name="see-also"></a>참고 항목

[CListCtrl 사용](using-clistctrl.md)<br/>
[컨트롤](controls-mfc.md)
