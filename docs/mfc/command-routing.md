---
title: 명령 라우팅 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecb836f8fee1efab7f5f925c6ec3ce0f470d666b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="command-routing"></a>명령 라우팅
명령 작업을 수행하는 경우 사용자의 역할은 메시지 맵을 사용하여 명령과 해당 처리기 함수를 연결하는 것으로 제한됩니다. 이 작업에는 속성 창을 사용합니다. 또한 사용자는 대부분의 명령 처리기를 작성해야 합니다.  
  
 일반적으로 Windows 메시지는 주 프레임 창에 전달되지만 명령 메시지는 나중에 다른 개체에 라우팅됩니다. 프레임워크는 명령 대상 개체의 표준 시퀀스를 통해 명령을 라우팅하고, 이 개체 중 하나에는 해당 명령에 대한 처리기가 포함됩니다. 각 명령 대상 개체는 자신의 메시지 맵을 확인하여 들어오는 메시지를 처리할 수 있는지 여부를 알아봅니다.  
  
 다른 명령 대상 클래스는 개별적으로 자신의 메시지 맵을 확인합니다. 일반적으로 클래스는 명령을 다른 특정 개체에 라우팅하여 해당 명령을 먼저 처리하도록 합니다. 모든 개체가 명령을 처리하지 못하는 경우 원래의 클래스가 자신의 메시지 맵을 확인합니다. 클래스에서 처리기를 제공할 수 없는 경우에는 해당 명령을 여러 명령 대상에 라우팅할 수 있습니다. 다음 [표준 명령 경로](#_core_standard_command_route) 표는 각 클래스가 이 시퀀스를 구성하는 방법을 보여 줍니다. 명령 대상이 명령을 라우팅하는 일반적인 순서는 다음과 같습니다.  
  
1.  현재 활성 상태인 자신의 자식 명령 대상 개체  
  
2.  자신  
  
3.  다른 명령 대상  
  
 비용이 많이 드는 처리기가 명령에 대 한 응답으로 수행 하려면이 라우팅 메커니즘 비교 하는 방법은 라우팅 비용은 낮은입니다. 사용자가 사용자 인터페이스 개체와 상호 작용할 경우에만 프레임워크가 명령을 생성한다는 점을 명심하세요.  
  
### <a name="_core_standard_command_route"></a> 표준 명령 경로  
  
|명령을 수신하는 개체 형식 이어야 합니다. 이어야 합니다.|자신 및 다른 명령 대상 개체가 명령을 처리하는 순서|  
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|  
|MDI 프레임 창(`CMDIFrameWnd`)|1.  활성 `CMDIChildWnd`<br />2.  이 프레임 창<br />3.  응용 프로그램 (`CWinApp` 개체)|  
|문서 프레임 창(`CFrameWnd`, `CMDIChildWnd`)|1.  활성 뷰<br />2.  이 프레임 창<br />3.  응용 프로그램 (`CWinApp` 개체)|  
|보기|1.  이 뷰<br />2.  뷰에 연결된 문서|  
|문서|1.  이 문서<br />2.  문서에 연결된 문서 템플릿|  
|대화 상자|1.  이 대화 상자<br />2.  대화 상자를 소유하는 창<br />3.  응용 프로그램 (`CWinApp` 개체)|  
  
 선행하는 테이블의 두 번째 열에 있는 번호가 매겨진 항목에서 다른 개체(예: 문서)를 지정한 경우 첫 번째 열에서 해당 항목을 참조합니다. 예를 들어, 두 번째 열에 뷰가 명령을 해당 문서에 전달하는 것으로 지정된 경우 이후의 라우팅을 확인하려면 첫 번째 열에 있는 "문서" 항목을 참조합니다.  
  
## <a name="see-also"></a>참고 항목  
 [프레임워크가 처리기를 호출하는 방법](../mfc/how-the-framework-calls-a-handler.md)

