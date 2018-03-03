---
title: "액티브 문서 서버 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3dacb923b2e51ddc031165e637b08c9614ee1bf3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="active-document-servers"></a>액티브 문서 서버
Word, Excel 또는 PowerPoint와 같은 액티브 문서 서버는 액티브 문서라고 부르는 다른 응용 프로그램 형식의 문서를 호스팅합니다. 다른 문서의 페이지 내에 간단히 표시되는 OLE 포함 개체와 달리 액티브 문서는 문서를 만드는 서버 응용 프로그램의 전체 인터페이스 및 완전한 고유 기능을 제공합니다. 사용자는 원하는 응용 프로그램의 모든 기능을 사용해서 문서를 만들 수 있지만(액티브 문서가 사용하도록 설정된 경우), 결과 프로젝트를 단일 엔터티로 취급할 수 있습니다.  
  
 액티브 문서는 두 개 이상의 페이지를 포함할 수 있으며 항상 내부 활성 상태입니다. 해당 메뉴와 병합 하 여 사용자 인터페이스의 일부를 제어 하는 액티브 문서는 **파일** 및 **도움말** 컨테이너의 메뉴. 액티브 문서는 컨테이너의 전체 편집 영역을 차지하고 프린터 페이지의 보기 및 레이아웃을 제어합니다(여백, 바닥글 등).  
  
 MFC는 문서/보기 인터페이스, 명령 디스패치 맵, 인쇄, 메뉴 관리 및 레지스트리 관리가 포함된 액티브 문서 서버를 구현합니다. 특정 프로그래밍 요구 사항에 대해서는 설명 [액티브 문서](../mfc/active-documents.md)합니다.  
  
 MFC는 액티브 문서를 지원 합니다.는 [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) 에서 파생 된 클래스 [CCmdTarget](../mfc/reference/ccmdtarget-class.md), 및 [CDocObjectServerItem](../mfc/reference/cdocobjectserveritem-class.md)에서 파생 된 [ COleServerItem](../mfc/reference/coleserveritem-class.md)합니다. MFC는 액티브 문서 컨테이너를 지원 합니다.는 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md) 에서 파생 된 클래스 [COleClientItem](../mfc/reference/coleclientitem-class.md)합니다.  
  
 `CDocObjectServer`는 액티브 문서 인터페이스를 매핑하고 액티브 문서를 초기화 및 활성화합니다. MFC는 또한 ACTIVE 문서에서 명령 라우팅을 처리하는 매크로를 제공합니다. 응용 프로그램에서 액티브 문서를 사용하려면 StdAfx.h 파일에 AfxDocOb.h를 포함합니다.  
  
 일반적인 MFC 서버는 고유 `COleServerItem` 파생 클래스를 연결합니다. MFC 응용 프로그램 마법사 선택 하는 경우이 클래스를 생성의 **미니 서버** 또는 **풀 서버** 확인란 복합 문서 지원 응용 프로그램 서버를 제공 합니다. 또한 선택 하는 경우는 **액티브 문서 서버** 확인란, MFC 응용 프로그램 마법사에서 파생 된 클래스를 생성 `CDocObjectServerItem` 대신 합니다.  
  
 `COleDocObjectItem` 클래스는 OLE 컨테이너가 액티브 문서 컨테이너가 되도록 허용합니다. MFC 응용 프로그램 마법사를 사용 하 여 선택 하 여 액티브 문서 컨테이너를 만들 수는 **액티브 문서 컨테이너** MFC 응용 프로그램 마법사의 복합 문서 지원 페이지에서 확인란을 선택 합니다. 자세한 내용은 참조 [액티브 문서 컨테이너 응용 프로그램 만들기](../mfc/creating-an-active-document-container-application.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [활성 문서 포함](../mfc/active-document-containment.md)

