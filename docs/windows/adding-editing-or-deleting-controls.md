---
description: '자세히 알아보기: 방법: 컨트롤 추가, 편집 또는 삭제 (c + +)'
title: '방법: 컨트롤 추가, 편집 또는 삭제 (c + +)'
ms.date: 02/15/2019
f1_keywords:
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- Dialog Editor [C++], creating controls
- dialog boxes [C++], adding controls to
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
- controls [C++], adding multiple
- dialog box controls [C++], size
- controls [C++], sizing
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls [C++], editing properties
- dialog box controls [C++], deleting
- controls [C++], deleting
- Dialog Editor [C++], default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls [C++], events
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog Editor [C++], defining member variables for controls
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 73cef03f-5c8c-456a-87d1-1458dff185cf
ms.openlocfilehash: 4ff0f3bdf7e4da935cba3437900e2319218de771
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337820"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>방법: 컨트롤 추가, 편집 또는 삭제 (c + +)

대화 상자 **편집기** 를 사용 하 여 대화 상자에서 컨트롤을 추가, 크기 조정, 편집 및 삭제할 수 있습니다. 컨트롤의 ID와 같은 컨트롤의 속성을 편집 하거나 런타임에 초기에 표시할지 여부를 편집할 수도 있습니다.

대화 **상자 편집기에서** 작업 하는 경우 대화 상자 **편집기** 탭이 [도구 상자 창](/visualstudio/ide/reference/toolbox) 에 표시 됩니다. 쉽게 사용할 수 있도록 **도구 상자** 창을 사용자 지정할 수도 있습니다. 자세한 내용은 [도구 상자 사용](/visualstudio/ide/using-the-toolbox) 및 [도구 상자 창 표시/숨기기](./dialog-editor.md)를 참조 하세요.

> [!TIP]
> 대부분의 경우 **대화 상자 편집기** 를 사용 하는 동안 마우스 오른쪽 단추를 선택 하 여 자주 사용 하는 명령의 바로 가기 메뉴를 표시할 수 있습니다.

## <a name="add-controls"></a>컨트롤 추가

### <a name="to-add-a-control"></a>컨트롤을 추가 하려면

1. 대화 상자 탭 창이 편집기 프레임에서 현재 문서인지 확인합니다. 대화 상자가 현재 문서가 아닌 경우 **도구 상자** 에 **대화 상자 편집기 탭** 이 표시 되지 않습니다.

1. **도구 상자** 창의 **대화 상자 편집기** 탭에서 원하는 컨트롤을 선택 하 고 다음 중 하나를 선택 합니다.

   - 컨트롤을 배치 하려는 위치에서 대화 상자를 선택 하면 컨트롤이 선택 된 위치에 표시 됩니다.

   - **도구 상자** 창에서 대화 상자의 위치로 컨트롤을 끌어서 놓습니다. 그런 다음 컨트롤을 이동 하거나 크기와 셰이프를 변경할 수 있습니다.

   - **도구 상자** 창에서 컨트롤을 두 번 클릭 하면 대화 상자에 나타납니다. 원하는 위치로 컨트롤의 위치를 변경 합니다.

### <a name="to-add-multiple-controls"></a>여러 컨트롤을 추가 하려면

1. **Ctrl** 키를 누른 채 **도구 상자** 창에서 컨트롤을 선택 합니다.

1. **Ctrl** 키를 놓고 특정 컨트롤을 추가할 횟수 만큼 대화 상자를 선택 합니다.

1. **Esc** 키를 눌러 컨트롤 배치를 중지 합니다.

### <a name="to-size-a-control-while-you-add-it"></a>컨트롤을 추가 하는 동안 컨트롤의 크기를 조정 하려면

1. **도구 상자** 창에서 컨트롤을 선택 합니다.

1. 대화 상자에 새 컨트롤의 왼쪽 위 모퉁이가 위치할 십자 모양으로 표시 되는 커서를 놓습니다.

1. 마우스 단추를 누르고 있으면 대화 상자에서 컨트롤의 왼쪽 위 모퉁이를 고정 합니다. 그런 다음 컨트롤이 원하는 크기가 될 때까지 커서를 오른쪽 아래로 끕니다.

   > [!NOTE]
   > 그리고 있는 컨트롤의 네 모퉁이 중 하나를 고정할 수 있습니다. 이 절차에서는 왼쪽 위 모서리를 예로 사용 했습니다.

