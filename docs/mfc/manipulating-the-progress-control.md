---
description: '자세히 알아보기: 진행률 컨트롤 조작'
title: 진행률 컨트롤 조작
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
ms.openlocfilehash: cfb89dee0047d910fb983546c71e4a1e4a618f56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281095"
---
# <a name="manipulating-the-progress-control"></a>진행률 컨트롤 조작

진행률 컨트롤 ([CProgressCtrl](reference/cprogressctrl-class.md))의 현재 위치를 변경 하는 방법에는 세 가지가 있습니다.

- 위치는 미리 설정 된 증분 양만큼 변경할 수 있습니다.

- 위치는 임의의 양만큼 변경할 수 있습니다.

- 위치를 특정 값으로 변경할 수 있습니다.

### <a name="to-change-the-position-by-a-preset-amount"></a>기본 설정 된 양만큼 위치를 변경 하려면

1. [Setstep](reference/cprogressctrl-class.md#setstep) 멤버 함수를 사용 하 여 증분 크기를 설정 합니다. 기본적으로이 값은 10입니다. 이 값은 일반적으로 컨트롤에 대 한 초기 설정 중 하나로 설정 됩니다. 단계 값은 음수일 수 있습니다.

1. [Stit](reference/cprogressctrl-class.md#stepit) 멤버 함수를 사용 하 여 위치를 늘립니다. 이렇게 하면 컨트롤이 자체적으로 다시 그려집니다.

    > [!NOTE]
    >  `StepIt` 에서 위치가 래핑됩니다. 예를 들어 범위가 1 -100이 고, 20 단계와 90의 위치가 지정 된 경우 `StepIt` 위치를 10으로 설정 합니다.

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>임의의 양만큼 위치를 변경 하려면

1. [OffsetPos](reference/cprogressctrl-class.md#offsetpos) 멤버 함수를 사용 하 여 위치를 변경 합니다. `OffsetPos` 음수 값을 허용 합니다.

    > [!NOTE]
    >  `OffsetPos`와 달리는 `StepIt` 위치를 래핑하지 않습니다. 새 위치는 범위 내에 유지 되도록 조정 됩니다.

### <a name="to-change-the-position-to-a-specific-value"></a>위치를 특정 값으로 변경 하려면

1. [Setpos](reference/cprogressctrl-class.md#setpos) 멤버 함수를 사용 하 여 위치를 특정 값으로 설정 합니다. 필요한 경우 새 위치가 범위 내에 맞게 조정 됩니다.

일반적으로 진행률 컨트롤은 출력에만 사용 됩니다. 새 값을 지정 하지 않고 현재 위치를 가져오려면 [GetPos](reference/cprogressctrl-class.md#getpos)을 사용 합니다.

## <a name="see-also"></a>참고 항목

[CProgressCtrl 사용](using-cprogressctrl.md)<br/>
[컨트롤](controls-mfc.md)
