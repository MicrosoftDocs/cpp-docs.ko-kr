---
description: '자세히 알아보기: 데이터 원본에 연결'
title: 데이터 원본에 연결
ms.date: 11/04/2016
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
ms.openlocfilehash: 3bc5436a678d39682b89d82dd7f3ab90eb6f5bb5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295122"
---
# <a name="connecting-to-a-data-source"></a>데이터 원본에 연결

ODBC 데이터 원본은 데이터의 특정 집합, 데이터에 액세스 하는 데 필요한 정보 및 데이터 원본 이름을 사용 하 여 설명할 수 있는 데이터 원본의 위치입니다. 프로그램의 관점에서 볼 때 데이터 원본에는 데이터, DBMS, 네트워크 (있는 경우) 및 ODBC가 포함 됩니다.

데이터 원본에서 제공 하는 데이터에 액세스 하려면 먼저 프로그램에서 데이터 원본에 대 한 연결을 설정 해야 합니다. 모든 데이터 액세스는 해당 연결을 통해 관리 됩니다.

데이터 원본 연결은 클래스 [CDatabase](../../mfc/reference/cdatabase-class.md)에 의해 캡슐화 됩니다. `CDatabase`개체가 데이터 원본에 연결 된 경우 다음을 수행할 수 있습니다.

- 테이블 또는 쿼리에서 레코드를 선택 하는 레코드 [집합](../../mfc/reference/crecordset-class.md)을 생성 합니다.

- 데이터 원본에서 필요한 트랜잭션 수준을 지 원하는 경우 [트랜잭션을](../../data/odbc/transaction-odbc.md)관리 하 고, 업데이트를 일괄 처리 하 여 데이터 원본에 한꺼번에 커밋 (또는 전체 트랜잭션을 롤백합니다.

- [SQL](../../data/odbc/sql.md) 문을 직접 실행 합니다.

데이터 원본 연결 작업을 마치면 개체를 닫고 `CDatabase` 제거 하거나 새 연결에 다시 사용 합니다. 데이터 원본 연결에 대 한 자세한 내용은 [데이터 원본 (ODBC)](../../data/odbc/data-source-odbc.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[ODBC 및 MFC](../../data/odbc/odbc-and-mfc.md)
