---
title: 확장된 콤보 상자 컨트롤 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: 87e2e1cd3c29ba838a17c24ece4a89adda21db0c
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907730"
---
# <a name="creating-an-extended-combo-box-control"></a>확장된 콤보 상자 컨트롤 만들기

확장 된 콤보 상자 컨트롤을 만드는 방법은 대화 상자에서 컨트롤을 사용 하는지 아니면 비 모달 창에서 만들었는지에 따라 달라 집니다.

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>대화 상자에서 직접 CComboBoxEx를 사용 하려면

1. 대화 상자 편집기에서 확장 된 콤보 상자 컨트롤을 대화 상자 템플릿 리소스에 추가 합니다. 해당 컨트롤 ID를 지정합니다.

1. 확장 된 콤보 상자 컨트롤의 속성 대화 상자를 사용 하 여 필요한 스타일을 지정 합니다.

1. [멤버 변수 추가 마법사](../ide/adding-a-member-variable-visual-cpp.md) 를 사용 하 여 [CComboBoxEx](../mfc/reference/ccomboboxex-class.md) 형식의 멤버 변수를 컨트롤 속성으로 추가할 수 있습니다. 이 멤버를 사용하여 `CComboBoxEx` 멤버 함수를 호출할 수 있습니다.

1. [클래스 마법사](reference/mfc-class-wizard.md) 를 사용 하 여 처리 해야 하는 확장 된 콤보 상자 컨트롤 알림 메시지에 대 한 대화 상자 클래스의 처리기 함수를 매핑할 수 있습니다 ( [메시지를 함수에 매핑](../mfc/reference/mapping-messages-to-functions.md)참조).

1. [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)에서 `CComboBoxEx` 개체에 대 한 추가 스타일을 설정 합니다.

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>비 모달 창에서 CComboBoxEx를 사용 하려면

1. 뷰 또는 창 클래스에서 컨트롤을 정의합니다.

1. 부모 창의 [OnCreate](../mfc/reference/cwnd-class.md#oncreate) handler 함수 초기에 가능 하면 [oninitialupdate](../mfc/reference/cview-class.md#oninitialupdate)에서 컨트롤의 [Create](../mfc/reference/ctabctrl-class.md#create) 멤버 함수를 호출 합니다. 컨트롤의 스타일을 설정합니다.

## <a name="see-also"></a>참고자료

[CComboBoxEx 사용](../mfc/using-ccomboboxex.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
