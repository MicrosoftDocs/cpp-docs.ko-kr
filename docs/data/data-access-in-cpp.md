---
description: '에 대 한 자세한 정보: 데이터 액세스 Visual C++'
title: Visual C++의 데이터 액세스
ms.date: 03/28/2017
helpviewer_keywords:
- Visual C++, data access applications
- databases [C++]
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 95da6237-bbe2-480a-ae50-3a520051ceff
ms.openlocfilehash: d314deef66e5f523cffa3434f91b3e0297432b94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170986"
---
# <a name="data-access-in-visual-c"></a>Visual C++의 데이터 액세스

SQL과 NoSQL의 거의 모든 데이터베이스 제품에서는 네이티브 C++ 애플리케이션에 대한 인터페이스를 제공합니다. 업계 표준 인터페이스는 모든 주요 SQL 데이터베이스 제품과 여러 NoSQL 제품에서 지원되는 ODBC입니다. 타사 제품의 경우 자세한 내용은 공급 업체에 문의하세요. 사용 조건이 다양한 타사 라이브러리도 사용할 수 있습니다.

Microsoft는 2011년부터 온-프레미스와 클라우드 모두에서 Microsoft SQL Server 데이터베이스에 연결하는 네이티브 애플리케이션에 대한 표준으로 ODBC를 제공해 왔습니다. 자세한 내용은 [데이터 액세스 프로그래밍\(MFC-ATL\)](data-access-programming-mfc-atl.md)을 참조하세요. C++/CLI 라이브러리는 네이티브 ODBC 드라이버 또는 ADO.NET을 사용할 수 있습니다. 자세한 내용은 [ADO.NET를 사용 하 여 데이터 액세스 (c + +/cli)](../dotnet/data-access-using-adonet-cpp-cli.md) 및 [Visual Studio에서 데이터](/visualstudio/data-tools/accessing-data-in-visual-studio)액세스를 참조 하세요.

## <a name="in-this-section"></a>섹션 내용

[데이터 액세스 프로그래밍 (MFC/ATL)](data-access-programming-mfc-atl.md)<br/>
Visual C++를 사용하는 레거시 데이터 액세스 프로그래밍에 대해 설명합니다. 이 프로그램에서는 기본적으로 ATL(액티브 템플릿 클래스 라이브러리) 또는 MFC(Microsoft Foundation Class) 라이브러리와 같은 클래스 라이브러리 중 하나를 사용하므로 데이터베이스 API를 간편하게 사용할 수 있습니다.

[ODBC (Open Database Connectivity)](odbc/open-database-connectivity-odbc.md)<br/>
MFC(Microsoft Foundation Classes) 라이브러리는 ODBC(Open Database Connectivity)를 사용하여 프로그래밍하는 데 필요한 클래스를 제공합니다.

[OLE DB 프로그래밍](oledb/ole-db-programming.md)<br/>
대부분의 레거시 인터페이스는 일부 시나리오에서, 특히 연결된 서버에 대해 프로그래밍할 때 여전히 필요합니다.

## <a name="related-topics"></a>관련 항목

[C 및 C++를 사용하여 SQL Database에 연결](/azure/sql-database/sql-database-develop-cplusplus-simple)<br/>
C 또는 C++ 애플리케이션에서 Azure SQL Database에 연결합니다.

[C++용 Microsoft Azure Storage Client Library](https://github.com/Azure/azure-storage-cpp)<br/>
[Azure Storage](/azure/storage/common/storage-introduction)는 내구성, 가용성, 확장성을 활용하여 고객의 요구 사항을 충족하는 최신 애플리케이션을 위한 클라우드 저장소 솔루션입니다. C++용 Microsoft Azure Storage Client Library를 사용하여 C++에서 Azure Storage에 연결하세요.

[SQL Server용 ODBC 드라이버](/sql/connect/odbc/microsoft-odbc-driver-for-sql-server)<br/>
최신 ODBC 드라이버는 Microsoft SQL Server 및 C/C++용 Microsoft Azure SQL Database 기반 애플리케이션에 대한 강력한 데이터 액세스를 제공합니다. Always Encrypted, Azure Active Directory 및 AlwaysOn 가용성 그룹을 비롯한 여러 기능을 지원합니다. MacOS 및 Linux에서도 사용할 수 있습니다.

[SQL Server용 OLE DB 드라이버](/sql/connect/oledb/oledb-driver-for-sql-server)<br/>
최신 OLE DB 드라이버는 Microsoft SQL Server 및 Microsoft Azure SQL Database를 지원하는 독립 실행형 데이터 액세스 API(애플리케이션 프로그래밍 인터페이스)입니다.

[Microsoft Azure C 및 C++ 개발자 센터](https://azure.microsoft.com/develop/cpp/)<br/>
향상된 유연성, 확장성 및 안정성을 제공하는 Azure에서는 원하는 도구를 사용하여 C++ 애플리케이션을 쉽게 빌드할 수 있습니다.

[C++에서 Blob Storage를 사용하는 방법](/azure/storage/storage-c-plus-plus-how-to-use-blobs)<br/>
Azure Blob Storage는 클라우드에 구조화되지 않은 데이터를 개체/Blob로 저장하는 서비스입니다. Blob Storage는 문서, 미디어 파일 또는 애플리케이션 설치 프로그램과 같은 모든 종류의 텍스트 또는 이진 데이터를 저장할 수 있습니다. 또한 Blob Storage를 개체 스토리지라고 합니다.

[ODBC 프로그래머 참조](/sql/odbc/reference/odbc-programmer-s-reference)<br/>
ODBC 인터페이스는 C 프로그래밍 언어와 함께 사용하도록 설계되었습니다. ODBC 인터페이스는 SQL 문, ODBC 함수 호출 및 C 프로그래밍의 세 가지 영역에서 사용됩니다.

## <a name="see-also"></a>참고 항목

[Visual Studio의 C++](../overview/visual-cpp-in-visual-studio.md)
