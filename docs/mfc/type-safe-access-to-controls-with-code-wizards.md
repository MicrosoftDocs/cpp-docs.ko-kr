---
title: 코드 마법사를 사용하여 컨트롤에 대한 형식이 안전한 액세스 수행
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: ee7c49f75dcdc2b6c32f2b391ace7260b46d197b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507897"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>코드 마법사를 사용하여 컨트롤에 대한 형식이 안전한 액세스 수행

DDX 기능에 대해 잘 알고 있는 경우 [멤버 변수 추가 마법사](../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard) 에서 컨트롤 속성을 사용 하 여 형식이 안전한 액세스를 만들 수 있습니다. 이 방법은 코드 마법사 없이 컨트롤을 만드는 것 보다 쉽습니다.

컨트롤의 값에 액세스 하려는 경우 DDX는이를 제공 합니다. 컨트롤의 값에 액세스 하는 것 보다 더 많은 작업을 수행 하려는 경우 멤버 변수 추가 마법사를 사용 하 여 해당 클래스의 멤버 변수를 대화 상자 클래스에 추가 합니다. 이 멤버 변수를 컨트롤 속성에 연결 합니다.

멤버 변수는 Value 속성 대신 컨트롤 속성을 가질 수 있습니다. Value 속성은 컨트롤에서 반환 된 데이터 형식 (예: 또는)을 참조 `CString` 합니다 **`int`** . 컨트롤 속성을 사용 하면 또는와 같은 MFC의 컨트롤 클래스 중 하나인 데이터 멤버를 통해 컨트롤에 직접 액세스할 수 있습니다 `CButton` `CEdit` .

> [!NOTE]
> 지정 된 컨트롤의 경우 Value 속성을 사용 하는 여러 멤버 변수와 컨트롤 속성을 가진 멤버 변수가 최대 하나만 있을 수 있습니다. 컨트롤에 연결 된 여러 개체 또는 다른 창에는 메시지 맵의 모호성이 발생 하므로 하나의 MFC 개체만 컨트롤에 매핑할 수 있습니다.

이 개체를 사용 하 여 컨트롤 개체에 대 한 멤버 함수를 호출할 수 있습니다. 이러한 호출은 대화 상자의 컨트롤에 영향을 줍니다. 예를 들어 형식 *m_Checkbox*변수로 표시 된 확인란 컨트롤의 경우 `CButton` 다음을 호출할 수 있습니다.

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

여기서 멤버 변수 *m_Checkbox* 는 `GetMyCheckbox` [코드 마법사 없이 컨트롤에 대 한 형식이 안전한 액세스](../mfc/type-safe-access-to-controls-without-code-wizards.md)에 표시 된 멤버 함수와 동일한 용도를 제공 합니다. 확인란이 자동 확인란이 아니면 단추를 클릭할 때 BN_CLICKED 컨트롤 알림 메시지에 대 한 대화 상자 클래스에 처리기가 계속 필요 합니다.

컨트롤에 대 한 자세한 내용은 [컨트롤](../mfc/controls-mfc.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[대화 상자의 컨트롤에 대 한 형식이 안전한 액세스](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[MFC에서 대화 상자를 통해 작업](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[코드 마법사를 사용 하지 않고 컨트롤에 대 한 형식이 안전한 액세스](../mfc/type-safe-access-to-controls-without-code-wizards.md)
