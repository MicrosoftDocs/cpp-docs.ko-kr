---
description: '자세한 정보: 메시지 보내기 및 받기'
title: 메시지 보내기 및 받기
ms.date: 11/04/2016
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
ms.openlocfilehash: 3a61346c51ce035f6fd5a53b8c329ef81154b089
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203213"
---
# <a name="message-sending-and-receiving"></a>메시지 보내기 및 받기

프로세스의 전송 부분과 프레임 워크가 응답 하는 방식을 고려 합니다.

대부분의 메시지는 사용자와 프로그램의 상호 작용으로 인해 발생 합니다. 메뉴 항목 또는 도구 모음 단추를 마우스 클릭 하거나 액셀러레이터 키 입력을 통해 명령이 생성 됩니다. 또한 사용자는 창을 이동 하거나 크기를 조정 하는 등의 방법으로 Windows 메시지를 생성 합니다. 다른 Windows 메시지는 프로그램 시작 또는 종료와 같은 이벤트가 발생 하는 경우 windows가 포커스를 얻거나 잃을 때 전송 됩니다. 컨트롤 알림 메시지는 대화 상자의 단추 또는 목록 상자 컨트롤과 같은 컨트롤을 사용 하 여 마우스를 클릭 하거나 다른 사용자 상호 작용을 통해 생성 됩니다.

`Run`클래스의 멤버 함수는 `CWinApp` 메시지를 검색 하 여 적절 한 창에 디스패치합니다. 대부분의 명령 메시지는 응용 프로그램의 주 프레임 창으로 전송 됩니다. `WindowProc`클래스 라이브러리에 의해 미리 정의 된는 메시지를 가져온 다음 받은 메시지의 범주에 따라 서로 다르게 라우팅합니다.

이제 프로세스의 수신 부분을 고려 합니다.

메시지의 초기 수신기는 window 개체 여야 합니다. Windows 메시지는 일반적으로 해당 창 개체에 의해 직접 처리 됩니다. 일반적으로 응용 프로그램의 주 프레임 창에서 시작 되는 명령 메시지는 명령 [라우팅](command-routing.md)에 설명 된 명령 대상 체인으로 라우팅됩니다.

메시지 또는 명령을 수신할 수 있는 각 개체에는 메시지 또는 명령을 해당 처리기의 이름과 쌍으로 포함 하는 자체 메시지 맵이 있습니다.

명령 대상 개체가 메시지나 명령을 받으면 메시지 맵에서 일치 항목을 검색 합니다. 메시지에 대 한 처리기를 찾으면 처리기를 호출 합니다. 메시지 맵을 검색 하는 방법에 대 한 자세한 내용은 [프레임 워크에서 메시지 맵을 검색 하는 방법](how-the-framework-searches-message-maps.md)을 참조 하세요. [프레임 워크의 그림 명령을](user-interface-objects-and-command-ids.md)다시 참조 합니다.

## <a name="see-also"></a>참고 항목

[프레임 워크가 처리기를 호출 하는 방법](how-the-framework-calls-a-handler.md)
