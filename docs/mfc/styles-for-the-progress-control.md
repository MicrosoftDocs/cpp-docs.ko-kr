---
description: '자세히 알아보기: 진행률 컨트롤에 대 한 스타일'
title: 진행률 컨트롤 스타일
ms.date: 11/19/2018
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
ms.openlocfilehash: cd6ce1093f8bd2e3271a386e894d1e8dcd1a4fd7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216498"
---
# <a name="styles-for-the-progress-control"></a>진행률 컨트롤 스타일

진행률 컨트롤 ([CProgressCtrl:: create](../mfc/reference/cprogressctrl-class.md#create))을 처음 만들 때 *dwstyle* 매개 변수를 사용 하 여 진행률 컨트롤에 원하는 창 스타일을 지정 합니다. 다음 목록에서는 적용 가능한 창 스타일을 자세히 설명 합니다. 컨트롤은 여기에 나열 된 것과 다른 모든 창 스타일을 무시 합니다. 컨트롤은 항상 자식 창 (일반적으로 대화 상자 부모)으로 만들어야 합니다.

|창 스타일|효과|
|------------------|------------|
|WS_BORDER|창 주위에 테두리를 만듭니다.|
|WS_CHILD|자식 창을 만듭니다 (항상에 사용 되어야 함 `CProgressCtrl` ).|
|WS_CLIPCHILDREN|부모 창에서 그릴 때 자식 창이 차지 하는 영역을 제외 합니다. 부모 창을 만들 때 사용 됩니다.|
|WS_CLIPSIBLINGS|서로를 기준으로 자식 창을 자릅니다.|
|WS_DISABLED|처음에 사용 하지 않도록 설정 된 창을 만듭니다.|
|WS_VISIBLE|처음에 표시 되는 창을 만듭니다.|
|WS_TABSTOP|사용자가 TAB 키를 눌러 이동할 때 컨트롤이 포커스를 받을 수 있도록 지정 합니다.|

또한 진행률 컨트롤, PBS_VERTICAL 및 PBS_SMOOTH에만 적용 되는 두 가지 스타일을 지정할 수 있습니다.

PBS_VERTICAL를 사용 하 여 가로가 아닌 컨트롤을 세로로 맞춥니다. PBS_SMOOTH를 사용 하 여 컨트롤을 증분 방식으로 채우는 작은 표시 사각형을 표시 하는 대신 컨트롤을 완전히 채웁니다.

PBS_SMOOTH 스타일 없음:

![표준 진행률 막대 스타일](../mfc/media/vc4ruw1.gif "표준 진행률 막대 스타일")

PBS_SMOOTH 및 PBS_VERTICAL 스타일 사용:

![진행률 막대 스타일, 부드러운 세로줄](../mfc/media/vc4ruw2.gif "진행률 막대 스타일, 부드러운 세로줄")

자세한 내용은 *MFC 참조* 의 [창 스타일](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CProgressCtrl 사용](../mfc/using-cprogressctrl.md)
