---
description: '자세한 정보: SQL Server에서 안정형 어셈블리 사용 (c + +/CLI)'
title: SQL Server에 안정형 어셈블리 사용(C++/CLI)
ms.date: 10/17/2018
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
ms.openlocfilehash: b155fb0360fb373f5931f51de3af557d06858a71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204201"
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>SQL Server에 안정형 어셈블리 사용(C++/CLI)

Dll (동적 연결 라이브러리)로 패키지 된 확장 저장 프로시저는 Visual C++를 사용 하 여 개발 된 함수를 통해 SQL Server 기능을 확장 하는 방법을 제공 합니다. 확장 저장 프로시저는 Dll 내에서 함수로 구현 됩니다. 확장 저장 프로시저는 함수 외에도 [사용자 정의 형식](../cpp/classes-and-structs-cpp.md) 및 집계 함수 (예: SUM 또는 AVG)를 정의할 수 있습니다.

클라이언트에서 확장 저장 프로시저를 실행 하면 SQL Server 확장 저장 프로시저와 연결 된 DLL을 검색 하 여 DLL을 로드 합니다. SQL Server는 요청한 확장 저장 프로시저를 호출 하 고 지정 된 보안 컨텍스트에서 실행 합니다. 그런 다음 확장 저장 프로시저는 결과 집합을 전달 하 고 매개 변수를 서버에 다시 반환 합니다.

SQL Server는 Transact-sql (T-sql)에 대 한 확장을 제공 하 여 SQL Server에 확인할 수 있는 어셈블리를 설치할 수 있습니다. SQL Server 권한 집합은 보안 컨텍스트를 지정 하며 보안 수준은 다음과 같습니다.

- 무제한 모드: 사용자의 위험에 따라 코드를 실행 합니다. 코드는 형식이 안전 해야 합니다.

- 안전 모드: 안정형 형식 안전 코드를 실행 합니다. /clr: safe를 사용 하 여 컴파일됩니다.

> [!IMPORTANT]
> Visual Studio 2015는 사용 되지 않으며 Visual Studio 2017은 안정형 프로젝트의 **/clr: pure** 및 **/clr: safe** 생성을 지원 하지 않습니다. 안정형 코드가 필요한 경우 코드를 c #으로 변환 하는 것이 좋습니다.

안정형 어셈블리를 만들어 SQL Server으로 로드 하려면 다음과 같이 Transact-sql commands CREATE ASSEMBLY 및 DROP ASSEMBLY를 사용 합니다.

```sql
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH
  PERMISSION_SET <permissions>
DROP ASSEMBLY <assemblyName>
```

PERMISSION_SET 명령은 보안 컨텍스트를 지정 하며, 제한 없음, 안전 또는 확장 값을 가질 수 있습니다.

또한 함수 만들기 명령을 사용 하 여 클래스의 메서드 이름에 바인딩할 수 있습니다.

```sql
CREATE FUNCTION <FunctionName>(<FunctionParams>)
RETURNS returnType
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]
```

## <a name="example"></a>예제

다음 SQL 스크립트 (예: "MyScript")는 어셈블리를 SQL Server로 로드 하 고 클래스의 메서드를 사용할 수 있도록 합니다.

```sql
-- Create assembly without external access
drop assembly stockNoEA
go
create assembly stockNoEA
from
'c:\stockNoEA.dll'
with permission_set safe

-- Create function on assembly with no external access
drop function GetQuoteNoEA
go
create function GetQuoteNoEA(@sym nvarchar(10))
returns real
external name stockNoEA:StockQuotes::GetQuote
go

-- To call the function
select dbo.GetQuoteNoEA('MSFT')
go
```

Sql 스크립트는 SQL 쿼리 분석기에서 대화형으로 실행 하거나 명령줄에서 sqlcmd.exe 유틸리티를 사용 하 여 실행할 수 있습니다. 다음 명령줄은 MyServer에 연결 하 고, 기본 데이터베이스를 사용 하며, 신뢰할 수 있는 연결 MyScript를 사용 하 고, MyResult.txt 출력 합니다.

```cmd
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt
```

## <a name="see-also"></a>참조

[클래스 및 구조체](../cpp/classes-and-structs-cpp.md)
