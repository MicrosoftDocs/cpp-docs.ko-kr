---
description: '자세한 정보: 도구 모음 기본 사항'
title: 도구 모음 기본 사항
ms.date: 11/04/2016
f1_keywords:
- RT_TOOLBAR
helpviewer_keywords:
- embedding toolbar in frame window class [MFC]
- application wizards [MFC], installing default application toolbars
- toolbars [MFC], creating
- resources [MFC], toolbar
- toolbar controls [MFC], toolbars created using Application Wizard
- toolbar controls [MFC], command ID
- RT_TOOLBAR resource [MFC]
- toolbars [MFC], adding default using Application Wizard
- LoadBitmap method [MFC], toolbars
- Toolbar editor [MFC], Application Wizard
- command IDs [MFC], toolbar buttons
- SetButtons method [MFC]
- CToolBar class [MFC], default toolbars in Application Wizard
- frame window classes [MFC], toolbar embedded in
- LoadToolBar method [MFC]
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
ms.openlocfilehash: ed52c5878482f2ff0fa1c31a133fd2948d21a76e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264390"
---
# <a name="toolbar-fundamentals"></a>도구 모음 기본 사항

이 문서에서는 응용 프로그램 마법사에서 옵션을 선택 하 여 응용 프로그램에 기본 도구 모음을 추가할 수 있는 기본적인 MFC 구현을 설명 합니다. 다음 내용을 다룹니다.

