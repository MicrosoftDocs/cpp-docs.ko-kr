---
description: '자세한 정보: 데이터 액세스 프로그래밍 (MFC/ATL)'
title: 데이터 액세스 프로그래밍 (MFC-ATL)
ms.date: 11/16/2018
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: def97b2c-b5a6-445f-afeb-308050fd4852
ms.openlocfilehash: 7785eb65bd26c6c8bf4b60d5a8a919097627f20c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136476"
---
# <a name="data-access-programming-mfcatl"></a>데이터 엑세스 프로그래밍 (MFC/ATL)

수년에 걸쳐 Visual C++는 데이터베이스로 작업하는 여러 가지 방법을 제공했습니다. 2011 Microsoft에서는 네이티브 코드의 SQL Server 제품에 액세스 하기 위한 기본 기술로 ODBC (Open Database Connectivity)를 정렬 하 고 있음을 발표 했습니다. ODBC는 산업 표준으로, 이것을 사용하여 여러 플랫폼 및 데이터 소스에서 코드의 이식성을 극대화할 수 있습니다. 대부분의 SQL 데이터베이스 제품 및 많은 NoSQL 제품이 ODBC를 지원합니다. 하위 수준 ODBC API를 호출하여 ODBC를 직접 사용할 수도 있고, MFC ODBC 래퍼 클래스 또는 타사 C++ 래퍼 라이브러리를 사용할 수도 있습니다.

OLE DB는 COM 사양을 기반으로 하는 하위 수준의 고성능 API이며 Windows에서만 지원됩니다. 프로그램이 [연결된 서버](/sql/relational-databases/linked-servers/linked-servers-database-engine)에 액세스하는 경우 OLE DB를 사용합니다. ATL은 사용자 지정 OLE DB 공급자 및 소비자를 보다 쉽게 생성할 수 있도록 하는 OLE DB 템플릿을 제공합니다. Microsoft SQL Server에 대 한 최신 공급자는 SQL Server에 대 한 [OLE DB 드라이버](/sql/connect/oledb/oledb-driver-for-sql-server)설명서에서 찾을 수 있습니다.

## <a name="porting-data-applications"></a>데이터 응용 프로그램 포팅

레거시 응용 프로그램에서 OLE DB 또는 더 높은 수준의 ADO 인터페이스를 사용 하 여 SQL Server에 연결 하는 경우 최신 SQL Server 기능을 활용 하기 위해 [SQL Server에 대 한 최신 OLE DB 드라이버로](/sql/connect/oledb/oledb-driver-for-sql-server) 마이그레이션하는 것을 고려해 야 합니다. 다른 대안은 플랫폼 간 이식성 또는 최신 SQL Server 기능이 필요 하지 않은 경우 Microsoft OLE DB Provider for ODBC (MSDASQL)를 사용할 수 있습니다.  MSDASQL은 OLEDB 및 ADO(내부적으로 OLEDB 사용)에서 빌드된 애플리케이션이 ODBC 드라이버를 통해 데이터 소스에 액세스하도록 허용합니다. 다른 변환 계층과 마찬가지로 MSDASQL도 데이터베이스 성능에 영향을 줄 수 있습니다. 그러한 영향이 애플리케이션에 중요한지 여부를 확인하려면 테스트해야 합니다. MSDASQL은 Windows 운영 체제와 함께 제공되며 Windows Server 2008 및 Windows Vista SP1은 64비트 버전을 포함할 수 있는 최초의 Windows 릴리스입니다.

C + + 응용 프로그램이 ODBC를 통해 SQL Server 또는 Azure SQL Database에 연결 하는 경우 [최신 odbc 드라이버](/sql/connect/odbc/download-odbc-driver-for-sql-server)를 사용 해야 합니다.

C++/CLI를 사용하는 경우에는 ADO.NET을 계속 사용할 수 있습니다. 자세한 내용은 [ADO.NET을 사용하여 데이터 액세스(C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) 및 [Visual Studio에서 데이터 액세스](/visualstudio/data-tools/accessing-data-in-visual-studio)를 참조하세요.

- ODBC 래퍼 클래스 외에도 MFC는 Access 데이터베이스에 연결하기 위한 DAO(데이터 액세스 개체) 래퍼 클래스도 제공합니다.  그러나 DAO는 사용되지 않습니다. CDaoDatabase 또는 CDaoRecordset 기반의 모든 코드를 업그레이드해야 합니다.

Microsoft Windows에서 데이터 액세스 기술의 기록에 대한 자세한 내용은 [Microsoft Data Access Components(Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components)를 참조하세요.

## <a name="see-also"></a>참고 항목

[데이터 액세스](data-access-in-cpp.md)<br/>
[Microsoft ODBC(Open Database Connectivity)](/sql/odbc/microsoft-open-database-connectivity-odbc)<br/>
