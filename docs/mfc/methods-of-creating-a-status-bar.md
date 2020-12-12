---
description: '자세히 알아보기: 상태 표시줄을 만드는 방법'
title: 상태 표시줄을 만드는 방법
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
ms.openlocfilehash: 06ae4002fdffb8ba90964b5ef488d0c115b3a0e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203057"
---
# <a name="methods-of-creating-a-status-bar"></a>상태 표시줄을 만드는 방법

MFC는 상태 표시줄을 만드는 두 가지 클래스를 제공 합니다. [Cstatusbar](reference/cstatusbar-class.md) and [CStatusBarCtrl](reference/cstatusbarctrl-class.md) (Windows 공용 컨트롤 API 래핑). `CStatusBar` 는 상태 표시줄 공용 컨트롤의 모든 기능을 제공 하 고, 메뉴와 도구 모음을 자동으로 조작 하며, 필요한 몇 가지 공용 컨트롤 설정 및 구조를 처리 합니다. 그러나 결과로 생성 되는 실행 파일은 일반적으로를 사용 하 여 만든 것 보다 큽니다 `CStatusBarCtrl` .

`CStatusBarCtrl` 일반적으로는 작은 실행 파일을 생성 하며, `CStatusBarCtrl` 상태 표시줄을 MFC 아키텍처에 통합 하지 않으려는 경우를 사용 하는 것이 좋습니다. 을 사용 하 `CStatusBarCtrl` 고 상태 표시줄을 mfc 아키텍처에 통합 하려는 경우 상태 표시줄 컨트롤 조작을 mfc에 전달 하려면 추가 주의를 기울여야 합니다. 이 통신은 어렵지 않습니다. 그러나를 사용 하는 경우에는 불필요 한 추가 작업이 있습니다 `CStatusBar` .

Visual C++는 상태 표시줄 공용 컨트롤을 활용 하는 두 가지 방법을 제공 합니다.

- 을 사용 하 여 상태 표시줄을 만든 `CStatusBar` 다음 [cstatusbar:: GetStatusBarCtrl](reference/cstatusbar-class.md#getstatusbarctrl) 를 호출 하 여 멤버 함수에 대 한 액세스 권한을 얻습니다 `CStatusBarCtrl` .

- [CStatusBarCtrl](reference/cstatusbarctrl-class.md)의 생성자를 사용 하 여 상태 표시줄을 만듭니다.

두 메서드 모두 상태 표시줄 컨트롤의 멤버 함수에 대 한 액세스를 제공 합니다. 를 호출 하면 `CStatusBar::GetStatusBarCtrl` `CStatusBarCtrl` 두 멤버 함수 집합을 사용할 수 있도록 개체에 대 한 참조를 반환 합니다. 을 사용 하 여 상태 표시줄을 생성 하 고 만드는 방법에 대 한 자세한 내용은 [Cstatusbar](reference/cstatusbar-class.md) 를 참조 하십시오 `CStatusBar` .

## <a name="see-also"></a>참고 항목

[CStatusBarCtrl 사용](using-cstatusbarctrl.md)<br/>
[컨트롤](controls-mfc.md)
