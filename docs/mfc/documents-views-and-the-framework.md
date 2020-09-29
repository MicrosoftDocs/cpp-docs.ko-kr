---
title: 문서, 뷰 및 MFC (Microsoft Foundation Class) 라이브러리 프레임 워크
description: MFC (Microsoft Foundation Class) 라이브러리의 문서 및 뷰에 대 한 설명입니다.
ms.date: 09/25/2020
helpviewer_keywords:
- document templates [MFC], template objects
- applications [MFC]
- MFC, application framework
- application objects [MFC], relation to other MFC objects
- documents [MFC]
- MFC, documents
- document objects [MFC], in relation to other MFC objects
- view objects [MFC], relation to other MFC objects
- MFC, views
- document/view architecture [MFC], about document/view architecture
- objects [MFC], MFC applications
- MFC object relationships
- thread objects [MFC]
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
ms.openlocfilehash: 41e145224e512b95d8674109f6ed3dcee39fffb1
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414102"
---
# <a name="documents-views-and-the-framework"></a>문서, 뷰 및 프레임워크

MFC 프레임 워크의 핵심은 문서 및 뷰의 개념입니다. 문서는 사용자가 편집 세션에서 상호 작용 하는 데이터 개체입니다. **파일** 메뉴에서 **새로 만들기** 또는 **열기** 명령으로 생성 되며 일반적으로 파일에 저장 됩니다. 클래스에서 파생 된 표준 MFC 문서 `CDocument` 는 활성 문서와 OLE 복합 문서와 다릅니다. 뷰는 사용자가 문서와 상호 작용 하는 데 사용할 수 있는 창 개체입니다.

실행 중인 응용 프로그램의 주요 개체는 다음과 같습니다.

- Thread 개체

   응용 프로그램이 별도의 실행 스레드를 만드는 경우 (예: 백그라운드에서 계산을 수행 하는 경우)에서 파생 된 클래스를 사용 [`CWinThread`](reference/cwinthread-class.md) 합니다. [`CWinApp`](reference/cwinapp-class.md) 자체는에서 파생 되며 `CWinThread` 응용 프로그램의 기본 실행 스레드 (또는 기본 프로세스)를 나타냅니다. 보조 스레드에서 MFC를 사용할 수도 있습니다.

- 응용 프로그램 개체

   응용 프로그램 클래스 (에서 파생 [`CWinApp`](reference/cwinapp-class.md) )는 위의 모든 개체를 제어 하 고 초기화 및 정리와 같은 응용 프로그램 동작을 지정 합니다. 응용 프로그램의 유일한 응용 프로그램 개체는 응용 프로그램이 지 원하는 모든 문서 유형에 대 한 문서 템플릿을 만들고 관리 합니다.

- 문서 템플릿

   문서 템플릿은 문서, 뷰 및 프레임 창의 생성을 오케스트레이션 합니다. 클래스에서 파생 된 특정 문서 템플릿 클래스는 [`CDocTemplate`](reference/cdoctemplate-class.md) 한 형식의 모든 열린 문서를 만들고 관리 합니다. 둘 이상의 문서 유형을 지 원하는 응용 프로그램에는 여러 문서 템플릿이 있습니다. SDI 응용 프로그램용 [Csingledoctemplate](reference/csingledoctemplate-class.md) 클래스를 사용 하거나 [`CMultiDocTemplate`](reference/cmultidoctemplate-class.md) MDI 응용 프로그램에 클래스를 사용 합니다.

