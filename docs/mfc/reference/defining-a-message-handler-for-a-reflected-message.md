---
description: '자세히 알아보기: 리플렉션된 메시지의 메시지 처리기 정의'
title: 리플렉트된 메시지의 메시지 처리기 정의
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: 5d742c589401f3537b34546dfa89bc50ca060d18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220190"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>리플렉트된 메시지의 메시지 처리기 정의

새 MFC 컨트롤 클래스를 만든 후에는 해당 클래스에 대 한 메시지 처리기를 정의할 수 있습니다. 반영 된 메시지 처리기를 통해 컨트롤 클래스는 부모에 의해 메시지가 수신 되기 전에 자신의 메시지를 처리할 수 있습니다. MFC [CWnd:: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) 함수를 사용 하 여 컨트롤에서 부모 창으로 메시지를 보낼 수 있습니다.

예를 들어이 기능을 사용 하 여 부모 창에 의존 하는 대신 자신을 다시 그리는 목록 상자를 만들 수 있습니다 (소유자가 그린). 반영 되는 메시지에 대 한 자세한 내용은 [리플렉션된 메시지 처리](../../mfc/handling-reflected-messages.md)를 참조 하세요.

동일한 기능을 사용 하 여 [activex 컨트롤](../../mfc/activex-controls-on-the-internet.md) 을 만들려면 activex 컨트롤에 대 한 프로젝트를 만들어야 합니다.

> [!NOTE]
> 아래 설명 된 대로 클래스 마법사를 사용 하 여 ActiveX 컨트롤에 대 한 리플렉션된 메시지 (OCM_ *메시지*)를 추가할 수 없습니다. 이러한 메시지는 수동으로 추가 해야 합니다.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>클래스 마법사에서 리플렉션된 메시지의 메시지 처리기를 정의 하려면

1. 목록, rebar 컨트롤, 도구 모음 또는 트리 컨트롤과 같은 컨트롤을 MFC 프로젝트에 추가 합니다.

1. 클래스 뷰에서 컨트롤 클래스의 이름을 클릭 합니다.

1. [클래스 마법사](mfc-class-wizard.md)에서 컨트롤 클래스 이름이 **클래스 이름** 목록에 표시 됩니다.

1. **메시지** 탭을 클릭 하 여 컨트롤에 추가할 수 있는 Windows 메시지를 표시 합니다.

1. 처리기를 정의 하려는 리플렉션된 메시지를 선택 합니다. 반영 된 메시지는 등호 (=)로 표시 됩니다.

1. 클래스 마법사의 오른쪽 열에 있는 셀을 클릭 하 여 처리기의 제안 된 이름을 HandlerName로 표시 합니다 \<add> . (예를 들어 **= WM_CTLCOLOR** 메시지 처리기에서 제안 \<add> 하는 **CtlColor**).

1. 허용할 제안 이름을 클릭 합니다. 처리기가 프로젝트에 추가 됩니다.

1. 메시지 처리기를 편집 하거나 삭제 하려면 4 ~ 7 단계를 반복 합니다. 처리기 이름을 포함 하는 셀을 클릭 하 여 편집 하거나 삭제 하 고 적절 한 태스크를 클릭 합니다.

## <a name="see-also"></a>참고 항목

[함수에 메시지 매핑](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[코드 마법사에서 기능 추가](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[클래스 추가](../../ide/adding-a-class-visual-cpp.md)<br/>
[멤버 함수 추가](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[멤버 변수 추가](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[가상 함수 재정의](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 메시지 처리기](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[클래스 구조 탐색](../../ide/navigate-code-cpp.md)
