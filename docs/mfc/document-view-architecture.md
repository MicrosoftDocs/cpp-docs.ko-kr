---
description: '자세히 알아보기: 문서/뷰 아키텍처'
title: Document-View 아키텍처
ms.date: 11/19/2018
helpviewer_keywords:
- CView class [MFC], view architecture
- CDocument class [MFC]
- MFC, views
- views [MFC], MFC document/view model
- document objects [MFC]
- document objects [MFC], MFC document/view model
- MFC, documents
- documents [MFC], MFC document/view model
- document objects [MFC], document/view architecture
ms.assetid: 6127768a-553f-462a-b01b-a5ee6068c81e
ms.openlocfilehash: ef6746a77a3f8a482c347d61685fccad3e6b4dfb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339724"
---
# <a name="documentview-architecture"></a>문서/뷰 아키텍처

기본적으로 MFC 응용 프로그램 마법사는 문서 클래스와 뷰 클래스로 응용 프로그램 구조를 만듭니다. MFC는 데이터 관리를 이러한 두 클래스로 분리 합니다. 문서는 데이터를 저장 하 고 데이터 인쇄를 관리 하며 데이터의 여러 뷰를 업데이트 하는 것을 조정 합니다. 뷰는 데이터를 표시 하 고 선택 및 편집을 포함 하 여 사용자의 상호 작용을 관리 합니다.

이 모델에서 MFC 문서 개체는 데이터를 읽고 영구 저장소에 씁니다. 문서는 데이터베이스에 있는 등의 데이터에 대 한 인터페이스를 제공할 수도 있습니다. 별도의 뷰 개체는 창의 데이터를 사용자 선택 및 편집으로 렌더링 하 여 데이터 표시를 관리 합니다. 뷰는 문서에서 표시 데이터를 가져오고 데이터 변경 내용을 문서에 다시 전달 합니다.

문서/뷰 분리를 쉽게 무시 하거나 무시할 수 있지만 대부분의 경우이 모델을 따라야 하는 중요 한 이유가 있습니다. 가장 좋은 방법 중 하나는 스프레드시트 및 차트 뷰와 같은 문서에 대 한 여러 뷰가 필요한 경우입니다. 문서/뷰 모델을 사용 하면 별도의 뷰 개체가 데이터의 각 뷰를 나타낼 수 있지만 계산 엔진과 같은 모든 뷰에 공통 된 코드는 문서에 상주할 수 있습니다. 또한이 문서에서는 데이터가 변경 될 때마다 모든 보기를 업데이트 하는 작업을 수행 합니다.

MFC 문서/뷰 아키텍처를 사용 하면 여러 뷰, 여러 문서 형식, 분할자 창 및 기타 중요 한 사용자 인터페이스 기능을 쉽게 지원할 수 있습니다.

사용자와 프로그래머 모두에 게 표시 되는 MFC 프레임 워크의 부분은 문서와 뷰입니다. 프레임 워크를 사용 하 여 응용 프로그램을 개발 하는 작업의 대부분은 문서 및 뷰 클래스를 작성 합니다. 이 문서 제품군은 다음을 설명 합니다.

- 문서와 보기의 용도 및 프레임 워크에서 상호 작용 하는 방법입니다.

- 구현 하기 위해 수행 해야 하는 작업입니다.

문서/보기의 핵심은 다음과 같은 네 가지 주요 클래스입니다.

[CDocument](reference/cdocument-class.md) (또는 [coledocument](reference/coledocument-class.md)) 클래스는 프로그램의 데이터를 저장 하거나 제어 하는 데 사용 되는 개체를 지원 하 고 프로그래머 정의 문서 클래스에 대 한 기본 기능을 제공 합니다. 문서는 일반적으로 파일 메뉴의 열기 명령을 사용 하 여 사용자가 여는 데이터의 단위를 나타내며 파일 메뉴의 저장 명령을 사용 하 여 저장 합니다.

[CView](reference/cview-class.md) (또는 여러 파생 클래스 중 하나)는 프로그래머 정의 뷰 클래스에 대 한 기본 기능을 제공 합니다. 뷰는 문서에 첨부 되 고 문서와 사용자 간의 중개자 역할을 합니다. 뷰에서 문서 이미지를 화면에 렌더링 하 고 사용자 입력을 문서에 대 한 작업으로 해석 합니다. 또한 보기는 인쇄 및 인쇄 미리 보기에 대 한 이미지를 렌더링 합니다.

[CFrameWnd](reference/cframewnd-class.md) (또는 그 변형 중 하나)는 하나 이상의 문서 보기 주위에 프레임을 제공 하는 개체를 지원 합니다.

[Cdoctemplate](reference/cdoctemplate-class.md) (또는 [Csingledoctemplate](reference/csingledoctemplate-class.md) 또는 [cmultidoctemplate](reference/cmultidoctemplate-class.md))은 지정 된 형식의 기존 문서를 하나 이상 조정 하 고 해당 형식에 대 한 올바른 문서, 뷰 및 프레임 창 개체를 만드는 것을 관리 하는 개체를 지원 합니다.

다음 그림에서는 문서와 뷰 간의 관계를 보여 줍니다.

![뷰는 표시되는 문서 중 일부임](../mfc/media/vc379n1.gif "뷰는 표시되는 문서 중 일부임") <br/>
문서 및 보기

클래스 라이브러리의 문서/뷰 구현은 데이터를 표시 및 데이터에 대 한 사용자 작업에서 분리 합니다. 데이터의 모든 변경 내용은 document 클래스를 통해 관리 됩니다. 뷰는이 인터페이스를 호출 하 여 데이터에 액세스 하 고 업데이트 합니다.

문서, 연결 된 뷰 및 뷰를 프레임 하는 프레임 창은 문서 템플릿에서 생성 됩니다. 문서 템플릿은 한 문서 종류의 모든 문서를 만들고 관리 하는 일을 담당 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [문서/뷰 아키텍처의 세로](a-portrait-of-the-document-view-architecture.md)

- [문서/뷰 아키텍처의 이점](advantages-of-the-document-view-architecture.md)

- [응용 프로그램 마법사에서 만든 문서 및 뷰 클래스](document-and-view-classes-created-by-the-mfc-application-wizard.md)

- [문서/뷰 아키텍처에 대 한 대안](alternatives-to-the-document-view-architecture.md)

- [단일 문서에 여러 뷰 추가](adding-multiple-views-to-a-single-document.md)

- [문서 사용](using-documents.md)

- [뷰 사용](using-views.md)

- [여러 문서 형식, 뷰 및 프레임 창](multiple-document-types-views-and-frame-windows.md)

- [문서 및 뷰 초기화 및 정리](initializing-and-cleaning-up-documents-and-views.md)

- [문서 & 뷰 클래스에 대 한 고유한 추가를 초기화 합니다.](creating-new-documents-windows-and-views.md)

- [문서 및 뷰를 이용한 데이터베이스 클래스 사용](../data/mfc-using-database-classes-with-documents-and-views.md)

- [문서 및 뷰를 이용하지 않는 데이터베이스 클래스 사용](../data/mfc-using-database-classes-without-documents-and-views.md)

- [샘플](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>참고 항목

[사용자 인터페이스 요소](user-interface-elements-mfc.md)<br/>
[Windows](windows.md)<br/>
[프레임 창](frame-windows.md)<br/>
[문서 템플릿 및 문서/뷰 만들기 프로세스](document-templates-and-the-document-view-creation-process.md)<br/>
[문서/뷰 만들기](document-view-creation.md)<br/>
[새 문서, 창 및 뷰 만들기](creating-new-documents-windows-and-views.md)
