---
description: '자세히 알아보기: 문서 클래스'
title: 문서 클래스
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: 7f5bd3011dec84cad20b10668e0a997838e79dbb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330289"
---
# <a name="document-classes"></a>문서 클래스

문서 템플릿 개체에서 만든 문서 클래스 개체는 응용 프로그램의 데이터를 관리 합니다. 이러한 클래스 중 하나에서 문서에 대 한 클래스를 파생 시킵니다.

문서 클래스 개체는 뷰 개체와 상호 작용 합니다. 뷰 개체는 창의 클라이언트 영역을 나타내고, 문서의 데이터를 표시 하 고, 사용자가 상호 작용할 수 있도록 합니다. 문서와 보기는 문서 템플릿 개체에 의해 생성 됩니다.

[CDocument](reference/cdocument-class.md)<br/>
응용 프로그램별 문서에 대 한 기본 클래스입니다. 에서 문서 클래스 또는 클래스를 파생 시킵니다 `CDocument` .

[COleDocument](reference/coledocument-class.md)<br/>
기본 컨테이너 지원 뿐만 아니라 복합 문서 구현에 사용 됩니다. [Cdocitem](reference/cdocitem-class.md)에서 파생 된 클래스의 컨테이너 역할을 합니다. 이 클래스는 컨테이너 문서에 대 한 기본 클래스로 사용 될 수 있으며의 기본 클래스입니다 `COleServerDoc` .

[COleLinkingDoc](reference/colelinkingdoc-class.md)<br/>
`COleDocument`연결을 위한 인프라를 제공 하는에서 파생 된 클래스입니다. 포함 된 개체에 대 한 링크를 지원 하려는 경우 대신이 클래스에서 컨테이너 응용 프로그램에 대 한 문서 클래스를 파생 해야 합니다 `COleDocument` .

[CRichEditDoc](reference/cricheditdoc-class.md)<br/>
Rich edit 컨트롤에 있는 OLE 클라이언트 항목의 목록을 유지 관리 합니다. [CRichEditView](reference/cricheditview-class.md) 및 [CRichEditCntrItem](reference/cricheditcntritem-class.md)와 함께 사용 됩니다.

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
서버 응용 프로그램 문서 클래스의 기본 클래스로 사용 됩니다. `COleServerDoc` 개체는 [COleServerItem](reference/coleserveritem-class.md) 개체와의 상호 작용을 통해 대량의 서버 지원을 제공 합니다. 시각적 편집 기능은 클래스 라이브러리의 문서/뷰 아키텍처를 사용 하 여 제공 됩니다.

[CHtmlEditDoc](reference/chtmleditdoc-class.md)<br/>
MFC 문서 뷰 아키텍처 컨텍스트 내에서 WebBrowser HTML 편집 플랫폼의 기능을 [CHtmlEditView](reference/chtmleditview-class.md)와 함께 제공 합니다.

## <a name="related-classes"></a>관련 클래스

문서 클래스 개체는 영구적 일 수 있습니다. 즉, 저장소 매체에 상태를 쓰고 다시 읽을 수 있습니다. MFC는 `CArchive` 문서 데이터를 저장 미디어로 쉽게 전송할 수 있는 클래스를 제공 합니다.

[CArchive](reference/carchive-class.md)<br/>
Serialization을 통해 개체에 대 한 영구 저장소를 구현 하려면 [CFile](reference/cfile-class.md) 개체와 협력 합니다 ( [CObject:: Serialize](reference/cobject-class.md#serialize)참조).

문서에는 OLE 개체도 포함 될 수 있습니다. `CDocItem` 는 서버 및 클라이언트 항목의 기본 클래스입니다.

[CDocItem](reference/cdocitem-class.md)<br/>
[COleClientItem](reference/coleclientitem-class.md) 및 [COleServerItem](reference/coleserveritem-class.md)의 추상 기본 클래스입니다. 에서 파생 된 클래스의 개체는 `CDocItem` 문서의 일부를 나타냅니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
