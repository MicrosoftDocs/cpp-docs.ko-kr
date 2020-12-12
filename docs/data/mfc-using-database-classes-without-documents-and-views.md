---
description: '자세한 정보: MFC: 문서 및 뷰를 사용 하지 않는 데이터베이스 클래스 사용'
title: 'MFC: 문서 및 뷰를 이용하지 않는 데이터베이스 클래스 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC applications [C++], without views
- documents [C++], applications without
- ODBC applications [C++]
- document/view architecture [C++], in databases
- files [C++], MFC
- database classes [C++], MFC
- CRecordView class, using in database applications
- database applications [C++], without views
- database applications [C++], application wizard options
- application wizards [C++], creating database applications
- ODBC [C++], file support in database applications
- ODBC applications [C++], without documents
- database applications [C++], without documents
- user interface [C++], drawing information
ms.assetid: 15bf52d4-91cf-4b1d-8b37-87c3ae70123a
ms.openlocfilehash: 32b019286a07cacc0c7bf95145d0aedde804ff92
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295161"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: 문서 및 뷰를 이용하지 않는 데이터베이스 클래스 사용

데이터베이스 응용 프로그램에서 프레임 워크의 문서/뷰 아키텍처를 사용 하지 않으려는 경우가 있습니다. 이 토픽에서는 다음 내용을 설명합니다.

