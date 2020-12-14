---
description: '자세한 정보: 스핀 단추 스타일'
title: 스핀 단추 스타일
ms.date: 09/09/2019
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: c08c878843ba68a46727cc2c54034bb42e5e5d41
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216771"
---
# <a name="spin-button-styles"></a>스핀 단추 스타일

스핀 단추 ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md))에 대 한 대부분의 설정은 스타일에 의해 제어 됩니다. [클래스 마법사](reference/mfc-class-wizard.md)를 사용 하 여 다음 스타일을 설정할 수 있습니다.

- **방향** 세로 또는 가로입니다. 화살표 단추의 방향을 제어 합니다. UDS_HORZ 스타일과 연결 됩니다.

- **맞춤** 연결 되지 않은, 왼쪽 또는 오른쪽 중 하나입니다. 스핀 단추의 위치를 제어 합니다. 왼쪽 및 오른쪽 배치 단추를 버디 창 옆에 배치 합니다. 버디 창의 너비가 스핀 단추를 수용할 수 있도록 줄어듭니다. UDS_ALIGNLEFT 및 UDS_ALIGNRIGHT 스타일과 연결 됩니다.

- **자동 버디** Z 순서에서 이전 창을 스핀 단추에 대 한 버디 창으로 자동으로 선택 합니다. 대화 상자 템플릿에서이 컨트롤은 탭 순서에서 스핀 단추 앞에 오는 컨트롤입니다. UDS_AUTOBUDDY 스타일과 연결 됩니다.

- **버디 정수 설정** 현재 위치가 변경 될 때 spin 컨트롤이 버디 창의 캡션을 증가 시키고 감소 시킵니다. UDS_SETBUDDYINT 스타일과 연결 됩니다.

- **천 단위 없음** 는 버디 창의 캡션에 있는 값에 천 단위 구분 기호를 삽입 하지 않습니다. UDS_NOTHOUSANDS 스타일과 연결 됩니다.

    > [!NOTE]
    >  DDX (대화 상자 데이터 교환)를 사용 하 여 버디 컨트롤에서 정수 값을 가져오려면이 스타일을 설정 합니다. `DDX_Text` 포함 된 천 단위 구분 기호를 허용 하지 않습니다.

- **줄 바꿈** 값이 컨트롤의 범위를 벗어나 증가 하거나 감소 하므로 위치가 "wrap"으로 설정 됩니다. UDS_WRAP 스타일과 연결 됩니다.

- **화살표 키** 위쪽 화살표 및 아래쪽 화살표 키를 누를 때 스핀 단추가 위치를 증가 시키거나 감소 시킵니다. UDS_ARROWKEYS 스타일과 연결 됩니다.

## <a name="see-also"></a>참고 항목

[CSpinButtonCtrl 사용](../mfc/using-cspinbuttonctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
