---
description: '자세히 알아보기: 직접 컨트롤 추가'
title: 수동으로 컨트롤 추가
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
ms.openlocfilehash: f6dfa65baa037aa168697aa7abcd3eedc76cc4d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339081"
---
# <a name="adding-controls-by-hand"></a>수동으로 컨트롤 추가

대화 [상자 편집기를 사용 하 여 대화 상자에 컨트롤을 추가](using-the-dialog-editor-to-add-controls.md) 하거나 코드를 사용 하 여 컨트롤을 직접 추가할 수 있습니다.

컨트롤 개체를 직접 만들려면 일반적으로 c + + 컨트롤 개체를 c + + 대화 상자 또는 프레임 창 개체에 포함 시킵니다. 프레임 워크의 다른 많은 개체와 마찬가지로 컨트롤은 2 단계 생성을 요구 합니다. 부모 대화 상자 또는 프레임 창을 만들 때 컨트롤의 **Create** member 함수를 호출 해야 합니다. 대화 상자의 경우이 작업은 일반적으로 [OnInitDialog](reference/cdialog-class.md#oninitdialog), [OnCreate](reference/cwnd-class.md#oncreate)에서 프레임 창의 경우에 수행 됩니다.

다음 예제에서는 `CEdit` 파생 된 대화 상자 클래스의 클래스 선언에서 개체를 선언한 다음에서 멤버 함수를 호출 하는 방법을 보여 줍니다 `Create` `OnInitDialog` . 개체는 `CEdit` 포함 된 개체로 선언 되기 때문에 대화 상자 개체가 생성 될 때 자동으로 생성 되지만 여전히 자체 멤버 함수를 사용 하 여 초기화 되어야 합니다 `Create` .

[!code-cpp[NVC_MFCControlLadenDialog#1](codesnippet/cpp/adding-controls-by-hand_1.h)]

다음 `OnInitDialog` 함수는 사각형을 설정 하 고를 호출 `Create` 하 여 Windows 편집 컨트롤을 만들고 초기화 되지 않은 개체에 연결 합니다 `CEdit` .

[!code-cpp[NVC_MFCControlLadenDialog#2](codesnippet/cpp/adding-controls-by-hand_2.cpp)]

편집 개체를 만든 후에는 멤버 함수를 호출 하 여 컨트롤에 대 한 입력 포커스를 설정할 수도 있습니다 `SetFocus` . 마지막으로에서 0을 반환 `OnInitDialog` 하 여 포커스를 설정 하는 것을 보여 줍니다. 0이 아닌 값을 반환 하면 대화 상자 관리자가 대화 상자 항목 목록의 첫 번째 컨트롤 항목으로 포커스를 설정 합니다. 대부분의 경우 대화 상자 편집기를 사용 하 여 대화 상자에 컨트롤을 추가 합니다.

## <a name="see-also"></a>참고 항목

[컨트롤 만들기 및 사용](making-and-using-controls.md)<br/>
[컨트롤](controls-mfc.md)<br/>
[CDialog::OnInitDialog](reference/cdialog-class.md#oninitdialog)
