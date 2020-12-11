---
description: '자세히 알아보기: 인쇄'
title: 인쇄
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: 0cb4455b2de27d7b609226099b00a37dc8175db6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154866"
---
# <a name="printing"></a>인쇄

Microsoft Windows는 장치 독립적 디스플레이를 구현 합니다. 즉, MFC에서 `OnDraw` 뷰 클래스의 멤버 함수에 있는 동일한 그리기 호출은 프린터와 같은 다른 장치 및 디스플레이에서 그리기를 담당 합니다. 인쇄 미리 보기의 경우 대상 장치는 디스플레이에 시뮬레이트된 프린터 출력입니다.

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> 인쇄의 역할 및 프레임 워크의 역할

뷰 클래스의 책임은 다음과 같습니다.

- 문서에 있는 페이지 수를 프레임 워크에 알립니다.

- 지정 된 페이지를 인쇄 하 라는 메시지가 표시 되 면 문서의 해당 부분을 그립니다.

- 인쇄에 필요한 글꼴이 나 기타 GDI (그래픽 장치 인터페이스) 리소스를 할당 및 할당 취소 합니다.

- 필요한 경우 지정 된 페이지를 인쇄 하기 전에 프린터 모드를 변경 하는 데 필요한 모든 이스케이프 코드를 전송 합니다 (예: 페이지 별로 인쇄 방향 변경).

프레임 워크의 책임은 다음과 같습니다.

- **인쇄** 대화 상자를 표시 합니다.

- 프린터에 대 한 [CDC](reference/cdc-class.md) 개체를 만듭니다.

- 개체의 [startdoc](reference/cdc-class.md#startdoc) 및 [enddoc](reference/cdc-class.md#enddoc) 멤버 함수를 호출 합니다 `CDC` .

- 개체의 [StartPage](reference/cdc-class.md#startpage) 멤버 함수 `CDC` 를 반복적으로 호출 하 고, 인쇄 될 페이지를 뷰 클래스에 알리고, 개체의 [endpage](reference/cdc-class.md#endpage) 멤버 함수를 호출 합니다 `CDC` .

- 뷰에서 재정의 가능한 함수를 적절 한 시간에 호출 합니다.

다음 문서에서는 프레임 워크에서 인쇄 및 인쇄 미리 보기를 지 원하는 방법을 설명 합니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [기본 인쇄가 수행되는 방법](how-default-printing-is-done.md)

- [다중 페이지 문서](multipage-documents.md)

- [머리글 및 바닥글](headers-and-footers.md)

- [인쇄용 GDI 리소스 할당](allocating-gdi-resources.md)

- [인쇄 미리 보기](print-preview-architecture.md)

## <a name="see-also"></a>참고 항목

[인쇄 및 인쇄 미리 보기](printing-and-print-preview.md)
