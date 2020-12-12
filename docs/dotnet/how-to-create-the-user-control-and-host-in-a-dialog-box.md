---
description: '자세히 알아보기: 방법: 대화 상자에서 사용자 정의 컨트롤 및 호스트 만들기'
title: '방법: 대화 상자에 사용자 정의 컨트롤 및 호스트 만들기'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
ms.openlocfilehash: 400906344f47f7100e52319adb37c39d1fb370e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283967"
---
# <a name="how-to-create-the-user-control-and-host-in-a-dialog-box"></a>방법: 대화 상자에 사용자 정의 컨트롤 및 호스트 만들기

이 문서의 단계에서는 대화 상자 기반 ([CDialog 클래스](../mfc/reference/cdialog-class.md)) MICROSOFT FOUNDATION CLASSES (mfc) 프로젝트를 만들지만 기존 mfc 대화 상자에 Windows Forms 컨트롤에 대 한 지원을 추가할 수도 있습니다.

### <a name="to-create-the-net-user-control"></a>.NET 사용자 정의 컨트롤을 만들려면

1. 이라는 Visual c # Windows Forms 컨트롤 라이브러리 프로젝트를 만듭니다 `WindowsFormsControlLibrary1` .

   **파일** 메뉴에서 **새로 만들기** 를 클릭하고 **프로젝트** 를 클릭합니다. **Visual c #** 폴더에서 **Windows Forms 컨트롤 라이브러리** 를 선택 합니다.

   `WindowsFormsControlLibrary1` **확인을** 클릭 하 여 프로젝트 이름을 그대로 적용 합니다.

   기본적으로 .NET 컨트롤의 이름은 `UserControl1` 입니다.

1. 에 자식 컨트롤을 추가 `UserControl1` 합니다.

   **도구 상자** 에서 **모든 Windows Forms** 목록을 엽니다. **단추** 컨트롤을 디자인 화면으로 끌어 옵니다 `UserControl1` .

   또한 **TextBox** 컨트롤을 추가 합니다.

1. **솔루션 탐색기** 에서 **UserControl1.Designer.cs** 를 두 번 클릭 하 여 편집을 위해 엽니다. 텍스트 상자 및 단추의 선언을에서로 변경 합니다 `private` `public` .

1. 프로젝트를 빌드합니다.

   **빌드** 메뉴에서 **솔루션 빌드** 를 클릭합니다.

### <a name="to-create-the-mfc-host-application"></a>MFC 호스트 응용 프로그램을 만들려면

1. MFC 응용 프로그램 프로젝트를 만듭니다.

   **파일** 메뉴에서 **새로 만들기** 를 클릭하고 **프로젝트** 를 클릭합니다. **Visual C++** 폴더에서 **MFC 응용 프로그램** 을 선택 합니다.

   **이름** 상자에 `MFC01`을 입력합니다. 솔루션 설정을 **솔루션에 추가** 로 변경 합니다. **확인** 을 클릭합니다.

   **MFC 응용 프로그램 마법사** 에서 응용 프로그램 종류에 대해 **대화 상자 기반** 을 선택 합니다. 나머지 기본 설정을 그대로 적용 하 고 **마침** 을 클릭 합니다. MFC 대화 상자를 포함 하는 MFC 응용 프로그램을 만듭니다.

1. MFC 대화 상자에 자리 표시자 컨트롤을 추가 합니다.

   **보기** 메뉴에서 **리소스 뷰** 를 클릭 합니다. **리소스 뷰** 에서 **대화 상자** 폴더를 확장 하 고를 두 번 클릭 `IDD_MFC01_DIALOG` 합니다. 대화 상자 리소스가 **리소스 편집기** 에 표시 됩니다.

   **도구 상자** 에서 **대화 상자 편집기** 목록을 엽니다. **정적 텍스트** 컨트롤을 대화 상자 리소스로 끌어 옵니다. **정적 텍스트** 컨트롤은 .net Windows Forms 컨트롤에 대 한 자리 표시자 역할을 합니다. 크기를 Windows Forms 컨트롤의 크기에 맞게 조정 합니다.

   **속성** 창에서 **정적 텍스트** 컨트롤의 **ID** 를로 변경 하 `IDC_CTRL1` 고 **TabStop** 속성을 **True** 로 변경 합니다.

