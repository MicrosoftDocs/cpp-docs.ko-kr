---
description: '자세한 정보: 방법: 컨트롤 액세스 및 값 정의 (c + +)'
title: '방법: 컨트롤 액세스 및 값 정의 (c + +)'
ms.date: 02/15/2019
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls [C++], mnemonics
- access keys [C++], checking
- mnemonics [C++], checking for duplicate
- mnemonics
- mnemonics [C++], dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
- combo boxes [C++], Data property
- controls [C++], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- Data property
- combo boxes [C++], testing values
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
ms.openlocfilehash: cedaa5c455dc5810c78158bec628f57c7f6e52b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327121"
---
# <a name="how-to-define-control-access-and-values-c"></a>방법: 컨트롤 액세스 및 값 정의 (c + +)

## <a name="tab-order"></a>탭 순서

탭 순서는 **tab** 키가 대화 상자 내에서 한 컨트롤에서 다음 컨트롤로 입력 포커스를 이동 하는 순서입니다. 일반적으로 탭 순서는 대화 상자에서 왼쪽에서 오른쪽으로, 위쪽에서 아래쪽으로 진행 됩니다. 각 컨트롤에는 컨트롤이 입력 포커스를 받을지 여부를 결정 하는 **Tabstop** 속성이 있습니다.

- 컨트롤에 대 한 입력 포커스를 설정 하려면 [속성 창의](/visualstudio/ide/reference/properties-window) **Tabstop** 속성에서 **True** 또는 **False** 를 선택 합니다.

**Tabstop** 속성이 True로 설정 되지 않은 컨트롤도 탭 순서의 일부가 되어야 합니다. 특히 캡션이 없는 컨트롤의 경우에도 **마찬가지** 입니다. 관련 컨트롤에 대 한 액세스 키를 포함 하는 정적 텍스트는 탭 순서의 관련 컨트롤 바로 앞에와 야 합니다.

> [!NOTE]
> 대화 상자에 겹치는 컨트롤이 있는 경우 탭 순서를 변경 하면 컨트롤이 표시 되는 방식이 변경 될 수 있습니다. 탭 순서에서 나중에 나오는 컨트롤은 탭 순서에서 앞에 오는 겹치는 컨트롤 위에 항상 표시 됩니다.

- 모든 컨트롤의 현재 탭 순서를 보려면 메뉴 **형식**  >  **탭 순서** 로 이동 하거나 **ctrl**  +  **D** 를 누릅니다.

   각 컨트롤의 왼쪽 위 모퉁이에 있는 숫자는 현재 탭 순서로 해당 자리를 표시 합니다.

- 모든 컨트롤의 탭 순서를 변경 하려면 메뉴 **형식**  >  **탭 순서** 로 이동 하 고 tab 키를 사용할 순서로 각 컨트롤을 선택 하 여 탭 순서를  설정 합니다.

- 두 개 이상의 컨트롤에 대 한 탭 순서를 변경 하려면 메뉴 **형식**  >  **탭 순서** 로 이동 합니다. **Ctrl** 키를 누른 상태에서 변경 내용이 시작 되는 컨트롤을 선택한 다음 **ctrl** 키를 놓고 **Tab** 키가 해당 지점에서 따라야 하는 순서 대로 컨트롤을 선택 합니다.

   예를 들어를 통해 컨트롤의 순서를 변경 하려면 `7` `9` **Ctrl 키** 를 누른 채 먼저 제어를 선택 `6` 합니다.

- 특정 컨트롤을 number로 설정 `1` 하거나 탭 순서에서 첫 번째 컨트롤을 두 번 클릭 합니다.

> [!TIP]
> **탭 순서** 모드를 입력 한 후 **Esc** 키 또는 **Enter** 키를 눌러 **탭 순서** 모드를 종료 하 고 탭 순서를 변경 하는 기능을 사용 하지 않도록 설정 합니다.

## <a name="mnemonics-access-keys"></a>니모닉 (선택 키)

