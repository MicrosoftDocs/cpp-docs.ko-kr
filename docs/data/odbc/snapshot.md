---
description: '자세한 정보: 스냅숏'
title: 스냅샷
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC cursor library [ODBC], snapshots
- cursors [ODBC], static
- recordsets, snapshots
- snapshots, support in ODBC
- static cursors
- ODBC recordsets, snapshots
- cursor library [ODBC], snapshots
- snapshots
ms.assetid: b5293a52-0657-43e9-bd71-fe3785b21c7e
ms.openlocfilehash: 33505eb02613f672d09b889a09382ce3b8cf19cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204292"
---
# <a name="snapshot"></a>스냅샷

스냅숏은 스냅숏이 생성 된 당시의 데이터의 정적 뷰를 반영 하는 레코드 집합입니다. 스냅숏을 열고 모든 레코드로 이동 하면 해당 스냅숏을 포함 하는 레코드 집합이 포함 되며를 호출 하 여 스냅숏을 다시 작성할 때까지 해당 값이 변경 되지 않습니다 `Requery` .

> [!NOTE]
> 이 토픽은 MFC ODBC 클래스에 적용됩니다. MFC ODBC 클래스 대신 MFC DAO 클래스를 사용 하는 경우 스냅숏 형식 레코드 집합에 대 한 설명은 [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open) 을 참조 하세요.

데이터베이스 클래스를 사용 하 여 업데이트 가능 또는 읽기 전용 스냅숏을 만들 수 있습니다. 다이너셋과 달리 업데이트할 수 있는 스냅숏에는 다른 사용자가 만든 값을 기록 하는 변경 내용은 반영 되지 않지만 프로그램에서 수행한 업데이트 및 삭제는 반영 됩니다. 스냅숏에 추가 된 레코드는를 호출할 때까지 스냅숏에 표시 되지 않습니다 `Requery` .

> [!TIP]
> 스냅숏은 ODBC 정적 커서입니다. 정적 커서는 해당 레코드로 스크롤할 때까지 실제로 데이터 행을 가져오지 않습니다. 모든 레코드가 즉시 검색 되도록 하려면 레코드 집합의 끝으로 스크롤한 다음 보려는 첫 번째 레코드로 스크롤할 수 있습니다. 그러나 끝으로 스크롤하면 추가 오버 헤드가 발생 하 여 성능이 저하 될 수 있습니다.

스냅숏은 보고서를 생성 하거나 계산을 수행할 때와 같이 작업 중에 데이터를 고정 된 상태로 유지 해야 하는 경우에 가장 유용 합니다. 따라서 데이터 원본은 스냅숏과 크게 달라질 수 있으므로 시간에서 다시 빌드해야 할 수 있습니다.

스냅숏 지원은 모든 수준 1 드라이버에 정적 커서 및 위치 지정 업데이트 (업데이트 프로그램에 필요)를 제공 하는 ODBC 커서 라이브러리를 기반으로 합니다. 이 지원을 위해 커서 라이브러리 DLL을 메모리에 로드 해야 합니다. 개체를 생성 하 `CDatabase` 고 해당 멤버 함수를 호출 하는 경우 `OpenEx` `CDatabase::useCursorLib` *dwOptions* 매개 변수의 옵션을 지정 해야 합니다. 멤버 함수를 호출 하면 `Open` 기본적으로 커서 라이브러리가 로드 됩니다. 스냅숏 대신 다이너셋을 사용 하는 경우 커서 라이브러리를 로드 하지 않는 것이 좋습니다.

스냅숏은 개체가 생성 될 때 ODBC 커서 라이브러리를 로드 `CDatabase` 했거나 사용 중인 odbc 드라이버가 정적 커서를 지 원하는 경우에만 사용할 수 있습니다.

> [!NOTE]
> 일부 ODBC 드라이버의 경우 스냅숏 (정적 커서)을 업데이트할 수 없습니다. 지원 되는 커서 유형 및 지원 되는 동시성 유형에 대해서는 드라이버 설명서를 참조 하세요. 업데이트 가능한 스냅숏을 보장 하려면 개체를 만들 때 커서 라이브러리를 메모리로 로드 해야 `CDatabase` 합니다. 자세한 내용은 odbc [: Odbc 커서 라이브러리](../../data/odbc/odbc-the-odbc-cursor-library.md)를 참조 하십시오.

> [!NOTE]
> 스냅숏과 다이너셋을 모두 사용 하려면 서로 다른 두 개의 `CDatabase` 개체 (두 개의 다른 연결)에 기반 해야 합니다.

모든 레코드 집합과 공유 하는 속성 스냅숏에 대 한 자세한 내용은 [레코드 집합 (ODBC)](../../data/odbc/recordset-odbc.md)을 참조 하세요. Odbc 커서 라이브러리를 비롯 한 odbc 및 스냅숏에 대 한 자세한 내용은 [odbc](../../data/odbc/odbc-basics.md)를 참조 하십시오.

## <a name="see-also"></a>참고 항목

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)
