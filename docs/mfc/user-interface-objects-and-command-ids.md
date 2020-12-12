---
description: User-Interface 개체 및 명령 Id에 대해 자세히 알아보세요.
title: 사용자 인터페이스 개체 및 명령 ID
ms.date: 11/19/2018
helpviewer_keywords:
- keyboard shortcuts, associating with IDs
- MFC, command routing
- toolbar controls [MFC], command ID
- menu items, associating with IDs
- user interface objects [MFC], associating with IDs
- command IDs, user interface objects
- command routing [MFC], MFC
- command handling [MFC], user-interface objects
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
ms.openlocfilehash: 142b72956e0a1b9e60ef48c7db325cd0ac822444
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263623"
---
# <a name="user-interface-objects-and-command-ids"></a>사용자 인터페이스 개체 및 명령 ID

메뉴 항목, 도구 모음 단추 및 액셀러레이터 키는 명령을 생성할 수 있는 "사용자 인터페이스 개체"입니다. 이러한 각 사용자 인터페이스 개체에는 ID가 있습니다. 개체 및 명령에 동일한 ID를 할당 하 여 사용자 인터페이스 개체를 명령과 연결 합니다. [메시지](../mfc/messages.md)에 설명 된 대로 명령은 특수 메시지로 구현 됩니다. 다음 그림 "프레임 워크의 명령"에서는 프레임 워크가 명령을 관리 하는 방법을 보여 줍니다. 사용자 인터페이스 개체가와 같은 명령을 생성 하면 `ID_EDIT_CLEAR_ALL` 응용 프로그램의 개체 중 하나가 명령을 처리 합니다. 아래 그림에서 문서 개체의 `OnEditClearAll` 함수는 문서의 메시지 맵을 통해 호출 됩니다.

![프레임워크의 명령](../mfc/media/vc385p1.gif "프레임워크의 명령") <br/>
프레임워크의 명령

"프레임 워크에서 명령 업데이트" 그림은 MFC가 메뉴 항목 및 도구 모음 단추와 같은 사용자 인터페이스 개체를 업데이트 하는 방법을 보여 줍니다. 도구 모음 단추의 경우 또는 유휴 루프 중에 메뉴가 축소 되기 전에 MFC는 업데이트 명령을 라우팅합니다. 아래 그림에서 문서 개체는 업데이트 명령 처리기를 호출 `OnUpdateEditClearAll` 하 여 사용자 인터페이스 개체를 활성화 하거나 비활성화 합니다.

![프레임 워크에서 명령 업데이트](../mfc/media/vc385p2.png "프레임워크에서 명령 업데이트") <br/>
Framework의 명령 업데이트

## <a name="see-also"></a>참고 항목

[프레임 워크의 메시지 및 명령](../mfc/messages-and-commands-in-the-framework.md)
