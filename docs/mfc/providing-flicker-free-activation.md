---
description: '자세한 정보: Flicker-Free 활성화 제공'
title: 깜빡임 없는 활성화 제공
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
ms.openlocfilehash: c0af1ccdd4795f55296ff38e0e74bc6492f79eb1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248829"
---
# <a name="providing-flicker-free-activation"></a>깜빡임 없는 활성화 제공

컨트롤이 비활성 및 활성 상태에서 동일 하 게 그려지고 창 없는 활성화를 사용 하지 않는 경우 비활성 상태와 활성 상태 간을 전환할 때 일반적으로 발생 하는 그리기 작업 및 해당 시각적 깜박임을 제거할 수 있습니다. 이렇게 하려면 [COleControl:: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags)에서 반환 된 플래그 집합에 **noFlickerActivate** 플래그를 포함 합니다. 예를 들어:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]

이 플래그를 포함 하는 코드는 MFC ActiveX 컨트롤 마법사를 사용 하 여 컨트롤을 만들 때 [컨트롤 설정](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 페이지에서 **깜빡임 없는 활성화** 옵션을 선택한 경우 자동으로 생성 됩니다.

창 없는 활성화를 사용 하는 경우이 최적화는 영향을 주지 않습니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤: 최적화](../mfc/mfc-activex-controls-optimization.md)
