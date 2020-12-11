---
description: '자세한 정보: ATL OLE DB 소비자 마법사'
title: ATL OLE DB 소비자 마법사
ms.date: 07/02/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
ms.openlocfilehash: 5d5fb0e6d5ec08ba75aa84a501169544598d8843
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158701"
---
# <a name="atl-ole-db-consumer-wizard"></a>ATL OLE DB 소비자 마법사

::: moniker range="msvc-160"

Visual Studio 2019 이상에서는 이 마법사를 사용할 수 없습니다.

::: moniker-end

::: moniker range="<=msvc-150"

이 마법사에서는 지정한 OLE DB 공급자를 통해 지정한 데이터 소스에 액세스하는 데 필요한 데이터 바인딩을 사용하여 OLE DB 소비자 클래스를 설정합니다.

> [!NOTE]
> 이 마법사에서 **데이터 소스** 단추를 클릭하여 데이터 소스를 선택한 다음, `Class` 및 **.h 파일** 필드에 이름을 입력해야 합니다.

## <a name="uielement-list"></a>UI 요소 목록

- **데이터 원본**

   **데이터 소스** 단추를 사용하면 지정한 OLE DB 공급자를 사용하여 지정한 데이터 소스를 설정할 수 있습니다. 이 단추를 클릭하면 **데이터 연결 속성** 대화 상자가 나타납니다. 연결 문자열을 작성하는 방법 및 **데이터 연결 속성** 대화 상자에 대한 자세한 내용은 Windows SDK 설명서에서 [데이터 연결 API 개요](/previous-versions/windows/desktop/ms718102(v=vs.85))를 참조하세요.

   다음 추가 정보는 **데이터 연결 속성** 대화 상자의 탭에 대해 설명합니다.

  - **공급자** 탭

      데이터 소스에 대한 연결을 관리할 적절한 공급자를 선택합니다. 공급자 형식은 일반적으로 연결하는 데이터베이스 형식에 따라 결정됩니다. **다음** 단추를 클릭하거나 **연결** 탭을 클릭합니다.

  - **연결** 탭

      이 탭의 내용은 선택한 공급자에 따라 달라집니다. 공급자 유형에는 여러 가지가 있지만이 섹션에서는 가장 일반적인 두 가지 SQL 및 ODBC 데이터에 대 한 연결을 다룹니다. 다른 공급자도 여기서 설명하는 필드와 비슷합니다.

      SQL 데이터:

      1. **서버 이름 선택 또는 입력:** 드롭다운 목록 메뉴를 클릭 하 여 네트워크에 등록 된 모든 데이터 서버를 표시 하 고 하나를 선택 합니다.

      1. **서버 로그온 정보 입력:** 사용자 이름 및 암호를 입력 하 여 데이터 서버에 로그온 합니다.

         > [!NOTE]
         > 데이터 연결 속성 대화 상자의 “암호 저장 허용” 기능을 사용하면 보안 문제가 발생합니다. “서버에 로그온하는 데 사용할 정보 입력”에는 다음 두 개의 라디오 단추가 있습니다.
         >
         > - **Windows NT 통합 보안 사용**
         > - **특정 사용자 이름 및 암호 사용**
         >
         > **특정 사용자 이름 및 암호 사용** 을 선택하면 암호를 저장할 수 있지만(“암호 저장 허용” 확인란 사용), 이 옵션은 안전하지 않습니다. **Windows NT 통합 보안 사용** 을 선택하는 것이 좋습니다. 이 옵션은 암호를 암호화하기 때문에 안전합니다.
         > “암호 저장 허용”을 선택하려는 경우도 있습니다. 예를 들어 프라이빗 데이터베이스 솔루션을 사용하여 라이브러리를 릴리스하는 경우 데이터베이스에 직접 액세스하면 안 됩니다. 그 대신에 중간 계층 애플리케이션을 사용하여 선택한 인증 체계를 통해 사용자를 검증한 다음 사용자에게 제공되는 데이터 종류를 제한해야 합니다.

      1. **서버에서 데이터베이스를 선택 합니다.** 드롭다운 목록 메뉴를 클릭 하 여 데이터 서버에 등록 된 모든 데이터베이스를 표시 하 고 하나를 선택 합니다.

         \- 또는 -

         데이터베이스 **파일을 데이터베이스 이름으로 연결 합니다.** 데이터베이스로 사용할 파일을 지정 합니다. 명시적 경로 이름을 입력 합니다.

      ODBC 데이터:

      1. **데이터 원본 지정:** 데이터 원본 이름 또는 연결 문자열을 사용할 수 있습니다.

         **데이터 원본 이름 사용:** 이 드롭다운 목록에는 컴퓨터에 등록 된 데이터 원본이 표시 됩니다. ODBC 데이터 소스 관리자를 사용하여 데이터 소스를 미리 설정할 수 있습니다.

         \- 또는 -

         **연결 문자열 사용:** 이미 가져온 연결 문자열을 입력 하거나 **빌드** 단추를 클릭 합니다. **데이터 소스 선택** 대화 상자가 나타납니다. 파일 또는 머신 데이터 소스를 선택하고 **확인** 을 클릭합니다.

         > [!NOTE]
         > **서버 탐색기** 에서 기존 연결의 속성을 확인하여 연결 문자열을 가져오거나, **서버 탐색기** 에서 **연결 추가** 를 두 번 클릭하여 연결을 만들 수 있습니다.

      1. **서버 로그온 정보 입력:** 사용자 이름 및 암호를 입력 하 여 데이터 서버에 로그온 합니다.

      1. 사용할 초기 카탈로그를 입력합니다.

      1. **연결 테스트** 를 클릭합니다. 테스트에 성공하면 **확인** 을 클릭합니다. 실패하면 로그온 정보를 확인하거나, 다른 데이터베이스를 시도하거나, 다른 데이터 서버를 시도합니다.

  - **고급** 탭

      **네트워크 설정:** **가장 수준** (클라이언트를 가장할 때 서버에서 사용할 수 있는 가장 수준, rpc 가장 수준에 직접 해당) 및 **보호 수준** (클라이언트와 서버 간에 전송 되는 데이터의 보호 수준)을 지정 합니다 .이는 rpc 보호 수준에 직접 대응 됩니다.

      **기타:** **연결 제한** 시간에서 시간 초과가 발생 하기 전까지 허용 되는 유휴 시간 (초)을 지정 합니다. **액세스 권한** 에서 데이터 연결에 대한 액세스 권한을 지정합니다.

      고급 초기화 속성에 대한 자세한 내용은 각 특정 OLE DB 공급자와 함께 제공되는 설명서를 참조하세요.

  - **모두** 탭

      이 탭에는 지정한 데이터 소스 및 연결의 초기화 속성이 요약되어 표시됩니다. 해당 값을 편집할 수 있습니다.

      **확인** 을 클릭하여 작업을 마칩니다. **데이터베이스 개체 선택** 대화 상자가 나타납니다. 이 대화 상자에서 소비자가 사용할 테이블, 뷰 또는 저장 프로시저를 선택합니다.

