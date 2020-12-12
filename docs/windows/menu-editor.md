---
description: '자세히 알아보기: 메뉴 편집기 (c + +)'
title: 메뉴 편집기 (c + +)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.menu.F1
- vc.editors.menu
helpviewer_keywords:
- resource editors [C++], Menu editor
- editors, menus
- Menu editor
- menus [C++], Menu editor
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
- menus [C++], adding items
- commands [C++], adding to menus
- menu items, adding to menus
- submenus
- submenus [C++], creating
- menus [C++], creating
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- shortcut menus [C++], connecting to applications
- pop-up menus
- menu commands [C++], selecting
- menus [C++], selecting
- commands [C++], menu commands
- commands [C++], copying on menus
- menu items, moving
- commands [C++], moving on menus
- menu items, copying
- menu items, deleting
- commands [C++], deleting from menus
- menus [C++], deleting
ms.assetid: 421fb215-6e12-4ec9-a3af-82d77f87bfa6
ms.openlocfilehash: ab4b0c3f2fe7986b7b30b3c9bce9c6558b09fc60
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180177"
---
# <a name="menu-editor-c"></a>메뉴 편집기 (c + +)

메뉴를 통해 논리적이고 찾기 쉬운 방식으로 명령을 정렬할 수 있습니다. **메뉴 편집기** 를 사용 하면 완성 된 응용 프로그램의 메뉴 모음과 매우 유사한 메뉴 모음을 직접 사용 하 여 메뉴를 만들고 편집할 수 있습니다.

> [!TIP]
> 대부분의 경우 **메뉴 편집기** 를 사용 하는 동안 마우스 오른쪽 단추를 클릭 하 여 자주 사용 되는 명령의 팝업 메뉴를 표시할 수 있습니다. 사용할 수 있는 명령은 포인터가 가리키는 내용에 따라 달라집니다.

## <a name="how-to"></a>방법

**메뉴 편집기** 를 사용 하면 다음을 수행할 수 있습니다.

### <a name="to-create-a-standard-menu"></a>표준 메뉴를 만들려면

1. 메뉴 **보기**  >  **다른 창**  >  **리소스 뷰** 로 이동 하 고 **메뉴** 머리글을 마우스 오른쪽 단추로 클릭 합니다. **리소스 추가** 를 선택 하 고 **메뉴** 를 선택 합니다.

