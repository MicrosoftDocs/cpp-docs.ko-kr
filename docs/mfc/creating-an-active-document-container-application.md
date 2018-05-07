---
title: 액티브 문서 컨테이너 응용 프로그램 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 880c6953addd0ec7db3abf5864010bd472d2d5a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-an-active-document-container-application"></a>액티브 문서 컨테이너 응용 프로그램 만들기
액티브 문서 컨테이너 응용 프로그램을 만드는 가장 간단하고 가장 권장되는 방법은 MFC 응용 프로그램 마법사를 사용해서 MFC EXE 컨테이너 응용 프로그램을 만들고 액티브 문서 포함을 지원하도록 응용 프로그램을 수정하는 방법입니다.  
  
#### <a name="to-create-an-active-document-container-application"></a>액티브 문서 컨테이너 응용 프로그램을 만들려면  
  
1.  **파일** 메뉴를 클릭 하 여 **프로젝트**에서 **새로** 하위 메뉴.  
  
2.  왼쪽된 창에서 클릭 **Visual c + +** 프로젝트 유형입니다.  
  
3.  선택 **MFC 응용 프로그램** 오른쪽 창에서.  
  
4.  프로젝트 이름을 `MyProj`, 클릭 **확인**합니다.  
  
5.  선택 된 **복합 문서 지원** 페이지.  
  
6.  선택 된 **컨테이너** 또는 **컨테이너/풀 서버** 옵션입니다.  
  
7.  선택 된 **액티브 문서 컨테이너** 확인란 합니다.  
  
8.  **마침**을 클릭합니다.  
  
9. MFC 응용 프로그램 마법사에서 응용 프로그램 생성이 완료되면 솔루션 탐색기를 사용해서 다음 파일을 엽니다.  
  
    -   MyProjview.cpp  
  
10. MyProjview.cpp에서 다음과 같이 변경합니다.  
  
    -   `CMyProjView::OnPreparePrinting`에서 함수 내용을 다음 코드로 바꿉니다.  
  
         [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]  
  
     `OnPreparePrinting`은 인쇄 지원을 제공합니다. 이 코드는 기본 인쇄 준비인 `DoPreparePrinting` 대신 사용됩니다.  
  
     액티브 문서 포함은 향상된 인쇄 체계를 제공합니다.  
  
    -   현재 문서를 먼저 호출 해당 `IPrint` 인터페이스를 인쇄 하도록 지시 합니다. 이 컨테이너를 프린터 포함된 된 항목의 이미지를 렌더링 해야 하는 이전 OLE 포함 다릅니다 `CDC` 개체입니다.  
  
    -   실패할 경우 알려 통해 자신을 인쇄 하는 포함 된 항목의 `IOleCommandTarget` 인터페이스  
  
    -   실패하면 항목을 직접 렌더링합니다.  
  
     정적 멤버 함수 `COleDocObjectItem::OnPrint` 및 `COleDocObjectItem::OnPreparePrinting`은 이전 코드에 구현된 대로 향상된 이 인쇄 체계를 처리합니다.  
  
11. 사용자의 고유 구현을 추가하고 응용 프로그램을 빌드합니다.  
  
## <a name="see-also"></a>참고 항목  
 [활성 문서 포함](../mfc/active-document-containment.md)

