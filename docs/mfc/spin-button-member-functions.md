---
description: '자세한 정보: 스핀 단추 멤버 함수'
title: 스핀 단추 멤버 함수
ms.date: 11/04/2016
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
ms.openlocfilehash: 6a03ab33d29634ed85d807eb5b51edfdef310d65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216836"
---
# <a name="spin-button-member-functions"></a>스핀 단추 멤버 함수

Spin 컨트롤 ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md))에 사용할 수 있는 여러 멤버 함수가 있습니다. 이러한 함수를 사용 하 여 스핀 단추의 다음 특성을 변경할 수 있습니다.

- **가속** 사용자가 화살표 단추를 누르고 있을 때 위치가 변경 되는 속도를 조정할 수 있습니다. 가속 작업을 수행 하려면 [SetAccel](../mfc/reference/cspinbuttonctrl-class.md#setaccel) 및 [GetAccel](../mfc/reference/cspinbuttonctrl-class.md#getaccel) 멤버 함수를 사용 합니다.

- **기본** 버디 창의 캡션에 위치를 표시 하는 데 사용 되는 기본 (10 또는 16)을 변경할 수 있습니다. 기반으로 작업 하려면 [getbase](../mfc/reference/cspinbuttonctrl-class.md#getbase) 및 [setbase](../mfc/reference/cspinbuttonctrl-class.md#setbase) 멤버 함수를 사용 합니다.

- **버디 창** 버디 창을 동적으로 설정할 수 있습니다. 버디 창에 해당 하는 컨트롤을 쿼리하거나 변경 하려면 [getbuddy](../mfc/reference/cspinbuttonctrl-class.md#getbuddy) 및 [setbuddy](../mfc/reference/cspinbuttonctrl-class.md#setbuddy) 멤버 함수를 사용 합니다.

- **위치** 위치를 쿼리하고 변경할 수 있습니다. 위치와 직접 작업 하려면 [GetPos](../mfc/reference/cspinbuttonctrl-class.md#getpos) 및 [setpos](../mfc/reference/cspinbuttonctrl-class.md#setpos) 멤버 함수를 사용 합니다. 버디 컨트롤의 캡션이 변경 될 수 있으므로 (예를 들어, 버디가 편집 컨트롤인 경우)는 `GetPos` 현재 캡션을 검색 하 고 그에 따라 위치를 조정 합니다.

- **범위** 스핀 단추에 대 한 최대 및 최소 위치를 변경할 수 있습니다. 기본적으로 최대값은 0으로 설정 되 고 최소값은 100로 설정 됩니다. 기본 최대값은 기본 최소값 보다 작기 때문에 화살표 단추의 작업은 카운터를 직관적으로 파악 합니다. 일반적으로는 [SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) 멤버 함수를 사용 하 여 범위를 설정 합니다. 범위를 쿼리하려면 [Getrange](../mfc/reference/cspinbuttonctrl-class.md#getrange)를 사용 합니다.

## <a name="see-also"></a>참고 항목

[CSpinButtonCtrl 사용](../mfc/using-cspinbuttonctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
