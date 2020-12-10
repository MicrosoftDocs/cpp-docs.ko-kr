---
title: Microsoft Foundation Classes (MFC) 응용 프로그램 아키텍처 클래스
description: MFC (Microsoft Foundation Class) 라이브러리 응용 프로그램 아키텍처 클래스에 대 한 개요입니다.
ms.date: 12/08/2020
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.openlocfilehash: 65aa9707d361c6d014c67c0f9ff1af86e19087de
ms.sourcegitcommit: 754df5278f795f661d4eeb0d4cacc908aa630159
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96933198"
---
# <a name="mfc-application-architecture-classes"></a>MFC 애플리케이션 아키텍처 클래스

이 범주의 MFC (Microsoft Foundation Class library) 클래스는 MFC 응용 프로그램의 아키텍처에 영향을 주지 않습니다. 대부분의 응용 프로그램에 공통적인 기능을 제공 합니다. 응용 프로그램 관련 기능을 추가 하려면 프레임 워크를 입력 합니다. 일반적으로 아키텍처 클래스에서 새 클래스를 파생 시킨 다음 새 멤버를 추가 하거나 기존 멤버 함수를 재정의 하 여이 작업을 수행 합니다.

[응용 프로그램 마법사](reference/mfc-application-wizard.md) 는 다양 한 방식으로 응용 프로그램 프레임 워크를 사용 하는 여러 유형의 응용 프로그램을 생성 합니다. SDI (단일 문서 인터페이스) 및 MDI (다중 문서 인터페이스) 응용 프로그램은 프레임 워크의 문서/뷰 부분을 완전히 활용 합니다. 대화 상자 기반 응용 프로그램, 폼 기반 응용 프로그램 및 Dll과 같은 다른 유형의 응용 프로그램은 일부 문서/뷰 아키텍처 기능만 사용 합니다.

문서/뷰 응용 프로그램에는 문서, 뷰 및 프레임 창의 집합이 하나 이상 포함 되어 있습니다. 문서 템플릿 개체는 각 문서/뷰/프레임 집합의 클래스를 연결 합니다.

MFC 응용 프로그램에서 문서/뷰 아키텍처를 사용할 필요는 없지만 이렇게 하면 여러 가지 이점이 있습니다. MFC OLE 컨테이너 및 서버 지원은 인쇄 및 인쇄 미리 보기를 지 원하는 문서/뷰 아키텍처를 기반으로 합니다.

모든 MFC 응용 프로그램에는 두 개 이상의 개체가 있습니다. 즉,에서 파생 된 응용 프로그램 개체 [`CWinApp`](reference/cwinapp-class.md) 와에서 주로 간접적으로 파생 된 주 창 개체를 정렬 [`CWnd`](reference/cwnd-class.md) 합니다. 주로 주 창은에서 파생 되는, 또는에서 파생 됩니다 [`CFrameWnd`](reference/cframewnd-class.md) [`CMDIFrameWnd`](reference/cmdiframewnd-class.md) [`CDialog`](reference/cdialog-class.md) `CWnd` .

문서/뷰 아키텍처를 사용 하는 응용 프로그램은 추가 개체를 포함 합니다. 주요 개체는 다음과 같습니다.

- 앞에서 설명한 것 처럼 클래스에서 파생 된 응용 프로그램 개체 [`CWinApp`](reference/cwinapp-class.md) 입니다.
- 클래스에서 파생 된 하나 이상의 문서 클래스 개체 [`CDocument`](reference/cdocument-class.md) 입니다. 문서 클래스 개체는 뷰에서 조작 되는 데이터의 내부 표현을 담당 합니다. 데이터 파일에 연결할 수 있습니다.
- 클래스에서 파생 된 하나 이상의 뷰 개체 [`CView`](reference/cview-class.md) 입니다. 각 보기는 문서에 연결 되 고 프레임 창과 연결 된 창입니다. 뷰는 문서 클래스 개체에 포함 된 데이터를 표시 하 고 조작 합니다.

문서/뷰 응용 프로그램에는 프레임 창 (에서 파생 [`CFrameWnd`](reference/cframewnd-class.md) ) 및 문서 템플릿 (에서 파생)도 포함 [`CDocTemplate`](reference/cdoctemplate-class.md) 됩니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)