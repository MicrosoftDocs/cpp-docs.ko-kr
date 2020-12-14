---
description: '자세한 정보: 방법: Windows Forms 컨트롤에 명령 라우팅 추가'
title: '방법: Windows Forms 컨트롤에 명령 라우팅 추가'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
ms.openlocfilehash: b46087d7df3da5f402432731db4b994b257a385b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335422"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>방법: Windows Forms 컨트롤에 명령 라우팅 추가

[CWinFormsView](../mfc/reference/cwinformsview-class.md) 는 명령 및 업데이트 명령 UI 메시지를 사용자 정의 컨트롤에 라우팅하여 MFC 명령 (예: 프레임 메뉴 항목 및 도구 모음 단추)을 처리할 수 있도록 합니다.

다음 예제와 같이 사용자 정의 컨트롤은 [ICommandTarget:: Initialize](../mfc/reference/icommandtarget-interface.md#initialize) 를 사용 하 여에 명령 소스 개체에 대 한 참조를 저장 합니다 `m_CmdSrc` . 을 사용 하려면 `ICommandTarget` mfcmifc80.dll에 대 한 참조를 추가 해야 합니다.

`CWinFormsView` 관리 되는 사용자 정의 컨트롤에 전달 하 여 일반적인 여러 MFC 뷰 알림을 처리 합니다. 이러한 알림에는 [Oninitialupdate](../mfc/reference/iview-interface.md#oninitialupdate), [OnUpdate](../mfc/reference/iview-interface.md#onupdate) 및 [oninitialupdate](../mfc/reference/iview-interface.md#onactivateview) 메서드가 포함 됩니다.

이 항목에서는 이전 [에 방법: 대화 상자에서 사용자 정의 컨트롤 및 호스트 만들기](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) 및 [방법: 사용자 정의 컨트롤 및 호스트 MDI 뷰 만들기](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)를 완료 했다고 가정 합니다.

### <a name="to-create-the-mfc-host-application"></a>MFC 호스트 응용 프로그램을 만들려면

1. [방법: 사용자 정의 컨트롤 및 호스트 만들기 대화 상자](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)에서 만든 Windows Forms 컨트롤 라이브러리를 엽니다.

1. **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가**, **참조** 를 차례로 선택한 다음 Microsoft Visual Studio 10.0 \ VC\atlmfc\lib.로 이동 하 여 수행할 수 있는 mfcmifc80.dll에 대 한 참조를 추가 합니다.

1. UserControl1.Designer.cs를 열고 다음 using 문을 추가 합니다.

    ```
    using Microsoft.VisualC.MFC;
    ```

1. 또한 UserControl1.Designer.cs에서 다음 줄을 변경 합니다.

    ```
    partial class UserControl1
    ```

   아래와 같이 변환합니다.

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. 다음에 대 한 클래스 정의의 첫 번째 줄로이를 추가 합니다 `UserControl1` .

    ```
    private ICommandSource m_CmdSrc;
    ```

1. 에 다음 메서드 정의를 추가 합니다 `UserControl1` . (다음 단계에서 MFC 컨트롤의 ID를 만듭니다.)

    ```
    public void Initialize (ICommandSource cmdSrc)
    {
       m_CmdSrc = cmdSrc;
       // need ID of control in MFC dialog and callback function
       m_CmdSrc.AddCommandHandler(32771, new CommandHandler (singleMenuHandler));
    }

    private void singleMenuHandler (uint cmdUI)
    {
       // User command handler code
       System.Windows.Forms.MessageBox.Show("Custom menu option was clicked.");
    }
    ```

1. [방법: 사용자 정의 컨트롤 및 호스트 MDI 뷰 만들기](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)에서 만든 MFC 응용 프로그램을 엽니다.

1. 을 호출 하는 메뉴 옵션을 추가 `singleMenuHandler` 합니다.

   **리소스 뷰** (Ctrl + Shift + E)로 이동 하 고 **메뉴** 폴더를 확장 한 다음 **IDR_MFC02TYPE** 을 두 번 클릭 합니다. 그러면 메뉴 편집기가 표시 됩니다.

   **보기** 메뉴의 아래쪽에 메뉴 옵션을 추가 합니다. **속성** 창에서 메뉴 옵션의 ID를 확인 합니다. 파일을 저장합니다.

   **솔루션 탐색기** 에서 resource.h 파일을 열고 방금 추가한 메뉴 옵션에 대 한 ID 값을 복사한 다음 c # 프로젝트의 메서드에서 호출에 첫 번째 매개 변수로 해당 값을 붙여넣습니다 `m_CmdSrc.AddCommandHandler` `Initialize` ( `32771` 필요한 경우 바꾸기).

1. 프로젝트를 빌드하고 실행합니다.

   **빌드** 메뉴에서 **솔루션 빌드** 를 클릭합니다.

   **디버그** 메뉴에서 **디버깅 하지 않고 시작** 을 클릭 합니다.

   추가한 메뉴 옵션을 선택 합니다. .Dll의 메서드가 호출 됩니다.

## <a name="see-also"></a>참고 항목

[Windows Forms 사용자 정의 컨트롤을 MFC 뷰로 호스팅](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[ICommandSource 인터페이스](../mfc/reference/icommandsource-interface.md)<br/>
[ICommandTarget 인터페이스](../mfc/reference/icommandtarget-interface.md)
