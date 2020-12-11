---
description: '자세히 알아보기: 확장 된 콤보 상자 컨트롤에서 이미지 목록 사용'
title: 확장 콤보 상자 컨트롤에서 이미지 목록 사용
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
ms.openlocfilehash: 9fb4b70f91a8ffc3d0175ec855cd005de10da280
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154372"
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>확장 콤보 상자 컨트롤에서 이미지 목록 사용

확장 된 콤보 상자 컨트롤의 주요 기능은 이미지 목록의 이미지를 콤보 상자 컨트롤의 개별 항목과 연결 하는 기능입니다. 각 항목은 세 가지 이미지를 표시할 수 있습니다. 하나는 선택 된 상태이 고 하나는 nonselected 상태이 고 다른 하나는 오버레이 이미지용입니다.

다음 절차에서는 확장 된 콤보 상자 컨트롤에 이미지 목록을 연결 합니다.

### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>확장 된 콤보 상자 컨트롤에 이미지 목록을 연결 하려면

1. [CImageList](../mfc/reference/cimagelist-class.md) 생성자를 사용 하 고 결과 포인터를 저장 하 여 새 이미지 목록을 생성 하거나 기존 이미지 목록 개체를 사용 합니다.

1. [CImageList:: Create](../mfc/reference/cimagelist-class.md#create)를 호출 하 여 새 이미지 목록 개체를 초기화 합니다. 다음 코드는이 호출의 한 예입니다.

   [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]

1. 가능한 각 상태에 대 한 선택적 이미지 (선택 또는 nonselected 및 오버레이)를 추가 합니다. 다음 코드는 미리 정의 된 세 개의 이미지를 추가 합니다.

   [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]

1. [CComboBoxEx:: SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist)를 호출 하 여 이미지 목록을 컨트롤과 연결 합니다.

이미지 목록이 컨트롤과 연결 된 후에는 각 항목에 사용할 수 있는 세 가지 상태에 사용할 이미지를 개별적으로 지정할 수 있습니다. 자세한 내용은 [개별 항목에 대 한 이미지 설정](../mfc/setting-the-images-for-an-individual-item.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CComboBoxEx 사용](../mfc/using-ccomboboxex.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
