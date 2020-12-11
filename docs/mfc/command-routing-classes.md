---
description: '자세한 정보: 명령 라우팅 클래스'
title: 명령 라우팅 클래스
ms.date: 11/04/2016
f1_keywords:
- vc.classes.command
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
ms.openlocfilehash: d469b119eb7c42c1385f27a3d8df54f3fd47c73f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159975"
---
# <a name="command-routing-classes"></a>명령 라우팅 클래스

사용자가 마우스를 사용 하 여 메뉴 또는 컨트롤 막대 단추를 선택 하 여 응용 프로그램과 상호 작용할 때 응용 프로그램은 영향을 받는 사용자 인터페이스 개체의 메시지를 적절 한 명령 대상 개체로 보냅니다. 에서 파생 된 명령 대상 클래스 `CCmdTarget` 는 [CWinApp](reference/cwinapp-class.md), [CWnd](reference/cwnd-class.md), [cdoctemplate](reference/cdoctemplate-class.md), [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md)및 여기에서 파생 된 클래스를 포함 합니다. 프레임 워크는 응용 프로그램에서 현재 활성 상태인 가장 적절 한 개체에 의해 명령이 처리 될 수 있도록 자동 명령 라우팅을 지원 합니다.

클래스의 개체는 `CCmdUI` 명령 대상의[ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)(update command UI) 처리기에 전달 되어 특정 명령에 대 한 사용자 인터페이스의 상태를 업데이트할 수 있습니다. 예를 들어 메뉴 항목의 검사를 확인 하거나 제거할 수 있습니다. 개체의 멤버 함수를 호출 `CCmdUI` 하 여 UI 개체의 상태를 업데이트 합니다. 이 프로세스는 특정 명령과 연결 된 UI 개체가 메뉴 항목이 나 단추 인지 또는 둘 다 인지와 동일 합니다.

[CCmdTarget](reference/ccmdtarget-class.md)<br/>
메시지를 수신 하 고 응답할 수 있는 모든 개체 클래스의 기본 클래스로 사용 됩니다.

[CCmdUI](reference/ccmdui-class.md)<br/>
메뉴 항목이 나 컨트롤 막대 단추와 같은 사용자 인터페이스 개체를 업데이트 하기 위한 프로그래밍 인터페이스를 제공 합니다. 명령 대상 개체는이 개체를 사용 하 여 사용자 인터페이스 개체를 사용 하거나 사용 하지 않도록 설정 하거나 확인 하거나 지웁니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
