---
description: '자세히 알아보기: 진행률 컨트롤에 대 한 설정'
title: 진행률 컨트롤에 대한 설정
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
ms.openlocfilehash: 0cf3caa5e7b87062b1714f8e5e350840157ff7ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217070"
---
# <a name="settings-for-the-progress-control"></a>진행률 컨트롤에 대한 설정

진행률 컨트롤에 대 한 기본 설정 ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md))은 범위 및 현재 위치입니다. 범위는 작업의 전체 지속 시간을 나타냅니다. 현재 위치는 응용 프로그램이 작업을 완료 하기 위해 수행한 진행률을 나타냅니다. 범위 또는 위치를 변경 하면 진행률 컨트롤이 자신을 다시 그리도록 합니다.

기본적으로 범위는 0-100으로 설정 되 고 초기 위치는 0으로 설정 됩니다. 진행률 컨트롤에 대 한 현재 범위 설정을 검색 하려면 [Getrange](../mfc/reference/cprogressctrl-class.md#getrange) 멤버 함수를 사용 합니다. 범위를 변경 하려면 [SetRange](../mfc/reference/cprogressctrl-class.md#setrange) 멤버 함수를 사용 합니다.

위치를 설정 하려면 [Setpos](../mfc/reference/cprogressctrl-class.md#setpos)를 사용 합니다. 새 값을 지정 하지 않고 현재 위치를 검색 하려면 [GetPos](../mfc/reference/cprogressctrl-class.md#getpos)를 사용 합니다. 예를 들어 현재 작업의 상태를 단순히 쿼리해야 할 수 있습니다.

진행률 컨트롤의 현재 위치를 단계별로 실행 하려면 [Stit](../mfc/reference/cprogressctrl-class.md#stepit)를 사용 합니다. 각 단계의 크기를 설정 하려면 [Setstep](../mfc/reference/cprogressctrl-class.md#setstep) 을 사용 합니다.

## <a name="see-also"></a>참고 항목

[CProgressCtrl 사용](../mfc/using-cprogressctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
