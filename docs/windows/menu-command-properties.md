---
title: 메뉴 명령 (c + +)
ms.date: 02/15/2019
helpviewer_keywords:
- menu items, properties
- keyboard shortcuts [C++], menu association
- commands [C++], associating menu commands with accelerator keys
- menu commands [C++], associating with keyboard shortcuts
- status bars [C++], associating menu items
- menus [C++], status bar text
- access keys [C++], checking
- menus [C++], shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics [C++], adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics [C++], uniqueness checking
- Check Mnemonics command
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
ms.openlocfilehash: a950e7d0156d1b952782fddcdff26718fcf0e291
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504326"
---
# <a name="menu-commands-c"></a>메뉴 명령 (c + +)

아래 정보는 메뉴 명령을 선택할 때 [속성 창](/visualstudio/ide/reference/properties-window) 에 나타나는 **메뉴** 속성에 따라 구성 됩니다. 이러한 속성은 **속성** 창 에서도 범주별로 볼 수 있지만 사전순으로 나열 됩니다.

|속성|설명|
|--------------|-----------------|
|**끊어야**|다음 값 중 하나를 사용할 수 있습니다.<br/>  - **None**: 나누지 않습니다. 이것이 기본값입니다.<br/>  - **열**: 정적 메뉴의 경우이 값은 새 줄에 메뉴 명령을 배치 합니다.<br/>      팝업 메뉴의 경우 이 값은 열 사이에 구분선이 없이 새 열에 메뉴 명령을 배치합니다.<br/>      이 속성을 설정하는 경우 런타임에만 메뉴 모양에 영향이 있으며 메뉴 편집기에서는 영향이 없습니다.<br />   - **Bar**: 열과 동일 합니다. **단** , 팝업 메뉴의 경우이 값은 새 열을 이전 열과 세로줄을 구분 합니다.<br/>      이 속성을 설정 하면 메뉴 **편집기**가 아니라 런타임에만 메뉴 모양에 영향을 줍니다.|
|**캡션**|메뉴 명령(메뉴 이름)의 레이블을 지정하는 텍스트입니다. 메뉴 명령의 캡션에 있는 문자 중 하나를 니모닉 키로 만들려면 문자 앞에 앰퍼샌드(&)를 추가합니다.|
|**선택됨**|**True**이면 메뉴 명령이 처음에 선택 됩니다. 형식: **Bool** 기본값: **False**|
|**Enabled**|**False**이면 메뉴 항목이 사용하지 않도록 설정됩니다.|
|**회색으로 표시**|**True**이면 메뉴 명령이 처음에 회색으로 표시 되 고 비활성 상태가 됩니다. 형식: **Bool** 기본값: **False**|
|**도움말**|메뉴 항목을 오른쪽에 맞춥니다. 기본값: **False**<br/><br/>예를 들어 **도움말** 메뉴 명령은 항상 모든 Windows 애플리케이션에서 오른쪽에 표시됩니다. 메뉴 항목에 이 속성을 설정하는 경우 해당 항목은 맨 오른쪽에 및 메뉴 끝에 표시됩니다. 최상위 항목에 적용됩니다.|
|**ID**|헤더 파일에 정의된 기호입니다. 형식: **기호**, **정수**또는 **따옴표 붙은 문자열**입니다.<br/><br/>[속성 창](/visualstudio/ide/reference/properties-window) 에서 선택할 수 있는 드롭다운 목록을 제공하지 않는 경우에도, 편집기에서 일반적으로 제공되는 기호를 사용할 수 있습니다.|
|**팝업**|**True**이면 메뉴 명령이 팝업 메뉴입니다. 형식: **Bool** 기본값: 메뉴 모음의 최상위 메뉴 인 경우 **True** 이 고, 그렇지 않으면 **False**입니다.|
|**프롬프트**|이 메뉴 명령이 강조 표시되면 상태 표시줄에 나타날 텍스트를 포함합니다. 이 텍스트는 메뉴 명령과 동일한 식별자를 사용하여 문자열 테이블에 배치됩니다.<br/><br/>이 속성은 모든 종류의 프로젝트에 사용할 수 있지만 런타임 기능은 MFC에 특정합니다.|
|**오른쪽에서 왼쪽 맞춤**|런타임에 메뉴 명령을 메뉴 모음의 오른쪽에 맞춥니다. 형식: **Bool** 기본값: **False**|
|**오른쪽에서 왼쪽 맞춤**|히브리어나 아랍어와 같이 오른쪽에서 왼쪽으로 읽는 언어에 맞춰 지역화된 인터페이스의 경우, 메뉴 명령을 오른쪽에서 왼쪽으로 표시할 수 있습니다.|
|**구분 기호**|**True**이면 메뉴 명령이 구분 기호입니다. 형식: **Bool** 기본값: **False**|

