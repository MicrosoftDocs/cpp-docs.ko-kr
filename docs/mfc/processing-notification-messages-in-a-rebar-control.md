---
description: '자세한 정보: Rebar 컨트롤에서 알림 메시지 처리'
title: Rebar 컨트롤에서 알림 메시지 처리
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: 6255f10068072f75f556cf1c8576008ab821ed27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154840"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Rebar 컨트롤에서 알림 메시지 처리

Rebar 컨트롤의 부모 클래스에서 `OnChildNotify` 처리 하려는 모든 rebar 컨트롤 () 알림 메시지에 대 한 switch 문을 사용 하 여 처리기 함수를 만듭니다 `CReBarCtrl` . 사용자가 rebar 컨트롤 위로 개체를 끌어서 rebar 밴드의 레이아웃을 변경 하 고 rebar 컨트롤에서 밴드를 삭제 하는 등의 방법으로 부모 창으로 알림을 보냅니다.

Rebar 컨트롤 개체에서 다음 알림 메시지를 보낼 수 있습니다.

- Rebar 컨트롤이 자동으로 크기를 조정 하는 경우 RBS_AUTOSIZE 스타일을 사용 하 여 만든 RBN_AUTOSIZE입니다.

- 사용자가 대역 끌기를 시작할 때 rebar 컨트롤에서 보낸 RBN_BEGINDRAG입니다.

- 밴드의 자식 창 크기가 조정 될 때 rebar 컨트롤에서 보낸 RBN_CHILDSIZE입니다.

- 밴드를 삭제 한 후 rebar 컨트롤에서 보낸 RBN_DELETEDBAND입니다.

- 밴드를 삭제 하려고 할 때 rebar 컨트롤에서 전송 하는 RBN_DELETINGBAND.

- 사용자가 대역 끌기를 중지할 때 rebar 컨트롤에서 보낸 RBN_ENDDRAG입니다.

- 컨트롤의 밴드 위로 개체를 끌 때 rebar 컨트롤 (RBS_REGISTERDROP 스타일을 사용 하 여 만듦)에서 보내는 RBN_GETOBJECT입니다.

- 높이가 변경 될 때 rebar 컨트롤에서 RBN_HEIGHTCHANGE를 보냅니다.

- 사용자가 컨트롤의 밴드 레이아웃을 변경할 때 rebar 컨트롤에서 전송 하는 RBN_LAYOUTCHANGED입니다.

이러한 알림에 대 한 자세한 내용은 Windows SDK의 [Rebar 컨트롤 참조](/windows/win32/controls/rebar-control-reference) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CReBarCtrl 사용](using-crebarctrl.md)<br/>
[컨트롤](controls-mfc.md)