1. 마우스 단추를 놓습니다. 지정 된 크기의 대화 상자에 컨트롤이 있습니다.

> [!TIP]
> 컨트롤의 테두리에서 크기 조정 핸들을 이동 하 여 대화 상자에 컨트롤을 놓은 후 컨트롤의 크기를 조정할 수 있습니다. 자세한 내용은 [개별 컨트롤 크기 조정](./arrangement-of-controls-on-dialog-boxes.md)을 참조 하세요.

### <a name="to-add-a-custom-control"></a>사용자 지정 컨트롤을 추가하려면

대화 상자에 사용자 지정 컨트롤을 추가할 수 있습니다. **도구 상자** 에서 **사용자 지정 컨트롤** 아이콘을 선택 하 고 대화 상자로 끌어 놓습니다. 컨트롤을 추가 하려면 `Syslink` 사용자 지정 컨트롤을 추가한 다음 컨트롤의 **클래스** 속성을로 변경 `Syslink` 합니다. 이 작업을 수행 하면 속성이 새로 고쳐 `Syslink` 컨트롤 속성이 표시 됩니다. MFC 래퍼 클래스에 대 한 자세한 내용은 [Clinkctrl](../mfc/reference/clinkctrl-class.md)를 참조 하세요.

## <a name="edit-controls"></a>편집 컨트롤

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>컨트롤이 나 컨트롤의 속성을 편집 하려면

1. 대화 상자에서 수정 하려는 컨트롤을 선택 합니다.

   > [!NOTE]
   > 여러 컨트롤을 선택한 경우에는 선택한 컨트롤에 공통 된 속성만 편집할 수 있습니다.