- [응용 프로그램 마법사 도구 모음 옵션](#_core_the_appwizard_toolbar_option)

- [코드의 도구 모음](#_core_the_toolbar_in_code)

- [도구 모음 리소스 편집](#_core_editing_the_toolbar_resource)

- [여러 도구 모음](#_core_multiple_toolbars)

## <a name="the-application-wizard-toolbar-option"></a><a name="_core_the_appwizard_toolbar_option"></a> 응용 프로그램 마법사 도구 모음 옵션

기본 단추가 포함 된 단일 도구 모음을 가져오려면 사용자 인터페이스 기능 페이지에서 표준 도킹 도구 모음 옵션을 선택 합니다. 그러면 응용 프로그램에 다음과 같은 코드가 추가 됩니다.

- Toolbar 개체를 만듭니다.

- 도킹 또는 부동을 해제 하는 기능을 포함 하 여 도구 모음을 관리 합니다.

## <a name="the-toolbar-in-code"></a><a name="_core_the_toolbar_in_code"></a> 코드의 도구 모음

도구 모음은 응용 프로그램 클래스의 데이터 멤버로 선언 된 [CToolBar](../mfc/reference/ctoolbar-class.md) 개체입니다 `CMainFrame` . 즉, toolbar 개체는 주 프레임 창 개체에 포함 되어 있습니다. 즉, MFC가 프레임 창을 만들 때 도구 모음을 만들고 프레임 창이 소멸 되 면 도구 모음을 소멸 시킵니다. MDI (다중 문서 인터페이스) 응용 프로그램에 대 한 다음 partial 클래스 선언은 포함 된 도구 모음 및 포함 된 상태 표시줄에 대 한 데이터 멤버를 표시 합니다. 또한 멤버 함수의 재정의를 보여 줍니다 `OnCreate` .

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

도구 모음 만들기가에서 발생 `CMainFrame::OnCreate` 합니다. MFC는 프레임에 대 한 창을 만든 다음 표시 되기 전에 [OnCreate](../mfc/reference/cwnd-class.md#oncreate) 를 호출 합니다. `OnCreate`응용 프로그램 마법사에서 생성 하는 기본은 다음과 같은 도구 모음 작업을 수행 합니다.

1. `CToolBar`개체의 [create](../mfc/reference/ctoolbar-class.md#create) member 함수를 호출 하 여 기본 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 개체를 만듭니다.

1. [Loadtoolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar) 를 호출 하 여 도구 모음 리소스 정보를 로드 합니다.

1. 는 함수를 호출 하 여 도킹, 부동 및 도구 설명을 사용 하도록 설정 합니다. 이러한 호출에 대 한 자세한 내용은 [도킹 및 부동 도구 모음](../mfc/docking-and-floating-toolbars.md)문서를 참조 하세요.

> [!NOTE]
> MFC 일반 샘플 [DOCKTOOL](../overview/visual-cpp-samples.md) 에는 이전 및 새 mfc 도구 모음 모두에 대 한 그림이 포함 되어 있습니다. 를 사용 하는 도구 모음은 `COldToolbar` 2 단계에서 `LoadBitmap` (대신 `LoadToolBar` ) 및를 호출 해야 합니다 `SetButtons` . 새 도구 모음에 대 한 호출이 필요 `LoadToolBar` 합니다.

도킹, 부동 및 도구 팁 호출은 선택 사항입니다. 원하는 경우에서 해당 줄을 제거할 수 있습니다 `OnCreate` . 결과는 고정 된 상태로 유지 되는 도구 모음이 며, float 또는 redock 수 없으며 도구 설명을 표시할 수 없습니다.

## <a name="editing-the-toolbar-resource"></a><a name="_core_editing_the_toolbar_resource"></a> 도구 모음 리소스 편집

응용 프로그램 마법사를 사용 하 여 가져오는 기본 도구 모음은 MFC 버전 4.0에 도입 된 **RT_TOOLBAR** 사용자 지정 리소스를 기반으로 합니다. [도구 모음 편집기](../windows/toolbar-editor.md)를 사용 하 여이 리소스를 편집할 수 있습니다. 편집기를 사용 하면 단추를 쉽게 추가, 삭제 및 다시 정렬할 수 있습니다. 여기에는 Visual C++의 일반 그래픽 편집기와 매우 유사한 단추에 대 한 그래픽 편집기가 포함 되어 있습니다. 이전 버전의 Visual C++에서 도구 모음을 편집한 경우 더 쉽게 작업을 찾을 수 있습니다.

명령에 도구 모음 단추를 연결 하려면 단추에와 같은 명령 ID를 지정 `ID_MYCOMMAND` 합니다. 도구 모음 편집기의 단추 속성 페이지에서 명령 ID를 지정 합니다. 그런 다음 명령에 대 한 처리기 함수를 만듭니다. 자세한 내용은 [함수에 메시지 매핑](../mfc/reference/mapping-messages-to-functions.md) 을 참조 하세요.

새 [CToolBar](../mfc/reference/ctoolbar-class.md) 멤버 함수는 **RT_TOOLBAR** 리소스를 사용 합니다. 이제 [Loadtoolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar) 는 [loadtoolbar](../mfc/reference/ctoolbar-class.md#loadbitmap) 을 사용 하 여 도구 모음 단추 이미지의 비트맵을 로드 하 고, [setbuttons](../mfc/reference/ctoolbar-class.md#setbuttons) 를 사용 하 여 단추 스타일을 설정 하 고, 비트맵 이미지를 사용 하 여 단추를 연결 합니다.

도구 모음 편집기를 사용 하는 방법에 대 한 자세한 내용은 [도구 모음 편집기](../windows/toolbar-editor.md)를 참조 하십시오.

## <a name="multiple-toolbars"></a><a name="_core_multiple_toolbars"></a> 여러 도구 모음

응용 프로그램 마법사는 하나의 기본 도구 모음을 제공 합니다. 응용 프로그램에 도구 모음이 두 개 이상 필요한 경우 기본 도구 모음에 대해 마법사에서 생성 된 코드에 따라 추가 도구 모음에 대 한 코드를 모델링할 수 있습니다.

명령 결과로 도구 모음을 표시 하려면 다음을 수행 해야 합니다.

- 도구 모음 편집기를 사용 하 여 새 도구 모음 리소스를 만들고 `OnCreate` [loadtoolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar) 멤버 함수를 사용 하 여이 리소스를 로드 합니다.

- 주 프레임 창 클래스에 새 [CToolBar](../mfc/reference/ctoolbar-class.md) 개체를 포함 합니다.

- 에서 적절 한 함수를 호출 `OnCreate` 하 여 도구 모음을 도킹 하거나 부동으로 설정 하 고, 스타일을 설정 하는 등의 작업을 수행 합니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [MFC 도구 모음 구현 (도구 모음에 대 한 개요 정보)](../mfc/mfc-toolbar-implementation.md)

- [도구 모음 고정 및 고정 해제](../mfc/docking-and-floating-toolbars.md)

- [도구 모음 도구 설명](../mfc/toolbar-tool-tips.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md) 및 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 클래스

- [도구 모음 컨트롤 사용](../mfc/working-with-the-toolbar-control.md)

- [이전 도구 모음 사용](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>참고 항목

[MFC 도구 모음 구현](../mfc/mfc-toolbar-implementation.md)
