---
description: '자세히 알아보기: 방법: Windows Forms 컨트롤의 속성 및 메서드 호출'
title: '방법: Windows Forms 컨트롤의 속성 및 메서드 호출'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- method calls, Windows Forms
- calling methods, Windows Forms control
- calling properties, Windows Forms control
- Windows Forms controls [C++], methods
- calling properties
- Windows Forms controls [C++], properties
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
ms.openlocfilehash: a797084a28eefec27699814a09c8521da7460bc7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268407"
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>방법: Windows Forms 컨트롤의 속성 및 메서드 호출

[CWinFormsView:: GetControl](../mfc/reference/cwinformsview-class.md#getcontrol) 은에 대 한 포인터가 아니라에 대 한 포인터를 반환 하기 때문에 <xref:System.Windows.Forms.Control?displayProperty=fullName> `WindowsControlLibrary1::UserControl1` 사용자 정의 컨트롤 형식의 멤버를 추가 하 고 [IView:: oninitialupdate](../mfc/reference/iview-interface.md#oninitialupdate)에서 초기화 하는 것이 좋습니다. 이제를 사용 하 여 메서드 및 속성을 호출할 수 있습니다 `m_ViewControl` .

이 항목에서는 이전 [에 방법: 대화 상자에서 사용자 정의 컨트롤 및 호스트 만들기](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) 및 [방법: 사용자 정의 컨트롤 및 호스트 MDI 뷰 만들기](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)를 완료 했다고 가정 합니다.

### <a name="to-create-the-mfc-host-application"></a>MFC 호스트 응용 프로그램을 만들려면

1. [방법: 사용자 정의 컨트롤 및 호스트 MDI 뷰 만들기](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)에서 만든 MFC 응용 프로그램을 엽니다.

1. `CMFC02View`MFC02View에 있는 클래스 선언의 공용 재정의 섹션에 다음 줄을 추가 합니다.

   `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`

1. OnInitialupdate에 대 한 재정의를 추가 합니다.

   **속성** 창 (F4)을 표시 합니다. **클래스 뷰** (CTRL + SHIFT + C)에서 CMFC02View 클래스를 선택 합니다. **속성** 창에서 재정의에 대 한 아이콘을 선택 합니다. 목록에서 OnInitialUpdate로 Scoll 합니다. 드롭다운 목록을 클릭 하 고를 선택 \<Add> 합니다. MFC02View. OnInitialUpdate 함수의 본문이 다음과 같은지 확인 합니다.

    ```
    CWinFormsView::OnInitialUpdate();
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());
    m_ViewControl->textBox1->Text = gcnew System::String("hi");
    ```

1. 프로젝트를 빌드하고 실행합니다.

   **빌드** 메뉴에서 **솔루션 빌드** 를 클릭합니다.

   **디버그** 메뉴에서 **디버깅 하지 않고 시작** 을 클릭 합니다.

   이제 텍스트 상자가 초기화 되었습니다.

## <a name="see-also"></a>참고 항목

[Windows Forms 사용자 정의 컨트롤을 MFC 뷰로 호스팅](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