- 프레임 창

   뷰는 "문서 프레임 창" 안에 표시 됩니다. SDI 응용 프로그램에서 문서 프레임 창은 응용 프로그램의 "주 프레임 창" 이기도 합니다. MDI 응용 프로그램에서 문서 창은 주 프레임 창 안에 표시 되는 자식 창입니다. 파생 된 주 프레임 창 클래스는 뷰를 포함 하는 프레임 창의 스타일 및 기타 특성을 지정 합니다. 프레임 창을 사용자 지정 해야 하는 경우에서 파생 [`CFrameWnd`](reference/cframewnd-class.md) 하 여 SDI 응용 프로그램의 문서 프레임 창을 사용자 지정 합니다. 에서 파생 [`CMDIFrameWnd`](reference/cmdiframewnd-class.md) 하 여 MDI 응용 프로그램의 주 프레임 창을 사용자 지정 합니다. 또한에서 클래스를 파생 시켜 [`CMDIChildWnd`](reference/cmdichildwnd-class.md) 응용 프로그램에서 지 원하는 각 고유 종류의 MDI 문서 프레임 창을 사용자 지정 합니다.

- 문서 또는 문서입니다.

   문서 클래스 (에서 파생 [`CDocument`](reference/cdocument-class.md) )는 응용 프로그램의 데이터를 지정 합니다.

   응용 프로그램에서 OLE 기능을 원하는 경우 [`COleDocument`](reference/coledocument-class.md) 필요한 기능 유형에 따라 또는 해당 파생 클래스 중 하나에서 문서 클래스를 파생 시킵니다.

- 뷰나 뷰입니다.

   에서 파생 된 뷰 클래스는 [`CView`](reference/cview-class.md) 사용자의 "데이터 창"입니다. View 클래스는 사용자가 문서의 데이터를 확인 하 고 상호 작용 하는 방법을 제어 합니다. 경우에 따라 문서에 데이터의 여러 뷰가 포함 되도록 할 수 있습니다.

   스크롤이 필요한 경우에서 파생 [`CScrollView`](reference/cscrollview-class.md) 합니다. 보기에 대화 상자 템플릿 리소스에 배치 된 사용자 인터페이스가 있는 경우에서 파생 [`CFormView`](reference/cformview-class.md) 합니다. 단순 텍스트 데이터의 경우를 사용 하거나에서 파생 [`CEditView`](reference/ceditview-class.md) 합니다. 데이터 입력 프로그램과 같은 폼 기반 데이터 액세스 응용 프로그램의 경우 [`CRecordView`](reference/crecordview-class.md) (ODBC의 경우)에서 파생 됩니다. 클래스, 및도 사용할 수 있습니다 [`CTreeView`](reference/ctreeview-class.md) [`CListView`](reference/clistview-class.md) [`CRichEditView`](reference/cricheditview-class.md) .

실행 중인 응용 프로그램에서 이러한 개체는 사용자 작업에 협조적으로 응답 하 고 명령 및 기타 메시지를 사용 하 여 함께 바인딩합니다. 단일 응용 프로그램 개체는 하나 이상의 문서 템플릿을 관리 합니다. 각 문서 템플릿은 응용 프로그램이 SDI 또는 MDI 인지에 따라 하나 이상의 문서를 만들고 관리 합니다. 사용자는 프레임 창 안에 포함 된 뷰를 통해 문서를 보고 조작 합니다. 다음 그림에서는 SDI 응용 프로그램에 대 한 이러한 개체 간의 관계를 보여 줍니다.

![실행 중인 SDI 응용 프로그램의 개체](../mfc/media/vc386v1.gif "실행 중인 SDI 응용 프로그램 개체")\
실행 중인 SDI 애플리케이션의 개체

이 문서의 나머지 부분에서는 프레임 워크 도구, MFC 응용 프로그램 마법사 및 리소스 편집기가 이러한 개체를 만들고 함께 작동 하는 방법과 프로그래밍에서 이러한 개체를 사용 하는 방법에 대해 설명 합니다. 문서, 뷰 및 프레임 창은 [창 개체](window-objects.md) 및 [문서/뷰 아키텍처](document-view-architecture.md)에서 더 자세히 설명 합니다.

## <a name="see-also"></a>참고 항목

[클래스를 사용 하 여 Windows 용 응용 프로그램 작성](using-the-classes-to-write-applications-for-windows.md)
