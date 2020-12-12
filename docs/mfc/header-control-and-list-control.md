---
description: '자세히 알아보기: 헤더 컨트롤 및 목록 컨트롤'
title: 헤더 컨트롤 및 목록 컨트롤
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
ms.openlocfilehash: d2301f82a76516a008de0a72e1c9288580b8f545
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325921"
---
# <a name="header-control-and-list-control"></a>헤더 컨트롤 및 목록 컨트롤

대부분의 경우 [CListCtrl](reference/clistctrl-class.md) 또는 [CListView](reference/clistview-class.md) 개체에 포함 된 헤더 컨트롤을 사용 합니다. 그러나 [CView](reference/cview-class.md)파생 개체에서 열 또는 행으로 정렬 된 데이터 조작과 같이 별도의 헤더 컨트롤 개체가 바람직한 경우도 있습니다. 이러한 경우에는 포함 헤더 컨트롤의 모양과 기본 동작을 보다 효율적으로 제어 해야 합니다.

표준, 기본 동작을 제공 하는 헤더 컨트롤이 필요한 일반적인 경우에는 대신 [CListCtrl](reference/clistctrl-class.md) 또는 [CListView](reference/clistview-class.md) 를 사용 하는 것이 좋습니다. `CListCtrl`기본 헤더 컨트롤의 기능을 목록 뷰 공용 컨트롤에 포함 하려는 경우에 사용 합니다. View 개체에 포함 된 기본 헤더 컨트롤의 기능을 사용 하려면 [CListView](reference/clistview-class.md) 를 사용 합니다.

> [!NOTE]
> 이러한 컨트롤은 목록 뷰 컨트롤이 **LVS_REPORT** 스타일을 사용 하 여 생성 된 경우에만 기본 제공 헤더 컨트롤을 포함 합니다.

대부분의 경우 포함 하는 목록 뷰 컨트롤의 스타일을 변경 하 여 포함 헤더 컨트롤의 모양을 수정할 수 있습니다. 또한 부모 목록 뷰 컨트롤의 멤버 함수를 통해 header 컨트롤에 대 한 정보를 얻을 수 있습니다. 그러나 포함 헤더 컨트롤의 특성과 스타일에 대 한 완전 한 제어 및 액세스를 위해서는 헤더 컨트롤 개체에 대 한 포인터를 얻는 것이 좋습니다.

포함 된 헤더 컨트롤 개체는 `CListCtrl` 또는 `CListView` 해당 클래스의 멤버 함수에 대 한 호출을 사용 하 여 액세스할 수 있습니다 `GetHeaderCtrl` . 다음 코드에서 이 과정을 보여 줍니다.

[!code-cpp[NVC_MFCControlLadenDialog#14](codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [이미지 목록과 헤더 컨트롤 함께 사용](using-image-lists-with-header-controls.md)

## <a name="see-also"></a>참고 항목

[CHeaderCtrl 사용](using-cheaderctrl.md)<br/>
[컨트롤](controls-mfc.md)
