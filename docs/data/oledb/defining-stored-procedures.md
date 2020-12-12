---
description: '자세한 정보: 저장 프로시저 정의'
title: 저장 프로시저 정의
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
ms.openlocfilehash: 52527da031093d82c9d74be5807a5de26f3ee091
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317690"
---
# <a name="defining-stored-procedures"></a>저장 프로시저 정의

저장 프로시저를 호출 하기 전에 먼저 [DEFINE_COMMAND](./macros-and-global-functions-for-ole-db-consumer-templates.md#define_command) 매크로를 사용 하 여 저장 프로시저를 정의 해야 합니다. 명령을 정의할 때 매개 변수 표식으로 물음표 (?)가 포함 된 매개 변수를 표시 합니다.

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{INSERT {name, phone} INTO shippers (?,?)}"))
```

이 항목의 코드 예제에 사용 된 구문 (중괄호 사용)은 SQL Server에만 해당 됩니다. 저장 프로시저에서 사용 하는 구문은 사용 하는 공급자에 따라 달라질 수 있습니다.

그런 다음 매개 변수 맵에서 명령에 사용 된 매개 변수를 지정 하 고 명령에서 발생 하는 순서 대로 매개 변수를 나열 합니다.

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param
END_PARAM_MAP()
```

이전 예에서는 저장 프로시저가 이동 하는 동안 정의 합니다. 일반적으로 코드를 효율적으로 다시 사용 하기 위해 데이터베이스에는 또는와 같은 이름을 가진 미리 정의 된 저장 프로시저 집합이 포함 되어 있습니다 `Sales by Year` `dt_adduserobject` . SQL Server Enterprise 관리자를 사용 하 여 해당 정의를 볼 수 있습니다. 다음과 같이 *호출 합니다.* 매개 변수는 저장 프로시저의 인터페이스에 종속 됩니다.

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }"))
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }"))
```

다음으로 command 클래스를 선언 합니다.

```cpp
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>
```

마지막으로 다음과 같이의 저장 프로시저를 호출 합니다 `OpenRowset` .

```cpp
CSession m_session;

HRESULT OpenRowset()
{
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);
}
```

데이터베이스 특성을 사용 하 여 다음과 같이 저장 프로시저를 정의할 수도 있습니다. [db_command](../../windows/attributes/db-command.md) 합니다.

```cpp
db_command("{ ? = CALL dbo.dt_adduserobject }")
```

## <a name="see-also"></a>참고 항목

[저장 프로시저 사용](../../data/oledb/using-stored-procedures.md)
