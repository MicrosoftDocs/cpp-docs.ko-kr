---
description: '자세히 알아보기: 명령이 아닌 메시지가 해당 처리기에 도달 하는 방법'
title: 명령이 아닌 메시지가 해당 처리기에 도달하는 방법
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: e337a62a731e7ed0832b6cd28d1f56024247c176
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172819"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>명령이 아닌 메시지가 해당 처리기에 도달하는 방법

명령과 달리 표준 Windows 메시지는 명령 대상 체인을 통해 라우팅되지 않지만 일반적으로 Windows에서 메시지를 전송 하는 창에서 처리 됩니다. 창은 주 프레임 창, MDI 자식 창, 표준 컨트롤, 대화 상자, 뷰 또는 다른 종류의 자식 창이 될 수 있습니다.

런타임에 각 Windows 창은 `CWnd` 자체 연결 된 메시지 맵과 처리기 함수가 있는 창 개체 (에서 직접 또는 간접적으로 파생 됨)에 연결 됩니다. 프레임 워크는 명령에 대해 메시지 맵을 사용 하 여 들어오는 메시지를 처리기에 매핑합니다.

## <a name="see-also"></a>참고 항목

[프레임 워크가 처리기를 호출 하는 방법](how-the-framework-calls-a-handler.md)
