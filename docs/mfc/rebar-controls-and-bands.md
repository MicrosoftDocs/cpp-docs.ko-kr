---
description: '자세한 정보: Rebar 컨트롤 및 밴드'
title: Rebar 컨트롤 및 밴드
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], working with bands in
- bands, in rebar controls
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
ms.openlocfilehash: 27ada3633a560ad8b5852b05bdd6330a0936fb99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248569"
---
# <a name="rebar-controls-and-bands"></a>Rebar 컨트롤 및 밴드

Rebar 컨트롤의 주요 목적은 자식 창, 공용 대화 상자 컨트롤, 메뉴, 도구 모음 등에 대 한 컨테이너 역할을 하는 것입니다. 이러한 포함은 "대역" 이라는 개념에 의해 지원 됩니다. 각 rebar 밴드에는 그리퍼 막대, 비트맵, 텍스트 레이블 및 자식 창의 모든 조합이 포함 될 수 있습니다.

클래스 `CReBarCtrl` 에는 특정 rebar 밴드에 대 한 정보를 검색 하 고 조작 하는 데 사용할 수 있는 많은 멤버 함수가 있습니다.

- [Get밴드 수](../mfc/reference/crebarctrl-class.md#getbandcount) Rebar 컨트롤의 현재 밴드 수를 검색 합니다.

- [Get대역 정보](../mfc/reference/crebarctrl-class.md#getbandinfo) 지정 된 밴드의 정보를 사용 하 여 **Re바 밴드 정보** 구조를 초기화 합니다. 해당 하는 [Set대역 정보](../mfc/reference/crebarctrl-class.md#setbandinfo) 멤버 함수가 있습니다.

- [Getrect](../mfc/reference/crebarctrl-class.md#getrect) 지정 된 밴드의 경계 사각형을 검색 합니다.

- [Getrowcount](../mfc/reference/crebarctrl-class.md#getrowcount) Rebar 컨트롤의 밴드 행 수를 검색 합니다.

- [Idtoindex](../mfc/reference/crebarctrl-class.md#idtoindex) 지정 된 밴드의 인덱스를 검색 합니다.

- [Get밴드 테두리](../mfc/reference/crebarctrl-class.md#getbandborders) 밴드의 테두리를 검색 합니다.

조작을 수행 하는 것 외에도 특정 rebar 밴드에 대해 작업을 수행할 수 있는 몇 가지 멤버 함수가 제공 됩니다.

[Insertband](../mfc/reference/crebarctrl-class.md#insertband) 및 [deleteband](../mfc/reference/crebarctrl-class.md#deleteband) rebar 밴드를 추가 및 제거 합니다. [MinimizeBand](../mfc/reference/crebarctrl-class.md#minimizeband) 및 [MaximizeBand](../mfc/reference/crebarctrl-class.md#maximizeband) 는 특정 rebar 밴드의 현재 크기에 영향을 줍니다. [Moveband](../mfc/reference/crebarctrl-class.md#moveband) 특정 rebar 밴드의 인덱스를 변경 합니다. [Showband](../mfc/reference/crebarctrl-class.md#showband) 사용자의 rebar 밴드를 표시 하거나 숨깁니다.

다음 예제에서는 기존 rebar 컨트롤에 도구 모음 밴드 (*m_wndToolBar*)를 추가 하는 방법을 보여 줍니다 (*m_wndReBar*). 밴드는 구조를 초기화 한 `rbi` 다음 멤버 함수를 호출 하 여 설명 됩니다 `InsertBand` .

[!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/cpp/rebar-controls-and-bands_1.cpp)]

## <a name="see-also"></a>참고 항목

[CReBarCtrl 사용](../mfc/using-crebarctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
