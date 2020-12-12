---
description: '자세히 알아보기: 서버: 서버 항목'
title: '서버: 서버 항목'
ms.date: 11/04/2016
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
ms.openlocfilehash: e3fceb3abe89ca6cda432d60441a47fc0d452cfc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217317"
---
# <a name="servers-server-items"></a>서버: 서버 항목

사용자가 포함 또는 연결된 OLE 항목을 편집할 수 있도록 컨테이너가 서버를 시작하면 서버 애플리케이션은 &quot;서버 항목&quot;을 만듭니다. `COleServerItem`에서 파생된 클래스의 개체인 서버 항목은 서버 문서와 컨테이너 애플리케이션 사이의 인터페이스를 제공합니다.

`COleServerItem` 클래스는 일반적으로 컨테이너의 요청에 따라서 OLE에 의해 호출된 여러 재정의 가능한 멤버 함수를 정의합니다. 서버 항목은 서버 문서의 일부 또는 전체 문서를 나타낼 수 있습니다. OLE 항목이 컨테이너 문서에 포함되면 서버 항목은 전체 서버 문서를 나타냅니다. OLE 항목이 연결되면 서버 항목은 연결이 일부에 대한 것인지 또는 전체에 대한 것인지에 따라 서버 문서의 일부나 전체 문서를 나타낼 수 있습니다.

예를 들어 [HIERSVR](../overview/visual-cpp-samples.md) 샘플에서 서버 항목 클래스에는 `CServerItem` 클래스의 개체에 대 한 포인터인 멤버가 있습니다 `CServerNode` . `CServerNode`개체는 HIERSVR 응용 프로그램의 문서에 있는 노드이며 트리입니다. `CServerNode`개체가 루트 노드인 경우 `CServerItem` 개체는 전체 문서를 나타냅니다. `CServerNode`개체가 자식 노드인 경우 `CServerItem` 개체는 문서의 일부를 나타냅니다. 이러한 상호 작용에 대 한 예제는 MFC OLE 샘플 [HIERSVR](../overview/visual-cpp-samples.md) 를 참조 하십시오.

## <a name="implementing-server-items"></a><a name="_core_implementing_server_items"></a> 서버 항목 구현

애플리케이션 마법사를 사용하여 애플리케이션에 대한 &quot;시작&quot; 코드를 생성하는 경우 시작 코드에 서버 항목을 포함하려면 OLE 옵션 페이지에서 서버 옵션 중 하나를 선택하기만 하면 됩니다. 기존 애플리케이션에 서버 항목을 추가하는 경우 다음 단계를 수행합니다.

#### <a name="to-implement-a-server-item"></a>서버 항목을 구현하려면

1. `COleServerItem`에서 클래스를 파생합니다.

1. 파생 클래스에서 `OnDraw` 멤버 함수를 재정의합니다.

   프레임워크는 `OnDraw`를 호출하여 OLE 항목을 메타파일로 렌더링합니다. 컨테이너 애플리케이션은 이 메타파일을 사용하여 항목을 렌더링합니다. 애플리케이션의 뷰 클래스에는 `OnDraw` 멤버 함수도 있습니다. 이 함수는 서버 애플리케이션이 활성화인 경우 항목을 렌더링하는 데 사용됩니다.

1. 서버 문서 클래스에 대한 `OnGetEmbeddedItem`의 재정의를 구현합니다. 자세한 내용은 서버 [: 서버 문서 구현](../mfc/servers-implementing-server-documents.md) 및 MFC OLE 샘플 [HIERSVR](../overview/visual-cpp-samples.md)문서를 참조 하세요.

1. 서버 항목 클래스의 `OnGetExtent` 멤버 함수를 구현합니다. 프레임워크는 항목의 크기를 검색하기 위해 이 함수를 호출합니다. 기본 구현은 아무 작업도 수행하지 않습니다.

## <a name="a-tip-for-server-item-architecture"></a><a name="_core_a_tip_for_server.2d.item_architecture"></a> Server-Item 아키텍처에 대 한 팁

서버 [항목 구현](#_core_implementing_server_items)에 설명 된 것 처럼 서버 응용 프로그램은 서버 뷰 및 컨테이너 응용 프로그램에서 사용 하는 메타 파일 모두에서 항목을 렌더링할 수 있어야 합니다. MFC 라이브러리의 응용 프로그램 아키텍처에서 뷰 클래스의 `OnDraw` 멤버 함수는 편집 될 때 항목을 렌더링 합니다 ( *클래스 라이브러리 참조* 의 [CView:: OnDraw](../mfc/reference/cview-class.md#ondraw) 참조). 서버 항목의는 `OnDraw` 다른 모든 경우에 항목을 메타 파일로 렌더링 합니다 ( [COleServerItem:: OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)참조).

서버 문서 클래스에서 도우미 함수를 작성하고 뷰와 서버 항목 클래스의 `OnDraw` 함수에서 해당 함수를 호출하여 코드의 중복을 방지할 수 있습니다. MFC OLE 샘플 [HIERSVR](../overview/visual-cpp-samples.md) 는이 전략을 사용 합니다. 즉 `CServerView::OnDraw` , 함수와 `CServerItem::OnDraw` 를 모두 호출 `CServerDoc::DrawTree` 하 여 항목을 렌더링 합니다.

다양한 상황에서 그리기 때문에 뷰 및 항목은 모두 `OnDraw` 멤버 함수를 보유합니다. 뷰는 확대/축소, 크기 및 범위 선택, 클리핑 및 사용자 인터페이스 요소(예: 스크롤 막대)와 같은 요소를 고려해야 합니다. 반면에 서버 항목은 항상 전체 OLE 개체를 그립니다.

자세한 내용은 *클래스 라이브러리 참조* 의 [CView:: ondraw](../mfc/reference/cview-class.md#ondraw), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem:: ondraw](../mfc/reference/coleserveritem-class.md#ondraw)및 [COleServerDoc:: OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[서버](../mfc/servers.md)
