---
description: '자세히 알아보기: TN062: Windows 컨트롤에 대 한 메시지 리플렉션'
title: 'TN062: Windows 컨트롤에 대한 메시지 리플렉션'
ms.date: 06/28/2018
f1_keywords:
- vc.controls.messages
helpviewer_keywords:
- ON_WM_VKEYTOITEM_REFLECT macro [MFC]
- ON_WM_DRAWITEM_REFLECT macro [MFC]
- ON_WM_VSCROLL_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT message [MFC]
- ON_CONTROL_REFLECT_EX macro [MFC]
- ON_UPDATE_COMMAND_UI_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT_EX message [MFC]
- ON_WM_HSCROLL_REFLECT macro [MFC]
- message reflection [MFC]
- ON_WM_COMPAREITEM_REFLECT macro [MFC]
- ON_WM_MEASUREITEM_REFLECT macro [MFC]
- ON_NOTIFY message [MFC]
- WM_COMMAND [MFC]
- WM_CTLCOLOR message [MFC]
- TN062 [MFC]
- ON_WM_CHARTOITEM_REFLECT macro [MFC]
- ON_WM_CTLCOLOR_REFLECT macro [MFC]
- ON_WM_DELETEITEM_REFLECT macro [MFC]
- notification messages [MFC]
- ON_WM_PARENTNOTIFY_REFLECT macro [MFC]
- WM_NOTIFY message [MFC]
- ON_CONTROL_REFLECT macro
ms.assetid: 53efb0ba-fcda-4fa0-a3c7-14e0b78fb494
ms.openlocfilehash: 9dc106c1513032e654acfc2c4b86b8eb3b939578
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214730"
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062: Windows 컨트롤에 대한 메시지 리플렉션

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 기술 정보는 MFC 4.0의 새로운 기능인 메시지 리플렉션에 대해 설명 합니다. 메시지 리플렉션을 사용 하는 다시 사용할 수 있는 간단한 컨트롤을 만들기 위한 지침을 포함 합니다.

이 기술 정보는 ActiveX 컨트롤 (이전의 OLE 컨트롤)에 적용 되는 메시지 리플렉션에 대해 설명 하지 않습니다. [ActiveX 컨트롤: Windows 컨트롤 서브클래싱](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)문서를 참조 하세요.

**메시지 리플렉션 이란?**

Windows 컨트롤은 종종 부모 창에 알림 메시지를 보냅니다. 예를 들어 대부분의 컨트롤은 컨트롤 색 알림 메시지 (WM_CTLCOLOR 또는 해당 변형 중 하나)를 부모로 보내 부모가 컨트롤의 배경을 그리기 위한 브러시를 제공할 수 있도록 합니다.

Windows 및 MFC 버전 4.0 이전에서 부모 창 (일반적으로 대화 상자)은 이러한 메시지를 처리 하는 일을 담당 합니다. 즉, 메시지를 처리 하는 코드는 부모 창의 클래스에 있어야 하 고 해당 메시지를 처리 해야 하는 모든 클래스에서 중복 되어야 합니다. 위의 경우 사용자 지정 배경의 컨트롤을 원하는 모든 대화 상자에서 컨트롤 색 알림 메시지를 처리 해야 합니다. 자체 배경색을 처리 하는 컨트롤 클래스를 작성할 수 있는 경우 코드를 다시 사용 하는 것이 훨씬 쉽습니다.

MFC 4.0에서 이전 메커니즘은 계속 작동 합니다. 즉, 부모 창에서 알림 메시지를 처리할 수 있습니다. 그러나 MFC 4.0는 자식 컨트롤 창이 나 부모 창에서 또는 둘 다에서 이러한 알림 메시지를 처리할 수 있도록 하는 "메시지 리플렉션" 이라는 기능을 제공 하 여 다시 사용을 용이 하 게 합니다. 컨트롤 배경 색 예제에서 이제 부모에 의존 하지 않고 리플렉션된 WM_CTLCOLOR 메시지를 처리 하 여 자체 배경색을 설정 하는 컨트롤 클래스를 작성할 수 있습니다. 메시지 리플렉션은 Windows가 아니라 MFC에서 구현 하므로 메시지 리플렉션이 작동 하려면에서 부모 창 클래스를 파생 해야 `CWnd` 합니다.

