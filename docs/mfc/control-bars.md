---
description: '자세히 알아보기: 컨트롤 막대'
title: 컨트롤 막대
ms.date: 11/04/2016
helpviewer_keywords:
- command bars [MFC], types of
- toolbars [MFC], control bars
- control bars [MFC]
- MFC, control bars
- control bars [MFC], types of
- CDialogBar class [MFC], control bars
- status bars [MFC], control bars
- CControlBar class [MFC], MFC control bars
- dialog bars [MFC], control bars
- CToolBar class [MFC], control bars
- CStatusBar class [MFC], control bars
ms.assetid: 31831910-3d23-4d70-9e71-03cc02f01ec4
ms.openlocfilehash: 985201b2c09c4d60996e9ee64b2507fe1593e5ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310150"
---
# <a name="control-bars"></a>컨트롤 막대

"컨트롤 막대"는 도구 모음, 상태 표시줄 및 대화 상자 모음의 일반 이름입니다. MFC 클래스 `CToolBar` ,,, `CStatusBar` 및는 `CDialogBar` `COleResizeBar` `CReBar` 공통 기능을 구현 하는 [ccontrolbar](reference/ccontrolbar-class.md)클래스에서 파생 됩니다.

컨트롤 막대는 사용자가 옵션을 선택 하거나 명령을 실행 하거나 프로그램 정보를 얻을 수 있는 컨트롤 행을 표시 하는 창입니다. 컨트롤 막대의 형식에는 도구 모음, 대화 상자 표시줄 및 상태 표시줄이 있습니다.

- [CToolBar](reference/ctoolbar-class.md) 클래스의 도구 모음

- 상태 표시줄, 클래스 [Cstatusbar](reference/cstatusbar-class.md)

- 대화 상자 모음, 클래스 [CDialogBar](reference/cdialogbar-class.md)

- [CReBar](reference/crebar-class.md) 클래스의 rebars

> [!IMPORTANT]
> MFC 버전 4.0을 사용 하 여 도구 모음, 상태 표시줄 및 도구 설명은 MFC에 한정 된 이전 구현 대신 *comctl32.dll* 에 구현 된 시스템 기능을 사용 하 여 구현 됩니다. comctl32.dll 기능을 래핑하는 MFC 버전 6.0에서 `CReBar` 도 추가 되었습니다.

컨트롤 막대 형식에 대 한 간략 한 소개는 다음과 같습니다. 자세한 내용은 아래 링크를 참조 하세요.

## <a name="control-bars"></a>컨트롤 막대

컨트롤 막대는 빠른 1 단계 명령 작업을 제공 하 여 프로그램의 유용성을 크게 향상 시킵니다. 클래스는 `CControlBar` 모든 도구 모음, 상태 표시줄 및 대화 상자 모음의 공통적인 기능을 제공 합니다. `CControlBar` 부모 프레임 창에서 컨트롤 막대의 위치를 지정 하는 기능을 제공 합니다. 일반적으로 컨트롤 막대는 부모 프레임 창의 자식 창이 기 때문에 프레임 창의 클라이언트 뷰 또는 MDI 클라이언트에 대 한 "형제"입니다. 컨트롤 막대 개체는 부모 창의 클라이언트 사각형에 대 한 정보를 사용 하 여 자신을 배치 합니다. 그런 다음 클라이언트 뷰나 MDI 클라이언트 창이 나머지 클라이언트 창을 채우도록 부모의 나머지 클라이언트 창 사각형을 변경 합니다.

> [!NOTE]
> 컨트롤 막대의 단추에 **명령** 또는 **UPDATE_COMMAND_UI** 처리기가 없으면 프레임 워크가 자동으로 단추를 사용 하지 않도록 설정 합니다.

## <a name="toolbars"></a>도구 모음

