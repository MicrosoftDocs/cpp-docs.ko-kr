---
title: OLE DB 소비자 특성 (c + + COM) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], database
- attributes [C++/CLI], data access
- databases [C++], attributes
- OLE DB consumers [C++], attributes
- database attributes [C++/CLI]
- attributes [C++/CLI], OLE DB consumer
ms.assetid: 017b591f-8f9a-42b4-84d5-cc42a21ab0cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19c3e441ff4130d30f3aeb7957c5af85576fb9e1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065865"
---
# <a name="ole-db-consumer-attributes"></a>OLE DB 소비자 특성
OLE DB 소비자 특성을 기준으로 코드를 삽입 합니다 [OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-reference.md), 소비자를 만드는 작업 OLE DB 여 테이블과 같은 작업을 수행 하는 데이터에 액세스 하 고 명령을 실행 합니다.

|특성|설명|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|행 집합의 열을 바인딩합니다 및 해당 접근자 맵은 바인딩합니다.|
|[db_column](db-column.md)|행 집합에 지정된 된 열을 바인딩합니다.|
|[db_command](db-command.md)|OLE DB 명령을 실행합니다.|
|[db_param](db-param.md)|지정 된 멤버 변수는 입력 또는 출력 매개 변수를 사용 하 여 연결합니다.|
|[db_source](db-source.md)|페이지를 만들고 데이터 원본에 공급자를 통해 연결을 캡슐화 합니다.|
|[db_table](db-table.md)|OLE DB 테이블을 엽니다.|

## <a name="see-also"></a>참고 항목

[그룹별 특성](attributes-by-group.md)