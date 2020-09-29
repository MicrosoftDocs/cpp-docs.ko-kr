---
title: 도구 모음 편집기 (c + +)
description: Visual Studio 도구 모음 편집기를 사용 하 여 도구 모음 리소스를 만들고 비트맵을 도구 모음 리소스로 변환 합니다.
ms.date: 09/26/2020
f1_keywords:
- vc.editors.toolbar.F1
- vc.editors.toolbar
- vc.editors.newtoolbarresource
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
- buttons [C++], custom toolbars
- toolbar buttons [C++], editing
- buttons
- toolbar buttons [C++], creating
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
- toolbar buttons [C++], moving
- Toolbar editor [C++], moving buttons
- Toolbar editor [C++], copying buttons
- toolbars [C++], copying buttons
- toolbar buttons [C++], copying
- toolbar buttons [C++], deleting
- Toolbar editor [C++], deleting buttons
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
- toolbar controls [MFC], command ID
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- command IDs, toolbar buttons
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
- tool tips [C++], adding to toolbar buttons
- "\n in tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
ms.openlocfilehash: 042bfafb1e55d45145306a8c388e1e3559fa9a33
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413803"
---
# <a name="toolbar-editor-c"></a>도구 모음 편집기 (c + +)

도구 **모음 편집기** 에서는 도구 모음 리소스를 만들고 비트맵을 도구 모음 리소스로 변환할 수 있습니다. **도구 모음 편집기** 에서는 그래픽 표시를 사용 합니다. 완성 된 응용 프로그램에서 표시 되는 것과 유사한 도구 모음과 단추를 표시 합니다.

**도구 모음 편집기** 창에는 **이미지 편집기** 창과 동일한 단추 이미지의 두 뷰가 표시 됩니다. 분할줄이 두 창을 구분합니다. 창의 상대적 크기를 변경 하려면 분할 막대를 양쪽에서 측면으로 끌어 놓을 수 있습니다. 활성 창에는 선택 테두리가 표시 되 고 이미지의 두 보기 위에 제목 도구 모음이 표시 됩니다.

