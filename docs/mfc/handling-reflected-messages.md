---
description: '자세히 알아보기: 리플렉션된 메시지 처리'
title: 리플렉션된 메시지 처리
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
ms.openlocfilehash: 4093c2feaa263470bc07df6feec32b12fea01542
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254913"
---
# <a name="handling-reflected-messages"></a>리플렉션된 메시지 처리

메시지 리플렉션을 사용 하면 컨트롤 자체 내에서 **WM_CTLCOLOR**, **WM_COMMAND** 및 **WM_NOTIFY** 와 같은 컨트롤에 대 한 메시지를 처리할 수 있습니다. 그러면 컨트롤의 독립성 및 이식성이 향상됩니다. 이 메커니즘은 Windows 공용 컨트롤 및 ActiveX 컨트롤(이전의 OLE 컨트롤)에서 작동합니다.

메시지 리플렉션을 사용하면 `CWnd` 파생 클래스를 보다 쉽게 재사용할 수 있습니다. 메시지 리플렉션은 특수 **ON_XXX_REFLECT** 메시지 맵 항목을 사용 하 여 [CWnd:: onchildnotify](reference/cwnd-class.md#onchildnotify)를 통해 작동 합니다 (예: **ON_CTLCOLOR_REFLECT** 및 **ON_CONTROL_REFLECT**). [기술 참고 62](tn062-message-reflection-for-windows-controls.md) 는 메시지 리플렉션에 대해 자세히 설명 합니다.

## <a name="what-do-you-want-to-do"></a>뭘 하고 싶으세요

- [메시지 리플렉션에 대해 자세히 알아보기](tn062-message-reflection-for-windows-controls.md)

- [공용 컨트롤을 위한 메시지 리플렉션 구현](tn062-message-reflection-for-windows-controls.md)

- [ActiveX 컨트롤을 위한 메시지 리플렉션 구현](mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>참고 항목

[메시지 처리기 함수 선언](declaring-message-handler-functions.md)
