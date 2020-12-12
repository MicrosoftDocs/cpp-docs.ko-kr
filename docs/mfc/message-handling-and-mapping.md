---
description: '자세한 정보: 메시지 처리 및 매핑'
title: 메시지 처리 및 매핑
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
ms.openlocfilehash: 50a55f4718b47054690325e882177fa9acad2f46
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203200"
---
# <a name="message-handling-and-mapping"></a>메시지 처리 및 매핑

이 문서에서는 MFC 프레임 워크에서 메시지 및 명령을 처리 하는 방법과이를 처리기 함수에 연결 하는 방법을 설명 합니다.

Windows 용 기존 프로그램에서 Windows 메시지는 창 프로시저의 긴 스위치 문에서 처리 됩니다. 대신 MFC에서는 [메시지 맵을](message-categories.md) 사용 하 여 직접 메시지를 고유한 클래스 멤버 함수에 매핑합니다. 메시지 맵은이 목적을 위해 가상 함수 보다 더 효율적 이며 응용 프로그램, 문서, 보기 등의 가장 적합 한 c + + 개체에서 메시지를 처리할 수 있도록 합니다. 단일 메시지 또는 메시지, 명령 Id 또는 컨트롤 Id의 범위를 매핑할 수 있습니다.

일반적으로 메뉴, 도구 모음 단추 또는 액셀러레이터에 의해 생성 되는 WM_COMMAND 메시지는 메시지 맵 메커니즘도 사용 합니다. MFC는 프로그램의 응용 프로그램, 프레임 창, 뷰 및 활성 문서 간에 명령 메시지의 표준 [라우팅을](command-routing.md) 정의 합니다. 필요한 경우이 라우팅을 재정의할 수 있습니다.

메시지 맵은 사용자 인터페이스 개체 (예: 메뉴 및 도구 모음 단추)를 업데이트 하 고 현재 컨텍스트에 맞게 사용 하거나 사용 하지 않도록 설정 하는 방법도 제공 합니다.

Windows의 메시지 및 메시지 큐에 대 한 일반적인 내용은 Windows SDK [메시지 및](/windows/win32/winmsg/messages-and-message-queues) 메시지 큐를 참조 하십시오.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [프레임 워크의 메시지 및 명령](messages-and-commands-in-the-framework.md)

- [프레임 워크에서 메시지 처리기를 호출 하는 방법](how-the-framework-calls-a-handler.md)

- [프레임 워크가 메시지 맵을 검색 하는 방법](how-the-framework-searches-message-maps.md)

- [메시지 처리기 함수 선언](declaring-message-handler-functions.md)

- [함수에 메시지 매핑](reference/mapping-messages-to-functions.md)

- [상태 표시줄에 명령 정보를 표시 하는 방법](how-to-display-command-information-in-the-status-bar.md)

- [사용자 인터페이스 개체의 동적 업데이트](how-to-update-user-interface-objects.md)

- [방법: 템플릿 클래스에 대 한 메시지 맵 만들기](how-to-create-a-message-map-for-a-template-class.md)

## <a name="see-also"></a>참고 항목

[개념](mfc-concepts.md)<br/>
[일반 MFC 항목](general-mfc-topics.md)<br/>
[CWnd 클래스](reference/cwnd-class.md)<br/>
[CCmdTarget 클래스](reference/ccmdtarget-class.md)
