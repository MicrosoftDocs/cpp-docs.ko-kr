---
description: '자세히 알아보기: 헤더 컨트롤과 함께 이미지 목록 사용'
title: 이미지 목록과 헤더 컨트롤 함께 사용
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 549f54c9fae7e0e0a63c726f4b75d2adeb38eef8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322733"
---
# <a name="using-image-lists-with-header-controls"></a>이미지 목록과 헤더 컨트롤 함께 사용

헤더 항목에는 헤더 항목 내에 이미지를 표시 하는 기능이 있습니다. 연결 된 이미지 목록에 저장 된이 이미지는 16 x 16 픽셀이 며, 목록 뷰 컨트롤에서 사용 되는 아이콘 이미지와 같은 특성을 갖습니다. 이 동작을 성공적으로 구현 하려면 먼저 이미지 목록을 만들고 초기화 하 고, 목록을 헤더 컨트롤과 연결한 다음 이미지를 표시 하는 헤더 항목의 특성을 수정 해야 합니다.

다음 절차에서는 헤더 컨트롤 ()에 대 `m_pHdrCtrl` 한 포인터와 이미지 목록 ()에 대 한 포인터를 사용 하 여 세부 정보를 보여 줍니다 `m_pHdrImages` .

### <a name="to-display-an-image-in-a-header-item"></a>머리글 항목에 이미지를 표시 하려면

1. [CImageList](../mfc/reference/cimagelist-class.md) 생성자를 사용 하 여 새 이미지 목록을 생성 하거나 기존 이미지 목록 개체를 사용 하 여 결과 포인터를 저장 합니다.

1. [CImageList:: Create](../mfc/reference/cimagelist-class.md#create)를 호출 하 여 새 이미지 목록 개체를 초기화 합니다. 다음 코드는이 호출의 한 예입니다.

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. 각 헤더 항목에 대 한 이미지를 추가 합니다. 다음 코드는 미리 정의 된 두 이미지를 추가 합니다.

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. [CHeaderCtrl:: SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist)를 호출 하 여 이미지 목록을 헤더 컨트롤과 연결 합니다.

1. 헤더 항목을 수정 하 여 연결 된 이미지 목록의 이미지를 표시 합니다. 다음 예에서는 첫 번째 이미지를에서 `m_phdrImages` 첫 번째 헤더 항목에 할당 `m_pHdrCtrl` 합니다.

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

사용 되는 매개 변수 값에 대 한 자세한 내용은 관련 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)을 참조 하십시오.

> [!NOTE]
> 동일한 이미지 목록을 사용 하는 컨트롤이 여러 개 있을 수 있습니다. 예를 들어 표준 목록 뷰 컨트롤에서 목록 뷰 컨트롤의 작은 아이콘 보기와 list view 컨트롤의 헤더 항목 모두에 사용 되는 이미지 목록 (16 x 16 픽셀 이미지)이 있을 수 있습니다.

## <a name="see-also"></a>참고 항목

[CHeaderCtrl 사용](../mfc/using-cheaderctrl.md)
