---
description: '자세한 정보: OLE 컨테이너 클래스'
title: OLE 컨테이너 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 1525fb41f15952d62b6b3c9a7603480d1e399229
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222231"
---
# <a name="ole-container-classes"></a>OLE 컨테이너 클래스

이러한 클래스는 컨테이너 응용 프로그램에서 사용 됩니다. `COleLinkingDoc`및 `COleDocument` 는 모두 개체의 컬렉션을 관리 `COleClientItem` 합니다. 문서 클래스를에서 파생 하는 대신 `CDocument` `COleLinkingDoc` `COleDocument` 문서에 포함 된 개체에 대 한 링크를 지원 하려는 지 여부에 따라 또는에서 문서 클래스를 파생 합니다.

개체를 사용 `COleClientItem` 하 여 문서에서 다른 문서에 포함 되어 있거나 다른 문서에 대 한 링크인 각 OLE 항목을 나타냅니다.

[COleDocObjectItem](reference/coledocobjectitem-class.md)<br/>
액티브 문서 포함을 지원 합니다.

[COleDocument](reference/coledocument-class.md)<br/>
기본 컨테이너 지원 뿐만 아니라 복합 문서 구현에 사용 됩니다. 에서 파생 된 클래스의 컨테이너 역할을 `CDocItem` 합니다. 이 클래스는 컨테이너 문서에 대 한 기본 클래스로 사용 될 수 있으며의 기본 클래스입니다 `COleServerDoc` .

[COleLinkingDoc](reference/colelinkingdoc-class.md)<br/>
`COleDocument`연결을 위한 인프라를 제공 하는에서 파생 된 클래스입니다. 포함 된 개체에 대 한 링크를 지원 하려는 경우 대신이 클래스에서 컨테이너 응용 프로그램에 대 한 문서 클래스를 파생 해야 합니다 `COleDocument` .

[CRichEditDoc](reference/cricheditdoc-class.md)<br/>
Rich edit 컨트롤에 있는 OLE 클라이언트 항목의 목록을 유지 관리 합니다. [CRichEditView](reference/cricheditview-class.md) 및 [CRichEditCntrItem](reference/cricheditcntritem-class.md)와 함께 사용 됩니다.

[CDocItem](reference/cdocitem-class.md)<br/>
및의 추상 기본 `COleClientItem` 클래스 `COleServerItem` 입니다. 에서 파생 된 클래스의 개체는 `CDocItem` 문서의 일부를 나타냅니다.

[COleClientItem](reference/coleclientitem-class.md)<br/>
포함 되거나 연결 된 OLE 항목에 대 한 클라이언트의 연결을 나타내는 클라이언트 항목 클래스입니다. 이 클래스에서 클라이언트 항목을 파생 시킵니다.

[CRichEditCntrItem](reference/cricheditcntritem-class.md)<br/>
및와 함께 사용할 경우 rich edit 컨트롤에 저장 된 OLE 항목에 대 한 클라이언트 쪽 액세스를 제공 합니다 `CRichEditView` `CRichEditDoc` .

[COleException](reference/coleexception-class.md)<br/>
OLE 처리 중 오류로 인해 발생하는 예외입니다. 이 클래스는 컨테이너 및 서버에서 모두 사용됩니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
