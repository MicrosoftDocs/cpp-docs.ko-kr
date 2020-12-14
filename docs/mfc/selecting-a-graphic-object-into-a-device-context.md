---
description: '자세한 정보: 장치 컨텍스트에 그래픽 개체 선택'
title: 그래픽 개체를 선택하여 디바이스 컨텍스트로 넣기
ms.date: 11/04/2016
helpviewer_keywords:
- graphic objects [MFC], selecting into device context
- SelectObject method [MFC]
- GDI objects [MFC], device contexts
- lifetime, graphic objects [MFC]
- device contexts, selecting graphic objects into
- device contexts, graphic objects [MFC]
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
ms.openlocfilehash: cc2aabbcb1614fc77e5eadf9e6fba13ba377a4c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217681"
---
# <a name="selecting-a-graphic-object-into-a-device-context"></a>그래픽 개체를 선택하여 디바이스 컨텍스트로 넣기

이 항목은 창의 장치 컨텍스트에서 그래픽 개체를 사용 하는 데 적용 됩니다. [그리기 개체를 만든](../mfc/one-stage-and-two-stage-construction-of-objects.md)후에는 여기에 저장 된 기본 개체 대신 장치 컨텍스트에서 해당 개체를 선택 해야 합니다.

[!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/cpp/selecting-a-graphic-object-into-a-device-context_1.cpp)]

## <a name="lifetime-of-graphic-objects"></a>그래픽 개체 수명

[SelectObject](../mfc/reference/cdc-class.md#selectobject) 에서 반환 된 그래픽 개체는 "임시"입니다. 즉, 다음에 프로그램이 유휴 시간을 받을 때 클래스의 [OnIdle](../mfc/reference/cwinapp-class.md#onidle) 멤버 함수에 의해 삭제 됩니다 `CWinApp` . `SelectObject`컨트롤을 주 메시지 루프로 반환 하지 않고 단일 함수에서 반환 된 개체를 사용 하는 경우에는 문제가 발생 하지 않습니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [그래픽 개체](../mfc/graphic-objects.md)

- [1단계 및 2단계 그래픽 개체 생성](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [디바이스 컨텍스트](../mfc/device-contexts.md)

- [뷰에 그리기](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>참고 항목

[그래픽 개체](../mfc/graphic-objects.md)
