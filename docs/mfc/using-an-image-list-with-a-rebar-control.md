---
description: '자세한 정보: Rebar 컨트롤에서 이미지 목록 사용'
title: 이미지 목록과 Rebar 컨트롤 함께 사용
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
ms.openlocfilehash: ae4aa0259cbe850dbab8ef4bc04277014b39e357
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271800"
---
# <a name="using-an-image-list-with-a-rebar-control"></a>이미지 목록과 Rebar 컨트롤 함께 사용

각 rebar 밴드는 특히 연결된 이미지 목록의 이미지를 포함할 수 있습니다. 다음 절차는 rebar 밴드에서 이미지를 표시하는 데 필요한 단계를 자세히 설명합니다.

### <a name="to-display-images-in-a-rebar-band"></a>rebar 밴드에서 이미지를 표시하려면

1. 기존 이미지 목록에 대 한 포인터를 전달 하 여 [Seon Agelist](../mfc/reference/crebarctrl-class.md#setimagelist)를 호출 하 여 이미지 목록을 rebar 컨트롤 개체에 연결 합니다.

1. 이미지를 rebar 밴드에 할당 하도록 **Re바 밴드 정보** 구조를 수정 합니다.

   - 필요에  `RBBIM_IMAGE` 따라 추가 플래그를 포함 하려면 비트 or 연산자를 사용 하 여 fmask 멤버를로 설정 합니다.

   - *Iimage* 멤버를 표시할 이미지의 이미지 목록 인덱스로 설정 합니다.

1. 필요한 정보를 사용하여 자식 창을 포함하는 핸들과 텍스트, 크기와 같은 나머지 모든 데이터 멤버를 초기화합니다.

1. [Cre ctrl:: InsertBand](../mfc/reference/crebarctrl-class.md#insertband)에 대 한 호출과 함께 새 대역 (이미지 포함)을 삽입 하 여 **Re바 밴드 정보** 구조를 전달 합니다.

다음 예제에서는 두 개의 이미지가 있는 기존 이미지 목록 개체가 rebar 컨트롤 개체(`m_wndReBar`)에 연결되어 있다고 가정합니다. 첫 번째 이미지를 포함하는 새 rebar 밴드(`rbi`로 정의됨)는 `InsertBand`에 대한 호출로 추가됩니다.

[!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]

## <a name="see-also"></a>참고 항목

[CReBarCtrl 사용](../mfc/using-crebarctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
