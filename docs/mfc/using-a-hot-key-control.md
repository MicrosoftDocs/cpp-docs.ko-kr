---
description: '자세한 정보: 바로 가기 키 컨트롤 사용'
title: 바로 가기 키 컨트롤 사용
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
ms.openlocfilehash: 078cd4b3d4746723d5996959edad20dd44e9abec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202706"
---
# <a name="using-a-hot-key-control"></a>바로 가기 키 컨트롤 사용

핫 키 컨트롤의 일반적인 사용법은 다음 패턴을 따릅니다.

- 컨트롤이 만들어집니다. 컨트롤이 대화 상자 템플릿에 지정될 경우 대화 상자를 만들 때 자동으로 만들어집니다. (바로 가기 키 컨트롤에 해당 하는 대화 상자 클래스에 [Chotkeyctrl](../mfc/reference/chotkeyctrl-class.md) 멤버가 있어야 합니다.) 또는 [create](../mfc/reference/chotkeyctrl-class.md#create) member 함수를 사용 하 여 모든 창의 자식 창으로 컨트롤을 만들 수 있습니다.

- 컨트롤에 대 한 기본값을 설정 하려면 [Sethotkey](../mfc/reference/chotkeyctrl-class.md#sethotkey) 멤버 함수를 호출 합니다. 특정 교대 상태를 방지 하려면 [SetRules](../mfc/reference/chotkeyctrl-class.md#setrules)를 호출 합니다. 대화 상자의 컨트롤에 대해이 작업을 수행 하는 데 좋은 시간은 대화 상자의 [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) 함수에서 수행 하는 것입니다.

- 사용자는 바로 가기 키 컨트롤에 포커스가 있을 때 바로 가기 키 조합을 눌러 컨트롤과 상호 작용 합니다. 사용자는 대화 상자에서 단추를 클릭 하 여이 작업이 완료 되었음을 나타냅니다.

- 사용자가 바로 가기 키를 선택 했다는 알림이 프로그램에 표시 되는 경우에는 [Gethotkey](../mfc/reference/chotkeyctrl-class.md#gethotkey) 멤버 함수를 사용 하 여 바로 가기 키 컨트롤에서 가상 키와 이동 상태 값을 검색 해야 합니다.

- 사용자가 선택한 키를 알고 있는 경우 [바로 가기 키 설정](../mfc/setting-a-hot-key.md)에 설명 된 방법 중 하나를 사용 하 여 바로 가기 키를 설정할 수 있습니다.

- 바로 가기 키 컨트롤이 대화 상자에 있는 경우 해당 컨트롤 및 개체는 `CHotKeyCtrl` 자동으로 제거 됩니다. 그렇지 않은 경우 컨트롤 및 `CHotKeyCtrl` 개체가 모두 제대로 소멸되었는지 확인해야 합니다.

## <a name="see-also"></a>참고 항목

[CHotKeyCtrl 사용](../mfc/using-chotkeyctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
