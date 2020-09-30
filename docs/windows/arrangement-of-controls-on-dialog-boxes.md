---
title: '방법: 컨트롤 레이아웃 (c + +) | Microsoft Docs'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.grouping
- vc.editors.dialog.combo
helpviewer_keywords:
- controls [C++], positioning
- dialog box controls [C++], placement
- Dialog Editor [C++], arranging controls
- Dialog Editor [C++], guides and margins
- guides, clearing
- guides
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
- guides, disabling snapping
- controls [C++], snap to guides/grid
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
- grid spacing
- guides, settings
- layout grid in Dialog Editor
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls [C++], grouping radio buttons
- grouping controls
- radio buttons [C++], grouping on dialog boxes
- controls [C++], tab order
- focus, tab order
- tab controls [C++], tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls [C++], tab order
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
ms.openlocfilehash: ac21096f18b1331759f9bf7dfe613100298b7296
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509664"
---
# <a name="how-to-layout-controls-c"></a>방법: 컨트롤 레이아웃 (c + +)

**대화 상자 편집기** 는 컨트롤을 자동으로 맞추고 크기를 조정 하는 레이아웃 도구를 제공 합니다. 대부분의 작업에 대해 [대화 상자 편집기 도구 모음](./dialog-editor.md)을 사용할 수 있습니다. 모든 **대화 상자 편집기** 도구 모음 명령은 **서식** 메뉴 에서도 사용할 수 있으며 대부분 [바로 가기 키](./dialog-editor.md)가 있습니다.

대화 상자에 대 한 대부분의 레이아웃 명령은 두 개 이상의 컨트롤을 선택한 경우에만 사용할 수 있습니다. 단일 컨트롤이 나 여러 컨트롤을 선택할 수 있으며, 둘 이상의 컨트롤이 선택 된 경우 기본적으로 첫 번째 컨트롤이 기준 컨트롤이 됩니다.

현재 컨트롤의 위치, 높이 및 너비가 상태 표시줄의 오른쪽 아래 모퉁이에 표시 됩니다. 전체 대화 상자를 선택 하면 상태 표시줄에 대화 상자의 위치 전체와 높이 및 너비를 표시 합니다.

## <a name="arrange-controls"></a>컨트롤 정렬

대화 상자 **편집기** 를 사용 하 여 다음과 같은 세 가지 상태 중 하나로 대화 상자에 컨트롤을 정렬할 수 있습니다.

- 안내선과 여백이 있는 상태에서 기본으로 설정 합니다.

- 에 레이아웃 모눈을 사용 합니다.

- 맞춤 또는 맞춤 기능을 사용 하지 않습니다.

[대화 상자 편집기 도구 모음](./dialog-editor.md) 에는 상태를 제어 하는 단추가 포함 되어 있습니다.

- 상태를 변경 하려면 적절 한 아이콘을 선택 하거나 메뉴 **형식**  >  **안내선 설정**으로 이동 합니다.

**안내선 설정** 대화 상자에는 다음과 같은 속성이 있습니다.

|속성|설명|
|---|---|
|**레이아웃 안내선**|레이아웃 안내선에 대 한 설정을 표시 합니다.|
|**없음**|레이아웃 도구를 숨깁니다.|
|**눈금자 및 안내선**|사용 하도록 설정 하면 레이아웃 도구에 눈금자가 추가 되 고 안내선이 눈금자에 배치 될 수 있습니다. 기본 안내선은 여백입니다.|
|**그리드**|레이아웃 표를 만듭니다. 새 컨트롤은 자동으로 표에 맞춰집니다.|
|**모눈 간격**|표 간격의 설정을 Dlu (대화 상자 단위)로 표시 합니다.|
|**Width: Dlu**|레이아웃 모눈의 너비를 Dlu로 설정 합니다. 가로 DLU는 대화 상자 글꼴의 평균 너비 (4)입니다.|
|**높이: Dlu**|레이아웃 모눈의 높이를 Dlu로 설정 합니다. 세로 DLU는 대화 상자 글꼴의 평균 높이를 8로 나눈 값입니다.|

