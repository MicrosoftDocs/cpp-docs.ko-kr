---
description: '자세히 알아보기: 속성 시트 및 속성 페이지 (MFC)'
title: 속성 시트 및 속성 페이지(MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
ms.openlocfilehash: 6819b890c699aeb428d2e0c76b048f5043e1dee7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248855"
---
# <a name="property-sheets-and-property-pages-mfc"></a>속성 시트 및 속성 페이지(MFC)

MFC [대화 상자](../mfc/dialog-boxes.md) 는 속성 시트와 속성 페이지를 통합 하 여 "탭 대화 상자"를 통해 수행할 수 있습니다. MFC에서 "속성 시트" 라고 하는 이러한 종류의 대화 상자는 Microsoft Word, Excel 및 Visual C++의 여러 대화 상자와 유사 하 게 이러한 종류의 대화 상자를 표시 합니다 .이 대화 상자는 앞에서 뒤로 표시 되는 파일 폴더의 스택 또는 종속 된 창 그룹의 경우와 매우 유사 합니다. 앞면 탭의 컨트롤이 표시 됩니다. 레이블이 지정 된 탭만 후면 탭에서 볼 수 있습니다. 속성 시트는 여러 그룹으로 분류 되는 많은 수의 속성 또는 설정을 관리 하는 데 특히 유용 합니다. 일반적으로 하나의 속성 시트는 여러 개의 개별 대화 상자를 대체 하 여 사용자 인터페이스를 단순화할 수 있습니다.

MFC 버전 4.0부터 속성 시트 및 속성 페이지는 Windows 95 및 Windows NT 버전 3.51 이상과 함께 제공 되는 공용 컨트롤을 사용 하 여 구현 됩니다.

속성 시트는 *MFC 참조* 에 설명 된 [CPropertySheet](../mfc/reference/cpropertysheet-class.md) 및 [CPropertyPage](../mfc/reference/cpropertypage-class.md) 클래스를 사용 하 여 구현 됩니다. `CPropertySheet` 에 따라 여러 개의 "페이지"를 포함할 수 있는 전체 대화 상자를 정의 합니다 `CPropertyPage` .

속성 시트를 만들고 사용 하는 방법에 대 한 자세한 내용은 [속성 시트](../mfc/property-sheets-mfc.md)항목을 참조 하세요.

## <a name="see-also"></a>참고 항목

[대화 상자](../mfc/dialog-boxes.md)<br/>
[MFC에서 대화 상자를 통해 작업](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[MFC의 속성 시트 및 속성 페이지](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[데이터 교환](../mfc/exchanging-data.md)<br/>
[모덜리스 속성 시트 만들기](../mfc/creating-a-modeless-property-sheet.md)<br/>
[적용 단추 처리](../mfc/handling-the-apply-button.md)
