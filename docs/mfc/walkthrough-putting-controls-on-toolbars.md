---
description: '자세히 알아보기: 연습: 도구 모음에 컨트롤 배치'
title: '연습: 도구 모음에 컨트롤 배치'
ms.date: 04/25/2019
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
ms.openlocfilehash: eafb1afa2ffffeaaabfc6b463e2951d8d532db58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143054"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>연습: 도구 모음에 컨트롤 배치

이 문서에서는 Windows 컨트롤을 포함 하는 도구 모음 단추를 도구 모음에 추가 하는 방법을 설명 합니다. MFC에서 도구 모음 단추는 클래스 파생 클래스 (예: [CMFCToolBarComboBoxButton class](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [CMFCToolBarEditBoxButton Class](../mfc/reference/cmfctoolbareditboxbutton-class.md), [CMFCDropDownToolbarButton Class](../mfc/reference/cmfcdropdowntoolbarbutton-class.md)또는 [cmfcCMFCToolBarButton menubutton 클래스](../mfc/reference/cmfctoolbarmenubutton-class.md)) 여야 합니다. [](../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="adding-controls-to-toolbars"></a>도구 모음에 컨트롤 추가

도구 모음에 컨트롤을 추가 하려면 다음 단계를 따르십시오.

1. 부모 도구 모음 리소스의 단추에 대한 더미 리소스 ID를 예약합니다. Visual Studio의 **도구 모음 편집기** 를 사용 하 여 단추를 만드는 방법에 대 한 자세한 내용은 [도구 모음 편집기](../windows/toolbar-editor.md) 문서를 참조 하세요.

1. 부모 도구 모음에서 모든 비트맵의 단추에 대한 도구 모음 이미지(단추 아이콘)를 예약합니다.

1. 메시지를 처리 하는 메시지 처리기에서 `AFX_WM_RESETTOOLBAR` 다음 단계를 수행 합니다.

   1. `CMFCToolbarButton` 파생 클래스를 사용하여 단추 컨트롤을 생성합니다.

   1. [Cmfctoolbar:: ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton)를 사용 하 여 더미 단추를 새 컨트롤로 바꿉니다. `ReplaceButton`은 단추 개체를 복사하고 복사본을 유지하므로 스택에서 단추 개체를 생성할 수 있습니다.

> [!NOTE]
> 응용 프로그램에서 사용자 지정을 사용 하도록 설정한 경우에는 **사용자 지정** 대화 상자의 **도구 모음** 탭에 있는 **다시 설정** 단추를 사용 하 여 다시 컴파일한 후 응용 프로그램에서 업데이트 된 컨트롤을 확인 하 여 도구 모음을 다시 설정 해야 할 수 있습니다. 도구 모음 상태는 Windows 레지스트리에 저장되며 레지스트리 정보는 애플리케이션이 시작하는 동안 `ReplaceButton` 메서드가 실행된 후 로드됩니다.

## <a name="toolbar-controls-and-customization"></a>도구 모음 컨트롤 및 사용자 지정

**사용자 지정** 대화 상자의 **명령** 탭에는 응용 프로그램에서 사용할 수 있는 명령 목록이 있습니다. 기본적으로 **사용자 지정** 대화 상자는 응용 프로그램 메뉴를 처리 하 고 각 메뉴 범주의 표준 도구 모음 단추 목록을 작성 합니다. 도구 모음 컨트롤이 제공 하는 확장 기능을 유지 하려면 표준 도구 모음 단추를 **사용자** 지정 대화 상자에서 사용자 지정 컨트롤로 바꾸어야 합니다.

사용자 지정을 사용 하도록 설정 하는  경우 `OnViewCustomize` [CMFCToolBarsCustomizeDialog 클래스](../mfc/reference/cmfctoolbarscustomizedialog-class.md) 클래스를 사용 하 여 사용자 지정 처리기에서 사용자 지정 대화 상자를 만듭니다. [CMFCToolBarsCustomizeDialog:: Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create)를 호출 하 여 **사용자 지정** 대화 상자를 표시 하기 전에 [CMFCToolBarsCustomizeDialog:: ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) 를 호출 하 여 표준 단추를 새 컨트롤로 대체 합니다.

## <a name="example-creating-a-find-combo-box"></a>예제: 찾기 콤보 상자 만들기

이 섹션에서는 도구 모음에 표시 되 고 최근에 사용한 검색 문자열을 포함 하는 **찾기** 콤보 상자 컨트롤을 만드는 방법을 설명 합니다. 사용자는 컨트롤에 문자열을 입력한 다음 Enter 키를 눌러 문서를 검색하거나 Esc 키를 눌러 주 프레임에 포커스를 반환합니다. 이 예에서는 문서가 [Ceditview 클래스](../mfc/reference/ceditview-class.md)파생 뷰에 표시 되는 것으로 가정 합니다.

### <a name="creating-the-find-control"></a>찾기 컨트롤 만들기

먼저 **찾기** 콤보 상자 컨트롤을 만듭니다.

1. 애플리케이션 리소스에 단추와 해당 명령을 추가합니다.

   1. 애플리케이션 리소스에서 `ID_EDIT_FIND` 명령 ID로 애플리케이션의 도구 모음이나 도구 모음과 연결된 모든 비트맵에 새 버튼을 추가합니다.

   1. 명령 ID를 사용 하 여 새 메뉴 항목을 만듭니다 `ID_EDIT_FIND` .

   1. 새로운 문자열 "텍스트 찾기\n찾기"를 문자열 테이블에 추가하고 `ID_EDIT_FIND_COMBO` 명령 ID를 할당합니다. 이 ID는 **찾기** 콤보 상자 단추의 명령 ID로 사용 됩니다.

        > [!NOTE]
        > `ID_EDIT_FIND`는 `CEditView`에 의해 처리되는 표준 명령이므로 이 명령을 위해 특수한 처리기를 구현하지 않아도 됩니다.  그러나 새 `ID_EDIT_FIND_COMBO` 명령에 대한 처리기를 구현해야 합니다.

1. `CFindComboBox` [Ccombobox 클래스](../mfc/reference/ccombobox-class.md)에서 파생 된 새 클래스를 만듭니다.

1. `CFindComboBox` 클래스에서 `PreTranslateMessage` 가상 메서드를 재정의합니다. 이 메서드를 사용 하면 콤보 상자에서 [WM_KEYDOWN](/windows/win32/inputdev/wm-keydown) 메시지를 처리할 수 있습니다. 사용자가 Esc 키를 누르면(`VK_ESCAPE`) 주 프레임 창으로 포커스를 반환합니다. 사용자가 Enter 키를 누르면(`VK_ENTER`) `WM_COMMAND` 명령 ID를 포함하는 `ID_EDIT_FIND_COMBO` 메시지를 주 프레임 창에 게시합니다.

1. [CMFCToolBarComboBoxButton 클래스](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)에서 파생 된 **찾기** 콤보 상자 단추에 대 한 클래스를 만듭니다. 이 예제에서는 `CFindComboButton`라는 이름으로 지정됩니다.

1. `CMFCToolbarComboBoxButton`의 생성자에는 세 개의 매개 변수(단추의 명령 ID, 단추 이미지 인덱스 및 콤보 상자의 스타일)가 있습니다. 이러한 매개 변수를 다음과 같이 설정합니다.

   1. `ID_EDIT_FIND_COMBO`를 명령 ID로 전달합니다.

   1. [Ccommandmanager:: GetCmdImage](reference/internal-classes.md) 를 사용 `ID_EDIT_FIND` 하 여 이미지 인덱스를 가져옵니다.

   1. 사용 가능한 콤보 상자 스타일의 목록은 [콤보 상자 스타일](../mfc/reference/styles-used-by-mfc.md#combo-box-styles)을 참조 하세요.

1. `CFindComboButton` 클래스에서 `CMFCToolbarComboBoxButton::CreateCombo` 메서드를 재정의합니다. 여기서 `CFindComboButton` 개체를 만들고 해당 개체에 대한 포인터를 반환해야 합니다.

1. [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) 매크로를 사용 하 여 콤보 단추를 영구적으로 만듭니다. 작업 영역 관리자가 Windows 레지스트리에서 단추의 상태를 자동으로 로드 및 저장합니다.

1. 문서 뷰에서 `ID_EDIT_FIND_COMBO` 처리기를 구현합니다. [Cmfctoolbar:: GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) 를 사용 `ID_EDIT_FIND_COMBO` 하 여 모든 **찾기** 콤보 상자 단추를 검색 합니다. 사용자 지정으로 인해 명령 ID가 동일한 단추의 복사본이 여러 개 있을 수 있습니다.

1. `ID_EDIT_FIND`메시지 처리기에서 `OnFind` [Cmfctoolbar:: IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) 을 사용 하 여 **찾기** 콤보 상자 단추에서 찾기 명령이 전송 되었는지 여부를 확인 합니다. 명령을 보낸 경우 텍스트를 찾고 콤보 상자에 검색 문자열을 추가합니다.

### <a name="adding-the-find-control-to-the-main-toolbar"></a>주 도구 모음에 찾기 컨트롤 추가

도구 모음에 콤보 상자 단추를 추가하려면 다음 단계를 따르십시오.

1. 주 프레임 창의 `AFX_WM_RESETTOOLBAR` 메시지 처리기 `OnToolbarReset`을 구현합니다.

    > [!NOTE]
    > 애플리케이션이 시작하는 동안 도구 모음이 초기화되는 경우 또는 도구 모음이 사용자 지정 동안 다시 설정되는 경우 프레임워크는 이 메시지를 주 프레임 창으로 보냅니다. 두 경우 모두 표준 도구 모음 단추를 사용자 지정 **찾기** 콤보 상자 단추로 바꾸어야 합니다.

1. 처리기에서 `AFX_WM_RESETTOOLBAR` 도구 모음 ID (AFX_WM_RESETTOOLBAR 메시지의 *WPARAM* )를 검사 합니다. 도구 모음 ID가 콤보 상자 **찾기** 단추가 포함 된 도구 모음의 도구 모음 ID와 같은 경우 [Cmfctoolbar:: ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) 를 호출 하 여 **찾기** 단추 (즉, 명령 ID가 있는 단추)를 `ID_EDIT_FIND)` 개체로 바꿉니다 `CFindComboButton` .

    > [!NOTE]
    > `CFindComboBox`이 단추 개체를 복사하고 복사본을 유지하므로 스택에서 `ReplaceButton`를 생성할 수 있습니다.

### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>사용자 지정 대화 상자에 찾기 컨트롤 추가

사용자 지정 처리기에서 `OnViewCustomize` [CMFCToolBarsCustomizeDialog:: ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) 를 호출 하 여 **찾기** 단추 (즉, 명령 ID로 단추)를 개체로 바꿉니다 `ID_EDIT_FIND` `CFindComboButton` .

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../mfc/hierarchy-chart.md)<br/>
[클래스](../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 클래스](../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton 클래스](../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 클래스](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCToolBarsCustomizeDialog 클래스](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
