---
description: '자세히 알아보기: 레코드 선택 및 조작'
title: 레코드 선택 및 조작
ms.date: 05/09/2019
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
ms.openlocfilehash: 8f4254f85eb8c2e30b5e912890fdc271340df9db
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204305"
---
# <a name="selecting-and-manipulating-records"></a>레코드 선택 및 조작

> [!NOTE]
> Visual Studio 2019 이상에서는 MFC ODBC 소비자 마법사를 사용할 수 없습니다. 여전히 수동으로 소비자를 만들 수 있습니다.

일반적으로 SQL **SELECT** 문을 사용하여 데이터 원본에서 레코드를 선택할 때 테이블 또는 쿼리의 레코드 세트인 결과 집합을 가져옵니다. 데이터베이스 클래스에서 레코드 집합 개체를 사용하여 결과 집합을 선택하고 액세스합니다. 클래스 [CRecordset](../../mfc/reference/crecordset-class.md)에서 파생되는 애플리케이션별 클래스의 개체입니다. 레코드 집합 클래스를 정의할 때 연결할 데이터 원본, 사용할 테이블 및 테이블의 열을 지정합니다. MFC 애플리케이션 마법사 또는 **클래스 추가**([MFC ODBC 소비자 추가](../../mfc/reference/adding-an-mfc-odbc-consumer.md)에 설명된 대로)에서 특정 데이터 원본에 연결된 클래스를 만듭니다. 마법사는 `CRecordset` 클래스의 [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) 멤버 함수를 작성하여 테이블 이름을 반환합니다.

런타임 시 [CRecordset](../../mfc/reference/crecordset-class.md) 개체를 사용하여 다음을 수행할 수 있습니다.

- 현재 레코드의 데이터 필드를 검사합니다.

- 레코드 집합을 필터링하거나 정렬합니다.

- 기본 SQL **SELECT** 문을 사용자 지정합니다.

- 선택한 레코드를 스크롤합니다.

- 레코드 추가, 업데이트 또는 삭제(데이터 원본과 레코드 집합이 모두 업데이트할 수 있는 경우).

- 레코드 집합이 다시 쿼리를 허용 하는지 여부를 테스트하고 레코드 집합의 콘텐츠를 새로 고칩니다.

레코드 집합 개체 사용을 마쳤으면 레코드를 닫고 삭제합니다. 레코드 집합에 대한 자세한 내용은 [레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[ODBC 및 MFC](../../data/odbc/odbc-and-mfc.md)