1. [속성 창](/visualstudio/ide/reference/properties-window)에서 컨트롤의 속성을 변경 합니다.

   > [!NOTE]
   > 단추, 라디오 단추 또는 확인란 컨트롤에 대 한 **Bitmap** 속성을 **True** 로 설정 하면 컨트롤에 대 한 스타일 BS_BITMAP 구현 됩니다. 자세한 내용은 [단추 스타일](../mfc/reference/styles-used-by-mfc.md#button-styles)을 참조 하세요. 비트맵을 컨트롤과 연결 하는 예제는 [Cbutton:: SetBitmap](../mfc/reference/cbutton-class.md#setbitmap)을 참조 하세요. **대화 상자 편집기** 에서 비트맵은 컨트롤에 나타나지 않습니다.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>컨트롤의 속성에 대 한 변경 내용을 취소 하려면

1. **대화 상자 편집기** 에서 컨트롤에 포커스가 있는지 확인 합니다.

1. 메뉴 **편집**  >  **취소** 로 이동 합니다. 컨트롤에 포커스가 없으면 **실행 취소** 명령을 사용할 수 없습니다.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>(단추 이외의) 대화 상자 컨트롤에 대해 멤버 변수를 정의하려면

> [!NOTE]
> 이 프로세스는 MFC 프로젝트의 대화 상자 컨트롤에만 적용 됩니다. ATL 프로젝트는 **새 Windows 메시지 및 이벤트 처리기** 대화 상자를 사용 해야 합니다. 자세한 내용은 [User-Interface 개체와 연결 된 메시지 유형](../mfc/reference/message-types-associated-with-user-interface-objects.md), [메시지 처리기 편집](../mfc/reference/editing-a-message-handler.md)및 [리플렉션된 메시지의 메시지 처리기 정의](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)를 참조 하세요.

1. [대화 상자 편집기](dialog-editor.md)에서 컨트롤을 선택 합니다.

1. **Ctrl** 키를 누른 상태에서 대화 상자 컨트롤을 두 번 클릭 합니다.

   [멤버 변수 추가 마법사](../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard) 가 나타납니다.

1. **멤버 변수 추가** 마법사에서 적절 한 정보를 입력 합니다. 자세한 내용은 [대화 상자 데이터 교환](../mfc/dialog-data-exchange.md)을 참조 하세요.

1. **확인** 을 선택 하 여 **대화 상자 편집기** 로 돌아갑니다.

> [!TIP]
> 대화 상자 컨트롤에서 기존 처리기로 이동하려면 컨트롤을 두 번 클릭합니다.

[MFC 클래스 마법사](../mfc/reference/mfc-class-wizard.md) 의 **멤버 변수** 탭을 사용 하 여 지정 된 클래스에 대 한 새 멤버 변수를 추가 하 고 이미 정의 된 멤버 변수를 볼 수도 있습니다.

## <a name="delete-controls"></a>컨트롤 삭제

대화 상자에서 컨트롤을 선택한 다음 **delete** 키를 누르거나 메뉴에서 삭제 **편집** 으로 이동  >  합니다.

## <a name="other-issues"></a>기타 이슈

### <a name="troubleshooting"></a>문제 해결

대화 상자에 공용 컨트롤이 나 rich edit 컨트롤을 추가한 후에는 대화 상자를 테스트할 때 표시 되지 않습니다. 또는 대화 자체가 나타나지 않습니다. 예를 들어:

1. Win32 프로젝트를 만들고 응용 프로그램 설정을 수정 하 여 콘솔 앱이 아닌 Windows 응용 프로그램을 만듭니다.

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 *.rc* 파일을 두 번 클릭 합니다.

1. 대화 상자 옵션 아래에서 **정보** 상자를 두 번 클릭 합니다.

1. 대화 상자에 **IP 주소 컨트롤** 을 추가 합니다.

1. 모두 저장 하 고 **다시 빌드합니다**.

1. 프로그램을 실행 합니다.

1. 대화 상자의 **도움말** 메뉴에서 **정보** 명령을 선택 하 고 아니요 대화 상자를 표시 합니다.

현재 대화 상자에 다음 공용 컨트롤 또는 rich edit 컨트롤을 끌어서 놓으면 **대화 상자 편집기** 가 자동으로 프로젝트에 코드를 추가 하지 않습니다. 이 문제가 발생 하는 경우에도 Visual Studio에서 오류 또는 경고를 제공 하지 않습니다. 수정 하려면 컨트롤에 대 한 코드를 수동으로 추가 합니다.

:::row:::
   :::column span="":::
      애니메이션 제어 \
      사용자 지정 컨트롤 \
      날짜 시간 선택 \
      확장 된 콤보 상자
   :::column-end:::
   :::column span="":::
      핫 키 \
      IP 주소 제어 \
      목록 컨트롤 \
      Month Calendar
   :::column-end:::
   :::column span="":::
      진행률 컨트롤 \
      Rich Edit 2.0 Control \
      Rich Edit 컨트롤 \
      슬라이더 컨트롤
   :::column-end:::
   :::column span="":::
      Spin 컨트롤 \
      탭 컨트롤 \
      트리 컨트롤
   :::column-end:::
:::row-end:::

대화 상자에서 공용 컨트롤을 사용 하려면 대화 상자를 만들기 전에 [InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) 를 호출 해야 `AFXInitCommonControls` 합니다.

RichEdit 컨트롤을 사용 하려면를 호출 해야 `LoadLibrary` 합니다. 자세한 내용은 Windows SDK의 [Rich Edit 컨트롤 정보](/windows/win32/Controls/about-rich-edit-controls) 및 [Rich edit 컨트롤 개요](../mfc/overview-of-the-rich-edit-control.md)를 참조 하세요.

> [!NOTE]
> MFC에서 RichEdit 컨트롤을 사용 하려면 먼저 [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) 를 호출 하 여 RichEdit 2.0 컨트롤 (RICHED20.DLL)을 로드 하거나 [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) 를 호출 하 여 이전 RichEdit 1.0 컨트롤 (RICHED32.DLL)을 로드 해야 합니다.
>
> 이전 RichEdit 1.0 컨트롤과 함께 현재 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) 클래스를 사용할 수 있지만 `CRichEditCtrl` RichEdit 2.0 컨트롤을 지원 하도록 설계 되었습니다. RichEdit 1.0 및 RichEdit 2.0는 유사 하기 때문에 대부분의 메서드는 작동 합니다. 그러나 1.0 컨트롤과 2.0 컨트롤 간에는 몇 가지 차이점이 있으므로 일부 메서드가 제대로 작동 하지 않거나 작동 하지 않을 수 있습니다.

## <a name="insert-activex-controls"></a>ActiveX 컨트롤 삽입

Visual Studio에서는 ActiveX 컨트롤을 대화 상자에 삽입할 수 있습니다. 자세한 내용은 [MFC Activex 컨트롤](../mfc/mfc-activex-controls.md) 및 [activex 컨트롤 컨테이너](../mfc/activex-control-containers.md)를 참조 하세요.