이전 버전의 MFC는 소유자가 그린 목록 상자에 대 한 메시지 (WM_DRAWITEM 등)와 같은 몇 가지 메시지에 대 한 가상 함수를 제공 하 여 메시지 리플렉션과 유사 하 게 수행 되었습니다. 새 메시지 리플렉션 메커니즘은 일반화 되 고 일관 됩니다.

메시지 리플렉션은 4.0 이전 버전의 MFC 용으로 작성 된 코드와 이전 버전과 호환 됩니다.

특정 메시지에 대 한 처리기를 제공 했거나 메시지 범위에 대 한 처리기를 부모 창의 클래스에서 제공 하는 경우 고유한 처리기에서 기본 클래스 처리기 함수를 호출 하지 않는 경우 동일한 메시지에 대해 리플렉션된 메시지 처리기를 재정의 합니다. 예를 들어 대화 상자 클래스에서 WM_CTLCOLOR를 처리 하는 경우 처리 시 반영 된 메시지 처리기가 재정의 됩니다.

부모 창 클래스에서 특정 WM_NOTIFY 메시지 또는 WM_NOTIFY 된 메시지 범위에 대 한 처리기를 제공 하는 경우 해당 메시지를 보내는 자식 컨트롤에 리플렉션된 메시지 처리기가 없는 경우에만 처리기가 호출 됩니다 `ON_NOTIFY_REFLECT()` . 메시지 맵에를 사용 하는 경우 메시지 `ON_NOTIFY_REFLECT_EX()` 처리기에서 부모 창이 메시지를 처리 하도록 허용 하거나 허용 하지 않을 수 있습니다. 처리기가 **FALSE** 를 반환 하는 경우에도 메시지는 부모에 의해 처리 되지만 **TRUE** 를 반환 하는 호출은 부모에서이를 처리할 수 없습니다. 반영 된 메시지는 알림 메시지 보다 먼저 처리 됩니다.

WM_NOTIFY 메시지가 전송 되 면 컨트롤은이를 처리할 수 있는 첫 번째 기회를 제공 합니다. 다른 리플렉션된 메시지가 전송 되 면 부모 창에는이를 처리할 수 있는 첫 번째 메시지가 표시 되 고 컨트롤은 리플 렉 트 된 메시지를 받습니다. 이렇게 하려면 처리기 함수 및 컨트롤의 클래스 메시지 맵에 적절 한 항목이 필요 합니다.

반영 된 메시지에 대 한 메시지 매핑 매크로는 일반적인 알림과는 약간 다릅니다. 일반적인 이름에 *_REFLECT* 추가 됩니다. 예를 들어 부모의 WM_NOTIFY 메시지를 처리 하려면 부모의 메시지 맵에 매크로 ON_NOTIFY를 사용 합니다. 자식 컨트롤에서 리플렉션된 메시지를 처리 하려면 자식 컨트롤의 메시지 맵에서 ON_NOTIFY_REFLECT 매크로를 사용 합니다. 경우에 따라 매개 변수도 다릅니다. 클래스 마법사는 일반적으로 메시지 맵 항목을 추가 하 고 올바른 매개 변수를 사용 하 여 기본 함수 구현을 제공할 수 있습니다.

새 WM_NOTIFY 메시지에 대 한 자세한 내용은 [TN061: ON_NOTIFY 및 WM_NOTIFY 메시지](../mfc/tn061-on-notify-and-wm-notify-messages.md) 를 참조 하세요.

**반영 되는 메시지에 대 한 메시지 맵 항목 및 처리기 함수 프로토타입**

반영 된 컨트롤 알림 메시지를 처리 하려면 아래 표에 나열 된 메시지 맵 매크로 및 함수 프로토타입을 사용 합니다.

클래스 마법사는 일반적으로 이러한 메시지 맵 항목을 추가 하 고 기본 함수 구현을 제공 합니다. 반영 된 메시지에 대 한 처리기를 정의 하는 방법에 대 한 자세한 내용은 [리플렉션된 메시지의 메시지 처리기 정의](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md) 를 참조 하세요.

