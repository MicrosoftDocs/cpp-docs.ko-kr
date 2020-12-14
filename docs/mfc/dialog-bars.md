---
description: '자세히 알아보기: 대화 상자 모음'
title: 대화 상자 모음
ms.date: 11/19/2018
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
ms.openlocfilehash: 701954dc9ec682bd95258b26d7af1290ea2da521
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261634"
---
# <a name="dialog-bars"></a>대화 상자 모음

대화 상자 모음은 모든 종류의 컨트롤을 포함할 수 있는 일종의 [컨트롤 모음](control-bars.md) 입니다. 모덜리스 대화 상자의 특성을 가지 므로 [CDialogBar](reference/cdialogbar-class.md) 개체는 보다 강력한 도구 모음을 제공 합니다.

도구 모음과 개체 간에는 몇 가지 주요 차이점이 있습니다 `CDialogBar` . `CDialogBar`개체는 대화 상자 템플릿 리소스에서 생성 되며, Visual C++ 대화 상자 편집기를 사용 하 여 만들 수 있으며 모든 종류의 Windows 컨트롤을 포함할 수 있습니다. 사용자가 컨트롤에서 컨트롤로 tab 키를 누를 수 있습니다. 또한 맞춤 스타일을 지정 하 여 부모 프레임 창의 모든 부분을 포함 하는 대화 상자 표시줄을 정렬 하거나 부모 크기를 조정 하는 경우에는 그대로 둘 수 있습니다. 다음 그림은 다양 한 컨트롤을 포함 하는 대화 상자 모음을 보여 줍니다.

![VC 대화 상자 막대](../mfc/media/vc378t1.gif "VC 대화 상자 막대") <br/>
대화 상자 표시줄

다른 측면에서는 개체 작업을 `CDialogBar` 모덜리스 대화 상자와 함께 사용 하는 것과 같습니다. 대화 상자 편집기를 사용 하 여 대화 상자 리소스를 디자인 하 고 만들 수 있습니다.

대화 상자 표시줄의 virtues 중 하나는 단추 이외의 컨트롤을 포함할 수 있다는 것입니다.

에서 고유한 대화 상자 클래스를 파생 하는 것은 `CDialog` 일반적 이지만 일반적으로 대화 상자 모음에 대 한 고유한 클래스를 파생 하지 않습니다. 대화 상자 모음은 주 창에 대 한 확장 이며 **BN_CLICKED** 또는 **EN_CHANGE** 와 같은 대화 상자 컨트롤 알림 메시지는 주 창인 대화 상자 모음의 부모로 전송 됩니다.

## <a name="see-also"></a>참고 항목

[사용자 인터페이스 요소](user-interface-elements-mfc.md)<br/>
[샘플](../overview/visual-cpp-samples.md)
