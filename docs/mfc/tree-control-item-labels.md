---
description: '자세한 정보: 트리 컨트롤 항목 레이블'
title: 트리 컨트롤 항목 레이블
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
ms.openlocfilehash: 62113a7534bf234ac8dde1154d5732bc29df8387
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264072"
---
# <a name="tree-control-item-labels"></a>트리 컨트롤 항목 레이블

일반적으로 트리 컨트롤 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))에 항목을 추가할 때 항목 레이블의 텍스트를 지정 합니다. `InsertItem`멤버 함수는 레이블의 텍스트를 포함 하는 문자열을 포함 하 여 항목의 속성을 정의 하는 [tvitem](/windows/win32/api/commctrl/ns-commctrl-tvitemw) 구조를 전달할 수 있습니다. `InsertItem` 에는 다양 한 매개 변수 조합을 사용 하 여 호출할 수 있는 여러 오버 로드가 있습니다.

트리 컨트롤은 각 항목을 저장 하기 위해 메모리를 할당 합니다. 항목 레이블의 텍스트는이 메모리의 상당 부분을 차지 합니다. 응용 프로그램이 트리 컨트롤에서 문자열의 복사본을 유지 관리 하는 경우 실제 문자열을 트리 컨트롤에 전달 하는 대신의 *pszText* 멤버  `TV_ITEM` 또는 *lpszItem* 매개 변수에서 LPSTR_TEXTCALLBACK 값을 지정 하 여 컨트롤의 메모리 요구 사항을 줄일 수 있습니다. **LPSTR_TEXTCALLBACK** 를 사용 하면 항목을 다시 그려야 할 때마다 트리 컨트롤이 응용 프로그램에서 항목의 레이블 텍스트를 검색 합니다. 텍스트를 검색 하기 위해 tree 컨트롤은 [NMTVDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmtvdispinfow) 구조체의 주소를 포함 하는 [TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo) 알림 메시지를 보냅니다. 포함 된 구조의 적절 한 멤버를 설정 하 여 응답 해야 합니다.

트리 컨트롤은 트리 컨트롤을 만드는 프로세스의 힙에서 할당 된 메모리를 사용 합니다. 트리 컨트롤의 최대 항목 수는 힙에서 사용 가능한 메모리의 양을 기반으로 합니다. 각 항목은 64 바이트를 사용 합니다.

## <a name="see-also"></a>참고 항목

[CTreeCtrl 사용](../mfc/using-ctreectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
