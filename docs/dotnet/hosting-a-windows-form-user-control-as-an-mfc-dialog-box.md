---
description: '자세히 알아보기: MFC 대화 상자로 Windows Form 사용자 정의 컨트롤 호스팅'
title: Windows Form 사용자 정의 컨트롤을 MFC 대화 상자로 호스팅
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
ms.openlocfilehash: 885b63e17140cca7983aeeed26e56eac47091a0d
ms.sourcegitcommit: 3987d9c39f5a5b4824303a48a6215984ce8949e8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99478060"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Windows Form 사용자 정의 컨트롤을 MFC 대화 상자로 호스팅

MFC는 [](../mfc/reference/cwinformsdialog-class.md) <xref:System.Windows.Forms.UserControl> 모달 또는 모덜리스 MFC 대화 상자에서 Windows Forms 사용자 정의 컨트롤 ()을 호스팅할 수 있도록 템플릿 클래스 CWinFormsDialog를 제공 합니다. `CWinFormsDialog` 는 MFC 클래스 [CDialog](../mfc/reference/cdialog-class.md)에서 파생 되므로 대화 상자를 모달 또는 모덜리스로 시작할 수 있습니다.

`CWinFormsDialog`를 사용 하 여 사용자 정의 컨트롤을 호스팅하는 프로세스는 [MFC 대화 상자에서 Windows Form 사용자 정의 컨트롤 호스팅](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)에 설명 된 프로세스와 비슷합니다. 그러나는 `CWinFormsDialog` 수동으로 프로그래밍할 필요가 없도록 사용자 정의 컨트롤의 초기화 및 호스팅을 관리 합니다.

