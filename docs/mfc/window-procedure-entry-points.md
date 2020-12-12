---
description: '자세히 알아보기: 창 프로시저 진입점'
title: 창 프로시저 진입점
ms.date: 11/04/2016
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
ms.openlocfilehash: 2c2e5dc5d37a2e6f187e694d39205c4cd95b3810
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214483"
---
# <a name="window-procedure-entry-points"></a>창 프로시저 진입점

MFC 창 프로시저를 보호 하기 위해 모듈 정적은 특수 창 프로시저 구현과 연결 됩니다. 이 링크는 모듈이 MFC에 연결 될 때 자동으로 발생 합니다. 이 창 프로시저는 AFX_MANAGE_STATE 매크로를 사용 하 여 유효한 모듈 상태를 올바르게 설정 하 고,를 호출한 다음을 호출 하 여 `AfxWndProc` `WindowProc` 적절 한 파생 개체의 멤버 함수를 위임 합니다 `CWnd` .

## <a name="see-also"></a>참고 항목

[MFC 모듈의 상태 데이터 관리](../mfc/managing-the-state-data-of-mfc-modules.md)
