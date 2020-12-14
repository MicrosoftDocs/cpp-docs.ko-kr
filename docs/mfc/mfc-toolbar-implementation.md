---
description: '자세한 정보: MFC 도구 모음 구현'
title: MFC 도구 모음 구현
ms.date: 11/04/2016
helpviewer_keywords:
- toolbars [MFC], creating
- buttons [MFC], MFC toolbars
- toolbars [MFC], docking
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- floating toolbars [MFC]
- toolbars [MFC], floating
- docking toolbars [MFC]
- bitmaps [MFC], toolbar
- toolbar controls [MFC]
- CToolBarCtrl class [MFC], implementing toolbars
- tool tips [MFC], enabling
- toolbars [MFC]
- toolbars [MFC], implementing MFC toolbars
ms.assetid: af3319ad-c430-4f90-8361-e6a2c06fd084
ms.openlocfilehash: 0e6ecf0536c55163dd63d5f05e4c5c9f24f2c4cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251156"
---
# <a name="mfc-toolbar-implementation"></a>MFC 도구 모음 구현

도구 모음은 컨트롤의 비트맵 이미지를 포함 하는 [컨트롤 막대](control-bars.md) 입니다. 이러한 이미지는 누름 단추, 확인란 또는 라디오 단추와 같이 동작할 수 있습니다. MFC는 [CToolbar](reference/ctoolbar-class.md) 클래스를 제공 하 여 도구 모음을 관리 합니다.

이 기능을 사용 하도록 설정 하면 MFC 도구 모음의 사용자가 창의 가장자리에 도킹 하거나 응용 프로그램 창 내의 아무 곳에 나 "float" 할 수 있습니다. MFC는 개발 환경에서와 같은 사용자 지정 가능한 도구 모음을 지원 하지 않습니다.

MFC는 도구 설명도 지원 합니다. 단추 위에 마우스를 놓으면 도구 모음 단추의 용도를 설명 하는 작은 팝업 창이 지원 됩니다. 기본적으로 사용자가 도구 모음 단추를 누르면 상태 표시줄에 상태 문자열이 표시 됩니다 (있는 경우). "날아오기" 상태 표시줄을 활성화 하 여 마우스를 누르지 않고 단추 위에 놓으면 상태 문자열을 표시할 수 있습니다.

> [!NOTE]
> MFC 버전 4.0을 사용 하 여 도구 모음 및 도구 설명은 MFC에 한정 된 이전 구현 대신 Windows 95 이상 기능을 사용 하 여 구현 됩니다.

이전 버전과의 호환성을 위해 MFC는 클래스의 이전 도구 모음 구현을 유지 합니다 `COldToolBar` . 이전 버전의 MFC에 대 한 설명서는 아래에 설명 되어 `COldToolBar` `CToolBar` 있습니다.

응용 프로그램 마법사에서 도구 모음 옵션을 선택 하 여 프로그램의 첫 번째 도구 모음을 만듭니다. 추가 도구 모음을 만들 수도 있습니다.

다음은이 문서에서 소개 하는 내용입니다.