1. 메뉴 모음에서 **새 항목** 상자 ( *여기에 형식이* 포함 된 사각형)를 선택 합니다.

   ![메뉴 편집기 새 항목 상자](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   **새 항목** 상자

1. 새 메뉴의 이름 (예: *File*)을 입력 합니다.

   입력 한 텍스트는 **메뉴 편집기** 와 [속성 창의](/visualstudio/ide/reference/properties-window) **캡션** 상자에 모두 나타납니다. 한 위치에서 새 메뉴에 대한 속성을 편집할 수 있습니다.

   메뉴 모음에서 새 메뉴에 이름을 지정하면 새 항목 상자가 오른쪽으로 이동하고(다른 메뉴를 추가할 수 있도록), 메뉴 명령을 추가할 수 있도록 또 다른 새 항목 상자가 첫 번째 메뉴 아래에 열립니다.

   ![확장 된 새 항목 상자](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded 됨")<br/>
   메뉴 이름을 입력 한 후 포커스가 이동 된 **새 항목** 상자

   > [!NOTE]
   > 메뉴 모음에서 단일 항목 메뉴를 만들려면 **Popup** 속성을 **False** 로 설정 합니다.

### <a name="to-create-a-submenu"></a>하위 메뉴를 만들려면

1. 하위 메뉴를 만들려는 메뉴 명령을 선택 합니다.

1. 오른쪽에 표시되는 **새 항목** 상자에 새 메뉴 명령의 이름을 입력합니다. 이 새로운 명령이 하위 메뉴에서 첫 번째로 표시됩니다.

1. 하위 메뉴에 메뉴 명령을 더 추가합니다.

### <a name="to-insert-a-new-menu-between-existing-menus"></a>기존 메뉴 사이에 새 메뉴를 삽입하려면

기존 메뉴 이름을 선택 하 고 **insert** 키를 누르거나 메뉴 모음을 마우스 오른쪽 단추로 클릭 하 고 **새로 삽입** 을 선택 합니다.

   **새 항목** 상자가 선택한 항목 앞에 삽입 됩니다.

### <a name="to-add-commands-to-a-menu"></a>메뉴에 명령을 추가하려면

1. 메뉴를 만듭니다. 그런 다음 메뉴 이름 (예: **File**)을 선택 합니다.

   각 메뉴가 확장되고 명령에 대한 새 항목 상자가 표시됩니다. 예를 들어, **파일** 메뉴에 **새로 만들기**, **열기** 및 **닫기** 명령을 추가할 수 있습니다.

1. 새 항목 상자에 새 메뉴 명령에 대한 이름을 입력합니다.

   > [!NOTE]
   > 입력 한 텍스트는 **메뉴 편집기** 와 [속성 창의](/visualstudio/ide/reference/properties-window) **캡션** 상자에 모두 나타납니다. 한 위치에서 새 메뉴에 대한 속성을 편집할 수 있습니다.

   > [!TIP]
   > 사용자가 메뉴 명령을 선택할 수 있도록 니모닉 키(바로 가기 키)를 정의할 수 있습니다. `&`문자 앞에 앰퍼샌드 ()를 입력 하 여 니모닉으로 지정 합니다. 사용자는 해당 문자를 입력하여 메뉴 명령을 선택할 수 있습니다.

1. **속성** 창에서 적용 되는 메뉴 명령 속성을 선택 합니다. 자세한 내용은 [메뉴 명령 속성](../windows/menu-command-properties.md)을 참조 하세요.

1. **속성** 창의 **프롬프트** 상자에 응용 프로그램의 상태 표시줄에 표시할 프롬프트 문자열을 입력 합니다.

   이 단계에서는 생성 한 메뉴 명령과 동일한 리소스 식별자를 사용 하 여 문자열 테이블에 항목을 만듭니다.

   > [!NOTE]
   > 프롬프트는 **Popup** 속성이 **True** 인 메뉴 항목에만 적용할 수 있습니다. 예를 들어 최상위 메뉴 항목은 하위 메뉴 항목이 있는 경우 프롬프트가 적용됩니다. **프롬프트** 의 목적은 사용자가 메뉴 항목을 선택 하는 경우 발생 하는 상황을 나타내는 것입니다.

1. **Enter** 키를 눌러 메뉴 명령을 완료 합니다.

   새 항목 상자를 선택하여 추가 메뉴 명령을 만들 수 있습니다.

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>여러 메뉴 명령을 선택 하 여 속성 삭제 또는 변경과 같은 대량 작업을 실행 하려면

**Ctrl** 키를 누른 채 원하는 메뉴 또는 하위 메뉴 명령을 선택 합니다.

### <a name="to-move-and-copy-menus-and-menu-commands"></a>메뉴 및 메뉴 명령을 이동 하 고 복사 하려면

- 끌어서 놓기 방법을 사용 합니다.

   1. 이동하려는 항목을 다음 위치로 끌거나 복사합니다.

      - 현재 메뉴의 새 위치.

      - 다른 메뉴. 마우스 포인터를 다른 메뉴로 끌어 이동할 수 있습니다.

   1. 삽입 가이드에 원하는 위치가 표시되면 메뉴 명령을 놓습니다.

- 바로 가기 메뉴 명령을 사용 합니다.

   1. 하나 이상의 메뉴 또는 메뉴 명령을 마우스 오른쪽 단추로 클릭 한 다음 **잘라내기** (이동) 또는 **복사** 를 선택 합니다.

   1. 다른 메뉴 리소스나 리소스 스크립트 파일로 항목을 이동 하는 경우 [다른 창에서 엽니다](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

   1. 이동하거나 복사하려는 메뉴 또는 메뉴 명령의 위치를 선택합니다.

   1. 바로 가기 메뉴에서 **붙여넣기** 를 선택합니다. 이동하거나 복사한 항목은 선택한 항목 앞에 배치됩니다.

> [!NOTE]
> 다른 메뉴 창에 있는 다른 메뉴로 끌거나 복사하고 붙여 넣을 수도 있습니다.

### <a name="to-delete-a-menu-or-menu-command"></a>메뉴 또는 메뉴 명령을 삭제하려면

메뉴 이름 또는 명령을 마우스 오른쪽 단추로 클릭 하 고 **삭제** 를 선택 합니다.

> [!NOTE]
> 마찬가지로 바로 가기 메뉴를 사용하여 복사, 잘라내기, 붙여넣기, 새로 삽입, 구분 기호 삽입, ID 편집, 팝업으로 보기, 니모닉 확인 등의 다른 작업을 수행할 수 있습니다.

## <a name="pop-up-menus"></a>팝업 메뉴

[팝업 메뉴](../mfc/menus-mfc.md) 에는 자주 사용되는 명령이 표시됩니다. 포인터 위치에 대한 상황에 맞는 메뉴일 수 있습니다. 애플리케이션에서 팝업 메뉴를 사용하려면 메뉴 자체를 빌드한 후 애플리케이션 코드에 연결해야 합니다.

메뉴 리소스를 만든 후에는 응용 프로그램 코드에서 메뉴 리소스를 로드 하 고 [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) 를 사용 하 여 메뉴를 표시 해야 합니다. 사용자가 팝업 메뉴 외부를 선택 하 여 해제 하거나 명령을 선택 하면 해당 함수가 반환 됩니다. 사용자가 명령을 선택하는 경우 해당 명령 메시지가 핸들이 전달된 창으로 전송됩니다.

> [!NOTE]
> MFC (Microsoft Foundation Class) 라이브러리 프로그램 및 ATL 프로그램의 경우 **코드 마법사** 를 사용 하 여 메뉴 명령을 코드에 연결 합니다. 자세한 내용은 [이벤트 추가](../ide/adding-an-event-visual-cpp.md) 및 [함수에 메시지 매핑](../mfc/reference/mapping-messages-to-functions.md)을 참조 하세요.

- 팝업 메뉴를 만들려면 빈 제목을 사용 하 여 메뉴를 만들고 *캡션을* 제공 하지 않습니다. 그런 다음 메뉴 명령을 새로 만들기 메뉴에 추가 하 고, 여기에 임시 캡션 *형식* 으로 빈 메뉴 제목 아래의 첫 번째 메뉴 명령으로 이동 하 고, *캡션과* 기타 정보를 입력 합니다.

   팝업 메뉴의 다른 모든 메뉴 명령에 대해이 프로세스를 반복 하 고 메뉴 리소스를 저장 해야 합니다.

- 예를 들어 팝업 메뉴를 응용 프로그램에 연결 하려면 WM_CONTEXTMENU 메시지 처리기를 추가한 후 메시지 처리기에 다음 코드를 추가 합니다.

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > 메시지 처리기에 의해 전달 된 [Cpoint](../atl-mfc-shared/reference/cpoint-class.md) 가 화면 좌표에 있습니다.

일반적으로 **메뉴 편집기** 에서 작업 하는 경우 메뉴 리소스가 메뉴 모음으로 표시 됩니다. 그러나 프로그램이 실행되는 동안 애플리케이션의 메뉴 모음에 메뉴 리소스가 추가될 수 있습니다.

- 메뉴 리소스를 팝업 메뉴로 보려면 메뉴를 마우스 오른쪽 단추로 클릭 하 고 **팝업으로 보기** 를 선택 합니다.

   이 옵션은 보기 기본 설정 이며 메뉴를 수정 하지 않습니다.

> [!TIP]
> 메뉴 모음 보기로 다시 변경 하려면 **팝업으로 보기** 를 다시 선택 합니다. 이 작업은 확인 표시를 제거 하 고 메뉴 모음 뷰를 반환 합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[리소스 편집기](../windows/resource-editors.md)<br/>
[메뉴 명령](../windows/menu-command-properties.md)<br/>
[사용자 인터페이스 개체 및 명령 Id](../mfc/user-interface-objects-and-command-ids.md)<br/>
[메뉴](../mfc/menus-mfc.md)<br/>
[메뉴](/windows/win32/menurc/menus)
