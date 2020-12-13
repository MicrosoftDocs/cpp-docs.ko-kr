---
description: '자세한 정보: 응용 프로그램 마법사에서 만든 레코드 뷰 코드 (MFC Data Access)'
title: 애플리케이션 마법사가 만든 레코드 뷰 코드  (MFC Data Access)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: b0fa7a4960096f11ab66194fa6e41be60b45d4c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332433"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>애플리케이션 마법사가 만든 레코드 뷰 코드  (MFC Data Access)

[MFC 응용 프로그램 마법사](../mfc/reference/database-support-mfc-application-wizard.md) 는 뷰의 `OnInitialUpdate` 및 멤버 함수를 재정의 합니다 `OnGetRecordset` . 프레임워크는 프레임 창, 문서 및 뷰를 만든 후 `OnInitialUpdate`를 호출하여 뷰를 초기화합니다. `OnInitialUpdate`는 문서에서 레코드 집합에 대한 포인터를 가져옵니다. 기본 클래스 [CView:: OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) 함수를 호출 하면 레코드 집합이 열립니다. 다음 코드에서는에 대 한이 프로세스를 보여 줍니다 `CRecordView` .

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

레코드 집합이 열리면 레코드를 선택합니다. [CRecordset:: Open](../mfc/reference/crecordset-class.md#open) 은 첫 번째 레코드를 현재 레코드로 설정 하 고 DDX는 데이터를 레코드 집합의 필드 데이터 멤버에서 뷰의 해당 폼 컨트롤로 이동 합니다. RFX에 대 한 자세한 내용은 [rfx (레코드 필드 교환)](../data/odbc/record-field-exchange-rfx.md)를 참조 하세요. DDX에 대한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](../mfc/dialog-data-exchange-and-validation.md)를 참조하세요. 문서/뷰 만들기 프로세스에 대 한 자세한 내용은 [클래스를 사용 하 여 Windows 용 응용 프로그램 작성](../mfc/using-the-classes-to-write-applications-for-windows.md)을 참조 하세요.

> [!NOTE]
> 최종 사용자가 레코드 집합에서의 레코드 뷰 컨트롤을 새로 고치는 기능을 제공해야 합니다. 이 기능을 제공하지 않는 경우 사용자가 컨트롤 값을 잘못된 값으로 변경하면 현재 레코드에서 영구적으로 작업이 중지될 수 있습니다. 컨트롤을 새로 고치려면 `CWnd` FALSE 매개 변수를 사용 하 여 멤버 함수 [updatedata](../mfc/reference/cwnd-class.md#updatedata) 를 호출 합니다.

## <a name="see-also"></a>참고 항목

[레코드 뷰 사용](../data/using-a-record-view-mfc-data-access.md)