## <a name="associate-menu-commands"></a>메뉴 명령 연결

메뉴 명령과 키보드 조합에서 동일한 프로그램 명령을 종종 실행하도록 하려고 합니다. 메뉴 **편집기** 를 사용 하 여 동일한 명령을 실행 하면 메뉴 명령과 응용 프로그램의 액셀러레이터 테이블에 있는 항목에 동일한 리소스 식별자를 할당할 수 있습니다. 그러고 나서 메뉴 명령의 [캡션](../windows/menu-command-properties.md) 을 편집하여 액셀러레이터 키의 이름을 표시합니다.

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>메뉴 명령을 액셀러레이터 키와 연결하려면

1. **메뉴 편집기**에서 원하는 메뉴 명령을 선택 합니다.

1. [속성 창](/visualstudio/ide/reference/properties-window)에서 액셀러레이터 키 이름을 **캡션** 속성에 추가합니다.

   - 모든 메뉴의 액셀러레이터 키가 왼쪽으로 맞춰 표시되도록 메뉴 캡션 뒤에 탭의 이스케이프 시퀀스(\t)를 입력합니다.

   - 보조 키의 이름 (**Ctrl**, **Alt**또는 **Shift**)을 입력 하 고 더하기 기호 ( **+** )와 추가 키의 이름, 문자 또는 기호를 차례로 입력 합니다.

   예를 들어 **Ctrl** + **O** 를 **파일** 메뉴의 **열기** 명령에 할당 하려면 다음 텍스트와 같이 메뉴 명령의 **캡션을** 수정 합니다.

   ```
   &Open...\tCtrl+O
   ```

   **메뉴 편집기** 의 메뉴 명령은 사용자가 입력 하는 새 캡션을 반영 하 여 업데이트 됩니다.

1. [액셀러레이터](./accelerator-editor.md) 편집기에서 **액셀러레이터 테이블 항목을 만들고** 메뉴 명령과 같은 식별자를 할당합니다. 기억하기 쉬운 키 조합을 사용합니다.

MFC 응용 프로그램은 사용자가 선택할 수 있는 각 메뉴 명령에 대 한 설명 텍스트를 표시할 수 있습니다. **속성** 창에서 **프롬프트** 속성을 사용 하 여 각 메뉴 명령에 텍스트 문자열을 할당 하 여 설명 텍스트를 표시 합니다. 명령과 동일한 ID를 가진 문자열이 [문자열 테이블](../windows/string-editor.md) 에 있는 경우 MFC 애플리케이션은 사용자가 메뉴 항목 위로 마우스를 가져갈 때 실행 중인 애플리케이션의 상태 표시줄에 이 문자열 리소스를 자동으로 표시합니다.

- MFC 응용 프로그램에서 메뉴 명령과 상태 표시줄 텍스트 문자열을 연결 하려면 메뉴 **편집기**에서 메뉴 명령을 선택 합니다. [속성 창](/visualstudio/ide/reference/properties-window)의 **프롬프트** 상자에 연결된 상태 표시줄 텍스트를 입력합니다.

C + + 프로젝트에서 메뉴 및 메뉴 명령에 대 한 액세스 키 (사용자가 키보드로 메뉴를 선택할 수 있게 하는 니모닉)를 할당할 수 있습니다.

- 액세스 (바로 가기) 키를 메뉴 명령에 할당 하려면 `&` 메뉴 이름이 나 명령 이름 앞에 앰퍼샌드 ()를 입력 하 여 해당 문자를 해당 액세스 키로 지정 합니다.

   예를 들어 "&파일"은 **Alt** + Microsoft Windows 용으로 작성 된 응용 프로그램의 **파일** 메뉴에 대 한 바로 가기 키로 Alt**F** 를 설정 합니다.

   메뉴 항목은 문자의 하나에 바로 가기 키가 할당되는 시각적 표시를 제공합니다. 앰퍼샌드 뒤의 문자에는 밑줄이 표시됩니다(운영 체제에 따라).

> [!NOTE]
> 메뉴를 마우스 오른쪽 단추로 클릭 하 고 **니모닉 확인**을 선택 하 여 메뉴의 모든 액세스 키가 고유한 지 확인 합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[메뉴 편집기](../windows/menu-editor.md)

<!--
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>-->
