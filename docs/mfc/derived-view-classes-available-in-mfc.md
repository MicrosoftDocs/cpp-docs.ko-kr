---
description: '자세한 정보: MFC에서 사용할 수 있는 파생 뷰 클래스'
title: MFC에서 사용할 수 있는 파생된 뷰 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: 669fb0f47cc2124fcf45d0eed3666869837f56f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211897"
---
# <a name="derived-view-classes-available-in-mfc"></a>MFC에서 사용할 수 있는 파생된 뷰 클래스

다음 표에서는 MFC의 뷰 클래스와 서로 간의 관계를 보여 줍니다. 뷰 클래스의 기능은 해당 기능이 파생 되는 MFC 뷰 클래스에 따라 다릅니다.

### <a name="view-classes"></a>뷰 클래스

|클래스|설명|
|-----------|-----------------|
|[CView](reference/cview-class.md)|모든 뷰의 기본 클래스입니다.|
|[CCtrlView](reference/cctrlview-class.md)|,, 및의 기본 클래스 `CTreeView` `CListView` `CEditView` `CRichEditView` 입니다. 이러한 클래스를 사용 하면 표시 된 Windows 공용 컨트롤과 함께 문서/뷰 아키텍처를 사용할 수 있습니다.|
|[CEditView](reference/ceditview-class.md)|Windows 편집 상자 컨트롤을 기반으로 하는 간단한 뷰입니다. 텍스트를 입력 하 고 편집할 수 있으며 간단한 텍스트 편집기 응용 프로그램의 기준으로 사용할 수 있습니다. `CRichEditView`을 참조하세요.|
|[CRichEditView](reference/cricheditview-class.md)|[CRichEditCtrl](reference/cricheditctrl-class.md) 개체를 포함 하는 뷰입니다. 이 클래스는와 유사 `CEditView` 하지만와는 `CEditView` 달리 `CRichEditView` 서식 지정 된 텍스트를 처리 합니다.|
|[CListView](reference/clistview-class.md)|[CListCtrl](reference/clistctrl-class.md) 개체를 포함 하는 뷰입니다.|
|[CTreeView](reference/ctreeview-class.md)|Visual C++의 솔루션 탐색기 창과 유사한 뷰에 대 한 [CTreeCtrl](reference/ctreectrl-class.md) 개체를 포함 하는 뷰입니다.|
|[CScrollView](reference/cscrollview-class.md)|, 및의 기본 클래스 `CFormView` `CRecordView` `CDaoRecordView` 입니다. 뷰의 내용 스크롤을 구현 합니다.|
|[CFormView](reference/cformview-class.md)|컨트롤을 포함 하는 형태인 폼 뷰입니다. 폼 기반 응용 프로그램은 이러한 폼 인터페이스를 하나 이상 제공 합니다.|
|[CHtmlView](reference/chtmlview-class.md)|응용 프로그램 사용자가 로컬 파일 시스템과 네트워크의 폴더 뿐 아니라 World Wide Web의 사이트를 검색할 수 있는 웹 브라우저 뷰입니다. 웹 브라우저 보기를 활성 문서 컨테이너로 사용할 수도 있습니다.|
|[CRecordView](reference/crecordview-class.md)|컨트롤에 ODBC 데이터베이스 레코드를 표시 하는 폼 뷰입니다. 프로젝트에서 ODBC 지원을 선택 하는 경우 뷰의 기본 클래스는 `CRecordView` 입니다. 뷰가 개체에 연결 되어 `CRowset` 있습니다.|
|[CDaoRecordView](reference/cdaorecordview-class.md)|컨트롤에 DAO 데이터베이스 레코드를 표시 하는 폼 뷰입니다. 프로젝트에서 DAO 지원을 선택 하는 경우 뷰의 기본 클래스는 `CDaoRecordView` 입니다. 뷰가 개체에 연결 되어 `CDaoRecordset` 있습니다.|
|[COleDBRecordView](reference/coledbrecordview-class.md)|컨트롤에 OLE DB 레코드를 표시 하는 폼 뷰입니다. 프로젝트에서 OLE DB 지원을 선택 하는 경우 뷰의 기본 클래스는 `COleDBRecordView` 입니다. 뷰가 개체에 연결 되어 `CRowset` 있습니다.|

> [!NOTE]
> MFC 버전 4.0 `CEditView` 부터은에서 파생 됩니다 `CCtrlView` .

응용 프로그램에서 이러한 클래스를 사용 하려면 해당 클래스에서 응용 프로그램의 뷰 클래스를 파생 시킵니다. 관련 정보는 [뷰 스크롤 및 크기 조정](scrolling-and-scaling-views.md)을 참조 하세요. 데이터베이스 클래스에 대 한 자세한 내용은 [개요: 데이터베이스 프로그래밍](../data/data-access-programming-mfc-atl.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[뷰 사용](using-views.md)
