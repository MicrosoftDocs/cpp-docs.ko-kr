---
description: '자세한 정보: 공용 컨트롤을 자식 창으로 사용'
title: 공용 컨트롤을 자식 창으로 사용
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
ms.openlocfilehash: 5a5fda2cbf8d0bf16ccb17f2766b31d24e5c0c67
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263558"
---
# <a name="using-a-common-control-as-a-child-window"></a>공용 컨트롤을 자식 창으로 사용

모든 Windows 공용 컨트롤은 다른 창의 자식 창으로 사용할 수 있습니다. 다음 절차에서는 공용 컨트롤을 동적으로 만든 다음 사용 하는 방법을 설명 합니다.

### <a name="to-use-a-common-control-as-a-child-window"></a>공용 컨트롤을 자식 창으로 사용 하려면

1. 관련 클래스 또는 처리기에서 컨트롤을 정의 합니다.

1. 컨트롤의 [CWnd:: Create](../mfc/reference/cwnd-class.md#create) 메서드 재정의를 사용 하 여 Windows 컨트롤을 만듭니다.

1. 컨트롤을 하위 클래스를 사용 하는 경우 처리기의 초기에 컨트롤을 만든 후에는 `OnCreate` 해당 멤버 함수를 사용 하 여 컨트롤을 조작할 수 있습니다. 메서드에 대 한 자세한 내용은 [컨트롤](../mfc/controls-mfc.md) 의 개별 컨트롤에 대 한 설명을 참조 하십시오.

1. 컨트롤을 마치면 [CWnd::D estroyWindow](../mfc/reference/cwnd-class.md#destroywindow) 를 사용 하 여 컨트롤을 제거 합니다.

## <a name="see-also"></a>참고 항목

[컨트롤 만들기 및 사용](../mfc/making-and-using-controls.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
