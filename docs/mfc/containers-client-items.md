---
description: '자세히 알아보기: 컨테이너: 클라이언트 항목'
title: '컨테이너: 클라이언트 항목'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
ms.openlocfilehash: e8aff84e825723b1615a0dbbadf7d5fec6d4cef1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310436"
---
# <a name="containers-client-items"></a>컨테이너: 클라이언트 항목

이 문서에서는 클라이언트 항목 및 응용 프로그램이 클라이언트 항목을 파생 시킬 클래스에 대해 설명 합니다.

클라이언트 항목은 OLE 컨테이너 응용 프로그램의 문서에 포함 되었거나 참조 되는 다른 응용 프로그램에 속하는 데이터 항목입니다. 문서에 포함 된 데이터를 포함 하는 클라이언트 항목 해당 데이터가 컨테이너 문서에서 참조 하는 다른 위치에 저장 되어 있는 경우에는 연결 됩니다.

OLE 응용 프로그램의 문서 클래스는가 아닌 [Coledocument](reference/coledocument-class.md) 클래스에서 파생 됩니다 `CDocument` . `COleDocument`클래스는 `CDocument` MFC 응용 프로그램의 기반이 되는 문서/뷰 아키텍처를 사용 하는 데 필요한 모든 기능에서 상속 됩니다. `COleDocument` 또한 문서를 개체 컬렉션으로 처리 하는 인터페이스를 정의 `CDocItem` 합니다. `COleDocument`해당 컬렉션의 요소를 추가, 검색 및 삭제 하기 위한 여러 멤버 함수가 제공 됩니다.

모든 컨테이너 응용 프로그램은에서 하나 이상의 클래스를 파생 해야 합니다 `COleClientItem` . 이 클래스의 개체는 OLE 문서에 포함 되거나 연결 된 항목을 나타냅니다. 이러한 개체는 문서에서 삭제 되는 경우를 제외 하 고 해당 개체를 포함 하는 문서 수명 동안 존재 합니다.

`CDocItem` 에 대 한 기본 클래스인 `COleClientItem` 고 `COleServerItem`입니다. 이러한 두 클래스에서 파생 된 클래스의 개체는 각각 OLE 항목과 클라이언트 및 서버 응용 프로그램 간의 중개자 역할을 합니다. 새 OLE 항목이 문서에 추가 될 때마다 MFC 프레임 워크는 클라이언트 응용 프로그램의 파생 클래스의 새 개체를 `COleClientItem` 문서의 개체 컬렉션에 추가 `CDocItem` 합니다.

## <a name="see-also"></a>참고 항목

[컨테이너](containers.md)<br/>
[컨테이너: 복합 파일](containers-compound-files.md)<br/>
[컨테이너: User-Interface 문제](containers-user-interface-issues.md)<br/>
[컨테이너: 고급 기능](containers-advanced-features.md)<br/>
[COleClientItem 클래스](reference/coleclientitem-class.md)<br/>
[COleServerItem 클래스](reference/coleserveritem-class.md)
