---
description: '자세히 알아보기: 애니메이션 컨트롤에서 보낸 알림'
title: 애니메이션 컨트롤이 보내는 알림
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 17dbd041e1c22b8d6542e64fd8b99d86389ea2d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280562"
---
# <a name="notifications-sent-by-animation-controls"></a>애니메이션 컨트롤이 보내는 알림

애니메이션 컨트롤 ([CAnimateCtrl](reference/canimatectrl-class.md))은 두 가지 유형의 알림 메시지를 보냅니다. 알림은 [WM_COMMAND](/windows/win32/menurc/wm-command) 메시지 형식으로 전송 됩니다.

애니메이션 컨트롤에서 클립 재생을 시작 하면 [ACN_START](/windows/win32/Controls/acn-start) 메시지가 전송 됩니다. 애니메이션 컨트롤이 클립 재생을 완료 하거나 중지 하면 [ACN_STOP](/windows/win32/Controls/acn-stop) 메시지가 전송 됩니다.

## <a name="see-also"></a>참고 항목

[CAnimateCtrl 사용](using-canimatectrl.md)<br/>
[컨트롤](controls-mfc.md)
