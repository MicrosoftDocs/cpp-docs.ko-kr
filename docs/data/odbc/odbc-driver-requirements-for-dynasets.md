---
description: '자세한 정보: 다이너셋을 위한 ODBC 드라이버 요구 사항'
title: 다이너셋에 대한 ODBC 드라이버 요구 사항
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
ms.openlocfilehash: 9e72499eb500ae79248673e73b666bf535fcdcc0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161015"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>다이너셋에 대한 ODBC 드라이버 요구 사항

MFC ODBC 데이터베이스 클래스에서 다이너셋은 동적 속성이 있는 레코드 집합입니다. 특정 방식으로 데이터 원본과 동기화 된 상태를 유지 합니다. MFC 다이너셋 (전방 전용 레코드 집합은 제외)에는 수준 2 API 규칙을 사용 하는 ODBC 드라이버가 필요 합니다. [데이터 원본](../../data/odbc/data-source-odbc.md) 에 대 한 드라이버가 수준 1 API 집합을 따르는 경우에도 업데이트 가능 하 고 읽기 전용 스냅숏과 전방 전용 레코드 집합을 모두 사용할 수 있지만 다이너셋은 사용할 수 없습니다. 그러나 확장 된 인출 및 키 집합 커서를 지 원하는 경우에는 수준 1 드라이버가 다이너셋을 지원할 수 있습니다.

ODBC 용어로 다이너셋과 스냅숏은 커서 라고 합니다. 커서는 레코드 집합에서의 위치를 추적 하는 데 사용 되는 메커니즘입니다. 다이너셋을 위한 드라이버 요구 사항에 대 한 자세한 내용은 [다이너셋](../../data/odbc/dynaset.md)을 참조 하세요. 커서에 대 한 자세한 내용은 [ODBC (Open Database Connectivity)](/sql/odbc/microsoft-open-database-connectivity-odbc) 설명서를 참조 하세요.

> [!NOTE]
> 업데이트 가능한 레코드 집합의 경우 ODBC 드라이버는 위치 지정 update 문 또는 odbc API 함수를 지원 해야 합니다 `::SQLSetPos` . 둘 다 지원 되는 경우 MFC는 `::SQLSetPos` 효율성을 위해를 사용 합니다. 또는 스냅숏에 대해 업데이트 가능한 스냅숏 (정적 커서 및 위치 지정 update 문)에 필요한 지원을 제공 하는 커서 라이브러리를 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[ODBC 기본 사항](../../data/odbc/odbc-basics.md)