### <a name="guides-and-margins"></a>안내선 및 여백

컨트롤을 이동 하거나, 컨트롤을 추가 하거나, 현재 레이아웃, 안내선 및 여백을 다시 정렬 하는 경우에는 대화 상자에서 컨트롤을 정확 하 게 맞출 수 있습니다.

대화 상자를 만들면 여백 이라는 4 가지 수정 된 안내선이 제공 되며 파란색 점선으로 표시 됩니다.

- 여백을 이동 하려면 여백을 새 위치로 끌어 옵니다.

- 여백을 사라지게 하려면 여백을 0 위치로 이동 합니다.

- 여백을 다시 가져오려면 포인터를 여백 제로 위치 위에 놓고 여백을 위치로 이동 합니다.

안내선은 편집기에 표시 되는 대화 상자와 **대화 상자 편집기**의 위쪽 및 왼쪽에 있는 눈금자의 해당 화살표에 파란색 점선으로 표시 됩니다. 컨트롤의 크기 조정 핸들은 컨트롤이 이동 될 때 안내선에 맞추고, 이전에 가이드에 맞춘 컨트롤이 없는 경우 안내선을 컨트롤에 맞춥니다. 안내선이 이동 하면 해당 안내선에도 맞춰진 컨트롤이 이동 합니다. 안내선 중 하나를 이동 하면 둘 이상의 안내선에 맞춰진 컨트롤의 크기가 조정 됩니다.

- 눈금자 내에서 안내선을 만들려면 한 번을 선택 하 여 안내선을 만들거나 안내선 설정을 지정할 수 있는 **안내선 설정** 대화 상자를 두 번 클릭 하 여 시작 합니다.

- 대화 상자에서 안내선을 설정 하려면 가이드를 선택 하 여 새 위치로 끌거나 눈금자의 화살표를 선택 하 여 연결 된 안내선을 끕니다.

   안내선의 좌표는 창의 아래쪽에 있는 상태 표시줄에 표시 되거나 눈금자의 화살표 위로 포인터를 이동 하 여 안내선의 정확한 위치를 표시 합니다.

- 안내선을 삭제 하려면 대화 상자에서 안내선을 끌거나 눈금자에서 해당 화살표를 끕니다.

안내선과 컨트롤의 간격을 결정 하는 눈금자의 눈금 표시는 Dlu (대화 상자 단위)로 정의 됩니다. DLU는 대화 상자 글꼴 크기 (일반적으로 8 포인트 MS Shell Dlg)를 기반으로 합니다. 가로 DLU는 대화 상자 글꼴의 평균 너비 (4)입니다. 세로 DLU는 글꼴의 평균 높이를 8로 나눈 값입니다.

- 눈금 표시 간격을 변경 하려면 메뉴 **형식**  >  **안내선 설정**으로 이동 하 여 **표 간격** 필드에서 새 너비와 높이를 dlu로 지정 합니다.

### <a name="layout-grid"></a>레이아웃 모눈

대화 상자에서 컨트롤을 배치 하거나 정렬 하는 경우 레이아웃 모눈을 사용 하 여 보다 정확한 위치를 지정 합니다. 그리드를 켜면 컨트롤이 표의 점선 (magnetized)으로 맞춰집니다.

- 레이아웃 모눈을 설정 하거나 해제 하려면 메뉴 **형식**  >  **안내선 설정** 으로 이동 하 여 **표 형태** 단추를 선택 하거나 선택 취소 합니다.

   [대화 상자 편집기 도구 모음의](./dialog-editor.md) **모눈 설정/해제** 단추를 사용 하 여 개별 **대화 상자 편집기** 창에서 표를 계속 제어할 수 있습니다.