일반적으로 키보드 사용자는 **Tab** 키와 **화살표** 키를 사용 하 여 대화 상자에서 입력 포커스를 한 컨트롤에서 다른 컨트롤로 이동 합니다. 그러나 사용자가 단일 키를 눌러 컨트롤을 선택할 수 있도록 하는 액세스 키 (니모닉 또는 쉽게 기억할 수 있는 이름)를 정의할 수 있습니다.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>표시 되는 캡션 (누름 단추, 확인란 및 라디오 단추)을 사용 하 여 컨트롤에 대 한 선택 키를 정의 하려면

1. 대화 상자에서 컨트롤을 선택 합니다.

1. [속성 창의](/visualstudio/ide/reference/properties-window) **Caption** 속성에서 컨트롤의 새 이름을 입력 하 고 `&` 원하는 문자 앞에 앰퍼샌드 ()를 입력 하 여 해당 컨트롤의 선택 키로 사용 합니다. 예: `&Radio1`.

1. **Enter** 키를 누릅니다.

   표시 된 캡션에 밑줄을 표시 하 여 선택 키 (예: **R** adio1)를 표시 합니다.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>표시 되는 캡션이 없는 컨트롤의 선택 키를 정의 하려면

1. [도구 상자](/visualstudio/ide/reference/toolbox)에서 **정적 텍스트** 컨트롤을 사용 하 여 컨트롤에 대 한 캡션을 만듭니다.

1. 정적 텍스트 캡션에 `&` 원하는 문자 앞에 있는 앰퍼샌드 ()를 선택 키로 입력 합니다.

1. 정적 텍스트 컨트롤은 탭 순서에서 레이블이 지정 된 컨트롤 바로 앞에와 야 합니다.

> [!NOTE]
> 대화 상자 내의 모든 액세스 키는 고유 해야 합니다. 중복 된 액세스 키를 확인 하려면 메뉴 **형식**  >  **확인 니모닉** 으로 이동 합니다.

## <a name="combo-box-values"></a>콤보 상자 값

**대화 상자 편집기** 가 열려 있는 동안 콤보 상자 컨트롤에 값을 추가할 수 있습니다.

> [!TIP]
> **대화 상자 편집기** 에서 상자의 크기를 조정 *하기 전에* 콤보 상자에 모든 값을 추가 하는 것이 좋습니다. 또는 콤보 컨트롤에 표시 되는 텍스트를 자를 수 있습니다.

### <a name="to-enter-values-into-a-combo-box-control"></a>콤보 상자 컨트롤에 값을 입력 하려면

1. 콤보 상자 컨트롤을 선택 하 여 선택 합니다.

1. [속성 창](/visualstudio/ide/reference/properties-window)에서 **데이터** 속성으로 스크롤합니다.

   > [!NOTE]
   > 유형별로 그룹화 된 속성을 표시 하는 경우 **데이터가** **기타** 속성에 나타납니다.

1. **데이터** 속성의 값 영역을 선택 하 고 세미콜론으로 구분 하 여 데이터 값을 입력 합니다.

   > [!NOTE]
   > 공백은 드롭다운 목록에서 사전순으로 표시 되는 것을 방해 하므로 값 사이에 공백을 넣지 마십시오.

1. 값 추가를 마쳤으면 **enter** 키를 누릅니다.

콤보 상자의 드롭다운 부분을 확대 하는 방법에 대 한 자세한 내용은 [콤보 상자의 크기 설정 및 Drop-Down 목록](./arrangement-of-controls-on-dialog-boxes.md)을 참조 하십시오.

> [!NOTE]
> 이 절차를 사용 하 여 Win32 프로젝트에 값을 추가할 수 없습니다 ( **데이터** 속성은 win32 프로젝트에 대해 회색으로 표시 됨). Win32 프로젝트에는이 기능을 추가 하는 라이브러리가 없으므로 Win32 프로젝트를 사용 하 여 프로그래밍 방식으로 콤보 상자에 값을 추가 해야 합니다.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>콤보 상자에서 값의 모양을 테스트 하려면

