---
description: '자세히 알아보기: 대화 상자 클래스'
title: 대화 상자 클래스
ms.date: 11/04/2016
f1_keywords:
- vc.classes.dialog
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
ms.openlocfilehash: 5c178bc6895e338bf4b2876be5233c1b80007abc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261556"
---
# <a name="dialog-box-classes"></a>대화 상자 클래스

클래스 `CDialog` 와 해당 파생 클래스는 대화 상자 기능을 캡슐화 합니다. 대화 상자는 특별 한 종류의 창이 기 때문에 `CDialog` 는에서 파생 됩니다 `CWnd` . 에서 대화 상자 클래스를 파생 시키거나 `CDialog` 파일 열기/저장, 인쇄, 글꼴 또는 색 선택, 검색 및 바꾸기 작업 시작, 다양 한 OLE 관련 작업 수행 등 표준 대화 상자에 대 한 일반 대화 상자 클래스 중 하나를 사용 합니다.

[CDialog](reference/cdialog-class.md)<br/>
모달 및 모덜리스의 모든 대화 상자에 대 한 기본 클래스입니다.

[CDataExchange](reference/cdataexchange-class.md)<br/>
대화 상자에 대 한 데이터 교환 및 유효성 검사 정보를 제공 합니다.

## <a name="common-dialogs"></a>일반 대화 상자

이러한 대화 상자 클래스는 Windows 공용 대화 상자를 캡슐화 합니다. 복잡 한 대화 상자를 사용 하기 쉬운 구현을 제공 합니다.

[CCommonDialog](reference/ccommondialog-class.md)<br/>
모든 일반 대화 상자에 대 한 기본 클래스입니다.

[CFileDialog](reference/cfiledialog-class.md)<br/>
파일을 열거나 저장할 때 사용할 표준 대화 상자를 제공 합니다.

[CColorDialog](reference/ccolordialog-class.md)<br/>
색을 선택할 때 표준 대화 상자를 제공 합니다.

[CFontDialog](reference/cfontdialog-class.md)<br/>
글꼴을 선택 하는 표준 대화 상자를 제공 합니다.

[CFindReplaceDialog](reference/cfindreplacedialog-class.md)<br/>
검색 및 바꾸기 작업을 위한 표준 대화 상자를 제공 합니다.

[CPrintDialog](reference/cprintdialog-class.md)<br/>
파일 인쇄를 위한 표준 대화 상자를 제공 합니다.

[CPrintDialogEx](reference/cprintdialogex-class.md)<br/>
Windows 인쇄 속성 시트를 제공 합니다.

[CPageSetupDialog](reference/cpagesetupdialog-class.md)<br/>
인쇄 여백을 설정 및 수정 하기 위한 추가 지원과 함께 Windows 공용 페이지 설정 대화 상자에서 제공 하는 서비스를 캡슐화 합니다.

## <a name="ole-common-dialogs"></a>OLE 일반 대화 상자

OLE는 창에 몇 가지 일반적인 대화 상자를 추가 합니다. 이러한 클래스는 OLE 일반 대화 상자를 캡슐화 합니다.

[COleDialog](reference/coledialog-class.md)<br/>
프레임 워크에서 모든 OLE 대화 상자에 대 한 일반적인 구현을 포함 하는 데 사용 됩니다. 사용자 인터페이스 범주의 모든 대화 상자 클래스는이 기본 클래스에서 파생 됩니다. `COleDialog` 직접 사용할 수 없습니다.

[COleInsertDialog](reference/coleinsertdialog-class.md)<br/>
새 OLE 연결 된 항목 또는 포함 된 항목을 삽입 하기 위한 표준 사용자 인터페이스인 개체 삽입 대화 상자를 표시 합니다.

[COlePasteSpecialDialog](reference/colepastespecialdialog-class.md)<br/>
붙여넣기 특수 편집 명령을 구현 하기 위한 표준 사용자 인터페이스인 붙여넣기 특수 대화 상자를 표시 합니다.

[COleLinksDialog](reference/colelinksdialog-class.md)<br/>
연결 된 항목에 대 한 정보를 수정 하기 위한 표준 사용자 인터페이스인 링크 편집 대화 상자를 표시 합니다.

[COleChangeIconDialog](reference/colechangeicondialog-class.md)<br/>
OLE 포함 또는 연결 된 항목과 연결 된 아이콘을 변경 하기 위한 표준 사용자 인터페이스인 아이콘 변경 대화 상자를 표시 합니다.

[COleConvertDialog](reference/coleconvertdialog-class.md)<br/>
OLE 항목을 한 형식에서 다른 형식으로 변환 하기 위한 표준 사용자 인터페이스인 변환 대화 상자를 표시 합니다.

