---
description: '자세한 정보: 명령 대상'
title: 명령 대상
ms.date: 11/04/2016
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
ms.openlocfilehash: b7be03282400c2d3a0dcf5eb0d24a0b06456ebca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206255"
---
# <a name="command-targets"></a>명령 대상

[프레임 워크](user-interface-objects-and-command-ids.md) 의 그림 명령은 사용자 인터페이스 개체 (예: 메뉴 항목)와 프레임 워크가 개체가 클릭 될 때 결과 명령을 수행 하기 위해 호출 하는 처리기 함수를 연결 하는 것을 보여 줍니다.

Windows에서는 명령 메시지가 아닌 메시지를 메시지 처리기가 있는 창에 직접 보냅니다. 그러나이 프레임 워크는 명령에 대 한 처리기를 일반적으로 호출 하는 여러 후보 개체 ("명령 대상" 이라고 함)로 명령을 라우팅합니다. 처리기 함수는 명령 및 표준 Windows 메시지에 대해 동일한 방식으로 작동 하지만,이 함수를 호출 하는 메커니즘은 [프레임 워크가 처리기를 호출 하는 방법](how-the-framework-calls-a-handler.md)에 설명 된 대로 서로 다릅니다.

## <a name="see-also"></a>참고 항목

[프레임 워크의 메시지 및 명령](messages-and-commands-in-the-framework.md)
