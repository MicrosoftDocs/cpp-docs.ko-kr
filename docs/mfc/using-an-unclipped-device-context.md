---
description: '자세한 정보: 잘리지 않는 장치 컨텍스트 사용'
title: 잘리지 않는 디바이스 컨텍스트 사용
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
ms.openlocfilehash: 76131d35b108b04caf0b07be8c46e250120f9f62
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202641"
---
# <a name="using-an-unclipped-device-context"></a>잘리지 않는 디바이스 컨텍스트 사용

컨트롤이 클라이언트 사각형 외부에 표시 되지 않도록 하는 것이 확실 한 경우에는에 대 한 호출을 사용 하지 않도록 설정 하 여 작고 검색 속도 향상을 실현할 수 있습니다 `IntersectClipRect` `COleControl` . 이렇게 하려면 [COleControl:: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags)에서 반환 된 플래그 집합에서 *clipPaintDC* 플래그를 제거 합니다. 예를 들어:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]

이 플래그를 제거 하는 코드는 MFC ActiveX 컨트롤 마법사를 사용 하 여 컨트롤을 만들 때 [컨트롤 설정](../mfc/reference/control-settings-mfc-activex-control-wizard.md) 페이지에서 **잘리지 않는 장치 컨텍스트** 옵션을 선택 하는 경우 자동으로 생성 됩니다.

창 없는 활성화를 사용 하는 경우이 최적화는 영향을 주지 않습니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤: 최적화](../mfc/mfc-activex-controls-optimization.md)