메시지 이름에서 리플렉션된 매크로 이름으로 변환 하려면 *ON_* 앞에 추가 *_REFLECT* 를 추가 합니다. 예를 들어 WM_CTLCOLOR ON_WM_CTLCOLOR_REFLECT 됩니다. 영향을 받을 수 있는 메시지를 확인 하려면 아래 표의 매크로 항목을 반대로 변환 합니다.

위의 규칙에 대 한 세 가지 예외는 다음과 같습니다.

- WM_COMMAND 알림에 대 한 매크로를 ON_CONTROL_REFLECT 합니다.

- WM_NOTIFY 리플렉션 용 매크로가 ON_NOTIFY_REFLECT 되었습니다.

- ON_UPDATE_COMMAND_UI 리플렉션 용 매크로가 ON_UPDATE_COMMAND_UI_REFLECT 되었습니다.

위의 각 특수 한 경우에는 처리기 멤버 함수의 이름을 지정 해야 합니다. 다른 경우에는 처리기 함수에 표준 이름을 사용 해야 합니다.

함수의 매개 변수 및 반환 값에 대 한 의미는 앞 *에 있는의* 함수 이름 또는 함수 이름에 설명 되어 있습니다. 예를 들어 `CtlColor` 은에 설명 되어 `OnCtlColor` 있습니다. 반영 된 여러 메시지 처리기에는 부모 창에서 유사한 처리기 보다 작은 매개 변수가 필요 합니다. 아래 표의 이름을 설명서에 있는 정식 매개 변수의 이름과 일치 시킵니다.

|맵 항목|함수 프로토타입|
|---------------|------------------------|
|**ON_CONTROL_REFLECT (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **( );**|
|**ON_NOTIFY_REFLECT (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *result* **);**|
|**ON_UPDATE_COMMAND_UI_REFLECT (** `memberFxn` **)**|**afx_msg void** `memberFxn` **(CCmdUI** <strong>\*</strong> `pCmdUI` **);**|
|**ON_WM_CTLCOLOR_REFLECT ()**|CDC (afx_msg **HBRUSH CtlColor)** <strong>\*</strong> `pDC` **, UINT** `nCtlColor` **);**|
|**ON_WM_DRAWITEM_REFLECT ()**|**afx_msg Void DrawItem (LPDRAWITEMSTRUCT** `lpDrawItemStruct` **);**|
|**ON_WM_MEASUREITEM_REFLECT ()**|**afx_msg Void MeasureItem (LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **);**|
|**ON_WM_DELETEITEM_REFLECT ()**|**afx_msg Void DeleteItem (LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **);**|
|**ON_WM_COMPAREITEM_REFLECT ()**|**afx_msg Int CompareItem (LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **);**|
|**ON_WM_CHARTOITEM_REFLECT ()**|**afx_msg int chartoitem (uint** `nKey` **, uint** `nIndex` **);**|
|**ON_WM_VKEYTOITEM_REFLECT ()**|**afx_msg int vkeytoitem (uint** `nKey` **, uint** `nIndex` **);**|
|**ON_WM_HSCROLL_REFLECT ()**|**afx_msg void hscroll (uint** `nSBCode` **, uint** `nPos` **);**|
|**ON_WM_VSCROLL_REFLECT ()**|**afx_msg void vscroll (uint** `nSBCode` **, uint** `nPos` **);**|
|**ON_WM_PARENTNOTIFY_REFLECT ()**|**afx_msg void parentnotify (UINT** `message` **, LPARAM** `lParam` **);**|

ON_NOTIFY_REFLECT 및 ON_CONTROL_REFLECT 매크로에는 지정 된 메시지를 처리 하기 위해 두 개 이상의 개체 (예: 컨트롤 및 부모)를 사용할 수 있는 변형이 있습니다.

|맵 항목|함수 프로토타입|
|---------------|------------------------|
|**ON_NOTIFY_REFLECT_EX (** `wNotifyCode` **,** `memberFxn` **)**|**AFX_MSG BOOL** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *result* **);**|
|**ON_CONTROL_REFLECT_EX (** `wNotifyCode` **,** `memberFxn` **)**|**AFX_MSG BOOL** `memberFxn` **( );**|

## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>리플렉션된 메시지 처리: 다시 사용할 수 있는 컨트롤의 예

