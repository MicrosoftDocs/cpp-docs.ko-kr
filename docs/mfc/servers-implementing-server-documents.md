---
description: '자세히 알아보기: 서버: 서버 문서 구현'
title: '서버: 서버 문서 구현'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
ms.openlocfilehash: b8843d3e2ac662cbb018a3063c9f04f5dd8d6f10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217330"
---
# <a name="servers-implementing-server-documents"></a>서버: 서버 문서 구현

이 문서에서는 응용 프로그램 마법사에서 OLE 서버 옵션을 지정 하지 않은 경우 서버 문서를 성공적으로 구현 하기 위해 수행 해야 하는 단계를 설명 합니다.

#### <a name="to-define-a-server-document-class"></a>서버 문서 클래스를 정의 하려면

1. 대신에서 문서 클래스를 파생 시킵니다 `COleServerDoc` `CDocument` .

1. 에서 파생 된 서버 항목 클래스를 만듭니다 `COleServerItem` .

1. `OnGetEmbeddedItem`서버 문서 클래스의 멤버 함수를 구현 합니다.

   `OnGetEmbeddedItem` 컨테이너 응용 프로그램의 사용자가 포함 된 항목을 만들거나 편집할 때가 호출 됩니다. 전체 문서를 나타내는 항목을 반환 해야 합니다. 이 클래스는 파생 클래스의 개체 여야 합니다 `COleServerItem` .

1. `Serialize`멤버 함수를 재정의 하 여 문서의 내용을 serialize 합니다. 문서에서 네이티브 데이터를 표시 하는 데 사용 하지 않는 한 서버 항목 목록을 직렬화 할 필요가 없습니다. 자세한 내용은 서버 [: 서버 항목](../mfc/servers-server-items.md)문서에서 *서버 항목 구현* 을 참조 하세요.

서버 문서를 만들면 프레임 워크에서 자동으로 OLE 시스템 Dll을 사용 하 여 문서를 등록 합니다. 이렇게 하면 Dll이 서버 문서를 식별할 수 있습니다.

자세한 내용은 *클래스 라이브러리 참조* 에서 [COleServerItem](../mfc/reference/coleserveritem-class.md) 및 [COleServerDoc](../mfc/reference/coleserverdoc-class.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[서버](../mfc/servers.md)<br/>
[서버: 서버 항목](../mfc/servers-server-items.md)<br/>
[서버: 서버 구현](../mfc/servers-implementing-a-server.md)<br/>
[서버: In-Place 프레임 창 구현](../mfc/servers-implementing-in-place-frame-windows.md)
