---
description: '자세한 정보: 애니메이션 컨트롤 사용'
title: 애니메이션 컨트롤 사용
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], animation
- CAnimateCtrl class [MFC], animation controls
- animation controls [MFC]
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
ms.openlocfilehash: 7ef4a7b5eb005569ac2a3e3cb66cc0ed785e9299
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202719"
---
# <a name="using-an-animation-control"></a>애니메이션 컨트롤 사용

애니메이션 컨트롤의 일반적인 사용법은 다음 패턴을 따릅니다.

- 컨트롤이 만들어집니다. 컨트롤이 대화 상자 템플릿에 지정될 경우 대화 상자를 만들 때 자동으로 만들어집니다. 애니메이션 컨트롤에 해당 하는 대화 상자 클래스에 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) 멤버가 있어야 합니다. 또는 [create](../mfc/reference/canimatectrl-class.md#create) member 함수를 사용 하 여 모든 창의 자식 창으로 컨트롤을 만들 수 있습니다.

- [Open](../mfc/reference/canimatectrl-class.md#open) 멤버 함수를 호출 하 여 애니메이션 컨트롤에 AVI 클립을 로드 합니다. 애니메이션 컨트롤이 대화 상자에 있는 경우 대화 상자 클래스의 [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) 함수에서이 작업을 수행 하는 것이 좋습니다.

- [Play](../mfc/reference/canimatectrl-class.md#play) 멤버 함수를 호출 하 여 클립을 재생 합니다. 애니메이션 컨트롤이 대화 상자에 있는 경우 대화 상자 클래스의 함수에서이 작업을 수행 하는 것이 좋습니다 `OnInitDialog` . `Play`애니메이션 컨트롤에 ACS_AUTOPLAY 스타일이 설정 되어 있으면를 호출할 필요가 없습니다.

- 클립의 일부를 표시 하거나 프레임별로 재생 하려면 `Seek` 멤버 함수를 사용 합니다. 재생 중인 클립을 중지 하려면 멤버 함수를 사용 `Stop` 합니다.

- 컨트롤을 즉시 삭제 하지 않으려면 구성원 함수를 호출 하 여 메모리에서 클립을 제거 `Close` 합니다.

- 애니메이션 컨트롤이 대화 상자에 있는 경우 해당 컨트롤 및 `CAnimateCtrl` 개체는 자동으로 제거 됩니다. 그렇지 않은 경우 컨트롤 및 `CAnimateCtrl` 개체가 모두 제대로 소멸되었는지 확인해야 합니다. 컨트롤을 소멸 시키면 AVI 클립이 자동으로 닫힙니다.

## <a name="see-also"></a>참고 항목

[CAnimateCtrl 사용](../mfc/using-canimatectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
