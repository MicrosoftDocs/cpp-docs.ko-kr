---
description: '자세한 정보: 연습: 응용 프로그램에 CTaskDialog 추가'
title: '연습: 애플리케이션에 CTaskDialog 추가'
ms.date: 04/25/2019
helpviewer_keywords:
- CTaskDialog, adding
- walkthroughs [MFC], dialogs
ms.assetid: 3a62abb8-2d86-4bec-bdb8-5784d5f9a9f8
ms.openlocfilehash: f7462551af785b85156f3f0b0f83b2ff3ddbf4c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159897"
---
# <a name="walkthrough-adding-a-ctaskdialog-to-an-application"></a>연습: 애플리케이션에 CTaskDialog 추가

이 연습에서는 [CTaskDialog Class](../mfc/reference/ctaskdialog-class.md) 를 소개하고 이를 애플리케이션에 추가하는 방법을 보여 줍니다.

는 `CTaskDialog` Windows Vista 이상에서 windows 메시지 상자를 대체 하는 작업 대화 상자입니다. `CTaskDialog` 는 원래 메시지 상자를 개선하고 기능을 추가합니다. Windows 메시지 상자는 Visual Studio에서 계속 지원 됩니다.

> [!NOTE]
> Windows Vista 이전 버전은를 지원 하지 않습니다 `CTaskDialog` . 이전 버전의 Windows에서 애플리케이션을 실행하는 사용자에게 메시지를 표시하려면 다른 대화 상자 옵션을 프로그래밍해야 합니다. 정적 메서드 [CTaskDialog::IsSupported](../mfc/reference/ctaskdialog-class.md#issupported) 를 사용하여 런타임에 사용자 컴퓨터에서 `CTaskDialog`에서 Windows 메시지 상자를 대체하는 작업 대화 상자입니다. 또한 `CTaskDialog` 는 애플리케이션이 유니코드 라이브러리와 함께 빌드된 경우에만 사용할 수 있습니다.

`CTaskDialog` 는 정보를 수집하고 표시할 수 있도록 여러 선택적 요소를 지원합니다. 예를 들어 `CTaskDialog` 는 명령 링크, 사용자 지정 단추, 사용자 지정 아이콘 및 바닥글을 표시할 수 있습니다. 또한 `CTaskDialog` 에는 사용자가 선택한 선택적 요소를 확인하기 위해 작업 대화 상자를 쿼리하는 데 사용할 수 있는 여러 메서드가 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- Visual Studio 2010 이상

- Windows Vista 이상

## <a name="replacing-a-windows-message-box-with-a-ctaskdialog"></a>Windows 메시지 상자를 CTaskDialog로 대체

다음 절차에서는 Windows 메시지 상자를 대체하는 `CTaskDialog`의 가장 기본적인 사용법을 보여 줍니다. 또한 이 예제에서는 작업 대화 상자와 연결된 아이콘을 변경합니다. 아이콘을 변경 하면가 `CTaskDialog` Windows 메시지 상자와 동일 하 게 표시 됩니다.

### <a name="to-replace-a-windows-message-box-with-a-ctaskdialog"></a>Windows 메시지 상자를 CTaskDialog로 대체하려면

1. **Mfc 응용 프로그램 마법사** 를 사용 하 여 모든 기본 설정을 사용 하 여 mfc 응용 프로그램을 만듭니다. 사용 중인 Visual Studio 버전에 대 한 마법사를 여는 방법에 대 한 지침은 [연습: 새 MFC 셸 컨트롤 사용](walkthrough-using-the-new-mfc-shell-controls.md) 을 참조 하세요.

1. *MyProject* 를 호출 합니다.

1. **솔루션 탐색기** 를 사용하여 MyProject.cpp 파일을 엽니다.

1. 포함 목록 뒤에 `#include "afxtaskdialog.h"` 를 추가합니다.

1. `CMyProjectApp::InitInstance`메서드를 찾습니다. `return TRUE;` 문 앞에 다음 코드 줄을 삽입합니다. 이 코드는 Windows 메시지 상자 또는 `CTaskDialog`에서 사용하는 문자열을 만듭니다.

    ```cpp
    CString message("My message to the user");
    CString dialogTitle("My Task Dialog title");
    CString emptyString;
    ```

1. 4단계의 코드 뒤에 다음 코드를 추가합니다. 이 코드를 사용하면 사용자 컴퓨터에서 `CTaskDialog`가 지원됩니다. 대화 상자가 지원 되지 않는 경우 응용 프로그램에 Windows 메시지 상자가 대신 표시 됩니다.

    ```cpp
    if (CTaskDialog::IsSupported())
    {

    }
    else
    {
        AfxMessageBox(message);
    }
    ```

1. 5 단계의 문 뒤에 있는 대괄호 사이에 다음 코드를 삽입 합니다 **`if`** . 이 코드는 `CTaskDialog`를 만듭니다.

    ```cpp
    CTaskDialog taskDialog(message, emptyString, dialogTitle, TDCBF_OK_BUTTON);
    ```

1. 그 다음 줄에 다음 코드를 추가합니다. 이 코드는 경고 아이콘을 설정합니다.

    ```cpp
    taskDialog.SetMainIcon(TD_WARNING_ICON);
    ```

1. 그 다음 줄에 다음 코드를 추가합니다. 이 코드는 작업 대화 상자를 표시합니다.

    ```cpp
    taskDialog.DoModal();
    ```

에서 `CTaskDialog` Windows 메시지 상자와 동일한 아이콘을 표시 하지 않으려면 7 단계를 방지할 수 있습니다. 이 단계를 방지 하는 경우 `CTaskDialog` 응용 프로그램에 아이콘이 표시 되지 않습니다.

애플리케이션을 컴파일하고 실행합니다. 애플리케이션이 시작된 후 작업 대화 상자가 표시됩니다.

## <a name="adding-functionality-to-the-ctaskdialog"></a>CTaskDialog에 기능 추가

다음 절차에서는 이전 절차에서 만든 `CTaskDialog` 에 기능을 추가하는 방법을 보여 줍니다. 예제 코드는 사용자의 선택에 따라 구체적인 지침을 실행하는 방법을 보여 줍니다.

### <a name="to-add-functionality-to-the-ctaskdialog"></a>CTaskDialog에 기능을 추가하려면

1. **리소스 뷰** 로 이동합니다. **리소스 뷰** 표시 되지 않으면 **보기** 메뉴에서 열 수 있습니다.

1. **문자열 테이블** 폴더를 선택할 수 있을 때까지 **리소스 뷰** 를 확장합니다. 폴더를 확장하고 **문자열 테이블** 항목을 두 번 클릭합니다.

1. 문자열 테이블의 아래쪽으로 스크롤한 다음 새 항목을 추가합니다. ID를 `TEMP_LINE1`로 변경합니다. 캡션을 **Command Line 1** 로 설정합니다.

1. 다른 새 항목을 추가합니다. ID를 `TEMP_LINE2`로 변경합니다. 캡션을 **Command Line 2** 로 설정합니다.

1. MyProject.cpp로 다시 이동합니다.

1. `CString emptyString;`뒤에 다음 코드를 추가합니다.

    ```cpp
    CString expandedLabel("Hide extra information");
    CString collapsedLabel("Show extra information");
    CString expansionInfo("This is the additional information to the user,\nextended over two lines.");
    ```

1. `taskDialog.DoModal()` 문을 찾아서 다음 코드로 바꿉니다. 이 코드는 작업 대화 상자를 업데이트하고 새 컨트롤을 추가합니다.

    ```cpp
    taskDialog.SetMainInstruction(L"Warning");
    taskDialog.SetCommonButtons(
        TDCBF_YES_BUTTON | TDCBF_NO_BUTTON | TDCBF_CANCEL_BUTTON);
    taskDialog.LoadCommandControls(TEMP_LINE1, TEMP_LINE2);
    taskDialog.SetExpansionArea(
        expansionInfo, collapsedLabel, expandedLabel);
    taskDialog.SetFooterText(L"This is the a small footnote to the user");
    taskDialog.SetVerificationCheckboxText(L"Remember your selection");
    ```

1. 사용자에게 작업 대화 상자를 표시하고 사용자가 선택한 항목을 검색하는 다음 코드 줄을 추가합니다.

    ```cpp
    INT_PTR result = taskDialog.DoModal();
    ```

1. `taskDialog.DoModal()`에 대한 호출 뒤에 다음 코드를 삽입합니다. 이 코드 섹션은 사용자의 입력을 처리합니다.

    ```cpp
    if (taskDialog.GetVerificationCheckboxState())
    {
        // PROCESS IF the user selects the verification checkbox
    }

    switch (result)
    {
    case TEMP_LINE1:
        // PROCESS IF the first command line
        break;
    case TEMP_LINE2:
        // PROCESS IF the second command line
        break;
    case IDYES:
        // PROCESS IF the user clicks yes
        break;
    case IDNO:
        // PROCESS IF the user clicks no
        break;
    case IDCANCEL:
        // PROCESS IF the user clicks cancel
        break;
    default:
        // This case should not be hit because closing
        // the dialog box results in IDCANCEL
        break;
    }
    ```

9 단계의 코드에서로 시작 하는 주석을 `PROCESS IF` 지정 된 조건에 따라 실행 하려는 코드로 바꿉니다.

애플리케이션을 컴파일하고 실행합니다. 새 컨트롤 및 추가 정보를 사용하는 작업 대화 상자가 애플리케이션에 표시됩니다.

## <a name="displaying-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>CTaskDialog 개체를 만들지 않고 CTaskDialog 표시

다음 절차에서는 `CTaskDialog` 개체를 만들지 않고 `CTaskDialog` 를 표시하는 방법을 보여 줍니다. 이 예제에서는 이전 절차를 계속 진행합니다.

### <a name="to-display-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>CTaskDialog 개체를 만들지 않고 CTaskDialog를 표시하려면

1. MyProject 파일이 아직 열려 있지 않으면 엽니다.

1. `if (CTaskDialog::IsSupported())` 문에 대한 오른쪽 대괄호로 이동합니다.

1. 문의 닫는 대괄호 바로 앞에 다음 코드를 삽입 합니다 **`if`** ( **`else`** 블록 앞).

    ```cpp
    HRESULT result2 = CTaskDialog::ShowDialog(L"My error message",
        L"Error",
        L"New Title",
        TEMP_LINE1,
        TEMP_LINE2);
    ```

애플리케이션을 컴파일하고 실행합니다. 두 개의 작업 대화 상자가 애플리케이션에 표시됩니다. 첫 번째 대화 상자는 **CTaskDialog 프로시저에 기능을 추가 하** 는 것입니다. 두 번째 대화 상자는 마지막 절차에서 가져온 것입니다.

이러한 예제는에 사용 가능한 모든 옵션을 보여 주지는 `CTaskDialog` 않지만 시작 하는 데 도움이 됩니다. 클래스에 대한 전체 설명은 [CTaskDialog Class](../mfc/reference/ctaskdialog-class.md) 를 참조하세요.

## <a name="see-also"></a>참고 항목

[대화 상자](../mfc/dialog-boxes.md)<br/>
[CTaskDialog 클래스](../mfc/reference/ctaskdialog-class.md)<br/>
[CTaskDialog:: CTaskDialog](../mfc/reference/ctaskdialog-class.md#ctaskdialog)
