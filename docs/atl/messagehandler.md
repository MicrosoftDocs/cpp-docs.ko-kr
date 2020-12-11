---
description: '자세한 정보: MessageHandler'
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: d369b94721e57eb4adc704570bc09d1aae184fe1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159507"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler` 메시지 맵에서 MESSAGE_HANDLER 매크로의 두 번째 매개 변수로 식별 되는 함수의 이름입니다.

## <a name="syntax"></a>구문

```cpp
LRESULT MessageHandler(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>매개 변수

*uMsg*<br/>
메시지를 지정합니다.

*wParam*<br/>
추가 메시지 관련 정보입니다.

*lParam*<br/>
추가 메시지 관련 정보입니다.

*bHandled*<br/>
메시지 맵은가 호출 되기 전에 *Bhandled* 를 TRUE로 설정 합니다 `MessageHandler` . `MessageHandler`에서 메시지를 완전히 처리 하지 않는 경우에는 메시지에 추가 처리가 필요 함을 나타내려면 *BHANDLED* 를 FALSE로 설정 해야 합니다.

## <a name="return-value"></a>반환 값

메시지 처리의 결과입니다. 성공 하는 경우 0입니다.

## <a name="remarks"></a>설명

메시지 맵에서이 메시지 처리기를 사용 하는 예제는 [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[창 구현](../atl/implementing-a-window.md)<br/>
[메시지 맵](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
