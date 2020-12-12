---
description: CSpinButtonCtrl 사용에 대 한 자세한 정보
title: CSpinButtonCtrl 사용
ms.date: 11/04/2016
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: ef596c4f194eb60fc8548231293d4570456d2f54
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271592"
---
# <a name="using-cspinbuttonctrl"></a>CSpinButtonCtrl 사용

*스핀 단추* 컨트롤 ( *up-down* 컨트롤이 라고도 함)은 사용자가 클릭 하 여 값을 조정할 수 있는 화살표 쌍을 제공 합니다. 이 값을 *현재 위치* 라고 합니다. 위치는 스핀 단추 범위 내에 유지 됩니다. 사용자가 위쪽 화살표를 클릭 하면 위치가 최대로 이동 합니다. 사용자가 아래쪽 화살표를 클릭 하면 위치가 최소로 이동 합니다.

Spin button 컨트롤은 [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) 클래스에 의해 MFC에 표시 됩니다.

> [!NOTE]
> 기본적으로 spin 단추의 범위는 최대 0 (0)으로 설정 되 고 최소값은 100로 설정 됩니다. 최 댓 값이 최소값 보다 작으므로 위쪽 화살표를 클릭 하면 위치가 줄어들고 아래쪽 화살표를 클릭 하면 해당 위치가 늘어납니다. 이러한 값을 조정 하려면 [CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) 를 사용 합니다.

일반적으로 현재 위치는 함께 제공 되는 컨트롤에 표시 됩니다. 동반 컨트롤을 *버디 창* 이라고 합니다. Spin button 컨트롤에 대 한 예시의 경우 Windows SDK의 [Up-Down 컨트롤 정보](/windows/win32/Controls/up-down-controls) 를 참조 하세요.

Spin 컨트롤 및 편집 컨트롤 버디 창을 만들려면 Visual Studio에서 먼저 편집 컨트롤을 대화 상자 또는 창으로 끌고 spin 컨트롤을 끕니다. Spin 컨트롤을 선택 하 고 **자동 버디** 를 설정 하 고 **버디 정수** 속성을 **True** 로 설정 합니다. 또한 **맞춤** 속성을 설정 합니다. **오른쪽 맞춤** 은 가장 일반적입니다. 이러한 설정을 사용 하면 편집 컨트롤은 탭 순서에서 편집 컨트롤 바로 앞에 있으므로 버디 창으로 설정 됩니다. 편집 컨트롤은 정수를 표시 하 고, spin 컨트롤은 편집 컨트롤의 오른쪽에 포함 됩니다. 필요에 따라 [CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) 메서드를 사용 하 여 spin 컨트롤의 유효한 범위를 설정할 수 있습니다. 사용자가 데이터를 직접 교환 하기 때문에 spin 컨트롤과 버디 창 간에 통신 하는 데는 이벤트 처리기가 필요 하지 않습니다. 예를 들어 창이 나 대화 상자 시퀀스를 통해 페이지를 표시 하는 등의 다른 용도로 spin 컨트롤을 사용 하는 경우 UDN_DELTAPOS 메시지에 대 한 처리기를 추가 하 고 사용자 지정 작업을 수행 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [스핀 단추 스타일](../mfc/spin-button-styles.md)

- [Spin 단추 멤버 함수](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>참고 항목

[컨트롤](../mfc/controls-mfc.md)
