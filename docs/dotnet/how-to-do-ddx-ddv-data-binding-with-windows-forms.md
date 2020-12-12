---
description: '자세한 정보: 방법: Windows Forms를 사용 하 여 DDX/DDV 데이터 바인딩 수행'
title: '방법: Windows Forms에서 DDX-DDV 데이터 바인딩 수행'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: 55dfdaac595b6de0369d7db555c40b8cd38d6c01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175653"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>방법: Windows Forms에서 DDX/DDV 데이터 바인딩 수행

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) [CWinFormsControl:: CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) 를 호출 하 여 리소스 컨트롤 ID와 일치 하는 컨트롤을 만듭니다. 를 사용 하 여 `DDX_ManagedControl` `CWinFormsControl` (마법사에서 생성 한 코드에서) 컨트롤에 대해를 사용 하는 경우 `CreateManagedControl` 동일한 컨트롤에 대해를 명시적으로 호출 하면 안 됩니다.

`DDX_ManagedControl` [CWnd::D odataexchange](../mfc/reference/cwnd-class.md#dodataexchange) 를 호출 하 여 리소스 id에서 컨트롤을 만듭니다. 데이터 교환의 경우 Windows Forms 컨트롤에서 DDX/DDV 함수를 사용할 필요가 없습니다. 대신 `DoDataExchange` 다음 예제와 같이 대화 상자 또는 뷰 클래스의 메서드에서 관리 되는 컨트롤의 속성에 액세스 하는 코드를 추가할 수 있습니다.

다음 예제에서는 네이티브 c + + 문자열을 .NET 사용자 정의 컨트롤에 바인딩하는 방법을 보여 줍니다.

## <a name="example-ddxddv-data-binding"></a>예: DDX/DDV 데이터 바인딩

다음은 `m_str` `NameText` .net 사용자 컨트롤의 사용자 정의 속성을 사용 하 여 MFC 문자열의 DDX/DDV 데이터 바인딩 예제입니다.

이 컨트롤은 [CDialog:: OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) 가 처음으로를 호출할 때 만들어지므로를 `CMyDlg::DoDataExchange` 참조 하는 모든 코드가 `m_UserControl` 호출 후에와 야 합니다 `DDX_ManagedControl` .

[방법: 사용자 정의 컨트롤 및 호스트 만들기 대화 상자](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)에서 만든 MFC01 응용 프로그램에서이 코드를 구현할 수 있습니다.

CMFC01Dlg의 선언에 다음 코드를 입력 합니다.

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example-implement-dodataexchange"></a>예: DoDataExchange () 구현

CMFC01Dlg 구현에 다음 코드를 입력 합니다.

```cpp
void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)
{
   CDialog::DoDataExchange(pDX);
   DDX_ManagedControl(pDX, IDC_CTRL1, m_MyControl);

   if (pDX->m_bSaveAndValidate) {
      m_str = m_MyControl->textBox1->Text;
   } else
   {
      m_MyControl->textBox1->Text = gcnew System::String(m_str);
   }
}
```

## <a name="example-add-handler-method"></a>예: Add handler 메서드

이제 확인 단추를 클릭 하 여 처리기 메서드를 추가 합니다. **리소스 뷰** 탭을 클릭 합니다. 리소스 뷰에서을 두 번 클릭 `IDD_MFC01_DIALOG` 합니다. 대화 상자 리소스가 리소스 편집기에 표시 됩니다. 그런 다음 확인 단추를 두 번 클릭 합니다.

다음과 같이 처리기를 정의 합니다.

```cpp
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example-set-the-textbox-text"></a>예: 텍스트 상자 텍스트 설정

BOOL CMFC01Dlg:: OnInitDialog ()의 구현에 다음 줄을 추가 합니다.

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

이제 애플리케이션을 빌드 및 실행할 수 있습니다. 응용 프로그램을 닫을 때 텍스트 상자의 텍스트가 팝업 메시지 상자에 표시 됩니다.

## <a name="see-also"></a>참고 항목

[CWinFormsControl 클래스](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