- [도구 모음 단추](#_core_toolbar_buttons)

- [도구 모음 고정 및 고정 해제](#_core_docking_and_floating_toolbars)

- [도구 모음 및 도구 설명](#_core_toolbars_and_tool_tips)

- [CToolBar 및 CToolBarCtrl 클래스](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [도구 모음 비트맵](#_core_the_toolbar_bitmap)

## <a name="toolbar-buttons"></a><a name="_core_toolbar_buttons"></a> 도구 모음 단추

도구 모음의 단추는 메뉴의 항목과 유사 합니다. 두 종류의 사용자 인터페이스 개체는 모두 처리기 함수를 제공 하 여 프로그램에서 처리 하는 명령을 생성 합니다. 일반적으로 도구 모음 단추는 메뉴 명령의 기능을 복제 하 여 동일한 기능에 대 한 대체 사용자 인터페이스를 제공 합니다. 이러한 중복은 단추와 메뉴 항목에 동일한 ID를 제공 하 여 간단히 정렬 됩니다.

도구 모음에서 단추가 표시 되 고 누름 단추, 확인란 또는 라디오 단추로 동작 하도록 할 수 있습니다. 자세한 내용은 클래스 [CToolBar](reference/ctoolbar-class.md)를 참조 하세요.

## <a name="docking-and-floating-toolbars"></a><a name="_core_docking_and_floating_toolbars"></a> 도킹 및 부동 도구 모음

MFC 도구 모음에서 다음을 수행할 수 있습니다.

- 부모 창에서 한 쪽을 따라 고정 된 상태로 유지 됩니다.

- 사용자가 지정 하는 부모 창의 어느 쪽 이나 면에 사용자가 연결 하거나 "도킹" 하거나 연결 합니다.

- 사용자가 편리한 위치로 이동할 수 있도록 프레임 창에서 자체 미니 프레임 창으로 "이동" 하거나 분리 합니다.

- 부동 상태일 때 크기를 조정 해야 합니다.

자세한 내용은 [도킹 및 부동 도구 모음](docking-and-floating-toolbars.md)문서를 참조 하세요.

## <a name="toolbars-and-tool-tips"></a><a name="_core_toolbars_and_tool_tips"></a> 도구 모음 및 도구 설명

MFC 도구 모음에는 도구 모음 단추의 용도에 대 한 간단한 텍스트 설명을 포함 하는 작은 팝업 창을 "도구 설명"으로 표시 하도록 설정할 수도 있습니다. 사용자가 도구 모음 단추 위로 마우스를 이동 하면 도구 설명 창이 표시 되어 힌트를 제공 합니다. 자세한 내용은 [도구 모음 도구 설명](toolbar-tool-tips.md)을 참조 하세요.

## <a name="the-ctoolbar-and-ctoolbarctrl-classes"></a><a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a> CToolBar 및 CToolBarCtrl 클래스

[CToolBar](reference/ctoolbar-class.md)클래스를 통해 응용 프로그램의 도구 모음을 관리할 수 있습니다. MFC 버전 4.0에서,는 `CToolBar` windows 95 이상 및 WINDOWS NT 버전 3.51 이상에서 사용할 수 있는 도구 모음 공용 컨트롤을 사용 하도록 다시 구현 되었습니다.

이 재구현를 사용 하면 MFC에서 운영 체제 지원을 사용 하기 때문에 도구 모음에 대 한 MFC 코드가 줄어듭니다. 또한 재구현는 기능을 향상 시킵니다. `CToolBar`멤버 함수를 사용 하 여 도구 모음을 조작 하거나, 기본 [CToolBarCtrl](reference/ctoolbarctrl-class.md) 개체에 대 한 참조를 가져와 도구 모음 사용자 지정 및 추가 기능에 대 한 멤버 함수를 호출할 수 있습니다.

> [!TIP]
> 의 이전 MFC 구현에 많이 투자 한 경우 `CToolBar` 해당 지원은 계속 사용할 수 있습니다. [이전 도구 모음 사용](using-your-old-toolbars.md)문서를 참조 하세요.

또한 MFC 일반 샘플 [DOCKTOOL](../overview/visual-cpp-samples.md)을 참조 하세요.

## <a name="the-toolbar-bitmap"></a><a name="_core_the_toolbar_bitmap"></a> 도구 모음 비트맵

구성 된 개체는 `CToolBar` 각 단추에 대해 하나의 이미지를 포함 하는 단일 비트맵을 로드 하 여 도구 모음 이미지를 만듭니다. 응용 프로그램 마법사는 Visual C++ [도구 모음 편집기](../windows/toolbar-editor.md)를 사용 하 여 사용자 지정할 수 있는 표준 도구 모음 비트맵을 만듭니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [도구 모음 기본 사항](toolbar-fundamentals.md)

- [도구 모음 고정 및 고정 해제](docking-and-floating-toolbars.md)

- [도구 모음 도구 설명](toolbar-tool-tips.md)

- [Toolbar 컨트롤 사용](working-with-the-toolbar-control.md)

- [이전 도구 모음 사용](using-your-old-toolbars.md)

- [CToolBar](reference/ctoolbar-class.md) 및 [CToolBarCtrl](reference/ctoolbarctrl-class.md) 클래스

## <a name="see-also"></a>참고 항목

[도구 모음](toolbars.md)<br/>
[도구 모음 편집기](../windows/toolbar-editor.md)