- **클래스**

   데이터 소스를 선택하면, 선택한 테이블 또는 저장 프로시저에 따라 기본 클래스 이름이 이 상자에 채워집니다(아래의 **데이터 소스 선택** 참조). 클래스 이름을 편집할 수 있습니다.

- **.h 파일**

   데이터 소스를 선택하면, 선택한 테이블 또는 저장 프로시저에 따라 기본 헤더 클래스 이름이 이 상자에 채워집니다(아래의 **데이터 소스 선택** 참조). 헤더 파일의 이름을 편집하거나 기존 헤더 파일을 선택할 수 있습니다.

- **특성 사용**

   이 옵션은 마법사에서 소비자 클래스를 만드는 데 특성을 사용할지 또는 템플릿 선언을 사용할지를 지정합니다. 이 옵션을 선택하면 템플릿 선언 대신 특성이 사용됩니다(기본 옵션). 이 옵션의 선택을 취소하면 특성 대신 템플릿 선언이 사용됩니다.

  - 소비자 **형식** 으로 **테이블** 을 선택하면 마법사에서 `db_source` 및 `db_table` 특성을 사용하여 테이블 및 테이블 접근자 클래스 선언을 만들고 `db_column`을 사용하여 열 맵을 만듭니다. 예를 들어 마법사에서 다음 맵을 만듭니다.

    ```cpp
    // Inject table class and table accessor class declarations
    [db_source("<initialization_string>"), db_table("dbo.Orders")]
    ...
    // Column map
    [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
    [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
    ...
    ```

     그러면 다음 예제와 같이 `CTable` 템플릿 클래스를 사용하여 테이블 및 테이블 접근자 클래스를 선언하고, BEGIN_COLUMN_MAP 및 END_COLUMN_MAP 매크로를 사용하여 열 맵을 만들지 않아도 됩니다.

    ```cpp
    // Table accessor class
        class COrdersAccessor; // Table class
        class COrders : public CTable<CAccessor<COrdersAccessor>>;
    // ...
    // Column map
        BEGIN_COLUMN_MAP(COrderDetailsAccessor)
            COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)
            COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)
            // ...
        END_COLUMN_MAP()
    ```

  - 소비자 **형식** 으로 **명령** 을 선택하면 마법사에서 `db_source` 및 `db_command` 특성을 사용하며, `db_column`을 사용하여 열 맵을 만듭니다. 예를 들어 마법사에서 다음 맵을 만듭니다.

    ```cpp
    [db_source("<initialization_string>"), db_command("SQL_command")]
    ...
    // Column map using db_column is the same as for consumer type of 'table'
    ```

     그러면 다음 예제와 같이 명령 클래스의 .h 파일에 명령 및 명령 접근자 클래스 선언을 사용하지 않아도 됩니다.

    ```cpp
    // Command accessor class:
        class CListOrdersAccessor;
    // Command class:
        class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
    // ...
    // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
    // for consumer type of 'table'
    ```

     자세한 내용은 [특성의 기본 메커니즘](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) 을 참조 하세요.

