---
description: '자세한 정보: 헤더 항목에 대 한 끌어서 놓기 지원 제공'
title: 헤더 항목에 대한 끌어서 놓기 지원 제공
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: ed42f61220ee2033dbc36e11c18664be3968dddd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248790"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>헤더 항목에 대한 끌어서 놓기 지원 제공

헤더 항목에 대 한 끌어서 놓기 지원을 제공 하려면 HDS_DRAGDROP 스타일을 지정 합니다. 헤더 항목에 대 한 끌어서 놓기 지원은 사용자에 게 헤더 컨트롤의 헤더 항목을 다시 정렬 하는 기능을 제공 합니다. 기본 동작은 끌어 온 헤더 항목의 반투명 끌기 이미지와 새 위치의 시각적 표시기를 제공 합니다 (머리글 항목이 삭제 된 경우).

일반적인 끌어서 놓기 기능을 사용 하는 것 처럼 HDN_BEGINDRAG 및 HDN_ENDDRAG 알림을 처리 하 여 기본 끌어서 놓기 동작을 확장할 수 있습니다. [CHeaderCtrl:: CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) 멤버 함수를 재정의 하 여 끌기 이미지의 모양을 사용자 지정할 수도 있습니다.

> [!NOTE]
> 목록 컨트롤에서 포함 된 헤더 컨트롤에 대 한 끌어서 놓기 지원을 제공 하는 경우 [목록 컨트롤 스타일 변경](../mfc/changing-list-control-styles.md) 항목에서 확장 스타일 섹션을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CHeaderCtrl 사용](../mfc/using-cheaderctrl.md)
