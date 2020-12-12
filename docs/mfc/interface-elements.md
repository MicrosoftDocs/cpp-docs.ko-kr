---
description: '자세한 정보: 인터페이스 요소'
title: 인터페이스 요소
ms.date: 11/19/2018
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
ms.openlocfilehash: a0aa762455f6bfe97d371244682c66dbd141a761
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228055"
---
# <a name="interface-elements"></a>인터페이스 요소

이 문서에서는 Visual Studio 2008 s p 1에 도입 된 인터페이스 요소에 대해 설명 하 고 이전 라이브러리 버전과의 차이점에 대해서도 설명 합니다.

다음 그림에서는 새 인터페이스 요소를 사용 하 여 빌드된 응용 프로그램을 보여 줍니다.

![MFC 기능 팩 예제 응용 프로그램](../mfc/media/mfc_featurepack.png "MFC 기능 팩 예제 응용 프로그램")

## <a name="window-docking"></a>창 도킹

창 도킹 기능은 Visual Studio 그래픽 사용자 인터페이스에서 사용 하는 창 도킹과 비슷합니다.

## <a name="control-bars-are-now-panes"></a>이제 컨트롤 막대는 창입니다.

이제 컨트롤 막대를 창 이라고 하며 [Cbasepane 클래스](reference/cbasepane-class.md)에서 파생 됩니다. 이전 버전의 MFC에서 컨트롤 막대의 기본 클래스는 `CControlBar` 입니다.

응용 프로그램 주 프레임 창은 일반적으로 [CFrameWndEx 클래스](reference/cframewndex-class.md) 또는 [CMDIFrameWndEx 클래스로](reference/cmdiframewndex-class.md)표현 됩니다. 주 프레임을 *dock 사이트* 라고 합니다. 창에는 도킹 사이트, 도크 막대 또는 미니 프레임 창의 세 가지 부모 유형 중 하나를 사용할 수 있습니다.

크기를 조정 하거나 크기를 조정할 수 있는 두 가지 창 유형이 있습니다. 상태 표시줄 및 도구 모음과 같은 크기 조정 가능한 창은 분할자 또는 슬라이더를 사용 하 여 크기를 조정할 수 있습니다. 크기를 조정할 수 있는 창에서 컨테이너를 형성할 수 있습니다. 한 창은 다른 창에 도킹 하 고 둘 사이의 분할자를 만들 수 있습니다. 그러나 크기 조정 가능한 창에는 도킹할 수 있습니다.

응용 프로그램에서 크기를 조정할 수 없는 창을 사용 하는 경우 [Cpane 클래스](reference/cpane-class.md)에서 파생 합니다.  응용 프로그램에서 크기 조정 가능한 창을 사용 하는 경우 [CDockablePane 클래스](reference/cdockablepane-class.md) 에서 파생 합니다.

## <a name="dock-site"></a>사이트 도킹

Dock 사이트 (또는 주 프레임 창)는 응용 프로그램의 모든 창 및 미니 프레임 창을 소유 합니다. Dock 사이트는 [CDockingManager](reference/cdockingmanager-class.md) 멤버를 포함 합니다. 이 구성원은 dock 사이트에 속하는 모든 창의 목록을 유지 관리 합니다. 도킹 사이트의 외부 가장자리에 생성 된 창이 목록의 시작 부분에 배치 되도록 목록이 정렬 됩니다. 프레임 워크는 도크 사이트를 다시 그리면이 목록을 반복 하 고 dock 사이트의 현재 경계 사각형을 포함 하도록 각 창의 레이아웃을 조정 합니다. `AdjustDockingLayout` `RecalcLayout` 도킹 레이아웃을 조정 해야 하는 경우 또는를 호출할 수 있으며, 프레임 워크는이 호출을 도킹 관리자로 리디렉션합니다.

## <a name="dock-bars"></a>도킹 막대

각 주 프레임 창은 테두리를 따라 *도크 막대* 를 배치할 수 있습니다. 도크 막대는 [CDockSite 클래스](reference/cdocksite-class.md)에 속하는 창입니다. 도킹 막대는 도구 모음과 같은 [Cpane](reference/cpane-class.md)에서 파생 된 개체를 허용할 수 있습니다. 주 프레임 창이 초기화 될 때 도킹 막대를 만들려면를 호출 `EnableDocking` 합니다. 자동 숨기기 막대를 사용 하도록 설정 하려면를 호출 `EnableAutoHideBars` 합니다. `EnableAutoHideBars`[CAutoHideDockSite](reference/cautohidedocksite-class.md) 개체를 만들고 각 도크 막대 옆에 배치 합니다.

각 도크 막대는 도크 행으로 나뉩니다. Dock 행은 [CDockingPanesRow 클래스](reference/cdockingpanesrow-class.md)에 의해 표시 됩니다. 각 도크 행에는 도구 모음 목록이 포함 됩니다. 사용자가 도구 모음을 도킹 하거나 동일한 도킹 막대 내에서 도구 모음을 한 행에서 다른 행으로 이동 하는 경우 프레임 워크는 새 행을 만들고 그에 따라 도킹 막대의 크기를 조정 하거나 기존 행에 도구 모음을 배치 합니다.

## <a name="mini-frame-windows"></a>미니 프레임 창

