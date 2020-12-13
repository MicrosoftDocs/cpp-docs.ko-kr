---
description: '자세히 알아보기: 컨트롤 그리기 최적화'
title: 컨트롤 그리기 최적화
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
ms.openlocfilehash: 93e948d4a572f4e02c8676b2af1b6f8943004f26
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331808"
---
# <a name="optimizing-control-drawing"></a>컨트롤 그리기 최적화

컨테이너 공급 디바이스 컨텍스트에 컨트롤을 그리게 되는 경우 일반적으로 디바이스 컨텍스트에 GDI 개체(예: 펜, 브러시, 글꼴 등)를 선택하고 해당 그리기 작업을 수행하고, 이전의 GDI 개체를 복원합니다. 컨테이너에 동일한 디바이스 컨텍스트로 그려지는 여러 컨트롤이 있고 각 컨트롤이 필요한 GDI 개체를 선택하는 경우 컨트롤이 이전에 선택한 개체를 개별적으로 복원하지 않으면 시간을 절약할 수 있습니다. 모든 컨트롤이 그려진 후 컨테이너에서는 원래 개체를 자동으로 복원할 수 있습니다.

컨테이너에서이 기술을 지원 하는지 여부를 검색 하기 위해 컨트롤은 [COleControl:: IsOptimizedDraw](reference/colecontrol-class.md#isoptimizeddraw) 멤버 함수를 호출할 수 있습니다. 이 함수가 **TRUE** 를 반환 하는 경우 컨트롤은 이전에 선택한 개체를 복원 하는 일반적인 단계를 건너뛸 수 있습니다.

다음 `OnDraw` 함수(최적화되지 않음)가 있는 컨트롤을 가정합니다.

[!code-cpp[NVC_MFC_AxOpt#15](codesnippet/cpp/optimizing-control-drawing_1.cpp)]

예제에서 펜과 브러시는 지역 변수입니다. 이는 소멸자가 범위를 벗어날 경우(`OnDraw` 함수가 종료할 때) 호출된다는 의미입니다. 소멸자는 해당 GDI 개체를 삭제하려고 합니다. 그러나 `OnDraw`에서 반환 시 선택한 해당 개체를 디바이스 컨텍스트에 남기려는 경우 삭제하지 않아야 합니다.

이 완료 되 면 [Cpen](reference/cpen-class.md) 및 [cpen](reference/cbrush-class.md) 개체가 소멸 되지 않도록 하려면 `OnDraw` 지역 변수 대신 멤버 변수에 저장 합니다. 컨트롤의 클래스 선언에서 두 개의 새 멤버 변수에 대한 선언을 추가합니다.

[!code-cpp[NVC_MFC_AxOpt#16](codesnippet/cpp/optimizing-control-drawing_2.h)]
[!code-cpp[NVC_MFC_AxOpt#17](codesnippet/cpp/optimizing-control-drawing_3.h)]

다음과 같이 `OnDraw` 함수를 다시 쓸 수 있습니다.

[!code-cpp[NVC_MFC_AxOpt#18](codesnippet/cpp/optimizing-control-drawing_4.cpp)]

이 방법을 사용하면 `OnDraw`를 호출할 때마다 펜 및 브러시를 만들지 않습니다. 추가 인스턴스 데이터를 관리하는 대신 속도가 향상됩니다.

ForeColor 또는 BackColor 속성이 변경되는 경우 펜 또는 브러시를 다시 만들어야 합니다. 이렇게 하려면 [OnForeColorChanged](reference/colecontrol-class.md#onforecolorchanged) 및 [Onbackcolorchanged](reference/colecontrol-class.md#onbackcolorchanged) 멤버 함수를 재정의 합니다.

[!code-cpp[NVC_MFC_AxOpt#19](codesnippet/cpp/optimizing-control-drawing_5.cpp)]

마지막으로 불필요한 `SelectObject` 호출을 제거하려면 `OnDraw`를 다음과 같이 수정합니다.

[!code-cpp[NVC_MFC_AxOpt#20](codesnippet/cpp/optimizing-control-drawing_6.cpp)]

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤: 최적화](mfc-activex-controls-optimization.md)<br/>
[COleControl 클래스](reference/colecontrol-class.md)<br/>
[MFC ActiveX 컨트롤](mfc-activex-controls.md)<br/>
[MFC ActiveX 컨트롤 마법사](reference/mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 컨트롤: ActiveX 컨트롤 그리기](mfc-activex-controls-painting-an-activex-control.md)
