---
title: '연습: 도구 모음에 컨트롤 배치 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dd920f3dd8d08d6ceb766b9c10969137b8bf03c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199266"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>연습: 도구 모음에 컨트롤 배치
이 항목에서는 Windows 컨트롤을 포함하는 도구 모음 단추를 도구 모음에 추가하는 방법을 설명합니다. MFC 도구 모음 단추 이어야 합니다는 [CMFCToolBarButton 클래스](../mfc/reference/cmfctoolbarbutton-class.md)-예를 들어 클래스를 파생 [CMFCToolBarComboBoxButton 클래스](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)를 [CMFCToolBarEditBoxButton 클래스](../mfc/reference/cmfctoolbareditboxbutton-class.md), [CMFCDropDownToolbarButton 클래스](../mfc/reference/cmfcdropdowntoolbarbutton-class.md), 또는 [CMFCToolBarMenuButton 클래스](../mfc/reference/cmfctoolbarmenubutton-class.md)합니다.  
  
## <a name="adding-controls-to-toolbars"></a>도구 모음에 컨트롤 추가  
 도구 모음에 컨트롤을 추가 하려면 다음 단계를 따르십시오.  
  
1.  부모 도구 모음 리소스의 단추에 대한 더미 리소스 ID를 예약합니다. Visual Studio의 도구 모음 편집기를 사용 하 여 단추를 만드는 방법에 대 한 자세한 내용은 참조는 [도구 모음 편집기](../windows/toolbar-editor.md) 항목입니다.  
  
2.  부모 도구 모음에서 모든 비트맵의 단추에 대한 도구 모음 이미지(단추 아이콘)를 예약합니다.  
  
3.  AFX_WM_RESETTOOLBAR 메시지를 처리 하는 메시지 처리기에서 다음을 수행 합니다.  
  
    1.  `CMFCToolbarButton` 파생 클래스를 사용하여 단추 컨트롤을 생성합니다.  
  
    2.  더미 단추를 사용 하 여 새 컨트롤 바꿉니다 [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton)합니다. `ReplaceButton`은 단추 개체를 복사하고 복사본을 유지하므로 스택에서 단추 개체를 생성할 수 있습니다.  
  
> [!NOTE]
>  사용 하 여 도구 모음 다시 설정 해야 응용 프로그램에서 사용자 지정을 사용 하는 경우는 **다시 설정** 단추를 **도구 모음** 탭의 **사용자 지정** 보려면 대화 상자를는 다시 컴파일한 후 응용 프로그램에서 컨트롤을 업데이트 합니다. 도구 모음 상태는 Windows 레지스트리에 저장되며 레지스트리 정보는 응용 프로그램이 시작하는 동안 `ReplaceButton` 메서드가 실행된 후 로드됩니다.  
  
## <a name="toolbar-controls-and-customization"></a>도구 모음 컨트롤 및 사용자 지정  
 **명령** 탭의 **사용자 지정** 대화 상자에 응용 프로그램에서 사용할 수 있는 명령 목록을 포함 합니다. 기본적으로 **사용자 지정** 대화 상자 응용 프로그램 메뉴를 처리 하 고 각 메뉴 범주의 표준 도구 모음 단추의 목록을 작성 합니다. 도구 모음 컨트롤을 제공 하는 확장된 된 기능을 유지 하기 위해에서 사용자 지정 컨트롤을 사용 하 여 표준 도구 모음 단추를 대체 해야 합니다 **사용자 지정** 대화 상자.  
  
 만든 사용자 지정을 사용 하도록 설정 하면 합니다 **사용자 지정** 사용자 지정 처리기에서 대화 상자 `OnViewCustomize` 사용 하 여 합니다 [CMFCToolBarsCustomizeDialog 클래스](../mfc/reference/cmfctoolbarscustomizedialog-class.md) 클래스. 표시 합니다 **사용자 지정** 호출 하 여 대화 상자 [CMFCToolBarsCustomizeDialog::Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create), 호출 [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) 바꾸려면 새 컨트롤을 사용 하 여 표준 단추입니다.  
  
## <a name="example-creating-a-find-combo-box"></a>예제: 찾기 콤보 상자 만들기  
 이 섹션에는 만드는 방법을 설명 합니다는 **찾을** 도구 모음에 나타나고 최근에 사용 된 검색 문자열을 포함 하는 콤보 상자 컨트롤입니다. 사용자는 컨트롤에 문자열을 입력한 다음 Enter 키를 눌러 문서를 검색하거나 Esc 키를 눌러 주 프레임에 포커스를 반환합니다. 이 예에서는 문서에 표시 되는 가정를 [CEditView 클래스](../mfc/reference/ceditview-class.md)-뷰를 파생 합니다.  
  
### <a name="creating-the-find-control"></a>찾기 컨트롤 만들기  
 먼저 `Find` 콤보 상자 컨트롤을 만듭니다.  
  
1.  응용 프로그램 리소스에 단추와 해당 명령을 추가합니다.  
  
    1.  응용 프로그램 리소스에서 `ID_EDIT_FIND` 명령 ID로 응용 프로그램의 도구 모음이나 도구 모음과 연결된 모든 비트맵에 새 버튼을 추가합니다.  
  
    2.  ID_EDIT_FIND 명령 ID를 사용하여 새 메뉴 항목을 만듭니다.  
  
    3.  새로운 문자열 "텍스트 찾기\n찾기"를 문자열 테이블에 추가하고 `ID_EDIT_FIND_COMBO` 명령 ID를 할당합니다. 이 ID는 `Find` 콤보 상자 단추의 명령 ID로 사용됩니다.  
  
        > [!NOTE]
        >  `ID_EDIT_FIND`는 `CEditView`에 의해 처리되는 표준 명령이므로 이 명령을 위해 특수한 처리기를 구현하지 않아도 됩니다.  그러나 새 `ID_EDIT_FIND_COMBO` 명령에 대한 처리기를 구현해야 합니다.  
  
