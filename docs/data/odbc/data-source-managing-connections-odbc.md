---
description: '자세한 정보: 데이터 원본: 연결 관리 (ODBC)'
title: '데이터 소스: 연결 관리(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], multiuser environments
- generalizing connection strings
- ODBC [C++], disconnecting from data sources
- connection strings [C++], generalizing
- database connections [C++], creating
- GetDefaultConnect method
- connections [C++], data source
- ODBC connections [C++], configuring
- disconnecting from data sources
- databases [C++], connecting to
- ODBC connections [C++], disconnecting
- data sources [C++], connecting to
- ODBC connections [C++], connecting to data source
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: c0adbcdd-c000-40c6-b199-09ffdc7b6ef2
ms.openlocfilehash: 748e81dd82190e8269ef30983a66dc3bb5f75731
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253886"
---
# <a name="data-source-managing-connections-odbc"></a>데이터 소스: 연결 관리(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

이 토픽에서는 다음 내용을 설명합니다.

- [데이터 원본을 구성 하는 방법](#_core_configuring_a_data_source)

- [다중 사용자 환경이 데이터 원본 및 해당 레코드 집합에 영향을 주는 방식](#_core_working_in_a_multiuser_environment)입니다.

- [데이터 원본에 대 한 연결 문자열을 일반화 하는 이유](#_core_generalizing_the_connection_string)입니다.

- [데이터 원본에 연결 하는 방법](#_core_connecting_to_a_specific_data_source)

- [데이터 원본에서 연결을 끊는 방법](#_core_disconnecting_from_a_data_source)

- [CDatabase 개체를 다시 사용 하는 방법](#_core_reusing_a_cdatabase_object)입니다.

데이터 원본에 연결 하는 것은 데이터에 액세스 하기 위해 DBMS와 통신을 설정 하는 것을 의미 합니다. ODBC 드라이버를 통해 응용 프로그램에서 데이터 원본에 연결 하는 경우 드라이버는 로컬로 또는 네트워크를 통해 연결을 설정 합니다.

ODBC 드라이버가 있는 모든 데이터 원본에 연결할 수 있습니다. 응용 프로그램의 사용자에 게는 해당 데이터 원본에 대 한 ODBC 드라이버가 동일 해야 합니다. ODBC 드라이버 재배포에 대 한 자세한 내용은 [고객에 게 Odbc 구성 요소 재배포](../../data/odbc/redistributing-odbc-components-to-your-customers.md)를 참조 하세요.

## <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a> 데이터 원본 구성

ODBC 관리자는 데이터 원본을 구성 하는 데 사용 됩니다. 설치 후 ODBC 관리자를 사용 하 여 데이터 원본을 추가 하거나 제거할 수도 있습니다. 응용 프로그램을 만들 때 사용자가 ODBC 관리자에 게 데이터 소스를 추가 하도록 지시 하거나 ODBC 설치를 직접 호출 하 여 응용 프로그램에이 기능을 빌드할 수 있습니다. 자세한 내용은 [ODBC 관리자](../../data/odbc/odbc-administrator.md)를 참조 하십시오.

Excel 파일을 데이터 원본으로 사용할 수 있으며, 파일이 등록 되어 **데이터 소스 선택** 대화 상자에 표시 되도록 구성 해야 합니다.

#### <a name="to-use-an-excel-file-as-a-data-source"></a>Excel 파일을 데이터 원본으로 사용 하려면

1. ODBC 데이터 원본 관리자를 사용 하 여 파일을 구성 합니다.

1. **파일 DSN** 탭에서 **추가** 를 클릭 합니다.

1. **새 데이터 소스 만들기** 대화 상자에서 Excel 드라이버를 선택 하 고 **다음** 을 클릭 합니다.

1. **찾아보기** 를 클릭 하 고 날짜 원본으로 사용할 파일의 이름을 선택 합니다.

> [!NOTE]
> .Xls 파일을 보려면 드롭다운 메뉴에서 **모든 파일** 을 선택 해야 할 수도 있습니다.

1. **다음** 을 클릭하고 **마침** 을 클릭합니다.

1. **ODBC Microsoft Excel 설치** 대화 상자에서 데이터베이스 버전 및 통합 문서를 선택 합니다.

## <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a> 다중 사용자 환경에서 작업

여러 사용자가 데이터 원본에 연결 된 경우 레코드 집합에서 데이터를 조작 하는 동안 데이터를 변경할 수 있습니다. 마찬가지로 변경 내용이 다른 사용자의 레코드 집합에 영향을 줄 수 있습니다. 자세한 내용은 [레코드 집합: 레코드 집합의 레코드 업데이트 방법 (odbc)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) 및 [트랜잭션 (odbc)](../../data/odbc/transaction-odbc.md)을 참조 하세요.

## <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a> 연결 문자열 일반화

마법사는 기본 연결 문자열을 사용 하 여 데이터 원본에 대 한 연결을 설정 합니다. 응용 프로그램을 개발 하는 동안이 연결을 사용 하 여 테이블 및 열을 볼 수 있습니다. 그러나이 기본 연결 문자열은 응용 프로그램을 통해 데이터 원본에 대 한 사용자의 연결에 적합 하지 않을 수 있습니다. 예를 들어, 데이터 소스와 해당 위치에 대 한 경로는 응용 프로그램을 개발 하는 데 사용 된 것과 다를 수 있습니다. 이 경우 [CRecordset:: GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) 멤버 함수를 보다 일반적인 방식으로 다시 구현 하 고 마법사 구현을 취소 해야 합니다. 예를 들어 다음 방법 중 하나를 사용 합니다.

- ODBC 관리자를 사용 하 여 연결 문자열을 등록 하 고 관리 합니다.

- 연결 문자열을 편집 하 고 데이터 원본 이름을 제거 합니다. 프레임 워크는 ODBC를 데이터 소스로 제공 합니다. 런타임에 ODBC는 데이터 원본 이름 및 기타 필요한 연결 정보를 요청 하는 대화 상자를 표시 합니다.

- 데이터 원본 이름만 제공 합니다. 필요한 경우 ODBC에서 사용자 ID와 암호를 묻는 메시지를 표시 합니다. 예를 들어 일반화 하기 전에 연결 문자열은 다음과 같습니다.

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   이 연결 문자열은 Windows NT 통합 보안을 사용 하는 트러스트 된 연결을 지정 합니다. 암호를 하드 코딩 하거나 빈 암호를 지정 하는 것은 중요 한 보안 약점을 만드는 것이 좋습니다. 대신 `GetDefaultConnect` 사용자 ID와 암호를 쿼리할 수 있도록 새 연결 문자열을 지정할 수 있습니다.

    ```cpp
    // User must select data source and supply user ID and password:
        return "ODBC;";
    // User ID and password required:
        return "ODBC;DSN=mydb;";
    // Password required (myuserid must be replaced with a valid user ID):
        return "ODBC;DSN=mydb;UID=myuserid;";
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";
    ```

## <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a> 특정 데이터 원본에 연결

특정 데이터 원본에 연결 하려면 [ODBC 관리자](../../data/odbc/odbc-administrator.md)를 사용 하 여 데이터 원본이 이미 구성 되어 있어야 합니다.

#### <a name="to-connect-to-a-specific-data-source"></a>특정 데이터 원본에 연결 하려면

1. 개체를 생성 `CDatabase` 합니다.

1. `OpenEx`또는 `Open` 멤버 함수를 호출 합니다.

마법사에서 지정한 것과 다른 데이터 소스를 지정 하는 방법에 대 한 자세한 내용은 *MFC 참조* 에서 [Cdatabase:: microsoft.office.interop.visio.documents.openex](../../mfc/reference/cdatabase-class.md#openex) 또는 [cdatabase:: Open](../../mfc/reference/cdatabase-class.md#open) 을 참조 하세요.

## <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a> 데이터 원본에서 연결 끊기

의 멤버 함수를 호출 하기 전에 열려 있는 모든 레코드 집합을 닫아야 합니다 `Close` `CDatabase` . 닫으려는 개체와 연결 된 레코드 집합에서 `CDatabase` 보류 중인 `AddNew` 또는 `Edit` 문이 취소 되 고 보류 중인 모든 트랜잭션이 롤백됩니다.

#### <a name="to-disconnect-from-a-data-source"></a>데이터 원본에서 연결을 끊으려면

1. `CDatabase`개체의 [Close](../../mfc/reference/cdatabase-class.md#close) 멤버 함수를 호출 합니다.

1. 다시 사용 하려는 경우가 아니면 개체를 삭제 합니다.

## <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a> CDatabase 개체 재사용

`CDatabase`동일한 데이터 원본에 다시 연결 하거나 다른 데이터 원본에 연결 하는 데 사용 하는지 여부에 관계 없이 개체를 연결을 끊은 후 다시 사용할 수 있습니다.

#### <a name="to-reuse-a-cdatabase-object"></a>CDatabase 개체를 다시 사용 하려면

1. 개체의 원래 연결을 닫습니다.

1. 개체를 삭제 하는 대신 `OpenEx` 또는 `Open` 멤버 함수를 다시 호출 합니다.

## <a name="see-also"></a>참고 항목

[데이터 원본 (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[데이터 원본: 데이터 원본의 스키마 확인 (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset 클래스](../../mfc/reference/crecordset-class.md)
