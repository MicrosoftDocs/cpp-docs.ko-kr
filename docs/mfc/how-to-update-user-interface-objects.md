---
description: '자세한 정보: 방법: User-Interface 개체 업데이트'
title: '방법: 사용자 인터페이스 개체 업데이트'
ms.date: 11/04/2016
helpviewer_keywords:
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- user interface objects [MFC]
- update handlers [MFC]
- enabling UI elements [MFC]
- disabling menus [MFC]
- updating user-interface objects [MFC]
- disabling UI elements [MFC]
- commands [MFC], updating UI
- enabling menus [MFC]
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
ms.openlocfilehash: 32d7c033d03ba679fa295237c1c49c5060c731ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330169"
---
# <a name="how-to-update-user-interface-objects"></a>방법: 사용자 인터페이스 개체 업데이트

일반적으로 메뉴 항목 및 도구 모음 단추에는 두 개 이상의 상태가 있습니다. 예를 들어 현재 컨텍스트에서 사용할 수 없는 경우 메뉴 항목이 회색으로 표시 됩니다 (흐리게 표시 됨). 메뉴 항목을 선택 하거나 선택 취소할 수도 있습니다. 도구 모음 단추를 사용할 수 없는 경우에도 사용 하지 않도록 설정 하거나 선택할 수 있습니다.

프로그램 조건으로 이러한 항목의 상태를 업데이트 하는 사람은 논리적으로 변경 됩니다. 즉, 메뉴 항목이 문서와 같이 처리 되는 명령을 생성 하는 경우 문서에서 메뉴 항목을 업데이트 하는 것이 좋습니다. 문서에는 업데이트의 기반이 되는 정보가 포함 되어 있을 수 있습니다.

명령에 여러 사용자 인터페이스 개체 (메뉴 항목 및 도구 모음 단추)가 있는 경우 둘 다 동일한 처리기 함수로 라우팅됩니다. 이는 단일 위치의 모든 해당 사용자 인터페이스 개체에 대 한 사용자 인터페이스 업데이트 코드를 캡슐화 합니다.

프레임 워크는 사용자 인터페이스 개체를 자동으로 업데이트 하기 위한 편리한 인터페이스를 제공 합니다. 다른 방법으로 업데이트를 수행 하도록 선택할 수 있지만 제공 되는 인터페이스는 효율적이 고 사용 하기 쉽습니다.

다음 항목에서는 업데이트 처리기를 사용 하는 방법을 설명 합니다.

- [업데이트 처리기가 호출되는 시점](when-update-handlers-are-called.md)

- [ON_UPDATE_COMMAND_UI 매크로](on-update-command-ui-macro.md)

- [CCmdUI 클래스](the-ccmdui-class.md)

## <a name="see-also"></a>참고 항목

[메뉴](menus-mfc.md)
