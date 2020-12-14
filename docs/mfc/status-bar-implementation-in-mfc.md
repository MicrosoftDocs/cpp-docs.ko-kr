---
description: '자세히 알아보기: MFC의 상태 표시줄 구현'
title: MFC의 상태 표시줄 구현
ms.date: 11/19/2018
f1_keywords:
- COldStatusBar
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
ms.openlocfilehash: d42f8b4bf6ae72cf8eb4a12d1f5eafb8603c5e1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216758"
---
# <a name="status-bar-implementation-in-mfc"></a>MFC의 상태 표시줄 구현

[Cstatusbar](../mfc/reference/cstatusbar-class.md) 개체는 텍스트 출력 창 행이 있는 컨트롤 막대입니다. 출력 창은 일반적으로 메시지 선과 상태 표시기로 사용 됩니다. 예를 들어 선택한 메뉴 명령을 간략하게 설명 하는 메뉴 도움말 메시지 줄과 스크롤 잠금, NUM LOCK 및 기타 키의 상태를 표시 하는 표시기가 있습니다.

MFC 버전 4.0을 사용 하 여 상태 표시줄은 상태 표시줄 공용 컨트롤을 캡슐화 하는 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)클래스를 사용 하 여 구현 됩니다. 이전 버전과의 호환성을 위해 MFC는 이전의 상태 표시줄 구현을 클래스에서 유지 합니다 `COldStatusBar` . 이전 버전의 MFC에 대 한 설명서는 아래에 설명 되어 `COldStatusBar` `CStatusBar` 있습니다.

MFC 4.0의 새로운 멤버인 [Cstatusbar:: GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl)를 사용 하면 상태 표시줄 사용자 지정 및 추가 기능에 대 한 Windows 공용 컨트롤의 지원을 활용할 수 있습니다. `CStatusBar` 멤버 함수는 Windows 공용 컨트롤의 기능을 대부분 제공 합니다. 그러나를 호출할 때 상태 `GetStatusBarCtrl` 표시줄의 특성을 더 많이 제공할 수 있습니다. 를 호출 하는 경우 `GetStatusBarCtrl` 개체에 대 한 참조를 반환 `CStatusBarCtrl` 합니다. 이 참조를 사용 하 여 상태 표시줄 컨트롤을 조작할 수 있습니다.

다음 그림에서는 여러 지표를 표시 하는 상태 표시줄을 보여 줍니다.

![상태 표시줄](../mfc/media/vc37dy1.gif "상태 표시줄") <br/>
상태 표시줄

도구 모음과 마찬가지로 상태 표시줄 개체는 부모 프레임 창에 포함 되 고 프레임 창이 생성 될 때 자동으로 생성 됩니다. 모든 컨트롤 막대와 같은 상태 표시줄은 부모 프레임이 제거 될 때 자동으로 삭제 됩니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [상태 표시줄 창의 텍스트 업데이트](../mfc/updating-the-text-of-a-status-bar-pane.md)

- MFC 클래스 [Cstatusbar](../mfc/reference/cstatusbar-class.md) 및 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)

- [컨트롤 막대](../mfc/control-bars.md)

- [대화 상자 모음](../mfc/dialog-bars.md)

- [도구 모음 (MFC 도구 모음 구현)](../mfc/mfc-toolbar-implementation.md)

## <a name="see-also"></a>참고 항목

[상태 표시줄](../mfc/status-bars.md)
