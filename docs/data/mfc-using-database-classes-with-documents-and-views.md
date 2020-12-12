---
description: '자세히 알아보기: MFC: 문서 및 뷰를 사용 하 여 데이터베이스 클래스 사용'
title: 'MFC: 문서 및 뷰를 이용한 데이터베이스 클래스 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- documents [C++], database applications
- recordsets [C++], documents and views
- CRecordView class, using in database forms
- views [C++], database applications
- forms [C++], database applications
- record views [C++], form-based applications
- document/view architecture [C++], in databases
- database applications [C++], forms
- database classes [C++], MFC
- ODBC recordsets [C++], documents and views
- ODBC [C++], forms
ms.assetid: 83979974-fc63-46ac-b162-e8403a572e2c
ms.openlocfilehash: 9742e180c8acab7e882cd31a94afec935a5ce21a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170869"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: 문서 및 뷰를 이용한 데이터베이스 클래스 사용

문서/뷰 아키텍처를 사용 하거나 사용 하지 않고 MFC 데이터베이스 클래스를 사용할 수 있습니다. 이 항목에서는 문서 및 보기 작업을 중점적으로 설명 합니다. 다음을 설명 합니다.

- 문서에서 개체를 기본 보기로 사용 하 여 [폼 기반 응용 프로그램을 작성 하는 방법](#_core_writing_a_form.2d.based_application) `CRecordView` 입니다.

- [문서 및 뷰에서 레코드 집합 개체를 사용 하는 방법](#_core_using_recordsets_in_documents_and_views)

- [기타 고려 사항](#_core_other_factors)

대안에 대해서는 [MFC: 문서 및 뷰를 사용 하지 않는 데이터베이스 클래스 사용](../data/mfc-using-database-classes-without-documents-and-views.md)을 참조 하세요.

## <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a> Form-Based 응용 프로그램 작성

많은 데이터 액세스 응용 프로그램은 양식을 기반으로 합니다. 사용자 인터페이스는 사용자가 데이터를 검사, 입력 또는 편집 하는 컨트롤을 포함 하는 폼입니다. 응용 프로그램 양식을 기반으로 만들려면 클래스를 사용 `CRecordView` 합니다. MFC 응용 프로그램 마법사를 실행 하 고 **데이터베이스 지원** 페이지에서 **ODBC** 클라이언트 유형을 선택 하는 경우 프로젝트는 `CRecordView` 뷰 클래스에 대해를 사용 합니다.

폼 기반 응용 프로그램에서 각 레코드 뷰 개체는 개체에 대 한 포인터를 저장 `CRecordset` 합니다. 프레임 워크의 RFX (레코드 필드 교환) 메커니즘은 레코드 집합과 데이터 원본 간에 데이터를 교환 합니다. DDX (대화 상자 데이터 교환) 메커니즘은 레코드 집합 개체의 필드 데이터 멤버와 폼의 컨트롤 간에 데이터를 교환 합니다. `CRecordView` 는 폼에서 레코드에서 레코드로 이동 하는 기본 명령 처리기 함수도 제공 합니다.

응용 프로그램 마법사를 사용 하 여 폼 기반 응용 프로그램을 만들려면 mfc 응용 프로그램 및 [데이터베이스 지원, Mfc 응용 프로그램 마법사](../mfc/reference/database-support-mfc-application-wizard.md) [Forms-Based 만들기](../mfc/reference/creating-a-forms-based-mfc-application.md) 를 참조 하세요.

폼에 대 한 자세한 내용은 [레코드 뷰](../data/record-views-mfc-data-access.md)를 참조 하세요.

## <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a> 문서 및 뷰에서 레코드 집합 사용

많은 간단한 양식 기반 응용 프로그램에는 문서가 필요 하지 않습니다. 응용 프로그램이 더 복잡 한 경우에는 데이터베이스에 대 한 프록시로 문서를 사용 하 여 `CDatabase` 데이터 원본에 연결 하는 개체를 저장 하는 것이 좋습니다. 폼 기반 응용 프로그램은 일반적으로 뷰의 레코드 집합 개체에 대 한 포인터를 저장 합니다. 다른 종류의 데이터베이스 응용 프로그램은 문서에 레코드 집합과 개체를 저장 `CDatabase` 합니다. 데이터베이스 응용 프로그램에서 문서를 사용 하는 몇 가지 가능성은 다음과 같습니다.

- 로컬 컨텍스트에서 레코드 집합에 액세스 하는 경우 `CRecordset` 필요에 따라 문서 또는 뷰의 멤버 함수에서 로컬로 개체를 만듭니다.

   레코드 집합 개체를 함수에서 지역 변수로 선언 합니다. 생성자에 NULL을 전달 하면 프레임 워크에서 임시 개체가 생성 되 고 열립니다 `CDatabase` . 또는 개체에 대 한 포인터를 전달 `CDatabase` 합니다. 함수 내에서 레코드 집합을 사용 하 고 함수가 종료 될 때 자동으로 제거 되도록 합니다.

   레코드 집합 생성자에 NULL을 전달 하면 프레임 워크는 레코드 집합의 멤버 함수에서 반환 된 정보를 사용 하 여 `GetDefaultConnect` 개체를 만들고 `CDatabase` 엽니다. 마법사가를 구현 `GetDefaultConnect` 합니다.

- 문서 수명 중에 레코드 집합에 액세스 하는 경우 문서에 하나 이상의 개체를 포함 `CRecordset` 합니다.

   문서를 초기화 하거나 필요에 따라 레코드 집합 개체를 생성 합니다. 이미 존재 하지 않는 경우 레코드 집합에 대 한 포인터를 반환 하는 함수를 작성할 수 있습니다 (이미 존재 하지 않는 경우). 필요에 따라 레코드 집합을 닫고 삭제 한 후 다시 만들거나 해당 `Requery` 멤버 함수를 호출 하 여 레코드를 새로 고칩니다.

- 문서의 수명이 지속 되는 동안 데이터 소스에 액세스 하는 경우 개체를 포함 `CDatabase` 하거나 개체에 대 한 포인터를 저장 `CDatabase` 합니다.

   `CDatabase`개체는 데이터 원본에 대 한 연결을 관리 합니다. 개체는 문서를 생성 하는 동안 자동으로 생성 되며 `Open` 문서를 초기화할 때 해당 멤버 함수를 호출 합니다. 문서 멤버 함수에서 레코드 집합 개체를 생성할 때 문서 개체에 대 한 포인터를 전달 `CDatabase` 합니다. 이렇게 하면 각 레코드 집합의 데이터 소스가 연결 됩니다. 일반적으로 문서를 닫을 때 데이터베이스 개체는 소멸 됩니다. 일반적으로 레코드 집합 개체는 함수 범위를 종료할 때 소멸 됩니다.

## <a name="other-factors"></a><a name="_core_other_factors"></a> 기타 요소

폼 기반 응용 프로그램은 프레임 워크의 문서 serialization 메커니즘을 사용 하지 않는 경우가 많으므로 **파일** 메뉴에서 **새로 만들기** 및 **열기** 명령을 제거 하거나 사용 하지 않도록 설정 하거나 대체 하는 것이 좋습니다. [Serialization: serialization 및 데이터베이스 입/출력](../mfc/serialization-serialization-vs-database-input-output.md)문서를 참조 하세요.

프레임 워크에서 지원할 수 있는 많은 사용자 인터페이스 가능성을 사용 해야 할 수도 있습니다. 예를 들어 `CRecordView`  분할자 창에서 여러 개체를 사용 하 고 다른 MDI (다중 문서 인터페이스) 자식 창에서 여러 레코드 집합을 열 수 있습니다.

보기에 있는 모든 항목의 인쇄를 구현 하는 것이 좋습니다. 즉, 또는 다른 것으로 구현 된 폼 인지 여부 `CRecordView` 에서 파생 된 클래스 `CFormView` 는 `CRecordView` 인쇄를 지원 하지 않지만 멤버 함수를 재정의 하 여 인쇄를 허용할 수 있습니다 `OnPrint` . 자세한 내용은 클래스 [CFormView](../mfc/reference/cformview-class.md)를 참조 하세요.

문서와 보기를 전혀 사용 하지 않으려고 할 수 있습니다. 이 경우 [MFC: 문서 및 뷰를 사용 하지 않는 데이터베이스 클래스 사용](../data/mfc-using-database-classes-without-documents-and-views.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC 데이터베이스 클래스](../data/mfc-database-classes-odbc-and-dao.md)
