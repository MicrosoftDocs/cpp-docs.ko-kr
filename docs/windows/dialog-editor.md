---
title: 대화 상자 편집기 (c + +)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
- vc.editors.dialog
helpviewer_keywords:
- resource editors [C++], Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes [C++], editing
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog Editor [C++], showing or hiding toolbar
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog Editor [C++], accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog Editor [C++], switching between controls and code
- Dialog Editor [C++], shortcut keys
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
ms.openlocfilehash: 6a83640bd50d4af40be3cdb7a47b29ae5ffb3f09
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504539"
---
# <a name="dialog-editor-c"></a>대화 상자 편집기 (c + +)

**대화 상자 편집기** 를 사용 하 여 대화 상자 리소스를 만들거나 편집할 수 있습니다.

- 편집기를 열려면 **리소스 뷰** 창에서 대화 상자의 .rc 파일을 두 번 클릭 하거나 메뉴 **보기**  >  **다른 창**  >  **리소스 뷰**로 이동 합니다.

새 대화 상자 또는 대화 상자 템플릿을 만드는 첫 번째 단계 중 하나는 컨트롤을 추가 하는 것입니다. 대화 상자 **편집기**에서 특정 크기, 모양 또는 맞춤에 맞게 컨트롤을 정렬 하거나 대화 상자 내에서 작업으로 이동할 수 있습니다. 또한 컨트롤을 쉽게 삭제할 수 있습니다.

대화 상자를 템플릿으로 저장하여 다시 사용할 수 있습니다. 대화 상자 디자인과 이를 구현하는 코드 편집 간을 쉽게 전환할 수도 있습니다.

또한 **대화 상자 편집기**에서 단일 또는 여러 컨트롤의 속성을 편집할 수 있습니다. 탭 순서 즉, **tab** 키를 누를 때 컨트롤이 포커스를 얻는 순서를 변경 하거나, 사용자가 키보드를 사용 하 여 컨트롤을 선택할 수 있도록 하는 액세스 키 또는 키 조합을 정의할 수 있습니다.

또한 **대화 상자 편집기** 에서는 ActiveX 컨트롤을 비롯 한 사용자 지정 컨트롤을 사용할 수 있습니다. [폼 보기](../mfc/reference/cformview-class.md), [레코드 뷰](../data/record-views-mfc-data-access.md)또는 [대화 상자 모음](../mfc/dialog-bars.md)을 편집할 수도 있습니다.

Visual Studio 2015부터 **대화 상자 편집기** 를 사용 하 여 사용자가 대화 상자의 크기를 조정할 때 컨트롤이 이동 하 고 크기를 조정 하는 방법을 지정 하는 동적 레이아웃을 정의할 수 있습니다. 자세한 내용은 [Dynamic Layout](../mfc/dynamic-layout.md)을 참조하세요.

리소스에 대 한 자세한 내용은 [대화 상자](../windows/creating-a-new-dialog-box.md) 및 [대화 상자 컨트롤](../windows/controls-in-dialog-boxes.md)을 만드는 방법을 참조 하세요.

> [!TIP]
> 대부분의 경우 **대화 상자 편집기**를 사용 하는 동안 마우스 오른쪽 단추를 선택 하 여 자주 사용 하는 명령의 바로 가기 메뉴를 표시할 수 있습니다.

## <a name="dialog-editor-toolbar"></a>대화 상자 편집기 도구 모음

**대화 상자 편집기** 도구 모음에는 크기 및 맞춤과 같은 대화 상자에서 컨트롤의 레이아웃을 정렬 하는 단추가 포함 되어 있습니다. **대화 상자 편집기** 도구 모음 단추는 **서식** 메뉴의 명령에 해당 합니다.

