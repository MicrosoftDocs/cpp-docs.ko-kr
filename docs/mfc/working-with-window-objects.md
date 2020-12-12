---
description: '자세히 알아보기: 창 개체 작업'
title: 창 개체 작업
ms.date: 11/04/2016
helpviewer_keywords:
- child windows [MFC], working with
- window objects [MFC], working with
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
ms.openlocfilehash: 4a8c6f2c40eadbfe53aa79683bea29847adf684f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172594"
---
# <a name="working-with-window-objects"></a>창 개체 작업

두 가지 종류의 작업에 대 한 windows 호출을 사용 합니다.

- Windows 메시지 처리

- 창에서 그리기

사용자 고유의 자식 창을 포함 하 여 창에서 Windows 메시지를 처리 하려면 [함수에 메시지 매핑](../mfc/reference/mapping-messages-to-functions.md) 을 참조 하 여 c + + 창 클래스에 메시지를 매핑합니다. 그런 다음 클래스에서 메시지 처리기 멤버 함수를 작성 합니다.

프레임 워크 응용 프로그램에서 대부분의 그리기는 뷰에서 발생 하며, 창 내용을 그려야 할 때마다 해당 [OnDraw](../mfc/reference/cview-class.md#ondraw) 멤버 함수가 호출 됩니다. 창이 뷰의 자식인 경우 창의 멤버 함수 중 하나를 호출 하 여 보기의 그리기를 자식 창에 위임할 수 있습니다 `OnDraw` .

어떤 경우 든 그리기를 위해 장치 컨텍스트가 필요 합니다. 창에 연결 된 장치 컨텍스트에 포함 된 스톡 펜, 브러시 및 기타 그래픽 개체를 사용할 수 있습니다. 또는 이러한 개체를 수정 하 여 필요한 그리기 효과를 얻을 수 있습니다. 원하는 대로 장치 컨텍스트를 설정 하 고, [CDC](../mfc/reference/cdc-class.md) (장치 컨텍스트 클래스) 클래스의 멤버 함수를 호출 하 여 선, 도형 및 텍스트를 그립니다. 색을 사용 하려면 좌표계를 사용 하 여 작업 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [메시지 처리 및 매핑](../mfc/message-handling-and-mapping.md)

- [뷰에 그리기](../mfc/drawing-in-a-view.md)

- [디바이스 컨텍스트](../mfc/device-contexts.md)

- [그래픽 개체](../mfc/graphic-objects.md)

## <a name="see-also"></a>참고 항목

[창 개체](../mfc/window-objects.md)
