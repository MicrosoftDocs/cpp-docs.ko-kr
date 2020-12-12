---
description: '자세한 정보: MFC 응용 프로그램 Explorer-Style 파일 만들기'
title: 파일 탐색기 스타일 MFC 애플리케이션 만들기
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcexplorer.project
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
ms.openlocfilehash: 9419aae58cf34ec70585b952360cb12702424381
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301323"
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>파일 탐색기 스타일 MFC 애플리케이션 만들기

많은 Windows 시스템 응용 프로그램은 파일 탐색기에 대 한 UI (사용자 인터페이스)를 사용 합니다. 예를 들어 파일 탐색기를 시작 하면 클라이언트 영역을 나누는 세로 분할자 막대가 있는 응용 프로그램이 표시 됩니다. 클라이언트 영역의 왼쪽은 탐색 및 검색 기능을 제공 하 고, 클라이언트 영역의 오른쪽에는 왼쪽 창에서 선택 하는 것과 관련 된 세부 정보가 표시 됩니다. 사용자가 왼쪽 창에서 항목을 클릭 하면 응용 프로그램에서 오른쪽 창이 다시 채워집니다. MDI 응용 프로그램에서 **보기** 메뉴의 명령을 사용 하 여 오른쪽 창에 표시 되는 세부 정보의 양을 변경할 수 있습니다. SDI 또는 다중 최상위 문서 응용 프로그램에서 도구 모음 단추를 사용 하 여 세부 정보를 변경할 수 있습니다.

창의 내용은 응용 프로그램에 따라 달라 집니다. 파일 시스템 브라우저의 왼쪽 창에는 디렉터리 또는 컴퓨터 또는 컴퓨터 그룹의 계층 보기가 표시 되 고 오른쪽 창에는 폴더, 개별 파일 또는 컴퓨터 및 세부 정보가 표시 됩니다. 내용이 파일이 아니어도 되는 것은 아닙니다. 전자 메일 메시지, 오류 보고서 또는 데이터베이스의 다른 항목 일 수 있습니다.

마법사는 다음과 같은 클래스를 만듭니다.

- `CLeftView`클래스는 클라이언트 영역의 왼쪽 창을 정의 합니다. 이는 항상 [Ctreeview](../../mfc/reference/ctreeview-class.md)에서 파생 됩니다.

- C *ProjName* View 클래스는 클라이언트 영역의 오른쪽 창을 정의 합니다. 기본적으로이 클래스는 [CListView](../../mfc/reference/clistview-class.md) 에서 파생 되지만 마법사의 [생성 된 클래스](../../mfc/reference/generated-classes-mfc-application-wizard.md) 페이지에서 **기본 클래스** 목록에서 지정 하는 클래스에 따라 다른 유형의 보기가 될 수 있습니다.

생성 된 응용 프로그램에는 SDI (단일 문서 인터페이스), MDI (다중 문서 인터페이스) 또는 다중 최상위 문서 아키텍처가 있을 수 있습니다. 응용 프로그램에서 만드는 각 프레임 창은 [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)를 사용 하 여 세로로 분할 됩니다. 이 응용 프로그램 종류를 코딩 하는 것은 분할자를 사용 하는 일반 MFC 응용 프로그램을 코딩 하는 것과 유사 합니다. 단,이 유형의 응용 프로그램은 각 분할자 창 내에서 별도의 컨트롤 뷰

오른쪽 창에서 기본 목록 뷰를 사용 하는 경우 마법사는 추가 메뉴 선택 항목 (MDI 응용 프로그램에만 해당) 및 도구 모음 단추를 만들어 보기의 스타일을 크게 아이콘, 작은 아이콘, 목록 및 세부 모드로 전환 합니다.

### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>파일 탐색기 스타일 MFC 실행 파일 만들기를 시작 하려면

1. [MFC 응용 프로그램 만들기](../../mfc/reference/creating-an-mfc-application.md)의 지침을 따릅니다.

1. MFC 응용 프로그램 마법사 [응용 프로그램 종류](../../mfc/reference/application-type-mfc-application-wizard.md) 페이지에서 **파일 탐색기** 프로젝트 스타일을 선택 합니다.

1. 마법사의 다른 페이지에서 원하는 다른 옵션을 설정 합니다.

1. **마침** 을 클릭 하 여 기본 응용 프로그램을 생성 합니다.

자세한 내용은 다음을 참조하세요.

- [여러 문서 형식, 뷰 및 프레임 창](../../mfc/multiple-document-types-views-and-frame-windows.md)

- [파생 뷰 클래스](../../mfc/derived-view-classes-available-in-mfc.md)

- [응용 프로그램 디자인 선택](../../mfc/application-design-choices.md)

## <a name="see-also"></a>참고 항목

[MFC 응용 프로그램 마법사](../../mfc/reference/mfc-application-wizard.md)<br/>
[웹 Browser-Style MFC 응용 프로그램 만들기](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)<br/>
[Forms-Based MFC 응용 프로그램 만들기](../../mfc/reference/creating-a-forms-based-mfc-application.md)
