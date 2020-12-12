---
description: '자세한 정보: 프레임 워크에서 코드를 호출 하는 방법'
title: 프레임워크가 코드를 호출하는 방법
ms.date: 11/04/2016
helpviewer_keywords:
- control flow [MFC], MFC framework and your code
- events [MFC], command routing in MFC
- command routing [MFC], framework
- command handling [MFC], calling handlers and code in MFC
- events [MFC], event-driven programming
- MFC, calling code from
- MFC, calling code
- application-specific events [MFC]
- command routing [MFC], MFC
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
ms.openlocfilehash: eebc431d8ba4d0edf7eddfe113d6f6559087be70
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290377"
---
# <a name="how-the-framework-calls-your-code"></a>프레임워크가 코드를 호출하는 방법

소스 코드와 MFC 프레임 워크의 코드 간 관계를 이해 하는 것이 중요 합니다. 응용 프로그램이 실행 될 때 대부분의 제어 흐름은 프레임 워크의 코드에 있습니다. 프레임 워크는 사용자가 명령을 선택 하 고 뷰에서 데이터를 편집할 때 Windows에서 메시지를 가져오는 메시지 루프를 관리 합니다. 프레임 워크가 자체적으로 처리할 수 있는 이벤트는 코드에 전혀 의존 하지 않습니다. 예를 들어 프레임 워크는 windows를 닫는 방법 및 사용자 명령에 응답 하 여 응용 프로그램을 종료 하는 방법을 알고 있습니다. 이러한 작업을 처리할 때 프레임 워크는 메시지 처리기와 c + + 가상 함수를 사용 하 여 이러한 이벤트에도 응답할 수 있는 기회를 제공 합니다. 그러나 코드가 제어 되지 않습니다. 프레임 워크는입니다.

프레임 워크는 응용 프로그램 관련 이벤트에 대 한 코드를 호출 합니다. 예를 들어 사용자가 메뉴 명령을 선택 하면 프레임 워크는 현재 보기 및 프레임 창, 보기와 연결 된 문서, 문서의 문서 템플릿 및 응용 프로그램 개체와 같은 c + + 개체의 시퀀스를 따라 명령을 라우팅합니다. 이러한 개체 중 하나가 명령을 처리할 수 있는 경우 적절 한 메시지 처리기 함수를 호출 합니다. 지정 된 명령에 대해 호출 된 코드는 자신의 코드 일 수도 있고 프레임 워크의 일 수도 있습니다.

이러한 정렬은 Windows 또는 이벤트 구동 프로그래밍에 대 한 기존의 프로그래밍에 익숙한 프로그래머에 게 매우 익숙할 것입니다.

관련 항목에서는 응용 프로그램을 초기화 하 고 실행할 때 프레임 워크에서 수행 하는 작업을 읽고 응용 프로그램이 종료 되 면 정리 합니다. 또한 코드를 작성 하는 코드의 위치를 이해 하 게 됩니다.

자세한 내용은 [클래스 CWinApp: 응용 프로그램 클래스](cwinapp-the-application-class.md) 및 [문서 템플릿 및 문서/뷰 만들기 프로세스](document-templates-and-the-document-view-creation-process.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[프레임 워크를 기반으로 빌드](building-on-the-framework.md)
