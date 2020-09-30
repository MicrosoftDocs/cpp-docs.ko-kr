---
title: 애플리케이션에서 속성 시트 사용
ms.date: 11/04/2016
helpviewer_keywords:
- dialog templates [MFC], property sheets
- dialog resources
- property pages [MFC], property sheets
- DoModal method property sheets
- AddPage method [MFC]
- property sheets, about property sheets
- Create method [MFC], property sheets
- CPropertyPage class [MFC], styles
ms.assetid: 240654d4-152b-4e3f-af7b-44234339206e
ms.openlocfilehash: 789764c9af988135219bd710d4f8aec1cda9143a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504649"
---
# <a name="using-property-sheets-in-your-application"></a>애플리케이션에서 속성 시트 사용

응용 프로그램에서 속성 시트를 사용 하려면 다음 단계를 완료 합니다.

1. 각 속성 페이지에 대 한 대화 상자 템플릿 리소스를 만듭니다. 사용자가 한 페이지에서 다른 페이지로 전환할 수 있으므로 각 페이지의 레이아웃을 가능한 한 일관 되 게 유지 해야 합니다.

   모든 페이지에 대 한 대화 상자 템플릿은 크기가 같을 필요가 없습니다. 프레임 워크는 가장 큰 페이지의 크기를 사용 하 여 속성 페이지의 속성 시트에서 할당할 공간의 크기를 결정 합니다.

   속성 페이지에 대 한 대화 상자 템플릿 리소스를 만들 때 대화 상자 속성 속성 시트에서 다음 스타일을 지정 해야 합니다.

   - **일반** 페이지의 **캡션** 편집 상자를이 페이지의 탭에 표시할 텍스트로 설정 합니다.

   - **스타일 페이지의** **스타일** 목록 상자를 **자식**으로 설정 합니다.

   - **스타일** 페이지에서 **테두리** 목록 상자를 **가늘게**로 설정 합니다.

   - **스타일** 페이지에서 **Titlebar** 확인란을 선택 했는지 확인 합니다.

   - **추가 스타일** 페이지에서 **사용 안 함** 확인란이 선택 되어 있는지 확인 합니다.

1. 각 속성 페이지 대화 상자 템플릿에 해당 하는 [CPropertyPage](../mfc/reference/cpropertypage-class.md)파생 클래스를 만듭니다. [클래스 추가를](../ide/adding-a-class-visual-cpp.md)참조 하세요. 를 `CPropertyPage` 기본 클래스로 선택 합니다.

1. 이 속성 페이지에 대 한 값을 보유할 멤버 변수를 만듭니다. 속성 페이지가 특수 한 대화 상자 이기 때문에 속성 페이지에 멤버 변수를 추가 하는 프로세스는 대화 상자에 멤버 변수를 추가 하는 것과 동일 합니다. 자세한 내용은 [대화 상자 컨트롤의 멤버 변수 정의](../windows/adding-editing-or-deleting-controls.md)를 참조 하세요.

1. 소스 코드에서 [CPropertySheet](../mfc/reference/cpropertysheet-class.md) 개체를 생성 합니다. 일반적으로 `CPropertySheet` 속성 시트를 표시 하는 명령에 대 한 처리기에서 개체를 생성 합니다. 이 개체는 전체 속성 시트를 나타냅니다. [DoModal](../mfc/reference/cpropertysheet-class.md#domodal) 함수를 사용 하 여 모달 속성 시트를 만드는 경우 프레임 워크는 기본적으로 확인, 취소 및 적용의 세 가지 명령 단추를 제공 합니다. 프레임 워크는 [Create](../mfc/reference/cpropertysheet-class.md#create) 함수를 사용 하 여 만든 모덜리스 속성 시트에 대 한 명령 단추를 만듭니다. `CPropertySheet`다른 컨트롤 (예: 미리 보기 창)을 추가 하거나 모덜리스 속성 시트를 표시 하지 않으려는 경우에는에서 클래스를 파생 시킬 필요가 없습니다. 이 단계는 속성 시트를 닫는 데 사용할 수 있는 기본 컨트롤을 포함 하지 않기 때문에 모덜리스 속성 시트에 필요 합니다.

1. 속성 시트에 추가할 각 페이지에 대해 다음을 수행 합니다.

   - `CPropertyPage`이 프로세스의 앞부분에서 만든 각 파생 클래스에 대해 하나의 개체를 생성 합니다.

   - 각 페이지에 대해 [CPropertySheet:: AddPage](../mfc/reference/cpropertysheet-class.md#addpage) 를 호출 합니다.

   일반적으로를 만드는 개체 `CPropertySheet` 도 `CPropertyPage` 이 단계에서 개체를 만듭니다. 그러나 파생 클래스를 구현 하는 경우 `CPropertySheet` 개체에 개체를 포함 `CPropertyPage` `CPropertySheet` 하 고 `AddPage` 파생 클래스 생성자에서 각 페이지에 대해를 호출할 수 있습니다 `CPropertySheet` . `AddPage` 개체를 `CPropertyPage` 속성 시트의 페이지 목록에 추가 하지만 실제로 해당 페이지에 대 한 창을 만들지는 않습니다. 따라서 호출할 속성 시트 창을 만들 때까지 기다릴 필요가 없습니다. `AddPage` `AddPage` 속성 시트의 생성자에서를 호출할 수 있습니다.

   기본적으로 속성 시트의 탭 수가 속성 시트의 단일 행에 맞는 것 보다 많은 경우 탭은 여러 행에 쌓입니다. 스태킹를 사용 하지 않으려면 매개 변수를 **FALSE**로 설정 하 여 [CPropertySheet:: EnableStackedTabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs) 를 호출 합니다. `EnableStackedTabs`속성 시트를 만들 때를 호출 해야 합니다.

1. [CPropertySheet::D oModal](../mfc/reference/cpropertysheet-class.md#domodal) 또는 [Create](../mfc/reference/cpropertysheet-class.md#create) 를 호출 하 여 속성 시트를 표시 합니다. `DoModal`을 호출 하 여 속성 시트를 모달 대화 상자로 만듭니다. **Create** 를 호출 하 여 속성 시트를 모덜리스 대화 상자로 만듭니다.

1. 속성 페이지와 속성 시트 소유자 간에 데이터를 교환 합니다. 이에 대해서는 [데이터 교환](../mfc/exchanging-data.md)문서에 설명 되어 있습니다.

속성 시트를 사용 하는 방법에 대 한 예제는 MFC 일반 샘플 [PROPDLG](../overview/visual-cpp-samples.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[속성 시트](../mfc/property-sheets-mfc.md)
