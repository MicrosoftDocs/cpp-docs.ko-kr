---
description: '자세한 정보: OLE 서버 클래스'
title: OLE 서버 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: a2f60f148d6a24323ca6546e633c30103b315ee2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243993"
---
# <a name="ole-server-classes"></a>OLE 서버 클래스

이러한 클래스는 서버 응용 프로그램에서 사용 됩니다. 서버 문서는가 아닌에서 파생 됩니다 `COleServerDoc` `CDocument` . `COleServerDoc`는에서 파생 되므로 `COleLinkingDoc` 서버 문서는 링크를 지 원하는 컨테이너가 될 수도 있습니다.

`COleServerItem`클래스는 다른 문서에 포함 되거나에 연결 될 수 있는 문서 또는 문서 부분을 나타냅니다.

`COleIPFrameWnd` 및은 `COleResizeBar` 개체가 컨테이너에 있는 동안 내부 편집을 지원 하 고 `COleTemplateServer` 다른 응용 프로그램의 OLE 개체를 편집할 수 있도록 문서/뷰 쌍 만들기를 지원 합니다.

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
서버 응용 프로그램 문서 클래스의 기본 클래스로 사용 됩니다. `COleServerDoc` 개체는 개체와의 상호 작용을 통해 대량의 서버 지원을 제공 `COleServerItem` 합니다. 시각적 편집 기능은 클래스 라이브러리의 문서/뷰 아키텍처를 사용 하 여 제공 됩니다.

[CDocItem](reference/cdocitem-class.md)<br/>
및의 추상 기본 `COleClientItem` 클래스 `COleServerItem` 입니다. 에서 파생 된 클래스의 개체는 `CDocItem` 문서의 일부를 나타냅니다.

[COleServerItem](reference/coleserveritem-class.md)<br/>
항목에 대 한 OLE 인터페이스를 나타내는 데 사용 `COleServerDoc` 됩니다. 일반적으로 `COleServerDoc` 문서의 포함 된 부분을 나타내는 하나의 개체가 있습니다. 문서 파트에 대 한 링크를 지 원하는 서버에서는 여러 개체가 있을 수 있으며 `COleServerItem` , 각 개체는 문서의 특정 부분에 대 한 링크를 나타냅니다.

[클래스에서 파생하는 대신](reference/coleipframewnd-class.md)<br/>
서버 문서를 편집 하는 동안 보기에 대 한 프레임 창을 제공 합니다.

[COleResizeBar](reference/coleresizebar-class.md)<br/>
내부 크기 조정을 위한 표준 사용자 인터페이스를 제공 합니다. 이 클래스의 개체는 항상 개체와 함께 사용 됩니다 `COleIPFrameWnd` .

[COleTemplateServer](reference/coletemplateserver-class.md)<br/>
프레임 워크의 문서/뷰 아키텍처를 사용 하 여 문서를 만드는 데 사용 됩니다. `COleTemplateServer`개체는 대부분의 작업을 연결 된 개체에 위임 `CDocTemplate` 합니다.

[COleException](reference/coleexception-class.md)<br/>
OLE 처리 중 오류로 인해 발생하는 예외입니다. 이 클래스는 컨테이너 및 서버에서 모두 사용됩니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
