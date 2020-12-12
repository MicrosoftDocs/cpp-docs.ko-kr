---
description: '자세한 정보: MFC의 속성 시트 및 속성 페이지'
title: MFC의 속성 시트 및 속성 페이지
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
ms.openlocfilehash: 93662dcf07e2810ad9f4f51d6df8341f9f6df6dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185429"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>MFC의 속성 시트 및 속성 페이지

속성 시트 (탭 대화 상자 라고도 함)는 속성 페이지를 포함 하는 대화 상자입니다. 각 속성 페이지는 대화 상자 템플릿 리소스를 기반으로 하며 컨트롤을 포함 합니다. 위쪽에 탭이 있는 페이지로 묶여 있습니다. 탭은 페이지의 이름을 지정 하 고 용도를 나타냅니다. 사용자가 속성 시트에서 탭을 클릭 하 여 컨트롤 집합을 선택할 수 있습니다.

페이지를 사용 하 여 속성 시트의 컨트롤을 의미 있는 집합으로 그룹화 합니다. 일반적으로 포함 된 속성 시트에는 자체의 여러 컨트롤이 있습니다. 이는 모든 페이지에 적용 됩니다.

속성 시트는 [CPropertySheet](../mfc/reference/cpropertysheet-class.md)클래스를 기반으로 합니다. 속성 페이지는 [CPropertyPage](../mfc/reference/cpropertypage-class.md)클래스를 기반으로 합니다.

속성 시트는 뷰의 현재 선택 항목과 같은 일부 외부 개체의 특성을 수정 하는 데 일반적으로 사용 되는 특별 한 종류의 대화 상자입니다. 속성 시트에는 세 가지 주요 부분, 즉 포함 대화 상자, 한 번에 하나씩 표시 된 하나 이상의 속성 페이지, 사용자가 해당 페이지를 선택 하기 위해 클릭 하는 각 페이지의 맨 위에 있는 탭이 있습니다. 속성 시트는 여러 유사한 설정이 나 변경할 옵션 그룹이 있는 경우에 유용 합니다. 속성 시트는 이해 하기 쉬운 방식으로 정보를 그룹화 합니다.

> [!NOTE]
> 를 사용 하 여 속성 시트를 표시 하려고 하면 `CPropertySheet::DoModal` 시스템에서 첫 번째 예외를 생성할 수 있습니다. 이 예외는 시스템에서 개체를 만들기 전에 개체의 [창 스타일](../mfc/reference/styles-used-by-mfc.md#window-styles) 을 변경 하려고 하기 때문에 발생 합니다. 이 예외에 대 한 자세한 내용과이 예외를 방지 하거나 처리 하는 방법에 대 한 자세한 내용은 [CPropertySheet::D oModal](../mfc/reference/cpropertysheet-class.md#domodal)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[속성 시트](../mfc/property-sheets-mfc.md)
