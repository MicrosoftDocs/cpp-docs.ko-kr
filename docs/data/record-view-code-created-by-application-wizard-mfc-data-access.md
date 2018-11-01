---
title: 응용 프로그램 마법사가 만든 레코드 뷰 코드  (MFC Data Access)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: 5340926789925d8243ecd20c27537c9690582a41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50427978"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>응용 프로그램 마법사가 만든 레코드 뷰 코드  (MFC Data Access)

[MFC 응용 프로그램 마법사](../mfc/reference/database-support-mfc-application-wizard.md) 뷰의 재정의 `OnInitialUpdate` 고 `OnGetRecordset` 멤버 함수입니다. 프레임워크는 프레임 창, 문서 및 뷰를 만든 후 `OnInitialUpdate`를 호출하여 뷰를 초기화합니다. `OnInitialUpdate`는 문서에서 레코드 집합에 대한 포인터를 가져옵니다. 기본 클래스에 대 한 호출 [cview:: Oninitialupdate](../mfc/reference/cview-class.md#oninitialupdate) 함수 레코드 집합을 엽니다. 다음 코드에서는이 프로세스는 `CRecordView`:

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

레코드 집합이 열리면 레코드를 선택합니다. [Crecordset:: Open](../mfc/reference/crecordset-class.md#open) 현재 레코드와 DDX 이동 데이터를 레코드 집합의 필드 데이터 멤버에서 해당 폼 컨트롤 뷰에서 첫 번째 레코드를 만듭니다. RFX에 대 한 자세한 내용은 참조 하세요. [Exchange RFX (레코드 필드)](../data/odbc/record-field-exchange-rfx.md)합니다. DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../mfc/dialog-data-exchange-and-validation.md)를 참조하세요. 문서/뷰 만들기 프로세스에 대 한 자세한 내용은 [클래스를 사용 하 여 Windows에 대 한 응용 프로그램 작성을](../mfc/using-the-classes-to-write-applications-for-windows.md)입니다.

> [!NOTE]
>  최종 사용자가 레코드 집합에서의 레코드 뷰 컨트롤을 새로 고치는 기능을 제공해야 합니다. 이 기능을 제공하지 않는 경우 사용자가 컨트롤 값을 잘못된 값으로 변경하면 현재 레코드에서 영구적으로 작업이 중지될 수 있습니다. 호출 컨트롤을 새로 고치려면 합니다 `CWnd` 멤버 함수 [UpdateData](../mfc/reference/cwnd-class.md#updatedata) FALSE 매개 변수를 사용 하 여 합니다.

## <a name="see-also"></a>참고 항목

[레코드 뷰 사용](../data/using-a-record-view-mfc-data-access.md)