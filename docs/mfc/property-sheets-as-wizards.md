---
description: '자세히 알아보기: 속성 시트를 마법사로'
title: 마법사 역할을 하는 속성 시트
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
ms.openlocfilehash: 2a68a16936e8ab134bab2fe78dac0d29c125b4db
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248868"
---
# <a name="property-sheets-as-wizards"></a>마법사 역할을 하는 속성 시트

마법사 속성 시트의 주요 특징은 탭 대신 다음 또는 마침, 뒤로 및 취소 단추를 사용 하 여 탐색을 제공 한다는 것입니다. 이 기능을 활용 하려면 속성 시트 개체에서 [CPropertySheet::D oModal](../mfc/reference/cpropertysheet-class.md#domodal) 을 호출 하기 전에 [CPropertySheet:: setwizardmode](../mfc/reference/cpropertysheet-class.md#setwizardmode) 를 호출 해야 합니다.

사용자는 한 페이지에서 다른 페이지로 이동 하는 동안 동일한 [CPropertyPage:: OnSetActive](../mfc/reference/cpropertypage-class.md#onsetactive) 및 [CPropertyPage:: OnKillActive](../mfc/reference/cpropertypage-class.md#onkillactive) 알림을 받습니다. 다음 단추와 마침 단추는 함께 사용할 수 없는 컨트롤입니다. 즉, 한 번에 하나만 표시 됩니다. 첫 번째 페이지에서 다음 단추를 사용 하도록 설정 해야 합니다. 사용자가 마지막 페이지에 있는 경우 마침 단추를 사용 하도록 설정 해야 합니다. 이는 프레임 워크에서 자동으로 수행 되지 않습니다. 이를 위해서는 마지막 페이지에서 [CPropertySheet:: SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons) 을 호출 해야 합니다.

모든 기본 단추를 표시 하려면 마침 단추를 표시 하 고 다음 단추를 이동 mush. 그런 다음 다음 단추에 대 한 상대 위치가 유지 되도록 뒤로 단추를 이동 합니다.

## <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]

## <a name="see-also"></a>참고 항목

[속성 시트](../mfc/property-sheets-mfc.md)
