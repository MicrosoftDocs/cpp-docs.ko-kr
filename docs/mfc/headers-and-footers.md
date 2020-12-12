---
description: '자세한 정보: 머리글 및 바닥글'
title: 머리글 및 바닥글
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], multipage documents
- page headers [MFC], printing
- headers [MFC], printing
- footers [MFC], printing
- page footers [MFC], printing
- page headers [MFC]
- printing [MFC], headers and footers
- page footers [MFC]
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
ms.openlocfilehash: 8b2b6c3278e512d5e8ceff63b003ed05a99d78bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325907"
---
# <a name="headers-and-footers"></a>머리글 및 바닥글

이 문서에서는 인쇄 된 문서에 머리글과 바닥글을 추가 하는 방법을 설명 합니다.

화면에서 문서를 살펴보면 문서 이름과 문서 내의 현재 위치는 일반적으로 제목 표시줄과 상태 표시줄에 표시 됩니다. 문서의 인쇄 된 복사본을 볼 때 머리글 또는 바닥글에 표시 되는 이름과 페이지 번호를 포함 하는 것이 유용 합니다. 이 방법은 WYSIWYG 프로그램이 인쇄 및 화면 표시를 수행 하는 방식에 차이가 있는 일반적인 방법입니다.

[OnPrint](reference/cview-class.md#onprint) 멤버 함수는 각 페이지에 대해 호출 되기 때문에 머리글 또는 바닥글을 인쇄 하는 적절 한 위치가 며 화면 표시가 아닌 인쇄용 으로만 호출 되기 때문입니다. 별도의 함수를 정의 하 여 머리글 또는 바닥글을 인쇄 하 고에서 프린터 장치 컨텍스트를 전달할 수 있습니다 `OnPrint` . 페이지의 본문이 머리글이 나 바닥글과 겹치지 않도록 하려면 [OnDraw](reference/cview-class.md#ondraw) 를 호출 하기 전에 창 원점 또는 익스텐트를 조정 해야 할 수 있습니다. `OnDraw`페이지에 맞는 문서 크기를 줄일 수 있기 때문에를 수정 해야 할 수도 있습니다.

머리글이 나 바닥글에서 수행 하는 영역을 보정 하는 한 가지 방법은 [Cprintinfo](reference/cprintinfo-structure.md)의 **m_rectDraw** 멤버를 사용 하는 것입니다. 페이지가 인쇄 될 때마다이 멤버가 페이지의 사용 가능한 영역으로 초기화 됩니다. 페이지의 본문을 인쇄 하기 전에 머리글이 나 바닥글을 인쇄 하면 **m_rectDraw** 에 저장 된 사각형의 크기를 줄여 머리글이 나 바닥글에서 사용 하는 영역을 확인할 수 있습니다. 그런 다음 `OnPrint` **m_rectDraw** 를 참조 하 여 페이지 본문 인쇄를 위해 남은 영역을 확인할 수 있습니다.

헤더는 CDC의 멤버 함수를 호출 하기 전에 호출 되기 때문에 [Onpreparedc](reference/cview-class.md#onpreparedc)에서 인쇄할 수 없습니다 `StartPage` . [](reference/cdc-class.md) 이 시점에서 프린터 장치 컨텍스트는 페이지 경계에 있는 것으로 간주 됩니다. 멤버 함수 에서만 인쇄를 수행할 수 있습니다 `OnPrint` .

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [다중 페이지 문서 인쇄](multipage-documents.md)

- [인쇄용 GDI 리소스 할당](allocating-gdi-resources.md)

## <a name="see-also"></a>참고 항목

[인쇄](printing.md)
