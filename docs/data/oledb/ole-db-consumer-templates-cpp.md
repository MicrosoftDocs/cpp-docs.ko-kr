---
description: '자세한 정보: 소비자 템플릿 OLE DB (c + +)'
title: OLE DB 소비자 템플릿(C++)
ms.date: 10/22/2018
helpviewer_keywords:
- databases [C++], OLE DB templates
- OLE DB consumers [C++], data access
- OLE DB consumer templates [C++]
- databases [C++], consumers
ms.assetid: d3e42612-0bc0-4d65-9c32-0e8a7b219e82
ms.openlocfilehash: 6aaf935234b8ec3396c97345ca7e38a0f8d806bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317157"
---
# <a name="ole-db-consumer-templates-c"></a>OLE DB 소비자 템플릿(C++)

OLE DB 소비자 템플릿은 OLE DB 버전 2.6 사양을 지원합니다. OLE DB 소비자 템플릿은 OLE DB 2.6에 대해 테스트 되지만 사양의 모든 인터페이스를 지원 하지는 않습니다. 소비자 템플릿은 OLE DB 소비자를 구현 하기 위해 작성 해야 하는 코드의 양을 최소화 합니다. 이 템플릿은 다음과 같은 장점이 있습니다.

- OLE DB 기능에 쉽게 액세스하고 ATL 및 MFC와 간단하게 통합할 수 있습니다.

- 데이터베이스 매개 변수 및 열에 대한 간단한 바인딩 모델을 제공합니다.

- OLE DB 프로그래밍을 위한 네이티브 C/C++ 데이터 형식을 제공합니다.

OLE DB 템플릿을 사용하려면 C++ 템플릿, COM 및 OLE DB 인터페이스에 대해 잘 알고 있어야 합니다. OLE DB에 익숙하지 않은 경우 [Microsoft OLE DB Driver for SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)를 참조 하세요.

OLE DB 템플릿은 새로운 개체 모델을 추가하는 대신 기존 OLE DB 개체 모델을 지원합니다. OLE DB 소비자 템플릿의 최상위 계층 클래스는 OLE DB 사양에 정의된 구성 요소와 유사합니다. OLE DB 소비자 템플릿의 디자인에는 행 집합의 여러 접근자와 같은 고급 기능이 포함됩니다. 템플릿과 다중 상속을 사용하면 라이브러리가 작고 유연해집니다.

## <a name="how-ole-db-consumers-access-data"></a>OLE DB 소비자에서 데이터에 액세스하는 방법

소비자는 다음 항목에 설명되어 있는 여러 종류의 개체를 사용합니다.

- [데이터 원본 및 세션](../../data/oledb/data-sources-and-sessions.md)

- [접근자 및 행 집합](../../data/oledb/accessors-and-rowsets.md)

- [명령 및 테이블](../../data/oledb/commands-and-tables.md)

- [사용자 레코드](../../data/oledb/user-records.md)

소비자는 작업을 수행하기 전에 먼저 액세스해야 하는 데이터베이스의 형식(예: SQL, Oracle, ODBC 및 MSDS)에 적합한 OLE DB 공급자를 선택합니다. 이 작업을 수행하려면 일반적으로 열거자( [데이터 소스 및 세션](../../data/oledb/cenumerator-class.md) 에 설명된 대로 [CEnumerator](../../data/oledb/data-sources-and-sessions.md)참조)를 사용합니다.

[데이터 소스 개체](../../data/oledb/data-sources-and-sessions.md) 는 선택한 데이터 소스에 연결하는 데 필요한 연결 정보를 제공합니다. 또한 데이터 소스 개체에는 데이터 소스에 액세스할 수 있는 권한을 사용자에게 제공하는 데 사용되는 인증 정보(예: 로그인 이름 및 암호)가 포함됩니다. 데이터 소스 개체는 데이터베이스에 연결한 다음 하나 이상의 세션 개체를 만듭니다. 각 [세션 개체](../../data/oledb/data-sources-and-sessions.md) 는 데이터베이스와의 고유한 상호 작용(즉, 쿼리 및 데이터 검색)을 관리하고 다른 기존 세션과 독립적으로 이러한 트랜잭션을 수행합니다.

세션에서는 행 집합 및 명령 개체를 만듭니다. [명령 개체](../../data/oledb/commands-and-tables.md) 를 통해 사용자는 데이터베이스와 상호 작용(예: SQL 명령 사용)할 수 있습니다. [행 집합 개체](../../data/oledb/accessors-and-rowsets.md) 는 탐색할 수 있고 [행을 업데이트, 삭제 및 삽입](../../data/oledb/updating-rowsets.md)할 수 있는 데이터 집합입니다.

OLE DB 소비자는 지역 변수로 데이터베이스 테이블의 열을 바인딩합니다. 이렇게 하기 위해 [접근자](../../data/oledb/accessors-and-rowsets.md)를 사용하며, 여기에는 소비자 내에서 데이터가 저장되는 방법에 대한 지도가 들어 있습니다. 이 지도는 소비자 애플리케이션에서 테이블 열과 로컬 버퍼(변수)간의 바인딩 집합으로 구성됩니다.

소비자를 사용할 때 중요한 한 가지 개념은 소비자에서 [명령(또는 테이블) 클래스](../../data/oledb/commands-and-tables.md) 및 [사용자 레코드 클래스](../../data/oledb/user-records.md)의 두 가지 클래스를 선언한다는 것입니다. 접근자 클래스와 행 집합 클래스 둘 다에서 상속되는 명령(또는 테이블) 클래스를 통해 행 집합에 액세스합니다. 사용자 레코드 클래스에는 앞에서 설명한 행 집합 바인딩 지도가 포함됩니다.

자세한 내용은 다음 항목을 참조하세요.

- [OLE DB 소비자 만들기](../../data/oledb/creating-an-ole-db-consumer.md)

- [일반 OLE DB 소비자 시나리오(예제)](../../data/oledb/working-with-ole-db-consumer-templates.md)

## <a name="see-also"></a>참고 항목

[OLE DB 프로그래밍](../../data/oledb/ole-db-programming.md)<br/>
[데이터 액세스](../data-access-in-cpp.md)<br/>
[OLE DB SDK 설명서](/previous-versions/windows/desktop/ms722784(v=vs.85))<br/>
[SQL Server용 Microsoft OLE DB 드라이버](/sql/connect/oledb/oledb-driver-for-sql-server)
