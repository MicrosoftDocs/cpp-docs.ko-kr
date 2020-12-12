---
description: '자세한 정보: ATL 메시지 처리기 추가'
title: ATL 메시지 처리기 추가
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
ms.openlocfilehash: 263cbcb863ee287c9b3f4650263a3fac33d7ab7b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166345"
---
# <a name="adding-an-atl-message-handler"></a>ATL 메시지 처리기 추가

메시지 처리기 (Windows 메시지를 처리 하는 멤버 함수)를 컨트롤에 추가 하려면 먼저 클래스 뷰에서 컨트롤을 선택 합니다. 그런 다음 **속성** 창을 열고, **메시지** 아이콘을 선택 하 고, 필요한 메시지 옆의 상자에 있는 드롭다운 컨트롤을 클릭 합니다. 그러면 컨트롤의 헤더 파일에 메시지 처리기의 선언이 추가 되 고 컨트롤의 .cpp 파일에 처리기의 기본 구현이 추가 됩니다. 또한 메시지 맵을 추가 하 고 처리기에 대 한 항목을 추가 합니다.

ATL에서 메시지 처리기를 추가 하는 것은 MFC 클래스에 메시지 처리기를 추가 하는 것과 비슷합니다. 자세한 내용은 [MFC 메시지 처리기 추가](../mfc/reference/adding-an-mfc-message-handler.md) 를 참조 하세요.

다음 조건은 ATL 메시지 처리기를 추가 하는 경우에만 적용 됩니다.

- 메시지 처리기는 MFC와 동일한 명명 규칙을 따릅니다.

- 새 메시지 맵 항목이 주 메시지 맵에 추가 됩니다. 이 마법사는 대체 메시지 맵과 체인을 인식 하지 못합니다.

## <a name="see-also"></a>참고 항목

[창 구현](../atl/implementing-a-window.md)
