---
description: '자세히 알아보기: Schema (MFC Data Access)'
title: 스키마(데이터 액세스)
ms.date: 11/04/2016
helpviewer_keywords:
- structures [C++], database
- databases [C++], schema
- database schema [C++], about database schemas
- database schema [C++]
- schemas [C++], database
- structures [C++]
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
ms.openlocfilehash: 87080cb05d22a5328e0e6ad5a36b25771d319209
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332427"
---
# <a name="schema--mfc-data-access"></a>스키마(데이터 액세스)

데이터베이스 스키마는 데이터베이스의 데이터베이스 뷰와 테이블의 현재 구조를 설명합니다. 일반적으로 마법사에서 생성된 코드는 레코드 집합에서 액세스하는 테이블 하나 이상의 스키마가 변경되지 않는다고 가정합니다. 그러나 데이터베이스 클래스는 바인딩되지 않은 열 추가, 다시 정렬, 삭제 등의 일부 스키마 변경을 처리할 수 있습니다. 테이블이 변경되면 수동으로 테이블의 레코드 집합을 업데이트한 다음 애플리케이션을 다시 컴파일해야 합니다.

또한 컴파일 타임에 스키마가 완전히 확인되지 않은 데이터베이스를 처리할 수 있도록 마법사에서 생성된 코드를 보완할 수도 있습니다. 자세한 내용은 [레코드 집합: 데이터 열 동적 바인딩 (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[데이터 액세스 프로그래밍 (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[레코드 집합(ODBC)](../data/odbc/recordset-odbc.md)
