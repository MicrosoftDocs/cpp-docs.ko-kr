---
description: '자세히 알아보기: 출력 매개 변수'
title: 출력 매개 변수
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
ms.openlocfilehash: c52877483d40d7de1a8313eb806769ce92af7337
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316936"
---
# <a name="output-parameters"></a>출력 매개 변수

저장 프로시저를 호출 하는 것은 SQL 명령을 실행 하는 것과 비슷합니다. 주요 차이점은 저장 프로시저는 출력 매개 변수 ("outparameters")와 반환 값을 사용 한다는 것입니다.

다음 저장 프로시저에서 첫 번째 '? '는 반환 값 (phone)이 고 두 번째 '? '는 입력 매개 변수 (이름)입니다.

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }"))
```

매개 변수 맵에서 in 및 out 매개 변수를 지정 합니다.

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter
END_PARAM_MAP()
```

응용 프로그램은 저장 프로시저에서 반환 된 출력을 처리 해야 합니다. OLE DB 공급자는 결과를 처리하는 동안 각각 다른 시기에 출력 매개 변수와 반환 값을 반환합니다. 예를 들어 Microsoft OLE DB provider for SQL Server (SQLOLEDB)는 소비자가 저장 프로시저에서 반환 된 결과 집합을 검색 하거나 취소할 때까지 출력 매개 변수와 반환 코드를 제공 하지 않습니다. 서버에서 마지막 TDS 패킷에 출력이 반환 됩니다.

## <a name="row-count"></a>행 개수

OLE DB 소비자 템플릿을 사용 하 여 outparameters 있는 저장 프로시저를 실행 하는 경우 행 집합을 닫을 때까지 행 개수가 설정 되지 않습니다.

예를 들어 행 집합과 outparameter를 포함 하는 저장 프로시저를 생각해 보겠습니다.

```sql
create procedure sp_test
   @_rowcount integer output
as
   select top 50 * from test
   @_rowcount = @@rowcount
return 0
```

`@_rowcount`Outparameter는 테스트 테이블에서 반환 된 행 수를 보고 합니다. 그러나이 저장 프로시저는 행 수를 50로 제한 합니다. 예를 들어 테스트에 100 행이 있는 경우이 코드는 상위 50 행만 검색 하므로 rowcount는 50이 됩니다. 테이블에 30 개의 행만 있는 경우 rowcount는 30입니다. `Close` `CloseAll` 값을 페치 하기 전에 또는를 호출 하 여 outparameter를 채워야 합니다.

## <a name="see-also"></a>참고 항목

[저장 프로시저 사용](../../data/oledb/using-stored-procedures.md)
