---
description: '자세한 정보: 메시지 범주'
title: 메시지 범주
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
ms.openlocfilehash: 66635101a8727e560d21d44546e2e12ace6f33ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203382"
---
# <a name="message-categories"></a>메시지 범주

처리기를 작성 하는 메시지 종류에는 세 가지 주요 범주가 있습니다.

1. Windows 메시지

   여기에는 WM_COMMAND를 제외 하 고 주로 **WM_** 접두사로 시작 하는 메시지가 포함 됩니다. Windows 메시지는 windows 및 뷰에서 처리 됩니다. 이러한 메시지에는 메시지 처리 방법을 결정 하는 데 사용 되는 매개 변수가 포함 되어 있는 경우가 많습니다.

1. 컨트롤 알림

   여기에는 컨트롤 및 다른 자식 창에서 부모 창으로의 알림 메시지 WM_COMMAND 포함 됩니다. 예를 들어 편집 컨트롤은 사용자가 편집 컨트롤에서 텍스트를 변경 했을 수 있는 작업을 수행 했을 때 EN_CHANGE 컨트롤 알림 코드를 포함 하는 WM_COMMAND 메시지를 해당 부모에 보냅니다. 메시지에 대 한 창의 처리기는 컨트롤의 텍스트를 검색 하는 것과 같이 적절 한 방법으로 알림 메시지에 응답 합니다.

   프레임 워크는 다른 **WM_** 메시지와 같이 제어 알림 메시지를 라우팅합니다. 그러나 한 가지 예외는 사용자가 단추를 클릭할 때 단추에서 전송 하는 BN_CLICKED 컨트롤 알림 메시지입니다. 이 메시지는 명령 메시지로 특수 하 게 처리 되 고 다른 명령과 같이 라우팅됩니다.

1. 명령 메시지

   여기에는 사용자 인터페이스 개체의 WM_COMMAND 알림 메시지 (메뉴, 도구 모음 단추 및 액셀러레이터 키)가 포함 됩니다. 프레임 워크는 다른 메시지와 다른 메시지를 처리 하며 [명령 대상](command-targets.md)에 설명 된 대로 더 많은 종류의 개체에서 처리할 수 있습니다.

## <a name="windows-messages-and-control-notification-messages"></a><a name="_core_windows_messages_and_control.2d.notification_messages"></a> Windows 메시지 및 Control-Notification 메시지

범주 1과 2의 메시지 (Windows 메시지 및 컨트롤 알림)는 windows: 클래스에서 파생 된 클래스의 개체에 의해 처리 됩니다 `CWnd` . 여기에는,,,, `CFrameWnd` `CMDIFrameWnd` `CMDIChildWnd` `CView` `CDialog` 및 이러한 기본 클래스에서 파생 된 고유한 클래스가 포함 됩니다. 이러한 개체는 `HWND` Windows 창에 대 한 핸들을 캡슐화 합니다.

## <a name="command-messages"></a><a name="_core_command_messages"></a> 명령 메시지

범주 3-commands의 메시지는 windows 및 보기 외에도 다양 한 개체 (문서, 문서 템플릿 및 응용 프로그램 개체 자체)로 처리할 수 있습니다. 명령이 특정 개체에 직접 영향을 주는 경우 해당 개체가 명령을 처리 하는 것이 좋습니다. 예를 들어 파일 메뉴의 열기 명령은 응용 프로그램과 논리적으로 연결 되어 있습니다. 응용 프로그램은 명령을 받을 때 지정 된 문서를 엽니다. 따라서 Open 명령의 처리기는 응용 프로그램 클래스의 멤버 함수입니다. 명령 및 개체를 개체로 라우팅하는 방법에 대 한 자세한 내용은 [프레임 워크가 처리기를 호출 하는 방법](how-the-framework-calls-a-handler.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[프레임 워크의 메시지 및 명령](messages-and-commands-in-the-framework.md)