MFC와 함께 사용 Windows Forms을 보여 주는 예제 응용 프로그램은 [mfc 및 Windows Forms 통합](https://download.cnet.com/MFC-and-WinForms-Integration/3000-2383_4-75453644.html)을 참조 하세요.

### <a name="to-create-the-mfc-host-application"></a>MFC 호스트 응용 프로그램을 만들려면

1. MFC 응용 프로그램 프로젝트를 만듭니다.

   **파일** 메뉴에서 **새로 만들기** 를 선택한 다음 **프로젝트** 를 클릭 합니다. **Visual C++** 폴더에서 **MFC 응용 프로그램** 을 선택 합니다.

   **이름** 상자에을 입력 하 `MFC03` 고 솔루션 설정을 **솔루션에 추가** 로 변경 합니다. **확인을** 클릭 합니다.

   **MFC 응용 프로그램 마법사** 에서 모든 기본값을 적용 한 다음 **마침** 을 클릭 합니다. 이렇게 하면 다중 문서 인터페이스를 사용 하 여 MFC 응용 프로그램을 만듭니다.

1. 프로젝트를 구성 합니다.

   **솔루션 탐색기** 에서 **MFC03** 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다. **속성 페이지** 대화 상자가 나타납니다.

   **속성 페이지** 대화 상자의 **구성 속성** 트리 컨트롤에서 **일반** 을 선택한 다음 **프로젝트 기본값** 섹션에서 **공용 언어 런타임 지원** 을 **공용 언어 런타임 지원 (/clr)** 으로 설정 합니다. **확인** 을 클릭합니다.

1. .NET 컨트롤에 대 한 참조를 추가 합니다.

   **솔루션 탐색기** 에서 **MFC03** 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가**, **참조** 를 선택 합니다. **속성 페이지** 에서 **새 참조 추가** 를 클릭 하 고 **프로젝트** 탭 아래에서 WindowsControlLibrary1을 선택한 다음 **확인** 을 클릭 합니다. 그러면 프로그램에서 컴파일되도록 참조를 [/fu](../build/reference/fu-name-forced-hash-using-file.md) 컴파일러 옵션의 형태로 추가 합니다. 또한 프로그램을 실행 하기 위해 WindowsControlLibrary1.dll를 `MFC03` 프로젝트 디렉터리로 복사 합니다.

1. `#include <afxwinforms.h>`기존 문의 끝에 있는 *.Pch* (Visual Studio 2017 및 이전 버전의 *stdafx.h* )에를 추가 `#include` 합니다.

1. 서브 클래스를 추가 하는 새 클래스를 추가 `CDialog` 합니다.

   프로젝트 이름을 마우스 오른쪽 단추로 클릭 하 고 서브 클래스에 대 한 MFC 클래스 (CHostForWinForm 라고 함)를 추가 `CDialog` 합니다. 대화 상자 리소스가 필요 하지 않으므로 리소스 ID를 삭제할 수 있습니다 ( **리소스 뷰** 을 선택 하 고, **대화** 상자 폴더를 확장 하 고 리소스를 삭제 `IDD_HOSTFORWINFORM` 합니다.  그런 다음 코드에서 ID에 대 한 모든 참조를 제거 합니다.)

1. `CDialog`CHostForWinForm 및 CHostForWinForm 파일에서를로 바꿉니다. `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`

1. CHostForWinForm 클래스에서 DoModal를 호출 합니다.

   MFC03에서을 추가 `#include "HostForWinForm.h"` 합니다.

   CMFC03App:: InitInstance 정의에서 return 문 앞에 다음을 추가 합니다.

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. 프로젝트를 빌드하고 실행합니다.

   **빌드** 메뉴에서 **솔루션 빌드** 를 클릭합니다.

   **디버그** 메뉴에서 **디버깅 하지 않고 시작** 을 클릭 합니다.

   다음에는 MFC 응용 프로그램에서 Windows Forms 컨트롤의 상태를 모니터링 하는 코드를 추가 합니다.

1. OnInitDialog에 대 한 처리기를 추가 합니다.

   **속성** 창 (F4)을 표시 합니다. **클래스 뷰** 에서 CHostForWinForm을 선택 합니다. **속성** 창에서 재정의를 선택 하 고 OnInitDialog에 대 한 행에서 왼쪽 열을 클릭 한 다음를 선택 \< Add > 합니다. 이렇게 하면 CHostForWinForm에 다음 줄이 추가 됩니다.

    ```cpp
    virtual BOOL OnInitDialog();
    ```

1. 다음과 같이 OnInitDialog (CHostForWinForm)를 정의 합니다.

    ```cpp
    BOOL CHostForWinForm::OnInitDialog() {
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);
       return TRUE;
    }
    ```

1. 그런 다음 OnButton1 처리기를 추가 합니다. CHostForWinForm에서 CHostForWinForm 클래스의 public 섹션에 다음 줄을 추가 합니다.

    ```cpp
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );

    BEGIN_DELEGATE_MAP( CHostForWinForm )
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );
    END_DELEGATE_MAP()
    ```

   CHostForWinForm에서 다음 정의를 추가 합니다.

    ```cpp
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )
    {
       System::Windows::Forms::MessageBox::Show("test");
    }
    ```

1. 프로젝트를 빌드하고 실행합니다. Windows Form에 있는 단추를 클릭 하면 MFC 응용 프로그램의 코드가 실행 됩니다.

    다음으로는 MFC 코드에서 Windows Form의 텍스트 상자에 있는 값을 표시 하는 코드를 추가 합니다.

1. CHostForWinForm에 있는 CHostForWinForm 클래스의 public 섹션에 다음 선언을 추가 합니다.

    ```cpp
    CString m_sEditBoxOnWinForm;
    ```

1. CHostForWinForm의 DoDataExchange 정의에서 함수 끝에 다음 세 줄을 추가 합니다.

    ```cpp
    if (pDX->m_bSaveAndValidate)
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);
    else
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);
    ```

1. CHostForWinForm의 OnButton1 정의에서 함수 끝에 다음 세 줄을 추가 합니다.

    ```cpp
    this->UpdateData(TRUE);
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);
    System::Windows::Forms::MessageBox::Show(z);
    ```

1. 프로젝트를 빌드하고 실행합니다.

## <a name="see-also"></a>참고 항목

<xref:System.Windows.Forms.UserControl?displayProperty=fullName>
[MFC에서 Windows Form 사용자 정의 컨트롤 사용](../dotnet/using-a-windows-form-user-control-in-mfc.md)
