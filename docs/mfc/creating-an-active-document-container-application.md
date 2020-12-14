---
description: '자세한 정보: 액티브 문서 컨테이너 응용 프로그램 만들기'
title: 액티브 문서 컨테이너 애플리케이션 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
ms.openlocfilehash: 9bf00a73e7520cde45d4e43ae79813896d4c1129
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309994"
---
# <a name="creating-an-active-document-container-application"></a>액티브 문서 컨테이너 애플리케이션 만들기

액티브 문서 컨테이너 애플리케이션을 만드는 가장 간단하고 가장 권장되는 방법은 MFC 애플리케이션 마법사를 사용해서 MFC EXE 컨테이너 애플리케이션을 만들고 액티브 문서 포함을 지원하도록 애플리케이션을 수정하는 방법입니다.

#### <a name="to-create-an-active-document-container-application"></a>액티브 문서 컨테이너 애플리케이션을 만들려면

1. **파일** 메뉴의 **새** 하위 메뉴에서 **프로젝트** 를 클릭 합니다.

1. 왼쪽 창에서 **Visual C++** 프로젝트 형식을 클릭 합니다.

1. 오른쪽 창에서 **MFC 응용 프로그램** 을 선택 합니다.

1. 프로젝트 이름을 *Myproj* 로 선택 하 고 **확인** 을 클릭 합니다.

1. **복합 문서 지원** 페이지를 선택 합니다.

1. **컨테이너** 또는 **컨테이너/전체 서버** 옵션을 선택 합니다.

1. **액티브 문서 컨테이너** 확인란을 선택 합니다.

1. **Finish** 를 클릭합니다.

1. MFC 애플리케이션 마법사에서 애플리케이션 생성이 완료되면 솔루션 탐색기를 사용해서 다음 파일을 엽니다.

   - *MyProjview.cpp*

1. *MyProjview* 에서 다음과 같이 변경 합니다.

   - `CMyProjView::OnPreparePrinting`에서 함수 내용을 다음 코드로 바꿉니다.

     [!code-cpp[NVC_MFCDocView#56](codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting`은 인쇄 지원을 제공합니다. 이 코드는 기본 인쇄 준비인 `DoPreparePrinting` 대신 사용됩니다.

   액티브 문서 포함은 향상된 인쇄 체계를 제공합니다.

   - 먼저 인터페이스를 통해 활성 문서를 호출 `IPrint` 하 고 자신을 인쇄 하도록 지시할 수 있습니다. 이는 컨테이너에서 프린터 개체에 포함 된 항목의 이미지를 렌더링 해야 하는 이전 OLE 포함과는 다릅니다 `CDC` .

   - 이 작업이 실패 하면 포함 된 항목에 인터페이스를 통해 자체 인쇄를 지시 합니다. `IOleCommandTarget`

   - 실패하면 항목을 직접 렌더링합니다.

   정적 멤버 함수 `COleDocObjectItem::OnPrint` 및 `COleDocObjectItem::OnPreparePrinting`은 이전 코드에 구현된 대로 향상된 이 인쇄 체계를 처리합니다.

1. 사용자의 고유 구현을 추가하고 애플리케이션을 빌드합니다.

## <a name="see-also"></a>참고 항목

[액티브 문서 포함](active-document-containment.md)