- 레이아웃 모눈의 크기를 변경 하려면 메뉴 **형식**  >  **안내선 설정** 으로 이동 하 여 표의 셀에 대 한 높이와 너비를 dlu로 입력 합니다. 최소 높이 또는 너비는 4입니다.

### <a name="disable-guides"></a>안내선 사용 안 함

특수 키를 마우스와 함께 사용 하 여 안내선 맞추기 효과를 비활성화할 수 있습니다. **Alt** 키를 사용 하면 선택한 가이드의 맞추기 효과를 사용할 수 없습니다. **Shift** 키를 사용 하 여 안내선을 이동 하면 맞춰진 컨트롤이 안내선으로 이동 하지 않습니다.

- 안내선 맞추기 효과를 사용 하지 않으려면 **Alt** 키를 누른 채 컨트롤을 끕니다.

- 스냅 된 컨트롤을 이동 하지 않고 안내선을 이동 하려면 **Shift** 키를 누른 채 안내선을 끕니다.

- 안내선을 해제 하려면 메뉴 **형식**  >  **가이드 설정**으로 이동 합니다. 그런 다음 **레이아웃 안내선**에서 **없음**을 선택 합니다.

   > [!TIP]
   > 메뉴 **형식**  >  **토글 안내선**에서 바로 가기를 사용할 수도 있습니다.

## <a name="select-controls"></a>컨트롤 선택

크기 조정, 맞춤, 이동, 복사 또는 삭제를 위한 컨트롤을 선택 하 고 원하는 작업을 완료 합니다. 대부분의 경우 [대화 상자 편집기 도구 모음](./dialog-editor.md)에서 크기 조정 및 맞춤 도구를 사용할 컨트롤을 두 개 이상 선택 해야 합니다.

컨트롤이 선택 되 면 선택 테두리에 표시 되는 단색 (활성) 또는 빈 (비활성) 크기 조정 핸들을 사용 하 여 주위에 음영이 있는 테두리가 표시 됩니다. 여러 컨트롤이 선택 된 경우 기준 컨트롤에는 고정 크기 조정 핸들이 있고, 선택한 다른 모든 컨트롤에는 빈 크기 조정 핸들이 있습니다.

- 컨트롤을 선택 하려면 [도구 상자 창](/visualstudio/ide/reference/toolbox)에서 **포인터** 도구를 선택 하 고 다음 단계 중 하나를 사용 하 여 선택 합니다.

  - 포인터를 끌어 대화 상자에서 선택 하려는 컨트롤 주위에 선택 상자를 그립니다. 마우스 단추를 놓으면 선택 상자 안의 모든 컨트롤이 선택 됩니다.

  - **Shift** 키를 누른 채 선택 영역에 포함 하려는 컨트롤을 선택 합니다.

  - **Ctrl** 키를 누른 채 선택 영역에 포함 하려는 컨트롤을 선택 합니다.

- 선택한 컨트롤의 그룹에서 컨트롤을 추가 하거나 제거 하려면 **shift** 키를 누른 채 추가 하거나 제거할 컨트롤을 선택 합니다.

### <a name="dominant-controls"></a>기준 컨트롤

여러 컨트롤의 크기를 조정 하거나 정렬 하는 경우 **대화 상자 편집기** 는 기준 컨트롤을 사용 하 여 다른 컨트롤의 크기를 조정 하거나 정렬 하는 방법을 결정 합니다. 기본적으로 기준 컨트롤은 선택한 첫 번째 컨트롤입니다.

- 기준 컨트롤을 지정 하려면 **Ctrl** 키를 누른 상태에서 다른 컨트롤의 크기나 위치에 *먼저*영향을 주는 데 사용할 컨트롤을 선택 합니다. **Ctrl** 키를 누른 채 선택 영역 내에서 컨트롤을 선택 하면 해당 선택 항목의 기준 컨트롤이 제어 됩니다.