2.  새 클래스를 만듭니다 `CFindComboBox`에서 파생 된 [CComboBox 클래스](../mfc/reference/ccombobox-class.md)합니다.  
  
3.  `CFindComboBox` 클래스에서 `PreTranslateMessage` 가상 메서드를 재정의합니다. 이 메서드를 처리 하는 데 콤보 상자를 통해 합니다 [WM_KEYDOWN](/windows/desktop/inputdev/wm-keydown) 메시지입니다. 사용자가 Esc 키를 누르면(`VK_ESCAPE`) 주 프레임 창으로 포커스를 반환합니다. 사용자가 Enter 키 (`VK_ENTER`)를 포함 하는 WM_COMMAND 메시지를 주 프레임 창에 게시 된 `ID_EDIT_FIND_COMBO` 명령 id입니다.  
  
4.  클래스를 만듭니다는 **찾을** 에서 파생 되는 콤보 상자 단추 [CMFCToolBarComboBoxButton 클래스](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)합니다. 이 예제에서는 `CFindComboButton`이라는 이름으로 지정됩니다.  
  
5.  `CMFCToolbarComboBoxButton`의 생성자에는 세 개의 매개 변수(단추의 명령 ID, 단추 이미지 인덱스 및 콤보 상자의 스타일)가 있습니다. 이러한 매개 변수를 다음과 같이 설정합니다.  
  
    1.  `ID_EDIT_FIND_COMBO`를 명령 ID로 전달합니다.  
  
    2.  사용 하 여 [CCommandManager::GetCmdImage](https://msdn.microsoft.com/4094d08e-de74-4398-a483-76d27a742dca) 사용 하 여 `ID_EDIT_FIND` 이미지 인덱스를 가져오려고 합니다.  
  
    3.  사용 가능한 콤보 상자 스타일의 목록은 참조 하세요 [콤보 상자 스타일](../mfc/reference/styles-used-by-mfc.md#combo-box-styles)합니다.  
  
6.  `CFindComboButton` 클래스에서 `CMFCToolbarComboBoxButton::CreateCombo` 메서드를 재정의합니다. 여기서 `CFindComboButton` 개체를 만들고 해당 개체에 대한 포인터를 반환해야 합니다.  
  
7.  사용 합니다 [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) 매크로를 콤보 단추를 지속 되도록 할 것입니다. 작업 영역 관리자가 Windows 레지스트리에서 단추의 상태를 자동으로 로드 및 저장합니다.  
  
8.  문서 뷰에서 `ID_EDIT_FIND_COMBO` 처리기를 구현합니다. 사용 하 여 [CMFCToolBar::GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) 사용 하 여 `ID_EDIT_FIND_COMBO` 모든 검색할 **찾을** 콤보 상자 단추입니다. 사용자 지정으로 인해 명령 ID가 동일한 단추의 복사본이 여러 개 있을 수 있습니다.  
  
9. ID_EDIT_FIND 메시지 처리기에서 `OnFind`를 사용 하 여 [CMFCToolBar::IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) 에서 찾기 명령을 보냈는지 여부를 결정 하는 **찾을** 콤보 상자 단추입니다. 명령을 보낸 경우 텍스트를 찾고 콤보 상자에 검색 문자열을 추가합니다.  
  
### <a name="adding-the-find-control-to-the-main-toolbar"></a>주 도구 모음에 찾기 컨트롤 추가  
 도구 모음에 콤보 상자 단추를 추가하려면 다음 단계를 따르십시오.  
  
1.  주 프레임 창의 `AFX_WM_RESETTOOLBAR` 메시지 처리기 `OnToolbarReset`을 구현합니다.  
  
    > [!NOTE]
    >  응용 프로그램이 시작하는 동안 도구 모음이 초기화되는 경우 또는 도구 모음이 사용자 지정 동안 다시 설정되는 경우 프레임워크는 이 메시지를 주 프레임 창으로 보냅니다. 두 경우 모두 사용자 지정을 사용 하 여 표준 도구 모음 단추를 대체 해야 **찾을** 콤보 상자 단추입니다.  
  
2.  에 `AFX_WM_RESETTOOLBAR` 처리기를 도구 모음 ID를 검사 하는, *WPARAM* AFX_WM_RESETTOOLBAR 메시지입니다. 도구 모음 ID를 포함 하는 도구 모음과 동일한 경우는 **찾을** 콤보 상자 단추, 호출 [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) 바꾸려면 합니다 **찾을** 단추 (즉,는 명령 ID 사용 하 여 단추 `ID_EDIT_FIND)` 사용 하 여를 `CFindComboButton` 개체입니다.  
  
    > [!NOTE]
    >  `CFindComboBox`이 단추 개체를 복사하고 복사본을 유지하므로 스택에서 `ReplaceButton`를 생성할 수 있습니다.  
  
### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>사용자 지정 대화 상자에 찾기 컨트롤 추가  
 사용자 지정 처리기에서 `OnViewCustomize`, 호출 [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) 바꾸려면 합니다 **찾습니다** 단추 (명령 ID 사용 하 여 단추, `ID_EDIT_FIND)` 를사용하여`CFindComboButton` 개체입니다.  
  
## <a name="see-also"></a>참고 항목  
 [계층 구조 차트](../mfc/hierarchy-chart.md)   
 [클래스](../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 클래스](../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 클래스](../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton 클래스](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCToolBarsCustomizeDialog 클래스](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