이 간단한 예제에서는 라는 다시 사용할 수 있는 컨트롤을 만듭니다 `CYellowEdit` . 컨트롤은 노란색 배경에 검정 텍스트를 표시 한다는 점을 제외 하 고는 일반 편집 컨트롤과 동일 하 게 작동 합니다. `CYellowEdit`컨트롤에서 다른 색을 표시할 수 있도록 하는 멤버 함수를 추가 하는 것이 쉽습니다.

### <a name="to-try-the-example-that-creates-a-reusable-control"></a>재사용 가능한 컨트롤을 만드는 예제를 사용 하려면

1. 기존 응용 프로그램에 새 대화 상자를 만듭니다. 자세한 내용은 [대화 상자 편집기](../windows/dialog-editor.md) 항목을 참조 하세요.

   재사용 가능한 컨트롤을 개발할 수 있는 응용 프로그램이 있어야 합니다. 사용할 기존 응용 프로그램이 없는 경우 응용 프로그램 마법사를 사용 하 여 대화 상자 기반 응용 프로그램을 만듭니다.

2. 프로젝트가 Visual C++로 로드 되 면 클래스 마법사를 사용 하 여를 기반으로 하는 라는 새 클래스를 만듭니다 `CYellowEdit` `CEdit` .

3. 세 개의 멤버 변수를 클래스에 추가 `CYellowEdit` 합니다. 처음 두 개는 텍스트 색과 배경색을 포함 하는 *Colorref* 변수가 됩니다. 세 번째는 `CBrush` 배경을 그리기 위한 브러시를 보유 하는 개체입니다. `CBrush`개체를 사용 하면 브러시를 한 번만 만든 다음,이를 참조 하면 컨트롤이 제거 될 때 자동으로 브러시를 소멸 시킬 수 있습니다 `CYellowEdit` .

4. 다음과 같이 생성자를 작성 하 여 멤버 변수를 초기화 합니다.

    ```cpp
    CYellowEdit::CYellowEdit()
    {
        m_clrText = RGB(0, 0, 0);
        m_clrBkgnd = RGB(255, 255, 0);
        m_brBkgnd.CreateSolidBrush(m_clrBkgnd);
    }
    ```

5. 클래스 마법사를 사용 하 여 리플렉션 WM_CTLCOLOR 메시지에 대 한 처리기를 클래스에 추가 `CYellowEdit` 합니다. 처리할 수 있는 메시지 목록에서 메시지 이름 앞에 있는 등호는 메시지가 반영 되었음을 나타냅니다. 이에 대해서는 [리플렉션된 메시지의 메시지 처리기 정의](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)에 설명 되어 있습니다.

   클래스 마법사는 다음과 같은 메시지 매핑 매크로 및 기본 함수를 추가 합니다.

    ```cpp
    ON_WM_CTLCOLOR_REFLECT()
    // Note: other code will be in between....

    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)
    {
        // TODO: Change any attributes of the DC here
        // TODO: Return a non-NULL brush if the
        //       parent's handler should not be called
        return NULL;
    }
    ```

6. 함수 본문을 다음 코드로 바꿉니다. 코드는 컨트롤의 나머지 부분에 대 한 텍스트 색, 텍스트 배경색 및 배경색을 지정 합니다.

    ```cpp
    pDC->SetTextColor(m_clrText);   // text
    pDC->SetBkColor(m_clrBkgnd);    // text bkgnd
    return m_brBkgnd;               // ctl bkgnd
    ```

7. 대화 상자에서 편집 컨트롤을 만든 다음 컨트롤 키를 누른 채 편집 컨트롤을 두 번 클릭 하 여 멤버 변수에 연결 합니다. 멤버 변수 추가 대화 상자에서 변수 이름을 입력 하 고 범주에 대해 "제어"를 선택한 다음 변수 형식으로 "CYellowEdit"를 선택 합니다. 대화 상자에서 탭 순서를 설정 하는 것을 잊지 마십시오. 또한 `CYellowEdit` 대화 상자의 헤더 파일에 컨트롤에 대 한 헤더 파일을 포함 해야 합니다.

8. 애플리케이션을 빌드하고 실행합니다. 편집 컨트롤에는 노란색 배경이 있습니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