- 기준 컨트롤을 변경 하려면 현재 선택 된 컨트롤의 바깥쪽을 선택 하 여 현재 선택을 취소 하 고 위의 절차를 반복 하 여 다른 컨트롤을 *먼저*선택 합니다.

> [!NOTE]
> 하위 컨트롤의 핸들이 비어 있는 동안에는 기준 컨트롤의 크기 조정 핸들이 고정 되어 있습니다. 모든 추가 크기 조정 또는 맞춤은 기준 컨트롤을 기반으로 합니다.

## <a name="size-controls"></a>크기 제어

크기 조정 핸들을 사용 하 여 컨트롤의 크기를 조정 합니다. 포인터가 크기 조정 핸들에 배치 되 면 셰이프를 변경 하 여 컨트롤의 크기를 조정할 수 있는 방향을 표시 합니다. 활성 크기 조정 핸들은 실선이 며 크기 조정 핸들이 비어 있는 경우 해당 축을 따라 컨트롤의 크기를 조정할 수 없습니다.

- 컨트롤의 크기를 조정 하려면 컨트롤을 선택 하 고 크기 조정 핸들을 끌어 크기를 변경 합니다.

  - 위쪽 및 옆쪽의 크기 핸들은 가로 또는 세로 크기를 변경 합니다.

  - 모퉁이의 크기 핸들은 가로 및 세로 크기를 모두 변경 합니다.

   > [!TIP]
   > **Shift** 키를 누른 상태에서 **오른쪽** 및 **아래쪽** 화살표 키를 사용 하 여 한 번에 하나씩 컨트롤의 크기를 조정할 수 있습니다.

- 컨트롤 내의 텍스트에 맞게 컨트롤의 크기를 자동으로 조정 하려면 메뉴 **형식** 으로 이동 하거나 컨트롤을 마우스 오른쪽 단추로 클릭 하 고 **콘텐츠 크기를**선택 합니다.

- 컨트롤의 크기를 동일 하 게 만들려면 크기를 조정 하려는 컨트롤을 선택 하 고 메뉴 **형식**을  >  **같은 크기로**이동한 다음, **높이**또는 **너비**중 하나를 선택 합니다. **Both**

   기준 컨트롤의 크기에 따라 컨트롤 그룹의 크기를 조정 합니다 .이 컨트롤은 계열에서 첫 번째로 선택한 컨트롤입니다. 그룹에 있는 컨트롤의 최종 크기는 기준 컨트롤의 크기에 따라 달라 집니다.

- 안내선을 사용 하 여 컨트롤 그룹의 크기를 조정 하려면 컨트롤의 한 쪽을 안내선에 맞추고 안내선을 컨트롤의 다른 쪽 (또는 컨트롤)으로 끌어 놓습니다. 이제 각 안내선을 이동 하 여 컨트롤의 크기를 조정할 수 있습니다 (또는 컨트롤).

   여러 컨트롤에서 필요한 경우 크기를 조정 하 여 두 번째 가이드에 맞춥니다.

### <a name="other-controls"></a>기타 컨트롤

대화 상자에 콤보 상자를 추가할 때 크기를 지정할 수 있습니다. 드롭다운 목록 상자의 크기를 지정할 수도 있습니다. 자세한 내용은 [콤보 상자 컨트롤에 값 추가](./defining-mnemonics-access-keys.md)를 참조 하세요.