1. **데이터** 속성에 값을 입력 한 후 [대화 상자 편집기 도구 모음](./dialog-editor.md)에서 **테스트** 단추를 선택 합니다.

1. 전체 값 목록을 아래로 스크롤합니다. 값은 **속성** 창의 **데이터** 속성에 입력 된 대로 정확 하 게 표시 됩니다. 철자 및 대/소문자 검사는 없습니다.

1. **Esc** 키를 눌러 **대화 상자** 편집기로 돌아갑니다.

## <a name="radio-button-values"></a>라디오 단추 값

대화 상자에 라디오 단추를 추가 하는 경우 그룹의 첫 번째 단추에 대 한 **속성** 창에서 **그룹** 속성을 설정 하 여 해당 단추를 그룹으로 처리 합니다. 그러면 해당 라디오 단추의 컨트롤 ID가 [멤버 변수 추가 마법사](../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard)에 표시됩니다. 이 마법사를 통해 라디오 단추 그룹에 대한 멤버 변수를 추가할 수 있습니다.

대화 상자에 라디오 단추 그룹을 여러 개 포함할 수 있습니다. 다음 절차를 사용 하 여 각 그룹을 추가 합니다.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>대화 상자에 라디오 단추 그룹을 추가하려면

1. [도구 상자 창](/visualstudio/ide/reference/toolbox) 에서 라디오 단추 컨트롤을 선택 하 고 대화 상자에서 컨트롤을 놓을 위치를 선택 합니다.

1. 위의 단계를 반복 하 여 원하는 수의 라디오 단추를 추가 합니다. 그룹의 라디오 단추가 탭 순서로 연속 되어 있는지 확인 합니다.

1. [속성 창](/visualstudio/ide/reference/properties-window)에서, 탭 순서 중 **첫 번째** 라디오 단추의 *그룹* 속성을 **True** 로 설정합니다.

   **Group** 속성을 **True** 로 변경 하면 WS_GROUP 스타일이 리소스 스크립트의 대화 상자 개체에 있는 단추의 항목에 추가 되 고 사용자가 단추 그룹에서 한 번에 두 개 이상의 라디오 단추를 선택할 수 없습니다. 사용자가 라디오 단추 하나를 선택 하면 그룹의 다른 사용자가 지워집니다.

   > [!NOTE]
   > 그룹의 첫 번째 라디오 단추만 **그룹** 속성이 **True** 로 설정되어야 합니다. 단추 그룹에 포함 되지 않는 추가 컨트롤이 있는 경우 *그룹 외부에 있는* 첫 번째 컨트롤의 **그룹** 속성을 **True** 로 설정 합니다.  + 탭 순서를 보려면 Ctrl **D** 를 사용 하 여 그룹 외부의 첫 번째 컨트롤을 빠르게 식별할 수 있습니다.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>라디오 단추 그룹의 멤버 변수를 추가하려면

1. 탭 순서의 첫 번째 라디오 단추 컨트롤 (기준 컨트롤 및 **그룹** 속성이 **True** 로 설정 된 컨트롤)을 마우스 오른쪽 단추로 클릭 하 고 **변수 추가** 를 선택 합니다.

1. [멤버 변수 추가 마법사](../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard)에서 **제어 변수** 확인란을 선택한 후 **값** 라디오 단추를 선택합니다.

   - **변수 이름** 상자에 새 멤버 변수 이름을 입력합니다.

   - **변수 형식** 목록 상자에서 int를 선택 **`int`** 하거나 입력 합니다.

   이제 선택된 상태로 표시할 라디오 단추를 지정하도록 코드를 수정할 수 있습니다. 예를 들어는 `m_radioBox1 = 0;` 그룹의 첫 번째 라디오 단추를 선택 합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[대화 상자 컨트롤 관리](controls-in-dialog-boxes.md)<br/>
[방법: 컨트롤 추가, 편집 또는 삭제](adding-editing-or-deleting-controls.md)<br/>
[방법: 컨트롤 레이아웃](arrangement-of-controls-on-dialog-boxes.md)<br/>
