---
description: '자세히 알아보기: 클래스를 사용 하 여 Windows 용 응용 프로그램 작성'
title: 클래스를 사용하여 Windows 애플리케이션 작성
ms.date: 11/04/2016
helpviewer_keywords:
- Windows applications [MFC], MFC application framework
- MFC, application development
- applications [OLE], MFC application framework
- MFC ActiveX controls [MFC], creating
- OLE applications [MFC], MFC application framework
- database applications [MFC], creating
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
ms.openlocfilehash: b94155b565872b614efa291699cecbaf4770fdaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322714"
---
# <a name="using-the-classes-to-write-applications-for-windows"></a>클래스를 사용하여 Windows 애플리케이션 작성

MFC (Microsoft Foundation Class) 라이브러리의 클래스를 함께 사용 하면 Windows 운영 체제에 대 한 응용 프로그램을 빌드하는 "응용 프로그램 프레임 워크"를 구성 합니다. 매우 일반적인 수준에서 프레임 워크는 응용 프로그램의 기본 구조를 정의 하 고 기본에 배치할 수 있는 표준 사용자 인터페이스 구현을 제공 합니다. 프로그래머의 작업은 응용 프로그램에 특정 한 것과 같은 기초를 채우는 것입니다. MFC 응용 프로그램 마법사를 사용 하 여 매우 철저 한 시작 응용 프로그램에 대 한 파일을 만들 수 있습니다. Microsoft Visual C++ 리소스 편집기를 사용 하 여 사용자 인터페이스 요소를 시각적으로 디자인 하 고, 이러한 요소를 코드에 연결 하는 명령을 클래스 뷰 하 고, 클래스 라이브러리를 사용 하 여 응용 프로그램별 논리를 구현 합니다.

버전 3.0 이상 MFC 프레임 워크는 Microsoft Windows 95 이상 및 Windows NT 버전 3.51 이상을 포함 하 여 Win32 플랫폼에 대 한 프로그래밍을 지원 합니다. MFC Win32 지원에는 다중 스레딩을 포함 됩니다. 16 비트 프로그래밍을 수행 해야 하는 경우 버전 1.5 *x* 를 사용 합니다.

이 문서의 패밀리는 응용 프로그램 프레임 워크에 대 한 광범위 한 개요를 제공 합니다. 또한 응용 프로그램을 구성 하는 주요 개체와 응용 프로그램을 만드는 방법을 살펴봅니다. 이러한 문서에서 설명 하는 항목 중 하나는 다음과 같습니다.

- [프레임 워크](../mfc/framework-mfc.md)입니다.

- 프레임 워크를 [기반](../mfc/building-on-the-framework.md)으로 하는 방법에 설명 된 대로 프레임 워크와 코드 간의 인력 분할.

- 응용 프로그램 수준 기능을 캡슐화 하는 [응용 프로그램 클래스](../mfc/cwinapp-the-application-class.md)입니다.

- [문서 템플릿이](../mfc/document-templates-and-the-document-view-creation-process.md) 문서와 관련 보기 및 프레임 창을 만들고 관리 하는 방법입니다.

- 클래스 [CWnd](../mfc/window-objects.md), 모든 창의 루트 기본 클래스입니다.

- 펜 및 브러시와 같은 [그래픽 개체](../mfc/graphic-objects.md)입니다.

프레임 워크의 다른 부분은 다음과 같습니다.

- [창 개체: 개요](../mfc/window-objects.md)

- [메시지 처리 및 매핑](../mfc/message-handling-and-mapping.md)

- [MFC의 루트 기본 클래스인 CObject](../mfc/using-cobject.md)

- [문서/뷰 아키텍처](../mfc/document-view-architecture.md)

- [대화 상자](../mfc/dialog-boxes.md)

- [컨트롤](../mfc/controls-mfc.md)

- [컨트롤 막대](../mfc/control-bars.md)

- [OLE](../mfc/ole-in-mfc.md)

- [메모리 관리](../mfc/memory-management.md)

   MFC는 Windows 운영 체제에 대 한 응용 프로그램을 작성 하는 이점을 제공 하는 것 외에도 OLE 연결 및 포함 기술을 사용 하는 응용 프로그램을 훨씬 더 쉽게 작성할 수 있도록 합니다. 응용 프로그램을 OLE 비주얼 편집 컨테이너, OLE 비주얼 편집 서버 또는 둘 다로 만들 수 있으며, 다른 응용 프로그램에서 응용 프로그램의 개체를 사용 하거나 원격으로 구동 하도록 자동화를 추가할 수 있습니다.

- [MFC ActiveX 컨트롤](../mfc/mfc-activex-controls.md)

   이제 CDK (OLE 컨트롤 개발 키트)가 프레임 워크와 완전히 통합 되었습니다. 이 문서 제품군에서는 MFC로 ActiveX 컨트롤을 개발 하는 방법에 대 한 개요를 제공 합니다. ActiveX 컨트롤은 이전에 OLE 컨트롤 이라고 했습니다.

- [데이터베이스 프로그래밍](../data/data-access-programming-mfc-atl.md)

   또한 MFC는 데이터 액세스 응용 프로그램 작성을 간소화 하는 두 가지 데이터베이스 클래스 집합을 제공 합니다. ODBC 데이터베이스 클래스를 사용 하 여 ODBC (Open Database Connectivity) 드라이버를 통해 데이터베이스에 연결 하 고, 테이블에서 레코드를 선택 하 고, 화면 형식으로 레코드 정보를 표시할 수 있습니다. DAO (Data Access Object) 클래스를 사용 하 여 Microsoft Jet 데이터베이스 엔진 또는 ODBC 데이터 원본 등의 외부 (비 Jet) 데이터 원본을 통해 데이터베이스 작업을 수행할 수 있습니다.

   또한 MFC는 유니코드 및 MBCS (멀티 바이트 문자 집합), 특히 DBCS (더블 바이트 문자 집합)를 사용 하는 응용 프로그램을 작성할 수 있도록 완전히 활성화 됩니다.

MFC 설명서에 대 한 일반적인 가이드는 [일반 Mfc 항목](../mfc/general-mfc-topics.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[일반 MFC 항목](../mfc/general-mfc-topics.md)
