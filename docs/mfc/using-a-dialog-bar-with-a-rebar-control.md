---
description: '자세한 정보: Rebar 컨트롤에 대화 상자 모음 사용'
title: 대화 상자 모음과 Rebar 컨트롤 함께 사용
ms.date: 11/04/2016
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
ms.openlocfilehash: 97fb8ca5c356d91fa4b4ba44753fbdc9bf298435
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263532"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>대화 상자 모음과 Rebar 컨트롤 함께 사용

[Rebar 컨트롤 및 밴드](../mfc/rebar-controls-and-bands.md)에 설명 된 대로 각 밴드에는 하나의 자식 창 (또는 컨트롤)만 포함 될 수 있습니다. 이는 밴드 마다 자식 창을 두 개 이상 포함 하려는 경우에 제한이 있을 수 있습니다. 편리한 해결 방법은 여러 컨트롤이 있는 대화 상자 표시줄 리소스를 만든 다음, rebar 컨트롤에 rebar 밴드 (대화 상자 모음 포함)를 추가 하는 것입니다.

일반적으로 대화 상자 표시줄 밴드를 투명 하 게 표시 하려면 대화 상자 모음 개체에 대 한 WS_EX_TRANSPARENT 확장 스타일을 설정 합니다. 그러나 WS_EX_TRANSPARENT는 대화 상자 모음의 배경을 제대로 칠하는 데 문제가 있기 때문에 원하는 효과를 얻기 위해 약간의 추가 작업을 수행 해야 합니다.

다음 절차에서는 WS_EX_TRANSPARENT 확장 스타일을 사용 하지 않고 투명성을 구현 하는 데 필요한 단계를 자세히 설명 합니다.

### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>Rebar 밴드에서 투명 대화 상자를 구현 하려면

1. [클래스 추가 대화 상자](../mfc/reference/adding-an-mfc-class.md)를 사용 하 여 `CMyDlgBar` 대화 상자 표시줄 개체를 구현 하는 새 클래스 (예:)를 추가 합니다.

1. WM_ERASEBKGND 메시지에 대 한 처리기를 추가 합니다.

1. 새 처리기에서 기존 코드를 다음 예제와 일치 하도록 수정 합니다.

   [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]

1. WM_MOVE 메시지에 대 한 처리기를 추가 합니다.

1. 새 처리기에서 기존 코드를 다음 예제와 일치 하도록 수정 합니다.

   [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]

새 처리기는 WM_ERASEBKGND 메시지를 부모 창으로 전달 하 고 대화 상자 표시줄 개체가 이동 될 때마다 강제로 다시 그리기를 수행 하 여 대화 상자의 투명도를 시뮬레이션 합니다.

## <a name="see-also"></a>참고 항목

[CReBarCtrl 사용](../mfc/using-crebarctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