![도구 모음 편집기](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")<br/>
**도구 모음 편집기**

**도구 모음 편집기** 는 기능의 **이미지 편집기** 와 비슷합니다. 두 항목 간의 메뉴 항목, 그래픽 도구 및 비트맵 표는 동일 합니다. **이미지** 메뉴에는 **도구 모음 편집기** 와 **이미지 편집기**사이에서 전환할 수 있는 메뉴 명령이 있습니다. **그래픽** 도구 모음, **색** 색상표 또는 **이미지** 메뉴 사용에 대 한 자세한 내용은 [이미지 편집기](../windows/image-editor-for-icons.md)를 참조 하세요.

비트맵을 변환 하 여 c + + 프로젝트에서 새 도구 모음을 만들 수 있습니다. 비트맵의 그래픽이 도구 모음에 대 한 단추 이미지로 변환 됩니다. 일반적으로 비트맵은 단일 비트맵에 여러 단추 이미지를 포함 하 고 각 단추에 대해 하나의 이미지를 포함 합니다. 기본값은 16 픽셀이 고 이미지의 높이는 이미지의 크기가 될 수 있습니다. **새 도구 모음 리소스** 대화 상자에서 단추 이미지의 크기를 지정할 수 있습니다. 크기를 지정 하려면 **이미지 편집기**에서 **이미지** 메뉴의 **도구 모음 편집기** 를 선택 합니다.

**새 도구 모음 리소스** 대화 상자에서 c + + 프로젝트의 도구 모음 리소스에 추가 하는 단추의 너비와 높이를 지정할 수 있습니다. 기본값은 16 x 15 픽셀입니다.

도구 모음을 만드는 데 사용 되는 비트맵의 최대 너비는 2048입니다. **단추 너비** 를 *512*로 설정 하면 단추가 네 개만 있을 수 있습니다. 그리고 너비를 *513*로 설정 하는 경우에는 단추를 세 개만 사용할 수 있습니다.

**새 도구 모음 리소스** 대화 상자에는 다음과 같은 속성이 있습니다.

|속성|Description|
|---|---------------|
|**단추 너비**|비트맵 리소스에서 도구 모음 리소스로 변환 하는 도구 모음 단추의 너비를 입력할 수 있는 공간을 제공 합니다.|
|**단추 높이**|비트맵 리소스에서 도구 모음 리소스로 변환 하는 도구 모음 단추의 높이를 입력할 수 있는 공간을 제공 합니다.|

> [!NOTE]
> 이미지는 지정 된 너비와 높이로 잘리고 색은 표준 도구 모음 색 (16 색)을 사용 하도록 조정 됩니다.

기본적으로 도구 모음은 도구 모음의 오른쪽 끝에 새 단추나 빈 단추를 표시 합니다. 이 단추를 편집 하기 전에 이동할 수 있습니다. 새 단추를 만들면 편집 된 단추 오른쪽에 또 다른 빈 단추가 나타납니다. 빈 단추는 도구 모음을 저장할 때 저장 되지 않습니다.

도구 모음 단추에는 다음과 같은 속성이 있습니다.

|속성|Description|
|--------------|-----------------|
|**ID**|단추의 ID를 정의 합니다. 드롭다운 목록에는 일반 **ID** 이름이 제공 됩니다.|
|**Width**|단추의 너비를 설정 합니다. 16 픽셀을 권장 합니다.|
|**높이**|단추의 높이를 설정 합니다. 한 단추의 높이가 도구 모음에 있는 모든 단추의 높이를 변경 합니다. 15 픽셀을 권장 합니다.|
|**프롬프트**|상태 표시줄에 표시 되는 메시지를 정의 합니다. *\N* 및 이름을 추가 하면 도구 모음 단추에 **도구 설명이** 추가 됩니다. 자세한 내용은 [도구 모음 단추에 대 한 도구 설명을 만들려면을](#to-create-a-tool-tip-for-a-toolbar-button)참조 하세요.|

**너비** 와 **높이** 는 모든 단추에 적용 됩니다. 도구 모음을 만드는 데 사용 되는 비트맵의 최대 너비는 2048입니다. 단추 너비를 *512*로 설정 하면 단추 4 개만 사용할 수 있습니다. 너비를 *513*로 설정 하는 경우에는 단추를 세 개만 사용할 수 있습니다.

## <a name="how-to"></a>방법

**도구 모음 편집기** 를 사용 하 여 다음을 수행할 수 있습니다.

### <a name="to-create-new-toolbars"></a>새 도구 모음을 만들려면

1. **리소스 뷰**에서 *.rc* 파일을 마우스 오른쪽 단추로 클릭 하 고 **리소스 추가**를 선택 합니다. *.Rc* 파일에 기존 도구 모음이 있는 경우 **도구** 모음 폴더를 마우스 오른쪽 단추로 클릭 하 고 **삽입 도구 모음**을 선택할 수 있습니다.

1. **리소스 추가** 대화 상자의 **리소스 종류** 목록에서 **도구 모음** 을 선택한 다음 **새로 만들기**를 선택 합니다.

   **+** **도구 모음** 리소스 형식 옆에 더하기 기호 ()가 표시 되 면 도구 모음 템플릿을 사용할 수 있음을 의미 합니다. 더하기 기호를 선택 하 여 템플릿 목록을 확장 하 고, 템플릿을 선택 하 고, **새로 만들기**를 선택 합니다.

### <a name="to-convert-bitmaps-to-toolbar-resources"></a>비트맵을 도구 모음 리소스로 변환 하려면

1. [이미지 편집기](../windows/image-editor-for-icons.md)에서 기존 비트맵 리소스를 엽니다. 비트맵이 *.rc* 파일에 없는 경우 *.rc* 파일을 마우스 오른쪽 단추로 클릭 하 고 **가져오기**를 선택 합니다. 그런 다음 *.rc* 파일에 추가 하려는 비트맵으로 이동 하 고 **열기**를 선택 합니다.

1. 메뉴 **이미지**  >  **도구 모음 편집기**로 이동 합니다.

   **새 도구 모음 리소스** 대화 상자가 나타납니다. 비트맵에 맞게 아이콘 이미지의 너비와 높이를 변경할 수 있습니다. 그러면 도구 모음 이미지가 **도구 모음 편집기**에 표시 됩니다.

1. 변환을 완료 하려면 [속성 창](/visualstudio/ide/reference/properties-window)을 사용 하 여 단추의 명령 **ID** 를 변경 합니다. 새 *id* 를 입력 하거나 드롭다운 목록에서 **id** 를 선택 합니다.

   > [!TIP]
   > **속성** 창에는 제목 표시줄에 압정 단추가 포함 되 고이를 선택 하면 창의 **자동 숨기기** 사용 하거나 사용 하지 않도록 설정 됩니다. 개별 속성 창을 다시 열지 않고 모든 도구 모음 단추 속성을 순환 하려면 **속성** 창이 고정 된 상태로 유지 되도록 **자동 숨기기** 해제 합니다.

   [속성 창](/visualstudio/ide/reference/properties-window)를 사용 하 여 새 도구 모음에서 단추의 명령 id를 변경할 수도 있습니다.

### <a name="to-manage-toolbar-buttons"></a>도구 모음 단추를 관리 하려면

#### <a name="to-create-a-new-toolbar-button"></a>새 도구 모음 단추를 만들려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources) 리소스 폴더 (예: *Project1*)를 확장 합니다.

1. **도구 모음** 폴더를 확장 하 고 편집할 도구 모음을 선택한 후 다음 중 하나를 수행 합니다.

   - 도구 모음의 오른쪽 끝에 있는 빈 단추에 ID를 할당 합니다. [속성 창](/visualstudio/ide/reference/properties-window)에서 **ID** 속성을 편집 하 여이 작업을 수행할 수 있습니다. 예를 들어 도구 모음 단추에 메뉴 옵션과 동일한 ID를 제공할 수 있습니다. 이 경우 드롭다운 목록 상자를 사용 하 여 메뉴 옵션의 **ID** 를 선택 합니다.

   - **도구 모음 보기** 창에서 도구 모음의 오른쪽 끝에 있는 빈 단추를 선택 하 고 그리기를 시작 합니다. 기본 단추 명령 ID (ID_BUTTON)가 할당 됩니다 \<n> .

#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>도구 모음에 이미지를 단추로 추가 하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 도구 모음을 두 번 클릭 하 여 엽니다.

1. 그런 다음 도구 모음에 추가 하려는 이미지를 엽니다.

   > [!NOTE]
   > Visual Studio에서 이미지를 열면 **이미지 편집기**에서 열립니다. 다른 그래픽 프로그램에서 이미지를 열 수도 있습니다.

1. 메뉴 복사본 **편집**으로 이동  >  **Copy**합니다.

1. 소스 창의 맨 위에 있는 탭을 선택 하 여 도구 모음으로 전환 합니다.

1. 메뉴 **편집**  >  **붙여넣기**로 이동 합니다.

   이미지가 도구 모음에 새 단추로 표시 됩니다.

#### <a name="to-move-a-toolbar-button"></a>도구 모음 단추를 이동 하려면

**도구 모음 보기** 창에서 도구 모음의 새 위치로 이동 하려는 단추를 끕니다.

- 도구 모음에서 단추를 복사 하려면 **Ctrl** 키를 누른 채 **도구 모음 보기** 창에서 단추를 도구 모음의 새 위치로 끌어 옵니다. 또는 다른 도구 모음의 위치로 끌어 놓습니다.

- 도구 모음 단추를 삭제 하려면 도구 모음 단추를 선택 하 고 도구 모음에서 끕니다.

- 도구 모음의 단추 사이에 공백을 삽입 하거나 제거 하려면 도구 모음에서 단추를 다른 위치로 끌어 놓습니다.

|작업|단계|
|------|------|
|공백이 아닌 단추 앞에 공백을 삽입 하려면|단추를 오른쪽으로 끌고 다음 단추 중간에 겹쳐질 때까지 아래로 끕니다.|
|공백 뒤에 공백이 오고 후행 공백을 유지 하는 단추 앞에 공백을 삽입 하려면|오른쪽 또는 아래쪽 가장자리가 다음 단추와만 접촉 하거나 겹쳐 놓을 때까지 단추를 끕니다.|
|공백 뒤에 오는 단추 앞에 공백을 삽입 하 고 다음 공간을 닫습니다.|단추를 오른쪽으로 끌고 다음 단추 중간에 겹쳐질 때까지 아래로 끕니다.|
|도구 모음의 단추 사이에 공백을 제거 하려면|공간의 한 쪽에서 단추를 선택 합니다. 다음 단추 중간에 겹쳐질 때까지 공간 반대쪽의 단추 쪽으로 끕니다.|

> [!NOTE]
> 끌어 온 단추 옆에 공백이 없는 경우 단추를 인접 한 단추 보다 절반 이상으로 끌면 **도구 모음 편집기** 에서 끌고 있는 단추의 반대쪽에 공백을 삽입 하 게 됩니다.

#### <a name="to-change-the-properties-of-a-toolbar-button"></a>도구 모음 단추의 속성을 변경 하려면

1. C + + 프로젝트에서 도구 모음 단추를 선택 합니다.

1. [속성 창](/visualstudio/ide/reference/properties-window)에서 **id** 속성에 새 id를 입력 하거나 드롭다운 목록을 사용 하 여 새 **id**를 선택 합니다.

#### <a name="to-create-a-tool-tip-for-a-toolbar-button"></a>도구 모음 단추에 대 한 도구 설명을 만들려면

1. 도구 모음 단추를 선택 합니다.

1. [속성 창의](/visualstudio/ide/reference/properties-window) **프롬프트** 필드에서 상태 표시줄에 대 한 단추에 대 한 설명을 추가 하 고 메시지 뒤에을 추가 하 `\n` 고 도구 설명 이름을 추가 합니다.

예를 들어 **워드 패드**에서 **인쇄** 단추에 대 한 도구 설명을 보려면 다음을 수행 합니다.

1. **워드 패드**를 엽니다.

1. 마우스 포인터를 **인쇄** 도구 모음 단추 위로 가져가면 `Print` 마우스 포인터 아래에 이제 라는 단어가 표시 됩니다.

1. **워드 패드** 창 맨 아래에 있는 상태 표시줄을 살펴보면 이제 텍스트를 표시 하는 것을 알 수 `Prints the active document` 있습니다.

`Print` 는 도구 설명 이름이 고는 `Prints the active document` 상태 표시줄 단추에 대 한 설명입니다.

**도구 모음 편집기**를 사용 하 여이 효과를 적용 하려면 **Prompt** 속성을로 설정 `Prints the active document\nPrint` 합니다.

## <a name="requirements"></a>요구 사항

MFC 또는 ATL

## <a name="see-also"></a>참고 항목

[리소스 편집기](../windows/resource-editors.md)\
[메뉴 및 기타 리소스](/windows/win32/menurc/resources)
