---
description: '자세한 정보: 데이터베이스 응용 프로그램을 만드는 작업 시퀀스'
title: 데이터베이스 애플리케이션을 만드는 작업 시퀀스
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
ms.openlocfilehash: 86f06ae5200fc8646ccb80bfec4e2814b94f9225
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217590"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>데이터베이스 애플리케이션을 만드는 작업 시퀀스

다음 표에서는 데이터베이스 응용 프로그램을 작성할 때의 역할 및 프레임 워크의 역할을 보여 줍니다.

> [!NOTE]
> Visual C++ 환경과 마법사는 dao를 지원 하지 않습니다 (DAO 클래스가 포함 되어 있지만 계속 사용할 수 있음). 새 MFC 프로젝트에는 ODBC를 사용 하는 것이 좋습니다. DAO는 기존 응용 프로그램을 유지 관리 하는 데만 사용 해야 합니다.

### <a name="creating-database-applications"></a>데이터베이스 응용 프로그램 만들기

|작업|너 해|프레임 워크는|
|----------|------------|------------------------|
|MFC ODBC 또는 DAO 클래스를 사용할지 여부를 결정 합니다.|새 MFC 프로젝트에 ODBC를 사용 합니다. DAO는 기존 응용 프로그램을 유지 관리 하는 데만 사용 합니다. 일반 정보는 [데이터 액세스 프로그래밍](../data/data-access-programming-mfc-atl.md)문서를 참조 하세요.|프레임 워크는 데이터베이스 액세스를 지 원하는 클래스를 제공 합니다.|
|데이터베이스 옵션을 사용 하 여 기본 응용 프로그램을 만듭니다.|MFC 응용 프로그램 마법사를 실행 합니다. 데이터베이스 지원 페이지에서 옵션을 선택 합니다. 레코드 뷰를 만드는 옵션을 선택 하는 경우 다음도 지정 합니다.<br /><br />-데이터 원본 및 테이블 이름<br />-쿼리 이름 또는 이름입니다.|MFC 응용 프로그램 마법사는 파일을 만들고 필요한 포함을 지정 합니다. 지정 하는 옵션에 따라 파일에는 레코드 집합 클래스가 포함 될 수 있습니다.|
|데이터베이스 양식이 나 폼을 디자인 합니다.|Visual C++ 대화 상자 편집기를 사용 하 여 레코드 뷰 클래스에 대 한 대화 상자 템플릿 리소스에 컨트롤을 추가할 수 있습니다.|MFC 응용 프로그램 마법사는 채울 빈 대화 상자 템플릿 리소스를 만듭니다.|
|필요에 따라 추가 레코드 뷰 및 레코드 집합 클래스를 만듭니다.|클래스 뷰를 사용 하 여 클래스와 대화 상자 편집기를 만들어 뷰를 디자인 합니다.|클래스 뷰 새 클래스에 대 한 추가 파일을 만듭니다.|
|필요에 따라 코드에 레코드 집합 개체를 만듭니다. 각 레코드 집합을 사용 하 여 레코드 조작 ...|레코드 집합은 마법사를 사용 하 여 [CRecordset](../mfc/reference/crecordset-class.md) 에서 파생 된 클래스를 기반으로 합니다.|ODBC는 RFX (레코드 필드 교환)를 사용 하 여 데이터베이스와 레코드 집합의 필드 데이터 멤버 간에 데이터를 교환 합니다. 레코드 뷰를 사용 하는 경우 DDX (대화 상자 데이터 교환)는 레코드 뷰에서 레코드 집합과 컨트롤 간에 데이터를 교환 합니다.|
|... 또는 열려는 각 데이터베이스에 대 한 명시적 [CDatabase](../mfc/reference/cdatabase-class.md) 를 코드에 만듭니다.|데이터베이스 개체의 레코드 집합 개체를 기준으로 합니다.|데이터베이스 개체는 데이터 원본에 대 한 인터페이스를 제공 합니다.|
|데이터 열을 레코드 집합에 동적으로 바인딩합니다.|ODBC에서 파생 된 레코드 집합 클래스에 코드를 추가 하 여 바인딩을 관리 합니다. [레코드 집합: 데이터 열 동적 바인딩 (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)문서를 참조 하세요.||

## <a name="see-also"></a>참고 항목

[프레임 워크를 기반으로 빌드](../mfc/building-on-the-framework.md)<br/>
[MFC 응용 프로그램을 빌드하기 위한 작업 시퀀스](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[OLE 응용 프로그램을 만들기 위한 작업 시퀀스](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[ActiveX 컨트롤을 만드는 작업 시퀀스](../mfc/sequence-of-operations-for-creating-activex-controls.md)
