---
description: '자세한 정보: MDI 탭 그룹'
title: MDI 탭 그룹
ms.date: 11/04/2016
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
ms.openlocfilehash: b859445c5cc1e14f19ec91c31b4d618237cfb9a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280770"
---
# <a name="mdi-tabbed-groups"></a>MDI 탭 그룹

Mdi (다중 문서 인터페이스) 탭 그룹 기능을 사용 하면 mdi (다중 문서 인터페이스)를 사용 하 여 mdi 클라이언트 영역에서 하나 이상의 탭 창 (또는 탭 *그룹* 이라고 하는 탭 창의 그룹)을 표시할 수 있습니다. 탭 창은 세로 또는 가로로 정렬할 수 있습니다. 애플리케이션이 두 개 이상의 MDI 탭 그룹을 호스팅할 경우, 그룹이 분할자로 구분됩니다.

## <a name="features"></a>기능

다음은 MDI 탭 그룹의 기능입니다.

- 애플리케이션은 탭 창을 동적으로 만들 수 있습니다.

- 애플리케이션은 가로 또는 세로로 탭 창을 정렬할 수 있습니다.

- 탭 창의 그룹은 분할자로 구분됩니다. 분할자를 사용해서 탭 그룹의 크기를 조정할 수 있습니다.

- 그룹 간에 개별 탭을 끌 수 있습니다.

- 개별 탭을 끌어서 새 그룹을 만들 수 있습니다.

- 바로 가기 메뉴를 사용해서 새 그룹을 만들거나 탭을 이동할 수 있습니다.

- 애플리케이션은 탭 창의 레이아웃을 저장하고 로드할 수 있습니다.

- 애플리케이션은 MDI 문서 목록을 저장하고 로드할 수 있습니다.

- 애플리케이션은 개별 탭 그룹에 액세스하고 해당 매개 변수를 수정할 수 있습니다.

### <a name="using-mdi-tabbed-groups"></a>MDI 탭 그룹 사용

다음은 MDI 탭 그룹에서 일반적으로 수행되는 작업입니다.

- 주 프레임 창에 대해 MDI 탭 그룹을 사용 하도록 설정 하려면 [CMDIFrameWndEx:: enablemditabbedgroups 메서드에](reference/cmdiframewndex-class.md#enablemditabbedgroups)를 호출 합니다. 이 메서드의 두 번째 매개 변수는 `CMDITabInfo` 클래스의 인스턴스입니다. `CMDIFrameWndEx::EnableMDITabbedGroups`를 호출하기 전에 기본 매개 변수를 사용하거나 이를 수정할 수 있습니다.

- 런타임에 MDI 탭 그룹의 속성을 수정하려면 `CMDITabInfo` 개체를 만들거나 수정하고 `CMDIFrameWndEx::EnableMDITabbedGroups`를 다시 호출합니다.

- MDI 탭 창 목록을 가져오려면 `CMDIFrameWndEx::GetMDITabGroups`를 호출합니다.

- 활성 탭 그룹 옆에 새 MDI 탭 그룹을 만들려면 `CMDIFrameWndEx::MDITabNewGroup`을 호출합니다.

- 탭 그룹의 이전 또는 다음 창에서 입력 포커스를 전환하려면 `CMDIFrameWndEx::MDITabMoveToNextGroup`을 호출합니다.

- 창이 MDI 탭 그룹의 멤버인지 여부를 확인하려면 `CMDIFrameWndEx::IsMemberOfMDITabGroup`을 호출합니다.

- 메인 프레임 창에 대해 MDI 탭 또는 MDI 탭 그룹이 설정되었는지 여부를 확인하려면 `CMDIFrameWndEx::AreMDITabs`를 호출합니다. MDI 탭 그룹이 설정되었는지 여부만 확인하려면 `CMDIFrameWndEx::IsMDITabbedGroup`을 호출합니다.

- 사용자가 탭을 클릭하거나 이를 다른 MDI 탭 그룹으로 끌어갈 때 바로 가기 메뉴를 표시하려면 `CMDIFrameWndEx::OnShowMDITabContextMenu` 파생 클래스에서 `CMDIFrameWndEx`를 재정의합니다. 이 메서드를 구현하지 않으면 애플리케이션에 바로 가기 메뉴가 표시되지 않습니다.

- 애플리케이션에서 MDI 탭 그룹의 레이아웃을 저장하려면 `CMDIFrameWndEx::SaveMDIState`를 호출합니다. 이전에 저장된 MDI 탭 그룹 프로필을 로드하려면 `CMDIFrameWndEx::LoadMDIState`를 호출합니다. 또한 이러한 메서드를 호출해서 열려 있는 문서의 목록을 MDI 애플리케이션에서 로드하거나 저장할 수 있습니다. MDI 상태를 저장 및 로드 하는 방법에 대 한 자세한 내용은 [CMDIFrameWndEx:: LoadMDIState](reference/cmdiframewndex-class.md#loadmdistate)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[사용자 인터페이스 요소](user-interface-elements-mfc.md)<br/>
[CMDIFrameWndEx 클래스](reference/cmdiframewndex-class.md)<br/>
[CMDIChildWndEx 클래스](reference/cmdichildwndex-class.md)<br/>
[CMDITabInfo 클래스](reference/cmditabinfo-class.md)
