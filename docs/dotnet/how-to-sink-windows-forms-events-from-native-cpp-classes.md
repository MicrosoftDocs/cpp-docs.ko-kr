---
description: '자세한 정보: 방법: 네이티브 c + + 클래스에서 Windows Forms 이벤트 싱크'
title: '방법: 네이티브 C++ 클래스에서 Windows Forms 이벤트 싱크'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, managed/native interop
- event handling, sinking .NET in C++
- event handling, .NET/native interop
- event handling, Windows Forms in C++
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
ms.openlocfilehash: 223590849f114bfe02b030a0639f160b8fc1c321
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286360"
---
# <a name="how-to-sink-windows-forms-events-from-native-c-classes"></a>방법: 네이티브 C++ 클래스에서 Windows Forms 이벤트 싱크

네이티브 c + + 클래스가 MFC 매크로 맵 형식을 사용 하 여 Windows Forms 컨트롤 또는 다른 폼에서 발생 한 관리 되는 이벤트에서 콜백을 받도록 할 수 있습니다. 뷰와 대화 상자에서 이벤트 싱크는 컨트롤에 대해 동일한 작업을 수행 하는 것과 비슷합니다.

이렇게 하려면 다음을 수행해야 합니다.

- `OnClick` [MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)를 사용 하 여 컨트롤에 이벤트 처리기를 연결 합니다.

- [BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map), [END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)및 [EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)를 사용 하 여 대리자 맵을 만듭니다.

이 샘플은 [방법: Windows Forms를 사용 하 여 DDX/DDV 데이터 바인딩 수행](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)에서 수행한 작업을 계속 합니다.

이제 MFC 컨트롤 ( `m_MyControl` )을 `OnClick` 관리 되는 이벤트에 대해 라는 관리 되는 이벤트 처리기 대리자와 연결 <xref:System.Windows.Forms.Control.Click> 합니다.

### <a name="to-attach-the-onclick-event-handler"></a>OnClick 이벤트 처리기를 연결 하려면:

1. BOOL CMFC01Dlg:: OnInitDialog의 구현에 다음 코드를 추가 합니다.

    ```
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );
    ```

1. CMFC01Dlg: public CDialog 클래스의 선언에서 public 섹션에 다음 코드를 추가 합니다.

    ```
    // delegate map
    BEGIN_DELEGATE_MAP( CMFC01Dlg )
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )
    END_DELEGATE_MAP()

    void OnClick( System::Object^ sender, System::EventArgs^ e );
    ```

1. 마지막으로 CMFC01Dlg에 대 한 구현을 추가 `OnClick` 합니다.

    ```
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)
    {
        AfxMessageBox(_T("Button clicked"));
    }
    ```

## <a name="see-also"></a>참고 항목

[MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)<br/>
[BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)<br/>
[END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)<br/>
[EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)
