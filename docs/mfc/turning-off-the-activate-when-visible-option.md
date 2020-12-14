---
description: '자세히 알아보기: 표시 될 때 활성화 옵션 해제'
title: 표시되었을 때 활성화 옵션 해제
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
ms.openlocfilehash: fcb5f7ef0518cbf257ef9ee7a659c9617092b7d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263870"
---
# <a name="turning-off-the-activate-when-visible-option"></a>표시되었을 때 활성화 옵션 해제

컨트롤은 활성 및 비활성의 두 가지 기본 상태를 가집니다. 일반적으로 이러한 상태는 컨트롤에 창이 있는지 여부에 따라 구분됩니다. 활성 컨트롤에는 창이 있지만 비활성 컨트롤에는 창이 없습니다. 창 없는 활성화의 도입으로 이러한 구분은 더 이상 일반적이지 않지만 여전히 많은 컨트롤에 적용됩니다.

일반적으로 ActiveX 컨트롤에서 수행 하는 초기화의 나머지 부분과 비교할 때 창 생성은 비용이 많이 드는 작업입니다. 이상적으로는 컨트롤이 반드시 필요할 때까지 창의 생성을 지연 시킬 수 있습니다.

컨테이너에 표시 되는 전체 시간 동안 많은 컨트롤이 활성화 될 필요는 없습니다. 사용자가 활성화 해야 하는 작업 (예: 마우스를 클릭 하거나 TAB 키를 누름)을 수행할 때까지 컨트롤이 비활성 상태로 유지 될 수 있는 경우가 종종 있습니다. 컨테이너가 활성화 해야 할 때까지 컨트롤이 비활성 상태로 유지 되도록 하려면 컨트롤의 기타 플래그에서 **OLEMISC_ACTIVATEWHENVISIBLE** 플래그를 제거 합니다.

[!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]

컨트롤을 만들 때 MFC ActiveX 컨트롤 마법사의 [컨트롤 설정](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 페이지에서 **표시 되는 경우 활성화** 옵션을 해제 하면 **OLEMISC_ACTIVATEWHENVISIBLE** 플래그가 자동으로 생략 됩니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤: 최적화](../mfc/mfc-activex-controls-optimization.md)
