---
description: '자세히 알아보기: 적용 단추 처리'
title: 적용 단추 처리
ms.date: 11/04/2016
helpviewer_keywords:
- Apply button in property sheet
- property sheets, Apply button
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
ms.openlocfilehash: a626dcab04d68d19efba79465bfca46545ff6670
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254939"
---
# <a name="handling-the-apply-button"></a>적용 단추 처리

속성 시트에는 표준 대화 상자에서 사용자가 속성 시트를 닫기 전에 수행한 변경 내용을 적용할 수 있는 기능이 있습니다. 적용 단추를 사용 하 여이 작업을 수행 합니다. 이 문서에서는이 기능을 올바르게 구현 하는 데 사용할 수 있는 방법을 설명 합니다.

모달 대화 상자는 일반적으로 사용자가 확인을 클릭 하 여 대화 상자를 닫을 때 외부 개체에 설정을 적용 합니다. 속성 시트의 경우에도 마찬가지입니다. 사용자가 확인을 클릭 하면 속성 시트의 새 설정이 적용 됩니다.

그러나 속성 시트 대화 상자를 닫지 않고도 사용자가 설정을 저장할 수 있도록 할 수 있습니다. 이는 적용 단추의 기능입니다. 적용 단추를 클릭 하면 현재 활성 페이지의 현재 설정만 적용 하는 것과는 반대로 모든 속성 페이지의 현재 설정이 외부 개체에 적용 됩니다.

기본적으로 적용 단추는 항상 사용 하지 않도록 설정 되어 있습니다. 적절 한 시간에 적용 단추를 사용 하도록 설정 하는 코드를 작성 해야 하며, 아래에서 설명 하는 대로 적용 효과를 구현 하는 코드를 작성 해야 합니다.

사용자에 게 적용 기능을 제공 하지 않으려면 적용 단추를 제거할 필요가 없습니다. 이후 버전의 Windows에서 사용할 수 있는 표준 속성 시트 지원을 사용 하는 응용 프로그램 간에 공통적으로 유지 되므로 사용 하지 않도록 설정할 수 있습니다.

페이지를 수정 된 것으로 보고 하 고 적용 단추를 사용 하도록 설정 하려면를 호출 `CPropertyPage::SetModified( TRUE )` 합니다. 수정 되는 페이지 보고서가 있는 경우 현재 활성 페이지가 수정 되었는지 여부에 관계 없이 적용 단추가 활성화 된 상태로 유지 됩니다.

사용자가 페이지의 설정을 변경할 때마다 [CPropertyPage:: SetModified](reference/cpropertypage-class.md#setmodified) 를 호출 해야 합니다. 사용자가 페이지에서 설정을 변경 하는 경우를 감지 하는 한 가지 방법은 속성 페이지의 각 컨트롤에 대 한 변경 알림 처리기 (예: **EN_CHANGE** 또는 **BN_CLICKED**)를 구현 하는 것입니다.

적용 단추의 효과를 구현 하려면 속성 시트에서 속성 페이지에 현재 설정을 적용 하기 위해 응용 프로그램의 소유자 또는 다른 외부 개체를 알려 주어 야 합니다. 동시에 속성 시트에서 `CPropertyPage::SetModified( FALSE )` 외부 개체에 대 한 수정 내용을 적용 한 모든 페이지에 대해를 호출 하 여 적용 단추를 사용 하지 않도록 설정 해야 합니다.

이 프로세스에 대 한 예제는 MFC 일반 샘플 [PROPDLG](../overview/visual-cpp-samples.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[속성 시트](property-sheets-mfc.md)
