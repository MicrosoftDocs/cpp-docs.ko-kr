---
description: '자세히 알아보기: 레코드 뷰를 사용 하 여 작업 하는 사용자의 역할 (MFC Data Access)'
title: 레코드 뷰를 사용하여 작업할 때의 사용자 작업  (MFC Data Access)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
ms.openlocfilehash: f1eff5db930859ca1956286a9364c72b02f2b473
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302610"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>레코드 뷰를 사용하여 작업할 때의 사용자 작업  (MFC Data Access)

다음 테이블에는 레코드 뷰를 사용하기 위해 일반적으로 수행해야 하는 작업과 프레임워크에서 자동으로 수행하는 작업이 나와 있습니다.

### <a name="working-with-a-record-view-you-and-the-framework"></a>레코드 뷰 사용: 개발자의 작업과 프레임워크에서 수행하는 작업

|사용자|프레임워크|
|---------|-------------------|
|Visual C++ 대화 상자 편집기를 사용하여 폼을 디자인합니다.|컨트롤이 있는 대화 상자 템플릿 리소스를 만듭니다.|
|[MFC 응용 프로그램 마법사](../mfc/reference/database-support-mfc-application-wizard.md) 를 사용 하 여 [CRecordView](../mfc/reference/crecordview-class.md) 및 [CRecordset](../mfc/reference/crecordset-class.md)에서 파생 된 클래스를 만들 수 있습니다.|클래스를 자동으로 작성합니다.|
|레코드 뷰 컨트롤을 레코드 집합 필드 데이터 멤버에 매핑합니다.|컨트롤과 레코드 집합 필드 간에 DDX를 제공합니다.|
||메뉴 또는 도구 모음 단추에서 **처음** 으로 이동, **마지막으로 이동**, **다음으로 이동** 및 이전 명령 **이동** 에 대 한 기본 명령 처리기를 제공 합니다.|
||데이터 소스에 대한 변경 내용을 업데이트합니다.|
|[선택 사항] 두 번째 레코드 집합의 데이터로 목록 상자 또는 콤보 상자나 기타 컨트롤을 채우는 코드를 작성합니다.||
|[선택 사항] 특수 유효성 검사용 코드를 작성합니다.||
|[선택 사항] 레코드를 추가하거나 삭제하는 코드를 작성합니다.||

데이터베이스를 사용할 때는 폼 기반 프로그래밍 방식만 사용할 수 있습니다. 다른 사용자 인터페이스를 사용 하거나 사용자 인터페이스를 사용 하지 않는 응용 프로그램에 대 한 자세한 내용은 Mfc: 문서 및 뷰를 사용 하 여 [데이터베이스 클래스 사용](../data/mfc-using-database-classes-with-documents-and-views.md) 및 [mfc: 문서 및 뷰 없이 데이터베이스 클래스 사용](../data/mfc-using-database-classes-without-documents-and-views.md)을 참조 하세요. 데이터베이스 레코드를 표시 하는 다른 방법은 [CListView](../mfc/reference/clistview-class.md) 및 [ctreeview](../mfc/reference/ctreeview-class.md)클래스를 참조 하세요.

## <a name="see-also"></a>참고 항목

[레코드 뷰 (MFC Data Access)](../data/record-views-mfc-data-access.md)<br/>
[ODBC 드라이버 목록](../data/odbc/odbc-driver-list.md)
