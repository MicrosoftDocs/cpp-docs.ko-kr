---
description: '자세히 알아보기: NotifyHandler'
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: 1c08eaa91962fa9f6acf330de89334ad1224e582
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159377"
---
# <a name="notifyhandler"></a>NotifyHandler

메시지 맵에 있는 NOTIFY_HANDLER 매크로의 세 번째 매개 변수로 식별 되는 함수의 이름입니다.

## <a name="syntax"></a>구문

```cpp
LRESULT NotifyHandler(
    int idCtrl,
    LPNMHDR pnmh,
    BOOL& bHandled);
```

#### <a name="parameters"></a>매개 변수

*idCtrl*<br/>
메시지를 보내는 컨트롤의 식별자입니다.

*pnmh*<br/>
알림 코드 및 추가 정보를 포함 하는 [NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr) 구조체의 주소입니다. 일부 알림 메시지의 경우이 매개 변수는 `NMHDR` 구조를 첫 번째 멤버로 포함 하는 더 큰 구조를 가리킵니다.

*bHandled*<br/>
*NotifyHandler* 를 호출 하기 전에 메시지 맵은 *BHANDLED* 를 TRUE로 설정 합니다. *NotifyHandler* 에서 메시지를 완전히 처리 하지 않는 경우에는 메시지에 추가 처리가 필요 함을 나타내는 *Bhandled* 를 **FALSE** 로 설정 해야 합니다.

## <a name="return-value"></a>반환 값

메시지 처리의 결과입니다. 성공 하는 경우 0입니다.

## <a name="remarks"></a>설명

메시지 맵에서이 메시지 처리기를 사용 하는 예제는 [NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler))를 참조 하세요.

## <a name="see-also"></a>참고 항목

[창 구현](../atl/implementing-a-window.md)<br/>
[메시지 맵](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
