---
title: 저장 프로시저 사용
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
ms.openlocfilehash: 436c796b24b0fa498f2b3f45e848392635b22a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376035"
---
# <a name="using-stored-procedures"></a>저장 프로시저 사용

저장 프로시저는 데이터베이스에 저장된 실행 가능한 개체입니다. 저장 프로시저를 호출하는 것은 SQL 명령을 호출하는 것과 유사합니다. 데이터 원본에 저장된 프로시저를 사용하는 경우(클라이언트 응용 프로그램에서 문을 실행하거나 준비하는 대신) 성능 향상, 네트워크 오버헤드 감소, 일관성 및 정확성 향상 등 몇 가지 이점을 제공할 수 있습니다.

저장 프로시저는 입력 또는 출력 매개 변수를 포함하여 여러 개(0)를 가질 수 있으며 반환 값을 전달할 수 있습니다. 하드 코드 매개 변수 값을 특정 데이터 값으로 사용하거나 매개 변수 마커(물음표 '?')를 사용할 수 있습니다.

> [!NOTE]
> Visual C++를 사용하여 만든 CLR SQL Server 저장 `/clr:safe` 프로시저는 컴파일러 옵션으로 컴파일해야 합니다.

SQLOLEDB(SQLOLEDB)에 대한 OLE DB 공급자는 저장 프로시저가 데이터를 반환하는 데 사용하는 다음 메커니즘을 지원합니다.

- 프로시저의 모든 **SELECT** 문은 결과 집합을 생성합니다.

- 프로시저는 출력 매개 변수를 통해 데이터를 반환할 수 있습니다.

- 프로시저에는 정수 반환 코드가 있을 수 있습니다.

> [!NOTE]
> 해당 공급자가 저장 프로시저를 지원하지 않으므로 Jet용 OLE DB 공급자와 함께 저장 프로시저를 사용할 수 없습니다. 쿼리 문자열에는 상수만 허용됩니다.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿 작업](../../data/oledb/working-with-ole-db-consumer-templates.md)