[COlePropertiesDialog](reference/colepropertiesdialog-class.md)<br/>
Windows 공용 OLE 속성 대화 상자를 캡슐화 합니다. 일반적인 OLE 속성 대화 상자를 사용 하면 Windows 표준과 일관 된 방식으로 OLE 문서 항목의 속성을 쉽게 표시 하 고 수정할 수 있습니다.

[COleUpdateDialog](reference/coleupdatedialog-class.md)<br/>
문서의 모든 링크를 업데이트 하기 위한 표준 사용자 인터페이스인 업데이트 대화 상자를 표시 합니다. 이 대화 상자에는 업데이트 절차를 완료 하는 방법을 나타내는 진행률 표시기가 있습니다.

[COleChangeSourceDialog](reference/colechangesourcedialog-class.md)<br/>
링크의 대상 또는 소스를 변경 하기 위한 표준 사용자 인터페이스인 소스 변경 대화 상자를 표시 합니다.

[COleBusyDialog](reference/colebusydialog-class.md)<br/>
사용 중인 응용 프로그램에 대 한 호출을 처리 하기 위한 표준 사용자 인터페이스인 서버 사용 중 및 서버 응답 없음 대화 상자를 표시 합니다. 일반적으로 [COleMessageFilter](reference/colemessagefilter-class.md) 구현에 의해 자동으로 표시 됩니다.

## <a name="property-sheet-classes"></a>속성 시트 클래스

속성 시트 클래스를 사용 하면 응용 프로그램에서 속성 시트 (탭 대화 상자 라고도 함)를 사용할 수 있습니다. 속성 시트는 단일 대화 상자에서 많은 수의 컨트롤을 구성 하는 효율적인 방법입니다.

[CPropertyPage](reference/cpropertypage-class.md)<br/>
속성 시트 내의 개별 페이지를 제공 합니다. `CPropertyPage`속성 시트에 추가할 각 페이지에 대해에서 클래스를 파생 시킵니다.

[CPropertySheet](reference/cpropertysheet-class.md)<br/>
여러 속성 페이지에 대 한 프레임을 제공 합니다. 에서 속성 시트 클래스를 파생 시켜 `CPropertySheet` 속성 시트를 빠르게 구현할 수 있습니다.

[COlePropertyPage](reference/colepropertypage-class.md)<br/>
대화 상자와 유사한 그래픽 인터페이스의 OLE 컨트롤 속성을 표시 합니다.

## <a name="html-based-dialog-classes"></a>HTML 기반 대화 상자 클래스

[CDHtmlDialog](reference/cdhtmldialog-class.md)<br/>
대화 상자 리소스가 아닌 HTML로 사용자 인터페이스를 구현 하는 대화 상자를 만드는 데 사용 됩니다.

[CMultiPageDHtmlDialog](reference/cmultipagedhtmldialog-class.md)<br/>
여러 HTML 페이지를 순차적으로 표시 하 고 각 페이지의 이벤트를 처리 합니다.

## <a name="related-classes"></a>관련 클래스

이러한 클래스는 사용자 당 대화 상자는 아니지만 대화 상자 템플릿을 사용 하 고 대화 상자에서 많은 동작을 포함 합니다.

[CDialogBar](reference/cdialogbar-class.md)<br/>
대화 상자 템플릿을 기반으로 하는 컨트롤 막대입니다.

[CFormView](reference/cformview-class.md)<br/>
대화 상자 템플릿에서 레이아웃을 정의 하는 스크롤 뷰입니다. `CFormView`대화 상자 템플릿을 기반으로 사용자 인터페이스를 구현 하려면에서 클래스를 파생 시킵니다.

[CDaoRecordView](reference/cdaorecordview-class.md)<br/>
DAO (Data Access Object) 레코드 집합 개체에 직접 연결 되는 폼 뷰를 제공 합니다. 모든 폼 보기와 마찬가지로는 `CDaoRecordView` 대화 상자 템플릿을 기반으로 합니다.

[CRecordView](reference/crecordview-class.md)<br/>
ODBC (Open Database Connectivity) 레코드 집합 개체에 직접 연결 된 폼 뷰를 제공 합니다. 모든 폼 보기와 마찬가지로는 `CRecordView` 대화 상자 템플릿을 기반으로 합니다.

[CPrintInfo](reference/cprintinfo-structure.md)<br/>
인쇄 또는 인쇄 미리 보기 작업에 대 한 정보를 포함 하는 구조체입니다. [CView](reference/cview-class.md)의 인쇄 아키텍처에 사용 됩니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
