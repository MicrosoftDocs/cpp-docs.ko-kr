---
title: 명령 대상 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cbcfa1042a8430c704bad93e4bc0ce5655b5921
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="command-targets"></a>명령 대상
그림 [프레임 워크의 명령](../mfc/user-interface-objects-and-command-ids.md) 메뉴 항목 및 개체를 클릭할 때 발생 하는 명령을 수행 하는 프레임 워크를 호출 하는 처리기 함수는 사용자 인터페이스 개체 간의 연결을 보여 줍니다.  
  
 Windows 명령 메시지는 메시지에 대 한 처리기가 호출 됩니다는 창으로 직접 없는 메시지를 보냅니다. 그러나이 프레임 워크 명령을 후보 개체 수를 라우팅하고-"명령 대상" 이라고-중 하나는 일반적으로 명령에 대 한 처리기를 호출 합니다. 처리기 함수 명령과 표준 Windows 메시지에 대 한 동일한 방식으로 작동 하지만 호출 되는 메커니즘 서로에 설명 된 대로 [프레임 워크가 처리기를 호출 하는 방법](../mfc/how-the-framework-calls-a-handler.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [프레임워크의 메시지 및 명령](../mfc/messages-and-commands-in-the-framework.md)

