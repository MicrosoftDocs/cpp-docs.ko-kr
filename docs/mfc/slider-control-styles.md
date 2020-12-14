---
description: '자세히 알아보기: Slider 컨트롤 스타일'
title: 슬라이더 컨트롤 스타일
ms.date: 11/04/2016
helpviewer_keywords:
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
ms.openlocfilehash: cec057683862212a4d999ec7d0488c5f2a0837cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216914"
---
# <a name="slider-control-styles"></a>슬라이더 컨트롤 스타일

슬라이더 컨트롤 ([CSliderCtrl](../mfc/reference/csliderctrl-class.md))에는 세로 방향 또는 가로 방향 중 하나가 있을 수 있습니다. 둘 중 하나 또는 양쪽에 눈금 표시를 포함할 수 있습니다. 연속 값의 범위를 지정 하는 데 사용할 수도 있습니다. 이러한 속성은 슬라이더 컨트롤을 만들 때 지정 하는 슬라이더 컨트롤 스타일을 사용 하 여 제어 됩니다.

TBS_HORZ 및 TBS_VERT 스타일은 슬라이더 컨트롤의 방향을 결정 합니다. 방향을 지정 하지 않으면 슬라이더 컨트롤이 가로 방향으로 표시 됩니다.

TBS_AUTOTICKS 스타일은 값 범위에서 각 증가값에 대 한 눈금이 있는 슬라이더 컨트롤을 만듭니다. 이러한 눈금 표시는 [SetRange](../mfc/reference/csliderctrl-class.md#setrange) 멤버 함수를 호출할 때 자동으로 추가 됩니다. TBS_AUTOTICKS 지정 하지 않으면 [Settic](../mfc/reference/csliderctrl-class.md#settic) 및 [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq)와 같은 멤버 함수를 사용 하 여 눈금 표시의 위치를 지정할 수 있습니다. 눈금 표시를 표시 하지 않는 슬라이더 컨트롤을 만들려면 TBS_NOTICKS 스타일을 사용할 수 있습니다.

슬라이더 컨트롤의 한쪽 또는 양쪽에 눈금 표시를 표시할 수 있습니다. 가로 슬라이더 컨트롤의 경우 TBS_BOTTOM 또는 TBS_TOP 스타일을 지정할 수 있습니다. 세로 슬라이더 컨트롤의 경우 TBS_RIGHT 또는 TBS_LEFT 스타일을 지정할 수 있습니다. TBS_BOTTOM 및 TBS_RIGHT 기본 설정입니다. 슬라이더 컨트롤의 양쪽에 있는 눈금 표시의 경우 모든 방향에서 TBS_BOTH 스타일을 지정 합니다.

슬라이더 컨트롤을 만들 때 TBS_ENABLESELRANGE 스타일을 지정 하는 경우에만 슬라이더 컨트롤이 선택 범위를 표시할 수 있습니다. 슬라이더 컨트롤에이 스타일이 있으면 선택 범위의 시작 위치와 끝 위치에 있는 눈금 표시가 삼각형으로 표시 되 고 선택 범위가 강조 표시 됩니다. 예를 들어 선택 범위는 간단한 예약 응용 프로그램에서 유용할 수 있습니다. 사용자는 예약 된 모임 시간을 식별 하기 위해 하루 중 시간에 해당 하는 눈금 표시 범위를 선택할 수 있습니다.

기본적으로 슬라이더 컨트롤의 슬라이더 길이는 선택 범위가 변경 됨에 따라 달라 집니다. 슬라이더 컨트롤에 TBS_FIXEDLENGTH 스타일이 있으면 선택 범위가 변경 되는 경우에도 슬라이더의 길이는 동일 하 게 유지 됩니다. TBS_NOTHUMB 스타일이 있는 슬라이더 컨트롤에 슬라이더가 포함 되지 않습니다.

## <a name="see-also"></a>참고 항목

[CSliderCtrl 사용](../mfc/using-csliderctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
