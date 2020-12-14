---
description: '자세한 정보: 레코드 집합: 책갈피 및 절대 위치 (ODBC)'
title: '레코드 집합: 책갈피와 절대 위치(ODBC)'
ms.date: 11/04/2016
f1_keywords:
- SetAbsolutePosition
helpviewer_keywords:
- CDBVariant class, bookmarks
- absolute positions, ODBC recordsets
- bookmarks, CDBVariant
- bookmarks, ODBC recordsets
- ODBC recordsets, absolute positions
- ODBC recordsets, bookmarks
- cursors [ODBC], absolute position in recordsets
- recordsets, bookmarks
- bookmarks
- SetAbsolutePosition method
- recordsets, absolute positions
- positioning records
- SetBookmark method
- record positioning
- GetBookmark method
- SetAbsolutePosition method, bookmarks
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
ms.openlocfilehash: b52ca2e43a89a6cab0e9197d8dbf32c321feca5e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186118"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>레코드 집합: 책갈피와 절대 위치(ODBC)

이 토픽은 MFC ODBC 클래스에 적용됩니다.

레코드 집합을 탐색할 때 특정 레코드에 반환 하는 방법이 필요 합니다. 레코드의 책갈피와 절대 위치는 이러한 두 가지 메서드를 제공 합니다.

이 토픽에서는 다음 내용을 설명합니다.

- [책갈피를 사용 하는 방법](#_core_bookmarks_in_mfc_odbc)

- [절대 위치를 사용 하 여 현재 레코드를 설정 하는 방법](#_core_absolute_positions_in_mfc_odbc)입니다.

## <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a> MFC ODBC의 책갈피

책갈피는 레코드를 고유 하 게 식별 합니다. 레코드 집합을 탐색할 때 레코드 집합에서 레코드를 삭제할 수 있으므로 항상 레코드의 절대 위치를 사용할 수 없습니다. 레코드의 위치를 추적 하는 신뢰할 수 있는 방법은 해당 책갈피를 사용 하는 것입니다. 클래스 `CRecordset` 는 다음에 대 한 멤버 함수를 제공 합니다.

- 변수 ([Getbookmark](../../mfc/reference/crecordset-class.md#getbookmark))에 저장할 수 있도록 현재 레코드의 책갈피 가져오기

- 이전에 변수 ([Setbookmark](../../mfc/reference/crecordset-class.md#setbookmark))에서 저장 한 책갈피를 지정 하 여 지정 된 레코드로 빠르게 이동 합니다.

다음 예제에서는 이러한 멤버 함수를 사용 하 여 현재 레코드를 표시 하 고 나중에 반환 하는 방법을 보여 줍니다.

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

[Cdbvariant 클래스](../../mfc/reference/cdbvariant-class.md) 개체에서 기본 데이터 형식을 추출할 필요는 없습니다. 를 사용 하 여 값을 할당 하 `GetBookmark` 고를 사용 하 여 해당 책갈피로 돌아갑니다 `SetBookmark` .

> [!NOTE]
> ODBC 드라이버 및 레코드 집합 유형에 따라 책갈피는 지원 되지 않을 수 있습니다. [CRecordset:: CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark)를 호출 하 여 책갈피가 지원 되는지 여부를 쉽게 확인할 수 있습니다. 또한 책갈피가 지원 되는 경우 `CRecordset::useBookmarks` [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) 멤버 함수에서 옵션을 지정 하 여 명시적으로 구현 하도록 선택 해야 합니다. 또한 특정 레코드 집합 작업 후 책갈피의 지 속성을 확인 해야 합니다. 예를 들어 `Requery` 레코드 집합의 경우 책갈피는 더 이상 유효 하지 않을 수 있습니다. [CDatabase:: Get책갈피 지 속성](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) 을 호출 하 여 안전 하 게 호출할 수 있는지 여부를 확인 `SetBookmark` 합니다.

## <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a> MFC ODBC의 절대 위치

책갈피 외에도 클래스를 `CRecordset` 사용 하면 서 수 위치를 지정 하 여 현재 레코드를 설정할 수 있습니다. 이를 절대 위치 지정 이라고 합니다.

> [!NOTE]
> 절대 위치 지정은 전방 전용 레코드 집합에서 사용할 수 없습니다. 앞 으로만 이동 가능한 레코드 집합에 대 한 자세한 내용은 [레코드 집합 (ODBC)](../../data/odbc/recordset-odbc.md)을 참조 하세요.

절대 위치를 사용 하 여 현재 레코드 포인터를 이동 하려면 [CRecordset:: SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition)를 호출 합니다. 값을에 전달 하면 해당 `SetAbsolutePosition` 서 수 위치에 해당 하는 레코드가 현재 레코드가 됩니다.

> [!NOTE]
> 레코드의 절대 위치는 잠재적으로 신뢰할 수 없습니다. 사용자가 레코드 집합에서 레코드를 삭제 하는 경우 후속 레코드의 서 수 위치가 변경 됩니다. 책갈피는 현재 레코드를 이동 하는 데 권장 되는 방법입니다. 자세한 내용은 [MFC ODBC의 책갈피](#_core_bookmarks_in_mfc_odbc)를 참조 하세요.

레코드 집합 탐색에 대 한 자세한 내용은 [레코드 집합: 스크롤 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[레코드 집합(ODBC)](../../data/odbc/recordset-odbc.md)
