---
title: SQL Server에 안정형 어셈블리 사용 (C + + /cli CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2bb4adbb960f9d062cc8573c7ca0f7cd5dcd0426
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382221"
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>SQL Server에 안정형 어셈블리 사용(C++/CLI)

동적 연결 라이브러리 (Dll)로 패키지 된 확장된 저장된 프로시저를 Visual c + +를 사용 하 여 개발 하는 함수를 통해 SQL Server 기능을 확장 하는 방법을 제공 합니다. 확장된 저장된 프로시저 Dll 내의 함수로 구현 됩니다. 함수 외에 확장된 저장된 프로시저를 정의할 수도 [사용자 정의 형식](../cpp/classes-and-structs-cpp.md) 와 집계 함수 (예: SUM 또는 AVG).

클라이언트는 확장된 저장된 프로시저를 실행 하는 경우 DLL에 대 한 SQL Server 검색 확장된 저장된 프로시저를 사용 하 여 연결 하 고 DLL을 로드 합니다. 요청 된 확장된 저장된 프로시저를 호출 하 고 지정 된 보안 컨텍스트에서 실행 하는 SQL Server입니다. 확장 저장 프로시저는 전달 결과 설정 하 고 서버에 다시 매개 변수를 반환 합니다.

SQL Server transact-sql (T-SQL)을 SQL Server에 안정형 어셈블리를 설치할 수 있도록 확장을 제공 합니다. SQL Server 사용 권한 집합에는 다음과 같은 수준의 보안을 사용 하 여 보안 컨텍스트를 지정합니다.

- 무제한 모드:; 위험은 사용자 고유의 코드를 실행 합니다. 코드 형식 안전성이 될 필요가 없습니다.

- 안전 모드: 형식이 안전한 코드를 실행 /clr: safe를 사용 하 여 컴파일됩니다.

안전 모드에서는 형식 안전 파일이 되도록 어셈블리를 실행된 합니다.

를 만들고 SQL Server에 안정형 어셈블리를 로드 하려면 다음과 같이 CREATE ASSEMBLY 문과 DROP ASSEMBLY TRANSACT-SQL 명령을 사용 합니다.

```sql
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH
  PERMISSION_SET <permissions>
DROP ASSEMBLY <assemblyName>
```

PERMISSION_SET 명령을 보안 컨텍스트를 지정 및 제한 없음, 안전 또는 확장 값을 가질 수 있습니다.

또한 클래스에 메서드 이름에 바인딩할 CREATE FUNCTION 명령을 사용할 수 있습니다.

```sql
CREATE FUNCTION <FunctionName>(<FunctionParams>)
RETURNS returnType
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]
```

## <a name="example"></a>예제

SQL Server에 어셈블리를 로드 하 고 클래스의 메서드를 사용할 수 있도록 하는 다음 SQL 스크립트 (예를 들어, 명명 된 "MyScript.sql"):

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

SQL 쿼리 분석기 또는 sqlcmd.exe 유틸리티를 사용 하 여 명령줄에서 SQL 스크립트를 대화형으로 실행할 수 있습니다. 다음 명령줄 MyServer 연결, 기본 데이터베이스를 사용 하 여, 트러스트 된 연결을 사용 하 여, MyScript.sql, 입력 및 MyResult.txt 출력 합니다.

```cmd
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt
```

## <a name="see-also"></a>참고 항목

[방법: /clr: safe로 마이그레이션 (C + + /cli CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)<br/>
[클래스 및 구조체](../cpp/classes-and-structs-cpp.md)