- 문서 serialization과 같은 [문서를 사용할 필요가 없는 경우](#_core_when_you_don.92.t_need_documents)

- Serialization 없이 응용 프로그램을 지원 하 고 **새로 만들기**, **열기**, **저장** 및 다른 **이름으로 저장** 과 같은 문서 관련 **파일** 메뉴 명령을 사용 하지 않는 [응용 프로그램 마법사 옵션](#_core_appwizard_options_for_documents_and_views) 입니다.

- [최소 문서를 사용 하는 응용 프로그램으로 작업 하는 방법](#_core_applications_with_minimal_documents)입니다.

- [문서 또는 뷰를 사용 하지 않고 응용 프로그램](#_core_applications_with_no_document)을 구성 하는 방법입니다.

## <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a> 문서가 필요 하지 않은 경우

일부 응용 프로그램에는 문서의 고유한 개념이 있습니다. 이러한 응용 프로그램은 일반적으로 **파일 열기** 명령을 사용 하 여 저장소의 파일을 모두 또는 대부분 메모리에 로드 합니다. **파일 저장** 또는 다른 **이름으로 저장** 명령을 사용 하 여 업데이트 된 파일을 저장소에 한꺼번에 다시 씁니다. 사용자에 게 표시 되는 데이터 파일은 무엇 인가요?

그러나 일부 응용 프로그램 범주에는 문서가 필요 하지 않습니다. 데이터베이스 응용 프로그램은 트랜잭션 측면에서 작동 합니다. 응용 프로그램은 데이터베이스에서 레코드를 선택 하 고 사용자에 게 한 번에 하나씩 표시 합니다. 사용자에 게 표시 되는 항목은 일반적으로 메모리의 유일한 현재 레코드입니다.

응용 프로그램에 데이터를 저장 하기 위한 문서가 필요 하지 않은 경우 프레임 워크의 문서/뷰 아키텍처 전체 또는 일부를 사용할 수 있습니다. 선호 하는 방법은 선호 하는 방법에 따라 달라 집니다. 다음 작업을 할 수 있습니다.

- 데이터 원본에 대 한 연결을 저장 하는 위치로 최소한의 문서를 사용 하지만 직렬화와 같은 일반적인 문서 기능을 사용 합니다. 이 방법은 데이터의 여러 보기를 원하는 경우 모든 뷰를 동기화 하 여 한 번에 모두 업데이트 하려는 경우에 유용 합니다.

- 뷰를 사용 하는 대신 직접 그리는 프레임 창을 사용 합니다. 이 경우 문서를 생략 하 고 모든 데이터 또는 데이터 연결을 프레임 창 개체에 저장 합니다.

## <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a> 문서 및 뷰에 대 한 응용 프로그램 마법사 옵션

MFC 응용 프로그램 마법사에는 다음 표에 나열 된 **데이터베이스 지원 선택** 에 몇 가지 옵션이 있습니다. MFC 응용 프로그램 마법사를 사용 하 여 응용 프로그램을 만드는 경우 이러한 모든 옵션은 문서 및 뷰로 응용 프로그램을 생성 합니다. 일부 옵션은 불필요 한 문서 기능을 생략 하는 문서와 보기를 제공 합니다. 자세한 내용은 [MFC 응용 프로그램 마법사, 데이터베이스 지원](../mfc/reference/database-support-mfc-application-wizard.md)을 참조 하세요.

|옵션|보기|문서|
|------------|----------|--------------|
|**없음**|`CView`에서 파생됩니다.|에서는 데이터베이스를 지원 하지 않습니다. 기본 옵션입니다.<br /><br /> [응용 프로그램 종류, MFC 응용 프로그램 마법사](../mfc/reference/application-type-mfc-application-wizard.md) 페이지에서 **문서/뷰 아키텍처 지원** 옵션을 선택 하는 경우 **파일** 메뉴에서 serialization 및 **새로 만들기** **,** **저장** 및 다른 **이름으로 저장** 명령을 비롯 한 전체 문서 지원을 받을 수 있습니다. [문서가 없는 응용 프로그램을](#_core_applications_with_no_document)참조 하십시오.|
|**헤더 파일만**|`CView`에서 파생됩니다.|응용 프로그램에 대 한 기본 수준의 데이터베이스 지원을 제공 합니다.<br /><br /> Afxdb를 포함 합니다. 링크 라이브러리를 추가 하지만 데이터베이스 관련 클래스를 만들지는 않습니다. 나중에 레코드 집합을 만들고이를 사용 하 여 레코드를 검사 하 고 업데이트할 수 있습니다.|
|**파일을 지원 하지 않는 데이터베이스 뷰**|파생 된 `CRecordView`|문서 지원을 제공 하지만 serialization은 지원 하지 않습니다. 문서는 레코드 집합을 저장 하 고 여러 뷰를 조정할 수 있습니다. 는 serialization 또는 **새**, **열기**, **저장** 및 다른 **이름으로 저장** 명령을 지원 하지 않습니다. [최소 문서를 사용 하는 응용 프로그램을](#_core_applications_with_minimal_documents)참조 하세요. 데이터베이스 뷰를 포함 하는 경우 데이터 원본을 지정 해야 합니다.<br /><br /> 데이터베이스 헤더 파일, 링크 라이브러리, 레코드 뷰 및 레코드 집합을 포함 합니다. [응용 프로그램 종류, MFC 응용 프로그램 마법사](../mfc/reference/application-type-mfc-application-wizard.md) 페이지에서 선택한 **문서/뷰 아키텍처 지원** 옵션을 사용 하는 응용 프로그램에만 사용할 수 있습니다.|
|**파일이 지원 되는 데이터베이스 뷰**|파생 된 `CRecordView`|Serialization 및 문서 관련 **파일** 메뉴 명령을 비롯 한 전체 문서 지원 기능을 제공 합니다. 데이터베이스 응용 프로그램은 일반적으로 파일 별로 아닌 레코드 별로 작업 하므로 serialization이 필요 하지 않습니다. 그러나 serialization에는 특별 한 사용이 있을 수 있습니다. [최소 문서를 사용 하는 응용 프로그램을](#_core_applications_with_minimal_documents)참조 하세요. 데이터베이스 뷰를 포함 하는 경우 데이터 원본을 지정 해야 합니다.<br /><br /> 데이터베이스 헤더 파일, 링크 라이브러리, 레코드 뷰 및 레코드 집합을 포함 합니다. [응용 프로그램 종류, MFC 응용 프로그램 마법사](../mfc/reference/application-type-mfc-application-wizard.md) 페이지에서 선택한 **문서/뷰 아키텍처 지원** 옵션을 사용 하는 응용 프로그램에만 사용할 수 있습니다.|

Serialization 및 serialization에 대 한 대체 사용의 대안에 대 한 자세한 내용은 [serialization: serialization 및 데이터베이스 입/출력](../mfc/serialization-serialization-vs-database-input-output.md)을 참조 하세요.

## <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a> 최소 문서를 사용 하는 응용 프로그램

MFC 응용 프로그램 마법사에는 폼 기반 데이터 액세스 응용 프로그램을 지 원하는 두 가지 옵션이 있습니다. 각 옵션은 `CRecordView` 파생 뷰 클래스 및 문서를 만듭니다. 문서에서 벗어나면 차이가 있습니다.

### <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a> 파일이 지원 되지 않는 문서

문서를 직렬화 하지 않아도 되는 경우 **파일을 지원 하지 않는 데이터베이스 뷰** 응용 프로그램 마법사 데이터베이스 옵션을 선택 합니다. 문서는 다음과 같은 유용한 용도로 사용 됩니다.

- 개체를 저장 하는 편리한 장소입니다 `CRecordset` .

   이 사용법은 일반적인 문서 개념과 유사 합니다. 문서는 데이터 (이 경우 레코드 집합)를 저장 하 고 보기는 문서 뷰입니다.

- 응용 프로그램에서 여러 개의 뷰 (예: 여러 레코드 뷰)를 표시 하는 경우 문서에서 뷰 조정을 지원 합니다.

   여러 뷰가 동일한 데이터를 표시 하는 경우 `CDocument::UpdateAllViews` 멤버 함수를 사용 하 여 뷰가 데이터를 변경할 때 모든 뷰로 업데이트를 조정할 수 있습니다.

간단한 양식 기반 응용 프로그램에는 일반적으로이 옵션을 사용 합니다. 응용 프로그램 마법사는 이러한 응용 프로그램에 대 한 편리한 구조를 자동으로 지원 합니다.

### <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a> 파일이 지원 되는 문서

문서 관련 **파일** 메뉴 명령 및 문서 serialization을 사용 하는 경우 응용 프로그램 마법사 데이터베이스 옵션 **파일 지원 포함 데이터베이스 뷰** 를 선택 합니다. 프로그램의 데이터 액세스 부분에 대해 [파일 지원 없이 문서](#_core_a_document_without_file_support)에 설명 된 것과 동일한 방법으로 문서를 사용할 수 있습니다. 예를 들어 문서의 직렬화 기능을 사용 하 여 사용자의 기본 설정이 나 기타 유용한 정보를 저장 하는 직렬화 된 사용자 프로필 문서를 읽고 쓸 수 있습니다. 자세한 내용은 [serialization: serialization 및 데이터베이스 입/출력](../mfc/serialization-serialization-vs-database-input-output.md)을 참조 하세요.

응용 프로그램 마법사는이 옵션을 지원 하지만 문서를 serialize 하는 코드를 작성 해야 합니다. Serialize 된 정보를 문서 데이터 멤버에 저장 합니다.

## <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a> 문서가 없는 응용 프로그램

문서나 뷰를 사용 하지 않는 응용 프로그램을 작성 해야 하는 경우도 있습니다. 문서 없이 `CRecordset` 프레임 창 클래스 또는 응용 프로그램 클래스에 데이터 (예: 개체)를 저장 합니다. 추가 요구 사항은 응용 프로그램이 사용자 인터페이스를 표시 하는지 여부에 따라 달라 집니다.

### <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a> 사용자 인터페이스를 사용 하 여 데이터베이스 지원

사용자 인터페이스 (예: 콘솔 명령줄 인터페이스)가 있는 경우 응용 프로그램은 뷰가 아니라 프레임 창의 클라이언트 영역에 직접 그립니다. 이러한 응용 프로그램은 `CRecordView` `CFormView` 기본 사용자 인터페이스에, 또는를 사용 하지 `CDialog` 않지만 일반적으로 `CDialog` 일반 대화에 사용 됩니다.

### <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a> 문서 없이 응용 프로그램 작성

응용 프로그램 마법사는 문서 없이 응용 프로그램을 만드는 기능을 지원 하지 않으므로 사용자가 직접 `CWinApp` 파생 된 클래스를 작성 하 고 필요한 경우 또는 클래스도 만들어야 합니다 `CFrameWnd` `CMDIFrameWnd` . `CWinApp::InitInstance`응용 프로그램 개체를 재정의 하 고 선언 합니다.

```cpp
CYourNameApp theApp;
```

프레임 워크는 여전히 메시지 매핑 메커니즘과 기타 많은 기능을 제공 합니다.

### <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a> 사용자 인터페이스와 별도의 데이터베이스 지원

일부 응용 프로그램에는 사용자 인터페이스가 없거나 최소한 하나만 필요 합니다. 예를 들어 다음을 작성 한다고 가정 합니다.

- 다른 응용 프로그램 (클라이언트)에서 응용 프로그램과 데이터 원본 간의 데이터를 특별 하 게 처리 하기 위해 호출 하는 중간 데이터 액세스 개체입니다.

- 데이터를 한 데이터베이스 형식에서 다른 데이터베이스로 이동 하거나 계산을 수행 하 고 일괄 처리 업데이트를 수행 하는 응용 프로그램과 같이 사용자 개입 없이 데이터를 처리 하는 응용 프로그램입니다.

개체를 소유 하 고 있는 문서가 없으므로 `CRecordset` 파생 된 응용 프로그램 클래스에 포함 된 데이터 멤버로 저장할 수도 있습니다 `CWinApp` . 대안은 다음과 같습니다.

- 영구 개체를 유지 하지 않습니다 `CRecordset` . NULL을 레코드 집합 클래스 생성자에 전달할 수 있습니다. 이 경우 프레임 워크는 `CDatabase`  레코드 집합의 멤버 함수에 있는 정보를 사용 하 여 임시 개체를 만듭니다 `GetDefaultConnect` . 가장 가능성이 높은 대체 방법입니다.

- 개체를 `CRecordset` 전역 변수로 설정 이 변수는 재정의에서 동적으로 만드는 레코드 집합 개체에 대 한 포인터 여야 합니다 `CWinApp::InitInstance` . 이렇게 하면 프레임 워크가 초기화 되기 전에 개체를 생성 하는 것을 방지할 수 있습니다.

- 문서 또는 뷰의 컨텍스트 내에서와 같이 레코드 집합 개체를 사용 합니다. 응용 프로그램 또는 프레임 창 개체의 멤버 함수에 레코드 집합을 만듭니다.

## <a name="see-also"></a>참고 항목

[MFC 데이터베이스 클래스](../data/mfc-database-classes-odbc-and-dao.md)
