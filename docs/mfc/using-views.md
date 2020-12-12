---
description: '자세히 알아보기: 뷰 사용'
title: 뷰 사용
ms.date: 11/04/2016
helpviewer_keywords:
- interacting with users and role of view class [MFC]
- drawing [MFC], data
- rendering data
- view classes [MFC], role in managing user interaction
- CView class [MFC], view architecture
- MFC, views
- views [MFC], using
- painting data
- user input [MFC], interpreting through view class [MFC]
- view classes [MFC], role in displaying application data
ms.assetid: dc3de6ad-5c64-4317-8f10-8bdcc38cdbd5
ms.openlocfilehash: f17855c1389da44630a21830033c4457db6e3703
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236648"
---
# <a name="using-views"></a>뷰 사용

뷰의 책임은 문서의 데이터를 사용자에 게 그래픽으로 표시 하 고 사용자 입력을 문서에 대 한 작업으로 해석 하 고 해석 하는 것입니다. 뷰 클래스를 작성 하는 작업은 다음과 같습니다.

- 문서 데이터를 렌더링 하는 뷰 클래스의 [OnDraw](../mfc/reference/cview-class.md#ondraw) 멤버 함수를 작성 합니다.

- 적절 한 Windows 메시지 및 메뉴 항목과 같은 사용자 인터페이스 개체를 뷰 클래스의 메시지 처리기 멤버 함수에 연결 합니다.

- 사용자 입력을 해석 하도록 이러한 처리기를 구현 합니다.

또한 `CView` 파생 된 뷰 클래스에서 다른 멤버 함수를 재정의 해야 할 수도 있습니다. 특히 뷰의 특수 초기화를 수행 하도록 [Oninitialupdate](../mfc/reference/cview-class.md#oninitialupdate) 를 재정의 하 고 뷰가 자체 다시 그리기 직전에 필요한 특별 한 처리를 [OnUpdate](../mfc/reference/cview-class.md#onupdate) 할 수 있습니다. 다중 페이지 문서의 경우 인쇄 대화 상자를 인쇄 하는 데 사용할 페이지 수와 기타 정보를 사용 하 여 인쇄 대화 상자를 초기화 하려면 [Onprepareprinting](../mfc/reference/cview-class.md#onprepareprinting) 를 재정의 해야 합니다. 멤버 함수 재정의에 대 한 자세한 내용은 `CView` *MFC 참조* 의 [CView](../mfc/reference/cview-class.md) 클래스를 참조 하세요.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [MFC에서 사용할 수 있는 파생된 뷰 클래스](../mfc/derived-view-classes-available-in-mfc.md)

- [뷰에 그리기](../mfc/drawing-in-a-view.md)

- [뷰를 통해 사용자 입력 해석](../mfc/interpreting-user-input-through-a-view.md)

- [인쇄 중인 뷰의 역할](../mfc/role-of-the-view-in-printing.md)

- [뷰 스크롤 및 크기 조정](../mfc/scrolling-and-scaling-views.md)

- [문서 및 뷰 초기화 및 정리](../mfc/initializing-and-cleaning-up-documents-and-views.md)

## <a name="see-also"></a>참고 항목

[문서/뷰 아키텍처](../mfc/document-view-architecture.md)<br/>
[CFormView 클래스](../mfc/reference/cformview-class.md)<br/>
[레코드 뷰 (MFC Data Access)](../data/record-views-mfc-data-access.md)<br/>
[Serialization 메커니즘 무시](../mfc/bypassing-the-serialization-mechanism.md)