1. 콤보 상자 오른쪽에 있는 드롭다운 화살표 단추를 선택 합니다.

   ![MFC 프로젝트 콤보 상자의 화살표](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   컨트롤의 개요는 드롭다운 목록 영역이 확장 된 콤보 상자의 크기를 표시 하도록 변경 됩니다.

1. 아래쪽 크기 조정 핸들을 사용 하 여 드롭다운 목록 영역의 초기 크기를 변경 합니다.

   ![MFC 프로젝트의 콤보&#45;상자 크기 조정](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. 드롭다운 화살표를 다시 선택 하 여 콤보 상자의 드롭다운 목록 부분을 닫습니다.

> [!NOTE]
> MFC를 사용 하 여 가로 스크롤 막대가 있는 목록 상자를 대화 상자에 추가 하면 스크롤 막대가 응용 프로그램에 자동으로 표시 되지 않습니다.
>
> 코드에서 [CListBox:: SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) 를 호출 하 여 가장 넓은 요소의 최대 너비를 설정 합니다. 이 값을 설정 하지 않으면 목록 상자에 있는 항목이 상자 보다 넓은 경우에도 스크롤 막대가 표시 되지 않습니다.

## <a name="align-controls"></a>컨트롤 맞춤

- 컨트롤을 맞추려면 정렬할 컨트롤을 선택 합니다. 메뉴 **형식**  >  **맞춤** 으로 이동 하 고 다음 맞춤 중 하나를 선택 합니다.

   |맞춤|Description|
   |-----|-----------|
   |**맞춤**|선택한 컨트롤을 왼쪽에 맞춥니다.|
   |**가운데가**|선택한 컨트롤을 중심점에 따라 가로로 맞춥니다.|
   |**권한**|선택한 컨트롤을 오른쪽에 맞춥니다.|
   |**위쪽**|위쪽 가장자리를 따라 선택 된 컨트롤을 정렬 합니다.|
   |**중간**|선택한 컨트롤을 중간 요소를 따라 세로로 정렬 합니다.|
   |**아래쪽**|선택한 컨트롤을 아래쪽 가장자리에 맞춥니다.|

   먼저 기준으로 사용할 컨트롤을 선택 하거나, 컨트롤 그룹의 마지막 위치가 기준 컨트롤의 위치에 따라 달라 지는 맞춤 또는 크기 조정 명령을 실행 하기 전에 기준 컨트롤로 설정 해야 합니다.

- 균일 한 공간 컨트롤을 만들려면 다시 정렬할 컨트롤을 선택 합니다. 메뉴 **형식**공간을 균등 하 게 이동 하  >  **Space Evenly** 고 다음 간격 맞춤 중 하나를 선택 합니다.

   |간격|설명|
   |---|---|
   |**옆으로**|가장 왼쪽 및 가장 오른쪽 컨트롤 사이에서 간격이 균일 하 게 제어 됩니다.|
   |**아래로**|선택 된 컨트롤의 위쪽 및 아래쪽 컨트롤 사이에서 간격이 균일 하 게 제어 됩니다.|

- 컨트롤을 가운데에 표시 하려면 다시 정렬할 컨트롤이 나 컨트롤을 선택 합니다. **Format**  >  **대화 상자에서** 메뉴 형식 센터로 이동 하 고 다음 배열 중 하나를 선택 합니다.

   |정렬|설명|
   |---|---|
   |**세로**|대화 상자에서 컨트롤을 세로로 가운데 맞춤 합니다.|
   |**가로**|대화 상자에서 컨트롤을 가로로 가운데 맞춤 합니다.|

- 푸시 단추를 맞추려면 하나 이상의 푸시 단추를 선택 합니다. 메뉴 **형식**  >  **정렬 단추**로 이동한 후 다음 정렬 중 하나를 선택 합니다.

   |정렬|설명|
   |---|---|
   |**오른쪽**|대화 상자의 오른쪽 가장자리를 따라 누름 단추를 맞춥니다.|
   |**아래쪽**|대화 상자의 아래쪽 가장자리를 따라 누름 단추를 맞춥니다.|

   푸시 단추가 아닌 다른 컨트롤을 선택 하는 경우 해당 위치는 영향을 받지 않습니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[대화 상자 컨트롤 관리](controls-in-dialog-boxes.md)<br/>
[방법: 컨트롤 추가, 편집 또는 삭제](adding-editing-or-deleting-controls.md)<br/>
[방법: 컨트롤 액세스 및 값 정의](defining-mnemonics-access-keys.md)<br/>
