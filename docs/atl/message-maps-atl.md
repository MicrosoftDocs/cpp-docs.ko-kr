---
description: '자세한 정보: 메시지 맵 (ATL)'
title: 메시지 맵 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message maps, ATL
- ATL, message handlers
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
ms.openlocfilehash: c5b3340abbfbc66ac710ab716e3daa38dd7cd6df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159520"
---
# <a name="message-maps-atl"></a>메시지 맵 (ATL)

메시지 맵은 처리기 함수를 특정 메시지, 명령 또는 알림과 연결 합니다. ATL의 [메시지 맵 매크로](../atl/reference/message-map-macros-atl.md)를 사용 하 여 창에 대 한 메시지 맵을 지정할 수 있습니다. , 및의 창 프로시저는 창의 메시지를 `CWindowImpl` `CDialogImpl` `CContainedWindowT` 메시지 맵으로 보냅니다.

[메시지 처리기 함수](../atl/message-handler-functions.md) 는 형식의 추가 인수를 허용 합니다 `BOOL&` . 이 인수는 메시지가 처리 되었는지 여부를 나타내며, 기본적으로 TRUE로 설정 되어 있습니다. 그러면 처리기 함수는 인수를 FALSE로 설정 하 여 메시지를 처리 하지 않았음을 나타낼 수 있습니다. 이 경우 ATL은 메시지 맵에서 처리기 함수를 계속 찾습니다. 이 인수를 FALSE로 설정 하면 먼저 메시지에 대 한 응답으로 일부 작업을 수행한 다음 기본 처리 또는 다른 처리기 함수에서 메시지 처리를 완료할 수 있습니다.

## <a name="chained-message-maps"></a>연결 된 메시지 맵

ATL을 사용 하면 메시지 맵을 연결 하 여 메시지 처리를 다른 클래스에 정의 된 메시지 맵으로 이동할 수도 있습니다. 예를 들어, 별도의 클래스에서 일반적인 메시지 처리를 구현 하 여 해당 클래스에 대 한 모든 windows 연결에 대 한 일관 된 동작을 제공할 수 있습니다. 기본 클래스 또는 클래스의 데이터 멤버에 연결할 수 있습니다.

또한 ATL은 런타임에 다른 개체의 메시지 맵에 연결할 수 있는 동적 체인을 지원 합니다. 동적 체인을 구현 하려면 [Cdynamicchain](../atl/reference/cdynamicchain-class.md)에서 클래스를 파생 해야 합니다. 그런 다음 메시지 맵에서 [CHAIN_MSG_MAP_DYNAMIC](reference/message-map-macros-atl.md#chain_msg_map_dynamic) 매크로를 선언 합니다. CHAIN_MSG_MAP_DYNAMIC에는 연결 하려는 개체와 메시지 맵을 식별 하는 고유 숫자가 필요 합니다. 을 호출 하 여이 고유한 값을 정의 해야 합니다 `CDynamicChain::SetChainEntry` .

클래스가 [Cmessagemap](../atl/reference/cmessagemap-class.md)에서 파생 되는 경우 메시지 맵을 선언 하는 모든 클래스에 연결할 수 있습니다. `CMessageMap` 개체가 메시지 맵을 다른 개체에 노출할 수 있도록 합니다. 는 `CWindowImpl` 이미에서 파생 `CMessageMap` 됩니다.

## <a name="alternate-message-maps"></a>대체 메시지 맵

마지막으로, ATL은 [ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map) 매크로로 선언 된 대체 메시지 맵을 지원 합니다. 각 대체 메시지 맵은 ALT_MSG_MAP에 전달 하는 고유한 숫자로 식별 됩니다. 대체 메시지 맵을 사용 하 여 한 맵에서 여러 창의 메시지를 처리할 수 있습니다. 기본적으로는 `CWindowImpl` 대체 메시지 맵을 사용 하지 않습니다. 이 지원을 추가 하려면 `WindowProc` 파생 클래스에서 메서드를 재정의 하 `CWindowImpl` 고 `ProcessWindowMessage` 메시지 맵 식별자를 사용 하 여를 호출 합니다.

## <a name="see-also"></a>참고 항목

[창 구현](../atl/implementing-a-window.md)
