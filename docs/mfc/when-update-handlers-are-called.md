---
description: 업데이트 처리기가 호출 되는 경우에 대 한 자세한 정보
title: 업데이트 처리기가 호출되는 시점
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- command routing [MFC], update commands
- toolbar buttons [MFC], enabling
- disabling toolbar buttons
- menus [MFC], initializing
- update handlers [MFC]
- disabling menu items
- toolbars [MFC], updating
- menus [MFC], updating as context changes
- toolbar controls [MFC], updated during OnIdle method [MFC]
- menu items, enabling
- command routing [MFC], update handlers
- update handlers, calling
ms.assetid: 7359f6b1-4669-477d-bd99-690affed08d9
ms.openlocfilehash: ee5d402eea4121c9ceb4bcbd48e752549c55b1c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297176"
---
# <a name="when-update-handlers-are-called"></a>업데이트 처리기가 호출되는 시점

사용자가 파일 메뉴에서 마우스를 클릭 하 여 WM_INITMENUPOPUP 메시지를 생성 한다고 가정 합니다. 프레임 워크의 업데이트 메커니즘은 메뉴가 축소 되기 전에 파일 메뉴의 모든 항목을 전체적으로 업데이트 하므로 사용자가 해당 항목을 볼 수 있습니다.

이렇게 하기 위해 프레임 워크는 표준 명령 라우팅을 따라 팝업 메뉴의 모든 메뉴 항목에 대 한 업데이트 명령을 라우팅합니다. 라우팅의 명령 대상에는 update 명령과 적절 한 메시지 맵 항목 (양식)을 비교 하 `ON_UPDATE_COMMAND_UI` 고 "업데이트 처리기" 함수를 호출 하 여 메뉴 항목을 업데이트할 수 있는 기회가 있습니다. 따라서 6 개의 메뉴 항목이 있는 메뉴의 경우 6 개의 업데이트 명령이 전송 됩니다. 메뉴 항목의 명령 ID에 대 한 업데이트 처리기가 있는 경우이를 호출 하 여 업데이트를 수행 합니다. 그렇지 않은 경우 프레임 워크는 해당 명령 ID에 대 한 처리기가 있는지 확인 하 고 적절 하 게 메뉴 항목을 사용 하거나 사용 하지 않도록 설정 합니다.

프레임 워크에서 `ON_UPDATE_COMMAND_UI` 명령 라우팅 중에 항목을 찾을 수 없는 경우 동일한 명령 ID를 사용 하는 항목이 있으면 자동으로 사용자 인터페이스 개체를 사용 하도록 설정 합니다 `ON_COMMAND` . 그렇지 않으면 사용자 인터페이스 개체를 사용 하지 않도록 설정 합니다. 따라서 사용자 인터페이스 개체를 사용 하도록 설정 하려면 개체가 생성 하거나 업데이트 처리기를 제공 하는 명령에 대 한 처리기를 제공 합니다. [사용자 인터페이스 개체 및 명령 id](../mfc/user-interface-objects-and-command-ids.md)항목의 그림을 참조 하세요.

사용자 인터페이스 개체의 기본 비활성화를 사용 하지 않도록 설정할 수 있습니다. 자세한 내용은 [](../mfc/reference/cframewnd-class.md#m_bautomenuenable) `CFrameWnd` *MFC 참조* 에서 클래스의 m_bAutoMenuEnable 멤버를 참조 하십시오.

메뉴 초기화는 응용 프로그램이 WM_INITMENUPOPUP 메시지를 받을 때 발생 하는 프레임 워크에서 자동으로 수행 됩니다. 유휴 루프에서 프레임 워크는 메뉴에 대해 수행 하는 것과 거의 동일한 방식으로 명령 라우팅을 검색 하 여 단추 업데이트 처리기를 검색 합니다.

## <a name="see-also"></a>참고 항목

[방법: User-Interface 개체 업데이트](../mfc/how-to-update-user-interface-objects.md)
