---
description: '자세한 정보: 레코드 집합: 레코드 집합 다시 쿼리 (ODBC)'
title: '레코드 집합: 레코드 집합 다시 쿼리(ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
ms.openlocfilehash: 3efcaac1273e6b5cc786e983bfd59f73c870cbea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204474"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>레코드 집합: 레코드 집합 다시 쿼리(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

이 항목에서는 레코드 집합 개체를 사용 하 여 데이터베이스에서 다시 쿼리 (즉, 새로 고침) 하는 방법과 [requery](../../mfc/reference/crecordset-class.md#requery) 멤버 함수를 사용 하 여이 작업을 수행할 수 있는 방법에 대해 설명 합니다.

레코드 집합을 다시 쿼리 하는 주요 이유는 다음과 같습니다.

- 사용자가 추가한 레코드 또는 다른 사용자가 삭제 한 레코드와 관련 하 여 레코드 집합을 최신 상태로 유지 합니다. 삭제 한 내용이 이미 레코드 집합에 반영 되어 있습니다.

- 변경 매개 변수 값에 따라 레코드 집합을 새로 고칩니다.

## <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a> 레코드 집합을 최신 상태로 만들기

자주 레코드 집합 개체를 다시 쿼리하여 최신 상태로 만들 수 있습니다. 다중 사용자 데이터베이스 환경에서 다른 사용자는 레코드 집합의 수명 동안 데이터를 변경할 수 있습니다. 레코드 집합에 다른 사용자가 변경한 내용이 반영 되 고 다른 사용자의 레코드 집합이 변경 내용을 반영 하는 경우에 대 한 자세한 내용은 [레코드 집합: 레코드 집합의 레코드 업데이트 방법 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) 및 [다이너셋](../../data/odbc/dynaset.md)을 참조 하십시오.

## <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a> 새 매개 변수를 기반으로 다시 쿼리

다시 [쿼리](../../mfc/reference/crecordset-class.md#requery) 를 사용 하는 경우에는 변경 매개 변수 값을 기반으로 하 여 새 레코드 집합을 선택 하는 것이 자주 수행 되며 똑같이 중요 합니다.

> [!TIP]
> 를 `Requery` 다시 호출 하는 경우 매개 변수 값을 변경 하 여를 호출 하는 경우 쿼리 속도가 훨씬 빨라질 수 있습니다 `Open` .

## <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a> 다이너셋 및 스냅숏 다시 쿼리

다이너셋은 동적 최신 데이터가 포함 된 레코드 집합을 제공 하기 때문에 다른 사용자의 추가를 반영 하려는 경우에 자주 다이너셋을 다시 쿼리해야 합니다. 반면에 스냅숏은 보고서를 준비 하 고 합계를 계산 하는 동안 정적 콘텐츠를 안전 하 게 사용할 수 있기 때문에 유용 합니다. 그래도 스냅숏을 다시 쿼리해야 하는 경우도 있습니다. 다중 사용자 환경에서는 다른 사용자가 데이터베이스를 변경할 때 스냅숏 데이터가 데이터 원본과 동기화 되지 않을 수 있습니다.

#### <a name="to-requery-a-recordset-object"></a>레코드 집합 개체를 다시 쿼리하려면

1. 개체의 [Requery](../../mfc/reference/crecordset-class.md#requery) 멤버 함수를 호출 합니다.

또는 원래 레코드 집합을 닫았다가 다시 열 수 있습니다. 두 경우 모두 새 레코드 집합은 데이터 원본의 현재 상태를 나타냅니다.

예제는 [레코드 뷰: 두 번째 레코드 집합에서 목록 상자 채우기](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)를 참조 하세요.

> [!TIP]
> 성능을 최적화 하려면 `Requery` 레코드 집합의 [필터나](../../data/odbc/recordset-filtering-records-odbc.md) [정렬을](../../data/odbc/recordset-sorting-records-odbc.md)변경 하지 마십시오. 를 호출 하기 전에 매개 변수 값만 변경 `Requery` 합니다.

호출에 `Requery` 실패 하면 호출을 다시 시도할 수 있습니다. 그렇지 않으면 응용 프로그램이 정상적으로 종료 됩니다. 또는에 대 한 호출이 `Requery` `Open` 여러 가지 이유로 실패할 수 있습니다. 네트워크 오류가 발생 했을 수도 있습니다. 또는 호출 하는 동안 기존 데이터가 해제 된 후 새 데이터를 얻기 전에 다른 사용자가 단독으로 액세스할 수 있습니다. 또는 레코드 집합이 종속 된 테이블을 삭제할 수 있습니다.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[레코드 집합: 데이터 열 동적 바인딩 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[레코드 집합: 레코드 집합 만들기 및 닫기 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
