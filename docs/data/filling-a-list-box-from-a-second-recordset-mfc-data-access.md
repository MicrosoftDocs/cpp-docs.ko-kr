---
title: 두 번째 레코드 집합 (데이터 액세스)에서 목록 상자 채우기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, filling list boxes
- list boxes, filling from second recordset
- recordsets [C++], filling list boxes or combo boxes
- CComboBox class, filling object from second rowset
- ODBC recordsets [C++], filling list boxes or combo boxes
- combo boxes [C++], filling from second recordset
- CListCtrl class, filling from second recordset
ms.assetid: 360c0834-da6b-4dc0-bcea-80e9acd611f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ed294527b4335459ab6d0658d9f57a5cb64a8fd1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="filling-a-list-box-from-a-second-recordset--mfc-data-access"></a>번째 레코드 집합에서 목록 상자 채우기  (MFC Data Access)
기본적으로 레코드 뷰는 해당 필드가 레코드 뷰의 컨트롤로 매핑되는 단일 레코드 집합 개체와 연결됩니다. 레코드 뷰에 목록 상자 또는 콤보 상자 컨트롤을 삽입하고 두 번째 레코드 집합 개체의 값을 채우는 경우가 있습니다. 이때 사용자는 목록 상자를 사용하여 레코드 뷰에 표시할 새 정보 범주를 선택할 수 있습니다. 이 항목에서는 이러한 작업을 수행하는 방법과 시기에 대해 설명합니다.  
  
> [!TIP]
>  데이터 소스에서 콤보 상자나 목록 상자를 채우는 작업은 속도가 느릴 수 있습니다. 그러므로 가급적이면 레코드 수가 많은 레코드 집합에서 컨트롤을 채우지 않아야 합니다.  
  
 이 항목의 모델은 폼의 컨트롤을 채우는 기본 레코드 집합과 목록 상자 또는 콤보 상자를 채우는 두 번째 레코드 집합으로 구성됩니다. 목록 상자에서 문자열을 선택하면 선택한 항목에 따라 프로그램이 기본 레코드 집합을 다시 쿼리합니다. 다음 절차에서는 콤보 상자를 사용하지만 목록 상자에도 동일한 절차가 적용됩니다.  
  
#### <a name="to-fill-a-combo-box-or-list-box-from-a-second-recordset"></a>두 번째 레코드 집합에서 콤보 상자 또는 목록 상자를 채우려면  
  
1.  레코드 집합 개체를 만듭니다 ([CRecordset](../mfc/reference/crecordset-class.md)합니다.  
  
2.  한 포인터를 가져옵니다는 [CComboBox](../mfc/reference/ccombobox-class.md) 콤보 상자 컨트롤에 대 한 개체입니다.  
  
3.  콤보 상자에서 이전 콘텐츠를 비웁니다.  
  
4.  레코드 집합의 모든 레코드 간을 이동 호출 [ccombobox:: Addstring](../mfc/reference/ccombobox-class.md#addstring) 콤보 상자에 추가할 현재 레코드에서 각 문자열에 대 한 합니다.  
  
5.  콤보 상자의 선택 항목을 초기화합니다.  
  
```  
void CSectionForm::OnInitialUpdate()  
{  
    // ...  
  
    // Fill the combo box with all of the courses  
    CENROLLDoc* pDoc = GetDocument();  
    if (!pDoc->m_courseSet.Open())  
        return;  
  
    // ...  
  
    m_ctlCourseList.ResetContent();  
    if (pDoc->m_courseSet.IsOpen())  
    {   
        while (!pDoc->m_courseSet.IsEOF() )  
        {  
            m_ctlCourseList.AddString(  
                pDoc->m_courseSet.m_CourseID);  
            pDoc->m_courseSet.MoveNext();  
        }  
    }  
    m_ctlCourseList.SetCurSel(0);  
}  
```  
  
 이 함수는 제공되는 각 과정에 대한 레코드를 포함하는 두 번째 레코드 집합(`m_courseSet`)과 레코드 뷰 클래스에 저장되는 `CComboBox` 컨트롤(`m_ctlCourseList`)을 사용합니다.  
  
 함수는 문서에서 `m_courseSet`를 가져와서 엽니다. 그런 다음 `m_ctlCourseList`를 비우고 `m_courseSet`를 스크롤합니다. 그리고 각 레코드에 대해 콤보 상자의 `AddString` 멤버 함수를 호출하여 레코드의 과정 ID 값을 추가합니다. 마지막으로 코드가 콤보 상자의 선택 항목을 설정합니다.  
  
## <a name="see-also"></a>참고 항목  
 [레코드 뷰 (데이터 액세스)](../data/record-views-mfc-data-access.md)   
 [ODBC 드라이버 목록](../data/odbc/odbc-driver-list.md)