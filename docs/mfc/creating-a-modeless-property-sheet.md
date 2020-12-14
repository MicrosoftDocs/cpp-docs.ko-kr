---
description: '자세히 알아보기: 모덜리스 속성 시트 만들기'
title: 모덜리스 속성 시트 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
ms.openlocfilehash: 1eaec55fe3c7c69ba558a10616dc2658025282d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310059"
---
# <a name="creating-a-modeless-property-sheet"></a>모덜리스 속성 시트 만들기

일반적으로 사용자가 만드는 속성 시트는 모달이 됩니다. 모달 속성 시트를 사용 하는 경우 사용자는 응용 프로그램의 다른 부분을 사용 하기 전에 속성 시트를 닫아야 합니다. 이 문서에서는 사용자가 응용 프로그램의 다른 부분을 사용 하는 동안 속성 시트를 열어 둘 수 있는 모덜리스 속성 시트를 만드는 데 사용할 수 있는 메서드를 설명 합니다.

속성 시트를 모달 대화 상자 대신 모덜리스 대화 상자로 표시 하려면 [DoModal](reference/cpropertysheet-class.md#domodal)대신 [CPropertySheet:: Create](reference/cpropertysheet-class.md#create) 를 호출 합니다. 또한 모덜리스 속성 시트를 지원 하기 위해 몇 가지 추가 작업을 구현 해야 합니다.

추가 작업 중 하나는 속성 시트와 속성 시트를 열 때 수정 하는 외부 개체 간에 데이터를 교환 하는 것입니다. 일반적으로 표준 모덜리스 대화 상자와 같은 작업입니다. 이 작업의 일부는 모덜리스 속성 시트와 속성 설정이 적용 되는 외부 개체 간의 통신 채널을 구현 하는 것입니다. 이 구현은 모덜리스 속성 시트에 대해 [CPropertySheet](reference/cpropertysheet-class.md) 에서 클래스를 파생 하는 경우 훨씬 더 쉽습니다. 이 문서에서는 사용자가를 완료 했다고 가정 합니다.

모덜리스 속성 시트와 외부 개체 (예: 뷰의 현재 선택 항목) 간에 통신 하는 한 가지 방법은 속성 시트에서 외부 개체에 대 한 포인터를 정의 하는 것입니다. 파생 클래스에 함수 (과 같은 항목 이라고 함)를 정의 `SetMyExternalObject` `CPropertySheet` 하 여 포커스가 외부 개체 간에 변경 될 때마다 포인터를 변경 합니다. `SetMyExternalObject`함수는 새로 선택한 외부 개체가 반영 되도록 각 속성 페이지에 대 한 설정을 다시 설정 해야 합니다. 이를 위해 함수는 `SetMyExternalObject` 클래스에 속한 [CPropertyPage](reference/cpropertypage-class.md) 개체에 액세스할 수 있어야 합니다 `CPropertySheet` .

속성 시트 내에서 속성 페이지에 대 한 액세스를 제공 하는 가장 편리한 방법은 `CPropertyPage` 개체를 파생 개체에 포함 하는 것입니다 `CPropertySheet` . 파생 개체에 개체를 포함 하는 것은 `CPropertyPage` `CPropertySheet` 속성 시트의 소유자가 개체를 만들고 `CPropertyPage` [CPropertySheet:: AddPage](reference/cpropertysheet-class.md#addpage)를 통해 속성 시트에 전달 하는 일반적인 모달 디자인 대화 상자와 다릅니다.

모덜리스 속성 시트의 설정을 외부 개체에 적용할지 여부를 결정 하는 데는 여러 가지 사용자 인터페이스 대안이 있습니다. 한 가지 대안은 사용자가 값을 변경할 때마다 현재 속성 페이지의 설정을 적용 하는 것입니다. 또 다른 방법은 적용 단추를 제공 하는 것입니다 .이 단추를 사용 하면 사용자가 속성 페이지에서 변경 내용을 외부 개체에 커밋하기 전에 누적 시킬 수 있습니다. 적용 단추를 처리 하는 방법에 대 한 자세한 내용은 [적용 단추 처리](handling-the-apply-button.md)문서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[속성 시트](property-sheets-mfc.md)<br/>
[데이터 교환](exchanging-data.md)<br/>
[MFC에서 대화 상자를 통해 작업](life-cycle-of-a-dialog-box.md)
