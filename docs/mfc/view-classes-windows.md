---
description: '자세히 알아보기: 클래스 보기 (Windows)'
title: 뷰 클래스(Windows)
ms.date: 09/17/2019
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
ms.openlocfilehash: f7ad1fb97952468fd2f2bde9560b1a4c18252332
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143106"
---
# <a name="view-classes-windows"></a>뷰 클래스(Windows)

`CView` 및 해당 파생 클래스는 프레임 창의 클라이언트 영역을 나타내는 자식 창입니다. 보기는 데이터를 표시 하 고 문서에 대 한 입력을 허용 합니다.

뷰 클래스는 문서 클래스 및 문서 템플릿 개체를 사용 하는 프레임 창 클래스와 연결 됩니다.

[CView](../mfc/reference/cview-class.md)<br/>
문서 데이터의 응용 프로그램별 보기에 대 한 기본 클래스입니다. 보기 데이터를 표시 하 고 사용자 입력을 수락 하 여 데이터를 편집 하거나 선택 합니다. 에서 뷰 클래스 또는 클래스를 파생 시킵니다 `CView` .

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
스크롤 기능이 있는 뷰의 기본 클래스입니다. 자동 스크롤을 위해에서 뷰 클래스를 파생 `CScrollView` 합니다.

## <a name="form-and-record-views"></a>폼 및 레코드 뷰

또한 폼 보기는 스크롤 뷰입니다. 대화 상자 템플릿을 기반으로 합니다.

레코드 뷰는 폼 보기에서 파생 됩니다. 대화 상자 템플릿 외에도 데이터베이스에도 연결 되어 있습니다.

[CFormView](../mfc/reference/cformview-class.md)<br/>
대화 상자 템플릿에서 레이아웃을 정의 하는 스크롤 뷰입니다. `CFormView`대화 상자 템플릿을 기반으로 사용자 인터페이스를 구현 하려면에서 클래스를 파생 시킵니다.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
DAO (Data Access Object) 레코드 집합 개체에 직접 연결 되는 폼 뷰를 제공 합니다. 모든 폼 보기와 마찬가지로는 `CDaoRecordView` 대화 상자 템플릿을 기반으로 합니다. DAO는 Access 데이터베이스에 사용 되며 Office 2013을 통해 지원 됩니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
ODBC (Open Database Connectivity) 레코드 집합 개체에 직접 연결 된 폼 뷰를 제공 합니다. 모든 폼 보기와 마찬가지로는 `CRecordView` 대화 상자 템플릿을 기반으로 합니다.

[CHtmlEditView](../mfc/reference/chtmleditview-class.md)<br/>
WebBrowser HTML 편집 플랫폼의 기능을 제공 하는 폼 뷰입니다.

## <a name="control-views"></a>컨트롤 뷰

컨트롤 뷰는 컨트롤을 뷰로 표시 합니다.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Windows 컨트롤과 연결 된 모든 뷰의 기본 클래스입니다. 컨트롤을 기반으로 하는 뷰는 아래에 설명 되어 있습니다.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Windows 표준 편집 컨트롤을 포함 하는 뷰입니다 ( [CEdit](../mfc/reference/cedit-class.md)참조). 편집 컨트롤은 텍스트 편집, 검색, 바꾸기 및 스크롤 기능을 지원 합니다.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Windows rich edit 컨트롤을 포함 하는 뷰입니다 ( [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)참조). 편집 컨트롤의 기능 외에도 서식 있는 편집 컨트롤은 글꼴, 색, 단락 서식 및 포함 된 OLE 개체를 지원 합니다.

[CListView](../mfc/reference/clistview-class.md)<br/>
Windows 목록 컨트롤을 포함 하는 뷰입니다 ( [CListCtrl](../mfc/reference/clistctrl-class.md)참조). 목록 컨트롤은 각각 아이콘과 레이블로 구성 되는 항목 컬렉션을 파일 탐색기의 오른쪽 창과 비슷한 방식으로 표시 합니다.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Windows 트리 컨트롤을 포함 하는 뷰입니다 ( [CTreeCtrl](../mfc/reference/ctreectrl-class.md)참조). 트리 컨트롤은 파일 탐색기의 왼쪽 창과 비슷한 방식으로 정렬 된 아이콘 및 레이블의 계층 목록을 표시 합니다.

## <a name="related-classes"></a>관련 클래스

`CSplitterWnd` 단일 프레임 창 내에서 여러 뷰를 사용할 수 있습니다. `CPrintDialog` 및는 `CPrintInfo` 보기의 인쇄 및 인쇄 미리 보기 기능을 지원 합니다. `CRichEditDoc` 및 `CRichEditCntrItem` 는와 함께 `CRichEditView` OLE 컨테이너 기능을 구현 하는 데 사용 됩니다.

[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)<br/>
사용자가 여러 창으로 분할할 수 있는 창입니다. 이러한 창은 사용자 또는 고정 크기로 크기를 조정할 수 있습니다.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
파일 인쇄를 위한 표준 대화 상자를 제공 합니다.

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
인쇄 또는 인쇄 미리 보기 작업에 대 한 정보를 포함 하는 구조체입니다. `CView`의 인쇄 아키텍처에 사용 됩니다.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
에 있는 OLE 클라이언트 항목의 목록을 유지 관리 합니다 `CRichEditView` .

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
에 저장 된 OLE 항목에 대 한 클라이언트 쪽 액세스를 제공 `CRichEditView` 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../mfc/class-library-overview.md)