|아이콘|의미|아이콘|의미|
|----------|-------------|----------|-------------|
|![테스트 대화 상자 단추](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|대화 상자 테스트|![전체 공간 단추](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|옆으로|
|![왼쪽 맞춤 단추](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|왼쪽 맞춤|![아래 공간 단추](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|아래로|
|![오른쪽 맞춤 단추](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|오른쪽 맞춤|![같은 너비로 단추](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|같은 너비로|
|![위쪽 맞춤 단추](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|위쪽 맞춤|![같은 높이로 단추](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|같은 높이로|
|![아래쪽 맞춤 단추](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|아래쪽 맞춤|![같은 크기로 단추](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|같은 크기로|
|![세로 가운데 단추](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Vertical|![모눈 설정/해제 단추](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|모눈 설정/해제|
|![가로 가운데 단추](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|수평적 크기 조정|![안내선 설정/해제 단추](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|안내선 설정/해제|

- **대화 상자 편집기** 도구 모음을 표시 하거나 숨기려면 메뉴 **보기**  >  **도구 모음**  >  **대화 상자 편집기**로 이동 합니다.

C + + 프로젝트에서 **대화 상자 편집기** 를 열면 솔루션 위쪽에 **대화 상자 편집기** 도구 모음이 자동으로 표시 되지만 도구 모음을 명시적으로 닫으면 다음에 **대화 상자 편집기**를 열 때 호출 해야 합니다. 사용 가능한 도구 모음 및 창 목록에서 선택 하 여 표시를 전환할 수 있습니다.

## <a name="switch-between-dialog-box-controls-and-code"></a>대화 상자 컨트롤과 코드 사이를 전환 합니다.

MFC 응용 프로그램에서 대화 상자 컨트롤을 두 번 클릭 하 여 해당 처리기 코드로 이동 하거나 스텁 처리기 함수를 신속 하 게 만들 수 있습니다.

컨트롤이 선택 된 상태에서 **ControlEvents** 단추나 [속성 창](/visualstudio/ide/reference/properties-window) 의 **메시지** 단추를 선택 하 여 선택한 항목에 사용할 수 있는 Windows 메시지 및 이벤트의 전체 목록을 볼 수 있습니다. 처리기 함수를 만들거나 편집 하려면 목록에서 선택 합니다.

- **대화 상자 편집기**에서 코드로 이동 하려면 대화 상자에서 컨트롤을 두 번 클릭 하 여 가장 최근에 구현 된 메시지 처리 함수에 대 한 선언으로 이동 합니다.

   ATL 기반 대화 상자 클래스의 경우 항상 생성자 정의로 이동 합니다.

- 컨트롤을 선택 하 여 컨트롤에 대 한 이벤트를 보려면 **속성** 창에서 **ControlEvents** 단추를 선택 합니다.

   대화 상자에서 단일 컨트롤에 포커스가 있는 경우 마우스 오른쪽 단추를 클릭 하 고 **이벤트 처리기 추가**를 선택할 수 있습니다. 이를 통해 처리기가 추가 되는 클래스를 지정할 수 있습니다. 자세한 내용은 [이벤트 처리기 추가](../ide/adding-an-event-handler-visual-cpp.md)를 참조 하세요.

   > [!NOTE]
   > 대화 상자에 포커스가 있을 때 **ControlEvents** 단추를 선택 하면 대화 상자의 모든 컨트롤 목록이 표시 되며,이를 확장 하 여 개별 컨트롤에 대 한 이벤트를 편집할 수 있습니다.

- 대화 상자에 대 한 메시지를 보려면 대화 상자를 선택한 상태에서 **속성** 창에 있는 **메시지** 단추를 선택 합니다.

## <a name="accelerator-keys"></a>액셀러레이터 키

다음은 **대화 상자 편집기** 명령에 대 한 기본 액셀러레이터 키입니다.  

|명령|구성|설명|
|-------------|----------|-----------------|
|Format.AlignBottoms|**Ctrl**  +  **Shift**  +  **아래쪽 화살표**|선택한 컨트롤의 아래쪽 가장자리를 기준 컨트롤과 맞춥니다.|
|Format.AlignCenters|**Shift**  +  **F9**|선택한 컨트롤의 세로 가운데를 기준 컨트롤에 맞춥니다.|
|Format.AlignLefts|**Ctrl**  +  **Shift**  +  **왼쪽 화살표**|선택한 컨트롤의 왼쪽 가장자리를 기준 컨트롤에 맞춥니다.|
|Format.AlignMiddles|**F9**|선택한 컨트롤의 가로 가운데를 기준 컨트롤에 맞춥니다.|
|Format.AlignRights|**Ctrl**  +  **Shift**  +  **오른쪽 화살표**|선택한 컨트롤의 오른쪽 가장자리를 기준 컨트롤에 맞춥니다.|
|Format.AlignTops|**Ctrl**  +  **Shift**  +  **위쪽 화살표**|선택한 컨트롤의 위쪽 가장자리를 기준 컨트롤과 맞춥니다.|
|Format.ButtonBottom|**Ctrl** + **B**|선택한 단추를 대화 상자의 아래쪽 가운데에 배치 합니다.|
|Format.ButtonRight|**Ctrl**  +  **R**|선택한 단추를 대화 상자의 오른쪽 위 모퉁이에 배치 합니다.|
|Format.CenterHorizontal|**Ctrl**  +  **Shift**  +  **F9**|대화 상자 내에서 컨트롤을 가로로 가운데 맞춤 합니다.|
|Format.CenterVertical|**Ctrl** + **F9**|대화 상자 내에서 컨트롤을 세로 방향으로 가운데에 맞춥니다.|
|Format.CheckMnemonics|**Ctrl**  +  **M**|니모닉의 고유성을 검사 합니다.|
|System.windows.window.sizetocontent|**Shift**  +  **F7**|선택한 컨트롤의 크기를 캡션 텍스트에 맞게 조정 합니다.|
|Format.SpaceAcross|**Alt**  +  **왼쪽 화살표**|선택한 컨트롤을 가로로 간격 하 게 배치 합니다.|
|Format.SpaceDown|**Alt**  +  **아래쪽 화살표**|선택한 컨트롤을 세로로 균등 하 게 배치 합니다.|
|Format.TabOrder|**Ctrl** + **D**|대화 상자 내에서 컨트롤의 순서를 설정 합니다.|
|Format.TestDialog|**Ctrl** + **T**|대화 상자를 실행 하 여 모양과 동작을 테스트 합니다.|
|Format.ToggleGuides|**Ctrl**  +  **G**|대화 상자를 편집 하기 위해 모눈, 지침 및 그리드를 순환 하지 않습니다.|

- 바로 가기 키를 변경 하려면 메뉴 **도구**  >  **옵션**으로 이동 하 고 **환경** 폴더 아래에서 **키보드** 를 선택 합니다.

   자세한 내용은 [바로 가기 키 식별 및 사용자 지정](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)을 참조하세요.

- 설정을 변경 하려면 메뉴 **도구**  >  **설정 가져오기 및 내보내기**로 이동 합니다.

   대화 상자에서 사용할 수 있는 옵션과 메뉴 명령의 이름 및 위치는 활성 설정 또는 버전에 따라 **도움말** 에 설명 된 것과 다를 수 있습니다.  자세한 내용은 [Visual Studio IDE 개인 설정](/visualstudio/ide/personalizing-the-visual-studio-ide)을 참조하세요.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[리소스 편집기](../windows/resource-editors.md)<br/>
[방법: 대화 상자 만들기](../windows/creating-a-new-dialog-box.md)<br/>
[대화 상자 컨트롤](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/adding-a-member-variable-visual-cpp.md#dialog-box-controls-and-variable-types)-->