**Activex 컨트롤 삽입** 대화 상자를 사용 하면 대화 상자 [편집기](dialog-editor.md)를 사용 하는 동안 activex 컨트롤을 대화 상자에 삽입할 수 있습니다. 이 대화 상자에는 다음과 같은 속성이 있습니다.

|속성|설명|
|---|---|
|**ActiveX 컨트롤**|ActiveX 컨트롤 목록을 표시 합니다.<br/><br/>이 대화 상자에서 컨트롤을 삽입 해도 래퍼 클래스는 생성 되지 않습니다. 래퍼 클래스가 필요한 경우 [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code) 를 사용 하 여 래퍼 클래스를 만듭니다. [클래스 추가](../ide/adding-a-class-visual-cpp.md)를 참조 하세요.<br/><br/>이 대화 상자에 ActiveX 컨트롤이 표시 되지 않는 경우 공급 업체의 지침에 따라 컨트롤을 설치 해 보십시오.|
|**Path**|ActiveX 컨트롤을 찾은 파일을 표시 합니다.|

> [!CAUTION]
> 시스템에 일부 ActiveX 컨트롤을 배포하지 못할 수 있습니다. 컨트롤을 설치한 소프트웨어에 대 한 사용권 계약을 참조 하거나 소프트웨어 회사에 문의 하십시오.

### <a name="to-add-an-activex-control"></a>ActiveX 컨트롤을 추가 하려면

1. **대화 상자 편집기** 에서 대화 상자를 엽니다.

1. 대화 상자의 본문에서 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 **ActiveX 컨트롤 삽입** 을 선택 합니다.

   시스템의 모든 ActiveX 컨트롤을 표시 하는 **Activex 컨트롤 삽입** 대화 상자가 나타납니다. 대화 상자 아래쪽에 ActiveX 컨트롤 파일 경로가 표시됩니다.

1. 대화 상자에 추가할 컨트롤을 선택 하 고 **확인** 을 선택 합니다.

   컨트롤이 대화 상자에 표시되고, 이 대화 상자에서 컨트롤을 편집하거나 다른 컨트롤처럼 컨트롤용 처리기를 만들 수 있습니다.

> [!TIP]
> **대화 상자 편집기** 의 바로 가기 메뉴를 사용 하 여 등록 된 activex 컨트롤을 대화 상자에 빠르게 추가 하거나 쉽게 액세스할 수 있도록 **도구 상자** 창에 activex 컨트롤을 추가 해 볼 수 있습니다.

### <a name="to-edit-properties-for-an-activex-control"></a>ActiveX 컨트롤에 대 한 속성을 편집 하려면

독립 공급 업체에서 제공 하는 ActiveX 컨트롤은 고유한 속성 및 특성을 제공 합니다. 이러한 속성은 **속성** 창에 표시 됩니다. ActiveX 컨트롤의 작성기에서 만든 속성 페이지는 **속성 페이지** 대화 상자에 표시 됩니다. 특정 ActiveX 컨트롤에 대 한 **속성 페이지** 를 보려면 [속성 창](/visualstudio/ide/reference/properties-window))에서 **속성 페이지** 단추를 선택 합니다.

- **ActiveX** 컨트롤을 선택 하 고 메뉴 **보기**  >  **속성 페이지로** 이동 하 여 속성을 확인 합니다. 속성 페이지에서 필요에 따라 변경 합니다.

   Activex 컨트롤의 일부로 제공 되는 속성 시트에 따라 ActiveX 컨트롤에 대 한 속성 페이지에 다양 한 탭이 표시 됩니다.

> [!NOTE]
> 이 절차는 속성 페이지를 사용 하 여 ActiveX 컨트롤을 편집 하는 데 적용 됩니다. 새 **속성** 창에서 ActiveX 속성을 찾아보고 편집할 수도 있습니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[대화 상자 컨트롤 관리](controls-in-dialog-boxes.md)<br/>
[방법: 컨트롤 레이아웃](arrangement-of-controls-on-dialog-boxes.md)<br/>
[방법: 컨트롤 액세스 및 값 정의](defining-mnemonics-access-keys.md)

<!-- excluded links
[Mapping Messages to Functions](../mfc/reference/mapping-messages-to-functions.md)<br/>
[Adding Functionality with Code Wizards](../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Adding a Class](../ide/adding-a-class-visual-cpp.md)<br/>
[Adding a Member Function](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler](../mfc/reference/adding-an-mfc-message-handler.md)
[Declaring a Variable Based on Your New Control Class](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)<br/>
-->