부동 창은 미니 프레임 창에 상주 합니다. 미니 프레임 창은 [Cmditabinfo 클래스](reference/cmditabinfo-class.md) (창 하나만 포함할 수 있음)와 [CMultiPaneFrameWnd 클래스](reference/cmultipaneframewnd-class.md) (여러 개의 창을 포함할 수 있음)의 두 클래스로 표현 됩니다. 코드에서 창을 부동 하려면 [Cbasepane:: FloatPane](reference/cbasepane-class.md#floatpane)를 호출 합니다. 창 float 후 프레임 워크는 자동으로 미니 프레임 창을 만들며 미니 프레임 창은 부동 창의 부모가 됩니다. 부동 창이 도킹 될 때 프레임 워크는 부모를 다시 설정 하 고 부동 창은 도킹 막대 (도구 모음) 또는 도크 사이트 (크기 조정 가능한 창의 경우)가 됩니다.

## <a name="pane-dividers"></a>창 분할자

창 구분선 (슬라이더 또는 분할자 라고도 합니다)은 [CPaneDivider 클래스로](reference/cpanedivider-class.md)표현 됩니다. 사용자가 창을 도킹 하면 창이 도킹 사이트 또는 다른 창에 도킹 되어 있는지 여부에 관계 없이 프레임 워크는 창 구분선을 만듭니다. 창이 도킹 사이트에 도킹 되 면 창 구분선을 *기본 창 구분선* 이라고 합니다. 기본 창 구분선은 dock 사이트에 있는 모든 도킹 창의 레이아웃을 담당 합니다. Dock 관리자는 기본 창 구분선 및 창 목록의 목록을 유지 관리 합니다. 도킹 관리자는 모든 도킹 창의 레이아웃을 담당 합니다.

## <a name="containers"></a>컨테이너

크기 조정 가능한 모든 창이 서로 도킹 된 경우 컨테이너에서 유지 관리 됩니다. 컨테이너는 [CPaneContainer 클래스로](reference/cpanecontainer-class.md)나타냅니다. 각 컨테이너에는 왼쪽 창, 오른쪽 창, 왼쪽 하위 컨테이너, 오른쪽 하위 컨테이너 및 왼쪽과 오른쪽 부분 사이의 분할자에 대 한 포인터가 있습니다. *왼쪽* 및 *오른쪽* 은 물리적 측면을 참조 하지 않고 트리 구조의 분기를 식별 합니다. 이러한 방식으로 창 및 분할자 트리를 작성 하 여 크기를 조정할 수 있는 복잡 한 창 레이아웃을 달성할 수 있습니다. `CPaneContainer`클래스는 컨테이너 트리를 유지 관리 합니다. 또한이 트리에 있는 창의 두 목록과 슬라이더를 유지 관리 합니다. 창 컨테이너 관리자는 일반적으로 기본 슬라이더와 여러 창을 포함 하는 미니 프레임 창에 포함 되어 있습니다.

## <a name="auto-hide-control-bars"></a>컨트롤 막대 자동 숨기기

기본적으로는 각각 `CDockablePane` 자동 숨기기 기능을 지원 합니다. 사용자가의 캡션에 있는 고정 단추를 클릭 하면 `CDockablePane` 프레임 워크에서 창을 자동 숨기기 모드로 전환 합니다. 클릭을 처리 하기 위해 프레임 워크는 개체와 연결 된 [CMFCAutoHideBar 클래스](reference/cmfcautohidebar-class.md) 및 [CMFCAutoHideButton 클래스](reference/cmfcautohidebutton-class.md) 를 만듭니다 `CMFCAutoHideBar` . 프레임 워크는 새를 `CMFCAutoHideBar` [CAutoHideDockSite](reference/cautohidedocksite-class.md)에 넣습니다. 또한 프레임 워크는를 `CMFCAutoHideButton` 도구 모음에 연결 합니다. [CDockingManager 클래스](reference/cdockingmanager-class.md) 는를 유지 관리 합니다 `CDockablePane` .

## <a name="tabbed-control-bars-and-outlook-bars"></a>탭 컨트롤 막대 및 Outlook 표시줄

[CMFCBaseTabCtrl 클래스](reference/cmfcbasetabctrl-class.md) 는 분리 가능한 탭을 사용 하 여 탭 창의 기본 기능을 구현 합니다. 개체를 사용 하려면 `CMFCBaseTabCtrl` 응용 프로그램에서 [CBaseTabbedPane 클래스](reference/cbasetabbedpane-class.md) 를 초기화 합니다. `CBaseTabbedPane` 는에서 파생 되 `CDockablePane` 고 개체에 대 한 포인터를 유지 `CMFCBaseTabCtrl` 합니다. 사용자는를 `CBaseTabbedPane` 사용 하 여 탭 컨트롤 막대를 도킹 하 고 크기를 조정할 수 있습니다. [CDockablePane:: AttachToTabWnd](reference/cdockablepane-class.md#attachtotabwnd) 를 사용 하 여 도킹 및 탭 된 컨트롤 막대를 동적으로 만듭니다.

Outlook bar 컨트롤은 탭 막대를 기반으로 합니다. [CMFCOutlookBar 클래스](reference/cmfcoutlookbar-class.md) 는에서 파생 됩니다 `CBaseTabbedPane` . Outlook bar를 사용 하는 방법에 대 한 자세한 내용은 [CMFCOutlookBar 클래스](reference/cmfcoutlookbar-class.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[개념](mfc-concepts.md)