도구 모음은 명령을 실행 하는 비트맵 단추 행을 표시 하는 컨트롤 막대입니다. 도구 모음 단추를 누르는 것은 메뉴 항목을 선택 하는 것과 같습니다. 해당 메뉴 항목에 도구 모음 단추와 동일한 ID가 있는 경우 메뉴 항목에 매핑되는 동일한 처리기를 호출 합니다. 단추는 누름 단추, 라디오 단추 또는 확인란으로 표시 되 고 동작 하도록 구성할 수 있습니다. 도구 모음은 일반적으로 프레임 창의 위쪽에 정렬 되지만, MFC 도구 모음은 부모 창의 어느 쪽에 나 고정 하거나 자체 미니 프레임 창에서 부동으로 "도킹" 할 수 있습니다. 도구 모음도 "float" 할 수 있으며, 크기를 변경 하 고 마우스로 끌 수 있습니다. 도구 모음에서는 사용자가 도구 모음 단추 위로 마우스를 이동할 때 도구 설명이 표시 될 수도 있습니다. 도구 설명은 단추의 용도를 간략하게 설명 하는 작은 팝업 창입니다.

> [!NOTE]
> MFC 버전 4.0을 사용 하는 [CToolBar](reference/ctoolbar-class.md) 클래스는 Windows 도구 모음 공용 컨트롤을 사용 합니다. 에는 `CToolBar` [CToolBarCtrl](reference/ctoolbarctrl-class.md)포함 됩니다. 그러나 이전 도구 모음은 계속 지원 됩니다. 문서 [도구 모음](mfc-toolbar-implementation.md)을 참조 하세요.

## <a name="status-bars"></a>상태 표시줄

상태 표시줄은 텍스트 출력 창 또는 "표시기"를 포함 하는 컨트롤 막대입니다. 출력 창은 일반적으로 메시지 선과 상태 표시기로 사용 됩니다. 메시지 줄 예제에는 MFC 응용 프로그램 마법사에서 만든 기본 상태 표시줄의 가장 왼쪽 창에 있는 선택한 메뉴 또는 도구 모음 명령을 간략하게 설명 하는 명령 도움말 메시지 줄이 포함 되어 있습니다. 상태 표시기 예에는 SCROLL LOCK, NUM LOCK 및 기타 키가 있습니다. 상태 표시줄은 일반적으로 프레임 창의 아래쪽에 정렬 됩니다. [Cstatusbar](reference/cstatusbar-class.md) 및 class [CStatusBarCtrl](reference/cstatusbarctrl-class.md)클래스를 참조 하세요.

## <a name="dialog-bars"></a>대화 상자 모음

대화 상자 모음은 모덜리스 대화 상자의 기능과 함께 대화 상자 템플릿 리소스를 기반으로 하는 컨트롤 막대입니다. 대화 상자 표시줄에는 창, 사용자 지정 또는 ActiveX 컨트롤이 포함 될 수 있습니다. 대화 상자에서와 같이 사용자는 컨트롤 사이에서 tab 키를 누를 수 있습니다. 대화 상자 모음은 프레임 창의 위쪽, 아래쪽, 왼쪽 또는 오른쪽에 맞춰 정렬할 수 있으며 해당 프레임 창에서 부동 창으로 이동할 수도 있습니다. 클래스 [CDialogBar](reference/cdialogbar-class.md)를 참조 하세요.

## <a name="rebars"></a>Rebars

[Rebar](using-crebarctrl.md) 는 rebar 컨트롤에 대 한 도킹, 레이아웃, 상태 및 지 속성 정보를 제공 하는 컨트롤 막대입니다. Rebar 개체는 편집 상자, 도구 모음 및 목록 상자를 포함 하 여 다양 한 자식 창, 일반적으로 다른 컨트롤을 포함할 수 있습니다. Rebar 개체는 지정 된 비트맵 위에 자식 창을 표시할 수 있습니다. 그리퍼 막대를 클릭 하거나 끌어서 자동 또는 수동으로 크기를 조정할 수 있습니다. 클래스 [CReBar](reference/crebar-class.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[사용자 인터페이스 요소](user-interface-elements-mfc.md)
