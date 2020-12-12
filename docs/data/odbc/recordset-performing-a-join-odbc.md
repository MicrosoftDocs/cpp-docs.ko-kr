---
description: '자세한 정보: 레코드 집합: 조인 수행 (ODBC)'
title: '레코드 집합: 조인 수행(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
ms.openlocfilehash: 1c7aa7bfb6925d9f7e916ddb6cd60061667d7859
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204513"
---
# <a name="recordset-performing-a-join-odbc"></a>레코드 집합: 조인 수행(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

## <a name="what-a-join-is"></a>조인 정의

공통 데이터 액세스 태스크 인 조인 작업을 사용 하면 단일 레코드 집합 개체를 사용 하 여 둘 이상의 테이블에서 데이터를 사용할 수 있습니다. 둘 이상의 테이블을 조인 하면 각 테이블의 열을 포함할 수 있지만 응용 프로그램에 단일 테이블로 표시 되는 레코드 집합이 생성 됩니다. 조인에서 모든 테이블의 모든 열을 사용 하는 경우도 있지만 조인의 SQL **SELECT** 절은 각 테이블의 일부 열만 사용 합니다. 데이터베이스 클래스는 읽기 전용 조인을 지원 하지만 업데이트 가능한 조인은 지원 하지 않습니다.

조인 된 테이블의 열을 포함 하는 레코드를 선택 하려면 다음 항목이 필요 합니다.

- 조인 되는 모든 테이블의 이름을 포함 하는 테이블 목록입니다.

- 참여 하는 모든 열의 이름을 포함 하는 열 목록입니다. 이름이 같지만 테이블이 다른 열은 테이블 이름으로 한정 됩니다.

- 테이블이 조인 되는 열을 지정 하는 필터 (SQL **WHERE** 절)입니다. 이 필터는 "Table1. KeyCol = Table2" 형식을 사용 하 여 실제로 조인을 수행 합니다.

여러 쌍의 열을 연결 하 여 동일한 방식으로 두 개 이상의 테이블을 조인할 수 있습니다. 각 쌍은 SQL 키워드 **및** 에 의해 조인 됩니다.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 미리 정의 된 쿼리에 대 한 클래스 선언 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[레코드 집합: 테이블에 대 한 클래스 선언 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[레코드 집합: 레코드 집합 다시 쿼리 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)