- **유형**

   이러한 라디오 단추 중 하나를 선택하여 소비자 클래스를 `CTable`에서 파생할지 또는 `CCommand`(기본값)에서 파생할지를 지정합니다.

  - **테이블**

      `CTable` 또는 `db_table`을 사용하여 테이블 및 테이블 접근자 클래스 선언을 만들려는 경우 이 옵션을 선택합니다.

  - **명령**

      `CCommand` 또는 `db_command`를 사용하여 명령 및 명령 접근자 클래스 선언을 만들려는 경우 이 옵션을 선택합니다. 이 옵션이 기본 옵션입니다.

- **지원**

   확인란을 선택하여 소비자에서 지원할 업데이트 종류를 지정합니다(없음이 기본값임). 다음 옵션은 각각 속성 집합 맵의 [DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676(v=vs.85))에 대한 해당 항목과 [DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892(v=vs.85))를 설정합니다.

  - **변경**

      소비자에서 행 집합의 행 데이터 업데이트를 지원하도록 지정합니다.

  - **삽입**

      소비자에서 행 집합의 행 삽입을 지원하도록 지정합니다.

  - **삭제**

      소비자에서 행 집합의 행 삭제를 지원하도록 지정합니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

[ATL OLE DB 소비자](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[코드 마법사에서 기능 추가](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[연결 문자열 및 데이터 연결(OLE DB)](/previous-versions/windows/desktop/ms718376(v=vs.85))
