---
description: '자세한 정보: 저장 프로시저 사용'
title: 저장 프로시저 사용
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
ms.openlocfilehash: 6bd7dbd3980eb4bfe0fbca71d86af080128d3309
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319107"
---
# <a name="using-stored-procedures"></a>저장 프로시저 사용

저장 프로시저는 데이터베이스에 저장된 실행 가능한 개체입니다. 저장 프로시저를 호출 하는 것은 SQL 명령을 호출 하는 것과 비슷합니다. 클라이언트 응용 프로그램에서 문을 실행 하거나 준비 하는 대신 데이터 원본에서 저장 프로시저를 사용 하면 성능 향상, 네트워크 오버 헤드 감소, 일관성 및 정확성 향상을 비롯 한 여러 가지 이점을 얻을 수 있습니다.

저장 프로시저에는 임의의 수의 입력 또는 출력 매개 변수를 포함 하 고 반환 값을 전달할 수 있습니다. 매개 변수 값을 특정 데이터 값으로 하드 코딩 하거나 매개 변수 표식 (물음표 '? ')을 사용할 수 있습니다.

> [!NOTE]
> Visual C++를 사용 하 여 만든 CLR SQL Server 저장 프로시저는 컴파일러 옵션을 사용 하 여 컴파일해야 합니다 `/clr:safe` .

SQLOLEDB (OLE DB provider for SQL Server)는 저장 프로시저에서 데이터를 반환 하는 데 사용 하는 다음과 같은 메커니즘을 지원 합니다.

- 프로시저의 모든 **SELECT** 문은 결과 집합을 생성 합니다.

- 프로시저는 출력 매개 변수를 통해 데이터를 반환할 수 있습니다.

- 프로시저에는 정수 반환 코드가 있을 수 있습니다.

> [!NOTE]
> 저장 프로시저는 저장 프로시저를 지원 하지 않으므로 OLE DB provider for Jet에서 사용할 수 없습니다. 쿼리 문자열에는 상수만 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿 사용](../../data/oledb/working-with-ole-db-consumer-templates.md)