1. CLR (공용 언어 런타임) 지원에 대 한 프로젝트를 구성 합니다.

   **솔루션 탐색기** 에서 MFC01 프로젝트 노드를 마우스 오른쪽 단추로 클릭 한 다음 **속성** 을 클릭 합니다.

   **속성 페이지** 대화 상자의 **구성 속성** 에서 **일반** 을 선택 합니다. **프로젝트 기본값** 섹션에서 **공용 언어 런타임 지원** 을 **공용 언어 런타임 지원 (/clr)** 으로 설정 합니다.

   **구성 속성** 에서 **c/c + +** 를 확장 하 고 **일반** 노드를 선택 합니다. **디버그 정보 형식을** **Program Database (/zi)** 로 설정 합니다.

   **코드 생성** 노드를 선택 합니다. **최소 다시 빌드 사용** 을 **아니요 (/gm-)** 로 설정 합니다. 또한 기본 **런타임 검사** 를 **기본** 으로 설정 합니다.

   **확인** 을 클릭하여 변경 내용을 적용합니다.

1. .NET 컨트롤에 대 한 참조를 추가 합니다.

   **솔루션 탐색기** 에서 MFC01 프로젝트 노드를 마우스 오른쪽 단추로 클릭 한 다음 **추가**, **참조** 를 클릭 합니다. **속성 페이지** 에서 **새 참조 추가** 를 클릭 하 고 **프로젝트** 탭 아래에서 **WindowsFormsControlLibrary1** 을 선택한 다음 **확인** 을 클릭 합니다. 그러면 프로그램에서 컴파일되도록 참조를 [/fu](../build/reference/fu-name-forced-hash-using-file.md) 컴파일러 옵션의 형태로 추가 합니다. 또한 \MFC01\ 프로젝트 폴더에 WindowsFormsControlLibrary1.dll 복사본을 넣고 프로그램이 실행 됩니다.

1. Stdafx.h에서 다음 줄을 찾습니다.

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   다음 줄을 추가 합니다.

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. 관리 되는 컨트롤을 만드는 코드를 추가 합니다.

   먼저 관리 되는 컨트롤을 선언 합니다. MFC01Dlg에서 대화 상자 클래스의 선언으로 이동 하 고 다음과 같이 보호 된 범위에서 사용자 정의 컨트롤에 대 한 데이터 멤버를 추가 합니다.

    ```
    class CMFC01Dlg : public CDialog
    {
       // ...
       // Data member for the .NET User Control:
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;
    ```

   그런 다음 관리 되는 컨트롤에 대 한 구현을 제공 합니다. MFC01Dlg에서, MFC 응용 프로그램 마법사에서 생성 된의 대화 상자 재정의 `CMFC01Dlg::DoDataExchange` ( `CAboutDlg::DoDataExchange` 동일한 파일에 있는)에서 다음 코드를 추가 하 여 관리 되는 컨트롤을 만들고이를 정적 자리 표시자 IDC_CTRL1에 연결 합니다.

    ```
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)
    {
       CDialog::DoDataExchange(pDX);
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);
    }
    ```

1. 프로젝트를 빌드하고 실행합니다.

   **솔루션 탐색기** 에서 **MFC01** 을 마우스 오른쪽 단추로 클릭 한 다음 **시작 프로젝트로 설정** 을 클릭 합니다.

   **빌드** 메뉴에서 **솔루션 빌드** 를 클릭합니다.

   **디버그** 메뉴에서 **디버깅 하지 않고 시작** 을 클릭 합니다. MFC 대화 상자에 Windows Forms 컨트롤이 표시 되어야 합니다.

## <a name="see-also"></a>참고 항목

[MFC 대화 상자에서 Windows Form 사용자 정의 컨트롤 호스팅](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)
